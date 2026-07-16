# 23. 日志、监控与审计

English: [23-logging-monitoring-auditing.md](23-logging-monitoring-auditing.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 记录 oid/tid/app/scopes/tool/resource/decision/policy/correlation——永不记令牌/密钥（§21）。
- 与 Decision Ledger「可追溯允许/拒绝」同向（[decision-ledger-pattern](../decision-ledger-pattern.zh.md)）。

## 缺失

- XingAI raw 无 Sentinel/App Insights 接线示例。

## 需重新思考

- 日志记下含令牌的完整 prompt——相邻泄露。

## 争议

- 何进 Decision Ledger vs SIEM。

## 待证

- 公共 POC 审计字段 vs 大纲表。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
