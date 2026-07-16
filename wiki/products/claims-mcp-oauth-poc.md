# Product: claims-mcp-oauth-poc

Chinese: [claims-mcp-oauth-poc.zh.md](claims-mcp-oauth-poc.zh.md)

**Repo:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **Status:** Runnable · Phase 1

The public proof that "MCP auth" is not a middleware checkbox: OAuth 2.1 + mandatory PKCE, `.well-known` discovery, short-lived audience-scoped JWTs, Review→Adjudicate (no one-step binding write), and two walls — scope answers "can this caller invoke this tool," settlement policy answers "may *this* claim at *this* amount go through."

## What the README won't emphasize

It is deliberately **narrow**. Four-ish tools beat eighteen when the experiment is cryptography and policy walls. That is why it sits opposite [claims-partner-api-mcp-poc](claims-partner-api-mcp-poc.md) (coverage-first, auth deferred). Treating either as "the" claims MCP design collapses the matrix — see [Claims POC family](../syntheses/claims-poc-family-tradeoffs.md).

Wall #2 is the Course 03 idea (`Validate → Approve` for consequential actions) implemented as code in `policies.py`, not as prompt text. Scope alone cannot express dollar caps; that is the whole point of ADR-006.

## Tension with workflow-v2

[claims-workflow-v2-poc](claims-workflow-v2-poc.md) still uses a static service token on its MCP server. Its own production-readiness list ranks "real OAuth" as priority #2 and points Phase 4 at *this* pattern. So the gap is not "nobody designed auth" — it is "the workflow POC has not wired the auth POC yet."

## Connects to

- [Concept: Agent governance and MCP](../concepts/agent-governance-and-mcp.md), [Course 03](../courses/03-tool-use-ai-agents.md), [Course 04](../courses/04-mcp-interoperability.md)
- Design: [Robinhood MCP case](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-11-mcp-in-production-robinhood-case.md), [PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)

## Sources

`raw/pocs/claims-mcp-oauth-poc/` (README, architecture, mcp-auth-deep-dive); `raw/pocs/docs/adr/006-claims-mcp-oauth-poc-real-auth.md`
