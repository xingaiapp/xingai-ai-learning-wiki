# 25. Common Errors and Troubleshooting

Chinese: [25-common-errors-troubleshooting.zh.md](25-common-errors-troubleshooting.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- 401 = invalid credential (missing/expired/bad sig/wrong aud). 403 = valid credential, insufficient scope/role/policy (§8 + ops).
- Redirect URI mismatch, PKCE verifier fail, nonce mismatch, wrong tenant — typical OIDC failures implied by §§3–4,9.

## Missing

- No concrete error-code catalog from Entra in outline.

## Rethink

- Treating all failures as 401 hides authorization bugs.

## Debate

- How MCP transports surface HTTP status vs JSON-RPC errors.

## Needs evidence

- Captured failing authorize/token traces in public labs.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
