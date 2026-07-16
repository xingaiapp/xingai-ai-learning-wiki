# 产品:claims-workflow-v2-poc

English: [claims-workflow-v2-poc.md](claims-workflow-v2-poc.md)

**仓库:** [xingai-enterprise-ai-pocs/pocs/claims-workflow-v2-poc](https://github.com/xingaiapp/xingai-enterprise-ai-pocs) · **状态(2026-07-16):** 可运行 · 第 1+2+3 阶段 · 40 个测试通过

多 agent 保险理赔流水线,用来证明对一张流行(但有缺陷)的理赔自动化信息图的三处修正:欺诈检测拆成评估前 Triage 与评估后 Scoring 两个 agent;Case Resolution Router 从特定阶段恢复而不是从 intake 重启;每个阶段写入 Decision-Ledger 形态的合规审计轨迹。再经三阶段加深:真实 MCP 数据访问边界(第 1 阶段)、带依赖很轻的 RAG 层的 LLM agent(第 2 阶段)、LangGraph supervisor(第 3 阶段)。

这是本 wiki 里主要的公开可运行交叉引用——几乎每门课都接到它的某块。它与 oauth / partner-api / RAG 兄弟的关系(不是「同一 demo 的 v2」)见[Claims POC 族](../syntheses/claims-poc-family-tradeoffs.zh.md)。

## 原先的三处修正

1. **欺诈检测拆分** —— `fraud_triage.py`(Damage Assessment 之前,仅速度/tenure 信号) vs `fraud_scoring.py`(之后,成本异常/照片取证信号)。各自钉住不同的 `model_version`,便于公平性审计追溯。
2. **Case Resolution Router** —— 把 `(escalation.reason, escalation.stage, human_decision.outcome)` 映射到具体再入阶段;无法识别的组合落到安全默认拒绝,绝不静默重启。实现中才发现(不在原设计文章里):路由必须*阶段感知*,不能只感知 reason。
3. **合规与审计轨迹** —— 每个 agent 决策都是 MCP 工具支撑的 `DecisionLedger` 行(见[概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md));不利行动信函引用导致拒绝的具体政策条款。

## 三阶段加深(ADR-009)

- **第 1 阶段 —— MCP 数据边界:** 政策查询、台账写入、支付移到手写的 JSON-RPC-over-FastAPI `mcp_server/` 后面;默认进程内(经 `starlette.testclient.TestClient`,不是原始 `httpx.ASGITransport`——后者不支持同步调用),或在设置 `MCP_SERVER_URL` 时走真实 HTTP。
- **第 2 阶段 —— LLM agent + RAG:** 每个 LLM agent 都有启发式路径(不变,默认)与 LLM 路径(经 `llm_client.is_available()` 分发),任何 `LLMError` 回退启发式。Policy Coverage 的 LLM 路径经约 40 行纯 Python hashing-trick embedding 检索真实条款文本(含排除项)——故意不要向量库,因为每份保单语料很小且始终限定在一份已知保单。
- **第 3 阶段 —— LangGraph supervisor:** 同一批 8 个 agent 函数变成图节点;Case Resolution Router「从特定阶段恢复」的需求,靠每次调用从所选阶段编译*新*图来满足,明确**不是**真 LangGraph checkpoint——有文档记录的、故意的范围收缩。

## PRODUCTION-READINESS.md —— 第 06 课案例

按四个镜头组织:AI Agent 层(喂给两个 Fraud agent 与 Policy Coverage 的自由文本 `loss_description` 上的提示注入风险——标为代码库任何地方都未处理;未校准的启发式阈值;无模型风险治理流程)、MCP 层(无工具 schema 版本、无调用韧性/熔断、台账保留无上限)、自动化/运维(无持久化、无可观测性、无 DR、无 canary)、以及通用清单不会浮现的理赔行业监管关切(及时支付法期限、SIU/欺诈局报告、管辖区感知的不利行动信函、LLM 调用周围的 PII、模型变更管理)。

**该文档给出的优先级:** (1) 提示注入筛查——便宜,关掉真实欺诈向量;(2) 在 `mcp_server` 前挂真实 OAuth——已作为 ADR-009 第 4 阶段完整设计;(3) 及时支付期限跟踪 + LLM 数据处理姿态;(4) 持久化与保留策略一起做,不要只做持久化。

## 关联

- [概念:决策台账模式](../concepts/decision-ledger-pattern.zh.md)、[概念:缓存/回退 LLM 纪律](../concepts/cache-first-llm-architecture.zh.md)、[概念:Agent 治理与 MCP](../concepts/agent-governance-and-mcp.zh.md)
- [第 05 课](../courses/05-agent-runtime-multi-agent.zh.md)(LangGraph、状态机)、[第 06 课](../courses/06-production-ai-engineering.zh.md)(生产就绪差距分析)、[第 07 课](../courses/07-enterprise-decision-systems.zh.md)(决策台账)、[第 04 课](../courses/04-mcp-interoperability.zh.md)(MCP 服务器本身)
- 兄弟公开 POC:[claims-mcp-oauth-poc](claims-mcp-oauth-poc.zh.md)(OAuth 第 4 阶段目标)、[claims-multiagent-rag-poc](claims-multiagent-rag-poc.zh.md)、[claims-partner-api-mcp-poc](claims-partner-api-mcp-poc.zh.md)

## 来源

`raw/pocs/claims-workflow-v2-poc/README.md`, `PRODUCTION-READINESS.md`, `architecture.md`; `raw/pocs/docs/adr/008-claims-workflow-v2-poc.md`, `009-claims-workflow-v2-mcp-multiagent.md`
