# 03 · 文档处理流水线

## 学习目标

讲清一份文档从上传到变成可检索 chunk 的完整链路，以及每个环节的可配置点。

## 关键问题

- 上传后任务如何投递（MQ）与消费（worker 池）？状态如何回写？
- docreader（Python）与主服务（Go）的职责边界与 gRPC 协议定义在哪？
- 各格式解析实现分布（PDF / Word / Excel / PPT / 图片 / HTML / EPUB / XMind…）？
- 默认分块算法是什么？`docs/CHUNKING.md` 的描述与代码是否一致？
- 父子分块（parent-child）的存储结构与检索时如何还原上下文？
- 多模态链路：VLM 图片理解、ASR 转写的触发条件与配置？
- Embedding 维度、批大小、失败重试与重解析（reparse）的行为？
- `process_config` 能覆盖哪些阶段？按批次覆盖的实现位置？

## 流水线草图

```text
上传/导入 → 入库(Knowledge) → MQ 任务 → 解析(docreader) → 分块 → 向量化 → 索引 → 可检索
```

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| 解析服务 | `docreader/` |
| 应用编排 | `internal/application/` |
| 知识库领域 | `internal/models/`, `internal/database/` |
| 任务队列 | 见 `docs/worker-pool-governance.md` 与 `internal/runtime/` |
| 数据源导入 | `internal/datasource/` |

## 参考

- `docs/CHUNKING.md`、`docs/数据源导入开发文档.md`
- `docs/worker-pool-governance.md`
