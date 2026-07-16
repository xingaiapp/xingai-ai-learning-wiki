# Index

Start at [overview.md](overview.md) if you're new here. This page is the flat catalog — read it first when answering a query, then drill into specific pages.

## Courses (`wiki/courses/`)

| Page | One-line summary |
|---|---|
| [00-ai-foundations](courses/00-ai-foundations.md) | Vocabulary + mental model: models are probabilistic, not oracles. |
| [01-llm-application-engineering](courses/01-llm-application-engineering.md) | Typed boundary around a model call — the discipline everything downstream assumes. |
| [02-rag-knowledge-systems](courses/02-rag-knowledge-systems.md) | Retrieval as a governed pipeline, not a library call; ACLs before ranking. |
| [03-tool-use-ai-agents](courses/03-tool-use-ai-agents.md) | Workflow vs. agent; bounded authority; approval gates for consequential actions. |
| [04-mcp-interoperability](courses/04-mcp-interoperability.md) | MCP as a governed capability boundary; confused-deputy risks. |
| [05-agent-runtime-multi-agent](courses/05-agent-runtime-multi-agent.md) | Durable execution; add agents only for real specialization. |
| [06-production-ai-engineering](courses/06-production-ai-engineering.md) | Demo vs. production evidence; release gates; golden/adversarial eval sets. |
| [07-enterprise-decision-systems](courses/07-enterprise-decision-systems.md) | The Decision Ledger pattern, taught as architecture. |
| [08-ai-leadership-cto](courses/08-ai-leadership-cto.md) | Portfolio judgment; score, but don't let the score decide alone. |
| [09-ai-interview-mastery](courses/09-ai-interview-mastery.md) | AI-engineering interview loops (not general DS&A drills). |

## Products (`wiki/products/`)

| Page | One-line summary |
|---|---|
| [claims-workflow-v2-poc](products/claims-workflow-v2-poc.md) | Multi-agent claims pipeline; Phase 1-3 (MCP boundary, LLM+RAG, LangGraph); main public POC cross-reference. |

## Concepts (`wiki/concepts/`)

| Page | One-line summary |
|---|---|
| [5w-how-framework](concepts/5w-how-framework.md) | The pedagogical spine of every course. |
| [decision-ledger-pattern](concepts/decision-ledger-pattern.md) | Immutable, versioned decision records — Course 07 + claims POC. |
| [cache-first-llm-architecture](concepts/cache-first-llm-architecture.md) | Bound LLM cost / never make one call a single point of failure. |
| [agent-governance-and-mcp](concepts/agent-governance-and-mcp.md) | Two-wall auth: OAuth scope vs independent business-rule policy. |

## Syntheses (`wiki/syntheses/`)

| Page | One-line summary |
|---|---|
| [review-findings-2026-07-16](syntheses/review-findings-2026-07-16.md) | Courses audit trail: structure, code, links, bilingual parity. |

## Raw sources (`raw/`)

Public snapshots only (2026-07-16; private-repo trees removed 2026-07-16):

- `courses/` — 10 course READMEs (EN+ZH) + index + `COURSE-STANDARD` (EN+ZH)
- `claims-workflow-v2-poc/` — README, `PRODUCTION-READINESS.md`, `architecture.md`, ADR-008, ADR-009
- `_llm-wiki-pattern.md` — the pattern doc this project follows
