# 04 · 检索与 RAG

## 学习目标

掌握召回链路的每个环节与可调参数，能定位「检索不到 / 检索不准」的问题。

## 关键问题

- 检索策略有哪些（BM25 稀疏 / Dense 稠密 / GraphRAG / 混合），如何选择？
- 向量库适配层的抽象接口长什么样？新增一种向量库要改哪些地方？
- 召回 → 融合 → rerank → 阈值过滤 → 上下文拼装的完整调用链？
- HNSW（pgvector 1024 维）索引如何创建与调参？
- GraphRAG：实体关系抽取时机、图谱存储、图检索与向量检索如何融合？
- 引用（citation）从 chunk 到前端 popover 的数据流？
- 内置 E2E 测试如何计算召回命中率 / BLEU / ROUGE？

## 笔记索引

| 笔记 | 说明 |
|------|------|
| [01 · 从召回到上下文：读懂 RRF 融合](01-hybrid-search-rrf.md) | 固定官方 v0.8.0：真实调用位置、输入输出、加权 RRF 手算、Go 实现与阈值/上下文边界；附理解自检 |

## 实验记录

| 实验 | 策略 / 参数 | 指标 | 结论 |
|------|-------------|------|------|
|  |  |  |  |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| 检索编排 | `internal/application/service/session_knowledge_qa.go`、`chat_pipeline/search.go` |
| 双路召回与 RRF 融合 | `internal/application/service/knowledgebase_search.go`、`knowledgebase_search_fusion.go` |
| rerank、正文合并与上下文 | `internal/application/service/chat_pipeline/` |
| 检索工具 | `internal/searchutil/` |
| 向量库适配 | `internal/infrastructure/` |
| 文本处理 | `internal/textconv/` |

## 参考

- `docs/使用其他向量数据库.md`、`docs/KnowledgeGraph.md`、`docs/开启知识图谱功能.md`
- `docs/QA.md`
