# AGENTS.md —— Wiki Schema 与约定

English: [AGENTS.md](AGENTS.md)

本文件告诉任何在此仓库工作的 LLM agent:wiki 是如何组织的,以及应遵循怎样的
工作流程。在摄入新来源、回答问题、或运行检查(lint)之前,先读本文件。
模式来源:Andrej Karpathy 的
["LLM Wiki"](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
gist——原文见 `raw/_llm-wiki-pattern.md`。

## 本 wiki 关于什么

范围:**公开的** XingAI AI 工程学习内容,以及演示这些内容的公开 POC。
2026-07-16 起种子内容来自:

1. **`courses/`** —— 一套 10 门课程的双语课程体系,来自
   [`xingai-enterprise-ai-design`](https://github.com/xingaiapp/xingai-enterprise-ai-design)
   (基础 → CTO 级领导力)。
2. **`claims-workflow-v2-poc`** —— 一个多 agent 保险理赔 POC,来自
   [`xingai-enterprise-ai-pocs`](https://github.com/xingaiapp/xingai-enterprise-ai-pocs);
   是课程概念的主要可运行交叉参照。

本 wiki 的存在是为了回答一次 grep 回答不了的问题:课程教学法如何体现在真实的
公开 POC 代码里,哪些模式(决策台账、MCP 双墙治理、启发式/LLM 双路径)反复出现,
以及历次审阅发现了哪些错误或确认了哪些结论。范围只通过摄入**公开**来源来增长——
查看 `wiki/index.md` 了解当前实际收录内容。

## 仅限公开来源(必须遵守)

本仓库是公开的。agent 必须:

- 只从公开的 XingAI GitHub 仓库、**其他公开 URL**,或**用户明确提供**、明确用于
  本 wiki 的上下文/图片/文件中摄入内容。
- 绝不将私有仓库的 README、ADR、PRD、portfolio、Decision Card、Content Pack
  或内部产品架构复制、转述或搬运到 `raw/` 或 `wiki/`。
- 优先使用绝对的 `https://github.com/xingaiapp/...`(或其他规范)链接,而非
  工作区内的相对相邻路径。
- 如果某个公开课程*提到*某个私有兄弟产品的名字,可以记录该课程引用了它——
  但不要把那个私有仓库的内部实现拉进本 wiki。

不确定某个来源是否公开时:对仓库检查 GitHub 可见性,对无法抓取的 URL 请用户
粘贴摘录。

### 临时性外部来源

非仓库输入(URL、图片、粘贴内容、本地文件)存放在:

```text
raw/external/YYYY-MM-DD-<slug>/
  SOURCE.md     # 清单(类型、canonical_url、是否已核实)
  content.md    # 抓取或粘贴的文本
  notes.md      # 可选的图片/agent 笔记
  assets/       # 可选
```

Cursor 技能:**`xingai-ai-learning-wiki`**(公开仓库同步)与
**`xingai-wiki-ingest`**(URL / 图片 / 上下文)。两者都必须满足
**综合门槛**、**认知标准**,以及**双语(EN+中文)**规则。

## 认知标准(必须遵守)

本 wiki 的目标是成为一个**知识库**,而不是宣传册,也不是猜测记录。

每个新建或实质性更新的 `wiki/` 页面,都必须明确写出以下内容(作为标题或清晰
标注的区块):

| 区块 | 必须包含的内容 |
|---|---|
| **已知(Known)** | 只写基于已快照的 `raw/`、已抓取的公开 URL,或你实际执行过的检查所证实的结论。注明路径/URL。 |
| **缺失(Missing)** | 来源省略了哪些在这里仍然重要的内容(鉴权、评测、台账*流程*本身、运维、成本、谁来审批、失败模式)。 |
| **再思考(Rethink)** | 对照其他公开来源(课程 vs POC、兄弟 POC、模式 vs demo),哪些假设显得错误或过度简化。 |
| **待辩论(Debate)** | 尚未定论的设计分歧——呈现双方观点;在没有 ADR 或已验证代码之前,不要替一方"下结论"。 |
| **需要更多证据(Needs evidence)** | 会改变本页结论的开放问题。保持开放,**不要**用猜测来回答。 |

**提交前应失败/重写的情况:**

- 页面基本上只是复述来源已经说过的内容,
- 用听起来合理的臆测填补空白,
- 把图片或营销文案当作实现事实来对待,
- 引用了本次会话并未真正读过的文件。

置信度用语:优先使用 `verified`(已验证)/ `partial`(部分)/ `unknown`(未知),
而不是"大概"。

技能文件遵循同一份检查清单:
`~/.cursor/skills/xingai-wiki-ingest/references/epistemic-checklist.md`。

## 分层

- **`raw/`** —— 公开源文档的不可变快照。目录结构镜像源仓库(`raw/courses/`、
  `raw/pocs/`、`raw/xingai-enterprise-ai-design/` 等)。这些**不是**活的原始
  文档——要了解当前真实情况,优先看公开 GitHub 仓库。如果源发生变化,重新
  摄入,而不是手工编辑 `raw/`。
- **`wiki/`** —— 这里的一切都由 LLM 撰写和维护。人来读,agent 来写。结构:
  - `wiki/index.md` —— 内容目录。回答问题时先读这个。
  - `wiki/log.md` —— 只追加的摄入/查询/检查(lint)时间线记录。
  - `wiki/overview.md` —— 顶层综合。
  - `wiki/courses/*.md` —— 每门课程(00-09)一个实体页:摘要 + 交叉引用,
    而不是原始 README 的复制。
  - `wiki/products/*.md` —— 每个**公开**产品/POC 一个实体页。
  - `wiki/concepts/*.md` —— 在多门课程或多个公开 POC 中反复出现的跨领域模式。
  - `wiki/syntheses/*.md` —— 归档回 wiki 的持久性答案。
  - `wiki/assets/ux/<slug>/` —— 当 chrome / 流程 / 主题 / 演示 UI 是故事的一部分时,
    由 wiki 页面嵌入的 UX PNG(见下方 UX PNG 规则)。

## 操作

### 摄入(Ingest)

添加新的**公开**原始来源时:

1. 确认源仓库/URL 是公开的。
2. 复制到 `raw/`,路径镜像其源仓库结构。
3. 更新或创建相应的 `wiki/courses/`、`wiki/products/`、`wiki/concepts/`
   或 `wiki/syntheses/` 页面——**同一次**摄入中同时写 `name.md` 和
   `name.zh.md`。
4. 若目录有变化,更新 `wiki/index.md` **和** `wiki/index.zh.md`。
5. 在 `wiki/log.md` 追加一条记录(运维日志用英文,不需要 `.zh.md`)。

### 查询(Query)

1. 先读 `wiki/index.md` 找候选页面。
2. 读具体的 wiki 页面,而不是原始来源——除非 wiki 页面本身说明某个结论
   需要对照 raw 重新核实。
3. 回答时引用 wiki 页面(以及被引用的原始来源)。
4. 如果答案内容充实且有持久价值,主动提出将其归档进 `wiki/syntheses/`。

### 检查(Lint)

1. 检查页面之间是否有矛盾。
2. 检查是否有结论已被更新的公开原始来源推翻。
3. 检查是否存在孤立页面(orphan pages)。
4. 检查是否有在 2 个以上页面中被提及、但缺少 `wiki/concepts/` 页面的概念。
5. 检查是否有页面重新引入了私有仓库的内部信息。
6. **批判性审计:** 只描述"这是什么"、没有 缺失/再思考/待辩论/需要更多证据
   的页面 → 重写。
7. **猜测审计:** 没有引用支撑的自信断言 → 降级或删除。
8. **双语审计:** `wiki/` 下每个内容页(courses、products、concepts、
   syntheses、index、overview)都有对应的 `.zh.md`;段落数一致;互相的语言
   链接存在;不存在只有英文、中文滞后的情况。
9. **UX 审计:** 讨论 chrome / 流程 / 主题 / 演示 UI 的页面,要么在 EN+ZH 两边
   都嵌入 `wiki/assets/ux/...`,要么明确写「尚无 UX 资产」;不要保留第三方署名
   营销海报;不要留下没有页面引用的孤立 UX 文件。
10. 将发现记录为 `log.md` 中的一条 `lint` 记录;将实质性内容归档为
   `wiki/syntheses/` 页面(EN+ZH)。

## 日志格式

```
## [YYYY-MM-DD] ingest | <source title>
## [YYYY-MM-DD] query | <question>
## [YYYY-MM-DD] lint | <what was checked>
```

`grep "^## \[" wiki/log.md | tail -5` 可查看最近 5 条记录。

## 约定

- **综合门槛(必须遵守):** `wiki/` 页面必须增添 raw 没有的价值。如果页面是
  缩短版 README、文件列表,或只是重述标题,视为不合格。多做对比、课程↔POC
  映射,以及单份仓库 grep 回答不了的问题。`raw/` 是副本;`wiki/` 是积累。
- **认知标准(必须遵守):** 已知 / 缺失 / 再思考 / 待辩论 / 需要更多证据——
  见上文。不得把猜测当作事实。
- **每个 wiki 内容页都是双语的:`name.md`(英文)+ `name.zh.md`(中文)**,
  与设计/POC 仓库自身的约定一致。中文是完整的本地化——相同的段落顺序
  (包括 已知/缺失/再思考/待辩论/需要更多证据)、相同的代码块、相同的图示
  含义、相同的结论。wiki 内部链接指向 `.zh.md` 对应页;`raw/` 与外部 URL
  保持不变。
  - 英文页头部:`Chinese: [name.zh.md](name.zh.md)`
  - 中文页头部:`English: [name.md](name.md)`
  - 适用于:`wiki/courses/`、`wiki/products/`、`wiki/concepts/`、
    `wiki/syntheses/`、`wiki/index`、`wiki/overview`,以及根目录的
    `README` / `AGENTS` / `DISCLAIMER`(在其变更时)。
  - **例外:** `wiki/log.md` 保持仅英文(运维时间线)。
  - **两种语言在同一次摄入中一起写**——绝不让一种语言先上线、另一种
    语言留作待办。
- **需要时纳入 UX PNG:** 若页面讨论产品 chrome、流程、主题或演示 UI——或
  用户附上了 UX 截图 / 公开快照中已有——把持久 PNG 复制到
  `wiki/assets/ux/<slug>/`,并在 **EN 与 ZH** 两边嵌入(相同相对路径;仅本地化
  alt)。主题相关时优先 light+dark 成对。不要把仓库里每张图都倒进来;**需要**
  优先于齐全。**不要**为第三方署名营销海报建 wiki 页(图上有明确的非 XingAI
  署名)。细则:`~/.cursor/skills/xingai-wiki-ingest/references/ux-png.md`。
- 每个 wiki 页面结尾都有一个 `## Sources` 段,链接回具体的 `raw/` 文件,
  或注明是对实际读过的公开来源所做的分析。
- 关于"代码做了什么"的结论,在 POC 可核实时需要附验证记录;否则标记为
  需要更多证据。
- 规模提示:在当前体量下,`index.md` 已足够作为导航。超过约 100 个来源时
  再重新评估(参见模式文档)。
