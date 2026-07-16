# ADR-002: Risk Scoring — Deterministic Rules First, LLM Advisory Only

**Date:** 2026-07-05
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](002-risk-scoring-model.zh.md)

## Context

Every intercepted tool call needs a verdict (`allow | deny | review`) and a risk score (0–100) that a human can understand in the approval queue and audit later in the ledger. Two philosophies:

- **Deterministic rules:** YAML policy + weighted signals. Same input → same score, explainable line by line, fast enough for the hook latency budget (ADR-001, <200ms p95).
- **LLM judge:** ask a model "is this call dangerous?". Flexible, catches novel patterns, but non-deterministic, slower, costs per call, and — critically — *itself promptable*. A firewall whose judge can be prompt-injected by the very content it inspects inherits the vulnerability it exists to stop.

The 0din-class attack signature is knowable in advance: instructions originating from untrusted repo content, leading to network fetch piped into a shell, or writes outside the workspace, or reads of credential paths.

## Decision

**The verdict is always produced by deterministic rules. Risk score = weighted sum of named signals, capped at 100. An optional LLM classifier may add one advisory signal (`llm_flag`, weight ≤ 15) but can never allow what rules deny, and is off by default at v1.**

v1 signal set (weights in `policies/default.yaml`, config-driven per the invest ADR-008 discipline):

| Signal | Example | Weight |
|---|---|---|
| `shell_pipe_from_network` | `curl ... \| sh`, `wget -O- ... \| bash` | 40 |
| `secrets_path_access` | reads of `~/.ssh`, `~/.aws`, `.env`, keychain | 35 |
| `write_outside_workspace` | file writes above cwd / to system paths | 25 |
| `network_unknown_host` | egress to a host not on the project allowlist | 20 |
| `untrusted_origin_instruction` | call arguments traced to freshly cloned repo content | 20 |
| `destructive_command` | `rm -rf`, `git push --force`, `DROP TABLE` | 25 |
| `privilege_escalation` | `sudo`, `chmod +s` | 30 |

Thresholds (also config): score < 25 → `allow` (logged), 25–69 → `review` (approval queue), ≥ 70 → `deny` (auto-block, still appealable from the queue). The allow ceiling sits at the lightest single-signal weight that warrants a human look — `destructive_command` or `write_outside_workspace` alone must land in `review`, not slip under the bar. Explicit `deny` rules (e.g. secrets exfiltration patterns) short-circuit regardless of score.

## Consequences

Positive:
- Every verdict is replayable and explainable: the ledger row lists exactly which signals fired and their weights — this *is* the audit story enterprises need.
- No per-call LLM cost or latency; hook budget holds.
- The scoring engine is testable with plain fixtures: a corpus of known-bad calls (0din reproduction, secrets reads) and known-good calls (npm install, git commit) as regression tests.

Tradeoffs:
- Rules miss novel attack shapes an LLM might catch. Mitigation: the advisory `llm_flag` channel exists for exactly this, capped so it can only *raise* review likelihood, never override a deny; plus policy updates are cheap YAML edits.
- Weight tuning is judgment, not science, at v1. Same position as founder ADR-003 (opportunity score formula): ship a defensible formula, revise with data from the ledger.

Risks:
- Signal evasion (obfuscated commands, base64 payloads) → normalize/decode inputs before matching; track evasion patterns as new signals; this arms race is documented, not hidden.
- Alert fatigue if `review` fires too often → per-project allowlists and a "remember this approval for this session" option in the queue (ADR-003).

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| LLM judge as primary | Non-deterministic verdicts are un-auditable ("why was this blocked yesterday but allowed today?"); the judge is itself prompt-injectable; adds cost + latency to every tool call. |
| Score-free binary allow/deny | Loses the middle ground that makes the product usable — `review` + approval queue is the human-in-the-loop core, and the score is what the human sees to decide quickly. |
| Per-tool static allowlist only (no scoring) | Where invest ADR-014 landed for one MCP — right for one broker surface, too coarse for general-purpose agents where `Bash` is one tool with unbounded inputs. |

## Migration Triggers

- Ledger data shows systematic false negatives rules can't express → promote the LLM classifier from advisory to a gated second stage (still never overriding explicit deny rules).
- Multi-tenant enterprise deployment → per-team policy inheritance (org base + project overrides).

## Related

- [ADR-001: Interception Point](./001-interception-point.md)
- [ADR-003: Approval Workflow + Decision Ledger](./003-approval-workflow-ledger.md)
- xingai-founder ADR-003 (opportunity score formula) — same "defensible formula now, data later" stance
- xingai-invest-decision-engine ADR-008 (config-driven parameters)
