# Concept: Agent Governance And MCP

Chinese: [agent-governance-and-mcp.zh.md](agent-governance-and-mcp.zh.md)

Two related but distinct control questions that recur across courses and public POCs:

1. **Can this caller invoke this tool at all?** — OAuth scope / MCP authorization ([Course 04](../courses/04-mcp-interoperability.md)).
2. **Is this specific action, right now, allowed?** — a business-rule policy layer independent of scope (dollar caps, claim-type allowlists, read-vs-write authority) ([Course 03](../courses/03-tool-use-ai-agents.md)'s `Validate → Approve/Execute` split).

This "two-wall" split is not academic —
[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.md)
(ADR-006) was written because scope alone can't express
"this partner may not authorize settlements over $10,000." The
[Third-Party MCP Access](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)
design article generalizes the same reasoning into an API-key-vs-OAuth decision framework.
[claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.md) is the complementary
coverage-first MCP surface (auth deferred).

[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.md) implements a
simplified MCP data boundary today (static service token; scopes pre-named for
a later Authorization Server) and flags prompt-injection on free-text claim
fields in `PRODUCTION-READINESS.md` — untrusted content steering an agent
decision, the same failure class Course 03 names for tool descriptions.

## Connects to

- [Course 03](../courses/03-tool-use-ai-agents.md), [Course 04](../courses/04-mcp-interoperability.md), [Course 05](../courses/05-agent-runtime-multi-agent.md)
- [Concept: Decision Ledger pattern](decision-ledger-pattern.md) — governance verdicts belong in ledger rows when you need after-the-fact proof.
- Street “enterprise agent” posters often bury auth under Platform Foundation — contrast [Enterprise agent architecture vs XingAI](../syntheses/enterprise-agent-architecture-vs-xingai.md) (Missing: two-wall auth; Rethink: guardrails after RESPOND vs gate before ACT).
- “MCP vs RAG vs Skills” as mutually exclusive columns — contrast [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.md) and the procedure-vs-capability blog post.

## Sources

`raw/courses/03-tool-use-ai-agents/README.md`, `raw/courses/04-mcp-interoperability/README.md`, `raw/pocs/claims-mcp-oauth-poc/`, `raw/pocs/claims-workflow-v2-poc/`, `raw/pocs/docs/adr/006-claims-mcp-oauth-poc-real-auth.md`, `raw/xingai-enterprise-ai-design/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md`
