# Product: claims-multiagent-rag-poc

Chinese: [claims-multiagent-rag-poc.zh.md](claims-multiagent-rag-poc.zh.md)

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status:** Runnable · Phases 1–6

Supervisor + specialist agents + RAG-with-citations + human-in-the-loop for insurance claims. Explicitly a **decision assistant**, not auto-adjudication — uncertain or high-dollar paths escalate.

## What the README won't emphasize

It sits between [multi-agent-lab](multi-agent-lab.md) (platform shape, fake tools) and [claims-workflow-v2-poc](claims-workflow-v2-poc.md) (domain fixes + MCP + dual-path LLM + LangGraph). Same industry nouns, different homework question:

| POC | Homework question |
|---|---|
| multi-agent-lab | Can we hand off + trace without domain baggage? |
| **this** | Can specialists + RAG citations survive a claims story? |
| workflow-v2 | Can we fix a bad automation diagram *and* deepen MCP/LLM/graph? |

Course 02's "ACLs before ranking" and "citation-shaped unsupported claims" failure modes are the evaluation lens for this POC's retrieval agent. Course 05's "add agents only for real specialization" is why Intake / Retrieval / Fraud / Adjudication are separate nodes instead of one mega-prompt.

## Tension

Human-in-the-loop is a feature here; workflow-v2 pushes further toward automated stages with a Case Resolution Router for *resume*, not only escalate. Don't treat them as v1/v2 of the same binary — they optimize different risks.

## Connects to

- [Course 02](../courses/02-rag-knowledge-systems.md), [Course 05](../courses/05-agent-runtime-multi-agent.md), [Concept: Loop engineering](../concepts/loop-engineering.md)
- [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md)
- Blog writeup snapshotted: `raw/xingai-tech-blog/posts/2026-06-25-claims-multiagent-rag-supervisor-poc.md`

## Sources

`raw/pocs/claims-multiagent-rag-poc/README.md`, `architecture.md`; ADR-001/002 under `raw/pocs/docs/adr/`
