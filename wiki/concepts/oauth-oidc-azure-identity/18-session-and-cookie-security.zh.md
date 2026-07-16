# 18. 会话与 Cookie 安全

English: [18-session-and-cookie-security.md](18-session-and-cookie-security.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 验证 ID Token 后应用创建会话 Cookie（Secure/HttpOnly/SameSite）——Cookie 不是 Access Token（§16）。

## 缺失

- 会话固定/轮换指导偏少。

## 需重新思考

- Access Token 放 localStorage——相对大纲的反模式。

## 争议

- XingAI Next 应用 BFF vs SPA 持令牌。

## 待证

- 各产品实际 Cookie 标志（需代码审计）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
