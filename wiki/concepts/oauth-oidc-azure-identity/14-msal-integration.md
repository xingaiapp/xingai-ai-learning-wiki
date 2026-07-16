# 14. MSAL Integration

Chinese: [14-msal-integration.zh.md](14-msal-integration.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Prefer MSAL / Microsoft.Identity.Web over hand-rolled PKCE/state/nonce/token cache (§12).
- Aligns with “don’t invent crypto” discipline in security courses.

## Missing

- Non-Microsoft stacks (Auth.js, oidc-client-ts) not compared.

## Rethink

- Silent acquire failures / iframe third-party cookie breakage — ops gap.

## Debate

- MSAL vs generic OIDC in portable XingAI templates.

## Needs evidence

- Which XingAI apps actually depend on MSAL today.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
