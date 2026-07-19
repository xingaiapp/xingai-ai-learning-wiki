# Concept: Loop Engineering

Chinese: [loop-engineering.zh.md](loop-engineering.zh.md)

Explicit loops with state, stop conditions, and evaluable steps — treating agent/LLM work as an engineered control loop, not an open-ended chat. Taught across design articles, engineering-system patterns, and tech-blog deep dives; advanced track continues it in `deep-enterprise-ai`.

XingAI map (three layers + hard stops — not an infinite agent kit):

![XingAI Loop Engineering — Context / Harness / Loop](../assets/ux/loop-engineering-vs-xingai/xingai-map.png)

Disambiguation vs Cobus Greyling OSS toolkit poster: [loop-engineering-toolkit-vs-xingai](../syntheses/loop-engineering-toolkit-vs-xingai.md).

## Known

- Public pattern separates **Context | Harness | Loop**; Loop requires entry, body, programmatic stop (max iterations, budget, no-progress, timeout, HITL). Cite `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`.
- Pedagogy: move from single prompts to durable loops — design articles + tech blog (see Sources).
- Runnable graphs in public POCs: [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md), [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.md).

## Missing

- Many marketing “loop” diagrams omit stop conditions and MCP walls (see toolkit synthesis).
- Decision ledger as a required loop artifact is taught elsewhere ([decision ledger](decision-ledger-pattern.md)) but not always drawn on loop posters.

## Rethink

- “Loop” in npm README marketing ≠ XingAI three-layer control loop — keep names separate when citing.
- Stop conditions in the prompt alone fail the pattern’s own test (agent runs forever).

## Debate

- How much of Harness (worktrees, schedulers) belongs in the Loop layer diagram vs runtime ops docs?

## Needs evidence

- Whether any XingAI public product currently scores “Loop Ready” in the Cobus toolkit sense — not claimed here.

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
- Toolkit poster critique: [loop-engineering-toolkit-vs-xingai](../syntheses/loop-engineering-toolkit-vs-xingai.md)

## Sources

`raw/xingai-enterprise-ai-design/articles/2026-07-03-beyond-prompt-engineering-loop-engineering.md`, `raw/xingai-engineering-system/patterns/loop-engineering-three-layer.md`, `raw/pocs/docs/adr/005-loop-engineering-platform-layers.md`, `raw/xingai-tech-blog/posts/2026-07-03-loop-engineering-enterprise-ai-runtime.md`, `raw/external/2026-07-19-loop-engineering-toolkit-poster/`
