# 概念:决策台账(Decision Ledger)模式

English: [decision-ledger-pattern.md](decision-ledger-pattern.md)

一份不可变的记录:*决定了什么、基于什么证据、在什么策略版本下、由哪个模型
做出*——在 worker/核心边界中计算,通过 API 只读传输,绝不在 UI 或请求处理器
中重新计算。

| 位置 | 形态 |
|---|---|
| [第 07 课](../courses/07-enterprise-decision-systems.zh.md) | 权威教学版本——冻结的 `Decision` dataclass,`api_view()` 明确注释"仅传输,不在请求时重新计算"。 |
| [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 的 `DecisionLedger` | 以 MCP 客户端为后盾(第 1 阶段),每一行都固定了 `model_version`,使公平性审计成为可能(该 POC 的 `PRODUCTION-READINESS.md` 指出审计*流程*本身仍是缺口——但数据形态已经存在)。 |
| [xingai-engineering-system](../products/xingai-engineering-system.zh.md) | 共享的 `Decision` schema——是模式,不是库(`raw/.../decision-ledger-schema.md`)。 |
| [multi-agent-lab](../products/multi-agent-lab.zh.md) / [claims-multiagent-rag-poc](../products/claims-multiagent-rag-poc.zh.md) | SQLite trace / 审计步骤——在完整 schema 出现之前的台账直觉。 |

第 07 课的"参考资料"部分还按路径引用了一个兄弟产品的决策缓存 ADR;本 wiki
不摄入该私有 ADR——把课程中的这一引用当作纯粹的指针。

## 为什么它反复出现

背后是同一个问题:事后能否证明一个自动化系统为什么做出了那样的决定?
理赔、投资、agent 治理都会碰到这个问题;正因为问题本身是持久的,这种台账
形态才如此持久。

## 一个尚未解决的缺口(在公开 POC 文档中已标出)

给 `model_version` 打上版本字符串,并不等同于在新模型或新 prompt 上线之前
有一套模型变更管理/审批流程。`claims-workflow-v2-poc/PRODUCTION-READINESS.md`
明确指出了这一点。

## 来源

`raw/courses/07-enterprise-decision-systems/README.md`、
`raw/pocs/claims-workflow-v2-poc/`、
`raw/xingai-engineering-system/patterns/decision-ledger-schema.md`、
`raw/pocs/docs/adr/008-claims-workflow-v2-poc.md`
