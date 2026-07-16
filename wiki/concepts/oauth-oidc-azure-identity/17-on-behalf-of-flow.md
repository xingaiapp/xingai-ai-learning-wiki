# 17. On-Behalf-Of Flow

Chinese: [17-on-behalf-of-flow.zh.md](17-on-behalf-of-flow.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- OBO: middle-tier exchanges user access token for downstream API token via Entra (§15).
- Useful when MCP/middle API must call Claims API while preserving user audit context.

## Missing

- OBO failure/consent edge cases not listed.

## Rethink

- Agent middle-tiers over-using OBO vs service MI — confused deputy risk.

## Debate

- OBO vs pure token exchange RFC — naming debate.

## Needs evidence

- Public XingAI MCP implementing OBO (unknown / likely absent).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
