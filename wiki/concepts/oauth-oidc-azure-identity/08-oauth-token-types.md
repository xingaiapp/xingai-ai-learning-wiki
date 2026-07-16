# 08. OAuth Token Types

Chinese: [08-oauth-token-types.zh.md](08-oauth-token-types.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Four values: Authorization Code, ID Token, Access Token, Refresh Token — distinct audiences (§5).
- Refresh Token must not go to APIs or logs.

## Missing

- Refresh token rotation / reuse detection not detailed.

## Rethink

- Long-lived refresh in desktop agents vs short-lived MCP access tokens — tension for AI agents.

## Debate

- Whether demo MCP servers issue refresh tokens at all.

## Needs evidence

- Token TTL numbers in public POCs.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
