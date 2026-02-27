<!-- Generated: 2026-02-27 | Updated: 2026-02-27 -->

# nanobot

## Purpose
nanobot 是一个超轻量级的个人 AI 助手框架，灵感来自 OpenClaw。它用约 4000 行核心代码提供了完整的智能代理功能，比 Clawdbot 小 99%。nanobot 具有研究友好、快速、易于使用的特点，支持多种聊天平台和 LLM 提供商。

## Key Files
| File | Description |
|------|-------------|
| `pyproject.toml` | Python 项目配置和依赖 |
| `README.md` | 项目文档（包含安装、配置、使用说明） |
| `Dockerfile` | Docker 镜像配置 |
| `docker-compose.yml` | Docker Compose 配置 |
| `LICENSE` | 许可证文件（MIT） |
| `SECURITY.md` | 安全说明 |
| `COMMUNICATION.md` | 沟通渠道信息（微信群、Discord 等） |
| `core_agent_lines.sh` | 计算核心代码行数的脚本 |

## Subdirectories
| Directory | Purpose |
|-----------|---------|
| `nanobot/` | 主源代码包 (see `nanobot/AGENTS.md`) |
| `tests/` | 测试文件 (see `tests/AGENTS.md`) |
| `case/` | 示例案例 (see `case/AGENTS.md`) |
| `bridge/` | WhatsApp 桥接 (Node.js) (see `bridge/AGENTS.md`) |

## For AI Agents

### Working In This Directory
- 这是项目根目录，修改需谨慎
- 配置文件更改可能影响整个项目
- 遵循 Python 项目最佳实践

### Testing Requirements
- 运行 `pytest` 执行测试
- 运行 `ruff check .` 检查代码风格

### Common Patterns
- 使用 `async/await` 异步模式
- 遵循 Pydantic 数据验证模式

## Dependencies

### External
- `typer` - CLI 框架
- `litellm` - LLM 统一接口
- `pydantic` - 数据验证
- `pydantic-settings` - 配置管理
- `websockets` - WebSocket 通信
- `websocket-client` - WebSocket 客户端
- `httpx` - HTTP 客户端
- `oauth-cli-kit` - OAuth 认证
- `loguru` - 日志
- `readability-lxml` - HTML 内容提取
- `rich` - 富文本输出
- `croniter` - 定时任务
- `dingtalk-stream` - 钉钉集成
- `python-telegram-bot` - Telegram 集成
- `lark-oapi` - 飞书集成
- `socksio` - SOCKS 代理
- `python-socketio` - Socket.IO 通信
- `msgpack` - 消息序列化
- `slack-sdk` - Slack 集成
- `slackify-markdown` - Slack Markdown 转换
- `qq-botpy` - QQ 集成
- `python-socks` - SOCKS 代理
- `prompt-toolkit` - 交互式提示
- `mcp` - Model Context Protocol
- `json-repair` - JSON 修复

<!-- MANUAL: 可以在这里添加手动注释 -->
