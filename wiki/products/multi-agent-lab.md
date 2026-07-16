# Product: multi-agent-lab

Chinese: [multi-agent-lab.zh.md](multi-agent-lab.zh.md)

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status:** Runnable · Phase 1 MVP

Orchestrator + specialist agents (Research, Product, Tech, Critic), simulated MCP tools, SQLite execution traces, demo metrics. Almost no insurance domain — on purpose.

## What the README won't emphasize

This is the **platform skeleton** the claims POCs put meat on. If you jump straight to workflow-v2, every failure looks like a claims bug. Start here to see handoffs, trace rows, and agent registry without policy/settlement noise.

Trace rows (`request_id`, agent, input, output, tool, duration) are the Decision Ledger *instinct* before the shared schema in [xingai-engineering-system](xingai-engineering-system.md). Course 05's rule — add agents only for specialization, trust separation, or parallelism — is the grading rubric for whether Critic/Research splits are justified or theater.

## Connects to

- [claims-multiagent-rag-poc](claims-multiagent-rag-poc.md) (next fidelity step), [Course 05](../courses/05-agent-runtime-multi-agent.md)
- [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md)

## Sources

`raw/pocs/multi-agent-lab/README.md`, `architecture.md`
