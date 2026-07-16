# Course 03: Tool Use And AI Agents

**Prerequisite:** [01](01-llm-application-engineering.md) · **Gate:** safe workflow/agent comparison · **Next:** [04 MCP](04-mcp-interoperability.md)

The workflow-vs-agent distinction that everything downstream depends on: a workflow follows coded paths, an agent lets a model choose steps and tools within *bounded authority*. The state diagram's `Validate → Approve (consequential) / Execute (read-only)` split is the exact shape of the two-wall authorization model this session found reused across `claims-mcp-oauth-poc`, [xingai-agent-firewall](../products/xingai-agent-firewall.md), and the [Agent Skill Assurance](../products/opportunity-radar.md) opportunity-radar pick — OAuth scope answers "can it call this at all," this course's approval gate answers "is this specific action allowed."

The failure-analysis line "tool descriptions are untrusted inputs to planning" is precisely the prompt-injection risk flagged (independently, in a different context) in `claims-workflow-v2-poc`'s `PRODUCTION-READINESS.md` for its free-text `loss_description` field — same underlying failure mode, two different courses/products converging on it.

## Connects to

- [04 MCP And Interoperability](04-mcp-interoperability.md) — MCP is one way to implement this course's "least-privilege tools behind policy and audit."
- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md)
- [xingai-agent-firewall](../products/xingai-agent-firewall.md) (reviewed 2026-07-16 as part of the Opportunity Radar Decision Card) is a real, running instance of this course's `Approve → Execute` gate, generalized to any tool call, not just one demo loop.

## Verified

ZH sibling ingested 2026-07-16: Python code byte-identical, heading count matches (7/7).

## Sources

`raw/courses/03-tool-use-ai-agents.md`
