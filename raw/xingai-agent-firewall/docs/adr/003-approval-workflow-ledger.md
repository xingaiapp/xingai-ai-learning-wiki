# ADR-003: Approval Workflow + Decision Ledger Reuse

**Date:** 2026-07-05
**Status:** Accepted
**Author:** Xing @ XingAI
**Also available:** [中文](003-approval-workflow-ledger.zh.md)

## Context

ADR-002 produces three verdicts. `allow` and `deny` are automatic; `review` needs a human. Two design questions:

1. **What does the approval workflow look like?** The call is held open by the synchronous hook (ADR-001) — the human must be able to decide fast, with enough context, and the default on timeout must be safe.
2. **How is everything recorded?** XingAI already has a cross-product answer: the Decision Ledger schema (`xingai-engineering-system/patterns/decision-ledger-schema.md`), adopted by invest-decision-engine (ADR-015/016) and research-startup-agent (ADR-003). The firewall's verdicts are decisions a human acts on — exactly the pattern's target shape.

There is one twist: in sibling products the *system recommends, the human executes outside the system*. Here the human's approval *causes execution inside the system* (the held call proceeds). The ledger must faithfully record both the firewall's recommendation and the human's ruling.

## Decision

**Adopt the shared Decision Ledger schema unchanged, one row per intercepted call. The approval queue is a local web UI (dashboard) fed by the same SQLite database; `review` verdicts block until approved, denied, or timed out — timeout resolves to deny (`APPROVAL_TIMEOUT_SECONDS`, default 300).**

Field mapping onto the shared schema:

| Ledger field | Firewall meaning |
|---|---|
| `product` | `"agent-firewall"` |
| `domain` | tool category: `"bash"`, `"file-write"`, `"network"`, `"secrets"` |
| `question` | the intercepted call, normalized (command line / path / host) |
| `recommendation` | firewall verdict: `allow` / `deny` / `review` |
| `reasoning` | fired signals with weights, human-readable (from ADR-002) |
| `confidence` | risk score / 100 — semantics documented here per the pattern's calibration rule: it is *risk*, not certainty; do not compare with other products' confidence |
| `action_taken` | `followed` (human agreed with verdict) / `modified` (human overrode) / `ignored` (timeout → deny) |
| `outcome` | what actually executed, exit status; null for blocked calls |
| `source_ref` | session id + tool-call id from the harness |

Approval UX rules:
- The queue card shows: normalized call, risk score, fired signals, originating session, and a diff-style preview for file writes. Decision is one click: **Approve once / Approve for session / Deny / Deny + add rule**.
- "Approve for session" writes a session-scoped allowlist entry (not a permanent policy change) — permanent policy edits go through YAML, reviewed like code.
- Every override (human allows what rules flagged, or denies what rules allowed) is the highest-value training data; the dashboard surfaces override rate per rule to drive weight tuning (ADR-002 migration trigger).

## Consequences

Positive:
- Zero new schema design; the audit story ("who approved what, when, why") falls out of a pattern already proven in two products.
- The firewall becomes the third adopter of the shared schema — strengthens the cross-product decision history vision without building central infrastructure.
- Timeout-to-deny keeps the fail-closed guarantee end-to-end (engine unreachable → deny; human unreachable → deny).

Tradeoffs:
- Synchronous holds mean an unattended agent run can stall up to the timeout on every `review`. Acceptable at v1: the answer for unattended runs is stricter pre-approved policy, not weaker gating.
- Session-scoped approvals add state the engine must expire correctly; scoped to session id to bound the blast radius of a wrong approval.

Risks:
- Approval fatigue → rubber-stamping. Mitigations: "Deny + add rule" makes tightening policy one click; override-rate dashboard makes noisy rules visible; ADR-002 thresholds are tunable per project.
- Ledger grows unbounded on chatty agents → `allow` rows below a configurable score floor can be sampled (counted, not stored verbatim) — full fidelity for `review`/`deny` always.

## Alternatives Considered

| Option | Reason rejected |
|---|---|
| Custom audit-log schema | Duplicates a proven internal pattern and forfeits the cross-product decision history; the shared shape costs nothing extra. |
| Async approval (call fails immediately, human approves a retry later) | Breaks agent flow — the agent treats the failure as an error and improvises around it, which is exactly the behavior a firewall shouldn't provoke. Synchronous hold matches how permission prompts already work in harnesses. |
| Auto-approve with post-hoc audit only | Audit without prevention fails the core use case — the 0din payload has already run by audit time. |

## Migration Triggers

- Team deployments need multi-approver rules (e.g. secrets access requires a second approver) → extend queue with approver roles; schema unchanged (`action_taken` already carries the ruling).
- A cross-product decision-history surface ships → firewall rows join it for free.

## Related

- [ADR-001: Interception Point](./001-interception-point.md)
- [ADR-002: Risk Scoring Model](./002-risk-scoring-model.md)
- xingai-engineering-system: `patterns/decision-ledger-schema.md`
- xingai-invest-decision-engine ADR-003 (human-in-the-loop), ADR-015/016 (decision ledger)
