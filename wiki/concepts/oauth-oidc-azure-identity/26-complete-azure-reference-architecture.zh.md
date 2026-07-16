# 26. 完整 Azure 参考架构

English: [26-complete-azure-reference-architecture.md](26-complete-azure-reference-architecture.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。



## 已知

- 大纲参考故事：User/Agent → Entra → Access Token → Client → (APIM) → MCP/API；数据面 MI；密钥 Key Vault；审计 Monitor/Sentinel。
- **仅教学架构**——非已核验的 XingAI 生产拓扑。

## 缺失

- raw 无单图产物；无容量/成本模型。

## 需重新思考

- 每个 POC 都抄全栈会伤害开源教学可移植性。

## 争议

- 最小可移植子集（AS+RS+PKCE+策略）vs 完整 Azure 套件。

## 待证

- 若需要可在后续 ingest 补 Mermaid 图。

## Sources

- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/content.md`
- `raw/external/2026-07-16-oauth-oidc-azure-identity-api-security/SOURCE.md`
- 相关 wiki：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.zh.md)、[Course 04](../../courses/04-mcp-interoperability.zh.md)
