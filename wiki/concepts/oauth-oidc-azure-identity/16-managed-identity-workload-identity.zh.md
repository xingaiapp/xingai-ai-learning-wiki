# 16. 托管标识与工作负载标识

English: [16-managed-identity-workload-identity.md](16-managed-identity-workload-identity.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- Managed Identity = 服务身份访问 Azure 资源；不是最终用户（§14）。
- 链：用户令牌进 API；API 用 MI 访问 SQL/Key Vault/Storage。

## 缺失

- 大纲对 Workload Identity Federation 偏少。

## 需重新思考

- 日志里把 MI 当成「用户已认证」。

## 争议

- 开源 POC 本地替代 MI 的方式。

## 待证

- XingAI Fly/Azure 服务是否使用 MI（需部署文档）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
