# 05 · Agent 与工具

## 学习目标

读懂 ReAct 主循环与工具体系，能新增一个工具 / MCP 服务 / Skill 并在会话中验证。

## 关键问题

- ReAct 循环的收敛判定、最大步数、失败重试策略？
- Prompt 如何组装：系统提示、工具描述、历史、检索上下文的注入顺序？
- 内置工具有哪些，各自契约是什么（`docs/agent-tools-design.md`）？
- MCP 客户端实现：stdio / SSE / HTTP 三种传输，OAuth2 远程服务与会话中途授权？
- Skill 沙箱：Docker / E2B / Cube 后端差异，会话持久化的实现？
- `@Skill` / `@MCP` 提及如何限定单轮运行时（`internal/modelcontext/`）？
- 流式输出与 chat steering（打断、纠偏）如何实现？
- 长任务如何通过 SSE / stream 推送到前端？

## Agent 循环草图

```text
用户输入 → 组装 Prompt → LLM 推理
   ├─ 需要工具 → 执行工具（内置 / MCP / Web / Sandbox） → 观察结果 → 回到推理
   └─ 收敛 → 生成带引用的回答 → 流式返回
```

## 笔记索引

| 笔记 | 说明 |
|------|------|
| _待补充_ | |

## 源码入口

| 关注点 | 路径 |
|--------|------|
| Agent 核心 | `internal/agent/` |
| 工具实现 | `internal/agent/`, `internal/mcp/` |
| 沙箱后端 | `internal/sandbox/`, `internal/container/` |
| 浏览器技能 | `internal/browserskill/` |
| 流式输出 | `internal/stream/` |
| 上下文管理 | `internal/modelcontext/` |

## 参考

- `docs/agent-tools-design.md`、`docs/agent-prompt-assembly.md`、`docs/agent-skills.md`
- `docs/MCP功能使用说明.md`、`docs/BUILTIN_MCP_SERVICES.md`、`docs/mcp-tool-directory.md`
- `docs/sandbox-docker-backend.md`、`docs/sandbox-protocol.md`、`docs/chat-steering.md`
