# 第 07 课:企业 AI 决策系统

English: [07-enterprise-decision-systems.md](07-enterprise-decision-systems.md)

**先修课程:** [06](06-production-ai-engineering.zh.md) · **通过门槛:** 架构评审委员会答辩 · **下一课:** [08](08-ai-leadership-cto.zh.md)

本课程*就是*决策台账(Decision Ledger)模式,作为架构来讲授:"决策计算属于
worker/核心领域边界;API 只传输已计算好的决策;UI 负责解释;执行环节单独
授权。"原始来源中不可变的 `Decision` dataclass,其 `api_view()` 明确注释为
`# transport only; no request-time recomputation`(仅传输,不在请求时重新
计算),正是公开 claims POC 实现为 `DecisionLedger` 的同一形态的教学版本。

课程"参考资料"部分按路径引用了一个兄弟产品的决策缓存 ADR;本公开 wiki 不
摄入该私有 ADR。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)——本课程是
  该模式的权威教学版本;概念页是交叉索引。
- [claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 的
  `DecisionLedger`(以 MCP 客户端为后盾)——同样的 schema 直觉,在一个可运行
  的公开 POC 中的体现。
- 公开模式文档:[xingai-engineering-system](https://github.com/xingaiapp/xingai-engineering-system)
  决策台账 schema("是模式,不是库")。

## 已验证

ZH 版本于 2026-07-16 摄入:Python 代码块只有一处差异——`api_view()` 的行内
注释做了本地化(`# transport only; no request-time recomputation` 对比
`# 仅传输,不在请求时重新计算`),按照 COURSE-STANDARD(注释不算"代码行为"),
这是正确的本地化,而不是一致性破坏。标题数一致(7/7)。

## 来源

`raw/courses/07-enterprise-decision-systems/README.md`
