# 26. 完整 Azure 参考架构

English: [26-complete-azure-reference-architecture.md](26-complete-azure-reference-architecture.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。  
**主要教学来源：** [课程 10 · 模块 26](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md) · [主页](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)

## 教学要点（来自课程 10）

- **是什么：** 
- **为什么：** 
- **谁：** 
- **何时：** 
- **何处：** 
- **怎么做：** 

### 图示

```mermaid
flowchart TB
    User --> MSAL[MSAL app]
    MSAL --> Entra[Entra ID / External ID]
    MSAL --> APIM[APIM JWT validate]
    APIM --> API[API + business policy]
    API --> MI[Managed identity]
    MI --> Azure[Key Vault / data]
    Host[MCP Host] --> Entra
    Host --> MCP[MCP Server resource]
    MCP --> Policy[Scope + business policy + ledger]
```

### 最小校验

```python
components = ["entra", "msal", "apim_optional", "api_policy", "managed_identity", "mcp_two_wall"]
assert "mcp_two_wall" in components and "apim_optional" in components
```

### 故障模式（课程）

- 把登录成功当成授权通过。
- 把错误类型的令牌发给错误的受众。
- 跳过 PKCE、state、nonce 或精确回调校验。
- 只把业务策略写在提示词或 UI 可见性里。

## Known（已知）

- 课程 10 模块 26 给出上文词汇、图示与失败关闭校验（`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md`；公开：[模块](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md)）。
- 可动手路径：[PKCE MCP 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md) · [认证深读](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md)。
- 交叉：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) · [课程 04](../../courses/04-mcp-interoperability.zh.md) · [课程 10 wiki](../../courses/10-oauth-oidc-azure-identity.zh.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md)。

## Missing（缺失）

- 「Complete Azure Reference Architecture」的运营深度停留在检查清单；课程 10 无 SIEM/手册工件。

## Rethink（重思）

- MCP 双墙 + 决策台账是 XingAI 的持久审计叙事——单靠 Azure APIM 不够。

## Debate（争议）

- Azure 参考架构，还是面向 XingAI demo 的可移植 Fly/Vercel 对照图。

## Needs evidence（待证）

- 与真实 XingAI 状态/API 拓扑匹配的公开部署图。

## Sources（来源）

- 课程：[完整 Azure 参考架构](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md) · [EN](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.md)
- 快照：`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/26-complete-azure-reference-architecture.zh.md`
- 实验：[OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)
