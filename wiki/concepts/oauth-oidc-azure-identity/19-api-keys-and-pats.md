# 19. API Keys and PATs

Chinese: [19-api-keys-and-pats.zh.md](19-api-keys-and-pats.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- API keys identify calling apps / rate-limit; lack full user authz context. PATs are long-lived user tokens — prefer MI → WIF → OAuth → PAT (§17).
- Design article: API key vs OAuth for third-party MCP ([link](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)).

## Missing

- Rotation/incident response for leaked PAT not spelled out.

## Rethink

- Partner MCP demos shipping only API keys — coverage-first tradeoff ([claims-partner](../../products/claims-partner-api-mcp-poc.md)).

## Debate

- When subscription keys in APIM are acceptable edge auth.

## Needs evidence

- Leaked-key stories in XingAI public postmortems (none cited).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
