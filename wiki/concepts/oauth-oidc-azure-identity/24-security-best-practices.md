# 24. Security Best Practices

Chinese: [24-security-best-practices.zh.md](24-security-best-practices.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Client: Auth Code+PKCE+MSAL; no ID Token to APIs; no Access Token for SPA authz UI. API: validate + business authz + 401/403. Infra: HTTPS, MI, Key Vault, short TTL (§22).

## Missing

- Incident response / purple-team drills not listed.

## Rethink

- Checklist theater without wall #2 tests.

## Debate

- How strict for local demo POCs vs production bars.

## Needs evidence

- Compliance mapping (SOC2 etc.) — out of scope / unknown.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
