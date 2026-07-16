# 10. Scope、Role 与业务授权

English: [10-scope-role-business-authorization.md](10-scope-role-business-authorization.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 授权链：令牌有效 → scope/role → 业务规则 → 数据（§7）。
- 即 [agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) 两墙模型；ADR-006 理赔策略超出 scope（[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)）。

## 缺失

- Entra App Role / 组 / 自定义 claim 映射表不完整。

## 需重新思考

- 只讲 scope 的 MCP 演示教错天花板——见 [claims-poc-family](../../syntheses/claims-poc-family-tradeoffs.zh.md)。

## 争议

- 高风险工具的人工审批相对角色检查的位置。

## 待证

- 下次核验 claims-mcp-oauth-poc `policies.py` 路径。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
