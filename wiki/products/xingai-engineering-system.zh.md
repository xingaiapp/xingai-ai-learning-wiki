# 产品族:xingai-engineering-system

English: [xingai-engineering-system.md](xingai-engineering-system.md)

**仓库:** [xingai-engineering-system](https://github.com/xingaiapp/xingai-engineering-system)

不是产品。模式包(「模式,不是库」),产品复制进自己的 DB 与仓库。对本 wiki,有用的动作是看见**同一个想法**的三个名字:

| 模式文档 | 课程 / POC 同韵 |
|---|---|
| `decision-ledger-schema` | 第 07 课教的 `Decision` + workflow-v2 的 `DecisionLedger` |
| `worker-cache-boundary` / `cache-first-before-llm` | 第 01/06 课成本纪律;workflow-v2 双路径是*回退*近亲 |
| `loop-engineering-three-layer` / `micro-loop-engine` | [Loop 工程](../concepts/loop-engineering.zh.md)文章 + ADR-005 |
| `agent-execution-gate` + ADR-002 | 第 03 课 approve/execute;oauth POC 的墙 |

## 不该做什么

不要把 schema markdown 贴进每个产品页。链到这里,再说*某个* POC 如何符合或偏离(例如 workflow-v2 钉了 `model_version`,但仍缺模型变更管理流程——写在它的 PRODUCTION-READINESS 里)。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)、[概念:缓存/回退](../concepts/cache-first-llm-architecture.zh.md)、[概念:Loop 工程](../concepts/loop-engineering.zh.md)

## 来源

`raw/xingai-engineering-system/patterns/*`(精选), `raw/xingai-engineering-system/docs/adr/002-agent-execution-safety.md`
