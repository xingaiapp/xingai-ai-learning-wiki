# 13. Azure 应用注册

English: [13-azure-app-registration.md](13-azure-app-registration.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- Client 应用注册 vs API `Expose an API`（URI、scopes、app roles）（§11）。
- 同意链：API 定义 scope → Client 申请 → 令牌 `scp`。

## 缺失

- 证书 vs 密钥运维指导偏薄。

## 需重新思考

- SPA+API 共用一个注册——常见捷径但糊掉 audience。

## 争议

- MCP resource audience 命名相对 `api://claims-api` 示例。

## 待证

- 本次无 Entra 控制台 UX 图。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
