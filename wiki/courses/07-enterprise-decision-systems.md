# Course 07: Enterprise AI Decision Systems

**Prerequisite:** [06](06-production-ai-engineering.md) · **Gate:** architecture review board defense · **Next:** [08](08-ai-leadership-cto.md)

This course *is* the Decision Ledger pattern, taught as architecture: "decision computation belongs in a worker/core domain boundary; APIs transport precomputed decisions; UIs explain them; execution remains separately authorized." The immutable `Decision` dataclass in the raw source, with `api_view()` explicitly commented `# transport only; no request-time recomputation`, is the same shape as `xingai-invest-ai`'s ADR-012 decision-cache boundary (cited directly in the course's own References) and `xingai-learn`'s [ADR-003](../products/xingai-learn.md#decision-ledger).

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md) — this course is the canonical teaching version of that concept; treat the concept page as the cross-product index and this page as the pedagogy.
- [xingai-learn](../products/xingai-learn.md) — `DecisionRecord`/ledger adoption there is a real product instance of this course's pattern, at smaller scale (one product, not a shared platform).
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s `DecisionLedger` (reviewed extensively this session, MCP-client-backed) — same schema shape, reused per `xingai-engineering-system/patterns/decision-ledger-schema.md`.

## Verified

ZH sibling ingested 2026-07-16: Python code blocks differ by exactly one thing — the `api_view()` inline comment is localized (`# transport only; no request-time recomputation` vs. `# 仅传输，不在请求时重新计算`), which is a correct localization under COURSE-STANDARD (comments aren't "code behavior"), not a parity break. Heading count matches (7/7).

## Sources

`raw/courses/07-enterprise-decision-systems.md`
