# Concept: Loop Engineering

Explicit loops with state, stop conditions, and evaluable steps — treating agent/LLM work as an engineered control loop, not an open-ended chat. Taught across design articles, engineering-system patterns, and tech-blog deep dives; advanced track continues it in `deep-enterprise-ai`.

## Where it shows up (public)

| Source | Angle |
|---|---|
| Design articles (Beyond Prompt Engineering / Prompt→Loop / Anthropic getting started) | Pedagogy: move from single prompts to durable loops |
| `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md` + `micro-loop-engine.md` | Reusable pattern docs |
| ADR-005 (`raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`) | Platform layering for POCs |
| Tech blog `2026-07-03-loop-engineering-enterprise-ai-runtime.md` | Runtime framing |
| [Course 05](../courses/05-agent-runtime-multi-agent.md) / deep-enterprise-ai course 05 | Curriculum placement |

## Connects to

- [Concept: Cache / fallback LLM discipline](cache-first-llm-architecture.md) — loops still need bounded cost and fallbacks
- [Concept: Agent governance and MCP](agent-governance-and-mcp.md) — loops that call tools need walls
- Runnable graphs: [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md), [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.md)
- External reference poster (critique, not blueprint): [Enterprise agent architecture vs XingAI](../syntheses/enterprise-agent-architecture-vs-xingai.md)

## Sources

`raw/xingai-enterprise-ai-design/articles/2026-07-03-beyond-prompt-engineering-loop-engineering.md`, `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`, `raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`, `raw/xingai-tech-blog/posts/2026-07-03-loop-engineering-enterprise-ai-runtime.md`
