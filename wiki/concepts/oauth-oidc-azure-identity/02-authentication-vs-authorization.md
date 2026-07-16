# 02. Authentication vs Authorization

Chinese: [02-authentication-vs-authorization.zh.md](02-authentication-vs-authorization.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Authentication = who; Authorization = what is allowed — outline §1.1 (`raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`).
- MCP tools need both: token subject + tool/business allow — [Course 03](../../courses/03-tool-use-ai-agents.md) Validate→Approve split.

## Missing

- Outline does not cover step-up / MFA as a separate authN factor story.

## Rethink

- Collapsing AuthN into “Bearer present” hides 401 vs 403 distinctions (§8).

## Debate

- Whether agent identity should be first-class AuthN subject vs acting-on-behalf-of user only.

## Needs evidence

- How claims-workflow-v2 static service token maps onto AuthN vs AuthZ vocabulary (partial in product page).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
