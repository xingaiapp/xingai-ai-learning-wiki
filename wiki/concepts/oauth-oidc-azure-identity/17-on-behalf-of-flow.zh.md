# 17. On-Behalf-Of 流程

English: [17-on-behalf-of-flow.md](17-on-behalf-of-flow.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- OBO：中间层用用户 Access Token 向 Entra 换下游 API 令牌（§15）。
- MCP/中间 API 调 Claims API 并保留用户审计上下文时有用。

## 缺失

- 未列 OBO 失败/同意边界。

## 需重新思考

- Agent 中间层滥用 OBO vs 服务 MI——混淆代理风险。

## 争议

- OBO vs 纯 token exchange RFC——命名争议。

## 待证

- 公共 XingAI MCP 是否实现 OBO（多半未见）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
