
<!--
  MTPBOT — 基于 MTProto Proxy 的 Telegram Bot 框架
  README.zh.md (简体中文)
  仓库地址: https://github.com/CodeNev/MTPBOT
-->

<div align="center">

# MTPBOT

**基于 MTProto Proxy 的 Telegram Bot 框架 — 异步、模块化、可用于生产环境。**

<!-- ===================== 语言切换器 ===================== -->
🌍 **语言 / Languages:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇸🇦 العربية](README.ar.md) ·
[🇷🇺 Русский](README.ru.md)

---

<!-- ===================== 徽章 ===================== -->
[![PyPI 版本](https://img.shields.io/pypi/v/mtpbot.svg?style=for-the-badge&logo=pypi&logoColor=white&color=3775A9)](https://pypi.org/project/mtpbot/)
[![Python 3.14.7](https://img.shields.io/badge/python-3.14.7-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3147/)
[![许可证: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
[![下载量](https://img.shields.io/pypi/dm/mtpbot.svg?style=for-the-badge&logo=pypistats&logoColor=white&color=0A66C2)](https://pypistats.org/packages/mtpbot)
[![GitHub 星标](https://img.shields.io/github/stars/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white&color=yellow)](https://github.com/CodeNev/MTPBOT/stargazers)
[![Fork 数](https://img.shields.io/github/forks/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/network/members)
[![Issue 数](https://img.shields.io/github/issues/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/issues)

<!-- ===================== 依赖版本 ===================== -->
[![Telethon](https://img.shields.io/badge/Telethon-1.44.0-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/Telethon/1.44.0/)
[![pytest](https://img.shields.io/badge/pytest-9.1.1-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest/9.1.1/)
[![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-1.4.0-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest-asyncio/1.4.0/)
[![Ruff](https://img.shields.io/badge/Ruff-0.15.20-000000.svg?style=for-the-badge&logo=ruff&logoColor=white)](https://pypi.org/project/ruff/0.15.20/)
[![mypy](https://img.shields.io/badge/mypy-2.1.0-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://pypi.org/project/mypy/2.1.0/)
[![cryptg](https://img.shields.io/badge/cryptg-0.6.0-2E8B57.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/cryptg/0.6.0/)

<!-- ===================== 状态 ===================== -->
[![异步](https://img.shields.io/badge/async-await-2E8B57.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/asyncio.html)
[![MTProto](https://img.shields.io/badge/protocol-MTProto-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/mtproto)
[![类型检查](https://img.shields.io/badge/type--checked-mypy-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://mypy-lang.org/)
[![欢迎 PR](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
[![用 ❤️ 构建](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-red.svg?style=for-the-badge)](#-致谢)

**为必须通过 MTProto Proxy 访问 Telegram 的机器人提供简洁、异步、类 Bot API 的接口
—— 而不是 HTTP 隧道。**

[文档](docs/) · [示例](examples/) · [更新日志](CHANGELOG.md) · [报告问题](https://github.com/CodeNev/MTPBOT/issues)

</div>

---

## 目录

- [为什么选择 MTPBOT？](#-为什么选择-mtpbot)
- [功能特性](#-功能特性)
- [架构](#-架构)
- [安装](#-安装)
- [快速开始](#-快速开始)
- [MTProto Proxy 配置](#-mtproto-proxy-配置)
- [环境变量](#-环境变量)
- [命令处理器](#-命令处理器)
- [消息处理器](#-消息处理器)
- [API 参考](#-api-参考)
- [CLI](#-cli)
- [错误处理](#-错误处理)
- [安全](#-安全)
- [开发](#-开发)
- [测试](#-测试)
- [路线图](#-路线图)
- [常见问题](#-常见问题)
- [贡献](#-贡献)
- [许可证](#-许可证)
- [致谢](#-致谢)

---

## 🚀 为什么选择 MTPBOT？

在许多网络环境中，Telegram Bot API 的官方端点（`api.telegram.org`）
会被过滤、限速甚至完全封锁。传统的绕过方式是使用 HTTP 或 SOCKS 代理，
但它们噪声大、容易被识别，并且经常被关闭。

**MTProto 代理使用 Telegram 自己的协议进行通信。** 它们快速、稳定、
难以检测，并且部署广泛。问题在于：直接使用它们需要实现 MTProto、
obfuscated2 握手、AES-256-CTR 密钥派生，以及完整的异步 RPC 层。

**MTPBOT 恰好解决了这个问题。** 它在真正的 MTProto 客户端之上，
为你提供简洁、熟悉的类 Bot API 接口，让你可以这样写：

```python
@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT 正在运行！")
```

……而其底层的流量，是真正经过加密、通过 MTProto Proxy 路由的
MTProto 会话。

> ⚠️ **重要说明：** MTPBOT **不是** HTTP 包装器。它**不会**把
> `requests` 或 `aiohttp` 调用通过代理转发。它在底层使用 Telethon
> 实现真正的 MTProto 协议。

---

## ✨ 功能特性

| 功能 | 状态 |
|---|---|
| 通过 MTProto Proxy 建立真实 MTProto 连接 | ✅ |
| Obfuscated2 握手（`dd` 密钥） | ✅ |
| FakeTLS 密钥解析（`ee` 密钥） | ✅（解析；运行时回退） |
| 旧版 abridged 密钥（`plain`） | ✅ |
| 原生异步 API（`async` / `await`） | ✅ |
| 基于装饰器的处理器（`@bot.command`、`@bot.on_message`） | ✅ |
| `message.reply(...)` 和 `bot.send_message(...)` | ✅ |
| `get_chat`、`get_user`、`get_me` | ✅ |
| 优雅关闭与自动重连 | ✅ |
| 超时与重试 | ✅ |
| 专属异常层级 | ✅ |
| 日志中隐藏 Token 与 Secret | ✅ |
| 支持环境变量 | ✅ |
| CLI（`mtpbot run`、`mtpbot check`、`mtpbot version`） | ✅ |
| Python 3.14.7 及以上 | ✅ |
| 完整类型标注（`mypy --strict` 无警告） | ✅ |
| 无多余依赖 | ✅ |

---

## 🧭 架构

```
┌─────────────────────────┐
│  你的 Bot（异步 Python） │
└────────────┬────────────┘
             │  await bot.send_message(...)
             ▼
┌─────────────────────────┐
│        MTPBOT           │  ← 类 Bot API 表面
│  （处理器、类型、CLI）   │
└────────────┬────────────┘
             │  MTProto RPC
             ▼
┌─────────────────────────┐
│   MTProto 客户端        │  ← Telethon（obfuscated2、AES-256-CTR）
└────────────┬────────────┘
             │  加密的 TCP
             ▼
┌─────────────────────────┐
│    MTProto Proxy        │  ← dd / ee / plain
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│     Telegram 数据中心   │
└─────────────────────────┘
```

### 包结构

```
mtpbot/
├── __init__.py        # 公共 API 表面
├── bot.py             # Bot 类、装饰器、生命周期
├── client.py          # Telethon 包装（感知 MTProxy）
├── mtproto.py         # 协议配置、数据中心端点
├── mtproxy.py         # MTProxy、parse_secret、proxy_from_dict
├── updates.py         # 事件 → Message 转换、分发器
├── methods.py         # send_message、get_chat、get_user、get_me
├── types.py           # User、Chat、Message、Update
├── handlers.py        # CommandHandler、MessageHandler、注册表
├── exceptions.py      # 完整异常层级
├── utils.py           # 日志、清洗、env 辅助
├── cli.py             # CLI 入口 `mtpbot`
└── __main__.py        # `python -m mtpbot`
```

---

## 📦 安装

### 从 PyPI 安装

```bash
pip install mtpbot
```

### 从源码安装

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
pip install .
```

### 开发模式

```bash
pip install -e ".[dev]"
```

### 可选的性能加速

`cryptg` 能显著加速 Telegram 的 AES-IGE 运算：

```bash
pip install "mtpbot[fast]"
```

### 依赖要求

| 组件 | 最低版本 | 最新版本（截至本次发布） |
|---|---|---|
| Python | 3.14.7 | 3.14.7 |
| Telethon | 1.44.0 | 1.44.0 |
| pytest | 9.1.1 | 9.1.1 |
| pytest-asyncio | 1.4.0 | 1.4.0 |
| Ruff | 0.15.20 | 0.15.20 |
| mypy | 2.1.0 | 2.1.0 |
| cryptg | 0.6.0 | 0.6.0 |

---

## ⚡ 快速开始

创建一个名为 `bot.py` 的文件。**第一个非空行必须是标记**
`# mtpbot run` —— CLI 正是通过它来识别合法的 MTPBOT 脚本。

```python
# mtpbot run

from mtpbot import Bot

bot = Bot(
    token="BOT_TOKEN",
    proxy={
        "server": "1.2.3.4",
        "port": 443,
        "secret": "dd0123456789abcdef0123456789abcdef",
    },
)

@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT 正通过 MTProto Proxy 运行！")

bot.run()
```

运行：

```bash
mtpbot run bot.py
```

只校验而不运行：

```bash
mtpbot check bot.py
```

---

## 🔐 MTProto Proxy 配置

你可以用字典或 `MTProxy` 实例来传入代理。

### 字典形式

```python
bot = Bot(
    token="BOT_TOKEN",
    proxy={
        "server": "1.2.3.4",
        "port": 443,
        "secret": "dd0123456789abcdef0123456789abcdef",
    },
)
```

### `MTProxy` 实例

```python
from mtpbot import Bot, MTProxy

proxy = MTProxy(
    server="1.2.3.4",
    port=443,
    secret="dd0123456789abcdef0123456789abcdef",
)

bot = Bot(token="BOT_TOKEN", proxy=proxy)
```

### 密钥格式

| 前缀 | 格式 | 握手方式 | Telethon 连接类 |
|--------|--------|-----------|---------------------|
| `dd` | `dd` + 32 位十六进制字符 | 随机化中间层（obfuscated2） | `ConnectionTcpMTProxyRandomizedIntermediate` |
| `ee` | `ee` + 32 位十六进制字符 + 域名 | FakeTLS | *回退到随机化中间层* |
| *（无）* | 32 位十六进制字符 | 旧版 abridged | `ConnectionTcpMTProxyAbridged` |

> **关于 FakeTLS 的说明：** Telethon 原生不支持 FakeTLS。MTPBOT 会
> 解析并校验 `ee` 密钥，记录一条警告，然后回退到随机化中间层。
> FakeTLS 原生传输的支持已列入[路线图](#-路线图)。

### `MTProxy` API

```python
proxy.raw_secret        # bytes（16 字节，无前缀）
proxy.secret_mode       # "dd" | "ee" | "plain"
proxy.connection_type   # Telethon 连接类名
proxy.as_telethon_proxy()  # (server, port, secret)
proxy.to_dict()         # {'server': ..., 'port': ..., 'secret': ...}
```

---

## 🌱 环境变量

永远不要把凭据硬编码到代码里。MTPBOT 从设计上就友好支持环境变量。

```python
import os
from mtpbot import Bot

bot = Bot(
    token=os.getenv("BOT_TOKEN"),
    proxy={
        "server": os.getenv("MTPROXY_SERVER"),
        "port": int(os.getenv("MTPROXY_PORT", "443")),
        "secret": os.getenv("MTPROXY_SECRET"),
    },
)
```

或使用内置辅助函数：

```python
from mtpbot import Bot
from mtpbot.utils import env, env_int

bot = Bot(
    token=env("BOT_TOKEN", required=True),
    proxy={
        "server": env("MTPROXY_SERVER", required=True),
        "port": env_int("MTPROXY_PORT", 443),
        "secret": env("MTPROXY_SECRET", required=True),
    },
)
```

---

## 🎯 命令处理器

使用 `@bot.command(...)` 装饰器注册命令处理器。

```python
@bot.command("/start")
async def start(message):
    await message.reply("欢迎！")

@bot.command("/help")
async def help_cmd(message):
    await message.reply(
        "可用命令：\n"
        "/start — 打招呼\n"
        "/help  — 本条消息\n"
        "/whoami — 显示你的 ID"
    )

@bot.command("/whoami")
async def whoami(message):
    user = message.from_user
    await message.reply(f"你是 {user.full_name}（id={user.id}）")
```

处理器会收到一个 `Message` 对象，它包含：

- `message.text` — 完整文本
- `message.command` — 例如 `"/start"`
- `message.command_args` — 参数列表
- `message.from_user` — 一个 `User`
- `message.chat_id`、`message.message_id`
- `await message.reply(...)`

命令也支持 `@botname` 后缀（`/start@mybot`）。

---

## 💬 消息处理器

`@bot.on_message()` 会对任何**未被命令处理器匹配**的入站消息触发。

```python
@bot.on_message()
async def echo(message):
    await message.reply(f"你说：{message.text}")
```

通过 predicate 添加过滤条件：

```python
@bot.on_message(predicate=lambda m: m.text and "你好" in m.text)
async def greet(message):
    await message.reply("你好！")
```

> **分发规则：** 如果命令匹配，则该消息的 `on_message` 处理器会被
> 跳过。这可以防止 echo 循环和重复处理。

---

## 📚 API 参考

### `Bot`

| 方法 / 属性 | 说明 |
|---|---|
| `Bot(token, proxy=None, *, api_id=None, api_hash=None, timeout=30.0, connection_retries=5, retry_delay=5.0, log_level=20, session=None)` | 构造一个 Bot。 |
| `bot.command(cmd)` | 注册命令处理器的装饰器。 |
| `bot.on_message(predicate=None)` | 注册消息处理器的装饰器。 |
| `await bot.start()` | 连接并注册处理器。 |
| `await bot.stop()` | 优雅断开连接。 |
| `await bot.send_message(chat_id, text, reply_to=None, parse_mode=None, silent=False)` | 发送消息。 |
| `await bot.get_chat(chat_id)` | 返回 `Chat`。 |
| `await bot.get_user(user_id)` | 返回 `User`。 |
| `await bot.get_me()` | 返回 Bot 自己的 `User`。 |
| `bot.run()` | 阻塞式入口（感知 Ctrl-C）。 |
| `async with bot:` | 异步上下文管理器。 |

### `Message`

| 属性 / 方法 | 说明 |
|---|---|
| `message_id` | Telegram 消息 ID。 |
| `chat_id` | 会话 ID。 |
| `text` | 消息文本。 |
| `date` | `datetime`。 |
| `from_user` | `User` 或 `None`。 |
| `chat` | `Chat` 或 `None`。 |
| `reply_to_message_id` | 被回复消息的 ID（若有）。 |
| `command` | 命令名，例如 `"/start"`。 |
| `command_args` | 参数列表。 |
| `await message.reply(text, **kwargs)` | 在同一会话中回复。 |
| `await message.reply_text(text, **kwargs)` | `reply` 的别名。 |

### `User` / `Chat`

标准的 Telegram 实体包装。`User.full_name` 与
`Chat.display_name` 是便捷属性。

### `MTProxy`

请参阅 [MTProto Proxy 配置](#-mtproto-proxy-配置)。

### 异常

```
MTPBOTError
├── ConfigurationError
├── MTProxyError
│   └── InvalidSecretError
├── InvalidTokenError
├── ConnectionError
├── UpdateError
└── HandlerError
    └── CommandNotFoundError
```

---

## 🖥 CLI

MTPBOT 自带一流的命令行工具。

```bash
mtpbot run bot.py            # 运行 Bot 文件
mtpbot check bot.py          # 校验标记、语法与结构
mtpbot version               # 打印版本
python -m mtpbot run bot.py  # 等价的模块调用形式
```

### `mtpbot check`

它会检查目标文件是否：

1. 首个非空行为 `# mtpbot run` 标记，
2. 能够作为合法 Python 解析，
3. 包含 `Bot(...)` 实例化，
4. 调用了 `bot.run()`。

退出码：成功为 `0`，有警告为 `1`，致命错误为 `2`。

---

## 🛡 错误处理

所有错误都继承自 `MTPBOTError`，因此你可以宽泛或精确地捕获。

```python
from mtpbot import Bot
from mtpbot.exceptions import InvalidSecretError, ConnectionError

try:
    bot = Bot(
        token="...",
        proxy={"server": "...", "port": 443, "secret": "bad"},
    )
except InvalidSecretError as exc:
    print("代理密钥无效：", exc)

try:
    await bot.send_message(chat_id, "hi")
except ConnectionError as exc:
    print("MTProto 连接中断：", exc)
```

**异常消息中绝不会暴露：**

- Bot Token，
- 代理密钥，
- 原始 MTProto 载荷，
- 任何形式的凭据。

异常消息只包含底层错误的类名。

---

## 🔒 安全

MTPBOT 将凭据视为一等公民的机密。

- 🚫 **Bot Token 从不完整写入日志。** `sanitize_token()` 在任何
  日志输出前将其替换为 `<redacted-token>`。
- 🚫 **代理密钥从不写入日志。** `MTProxy.__repr__` 会忽略它，
  而 `sanitize_secret()` 会在日志行中替换它。
- 🚫 **源码树中没有任何硬编码凭据。**
- ✅ **内置环境变量支持。**
- ✅ **异常消息**只包含异常类名。
- ✅ **默认使用内存会话** —— 不写入磁盘任何内容。

如果你发现了安全问题，**请不要公开发布 Issue。** 请参阅
[SECURITY.md](https://github.com/CodeNev/MTPBOT/blob/main/SECURITY.md)。

---

## 🛠 开发

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT

python -m venv .venv
source .venv/bin/activate         # Windows: .venv\Scripts\activate

pip install -e ".[dev]"
pre-commit install
```

### 质量关卡

```bash
ruff check .          # 静态检查
ruff format --check . # 格式检查
mypy mtpbot           # 严格类型检查
pytest -q             # 测试
```

在合并 PR 之前，这四项必须全部通过。

---

## 🧪 测试

```bash
pytest -q                    # 全部测试
pytest -q --cov=mtpbot       # 带覆盖率
pytest tests/test_mtproxy.py # 单个模块
```

### 覆盖率地图

| 模块 | 测试内容 |
|---|---|
| `mtproxy.py` | 密钥解析、校验、连接类选择、`repr` 隐藏 |
| `handlers.py` | 处理器注册、命令匹配、强制异步、分发顺序 |
| `types.py` | `Message.command`、`command_args`、`reply` 防护、`User.full_name` |
| `exceptions.py` | 完整异常层级 |
| `bot.py` | Token 校验、字典/实例代理、默认配置 |

所有涉及网络的测试都使用 mock。**仓库中绝不会存储任何真实凭据。**

---

## 🗺 路线图

| 里程碑 | 状态 |
|---|---|
| v0.1 — MTProxy `dd` + `plain`、命令与消息处理器、CLI | ✅ 已发布 |
| v0.2 — FakeTLS（`ee`）原生支持 | 🚧 进行中 |
| v0.3 — 内联键盘与回调查询 | 📋 计划中 |
| v0.4 — 媒体方法（`send_photo`、`send_document`、`send_video`） | 📋 计划中 |
| v0.5 — 持久会话后端（SQLite、Redis） | 📋 计划中 |
| v0.6 — 插件系统 | 📋 计划中 |
| v1.0 — 稳定 API + 完整类型 stub | 🎯 目标 |

请在 [Discussions](https://github.com/CodeNev/MTPBOT/discussions) 中
为优先级投票。

---

## ❓ 常见问题

<details>
<summary><b>MTPBOT 是伪装的 HTTP 客户端吗？</b></summary>

**不是。** MTPBOT 使用 Telethon 通过代理执行真实的 MTProto 握手。
代理密钥从不会交给 `requests`、`aiohttp` 或任何 HTTP 库。链路上传输的
字节是 MTProto 帧，使用由密钥派生的 AES-256-CTR 密钥加密。
</details>

<details>
<summary><b>我可以使用普通 Telegram Bot API Token 吗？</b></summary>

可以。MTPBOT 通过 MTProto 以 Bot 身份（`bot_token=...`）认证，
因此你使用的 Token 与 `python-telegram-bot` 或 `aiogram` 相同。
</details>

<details>
<summary><b>需要真实手机号吗？</b></summary>

不需要。Bot 授权会绕过交互式登录流程。
</details>

<details>
<summary><b>为什么我的 `ee`（FakeTLS）代理连不上？</b></summary>

Telethon 原生不实现 FakeTLS。MTPBOT 会解析并校验 `ee` 密钥，
但会回退到随机化中间层。如果你的代理只接受 FakeTLS，请安装
FakeTLS 传输并覆盖 `MTPClient._resolve_connection_class`。
原生支持已在路线图中。
</details>

<details>
<summary><b>我可以改用 SOCKS5 代理吗？</b></summary>

原则上可以 —— 但那是**另一个**问题，超出了本项目范围。MTPBOT
专门针对 MTProto 代理。
</details>

---

## 🤝 贡献

欢迎贡献 —— 从修正笔误到完整功能都欢迎。

1. Fork 仓库：https://github.com/CodeNev/MTPBOT/fork
2. 创建分支：`git checkout -b feat/my-feature`。
3. 为你的改动添加测试。
4. 运行 `ruff check .`、`mypy mtpbot` 和 `pytest -q`。
5. 提交描述清晰的 Pull Request。

请先阅读
[CONTRIBUTING.md](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
与
[CODE_OF_CONDUCT.md](https://github.com/CodeNev/MTPBOT/blob/main/CODE_OF_CONDUCT.md)。

**适合新手的问题**带有
[`good first issue`](https://github.com/CodeNev/MTPBOT/labels/good%20first%20issue)
标签。

---

## 📄 许可证

MTPBOT 采用 **MIT 许可证** 发布。完整文本请见
[LICENSE](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)。

```
MIT License — Copyright (c) 2026 MTPBOT Contributors
```

[![许可证: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)

---

## 🙏 致谢

MTPBOT 站在一个非凡的开源社区的肩膀上。衷心感谢：

- **[Telegram](https://telegram.org)** —— 提供了 MTProto 协议、
  obfuscated2 握手规范，以及使弹性 Bot 基础设施成为可能的
  MTProto Proxy 设计。
- **[Telethon](https://github.com/LonamiWebs/Telethon)** —— 由
  [Lonami](https://github.com/LonamiWebs) 开发的 MTProto 客户端库，
  提供了 MTPBOT 所构建的真实加密传输。没有 Telethon，本项目无从谈起。
- **[Cryptg](https://github.com/cher-nov/cryptg)** —— 加速 Telegram
  AES-IGE 运算、让高吞吐流量成为可能的 C 扩展。
- **[python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)**
  与 **[aiogram](https://github.com/aiogram/aiogram)** —— 为 MTPBOT
  采用的基于装饰器的处理器 API 提供了灵感。
- **[shields.io](https://shields.io)** —— 为本 README 提供了精美、
  透明的状态徽章。
- **[Astral](https://astral.sh)** —— 提供了 **[Ruff](https://github.com/astral-sh/ruff)**
  与 **[uv](https://github.com/astral-sh/uv)**，让 Python 工具链
  既快速又愉悦。
- **[pytest](https://github.com/pytest-dev/pytest)** 与
  **[pytest-asyncio](https://github.com/pytest-dev/pytest-asyncio)** ——
  让测试成为一种享受，而非负担。
- **[mypy](https://github.com/python/mypy)** —— 让类型检查在 Python 中
  成为一等公民。
- **每一位贡献者、测试者与 Bug 报告者** —— 你们塑造了 MTPBOT。
  你们的 Issue、Pull Request 与耐心，才是让这个项目真正存在的原因。

最后 —— **感谢你，亲爱的读者**，感谢你考虑用 MTPBOT 构建你的项目。
愿你的 Bot 永远在线。

<div align="center">

---

**MTPBOT** · 用 ❤️ 与对密码学的敬意构建。

仓库: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

[⬆ 回到顶部](#mtpbot)

</div>
