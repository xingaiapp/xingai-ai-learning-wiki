# 05. ID Token 与 Access Token

English: [05-id-token-vs-access-token.md](05-id-token-vs-access-token.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- ID Token → Client；Access Token → API/MCP（§2.1）。API 验过令牌仍要业务授权。
- 设计文讨论第三方 MCP 的 API Key vs OAuth（[链接](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)）。

## 缺失

- Claims 表偏 Entra；其他 IdP 字段不同。

## 需重新思考

- 前端解析 Access Token 做 UI 授权——大纲禁止，演示仍常见。

## 争议

- MCP 是否曾接受 ID Token 作 Bearer？大纲否；需核验公共网关。

## 待证

- 各 POC 选 introspection 还是本地 JWT 校验。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
