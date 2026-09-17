# 07 · 集成与扩展

## 学习目标

掌握对外接口与扩展点，能接入自有系统或按需扩展模型/数据源/渠道。

## 关键问题

- REST API 全貌：如何与 `docs/swagger.yaml` 对照阅读？鉴权头与错误码约定？
- Scoped API Key 的授权模型：能力级授权、按知识库限制、last-used 节流统计？
- IM 渠道（企业微信 / 飞书 / Slack / Telegram / 钉钉…）的统一抽象在哪一层？
- 数据源导入框架如何扩展一个新数据源？增量同步与全量同步的实现差异？
- 模型接入：LLM / Embedding / Rerank 适配层设计，内置模型 YAML 声明方式？
- 网站嵌入 Widget 的域名白名单、限流、安全模式令牌交换？
- `mcp-server`（`tencent-weknora-mcp`，29 个工具）如何暴露知识库能力？

## 扩展点清单

| 想扩展什么 | 改动位置 | 是否需改前端 |
|------------|----------|--------------|
| 新 LLM / Embedding provider | | |
| 新向量库 | | |
| 新数据源 | | |
| 新 IM 渠道 | | |
| 新 Agent 工具 | | |

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| HTTP handler | `internal/handler/` |
| 路由注册 | `internal/router/` |
| IM 集成 | `internal/im/` |
| 数据源 | `internal/datasource/` |
| 中间件（鉴权/限流） | `internal/middleware/`, `internal/ratelimit/` |
| MCP Server | `mcp-server/` |
| CLI | `cli/` |

## 参考

- `docs/swagger.yaml`、`docs/api/`、`docs/BUILTIN_MODELS.md`
- `docs/IM集成开发文档.md`、`docs/数据源导入开发文档.md`、`docs/添加新的网络搜索引擎.md`
- `docs/embed-secure-mode.md`、`docs/embed-subdomain.md`
