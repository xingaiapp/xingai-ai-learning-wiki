# Concept: The Decision Ledger Pattern

An immutable record of *what was decided, on what evidence, under what policy version, by what model* — computed once in a worker/core boundary, transported read-only through APIs, never recomputed in a UI or request handler. The same shape recurs across every XingAI product/POC touched this session:

| Where | Shape |
|---|---|
| [Course 07](../courses/07-enterprise-decision-systems.md) | Canonical teaching version — `Decision` frozen dataclass, `api_view()` explicitly comments "transport only; no request-time recomputation." |
| [xingai-learn](../products/xingai-learn.md) ADR-003 | `DecisionRecord`/ledger adoption for interview-pattern recommendations. |
| `xingai-invest-ai` ADR-012 | The decision-cache boundary Course 07 cites directly as a real-world instance. |
| [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md) `DecisionLedger` | MCP-client-backed (Phase 1), `model_version` pinned per row so fairness audits are possible (though this session's `PRODUCTION-READINESS.md` noted the audit *process* itself doesn't exist yet — the data does). |
| [xingai-agent-firewall](../products/xingai-agent-firewall.md) `engine/ledger.py` | Every policy verdict (tool call allow/deny/review) is a Decision row; the [Agent Skill Assurance opportunity](../products/opportunity-radar.md) (2026-07-16 Radar pick) is designed to reuse this exact table for pre-production `ReleaseDecision`s rather than inventing a parallel ledger. |
| `xingai-engineering-system/patterns/decision-ledger-schema.md` | The shared schema definition all of the above implement independently — "patterns, not libraries" (verbatim from `xingai-learn` ADR-001). |

## Why it recurs

Every one of these is answering the same underlying question — "can you prove why an automated system did what it did, after the fact, to a regulator/auditor/engineer who wasn't there" — in a different domain (claims, investing, interview recommendations, agent tool-call governance). The pattern is durable because the question is durable, not because any one team copied another's code — see `xingai-learn` ADR-001's explicit "patterns, not libraries" stance.

## Open gap (flagged, not yet closed)

None of the instances above have a **model change-management process** — versioning a `model_version` string is not the same as an approval workflow before a new model/prompt goes live. `claims-workflow-v2-poc/PRODUCTION-READINESS.md` names this gap explicitly; it applies equally to `xingai-learn` and `xingai-agent-firewall`.

## Sources

`raw/xingai-learn/docs/adr/003-decision-ledger.md`, `raw/courses/07-enterprise-decision-systems.md`; cross-repo claims verified during the 2026-07-16 review (chat analysis, not a single raw file).
