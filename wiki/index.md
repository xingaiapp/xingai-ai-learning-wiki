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
| [09-ai-interview-mastery](courses/09-ai-interview-mastery.md) | AI-engineering interview loops — distinct from xingai-learn, see boundary synthesis. |

## Products (`wiki/products/`)

| Page | One-line summary |
|---|---|
| [xingai-learn](products/xingai-learn.md) | Live coding-interview pattern trainer; 187 patterns verified accurate; one ADR-001 reference fixed. |
| [claims-workflow-v2-poc](products/claims-workflow-v2-poc.md) | Multi-agent claims pipeline; Phase 1-3 (MCP boundary, LLM+RAG, LangGraph); most cross-referenced product in this wiki. |
| [xingai-agent-firewall](products/xingai-agent-firewall.md) | Runtime tool-call governance (policy→risk score→approval→ledger); deterministic scoring, LLM judges deliberately rejected. |
| [opportunity-radar](products/opportunity-radar.md) | The issue→Decision Card→Content Pack pipeline; this session's own Agent Skill Assurance pick lives here. |

## Concepts (`wiki/concepts/`)

| Page | One-line summary |
|---|---|
| [5w-how-framework](concepts/5w-how-framework.md) | The pedagogical spine of every course. |
| [decision-ledger-pattern](concepts/decision-ledger-pattern.md) | Immutable, versioned decision records — recurs across 5+ products. |
| [cache-first-llm-architecture](concepts/cache-first-llm-architecture.md) | LLM in the request path, guarded by content-hash caches instead of a precompute worker. |
| [agent-governance-and-mcp](concepts/agent-governance-and-mcp.md) | Runtime authorization (scope) vs. pre-production certification (Skill Assurance) — a gap this session's Radar pick closes. |

## Syntheses (`wiki/syntheses/`)

| Page | One-line summary |
|---|---|
| [courses-vs-xingai-learn-boundary](syntheses/courses-vs-xingai-learn-boundary.md) | Answers "are these two things duplicates?" — no. |
| [review-findings-2026-07-16](syntheses/review-findings-2026-07-16.md) | Full audit trail: what was checked, the one real error found, and the wrong first attempt to fix it. |

## Raw sources (`raw/`)

50 files, all snapshotted 2026-07-16 (see [README.md](../README.md) for re-sync notes):

- `courses/` — 10 course READMEs (EN+ZH) + `courses/README.md` (EN+ZH) + `COURSE-STANDARD.md` (EN+ZH) = 24 files
- `xingai-learn/` — README + ADR-001 through 007 = 8 files
- `claims-workflow-v2-poc/` — README, `PRODUCTION-READINESS.md`, `architecture.md`, ADR-008, ADR-009 = 5 files
- `xingai-agent-firewall/` — README, `docs/PRD.md`, ADR-001 through 006 = 8 files
- `xingai-opportunity-radar/` — the 2026-07-16 issue, Decision Card, Content Pack, `portfolio.yaml` = 4 files
- `_llm-wiki-pattern.md` — the pattern doc this whole project is an instance of
