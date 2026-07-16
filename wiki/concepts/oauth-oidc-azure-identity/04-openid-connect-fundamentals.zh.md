# 04. OpenID Connect 基础

English: [04-openid-connect-fundamentals.md](04-openid-connect-fundamentals.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- OIDC = OAuth 2.0 + 标准化身份（`scope=openid` + ID Token）（§1.3）。
- Client 验证 ID Token 后建立自己的 Session——不是用 Access Token。

## 缺失

- 大纲未展开 UserInfo 隐私最小化。

## 需重新思考

- SPA 把 Access Token 当「已登录证明」——相对大纲的常见反模式。

## 争议

- OIDC 登出 front/back-channel——此处未覆盖。

## 待证

- XingAI 营销应用用完整 OIDC 库还是仅 NextAuth Google（产品相关）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
