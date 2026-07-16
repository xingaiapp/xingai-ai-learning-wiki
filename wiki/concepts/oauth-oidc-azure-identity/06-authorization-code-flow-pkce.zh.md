# 06. 授权码流 + PKCE

English: [06-authorization-code-flow-pkce.md](06-authorization-code-flow-pkce.md)

属于 [OAuth / OIDC / Azure Identity 目录](00-overview.zh.md)。  
**主要教学来源：** [课程 10 · 模块 06](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.zh.md) · [主页](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/README.zh.md)

## 教学要点（来自课程 10）

- **是什么：** 
- **为什么：** 
- **谁：** 
- **何时：** 
- **何处：** 
- **怎么做：** 

### 图示

```mermaid
sequenceDiagram
    participant C as Client
    participant AS as AS
    C->>C: code_verifier + challenge
    C->>AS: authorize + challenge
    AS-->>C: authorization code
    C->>AS: code + verifier
    AS-->>C: tokens
```

### 最小校验

```python
import hashlib, base64, secrets
verifier = secrets.token_urlsafe(32)
digest = hashlib.sha256(verifier.encode()).digest()
challenge = base64.urlsafe_b64encode(digest).rstrip(b"=").decode()
assert len(verifier) >= 32 and challenge != verifier
```

### 故障模式（课程）

- 把登录成功当成授权通过。
- 把错误类型的令牌发给错误的受众。
- 跳过 PKCE、state、nonce 或精确回调校验。
- 只把业务策略写在提示词或 UI 可见性里。

## Known（已知）

- 课程 10 模块 06 给出上文词汇、图示与失败关闭校验（`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.zh.md`；公开：[模块](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.zh.md)）。
- 可动手路径：[PKCE MCP 实验](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md) · [认证深读](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-auth-deep-dive.md)。
- 交叉：[agent-governance-and-mcp](../agent-governance-and-mcp.zh.md) · [课程 04](../../courses/04-mcp-interoperability.zh.md) · [课程 10 wiki](../../courses/10-oauth-oidc-azure-identity.zh.md) · [claims-mcp-oauth-poc](../../products/claims-mcp-oauth-poc.md)。

## Missing（缺失）

- 课程模块保持精简——本 wiki 页无「Authorization Code Flow with PKCE」的真实令牌追踪。

## Rethink（重思）

- 协议素养须先于厂商 SDK；MSAL/Entra 映射在模块 12–21。

## Debate（争议）

- OAuth 2.1 / resource indicator 深度应落在本课，还是课程 04 MCP 实验。

## Needs evidence（待证）

- 端到端练习本模块负向测试的公开 POC 证据。

## Sources（来源）

- 课程：[授权码流 + PKCE](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.zh.md) · [EN](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.md)
- 快照：`raw/xingai-enterprise-ai-design/courses/10-oauth-oidc-azure-identity/modules/06-authorization-code-flow-pkce.zh.md`
- 实验：[OAuth 2.1 + PKCE MCP](https://github.com/xingaiapp/xingai-enterprise-ai-design/blob/main/guides/2026-07-12-mcp-oauth-pkce-lab.zh.md)
