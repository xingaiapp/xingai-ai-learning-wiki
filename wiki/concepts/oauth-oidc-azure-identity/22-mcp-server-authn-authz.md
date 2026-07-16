# 22. MCP Server Authentication and Authorization

Chinese: [22-mcp-server-authn-authz.zh.md](22-mcp-server-authn-authz.zh.md)

Part of [OAuth / OIDC / Azure Identity catalog](00-overview.md).



## Known

- MCP Server = Resource Server; MCP Client/Agent = OAuth Client (§20).
- Check list: signature, iss, aud, exp, tid, scope/roles, tool permission, business data, rate limit, audit — never log tokens.
- Maps to [Course 04](../../courses/04-mcp-interoperability.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [agent-governance](../agent-governance-and-mcp.md).

## Missing

- Outline’s Entra→APIM→MCP chain is aspirational; public POC may omit APIM.

## Rethink

- Tool allowlists without business policy = wall #1 only.

## Debate

- Human approval placement for `close_claim`-class tools.

## Needs evidence

- Code-level mapping table `get_claim`→scope in POC (verify on read).

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- Related wiki: [agent-governance-and-mcp](../agent-governance-and-mcp.md), [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md), [Course 04](../../courses/04-mcp-interoperability.md)
