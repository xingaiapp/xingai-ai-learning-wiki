# 06. Authorization Code Flow with PKCE

Chinese: [06-authorization-code-flow-pkce.zh.md](06-authorization-code-flow-pkce.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- Two phases: interactive login (code+PKCE→tokens→session) then API calls with Access Token (§3).
- PKCE lab guide exists in enterprise design: [PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md).

## Missing

- No diagram of AS failure modes (code reuse, redirect URI mismatch) beyond basics.

## Rethink

- Implicit flow nostalgia — outline assumes code+PKCE; good, but migration stories missing.

## Debate

- Public vs confidential client secret handling for XingAI Next.js apps.

## Needs evidence

- Live Entra authorize URL examples against a real tenant (not in raw).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
