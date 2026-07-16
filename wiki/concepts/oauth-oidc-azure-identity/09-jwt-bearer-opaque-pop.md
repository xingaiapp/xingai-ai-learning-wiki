# 09. JWT, Bearer, Opaque, and PoP Tokens

Chinese: [09-jwt-bearer-opaque-pop.zh.md](09-jwt-bearer-opaque-pop.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- JWT is a format; Bearer is a usage model; Opaque needs introspection; PoP binds sender (§6).
- Client should treat Access Token as opaque credential even if JWT-shaped.

## Missing

- DPoP/mTLS examples not labbed in XingAI public repos (unknown).

## Rethink

- JWT Access Tokens encourage unsafe client-side parsing.

## Debate

- Prefer opaque at gateway vs JWT locally — architecture fork.

## Needs evidence

- Which public XingAI MCP uses opaque vs JWT access tokens.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
