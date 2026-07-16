# 25. 常见错误与排障

English: [25-common-errors-troubleshooting.md](25-common-errors-troubleshooting.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 401 = 凭证无效；403 = 凭证有效但 scope/role/策略不足（§8）。
- redirect 不匹配、PKCE 失败、nonce 不匹配、错误租户——§§3–4,9 隐含。

## 缺失

- 大纲无 Entra 具体错误码表。

## 需重新思考

- 一律 401 会掩盖授权缺陷。

## 争议

- MCP 传输如何暴露 HTTP 状态 vs JSON-RPC 错误。

## 待证

- 公开实验中的失败 authorize/token 轨迹。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
