# 20. OAuth/OIDC 与 SAML

English: [20-oauth-oidc-vs-saml.md](20-oauth-oidc-vs-saml.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 新 API/SPA/移动/MCP → OIDC+OAuth；遗留浏览器 SSO 用 SAML（§18）。

## 缺失

- 未展开 SAML→OIDC 桥接。

## 需重新思考

- 企业强制 API Agent 只用 SAML——阻抗不匹配。

## 争议

- 人力 SSO 用 SAML、API 用 OIDC——常见混合。

## 待证

- XingAI 客户 IdP 构成（unknown）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
