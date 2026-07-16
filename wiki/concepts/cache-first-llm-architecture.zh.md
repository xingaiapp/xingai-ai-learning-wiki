# 概念:缓存 / 兜底 LLM 纪律

English: [cache-first-llm-architecture.md](cache-first-llm-architecture.md)

课程与公开 claims POC 中反复出现的两个相关但不同的目标:

1. **控制 LLM 成本**——当缓存或复用可行时,不为每一次相同或近似相同的请求都
   支付一次模型调用的代价([第 01 课](../courses/01-llm-application-engineering.zh.md)
   的缓存模块;[第 06 课](../courses/06-production-ai-engineering.zh.md)的
   单任务成本发布闸门)。
2. **绝不让单次 LLM 调用成为单点故障**——保留一条确定性路径,使系统在模型
   宕机或返回垃圾结果时仍能完成任务。

## 公开实例:claims-workflow-v2-poc 双路径

[claims-workflow-v2-poc](../products/claims-workflow-v2-poc.zh.md) 同时运行
启发式与 LLM 两条路径(`_run_heuristic` / `_run_llm`,由
`llm_client.is_available()` 决定是否启用),遇到任何 `LLMError` 时回退到
启发式路径。这是一种*兜底*,不是内容哈希缓存——但它与第 06 课对生产系统
"决策必须仍然能完成"的要求,共享同一种纪律。

## 在课程中的微缩体现

- [第 01 课](../courses/01-llm-application-engineering.zh.md)——校验、窄范围
  重试、观测、安全降级。
- [第 06 课](../courses/06-production-ai-engineering.zh.md)——像
  `cost_per_task` 这样的发布闸门阈值,把同一目标变成一个可衡量的关卡。

## 来源

`raw/courses/01-llm-application-engineering/README.md`、
`raw/courses/06-production-ai-engineering/README.md`、
`raw/pocs/claims-workflow-v2-poc/`、
`raw/xingai-engineering-system/patterns/cache-first-before-llm.md`、
`raw/xingai-engineering-system/patterns/worker-cache-boundary.md`
