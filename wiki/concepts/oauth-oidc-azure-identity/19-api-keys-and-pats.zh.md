# 19. API Key 与 PAT

English: [19-api-keys-and-pats.md](19-api-keys-and-pats.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- API Key 标识调用方/限流，缺完整用户授权上下文。PAT 长生命周期——优先级 MI→WIF→OAuth→PAT（§17）。
- 设计文：第三方 MCP 的 API Key vs OAuth（[链接](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/articles/2026-07-15-third-party-mcp-auth-api-key-vs-oauth2.md)）。

## 缺失

- 未写 PAT 泄露事件响应。

## 需重新思考

- 合作方 MCP 只发 API Key——覆盖优先权衡（[claims-partner](../../products/claims-partner-api-mcp-poc.zh.md)）。

## 争议

- APIM subscription key 何时可作边缘认证。

## 待证

- XingAI 公开复盘中的密钥泄露案例（未引）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
