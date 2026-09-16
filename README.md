
<!--
  MTPBOT — Telegram Bot framework over MTProto Proxy
  README.md (English)
  Repository: https://github.com/CodeNev/MTPBOT
-->

<div align="center">

# MTPBOT

**Telegram Bot framework over MTProto Proxy — async, modular, production-ready.**

<!-- ===================== LANGUAGE SWITCHER ===================== -->
🌍 **Languages:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇸🇦 العربية](README.ar.md) ·
[🇨🇳 中文](README.zh.md) ·
[🇷🇺 Русский](README.ru.md)

<!-- Replace the links above with your own URLs. -->

---

<!-- ===================== BADGES ===================== -->
[![PyPI version](https://img.shields.io/pypi/v/mtpbot.svg?style=for-the-badge&logo=pypi&logoColor=white&color=3775A9)](https://pypi.org/project/mtpbot/)
[![Python 3.14.7](https://img.shields.io/badge/python-3.14.7-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3147/)
[![License: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/CodeNev/MTPBOT/ci.yml?branch=main&style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/CodeNev/MTPBOT/actions)
[![Coverage](https://img.shields.io/codecov/c/github/CodeNev/MTPBOT.svg?style=for-the-badge&logo=codecov&logoColor=white)](https://codecov.io/gh/CodeNev/MTPBOT)
[![Downloads](https://img.shields.io/pypi/dm/mtpbot.svg?style=for-the-badge&logo=pypistats&logoColor=white&color=0A66C2)](https://pypistats.org/packages/mtpbot)
[![GitHub stars](https://img.shields.io/github/stars/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white&color=yellow)](https://github.com/CodeNev/MTPBOT/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/network/members)
[![GitHub issues](https://img.shields.io/github/issues/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/issues)

<!-- ===================== DEPENDENCY VERSIONS ===================== -->
[![Telethon](https://img.shields.io/badge/Telethon-1.44.0-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/Telethon/1.44.0/)
[![pytest](https://img.shields.io/badge/pytest-9.1.1-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest/9.1.1/)
[![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-1.4.0-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest-asyncio/1.4.0/)
[![Ruff](https://img.shields.io/badge/Ruff-0.15.20-000000.svg?style=for-the-badge&logo=ruff&logoColor=white)](https://pypi.org/project/ruff/0.15.20/)
[![mypy](https://img.shields.io/badge/mypy-2.1.0-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://pypi.org/project/mypy/2.1.0/)
[![cryptg](https://img.shields.io/badge/cryptg-0.6.0-2E8B57.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/cryptg/0.6.0/)

<!-- ===================== STATUS ===================== -->
[![Async](https://img.shields.io/badge/async-await-2E8B57.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/asyncio.html)
[![MTProto](https://img.shields.io/badge/protocol-MTProto-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/mtproto)
[![Type Checked](https://img.shields.io/badge/type--checked-mypy-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://mypy-lang.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
[![Made with ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-red.svg?style=for-the-badge)](#-acknowledgments)

**A clean, async, Bot-API-style interface for Telegram bots that must reach
Telegram through an MTProto Proxy — not an HTTP tunnel.**

[Documentation](docs/) · [Examples](examples/) · [Changelog](CHANGELOG.md) · [Report a bug](https://github.com/CodeNev/MTPBOT/issues)

</div>

---

## Table of Contents

- [Why MTPBOT](#-why-mtpbot)
- [Features](#-features)
- [Architecture](#-architecture)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [MTProto Proxy Configuration](#-mtproto-proxy-configuration)
- [Environment Variables](#-environment-variables)
- [Command Handlers](#-command-handlers)
- [Message Handlers](#-message-handlers)
- [API Reference](#-api-reference)
- [CLI](#-cli)
- [Error Handling](#-error-handling)
- [Security](#-security)
- [Development](#-development)
- [Testing](#-testing)
- [Roadmap](#-roadmap)
- [FAQ](#-faq)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

---

## 🚀 Why MTPBOT?

In many networks, the official Telegram Bot API endpoint (`api.telegram.org`)
is filtered, rate-limited, or outright blocked. Traditional workarounds use
HTTP or SOCKS proxies, which are noisy, easily fingerprinted, and often shut
down.

**MTProto proxies speak Telegram's own protocol.** They are fast, resilient,
hard to detect, and widely deployed. The problem: using them directly
requires implementing MTProto, the obfuscated2 handshake, AES-256-CTR key
derivation, and a full async RPC layer.

**MTPBOT solves exactly that.** It gives you a clean, familiar
Bot-API-style surface on top of a real MTProto client, so you can write:

```python
@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT is running!")
```

…while the traffic underneath is a genuine, encrypted MTProto session
routed through an MTProto Proxy.

> ⚠️ **Important:** MTPBOT is **not** an HTTP wrapper. It does **not**
> forward `requests` or `aiohttp` calls through the proxy. It performs the
> real MTProto protocol using Telethon under the hood.

---

## ✨ Features

| Feature | Status |
|---|---|
| Real MTProto connection through MTProto Proxy | ✅ |
| Obfuscated2 handshake (`dd` secret) | ✅ |
| FakeTLS secret parsing (`ee` secret) | ✅ (parsing; runtime fallback) |
| Legacy abridged secret (`plain`) | ✅ |
| Async-first API (`async` / `await`) | ✅ |
| Decorator-based handlers (`@bot.command`, `@bot.on_message`) | ✅ |
| `message.reply(...)` and `bot.send_message(...)` | ✅ |
| `get_chat`, `get_user`, `get_me` | ✅ |
| Graceful shutdown & auto-reconnect | ✅ |
| Timeouts and retries | ✅ |
| Dedicated exception hierarchy | ✅ |
| Token and secret redaction in logs | ✅ |
| Environment variable friendly | ✅ |
| CLI (`mtpbot run`, `mtpbot check`, `mtpbot version`) | ✅ |
| Python 3.14.7+ | ✅ |
| Fully typed (`mypy --strict` clean) | ✅ |
| Zero non-essential dependencies | ✅ |

---

## 🧭 Architecture

```
┌─────────────────────────┐
│  Your Bot (async Python)│
└────────────┬────────────┘
             │  await bot.send_message(...)
             ▼
┌─────────────────────────┐
│        MTPBOT           │  ← Bot API-style surface
│  (handlers, types, CLI) │
└────────────┬────────────┘
             │  MTProto RPC
             ▼
┌─────────────────────────┐
│   MTProto Client        │  ← Telethon (obfuscated2, AES-256-CTR)
└────────────┬────────────┘
             │  encrypted TCP
             ▼
┌─────────────────────────┐
│    MTProto Proxy        │  ← dd / ee / plain
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│       Telegram DC       │
└─────────────────────────┘
```

### Package layout

```
mtpbot/
├── __init__.py        # Public API surface
├── bot.py             # Bot class, decorators, lifecycle
├── client.py          # Telethon wrapper (MTProxy-aware)
├── mtproto.py         # Protocol config, DC endpoints
├── mtproxy.py         # MTProxy, parse_secret, proxy_from_dict
├── updates.py         # Event → Message conversion, dispatcher
├── methods.py         # send_message, get_chat, get_user, get_me
├── types.py           # User, Chat, Message, Update
├── handlers.py        # CommandHandler, MessageHandler, registry
├── exceptions.py      # Full exception hierarchy
├── utils.py           # Logging, sanitisation, env helpers
├── cli.py             # `mtpbot` command-line entry point
└── __main__.py        # `python -m mtpbot`
```

---

## 📦 Installation

### From PyPI

```bash
pip install mtpbot
```

### From source

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
pip install .
```

### Development mode

```bash
pip install -e ".[dev]"
```

### Optional performance boost

`cryptg` accelerates Telegram's AES-IGE operations significantly:

```bash
pip install "mtpbot[fast]"
```

### Requirements

| Component | Minimum | Latest (as of this release) |
|---|---|---|
| Python | 3.14.7 | 3.14.7 |
| Telethon | 1.44.0 | 1.44.0 |
| pytest | 9.1.1 | 9.1.1 |
| pytest-asyncio | 1.4.0 | 1.4.0 |
| Ruff | 0.15.20 | 0.15.20 |
| mypy | 2.1.0 | 2.1.0 |
| cryptg | 0.6.0 | 0.6.0 |

---

## ⚡ Quick Start

Create a file named `bot.py`. The **first non-empty line must be the
marker** `# mtpbot run` — this is how the CLI recognises a valid MTPBOT
script.

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
    await message.reply("MTPBOT is running through an MTProto proxy!")

bot.run()
```

Run it:

```bash
mtpbot run bot.py
```

Validate it without running:

```bash
mtpbot check bot.py
```

---

## 🔐 MTProto Proxy Configuration

You can pass the proxy either as a dictionary or as an `MTProxy` instance.

### Dictionary form

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

### `MTProxy` instance

```python
from mtpbot import Bot, MTProxy

proxy = MTProxy(
    server="1.2.3.4",
    port=443,
    secret="dd0123456789abcdef0123456789abcdef",
)

bot = Bot(token="BOT_TOKEN", proxy=proxy)
```

### Secret formats

| Prefix | Format | Handshake | Telethon connection |
|--------|--------|-----------|---------------------|
| `dd` | `dd` + 32 hex chars | Randomized intermediate (obfuscated2) | `ConnectionTcpMTProxyRandomizedIntermediate` |
| `ee` | `ee` + 32 hex chars + domain | FakeTLS | *Fallback to randomized intermediate* |
| *(none)* | 32 hex chars | Legacy abridged | `ConnectionTcpMTProxyAbridged` |

> **Note on FakeTLS:** Telethon does not natively support FakeTLS. MTPBOT
> parses `ee` secrets, validates them, and logs a warning before falling
> back to randomized intermediate. Support for a native FakeTLS transport
> is on the [roadmap](#-roadmap).

### `MTProxy` API

```python
proxy.raw_secret        # bytes  (16 bytes, no prefix)
proxy.secret_mode       # "dd" | "ee" | "plain"
proxy.connection_type   # Telethon connection class name
proxy.as_telethon_proxy()  # (server, port, secret)
proxy.to_dict()         # {'server': ..., 'port': ..., 'secret': ...}
```

---

## 🌱 Environment Variables

Never hard-code credentials. MTPBOT is env-var friendly by design.

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

Or using the built-in helpers:

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

## 🎯 Command Handlers

Register command handlers with the `@bot.command(...)` decorator.

```python
@bot.command("/start")
async def start(message):
    await message.reply("Welcome!")

@bot.command("/help")
async def help_cmd(message):
    await message.reply(
        "Available commands:\n"
        "/start — greet\n"
        "/help  — this message\n"
        "/whoami — show your id"
    )

@bot.command("/whoami")
async def whoami(message):
    user = message.from_user
    await message.reply(f"You are {user.full_name} (id={user.id})")
```

The handler receives a `Message` object with:

- `message.text` — full text
- `message.command` — e.g. `"/start"`
- `message.command_args` — list of arguments
- `message.from_user` — a `User`
- `message.chat_id`, `message.message_id`
- `await message.reply(...)`

Commands also work with the `@botname` suffix (`/start@mybot`).

---

## 💬 Message Handlers

`@bot.on_message()` fires for any incoming message that is **not** matched by
a command handler.

```python
@bot.on_message()
async def echo(message):
    await message.reply(f"You said: {message.text}")
```

Add a predicate to filter:

```python
@bot.on_message(predicate=lambda m: m.text and "hello" in m.text.lower())
async def greet(message):
    await message.reply("Hi there!")
```

> **Dispatch rule:** if a command matches, `on_message` handlers are skipped
> for that message. This prevents echo loops and accidental double-handling.

---

## 📚 API Reference

### `Bot`

| Method / Attribute | Description |
|---|---|
| `Bot(token, proxy=None, *, api_id=None, api_hash=None, timeout=30.0, connection_retries=5, retry_delay=5.0, log_level=20, session=None)` | Construct a bot. |
| `bot.command(cmd)` | Decorator to register a command handler. |
| `bot.on_message(predicate=None)` | Decorator to register a message handler. |
| `await bot.start()` | Connect and register handlers. |
| `await bot.stop()` | Disconnect gracefully. |
| `await bot.send_message(chat_id, text, reply_to=None, parse_mode=None, silent=False)` | Send a message. |
| `await bot.get_chat(chat_id)` | Return a `Chat`. |
| `await bot.get_user(user_id)` | Return a `User`. |
| `await bot.get_me()` | Return the bot's own `User`. |
| `bot.run()` | Blocking entry point (Ctrl-C aware). |
| `async with bot:` | Async context manager. |

### `Message`

| Attribute / Method | Description |
|---|---|
| `message_id` | Telegram message ID. |
| `chat_id` | Chat ID. |
| `text` | Message text. |
| `date` | `datetime`. |
| `from_user` | `User` or `None`. |
| `chat` | `Chat` or `None`. |
| `reply_to_message_id` | ID of the replied-to message, if any. |
| `command` | Command name, e.g. `"/start"`. |
| `command_args` | List of arguments. |
| `await message.reply(text, **kwargs)` | Reply in the same chat. |
| `await message.reply_text(text, **kwargs)` | Alias for `reply`. |

### `User` / `Chat`

Standard Telegram entity wrappers. `User.full_name` and
`Chat.display_name` are convenience properties.

### `MTProxy`

See [MTProto Proxy Configuration](#-mtproto-proxy-configuration).

### Exceptions

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

MTPBOT ships a first-class CLI.

```bash
mtpbot run bot.py            # Run a bot file
mtpbot check bot.py          # Validate marker, syntax, structure
mtpbot version               # Print version
python -m mtpbot run bot.py  # Equivalent module form
```

### `mtpbot check`

Verifies that the target file:

1. contains the `# mtpbot run` marker as its first non-empty line,
2. parses as valid Python,
3. contains a `Bot(...)` instantiation,
4. calls `bot.run()`.

Exit code is `0` on success, `1` on warnings, `2` on fatal errors.

---

## 🛡 Error Handling

All errors inherit from `MTPBOTError`, so you can catch broadly or narrowly.

```python
from mtpbot import Bot
from mtpbot.exceptions import InvalidSecretError, ConnectionError

try:
    bot = Bot(
        token="...",
        proxy={"server": "...", "port": 443, "secret": "bad"},
    )
except InvalidSecretError as exc:
    print("Proxy secret is invalid:", exc)

try:
    await bot.send_message(chat_id, "hi")
except ConnectionError as exc:
    print("Lost MTProto connection:", exc)
```

**Never exposed in exception messages:**

- the bot token,
- the proxy secret,
- raw MTProto payloads,
- credentials of any kind.

Exception messages contain only the class name of the underlying failure.

---

## 🔒 Security

MTPBOT treats credentials as first-class secrets.

- 🚫 **The bot token is never logged in full.** `sanitize_token()` replaces
  it with `<redacted-token>` before any log statement.
- 🚫 **The proxy secret is never logged.** `MTProxy.__repr__` omits it, and
  `sanitize_secret()` replaces it in log lines.
- 🚫 **No hard-coded credentials** anywhere in the source tree.
- ✅ **Environment variable support** built-in.
- ✅ **Exception messages** contain only the exception class name.
- ✅ **Memory sessions by default** — nothing persisted to disk.

If you find a security issue, **please do not open a public issue.** See
[SECURITY.md](https://github.com/CodeNev/MTPBOT/blob/main/SECURITY.md).

---

## 🛠 Development

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT

python -m venv .venv
source .venv/bin/activate         # Windows: .venv\Scripts\activate

pip install -e ".[dev]"
pre-commit install
```

### Quality gates

```bash
ruff check .          # Lint
ruff format --check . # Format
mypy mtpbot           # Strict type checking
pytest -q             # Tests
```

All four must pass before a PR is merged.

---

## 🧪 Testing

```bash
pytest -q                    # All tests
pytest -q --cov=mtpbot       # With coverage
pytest tests/test_mtproxy.py # Single module
```

### Coverage map

| Module | What is tested |
|---|---|
| `mtproxy.py` | Secret parsing, validation, connection-class selection, `repr` redaction |
| `handlers.py` | Handler registration, command matching, async enforcement, dispatch order |
| `types.py` | `Message.command`, `command_args`, `reply` guards, `User.full_name` |
| `exceptions.py` | Full exception hierarchy |
| `bot.py` | Token validation, dict/instance proxy, config defaults |

All network-touching tests use mocks. **No real credentials are stored in
the repository** — ever.

---

## 🗺 Roadmap

| Milestone | Status |
|---|---|
| v0.1 — MTProxy `dd` + `plain`, command & message handlers, CLI | ✅ Released |
| v0.2 — Native FakeTLS (`ee`) support | 🚧 In progress |
| v0.3 — Inline keyboards & callback queries | 📋 Planned |
| v0.4 — Media methods (`send_photo`, `send_document`, `send_video`) | 📋 Planned |
| v0.5 — Persistent session backends (SQLite, Redis) | 📋 Planned |
| v0.6 — Plugin system | 📋 Planned |
| v1.0 — Stable API + full type stubs | 🎯 Target |

Vote on priorities in [Discussions](https://github.com/CodeNev/MTPBOT/discussions).

---

## ❓ FAQ

<details>
<summary><b>Is MTPBOT an HTTP client in disguise?</b></summary>

**No.** MTPBOT performs a genuine MTProto handshake through the proxy using
Telethon. The proxy secret is never handed to `requests`, `aiohttp`, or any
HTTP library. The bytes on the wire are MTProto frames, encrypted with
AES-256-CTR keys derived from the secret.
</details>

<details>
<summary><b>Can I use this with a normal Telegram Bot API token?</b></summary>

Yes. MTPBOT authenticates as a bot (`bot_token=...`) over MTProto, so you use
the same token you would with `python-telegram-bot` or `aiogram`.
</details>

<details>
<summary><b>Do I need a real phone number?</b></summary>

No. Bot authorisation bypasses the interactive login flow.
</details>

<details>
<summary><b>Why does my `ee` (FakeTLS) proxy not connect?</b></summary>

Telethon does not natively implement FakeTLS. MTPBOT parses and validates
`ee` secrets but falls back to randomized intermediate. If your proxy only
accepts FakeTLS, install a FakeTLS transport and override
`MTPClient._resolve_connection_class`. Native support is on the roadmap.
</details>

<details>
<summary><b>Can I use a SOCKS5 proxy instead?</b></summary>

Yes, in principle — but that is a *different* problem and out of scope.
MTPBOT is specifically about MTProto proxies.
</details>

---

## 🤝 Contributing

Contributions are welcome — from typo fixes to full features.

1. Fork the repository: https://github.com/CodeNev/MTPBOT/fork
2. Create a branch: `git checkout -b feat/my-feature`.
3. Add tests for your change.
4. Run `ruff check .`, `mypy mtpbot`, and `pytest -q`.
5. Open a Pull Request with a clear description.

Please read [CONTRIBUTING.md](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
and [CODE_OF_CONDUCT.md](https://github.com/CodeNev/MTPBOT/blob/main/CODE_OF_CONDUCT.md)
first.

**Good first issues** are labelled
[`good first issue`](https://github.com/CodeNev/MTPBOT/labels/good%20first%20issue).

---

## 📄 License

MTPBOT is released under the **MIT License**. See
[LICENSE](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE) for the
full text.

```
MIT License — Copyright (c) 2026 MTPBOT Contributors
```

[![License: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)

---

## 🙏 Acknowledgments

MTPBOT stands on the shoulders of an extraordinary open-source community.
Sincere thanks to:

- **[Telegram](https://telegram.org)** — for the MTProto protocol, the
  obfuscated2 handshake specification, and the MTProto Proxy design that
  makes resilient bot infrastructure possible.
- **[Telethon](https://github.com/LonamiWebs/Telethon)** — the MTProto
  client library by [Lonami](https://github.com/LonamiWebs) that provides
  the real cryptographic transport MTPBOT builds upon. Without Telethon,
  this project would not exist.
- **[Cryptg](https://github.com/cher-nov/cryptg)** — the C extension that
  accelerates Telegram's AES-IGE operations and makes high-throughput
  traffic practical.
- **[python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)**
  and **[aiogram](https://github.com/aiogram/aiogram)** — for inspiring the
  decorator-based handler API that MTPBOT adopts.
- **[shields.io](https://shields.io)** — for the beautiful, transparent
  status badges powering this README.
- **[Astral](https://astral.sh)** — for **[Ruff](https://github.com/astral-sh/ruff)**
  and **[uv](https://github.com/astral-sh/uv)**, which make Python tooling
  fast and pleasant.
- **[pytest](https://github.com/pytest-dev/pytest)** and
  **[pytest-asyncio](https://github.com/pytest-dev/pytest-asyncio)** — for
  a testing experience that is a joy, not a chore.
- **[mypy](https://github.com/python/mypy)** — for making type checking
  first-class in Python.
- **Every contributor, tester, and bug reporter** who has helped shape
  MTPBOT. Your issues, pull requests, and patience are what make this
  project real.

And finally — **thank you, dear reader**, for considering MTPBOT for your
project. May your bots always stay online.

<div align="center">

---

**MTPBOT** · Built with ❤️ and a healthy respect for cryptography.

Repository: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

[⬆ Back to top](#mtpbot)

</div>
```

---

## What was changed

### 1. All GitHub URLs updated

Every reference to the old `mtpbot/mtpbot` organization was replaced with the real repository:

| Before | After |
|---|---|
| `github.com/mtpbot/mtpbot` | **`github.com/CodeNev/MTPBOT`** |
| `codecov.io/gh/mtpbot/mtpbot` | `codecov.io/gh/CodeNev/MTPBOT` |
| `github.com/mtpbot/mtpbot/labels/...` | `github.com/CodeNev/MTPBOT/labels/...` |
| `github.com/mtpbot/mtpbot/discussions` | `github.com/CodeNev/MTPBOT/discussions` |

### 2. License badge updated to MIT

The license badge now clearly states **MIT** and links directly to the LICENSE file:

```markdown
[![License: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
```

A second MIT badge was also added at the bottom, inside the License section itself.

### 3. Three new repository badges added

| Badge | Purpose |
|---|---|
| ⭐ GitHub stars | Shows community traction |
| 🍴 GitHub forks | Shows contribution activity |
| 🐛 GitHub issues | Links directly to the issue tracker |

### 4. All internal doc links now point to the correct repo

`SECURITY.md`, `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, and `LICENSE` links were rewritten from bare relative paths to absolute URLs pointing at `CodeNev/MTPBOT`.

### 5. Clone instructions fixed

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
```

### 6. Footer updated

The bottom of the README now shows the real repository URL:

> Repository: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

### 7. Language switcher preserved

The five-language switcher (English, فارسی, العربية, 中文, Русский) remains at the top with placeholder filenames you can point at your own translations.
