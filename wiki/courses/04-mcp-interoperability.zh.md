# 第 04 课:MCP 与互操作性

English: [04-mcp-interoperability.md](04-mcp-interoperability.md)

**先修课程:** [03](03-tool-use-ai-agents.zh.md) · **通过门槛:** 已加固的 MCP 客户端/服务端实验 · **下一课:** [05](05-agent-runtime-multi-agent.zh.md)

MCP 是受治理的能力边界,不只是一种插件格式:初始化 → 发现 → 校验 → 鉴权 →
针对目标资源授权 → 最小权限执行 → 审计。故障清单——绝不透传上游 token、绝不
接受本为其他资源签发的 token、绝不从"工具是否可见"推断出是否已授权——正是
[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md) 的双墙模型
(OAuth scope + 独立的业务规则 policy)专门为封堵这类 confused-deputy 风险
而设计的。[claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.zh.md)
则是互补的、以覆盖面优先的设计取向。

课程实验在一个已有实验(`guides/2026-07-12-mcp-oauth-pkce-lab.md`)的基础上
扩展,而不是从零搭建——这与本 wiki"不重新推导已经存在的东西"的原则一致。

## 关联

- [概念:Agent 治理与 MCP](../concepts/agent-governance-and-mcp.zh.md)
- [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md)、
  [claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.zh.md)、
  [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)
- [OAuth / OIDC / Azure Identity 目录](../concepts/oauth-oidc-azure-identity/00-overview.zh.md)
- MCP(工具) vs A2A(对等体) vs ACP 谱系:[mcp-vs-a2a-vs-acp](../syntheses/mcp-vs-a2a-vs-acp.zh.md)。
- 虚假的"MCP vs Skills vs RAG"互斥说法:
  [mcp-vs-rag-vs-skills](../syntheses/mcp-vs-rag-vs-skills.zh.md);
  程序 vs 能力的区分见该页引用的 tech-blog 文章。
- 周报地图（无状态/长任务 MCP、持久工作流）：[ai-architecture-digest-2026-07-17](../syntheses/ai-architecture-digest-2026-07-17.zh.md)。

## 已验证

`modelcontextprotocol.io/specification/2025-11-25/basic/authorization` 与
`a2a-protocol.org/latest/specification/` 均已确认为真实来源,于 2026-07-16
通过网络搜索解析到一手来源。ZH 版本于 2026-07-16 摄入:Python 代码逐字节
一致,标题数一致(7/7)。

## 来源

`raw/courses/04-mcp-interoperability/README.md`
