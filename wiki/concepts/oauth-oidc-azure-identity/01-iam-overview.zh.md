# 01. 身份与访问管理总览

English: [01-iam-overview.md](01-iam-overview.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。

本页打开偏 Azure 的 IAM 学习轨道。按下方目录阅读；不要把 Azure 服务名当成「XingAI 已实现」。

## 已知

- 大纲 §1–§23：OAuth=API 授权，OIDC=登录身份；最终规则见 `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`。
- XingAI 已区分墙 #1（OAuth scope）与墙 #2（业务策略）——见 [agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)。

## 缺失

- 大纲偏 Azure 教学；公共 POC 多用自建/演示 IdP，与 Entra 对照未完成。
- 本快照无生产 Entra 租户证据。

## 需重新思考

- 把「接了 OAuth」当成「MCP 已安全」会压扁 Course 04 的混淆代理教训——scope ≠ 理赔策略（[博文](https://github.com/xingaiapp/xingai-tech-blog/blob/main/posts/2026-07-13-mcp-auth-scope-is-not-policy-second-wall.md)）。

## 争议

- XingAI 面向消费者应用用 Workforce Entra 还是 External ID —— 产品选型未决。

## 待证

- 是否有 XingAI 产品在生产使用 Entra External ID（需公开部署说明）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
