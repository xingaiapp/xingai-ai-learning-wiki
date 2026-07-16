# 07. State, Nonce, and PKCE

Chinese: [07-state-nonce-and-pkce.zh.md](07-state-nonce-and-pkce.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- state protects callback/CSRF; nonce binds ID Token; PKCE binds code to client (§4).
- MSAL/libraries should generate these — outline §12 says do not hand-roll.

## Missing

- Outline does not quantify storage of state/nonce (cookie vs session server).

## Rethink

- Developers conflate state and nonce — teaching table in §4.1 is the fix.

## Debate

- PKCE S256 mandatory vs plain — when plain still appears in legacy.

## Needs evidence

- claims-mcp-oauth-poc code paths for state/nonce (cite on next code-verified ingest).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
