# WeKnora-Note

> 基于 [Tencent/WeKnora](https://github.com/Tencent/WeKnora) 的学习记录仓库 —— 架构拆解、源码阅读、本地实践与踩坑笔记。

[![Learning](https://img.shields.io/badge/type-learning--notes-blue)](#)
[![Based on](https://img.shields.io/badge/based%20on-WeKnora%20v0.8.0-2e6cc4)](https://github.com/Tencent/WeKnora)

---

## 📌 关于本仓库

本仓库是**个人学习笔记**，不是 WeKnora 的官方文档，也不包含 WeKnora 源码。
目的是把阅读 WeKnora 过程中的理解、验证结论和可复现的实验沉淀下来，便于回顾与二次开发。

| 项目 | 说明 |
|------|------|
| 学习对象 | [Tencent/WeKnora](https://github.com/Tencent/WeKnora) `v0.8.0` |
| 代码快照 | 本地参考 commit `f2606629`（2026-09-16） |
| 后端 | Go `1.26`，模块名 `github.com/Tencent/WeKnora` |
| 前端 | `frontend/`（Vue 技术栈） |
| 文档解析 | `docreader/`（Python 服务，gRPC 与主服务通信） |
| 默认存储 | PostgreSQL + pgvector、Redis、对象存储（本地 / MinIO / S3 等） |

> ⚠️ 笔记中的结论以对应 commit 为准。WeKnora 迭代很快，阅读时请核对当前源码版本。

---

## 🗂️ 目录结构

| 目录 | 主题 | 内容概要 |
|------|------|----------|
| [notes/01-overview](notes/01-overview/) | 项目总览 | 定位、整体架构、模块划分、核心数据模型 |
| [notes/02-quickstart](notes/02-quickstart/) | 快速开始 | 环境准备、Docker Compose 部署、首次跑通问答 |
| [notes/03-doc-pipeline](notes/03-doc-pipeline/) | 文档处理流水线 | 解析（docreader）、分块策略、多模态、向量化入库 |
| [notes/04-retrieval](notes/04-retrieval/) | 检索与 RAG | BM25 / Dense / GraphRAG、父子分块、rerank、召回评估 |
| [notes/05-agent](notes/05-agent/) | Agent 与工具 | ReAct 循环、工具体系、MCP、Skill 沙箱、Prompt 组装 |
| [notes/06-wiki-memory](notes/06-wiki-memory/) | Wiki 与记忆 | Wiki 模式、知识图谱、跨会话长期记忆 |
| [notes/07-integration](notes/07-integration/) | 集成与扩展 | REST API、API Key、IM 渠道、数据源、模型接入 |
| [notes/08-deploy-ops](notes/08-deploy-ops/) | 部署与运维 | Helm/K8s、任务队列与 worker 池、Langfuse 可观测性、安全 |
| [notes/09-source-reading](notes/09-source-reading/) | 源码阅读 | 按目录的源码走读记录、调用链追踪、调试技巧 |

其他：

- [ROADMAP.md](ROADMAP.md) —— 学习路线图与进度追踪
- [glossary.md](glossary.md) —— 术语表
- [templates/note-template.md](templates/note-template.md) —— 笔记模板
- `assets/` —— 笔记配图（架构图、时序图等）

---

## ✍️ 笔记约定

每篇笔记建议：
1. 从 [templates/note-template.md](templates/note-template.md) 复制生成；
2. 文件名使用 `kebab-case`，放在对应主题目录下；
3. 在所属目录的 `README.md` 索引表中登记；
4. 明确标注**结论来源**：`源码路径:行号` / 官方文档链接 / 实验验证；
5. 区分三类内容：**已验证结论**、**推测（待验证）**、**踩坑记录**。

目录内命名示例：

```text
notes/04-retrieval/
├── README.md                  # 主题索引与关键问题
├── 01-retrieval-strategies.md # 检索策略对比（BM25 / Dense / GraphRAG）
└── 02-hybrid-search-flow.md   # 混合检索调用链
```

---

## 🔗 相关资源

- WeKnora 仓库：<https://github.com/Tencent/WeKnora>
- 官方站点：<https://weknora.weixin.qq.com>
- 官方文档目录：WeKnora 仓库内 `docs/`（含中文文档 `docs/zh/`）

---

## 📄 License

本仓库笔记内容采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) 许可；
其中引用的 WeKnora 代码片段、架构图版权归 Tencent/WeKnora（MIT License）所有。
