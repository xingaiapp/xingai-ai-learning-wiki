# 05. ID Token vs Access Token

Chinese: [05-id-token-vs-access-token.zh.md](05-id-token-vs-access-token.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- ID Token → Client; Access Token → API/MCP (§2.1). API validates access token then still runs business authorization.
- Design article frames API-key vs OAuth for third-party MCP ([link](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)).

## Missing

- Claim tables (oid/tid) are Entra-shaped; other IdPs differ.

## Rethink

- Frontend parsing Access Token for UI authz — outline forbids; many demos still do it.

## Debate

- Should MCP ever accept ID Token as Bearer? Outline says no; verify all public MCP gateways.

## Needs evidence

- Introspection vs local JWT validation choices per POC.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
