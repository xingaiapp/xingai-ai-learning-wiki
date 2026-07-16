# 综合:2026-07-16 课程评审发现

English: [review-findings-2026-07-16.md](review-findings-2026-07-16.md)

播种本 wiki 的那次评审的审计轨迹——写成页面,而不是留在聊天里。此处范围仅限**公开课程**。

## 检查了什么

- 全部 10 门课对照 `COURSE-STANDARD.md` 的必需结构(5W+How、代码、Mermaid 图、失败分析、lab/面试闸门、来源)。
- 每个代码示例,手工:`cosine`、`recall_at_k`、`precision_recall`、`opportunity_score`、`release_allowed`、`transition`、`parse_triage`、`TOOL["inputSchema"]` 断言——全部正确。
- 双语一致性——抽查第 00 课与第 04 课以及顶层课程索引 ZH——忠实、结构匹配的翻译。
- 课程内部交叉引用(`guides/`、`articles/`、`assessments/`、`capstones/`、`interview-bank/`、`deep-enterprise-ai/`,以及 References 中命名的兄弟仓库路径)——在适用的公开设计 / POC 树中可解析。
- 看起来不寻常的外部 URL:`developers.openai.com/...`、`a2a-protocol.org/...`、`modelcontextprotocol.io/specification/2025-11-25/...`——经网络搜索核实为真实。

## 发现了什么

那一轮没有发现需要在课程本身修的课程结构或示例代码缺陷。ZH 一致性有一处故意的注释本地化(第 07 课 `api_view()`),正确当作本地化而非一致性断裂。

## 给 Lint 的教训

「本地工作区没有」不是证据说被引用的公开 URL 或公开仓库路径错了——在宣称交叉引用过时之前先查远程。反过来,对本**公开** wiki:本地有私有兄弟检出,不是摄入它的许可证。

## 来源

本会话(2026-07-16)关于公开 `xingai-enterprise-ai-design/courses/` 与公开 POC 文档的聊天历史;见 `raw/courses/` 与 `raw/pocs/claims-workflow-v2-poc/`。
