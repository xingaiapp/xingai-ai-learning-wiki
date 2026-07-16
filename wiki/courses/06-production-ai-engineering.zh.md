# 第 06 课:生产级 AI 工程

English: [06-production-ai-engineering.md](06-production-ai-engineering.md)

**先修课程:** [05](05-agent-runtime-multi-agent.zh.md) · **通过门槛:** 生产就绪评审 · **下一课:** [07](07-enterprise-decision-systems.zh.md)

"demo 证明的是可能性;生产证据证明的是在真实负载与故障下的可接受行为。"
发布闸门代码(`task_success >= 0.90`、`unsafe_action_rate == 0`,以及延迟与
成本阈值)是本次会话在 `claims-workflow-v2-poc/PRODUCTION-READINESS.md` 中
手工完成的那种缺口分析的正规化版本——那份文档实际上就是本课程"生产就绪评审"
闸门的一个未打分实例,只是按视角(AI Agent 层 / MCP 层 / 自动化运维 /
监管合规)组织,而不是按 SLO 指标组织。

故障分析中"评判模型可能与被评判系统共享同样的盲点"这一条,是本次会话为
某个 POC 单独标出的一个风险(自由文本字段既被 LLM 读取、又被要求由 LLM 判断,
从而遭受 prompt injection)的更尖锐、更普适的版本。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)——发布闸门
  与决策台账都是"在没有一次记录在案、带版本的检查之前,不让一个概率性系统
  的输出变成事实"。
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 的
  `PRODUCTION-READINESS.md`——本课程闸门的一个真实、人工撰写的实例,值得
  对照课程自身的评分标准,看它缺了什么(它没有明确的发布闸门*阈值*,只有
  定性的缺口描述)。

## 已验证

ZH 版本于 2026-07-16 摄入:Python 代码逐字节一致,标题数一致(7/7)。

## 来源

`raw/courses/06-production-ai-engineering/README.md`
