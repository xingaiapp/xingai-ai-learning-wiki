# 08. OAuth 令牌类型

English: [08-oauth-token-types.md](08-oauth-token-types.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。  
**主要教学来源：** [课程 10 · 模块 08](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.zh.md) · [主页](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)

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
    Code[Authorization code short-lived] --> AT[Access token API use]
    Code --> RT[Refresh token rotation]
    Code --> IDT[ID token client identity]
```

### 最小校验

```python
TOKEN_RULES = {
  "authorization_code": {"store": "none", "ttl": "minutes"},
  "access_token": {"store": "memory", "ttl": "short"},
  "refresh_token": {"store": "http_only_cookie_or_secure_store", "ttl": "long+rotate"},
  "id_token": {"store": "client_session", "ttl": "short"},
}
assert TOKEN_RULES["refresh_token"]["store"].startswith("http_only")
```

### 故障模式（课程）

- 把登录成功当成授权通过。
- 把错误类型的令牌发给错误的受众。
- 跳过 PKCE、state、nonce 或精确回调校验。
- 只把业务策略写在提示词或 UI 可见性里。

## Known（已知）

- 课程 10 模块 08 给出上文词汇、图示与失败关闭校验（`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.zh.md`；公开：[模块](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.zh.md)）。
- 可动手路径：[PKCE MCP 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md) · [认证深读](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md)。
- 交叉：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) · [课程 04](../../courses/04-mcp-interoperability.zh.md) · [课程 10 wiki](../../courses/10-oauth-oidc-azure-identity.zh.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md)。

## Missing（缺失）

- 课程模块保持精简——本 wiki 页无「OAuth Token Types」的真实令牌追踪。

## Rethink（重思）

- 协议素养须先于厂商 SDK；MSAL/Entra 映射在模块 12–21。

## Debate（争议）

- OAuth 2.1 / resource indicator 深度应落在本课，还是课程 04 MCP 实验。

## Needs evidence（待证）

- 端到端练习本模块负向测试的公开 POC 证据。

## Sources（来源）

- 课程：[OAuth 令牌类型](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.zh.md) · [EN](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.md)
- 快照：`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/08-oauth-token-types.zh.md`
- 实验：[OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)
