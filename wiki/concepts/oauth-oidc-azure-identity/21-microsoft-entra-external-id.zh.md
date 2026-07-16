# 21. Microsoft Entra External ID

English: [21-microsoft-entra-external-id.md](21-microsoft-entra-external-id.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- External ID = 面向客户的 CIAM；External 租户与 Workforce 分离；身份属性 vs 业务库（§19）。

## 缺失

- 大纲无定价/区域约束。

## 需重新思考

- 把订单/聊天写入身份目录——§19.4 指出的边界违规。

## 争议

- XingAI 消费端选 External ID 还是 Auth0/Clerk。

## 待证

- 是否有 XingAI 应用使用 External ID（待证）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
