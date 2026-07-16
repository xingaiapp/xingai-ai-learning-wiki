# 13. Azure App Registration

Chinese: [13-azure-app-registration.zh.md](13-azure-app-registration.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Client app registration vs API app `Expose an API` (Application ID URI, scopes, app roles) (§11).
- Consent chain: API defines scope → client requests → token `scp` claim.

## Missing

- Certificate vs secret operational guidance thin.

## Rethink

- Single app registration for SPA+API — common shortcut that muddies audiences.

## Debate

- How MCP resource audience should be named vs `api://claims-api` examples.

## Needs evidence

- Screenshots of Entra blades (no UX asset this ingest).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
