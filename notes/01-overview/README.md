# 01 · 项目总览

## 学习目标

建立对 WeKnora 的整体认知：它解决什么问题、由哪些模块构成、请求如何流转。

## 关键问题

- WeKnora 的定位是什么？（企业级文档理解 + 语义检索 + 自主推理的知识框架）
- 三大核心能力（RAG 快速问答 / ReAct Agent / Wiki 模式）如何划分代码边界？
- 服务如何拆分：主服务（Go）、docreader（Python）、frontend、mcp-server、cli？
- 核心领域模型有哪些，它们之间的归属关系是什么？
- 一次完整的「提问」请求会穿过哪些层？

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| 主服务入口 | `cmd/` |
| HTTP 路由 | `internal/router/` |
| 应用编排层 | `internal/application/` |
| 领域模型 | `internal/models/`, `internal/types/` |
| 配置装载 | `internal/config/` |
| 前端 | `frontend/` |
| CLI | `cli/` |
| MCP Server | `mcp-server/` |
| 数据库迁移 | `migrations/` |

## 参考

- 仓库 README（架构章节）与 `docs/`
- `docs/zh/` 中文文档
- `docs/ROADMAP.md`
