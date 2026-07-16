# Course 03: Tool Use And AI Agents

Chinese: [03-tool-use-ai-agents.zh.md](03-tool-use-ai-agents.zh.md)

**Prerequisite:** [01](01-llm-application-engineering.md) · **Gate:** safe workflow/agent comparison · **Next:** [04 MCP](04-mcp-interoperability.md)

The workflow-vs-agent distinction that everything downstream depends on: a workflow follows coded paths, an agent lets a model choose steps and tools within *bounded authority*. The state diagram's `Validate → Approve (consequential) / Execute (read-only)` split matches the two-wall authorization model in [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md) — OAuth scope answers "can it call this at all," this course's approval gate answers "is this specific action allowed."

The failure-analysis line "tool descriptions are untrusted inputs to planning" is the same underlying failure mode flagged in `claims-workflow-v2-poc`'s `PRODUCTION-READINESS.md` for free-text `loss_description` — untrusted content steering an agent/LLM decision.

## Connects to

- [04 MCP And Interoperability](04-mcp-interoperability.md) — MCP is one way to implement this course's "least-privilege tools behind policy and audit."
- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md)
- [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md), [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md)

## Verified

ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/03-tool-use-ai-agents/README.md`
