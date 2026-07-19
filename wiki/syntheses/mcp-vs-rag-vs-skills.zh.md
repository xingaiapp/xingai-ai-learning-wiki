# 综合:MCP vs RAG vs Skills(海报)vs XingAI 地图

English: [mcp-vs-rag-vs-skills.md](mcp-vs-rag-vs-skills.md)

三栏信息图(用户于 2026-07-16 摄入):MCP | RAG | Agent Skills,作为「改进 AI agent 的架构」。

资产:`raw/external/2026-07-16-mcp-vs-rag-vs-skills/`。

## 已验证(Known)

- 海报结构(视觉,`verified: partial`):见 `notes.md`——MCP host/client/server 接外部应用;RAG embed→向量库→增强提示→生成;Skills host + skill manager + 本地/开发工具 + `SKILL.md` / actions。
- XingAI 公开教学已经把**程序 vs 能力**分开:
  - `raw/xingai-tech-blog/posts/2026-06-14-cursor-skills-vs-mcp-when-to-use-which.md`:「Skills 教程序。MCP 授能力。」Skills = git 里版本化的 `SKILL.md` 工作流;MCP = 仓库外的运行时工具/资源。
  - [第 02 课](../courses/02-rag-knowledge-systems.zh.md):RAG 作为受治理的检索流水线(ACL 先于排序、引用、评测)——不只是「中间有个向量库」。
  - [第 04 课](../courses/04-mcp-interoperability.zh.md) + [agent 治理](../concepts/agent-governance-and-mcp.zh.md):MCP 作为带鉴权风险的能力边界(confused deputy、双墙)。
- 公开 POC 是组合这些,而不是挑一个:[claims-multiagent-rag](../products/claims-multiagent-rag-poc.zh.md)(RAG)、[claims-mcp-oauth](../products/claims-mcp-oauth-poc.zh.md) / [partner-api](../products/claims-partner-api-mcp-poc.zh.md)(MCP)、像 `xingai-wiki-ingest` 这样的 Cursor skills(程序)——[claims 族](claims-poc-family-tradeoffs.zh.md)。

## 缺失(海报上)

- **组合:** 没有 Skill → 调 MCP → MCP 工具返回 RAG 命中 的图。
- MCP 上的**鉴权 / 策略**(OAuth、scope、Review→Execute)。
- **RAG 质量:** 分块、ACL、引用忠实度、评测——只有 embedding→DB→增强。
- **Skills 信任模型:** 谁写 SKILL.md、如何版本化/评审、失败模式「过时指令」(XingAI 博文有名,这里没有)。
- 三栏中任一的 **评测 / 台账 / HITL**。

## 再想(Rethink)

- **「vs」是错误的连词。** 对 XingAI,有用的问题是*哪一层拥有哪份工作*,不是*哪种架构赢*。没有 MCP 的 Skills 拉不到实时经纪/理赔数据(博文);没有 Skills 的 MCP 把「我们怎么构建」留在未编码状态;两者都没有的 RAG 只是文档落地。
- **Skills 栏把两件事搅在一起:** (1) `SKILL.md` 剧本与 (2) 运行时工具执行(shell/docker)。XingAI 博文把 (1) 留作 Skill,把实时能力推到 MCP——海报把它们压在「Agent Skills」下。
- **MCP 栏看起来像快乐路径连通性。** 第 04 课 / oauth POC 存在,正是因为「选对服务器」而没有 audience 限定令牌是不安全的。

## 辩论(留开)

| 问题 | 海报倾向 | XingAI 公开倾向 | 状态 |
|---|---|---|---|
| MCP / RAG / Skills 是备选项吗? | 「vs」暗示 | 层/工作(博文 + 课程) | 偏好组合;非正式 ADR |
| Agent 工具住在哪? | Skills 栏(shell/git/docker) | 外部系统常是 MCP 服务器;Skills 做剧本 | IDE 本地工具 vs 远程 API 仍开放 |
| RAG 是「一种架构」还是 agent 内的检索模式? | 对等栏 | 第 02 课模式用*在* agent/POC *里* | 命名开放;实质:仍要 ACL + 评测 |

## 需要证据

- 本图的规范 URL / 作者。
- 「Drant」是否为 Qdrant(笔误)——不要当成产品主张。
- 任何 XingAI 公开文档是否背书排他的「选 MCP 或 RAG 或 Skills」(快照博文中未找到;缺席 ≠ 别处没有的证明)。

## 怎么用

- 面试 / 第 04–02 课探针:「画出这三者如何组合;再加鉴权与 ACL。」
- 摄入营销图时:只复述三栏的页面应判失败。
- 相关阶梯海报(RAG → agent → multi-agent MCP):[RAG vs Agentic RAG](rag-vs-agentic-rag-vs-xingai.zh.md)。
- 智能体通信协议(MCP 工具 vs A2A 对等体;ACP 谱系):[mcp-vs-a2a-vs-acp](mcp-vs-a2a-vs-acp.zh.md)。

## 来源

`raw/external/2026-07-16-mcp-vs-rag-vs-skills/`; `raw/xingai-tech-blog/posts/2026-06-14-cursor-skills-vs-mcp-when-to-use-which.md`; 第 02/04 课实体页; claims MCP/RAG 产品页。图:`verified: partial`。
