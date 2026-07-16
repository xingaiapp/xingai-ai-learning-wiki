# 18. Session and Cookie Security

Chinese: [18-session-and-cookie-security.zh.md](18-session-and-cookie-security.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- After ID Token verification, app creates session cookie (Secure, HttpOnly, SameSite) — cookie is not an Access Token (§16).

## Missing

- Session fixation / rotation guidance light.

## Rethink

- Storing Access Token in localStorage — anti-pattern vs outline.

## Debate

- BFF pattern vs SPA token handling for XingAI Next apps.

## Needs evidence

- Cookie flags actually used in each product (code audit).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
