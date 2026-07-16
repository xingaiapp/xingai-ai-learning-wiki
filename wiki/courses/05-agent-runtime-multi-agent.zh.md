# 第 05 课:Agent 运行时与多 Agent 系统

English: [05-agent-runtime-multi-agent.md](05-agent-runtime-multi-agent.md)

**先修课程:** [04](04-mcp-interoperability.zh.md) · **通过门槛:** 可恢复的有状态工作流 · **下一课:** [06](06-production-ai-engineering.zh.md)

持久化执行,以及最重要的多 agent 决策规则:"只在确有专业化分工、信任隔离
或并行需求时才增加 agent"——而不是因为 agent 更多看起来更高级。显式状态机
(`ALLOWED` 转移表,非法转移直接抛异常)与 `claims-workflow-v2-poc` 的
Case Resolution Router 所用的纪律一致——从特定阶段恢复,绝不靠猜测退回 intake。

本课程对 checkpoint 问题的坦诚提醒("更多 agent 会增加不确定性……要防止
循环委派、重复的副作用、过期的 checkpoint")值得对照
`claims-workflow-v2-poc` 自己的坦白(ADR-009"第 3 阶段实现说明")——它的
LangGraph supervisor 是每次调用重建一张全新的图,而不是使用真正的
checkpoint/`thread_id` 持久化——一个真实的 POC 选择了本课程标记为"更难、
但更有价值"的那个版本的缩水版。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)、
  [概念:Loop 工程](../concepts/loop-engineering.zh.md)
- [multi-agent-lab](../products/multi-agent-lab.zh.md)、
  [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md)、
  [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md)

## 已验证

ZH 版本于 2026-07-16 摄入:Python 代码逐字节一致,标题数一致(7/7)。

## 来源

`raw/courses/05-agent-runtime-multi-agent/README.md`
