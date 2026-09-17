# 06 · Wiki 与长期记忆

## 学习目标

理解 Wiki 模式的生成与维护机制，以及跨会话长期记忆的存取时机。

## 关键问题

### Wiki 模式

- Agent 如何把原始文档蒸馏成互链的 markdown Wiki 页面？触发与调度方式？
- Wiki 有独立的任务池（wiki pool），它与主流程的隔离设计？
- 页面版本历史、行级 diff、一键回滚的数据结构？
- 知识图谱的实体/关系抽取、存储与可视化接口？

### 长期记忆

- 记忆类型（profile / preference / fact / task / interest）各自定义与生命周期？
- 自动抽取发生在什么时机？用户确认流程如何实现？
- `search_memory` 工具在 ReAct 循环中何时被调用？记忆如何注入 Prompt？
- 记忆的存储位置、隔离粒度（会话 / 用户 / 工作空间）？

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| 记忆实现 | `internal/application/`, `internal/models/`（按记忆关键词检索） |
| 知识图谱 | 见 `docs/KnowledgeGraph.md` |
| Wiki | 见 `docs/wiki/` |

## 参考

- `docs/wiki/`、`docs/KnowledgeGraph.md`、`docs/开启知识图谱功能.md`
- 仓库 README 的 Wiki Mode / Long-term Memory 章节
