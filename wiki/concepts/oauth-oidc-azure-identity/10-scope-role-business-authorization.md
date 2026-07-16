# 10. Scope, Role, and Business Authorization

Chinese: [10-scope-role-business-authorization.zh.md](10-scope-role-business-authorization.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Authorization chain: token valid → scope/role → business rules → data (§7).
- This is the two-wall model in [agent-governance-and-mcp](../agent-governance-and-mcp.md); ADR-006 claims settlement policy beyond scope ([claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md)).

## Missing

- App roles vs groups vs custom claims mapping tables incomplete for Entra.

## Rethink

- Scope-only MCP demos teach the wrong ceiling — [claims-poc-family](../../syntheses/claims-poc-family-tradeoffs.md).

## Debate

- Where human approval sits relative to role checks for high-risk tools.

## Needs evidence

- Exact policy code paths in claims-mcp-oauth-poc `policies.py` on next verified read.

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
