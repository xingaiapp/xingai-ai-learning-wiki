# Concept: Agent Governance And MCP

Two related but distinct control questions that recur across courses and public POCs:

1. **Can this caller invoke this tool at all?** — OAuth scope / MCP authorization ([Course 04](../courses/04-mcp-interoperability.md)).
2. **Is this specific action, right now, allowed?** — a business-rule policy layer independent of scope (dollar caps, claim-type allowlists, read-vs-write authority) ([Course 03](../courses/03-tool-use-ai-agents.md)'s `Validate → Approve/Execute` split).

This "two-wall" split is not academic —
[`claims-mcp-oauth-poc`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs)
(ADR-006 in that public repo) was written because scope alone can't express
"this partner may not authorize settlements over $10,000." The
[Third-Party MCP Access](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)
design article generalizes the same reasoning into an API-key-vs-OAuth decision framework.

[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md) implements a
simplified MCP data boundary today (static service token; scopes pre-named for
a later Authorization Server) and flags prompt-injection on free-text claim
fields in `PRODUCTION-READINESS.md` — untrusted content steering an agent
decision, the same failure class Course 03 names for tool descriptions.

## Connects to

- [Course 03](../courses/03-tool-use-ai-agents.md), [Course 04](../courses/04-mcp-interoperability.md), [Course 05](../courses/05-agent-runtime-multi-agent.md)
- [Concept: Decision Ledger pattern](decision-ledger-pattern.md) — governance verdicts belong in ledger rows when you need after-the-fact proof.

## Sources

`raw/courses/03-tool-use-ai-agents.md`, `raw/courses/04-mcp-interoperability.md`, `raw/claims-workflow-v2-poc/`; public design article and `claims-mcp-oauth-poc` ADR-006 on GitHub (not snapshotted here).
