# 综合:企业 Agent 架构海报 vs XingAI 公开地图

English: [enterprise-agent-architecture-vs-xingai.md](enterprise-agent-architecture-vs-xingai.md)

参考架构信息图(用户于 2026-07-16 摄入,图上署名:Rishi):Inputs → Plan/Reason/Act/Respond 编排器 + 工具 → Context/Memory → Response 护栏 → LLMOps → Platform foundation。

资产:`raw/external/2026-07-16-enterprise-ai-agent-architecture/`。

本页**不是**重画那些框。它问海报主张什么、XingAI 公开课程/POC 已经覆盖什么、两边各自留下哪些洞。

## 已验证(Known)

- 海报标签(视觉读,`verified: partial`):`notes.md` 中六个区域——Inputs;编排环 PLAN→REASON→ACT→RESPOND,工具图标含 Knowledge Base 与 Payment Gateways;Memory(working / 向量 RAG / 可选 KG / episodic);Response 护栏含 Hallucination Check 与 Confidence Scoring;LLMOps(观察、LLM-as-judge 评测、诊断、闸门、发布);Platform foundation(安全、隐私、审计、FinOps、多租户等)。
- XingAI 公开课程已用不同名字教这张图的碎片:
  - Loop / 运行时 → [第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)、[loop 工程](../concepts/loop-engineering.zh.md)
  - RAG → [第 02 课](../courses/02-rag-knowledge-systems.zh.md)
  - 工具 + 审批 → [第 03 课](../courses/03-tool-use-ai-agents.zh.md)
  - 生产评测/闸门 → [第 06 课](../courses/06-production-ai-engineering.zh.md)
  - 审计 / 决策记录 → [第 07 课](../courses/07-enterprise-decision-systems.zh.md)、[决策台账](../concepts/decision-ledger-pattern.zh.md)
  - 工具鉴权墙 → [agent 治理 / MCP](../concepts/agent-governance-and-mcp.zh.md)、[claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md)
- 公开 POC 实现的是**切片**,不是整张海报:例如 [claims-workflow-v2](../products/claims-workflow-v2-poc.zh.md) 有编排 + 双路径 LLM + 台账形写入 + PRODUCTION-READINESS 缺口;[claims-multiagent-rag](../products/claims-multiagent-rag-poc.zh.md) 有 supervisor+RAG+HITL;oauth POC 在薄工具表面上有真实鉴权([族](claims-poc-family-tradeoffs.zh.md))。

## 缺失(海报上)

- **鉴权作为双墙**(OAuth scope vs 业务策略)——「Security & Access Control」是 foundation 砖;没有 Review→Execute / 结算上限模式。
- **MCP / 工具 schema / confused-deputy**——工具是图标(CRM、支付),没有能力协商。
- **决策台账 / 不利行动审计**作为一等数据产品——列了「Audit Logs」,不是带 `model_version` 的不可变决策记录。
- **Human-in-the-loop 位置**——没有显式 Approve 节点;只有响应后护栏。
- **停止条件 / 反 loop**——画了迭代环;没有「何时停下 / 升级」。
- **工具输入上的提示注入**——第 03 课 / workflow-v2 PRODUCTION-READINESS 在意这个;海报不命名。

## 缺失(XingAI 公开 POC 相对海报)

按快照 POC 文档(不声称私有产品也缺这些):

- 完整 LLMOps 环(LLM-as-judge、canary、提示/RAG 配置版本)——第 06 课有教;claims POC 多在 PRODUCTION-READINESS 列缺口,而不是把环跑起来。
- Knowledge Graph 带——海报上可选;不是快照 claims POC 的焦点。
- Platform 多租户 / FinOps 作为运行代码——foundation 砖;对任何具体 XingAI 公开 POC 当作**需要证据**。

## 再想(Rethink)

- **海报完整 ≠ 已实现架构。** 画出 Hallucination Check + FinOps 不代表它们存在;XingAI 自己的 POC 就绪文档是更好的诚实模型。
- **RESPOND 之后的护栏对 ACT 保护不足。** 若 ACT 能打到 Payment Gateways,策略必须闸住*工具调用*(第 03 课 Approve / oauth Review→Adjudicate),而不只是最终聊天字符串。
- **「Knowledge Base」当工具 vs RAG 记忆**——把检索与工具使用搅在一起,会藏住 ACL-先于-排序(第 02 课)。
- **LLM-as-a-Judge 作主评测**——第 06 课与工程模式也推金标准/对抗集与确定性闸门;仅靠裁判的评测有争议(见辩论)。

## 辩论(留开)

| 分叉 | 海报倾向 | XingAI 公开倾向 | 状态 |
|---|---|---|---|
| 鉴权 | Platform 砖 | 专用 MCP OAuth POC + 覆盖 POC 延后鉴权 | 公开 POC 中尚未合成一套系统 |
| 评测 | 突出 LLM-as-Judge | 第 06 课:指标 + 闸门;裁判可选 | 开放 |
| 记忆 | Working + 向量 + 可选 KG + episodic | POC:会话/状态 + 轻 RAG;KG 少见 | KG 是否「企业」必需仍开放 |
| 控制平面 | 同步编排器 | 还有仅设计的事件总线 POC | 开放([event-bus](../products/event-bus-ai-review.zh.md)) |

## 需要证据

- Rishi 对本图的规范 URL / 更长写记。
- 是否有任何 XingAI **公开** POC 在代码中实现命名的幻觉检查或置信度分数(此处不作断言)。
- 任何匹配本海报的系统中人工审批的确切位置(ACT 前 vs RESPOND 后)。

## 在本 wiki 怎么用

- 读第 05–06 课或新 agent POC 时的清单:哪些海报框在代码里是**已知**,哪些是**缺失**,哪些是**营销砖**。
- 与[Layers of AI vs 课程体系](layers-of-ai-vs-curriculum.zh.md)配对:那张是分类法;这张是控制平面——谁都不替代 PRODUCTION-READINESS。

## 来源

`raw/external/2026-07-16-enterprise-ai-agent-architecture/`(SOURCE.md、notes.md、assets/);上文引用的课程/POC 页;`raw/pocs/claims-workflow-v2-poc/PRODUCTION-READINESS.md` 作为缺口诚实先例。图标签:`verified: partial`。
