# Index

Chinese: [index.zh.md](index.zh.md)

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
| [xingai-enterprise-ai-design](products/xingai-enterprise-ai-design.md) | Curriculum hub: courses, articles, guides, deep-enterprise-ai index. |
| [claims-workflow-v2-poc](products/claims-workflow-v2-poc.md) | Multi-agent claims pipeline; Phase 1–3 (MCP, LLM+RAG, LangGraph). |
| [claims-mcp-oauth-poc](products/claims-mcp-oauth-poc.md) | Real OAuth 2.1 + PKCE + two-wall auth for claims MCP. |
| [claims-partner-api-mcp-poc](products/claims-partner-api-mcp-poc.md) | Full API-coverage MCP surface; auth deferred. |
| [claims-multiagent-rag-poc](products/claims-multiagent-rag-poc.md) | Supervisor + RAG + human-in-the-loop claims demo. |
| [multi-agent-lab](products/multi-agent-lab.md) | Orchestrator + specialists + SQLite traces (platform MVP). |
| [event-bus-ai-review](products/event-bus-ai-review.md) | Event-bus AI review — architecture only, not runnable. |
| [xingai-engineering-system](products/xingai-engineering-system.md) | Public patterns (Decision Ledger, loops, cache/worker). |
| [xingai-tech-blog](products/xingai-tech-blog.md) | Selected architecture teaching posts. |

## Concepts (`wiki/concepts/`)

| Page | One-line summary |
|---|---|
| [5w-how-framework](concepts/5w-how-framework.md) | The pedagogical spine of every course. |
| [decision-ledger-pattern](concepts/decision-ledger-pattern.md) | Immutable, versioned decision records. |
| [cache-first-llm-architecture](concepts/cache-first-llm-architecture.md) | Bound LLM cost / never one call as single point of failure. |
| [agent-governance-and-mcp](concepts/agent-governance-and-mcp.md) | Two-wall auth: OAuth scope vs business-rule policy. |
| [loop-engineering](concepts/loop-engineering.md) | Explicit loops with state, stop conditions, eval. |

## Syntheses (`wiki/syntheses/`)

| Page | One-line summary |
|---|---|
| [mcp-vs-rag-vs-skills](syntheses/mcp-vs-rag-vs-skills.md) | Three-column poster vs XingAI: composition over “vs”; Skills≠MCP tools. |
| [enterprise-agent-architecture-vs-xingai](syntheses/enterprise-agent-architecture-vs-xingai.md) | Rishi enterprise-agent poster vs Courses 02–07 / claims POCs — Known gaps both ways. |
| [layers-of-ai-vs-curriculum](syntheses/layers-of-ai-vs-curriculum.md) | Popular Classical→Agentic stack mapped onto XingAI courses — and where "autonomous" oversells. |
| [claims-poc-family-tradeoffs](syntheses/claims-poc-family-tradeoffs.md) | Auth vs coverage vs workflow matrix across the four claims POCs (+ event-bus contrast). |
| [review-findings-2026-07-16](syntheses/review-findings-2026-07-16.md) | Courses audit trail: structure, code, links, bilingual parity. |

## Raw sources (`raw/`)

Public snapshots refreshed 2026-07-16 (full sync). Skip list: private repos, `xingai-ai-learning-wiki` itself, `xingai-dot-app` (P2 marketing).

- `courses/` — foundation track folders 00–09 + COURSE-STANDARD + index
- `xingai-enterprise-ai-design/` — articles, guides, assessments README, deep-enterprise-ai README
- `pocs/` — all six public POCs + repo ADRs 001–009
- `xingai-engineering-system/` — selected patterns + ADR-002
- `xingai-tech-blog/posts/` — nine architecture posts
- `external/` — ad-hoc URL/image/context packages (see `xingai-wiki-ingest`)
- `_llm-wiki-pattern.md` — LLM Wiki pattern doc
