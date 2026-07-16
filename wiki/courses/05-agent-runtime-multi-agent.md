# Course 05: Agent Runtime And Multi-Agent Systems

**Prerequisite:** [04](04-mcp-interoperability.md) · **Gate:** recoverable stateful workflow · **Next:** [06](06-production-ai-engineering.md)

Durable execution and the multi-agent decision rule that matters most: "add agents only for real specialization, trust separation, or parallelism" — not because more agents feels more sophisticated. The explicit state machine (`ALLOWED` transition table, illegal transitions raise) is the same discipline `claims-workflow-v2-poc`'s Case Resolution Router uses — resume at a specific stage, never guess your way back to intake.

This course's honest caveat about checkpointing ("more agents increase nondeterminism... prevent cyclic delegation, duplicate side effects, stale checkpoints") is worth reading next to `claims-workflow-v2-poc`'s own admission (ADR-009 "Phase 3 implementation note") that its LangGraph supervisor rebuilds a fresh graph per call instead of using real checkpoint/`thread_id` persistence — a real POC choosing the scoped-down version of exactly what this course flags as the harder, more valuable version.

## Connects to

- [Concept: Decision Ledger pattern](../concepts/decision-ledger-pattern.md) — "traces and replay" here is the same audit requirement the Decision Ledger schema satisfies across products.
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)'s `graph/supervisor_graph.py` (LangGraph, reviewed this session) — a working, deliberately-scoped-down instance of this course's durable-execution material.

## Verified

ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/05-agent-runtime-multi-agent.md`
