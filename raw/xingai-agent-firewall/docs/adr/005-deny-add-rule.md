# ADR-005: Deny + Add Rule — Instant Local Pin, Reviewed YAML Suggestion

**Date:** 2026-07-11
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](005-deny-add-rule.zh.md)

## Context

ADR-003's approval UX promises four one-click actions: Approve once / Approve for session / Deny / **Deny + add rule**. The first three ship (ADR-001/002/003 implementation); "Deny + add rule" has no backend. ADR-003 also states: *"permanent policy edits go through YAML, reviewed like code."* These two statements are in tension — a literal one-click write to `policies/default.yaml` from a running service violates ADR-002's discipline that config changes are reviewed like code; but a button that does nothing but suggest "go edit the YAML yourself" delivers no more than plain Deny already does.

## Decision

**Split the action into two layers: an instant, reversible, local pin that stops the same call from re-entering the queue, and a durable-policy suggestion that still requires a human to commit YAML.**

1. **Instant layer — `pinned_denies` table** (`id`, `normalized_pattern`, `source_session`, `reason`, `created_at`). `/check` consults this table before scoring: an exact match on the normalized call short-circuits to `deny`, skipping the approval queue entirely. Structurally this mirrors `session_allowlist` (ADR-003) but with two differences: it is **not** session-scoped (the point is "don't ask me again for this exact call, anywhere"), and it persists until removed from the dashboard — not until session end. This is runtime state, not policy code; it carries no more authority than the human click that created it.

2. **Suggestion layer — `rule_suggestions` table** (`id`, `normalized_pattern`, `reasoning`, `created_at`, `resolved_at`). The same click inserts a suggestion row. The dashboard's "Rules" view lists unresolved suggestions with the exact pattern and the original fired-signal reasoning; a human reviews it, edits `policies/default.yaml` by hand (git-reviewed, per ADR-002/003), then marks the suggestion resolved. Resolving a suggestion optionally removes the matching `pinned_denies` row, since a real policy rule now covers it.

Net effect of one click: the specific call is denied immediately and never bothers a human again (pin), while a durable policy change is queued for review rather than auto-applied (suggestion) — honoring ADR-002's "config is reviewed like code" without making the button inert.

**Matching granularity (v1):** exact string match on the same `normalized` value used by `session_allowlist` — no new pattern language. If variants of the same attack (e.g. same shell-pipe pattern, different URL) turn out to slip past exact match often in practice, that's a migration trigger, not a v1 requirement.

**Scope:** not partitioned by `cwd` or session — a human judged the *call pattern itself* dangerous, so the pin applies wherever that exact normalized call appears next, consistent with how `deny_rules` in YAML already apply project-wide.

## Consequences

Positive:
- Delivers the fourth action ADR-003 promised without contradicting ADR-002's review discipline.
- `pinned_denies` reuses the exact shape and matching logic already proven by `session_allowlist` — no new concept to test from scratch.
- The suggestion queue becomes the dashboard's second view (alongside the approval queue) and gives the override-rate analytics (ADR-002 migration trigger) a natural home: frequently-pinned patterns are exactly the signal that a YAML rule is overdue.

Tradeoffs:
- Two new tables and two new dashboard views for one button — real scope, comparable to ADR-004.
- Exact-string matching means a human must click "Deny + add rule" again for each variant of an attack until someone writes the general YAML rule; this is deliberate (v1 doesn't invent a pattern language) but does mean the pin list can grow noisy before someone does the YAML review.

Risks:
- A pinned deny with a bad `normalized_pattern` (e.g. accidentally matching a benign command) silently blocks that command everywhere with no explanation beyond the dashboard's pin list — mitigated by the dashboard always showing pins as a visible, removable list, never a silent side effect.

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| One click directly rewrites `policies/default.yaml` | Violates ADR-002's "config reviewed like code" — a network-facing service silently mutating its own enforcement policy is the kind of unreviewed change the firewall exists to prevent elsewhere |
| Button only shows a copy-paste YAML snippet, no runtime effect | Doesn't stop the same call from re-entering `review` on every repeat until the human gets around to editing the file — fails the "don't ask me again" expectation the UI promises |
| Parameterized/regex rule generation from the clicked call | Real pattern generalization needs judgment about what varies (the URL? the host? the whole shell-pipe shape?) — that's exactly the human review step in the suggestion layer, not something to infer automatically at v1 |

## Migration Triggers

- Pinned-deny list grows large with many near-duplicate patterns (same attack shape, different literals) → invest in a parameterized rule language for suggestions, informed by the accumulated pins as training examples.
- Multi-user/team deployment (ADR-001 phase 2) → pins need an owner and a scope (team-wide vs personal), not just a flat list.

## Related

- [ADR-002: Risk Scoring Model](002-risk-scoring-model.md)
- [ADR-003: Approval Workflow + Decision Ledger Reuse](003-approval-workflow-ledger.md)
- [ADR-004: Origin Provenance — Session-Scoped Taint Tracking](004-origin-provenance-tracking.md)
