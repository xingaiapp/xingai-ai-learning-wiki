# 20. OAuth/OIDC vs SAML

Chinese: [20-oauth-oidc-vs-saml.zh.md](20-oauth-oidc-vs-saml.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- New API/SPA/mobile/MCP → OIDC+OAuth; SAML for legacy browser SSO (§18).

## Missing

- Federation bridge patterns (SAML→OIDC) not detailed.

## Rethink

- Enterprises forcing SAML-only IdP onto API agents — impedance mismatch.

## Debate

- Keep SAML for workforce SSO while APIs use OIDC — common hybrid.

## Needs evidence

- XingAI customer IdP mix (unknown).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
