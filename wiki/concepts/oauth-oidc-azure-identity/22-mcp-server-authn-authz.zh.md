# 22. MCP Server 认证与授权

English: [22-mcp-server-authn-authz.md](22-mcp-server-authn-authz.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- MCP Server = Resource Server；MCP Client/Agent = OAuth Client（§20）。
- 检查：签名、iss、aud、exp、tid、scope/roles、工具权限、业务数据、限流、审计——绝不记录令牌。
- 对应 [Course 04](../../courses/04-mcp-interoperability.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[agent-governance](../agent-governance-and-mcp.zh.md)。

## 缺失

- 大纲 Entra→APIM→MCP 链偏理想；公共 POC 可能无 APIM。

## 需重新思考

- 只有工具白名单无业务策略 = 仅墙 #1。

## 争议

- `close_claim` 类工具人工审批位置。

## 待证

- POC 中 `get_claim`→scope 代码映射（阅读时核验）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
