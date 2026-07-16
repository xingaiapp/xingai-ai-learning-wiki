# 15. Azure API Management 安全

English: [15-azure-api-management-security.md](15-azure-api-management-security.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- APIM 可验 JWT/issuer/audience/scope、限流、关联——但通过 ≠ 业务数据授权（§13）。
- 与「网关 ≠ 墙 #2」同一课。

## 缺失

- raw 无 XingAI 部署的 APIM policy XML。

## 需重新思考

- 停在 `<validate-jwt>` 就上线——失败模式。

## 争议

- APIM 挡在 MCP 前 vs MCP 自校验——放置争议。

## 待证

- XingAI 是否公开过 APIM 样例（unknown）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
