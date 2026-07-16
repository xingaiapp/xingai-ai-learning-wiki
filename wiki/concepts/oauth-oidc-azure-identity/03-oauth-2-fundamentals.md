# 03. OAuth 2.0 Fundamentals

Chinese: [03-oauth-2-fundamentals.zh.md](03-oauth-2-fundamentals.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- OAuth 2.0 is an authorization framework: Client, AS, RS, scopes — not a standardized login protocol by itself (§1.2).
- [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md) implements real OAuth 2.1 + PKCE as MCP Resource Server pattern.

## Missing

- Outline omits device code / client credentials / ROPC tradeoffs in one place.

## Rethink

- Calling every “login with Google” OAuth without OIDC blurs §1.3.

## Debate

- OAuth 2.0 vs 2.1 mandatory PKCE for public clients — XingAI POCs lean 2.1; industry still mixed.

## Needs evidence

- Exact OAuth version string claimed in each public POC README (re-verify on re-ingest).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
