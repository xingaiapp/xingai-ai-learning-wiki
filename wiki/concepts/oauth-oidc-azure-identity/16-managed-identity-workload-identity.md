# 16. Managed Identity and Workload Identity

Chinese: [16-managed-identity-workload-identity.zh.md](16-managed-identity-workload-identity.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Managed Identity = service identity to Azure resources; not the end-user (§14).
- Chain: user token into API; MI from API to SQL/Key Vault/Storage.

## Missing

- Workload Identity Federation details sparse in outline.

## Rethink

- Confusing MI with “user is authenticated” in logs.

## Debate

- Local-dev substitutes for MI in OSS POCs.

## Needs evidence

- Any XingAI Fly/Azure service using MI (needs deploy docs).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
