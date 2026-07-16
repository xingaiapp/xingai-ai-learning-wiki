# Concept: The Decision Ledger Pattern

An immutable record of *what was decided, on what evidence, under what policy version, by what model* — computed in a worker/core boundary, transported read-only through APIs, never recomputed in a UI or request handler.

| Where | Shape |
|---|---|
| [Course 07](../courses/07-enterprise-decision-systems.md) | Canonical teaching version — `Decision` frozen dataclass, `api_view()` explicitly comments "transport only; no request-time recomputation." |
| [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md) `DecisionLedger` | MCP-client-backed (Phase 1), `model_version` pinned per row so fairness audits are possible (the POC's `PRODUCTION-READINESS.md` notes the audit *process* itself is still a gap — the data shape exists). |
| Public engineering patterns | [xingai-engineering-system](https://github.com/xingaiapp/xingai-engineering-system) documents a shared Decision Ledger schema as "patterns, not libraries." |

Course 07's References also cite a sibling-product decision-cache ADR by path; this wiki does not ingest that private ADR — treat the course citation as a pointer only.

## Why it recurs

Same underlying question: can you prove why an automated system did what it did, after the fact? Claims, investing, and agent governance all hit that question; the ledger shape is durable because the question is.

## Open gap (flagged in public POC docs)

Versioning a `model_version` string is not the same as a model change-management / approval workflow before a new model or prompt goes live. `claims-workflow-v2-poc/PRODUCTION-READINESS.md` names this explicitly.

## Sources

`raw/courses/07-enterprise-decision-systems.md`, `raw/claims-workflow-v2-poc/` (README + PRODUCTION-READINESS + ADR-008/009)
