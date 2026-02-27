<!-- Parent: ../AGENTS.md -->
<!-- Generated: 2024-02-27 | Updated: 2024-02-27 -->

# cli

## Purpose
命令行界面模块，实现 nanobot 的 CLI 入口和所有命令。基于 Typer 框架，提供直观、易用的命令行接口。

## Key Files
| File | Description |
|------|-------------|
| `__init__.py` | CLI 包初始化 |
| `commands.py` | 所有 CLI 命令的实现，包括主入口和子命令 |

## Subdirectories
（无子目录）

## For AI Agents

### Working In This Directory
- 所有命令都在 `commands.py` 文件中实现，便于集中管理
- 使用 Typer 的装饰器定义命令
- 命令逻辑应委托给相应模块，保持 CLI 层薄
- 复杂命令使用内部辅助函数组织代码

### Testing Requirements
- CLI 命令需要集成测试
- 使用 Typer 的测试客户端
- 测试各种参数组合
- 测试交互模式和非交互模式

### Common Patterns
- 使用 `@app.command()` 定义命令
- 使用 `@app.async_command()` 定义异步命令
- 使用 `typer.Option` 定义选项
- 使用 `typer.Argument` 定义参数
- 子命令使用 `typer.Typer()` 创建并通过 `app.add_typer()` 添加
- 使用 Rich 库进行富文本输出

## Available Commands

### Core Commands
- `nanobot agent` - 启动交互式对话或单消息模式
- `nanobot gateway` - 启动网关服务
- `nanobot status` - 查看状态

### Configuration Commands
- `nanobot onboard` - 初始化配置
- `nanobot config` - 管理配置（当前未直接实现，通过 config 模块）

### Provider Commands
- `nanobot provider` - 管理 LLM 提供商（子命令组）
- `nanobot provider login` - OAuth 登录

### Channel Commands
- `nanobot channels` - 管理聊天渠道（子命令组）
- `nanobot channels status` - 查看渠道状态
- `nanobot channels login` - 渠道登录

### Task Commands
- `nanobot cron` - 管理定时任务（子命令组）
- `nanobot cron list` - 列出任务
- `nanobot cron add` - 添加任务
- `nanobot cron remove` - 删除任务
- `nanobot cron enable` - 启用/禁用任务
- `nanobot cron run` - 手动运行任务

## Dependencies

### Internal
- `agent/` - 智能体核心
- `config/` - 配置管理
- `channels/` - 渠道管理
- `providers/` - 提供商管理
- `bus/` - 消息总线
- `cron/` - 定时任务
- `heartbeat/` - 心跳服务

### External
- `typer` - CLI 框架
- `rich` - 富文本输出
- `prompt_toolkit` - 交互式输入处理
- `loguru` - 日志管理
- `asyncio` - 异步编程
- `pathlib` - 路径处理

## Command Structure Details

### Main Entry
- 文件: `commands.py`
- 使用 Typer 创建主应用: `app = typer.Typer()`
- 支持 `--version` 选项
- 所有命令通过装饰器注册

### Agent Command (`nanobot agent`)
- 支持单消息模式 (`--message`) 和交互模式
- 使用 prompt_toolkit 处理输入
- 支持会话管理 (`--session`)
- 支持 Markdown 渲染 (`--markdown/--no-markdown`)
- 支持日志显示 (`--logs/--no-logs`)

### Gateway Command (`nanobot gateway`)
- 启动完整的 nanobot 网关服务
- 支持端口配置 (`--port`)
- 支持详细输出 (`--verbose`)
- 管理所有通道、定时任务和心跳服务

### Onboard Command (`nanobot onboard`)
- 初始化配置文件
- 创建工作区目录结构
- 复制模板文件
- 指导用户完成初始设置

### Provider Commands
- `nanobot provider login` - OAuth 认证
- 支持 OpenAI Codex 和 GitHub Copilot 登录
- 使用 oauth_cli_kit 库处理 OAuth 流程

### Channel Commands
- `nanobot channels status` - 显示所有配置的通道状态
- `nanobot channels login` - 启动桥接服务进行设备配对
- 支持 WhatsApp、Discord、Feishu、Mochat、Telegram、Slack、DingTalk、QQ 和 Email 通道

### Cron Commands
- `nanobot cron list` - 列出任务，支持过滤已禁用任务
- `nanobot cron add` - 添加任务，支持 every/at/cron 三种调度类型
- `nanobot cron remove` - 删除任务
- `nanobot cron enable` - 启用/禁用任务
- `nanobot cron run` - 手动触发任务执行

## Code Organization in commands.py

### Helper Functions
- `_make_provider()` - 根据配置创建 LLM 提供商实例
- `_init_prompt_session()` - 初始化 prompt_toolkit 会话
- `_read_interactive_input_async()` - 读取用户输入
- `_print_agent_response()` - 格式化和输出代理响应
- `_create_workspace_templates()` - 创建工作区模板文件
- `_get_bridge_dir()` - 获取或初始化桥接服务目录
- `_register_login()` - 装饰器用于注册 OAuth 登录处理程序

### Internal State
- `_PROMPT_SESSION` - 全局 prompt_toolkit 会话对象
- `_SAVED_TERM_ATTRS` - 保存的终端属性，用于在退出时恢复
- `_LOGIN_HANDLERS` - 存储 OAuth 登录处理程序的字典
