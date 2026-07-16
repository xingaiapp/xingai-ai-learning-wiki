# 11. OIDC Discovery and JWKS

Chinese: [11-oidc-discovery-and-jwks.zh.md](11-oidc-discovery-and-jwks.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Discovery document at `/.well-known/openid-configuration`; JWKS via `jwks_uri`; validate by `kid` (§9).
- claims-mcp-oauth teaching emphasizes `.well-known` discovery in product page.

## Missing

- Key rotation runbooks / cache TTLs for JWKS not specified.

## Rethink

- Hardcoding signing keys — outline forbids; still appears in toy demos.

## Debate

- Multi-tenant issuer validation strategies.

## Needs evidence

- Live discovery JSON from a public demo AS used by XingAI POCs.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
