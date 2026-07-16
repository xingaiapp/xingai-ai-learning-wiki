# 08. OAuth 令牌类型

English: [08-oauth-token-types.md](08-oauth-token-types.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 四类：Authorization Code、ID Token、Access Token、Refresh Token——受众不同（§5）。
- Refresh Token 不得发给 API 或写入日志。

## 缺失

- 未展开 refresh rotation / 重放检测。

## 需重新思考

- 桌面 Agent 长 refresh vs MCP 短 access——AI Agent 张力。

## 争议

- 演示 MCP 是否签发 refresh。

## 待证

- 公共 POC 中的 TTL 数值。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
