# 20. OAuth/OIDC 与 SAML

English: [20-oauth-oidc-vs-saml.md](20-oauth-oidc-vs-saml.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。  
**主要教学来源：** [课程 10 · 模块 20](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.zh.md) · [主页](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)

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
    SAML[SAML assertions] --> BrowserSSO[Workforce browser SSO]
    OIDC[OIDC ID Token] --> ModernApps[Modern apps]
    OAuth[OAuth access token] --> APIs[APIs / MCP]
```

### 最小校验

```python
choice = {"browser_sso_legacy": "saml_or_oidc", "api_access": "oauth", "modern_login": "oidc"}
assert choice["api_access"] == "oauth"
```

### 故障模式（课程）

- 把登录成功当成授权通过。
- 把错误类型的令牌发给错误的受众。
- 跳过 PKCE、state、nonce 或精确回调校验。
- 只把业务策略写在提示词或 UI 可见性里。

## Known（已知）

- 课程 10 模块 20 给出上文词汇、图示与失败关闭校验（`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.zh.md`；公开：[模块](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.zh.md)）。
- 可动手路径：[PKCE MCP 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md) · [认证深读](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md)。
- 交叉：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) · [课程 04](../../courses/04-mcp-interoperability.zh.md) · [课程 10 wiki](../../courses/10-oauth-oidc-azure-identity.zh.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md)。

## Missing（缺失）

- 无「OAuth/OIDC vs SAML」的真实 Entra 租户截图——课程把 Azure 当映射，而非必选云。

## Rethink（重思）

- Entra 词汇必须映射回可移植 OIDC/OAuth，否则开源 POC 会漂移。

## Debate（争议）

- 面向公开 XingAI 仓库：Entra 优先教学还是 IdP 可移植教学。

## Needs evidence（待证）

- 哪些公开 XingAI 应用实际使用该 Azure 控件（若有）。

## Sources（来源）

- 课程：[OAuth/OIDC 与 SAML](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.zh.md) · [EN](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.md)
- 快照：`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/20-oauth-oidc-vs-saml.zh.md`
- 实验：[OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)
