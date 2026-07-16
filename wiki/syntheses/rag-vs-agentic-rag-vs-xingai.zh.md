# 综合:RAG vs Agentic RAG(海报)vs XingAI 地图

English: [rag-vs-agentic-rag-vs-xingai.md](rag-vs-agentic-rag-vs-xingai.md)

三栏架构海报(用户于 2026-07-16 摄入,**无可读署名**):**RAG**(线性 embed→向量库→增强→LLM)·**AI Agent**(记忆/规划/工具接数据源)·**Multi-Agent RAG**(聚合器 + 专家经 **MCP Servers** 接本地 / 搜索 / 云)。

资产:`raw/external/2026-07-16-rag-vs-agentic-rag/`。

相关营销切法(对等栏,不是阶梯):[MCP vs RAG vs Skills](mcp-vs-rag-vs-skills.zh.md)。

## 已验证(Known)

- 面板结构(视觉,`verified: partial`):见 `notes.md`。标题写「vs」;正文是三种架构。Multi-Agent 面板点名 MCP Servers、ReAct、CoT、短/长记忆;厂商 logo(Kagi、AWS、Azure)作为示例后端出现。
- XingAI 公开教学已覆盖这些面板勾勒的*工作*:
  - 受治理 RAG 流水线(ACL 先于排序、引用、评测)→ [第 02 课](../courses/02-rag-knowledge-systems.zh.md)
  - 工具使用 / 规划 / 审批 → [第 03 课](../courses/03-tool-use-ai-agents.zh.md)
  - MCP 作为能力边界 → [第 04 课](../courses/04-mcp-interoperability.zh.md)、[agent 治理](../concepts/agent-governance-and-mcp.zh.md)
  - 多 agent 运行时 / 何时加 agent → [第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)
- 公开 POC 是组合而不是选一个面板:[claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)(supervisor + 专家 + RAG + HITL)、[claims-workflow-v2](../products/claims-workflow-v2-poc.zh.md)(编排 + 双路径 LLM + 轻 RAG,小保单语料上常**没有**向量库)、[claims-mcp-oauth](../products/claims-mcp-oauth-poc.zh.md) / [partner-api](../products/claims-partner-api-mcp-poc.zh.md)(MCP 表面)——[族](claims-poc-family-tradeoffs.zh.md)。

## 缺失(海报上)

- **RAG 质量 / 安全(第 02 课):** 排序前的文档 ACL、引用忠实度评测、投毒/过时索引、「引用形态」的无支撑断言——标准 RAG 面板只有快乐路径。
- **MCP 上的鉴权 / 双墙策略** —— Multi-Agent 面板画出连到本地/搜索/云的 MCP Servers,没有 OAuth、scope、Review→Execute 或结算上限([oauth POC](../products/claims-mcp-oauth-poc.zh.md))。
- **Human-in-the-loop / 决策台账 / PRODUCTION-READINESS** —— 三栏都没有。
- **停止条件 / 成本 / 缓存优先双路径** —— agent 面板隐含循环;没有停下/升级或 [cache-first](../concepts/cache-first-llm-architecture.zh.md)。
- **何时不用向量库** —— 第 02 课 / workflow-v2 第 2 阶段对小而稳定语料的指引不可见;标准 RAG 默认有 Vector Db。

## 再想(Rethink)

- **「vs」又是错误连词。** XingAI POC 把检索叠进 agent,把 MCP 放在 RAG 旁边。有用的问题是在一个系统里需要哪块面板的*工作*,不是你「属于」哪个框。
- **中间面板标题是「AI Agent」,不是「Agentic RAG」。** Tools↔Data Sources 而没有显式 retrieve→ground→cite 路径,可以只是普通工具调用。没有落地/引用纪律就叫 Agentic RAG,会糊掉第 02 课与第 03 课。
- **Multi-Agent RAG ≈ 第 05 课聚合器故事 + 第 04 课管道** —— 与 [claims-multiagent-rag](../products/claims-multiagent-rag-poc.zh.md) 和 workflow-v2 的 supervisor 最同韵——但海报卖自主;公开 POC 文档卖升级与延后鉴权。
- **MCP 作为所有专家的唯一数据平面** 比 MCP|RAG|Skills 对等栏海报更贴近 XingAI「能力边界」教学——没有墙仍然不安全。

## 辩论(留开)

| 分叉 | 海报倾向 | XingAI 公开倾向 | 状态 |
|---|---|---|---|
| 标准 RAG / agent / multi-agent RAG 是备选项吗? | 标题「vs」 | 同一产品内组合 | 偏好组合 |
| RAG 必须等于 Vector Db 吗? | 标准面板是 | 第 02 课 / workflow-v2:不一定 | 命名开放;语料规模决定 |
| 「Agentic RAG」是真类别还是营销? | 中+下栏 | 拆开:检索纪律(02) vs agent 控制(03–05) | 词汇开放 |
| MCP 服务器坐在哪? | 仅 Multi-Agent 面板 | 第 04 课 + claims MCP POC 也服务单 agent 工具 | 画法约定开放 |

## 需要证据

- 本图的规范 URL / 作者。
- 是否有任何 XingAI **公开**课程把「Agentic RAG」用作正式术语(不单凭快照索引断言)。
- 角落若有淡印是否标识发布方——在可读之前当作未知。

## 怎么用

- 第 02–05 课面试探针:「去掉『vs』重画;在 Multi-Agent 面板上标出 ACL、引用评测与 MCP 鉴权。」
- 与 [mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.zh.md) 配对:那张把 RAG 当对等架构;这张把 RAG 当通向 agent 的成熟度阶梯。
- **不要**把厂商 logo(Kagi/AWS/Azure)当成 XingAI 产品选型。

## 来源

`raw/external/2026-07-16-rag-vs-agentic-rag/`(SOURCE.md、notes.md、assets/);第 02–05 课;claims POC 族;[mcp-vs-rag-vs-skills](mcp-vs-rag-vs-skills.zh.md)。图:`verified: partial`。
