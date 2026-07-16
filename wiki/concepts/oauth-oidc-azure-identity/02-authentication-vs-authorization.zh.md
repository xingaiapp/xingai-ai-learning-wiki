# 02. 身份认证与授权

English: [02-authentication-vs-authorization.md](02-authentication-vs-authorization.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 认证=你是谁；授权=你可以做什么——大纲 §1.1。
- MCP 工具两者都要：令牌主体 + 工具/业务允许——见 [Course 03](../../courses/03-tool-use-ai-agents.zh.md)。

## 缺失

- 大纲未单独展开 MFA/升级认证。

## 需重新思考

- 把认证缩成「有 Bearer」会抹掉 401/403 分界（§8）。

## 争议

- Agent 身份应作为一等认证主体，还是仅代表用户执行。

## 待证

- claims-workflow-v2 静态服务令牌如何映射到认证/授权词汇（产品页仅部分说明）。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
