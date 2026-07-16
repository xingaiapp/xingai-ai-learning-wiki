# 综合:Claims POC 族 —— 鉴权 vs 覆盖 vs 工作流

English: [claims-poc-family-tradeoffs.md](claims-poc-family-tradeoffs.md)

四个公开 POC 坐在同一个仓库里,看起来像「更多理赔 demo」。它们不是。按故意矩阵来读:

| 轴 | 窄工具 + 真实鉴权 | 广工具 + 延后鉴权 | 多 agent 工作流 + 审计 |
|---|---|---|---|
| **鉴权优先** | [claims-mcp-oauth-poc](../products/claims-mcp-oauth-poc.zh.md) | — | [claims-workflow-v2](../products/claims-workflow-v2-poc.zh.md) 今天用*静态*服务令牌;ADR-009 第 4 阶段指向 oauth POC |
| **覆盖优先** | — | [claims-partner-api-mcp-poc](../products/claims-partner-api-mcp-poc.zh.md)(约 18 个工具) | workflow-v2 的 MCP 表面故意很小(政策/台账/支付) |
| **编排** | 脚本化演示客户端,不是 supervisor | 假定合作伙伴 agent 在外部 | [multi-agent-lab](../products/multi-agent-lab.zh.md) → [claims-multiagent-rag](../products/claims-multiagent-rag-poc.zh.md) → workflow-v2(领域保真度递增) |

## 第 04 课不会大声说的权衡

[第 04 课](../courses/04-mcp-interoperability.zh.md)教受治理的能力协商。公开 POC 把它拆成两个实验,你不该在脑子里合并:

1. **oauth POC** —— 在*极小*工具表面上证明 OAuth 2.1 + PKCE + 双墙(scope ≠ 结算策略)。鉴权就是产品。
2. **partner-api POC** —— 证明 OpenAPI→MCP 全覆盖,好伙伴不会卡在「再多一个工具」。鉴权明确延后(ADR-007)。

把它们合起来是*下一步*工程动作,不是起点。ADR-009 第 4 阶段对 workflow-v2,就是把这组合瞄准工作流的 `mcp_server/`。

## 工作流谱系(同一领域,不同问题)

- **multi-agent-lab** —— 平台形态(orchestrator、专家、SQLite 轨迹),假工具。几乎没有保险语义。
- **claims-multiagent-rag** —— 保险语义 + RAG 引用 + human-in-the-loop。决策*助手*,不是自动裁决。
- **claims-workflow-v2** —— 修一张具体的坏信息图(拆分欺诈、阶段感知恢复、台账)。再加深到 MCP + 双路径 LLM + LangGraph。最接近「第 05–07 课作业且带测试上线」。

若只读一个 POC README,你会错过:workflow-v2 的生产就绪缺口 #2(真实 OAuth)已经作为*兄弟 POC*解决了,不是缺想象力。

## Event-bus 作为另类

[event-bus-ai-review](../products/event-bus-ai-review.zh.md) 仅设计、事件驱动。它回答不同的控制平面问题:同步 supervisor 图(lab / RAG / workflow-v2) vs 解耦订阅方做 AI 审核 + 合规 + 人工审批。不要硬塞进上面的 MCP 矩阵。

## 怎么用本页

问「为了 X 该学哪个 POC?」时:

- MCP 鉴权 / confused deputy → oauth POC + 第 04 课 + 第三方 MCP 文章
- MCP 工具膨胀 / OpenAPI 包装 → partner-api POC + coverage-vs-workflow 文章
- 多 agent + RAG + 引用 → claims-multiagent-rag + 第 02/05 课
- 决策台账 + 生产缺口 → workflow-v2 + 第 06/07 课 + [PRODUCTION-READINESS](../products/claims-workflow-v2-poc.zh.md#production-readinessmd--第-06-课案例)

## 来源

对 `raw/pocs/*/README.md`、`raw/pocs/docs/adr/006-*.md`、`007-*.md`、`008-*.md`、`009-*.md` 与第 04 课的会话综合——不是任何单份 README 的副本。
