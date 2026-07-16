# Course 07: Enterprise AI Decision Systems

Chinese: [07-enterprise-decision-systems.zh.md](07-enterprise-decision-systems.zh.md)

**Prerequisite:** [06](06-production-ai-engineering.md) · **Gate:** architecture review board defense · **Next:** [08](08-ai-leadership-cto.md)

This course *is* the Decision Ledger pattern, taught as architecture: "decision computation belongs in a worker/core domain boundary; APIs transport precomputed decisions; UIs explain them; execution remains separately authorized." The immutable `Decision` dataclass in the raw source, with `api_view()` explicitly commented `# transport only; no request-time recomputation`, is the teaching version of the same shape the public claims POC implements as `DecisionLedger`.

Course References cite a sibling-product decision-cache ADR by path; this public wiki does not ingest that private ADR.

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md) — this course is the canonical teaching version; the concept page is the cross-link index.
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s `DecisionLedger` (MCP-client-backed) — same schema instinct in a runnable public POC.
- Public pattern doc: [xingai-engineering-system](https://github.com/xingaiapp/xingai-engineering-system) Decision Ledger schema ("patterns, not libraries").

## Verified

ZH sibling ingested 2026-07-16: Python code blocks differ by exactly one thing — the `api_view()` inline comment is localized (`# transport only; no request-time recomputation` vs. `# 仅传输，不在请求时重新计算`), which is a correct localization under COURSE-STANDARD (comments aren't "code behavior"), not a parity break. Heading count matches (7/7).

## Sources

`raw/courses/07-enterprise-decision-systems/README.md`
