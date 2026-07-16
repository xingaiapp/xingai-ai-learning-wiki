# 15. Azure API Management Security

Chinese: [15-azure-api-management-security.zh.md](15-azure-api-management-security.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- APIM can validate JWT/issuer/audience/scope, rate-limit, correlate — but APIM pass ≠ business data authorization (§13).
- Same lesson as gateway ≠ policy wall #2.

## Missing

- No APIM policy XML from a XingAI deployment in raw.

## Rethink

- Teams stopping at `<validate-jwt>` and shipping — failure mode.

## Debate

- APIM in front of MCP vs MCP validating itself — placement debate.

## Needs evidence

- Public sample APIM configs linked from XingAI (unknown).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
