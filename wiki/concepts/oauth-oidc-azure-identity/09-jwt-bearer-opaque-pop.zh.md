# 09. JWT、Bearer、Opaque 与 PoP

English: [09-jwt-bearer-opaque-pop.md](09-jwt-bearer-opaque-pop.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- JWT 是格式；Bearer 是使用模型；Opaque 需 introspection；PoP 绑定发送方（§6）。
- 即便 Access Token 是 JWT 形，Client 也应当不透明凭证。

## 缺失

- XingAI 公共库未见 DPoP/mTLS 实验（unknown）。

## 需重新思考

- JWT Access Token 诱使不安全的客户端解析。

## 争议

- 网关 opaque vs 本地 JWT——架构分叉。

## 待证

- 哪些公共 XingAI MCP 用 opaque / JWT。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
