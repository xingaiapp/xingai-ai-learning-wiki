# 14. MSAL 集成

English: [14-msal-integration.md](14-msal-integration.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 优先 MSAL / Microsoft.Identity.Web，勿手写 PKCE/state/nonce/缓存（§12）。
- 符合安全课「不要自造密码学」纪律。

## 缺失

- 未对比 Auth.js、oidc-client-ts 等。

## 需重新思考

- 静默获取失败 / 第三方 cookie——运维缺口。

## 争议

- 可移植模板选 MSAL 还是通用 OIDC。

## 待证

- 哪些 XingAI 应用今天依赖 MSAL。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
