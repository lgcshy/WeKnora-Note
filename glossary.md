# 术语表

阅读 WeKnora 源码与文档时高频出现的概念，按主题归类。持续补充。

## 组织与权限

| 术语 | 含义 |
|------|------|
| Tenant | 租户，最外层隔离单位，承载用户与工作空间 |
| Workspace（共享空间） | 租户内的协作空间，RBAC、审计日志、模型共享的作用域 |
| Role Matrix | 4 级角色矩阵：Owner / Admin / Contributor / Viewer |
| Principal | 调用主体抽象，API Key、MCP OAuth、嵌入会话都绑定到某个 principal |
| Scoped API Key | 带能力级授权与知识库限制的 API Key |

## 知识与文档

| 术语 | 含义 |
|------|------|
| Knowledge Base（知识库） | 知识的逻辑容器，类型分 FAQ / Document / Wiki |
| Knowledge | 知识库中的一条知识条目（一份文档 / 一条 FAQ / 一个 URL） |
| Chunk | 文档切分后的检索单元，支持在线编辑、版本 diff 与回滚 |
| Parent-Child Chunking | 父子分块，子块用于召回、父块用于提供上下文 |
| chunk editing / revision | 分块编辑与版本快照机制 |
| Auto-Tagging | 解析完成后自动匹配知识库已有标签 |
| process_config | 按上传批次覆盖解析/分块/多模态/图谱抽取等配置 |
| docreader | 独立的文档解析服务（Python），经 gRPC 与主服务通信 |

## 检索与 RAG

| 术语 | 含义 |
|------|------|
| BM25 | 稀疏检索（关键词），Elasticsearch 等后端提供 |
| Dense Retrieval | 稠密向量检索，依赖 embedding + 向量库 |
| Hybrid Search | 稀疏与稠密结果的融合检索 |
| GraphRAG | 基于知识图谱的增强检索，依赖实体关系抽取 |
| Rerank | 召回后的重排序，提升 Top-N 精度 |
| HNSW | 近似最近邻索引算法，pgvector 场景用于加速 |
| Citation | 回答中引用来源的标注，前端以 popover / 引用抽屉呈现 |
| Recall Hit Rate | 召回命中率，内置 E2E 测试指标之一 |

## Agent 与工具

| 术语 | 含义 |
|------|------|
| ReAct | Reasoning + Acting 的多步推理范式，WeKnora 的 Agent 主循环 |
| Tool Calling | 工具调用，含内置工具、MCP 工具、Web 搜索 |
| MCP | Model Context Protocol，外部工具/服务的标准化接入协议 |
| Skill | 工作空间技能，可从 ClawHub / SkillHub / git / zip 安装 |
| Sandbox | 技能运行沙箱，支持 Docker / E2B / Cube，会话内持久 |
| chat steering | 对话过程中的打断与方向纠正 |
| Long-term Memory | 跨会话长期记忆，类型含 profile / preference / fact / task / interest |
| Wiki Mode | Agent 驱动的自动 Wiki 生成模式，产出互链 markdown 知识库 |

## 平台与运维

| 术语 | 含义 |
|------|------|
| Worker Pool Governance | 按阶段划分的 worker 池治理（core / post-process / enrichment / maintenance / elastic / wiki） |
| Governor | 按模型的后台并发控制器 |
| Langfuse | 唯一的链路追踪后端，覆盖 ReAct 循环、token、工具调用、解析流水线 |
| Embed Widget | 网站嵌入组件，支持域名白名单、限流、安全模式令牌交换 |
| SSRF-safe HTTP Client | 数据源 / URL 导入场景下的 SSRF 防护客户端 |
| OIDC | 身份认证协议，WeKnora 中涉及 ID-token JWKS 校验 |
