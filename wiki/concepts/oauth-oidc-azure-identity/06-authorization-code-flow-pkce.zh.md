# 06. 授权码流程与 PKCE

English: [06-authorization-code-flow-pkce.md](06-authorization-code-flow-pkce.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 两阶段：交互登录（code+PKCE→令牌→会话）再用 Access Token 调 API（§3）。
- 企业设计库有 [PKCE lab](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.md)。

## 缺失

- 缺少 AS 失败模式深挖（code 重用、redirect 不匹配等）。

## 需重新思考

- 大纲默认 code+PKCE，Implicit 迁移故事缺失。

## 争议

- XingAI Next.js 公有/机密客户端密钥处理。

## 待证

- 真实租户下的 Entra authorize URL 示例（raw 中无）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
