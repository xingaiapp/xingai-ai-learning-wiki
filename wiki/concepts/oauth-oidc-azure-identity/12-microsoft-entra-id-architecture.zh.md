# 12. Microsoft Entra ID 架构

English: [12-microsoft-entra-id-architecture.md](12-microsoft-entra-id-architecture.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- Entra 对应 IdP/AS/OP；RS 可为 API/MCP；并列出 APIM/Key Vault/MI/Sentinel（§10）。
- 这是**教学映射表**，不是声称 XingAI 已部署全栈。

## 缺失

- raw 中无完整 Entra 生产架构图。

## 需重新思考

- 把「Azure」等同「企业就绪」却无两墙策略——需重思。

## 争议

- XingAI 开源 POC 保持可移植时选 Entra 还是非微软 IdP。

## 待证

- 本次未附 Entra 应用注册 UX 截图。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
