# 产品:event-bus-ai-review

English: [event-bus-ai-review.md](event-bus-ai-review.md)

**仓库:** [xingai-enterprise-ai-pocs](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态:** 仅架构——不可运行

设计:经事件总线把业务事件路由到独立订阅方(AI 审核、合规、人工审批、审计),再组装决策包。

## README 不会强调的

本 wiki 里其他多 agent POC 都是**同步 supervisor 图**(lab、RAG、workflow-v2)。这个问的是:若 AI 审核与合规不能共享调用栈,怎么办?那是控制平面选择,不是「更多 agent」选择。

当第 05/06 课谈到持久化执行与 human-in-the-loop 时,用它作对照——同一需求可以落成 LangGraph 节点,*也可以*落成总线订阅方。ADR-004 标为占位;不要假装有代码可核。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)、[概念:Loop 工程](../concepts/loop-engineering.zh.md)
- [Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)(另类一节)

## 来源

`raw/pocs/event-bus-ai-review/README.md`, `architecture.md`; `raw/pocs/docs/adr/004-event-bus-ai-review-placeholder.md`
