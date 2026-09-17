# 08 · 部署与运维

## 学习目标

能在类生产环境部署 WeKnora，理解任务治理、可观测性与安全机制，具备基本排障能力。

## 关键问题

- Helm Chart 关键参数（副本数、资源、外部依赖开关）与生产化建议？
- 任务队列与 worker 池治理：core / post-process / enrichment / maintenance / elastic / wiki 的划分依据？
- 每模型后台并发治理（governor）如何避免模型侧限流？
- 运行时任务队列面板（队列深度、失败任务重试）背后的接口？
- Langfuse 集成：ReAct 链路、token 统计、工具调用、解析 trace 时间线如何查看？
- 安全机制：AES-256-GCM 静态加密与密钥轮换、SSRF 防护、gRPC TLS、Redis TLS、密钥脱敏？
- RBAC 落地：4 级角色矩阵、按资源归属、审计日志记录范围？
- 版本升级：数据库自动迁移机制、升级注意事项与回滚？

## 部署记录

| 项 | 值 |
|----|----|
| 环境 | |
| 部署方式 | Helm / Docker Compose |
| 向量库 | |
| 对象存储 | |
| 观测 | Langfuse 启用：是/否 |

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 排障速查

| 症状 | 排查方向 | 结论 |
|------|----------|------|
| 文档一直解析中 | worker 池、MQ、docreader 连通性 | |
| 检索结果为空 | 向量化是否成功、阈值是否过高 | |
| 回答无引用 | 引用开关、chunk 元数据 | |

## 参考

- `helm/`、`deploy/`、`docker/`、`migrations/`
- `docs/worker-pool-governance.md`、`docs/Langfuse集成.md`、`docs/RBAC说明.md`
- `docs/日志配置.md`、`docs/migration-troubleshooting.md`、`docs/sandbox-cluster.md`
- `SECURITY.md`
