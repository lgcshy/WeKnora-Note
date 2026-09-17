# 02 · 快速开始

## 学习目标

在本地把 WeKnora 全栈跑起来，完成一次端到端的「上传文档 → 提问 → 带引用回答」。

## 关键问题

- 最小可用依赖是什么？（PostgreSQL+pgvector、Redis、对象存储、模型 API Key）
- Docker Compose 各服务职责与端口映射？
- 首次启动时数据库迁移、向量库扩展（pgvector）如何初始化？
- 模型配置在哪里填，如何验证连通性？
- dev 模式（`docker-compose.dev.yml` / 快速开发模式）与生产模式的差异？
- CLI（`weknora`）能做哪些事？

## 环境记录

| 项 | 值 |
|----|----|
| 操作系统 | |
| Docker / Compose 版本 | |
| Go 版本 | 1.26 |
| 使用的模型 / 向量库 | |
| 部署方式 | Docker Compose |

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 踩坑记录

| 现象 | 原因 | 解决 |
|------|------|------|
|  |  |  |

## 参考

- 仓库 `docker-compose.yml` / `docker-compose.dev.yml` / `Makefile`
- `docs/快速开发模式说明.md`、`docs/开发指南.md`
- `docs/使用其他向量数据库.md`
