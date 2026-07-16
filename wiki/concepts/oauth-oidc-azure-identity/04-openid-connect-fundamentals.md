# 04. OpenID Connect Fundamentals

Chinese: [04-openid-connect-fundamentals.zh.md](04-openid-connect-fundamentals.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- OIDC = OAuth 2.0 + standardized identity via `scope=openid` and ID Token (§1.3).
- Client verifies ID Token then creates its own session — not the Access Token.

## Missing

- Outline does not detail UserInfo endpoint privacy/minimization.

## Rethink

- Using Access Token as “login proof” in SPAs — common anti-pattern vs outline.

## Debate

- OIDC session logout / front-channel vs back-channel — not covered here.

## Needs evidence

- Whether XingAI marketing apps use OIDC libraries vs NextAuth Google provider only (product-specific).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
