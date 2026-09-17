# 学习路线图

> 目标：从「能跑起来」到「能改得动」，最终能基于 WeKnora 做二次开发与生产落地。
> 勾选表示该阶段已产出对应笔记（笔记落在 `notes/` 对应目录）。

图例：`[ ]` 未开始 · `[~]` 进行中 · `[x]` 已完成

---

## 阶段一：跑通与总览（01-overview / 02-quickstart）

- [ ] 读懂官方 README 与 `docs/` 文档结构，产出《项目定位与能力地图》
- [ ] 画出整体架构图：Web/CLI → API 层 → application → 领域服务 → 存储
- [ ] 理解核心领域模型：Tenant / Workspace / KnowledgeBase / Knowledge / Chunk / Session / Message
- [ ] 用 Docker Compose 本地起全栈，跑通「上传文档 → 提问 → 带引用回答」
- [ ] 梳理 `internal/` 各包职责边界，产出《internal 包地图》
- [ ] 记录首次部署踩坑（端口、模型 Key、向量库初始化等）

## 阶段二：文档处理流水线（03-doc-pipeline）

- [ ] 摸清 docreader（Python）与主服务（Go）的职责切分与 gRPC 协议
- [ ] 支持格式清单与各格式解析实现位置（PDF/Word/Excel/PPT/图片/XMind…）
- [ ] 分块（Chunking）策略：默认切分算法、参数、父子分块
- [ ] 多模态链路：VLM 图片理解、ASR 语音转写
- [ ] 向量化与入库：embedding 维度、批处理、索引类型
- [ ] 异步任务：MQ 投递 → worker 消费 → 状态回写，失败重试机制
- [ ] 实验：同一文档不同分块参数对召回的影响

## 阶段三：检索与 RAG（04-retrieval）

- [ ] 检索策略全景：BM25 稀疏 / Dense 稠密 / GraphRAG / 混合
- [ ] 向量库适配层：pgvector、Elasticsearch、Milvus、Qdrant 等的抽象接口
- [ ] 召回 → 融合 → rerank → 阈值过滤 → 上下文拼装 的完整调用链
- [ ] HNSW 索引参数与 1024 维 pgvector 的性能表现
- [ ] GraphRAG：实体/关系抽取、图存储、图检索如何与向量检索协同
- [ ] 引用（citation）是如何从 chunk 一路带到前端展示的
- [ ] 实验：用内置 E2E 测试评估召回命中率 / BLEU / ROUGE

## 阶段四：Agent 与工具（05-agent）

- [ ] ReAct 循环实现：思考 → 行动 → 观察 → 收敛判定的源码走读
- [ ] Prompt 组装机制：系统提示、工具描述、上下文注入顺序
- [ ] 内置工具清单与 `agent-tools-design.md` 的设计取舍
- [ ] MCP 集成：客户端、OAuth2 远程服务、会话中途授权
- [ ] Skill 沙箱：Docker / E2B / Cube 后端差异、会话持久化、网络策略
- [ ] `@Skill` / `@MCP` 提及如何限定单轮运行时
- [ ] 流式输出与 chat steering（对话打断/纠正）实现

## 阶段五：Wiki 与记忆（06-wiki-memory）

- [ ] Wiki 模式：从原始文档生成互链 markdown 的流程与调度
- [ ] 页面版本历史、行级 diff、一键回滚的数据结构
- [ ] 知识图谱：抽取、存储、可视化接口
- [ ] 长期记忆：记忆类型（profile/preference/fact/task/interest）、自动抽取与用户确认
- [ ] `search_memory` 工具的召回时机与 Prompt 注入

## 阶段六：集成与扩展（07-integration）

- [ ] REST API 全貌与 `docs/swagger.yaml` 对照阅读
- [ ] Scoped API Key 与 principal 模型、权限粒度
- [ ] IM 渠道接入（企业微信/飞书/Slack/Telegram…）的统一抽象
- [ ] 数据源导入框架（飞书/GitLab/Notion/语雀/RSS）与增量同步
- [ ] 模型接入：20+ LLM provider 的适配层设计、内置模型 YAML 声明
- [ ] 网站嵌入 Widget、Chrome 扩展、微信小程序 的接入方式
- [ ] 动手：写一个自定义工具 / 自定义数据源

## 阶段七：部署与运维（08-deploy-ops）

- [ ] Helm Chart 参数梳理与生产化配置建议
- [ ] 任务队列与 worker 池治理（core/post-process/enrichment/maintenance/elastic/wiki）
- [ ] 每模型后台并发治理（governor）机制
- [ ] Langfuse 可观测性：ReAct 链路、token 追踪、解析 trace 时间线
- [ ] 安全：AES-256-GCM 静态加密与密钥轮换、SSRF 防护、gRPC TLS
- [ ] RBAC：4 级角色矩阵、按资源归属、审计日志
- [ ] 数据库迁移机制与版本升级注意事项

## 阶段八：二次开发产出（09-source-reading）

- [ ] 完成一条端到端调用链的源码走读笔记（从 HTTP handler 到 DB）
- [ ] 产出一张自定义时序图 / 架构补充图（放入 `assets/`）
- [ ] 提交第一个可运行的改动（自定义工具 / 分块策略 / 数据源）
- [ ] 形成《WeKnora 二次开发上手清单》

---

## 里程碑

| 里程碑 | 判定标准 | 状态 |
|--------|----------|------|
| M1 跑通 | 本地全栈可用，能完成一次带引用的 RAG 问答 | `[ ]` |
| M2 讲清 | 能向他人讲清文档入库到检索回答的完整链路 | `[ ]` |
| M3 改得动 | 能独立新增一个工具或数据源并跑通 | `[ ]` |
| M4 落得地 | 能在类生产环境部署并做基本调优与排障 | `[ ]` |
