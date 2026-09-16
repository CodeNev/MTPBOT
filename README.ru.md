
<!--
  MTPBOT — Фреймворк для Telegram-ботов через MTProto Proxy
  README.ru.md (Русский)
  Репозиторий: https://github.com/CodeNev/MTPBOT
-->

<div align="center">

# MTPBOT

**Фреймворк для Telegram-ботов через MTProto Proxy — асинхронный, модульный, готовый к продакшену.**

<!-- ===================== ПЕРЕКЛЮЧАТЕЛЬ ЯЗЫКОВ ===================== -->
🌍 **Языки:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇸🇦 العربية](README.ar.md) ·
[🇨🇳 中文](README.zh.md) ·

---

<!-- ===================== БЕЙДЖИ ===================== -->
[![Версия PyPI](https://img.shields.io/pypi/v/mtpbot.svg?style=for-the-badge&logo=pypi&logoColor=white&color=3775A9)](https://pypi.org/project/mtpbot/)
[![Python 3.14.7](https://img.shields.io/badge/python-3.14.7-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3147/)
[![Лицензия: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
[![Загрузки](https://img.shields.io/pypi/dm/mtpbot.svg?style=for-the-badge&logo=pypistats&logoColor=white&color=0A66C2)](https://pypistats.org/packages/mtpbot)
[![Звёзды GitHub](https://img.shields.io/github/stars/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white&color=yellow)](https://github.com/CodeNev/MTPBOT/stargazers)
[![Форки](https://img.shields.io/github/forks/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/network/members)
[![Issues](https://img.shields.io/github/issues/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/issues)

<!-- ===================== ВЕРСИИ ЗАВИСИМОСТЕЙ ===================== -->
[![Telethon](https://img.shields.io/badge/Telethon-1.44.0-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/Telethon/1.44.0/)
[![pytest](https://img.shields.io/badge/pytest-9.1.1-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest/9.1.1/)
[![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-1.4.0-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest-asyncio/1.4.0/)
[![Ruff](https://img.shields.io/badge/Ruff-0.15.20-000000.svg?style=for-the-badge&logo=ruff&logoColor=white)](https://pypi.org/project/ruff/0.15.20/)
[![mypy](https://img.shields.io/badge/mypy-2.1.0-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://pypi.org/project/mypy/2.1.0/)
[![cryptg](https://img.shields.io/badge/cryptg-0.6.0-2E8B57.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/cryptg/0.6.0/)

<!-- ===================== СТАТУС ===================== -->
[![Async](https://img.shields.io/badge/async-await-2E8B57.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/asyncio.html)
[![MTProto](https://img.shields.io/badge/protocol-MTProto-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/mtproto)
[![Type Checked](https://img.shields.io/badge/type--checked-mypy-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://mypy-lang.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
[![Сделано с ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-red.svg?style=for-the-badge)](#-благодарности)

**Чистый асинхронный интерфейс в стиле Bot API для Telegram-ботов, которым
нужно добираться до Telegram через MTProto Proxy — а не через HTTP-туннель.**

[Документация](docs/) · [Примеры](examples/) · [Changelog](CHANGELOG.md) · [Сообщить о баге](https://github.com/CodeNev/MTPBOT/issues)

</div>

---

## Содержание

- [Почему MTPBOT?](#-почему-mtpbot)
- [Возможности](#-возможности)
- [Архитектура](#-архитектура)
- [Установка](#-установка)
- [Быстрый старт](#-быстрый-старт)
- [Настройка MTProto Proxy](#-настройка-mtproto-proxy)
- [Переменные окружения](#-переменные-окружения)
- [Обработчики команд](#-обработчики-команд)
- [Обработчики сообщений](#-обработчики-сообщений)
- [Справочник API](#-справочник-api)
- [CLI](#-cli)
- [Обработка ошибок](#-обработка-ошибок)
- [Безопасность](#-безопасность)
- [Разработка](#-разработка)
- [Тестирование](#-тестирование)
- [Планы развития](#-планы-развития)
- [FAQ](#-faq)
- [Вклад в проект](#-вклад-в-проект)
- [Лицензия](#-лицензия)
- [Благодарности](#-благодарности)

---

## 🚀 Почему MTPBOT?

Во многих сетях официальная конечная точка Telegram Bot API
(`api.telegram.org`) фильтруется, ограничивается по скорости или полностью
блокируется. Традиционные обходные пути используют HTTP- или SOCKS-прокси,
которые шумные, легко идентифицируются и часто отключаются.

**MTProto-прокси говорят на родном протоколе Telegram.** Они быстрые,
устойчивые, их трудно обнаружить, и они широко развёрнуты. Проблема в том,
что их прямое использование требует реализации MTProto, рукопожатия
obfuscated2, вывода ключей AES-256-CTR и полноценного асинхронного слоя RPC.

**MTPBOT решает именно эту задачу.** Он даёт вам чистый, привычный
поверхностный слой в стиле Bot API поверх настоящего MTProto-клиента:

```python
@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT работает!")
```

…при этом трафик снизу — это настоящая зашифрованная MTProto-сессия,
проходящая через MTProto Proxy.

> ⚠️ **Важно:** MTPBOT — это **не** обёртка над HTTP. Он **не** пробрасывает
> вызовы `requests` или `aiohttp` через прокси. Он реализует настоящий
> протокол MTProto с помощью Telethon под капотом.

---

## ✨ Возможности

| Возможность | Статус |
|---|---|
| Настоящее MTProto-соединение через MTProto Proxy | ✅ |
| Рукопожатие obfuscated2 (секрет `dd`) | ✅ |
| Разбор FakeTLS-секрета (`ee`) | ✅ (разбор; откат во время работы) |
| Устаревший секрет abridged (`plain`) | ✅ |
| Асинхронный API изначально (`async` / `await`) | ✅ |
| Обработчики на декораторах (`@bot.command`, `@bot.on_message`) | ✅ |
| `message.reply(...)` и `bot.send_message(...)` | ✅ |
| `get_chat`, `get_user`, `get_me` | ✅ |
| Корректное завершение и авто-переподключение | ✅ |
| Таймауты и повторные попытки | ✅ |
| Отдельная иерархия исключений | ✅ |
| Скрытие токена и секрета в логах | ✅ |
| Поддержка переменных окружения | ✅ |
| CLI (`mtpbot run`, `mtpbot check`, `mtpbot version`) | ✅ |
| Python 3.14.7+ | ✅ |
| Полностью типизирован (`mypy --strict` без ошибок) | ✅ |
| Никаких лишних зависимостей | ✅ |

---

## 🧭 Архитектура

```
┌─────────────────────────┐
│  Ваш бот (async Python) │
└────────────┬────────────┘
             │  await bot.send_message(...)
             ▼
┌─────────────────────────┐
│        MTPBOT           │  ← поверхность в стиле Bot API
│ (обработчики, типы, CLI)│
└────────────┬────────────┘
             │  MTProto RPC
             ▼
┌─────────────────────────┐
│   MTProto-клиент        │  ← Telethon (obfuscated2, AES-256-CTR)
└────────────┬────────────┘
             │  зашифрованный TCP
             ▼
┌─────────────────────────┐
│    MTProto Proxy        │  ← dd / ee / plain
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│   Дата-центр Telegram   │
└─────────────────────────┘
```

### Структура пакета

```
mtpbot/
├── __init__.py        # Публичный API
├── bot.py             # Класс Bot, декораторы, жизненный цикл
├── client.py          # Обёртка Telethon (с учётом MTProxy)
├── mtproto.py         # Конфиг протокола, эндпоинты дата-центров
├── mtproxy.py         # MTProxy, parse_secret, proxy_from_dict
├── updates.py         # Преобразование событий → Message, диспетчер
├── methods.py         # send_message, get_chat, get_user, get_me
├── types.py           # User, Chat, Message, Update
├── handlers.py        # CommandHandler, MessageHandler, реестр
├── exceptions.py      # Полная иерархия исключений
├── utils.py           # Логирование, санитизация, помощники env
├── cli.py             # Точка входа CLI `mtpbot`
└── __main__.py        # `python -m mtpbot`
```

---

## 📦 Установка

### Из PyPI

```bash
pip install mtpbot
```

### Из исходников

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
pip install .
```

### Режим разработки

```bash
pip install -e ".[dev]"
```

### Опциональное ускорение

`cryptg` значительно ускоряет AES-IGE операции Telegram:

```bash
pip install "mtpbot[fast]"
```

### Требования

| Компонент | Минимум | Актуальная версия (на момент релиза) |
|---|---|---|
| Python | 3.14.7 | 3.14.7 |
| Telethon | 1.44.0 | 1.44.0 |
| pytest | 9.1.1 | 9.1.1 |
| pytest-asyncio | 1.4.0 | 1.4.0 |
| Ruff | 0.15.20 | 0.15.20 |
| mypy | 2.1.0 | 2.1.0 |
| cryptg | 0.6.0 | 0.6.0 |

---

## ⚡ Быстрый старт

Создайте файл `bot.py`. **Первая непустая строка должна быть маркером**
`# mtpbot run` — именно так CLI распознаёт корректный скрипт MTPBOT.

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
    await message.reply("MTPBOT работает через MTProto Proxy!")

bot.run()
```

Запуск:

```bash
mtpbot run bot.py
```

Проверка без запуска:

```bash
mtpbot check bot.py
```

---

## 🔐 Настройка MTProto Proxy

Прокси можно передать либо словарём, либо экземпляром `MTProxy`.

### Форма словаря

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

### Экземпляр `MTProxy`

```python
from mtpbot import Bot, MTProxy

proxy = MTProxy(
    server="1.2.3.4",
    port=443,
    secret="dd0123456789abcdef0123456789abcdef",
)

bot = Bot(token="BOT_TOKEN", proxy=proxy)
```

### Форматы секретов

| Префикс | Формат | Рукопожатие | Соединение Telethon |
|---------|--------|-------------|---------------------|
| `dd` | `dd` + 32 hex-символа | Randomized intermediate (obfuscated2) | `ConnectionTcpMTProxyRandomizedIntermediate` |
| `ee` | `ee` + 32 hex-символа + домен | FakeTLS | *Откат к randomized intermediate* |
| *(нет)* | 32 hex-символа | Устаревший abridged | `ConnectionTcpMTProxyAbridged` |

> **О FakeTLS:** Telethon не поддерживает FakeTLS из коробки. MTPBOT
> разбирает и проверяет секреты `ee`, логирует предупреждение и
> переключается на randomized intermediate. Поддержка настоящего
> FakeTLS-транспорта — в [планах развития](#-планы-развития).

### API `MTProxy`

```python
proxy.raw_secret        # bytes  (16 байт, без префикса)
proxy.secret_mode       # "dd" | "ee" | "plain"
proxy.connection_type   # Имя класса соединения Telethon
proxy.as_telethon_proxy()  # (server, port, secret)
proxy.to_dict()         # {'server': ..., 'port': ..., 'secret': ...}
```

---

## 🌱 Переменные окружения

Никогда не хардкодьте креденшелы. MTPBOT изначально дружелюбен к переменным
окружения.

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

Или с встроенными помощниками:

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

## 🎯 Обработчики команд

Регистрируйте обработчики команд декоратором `@bot.command(...)`.

```python
@bot.command("/start")
async def start(message):
    await message.reply("Добро пожаловать!")

@bot.command("/help")
async def help_cmd(message):
    await message.reply(
        "Доступные команды:\n"
        "/start — приветствие\n"
        "/help  — это сообщение\n"
        "/whoami — показать ваш ID"
    )

@bot.command("/whoami")
async def whoami(message):
    user = message.from_user
    await message.reply(f"Вы {user.full_name} (id={user.id})")
```

Обработчик получает объект `Message` со следующими полями:

- `message.text` — полный текст
- `message.command` — например, `"/start"`
- `message.command_args` — список аргументов
- `message.from_user` — объект `User`
- `message.chat_id`, `message.message_id`
- `await message.reply(...)`

Команды также работают с суффиксом `@botname` (`/start@mybot`).

---

## 💬 Обработчики сообщений

`@bot.on_message()` срабатывает для любого входящего сообщения, **не**
попавшего под обработчик команды.

```python
@bot.on_message()
async def echo(message):
    await message.reply(f"Вы сказали: {message.text}")
```

С предикатом для фильтрации:

```python
@bot.on_message(predicate=lambda m: m.text and "привет" in m.text.lower())
async def greet(message):
    await message.reply("Привет!")
```

> **Правило диспетчеризации:** если сработала команда, обработчики
> `on_message` для этого сообщения пропускаются. Это предотвращает
> циклы эха и двойную обработку.

---

## 📚 Справочник API

### `Bot`

| Метод / атрибут | Описание |
|---|---|
| `Bot(token, proxy=None, *, api_id=None, api_hash=None, timeout=30.0, connection_retries=5, retry_delay=5.0, log_level=20, session=None)` | Создать бота. |
| `bot.command(cmd)` | Декоратор для регистрации обработчика команды. |
| `bot.on_message(predicate=None)` | Декоратор для регистрации обработчика сообщения. |
| `await bot.start()` | Подключиться и зарегистрировать обработчики. |
| `await bot.stop()` | Корректно отключиться. |
| `await bot.send_message(chat_id, text, reply_to=None, parse_mode=None, silent=False)` | Отправить сообщение. |
| `await bot.get_chat(chat_id)` | Вернуть `Chat`. |
| `await bot.get_user(user_id)` | Вернуть `User`. |
| `await bot.get_me()` | Вернуть `User` самого бота. |
| `bot.run()` | Блокирующая точка входа (обрабатывает Ctrl-C). |
| `async with bot:` | Асинхронный контекстный менеджер. |

### `Message`

| Атрибут / метод | Описание |
|---|---|
| `message_id` | ID сообщения в Telegram. |
| `chat_id` | ID чата. |
| `text` | Текст сообщения. |
| `date` | `datetime`. |
| `from_user` | `User` или `None`. |
| `chat` | `Chat` или `None`. |
| `reply_to_message_id` | ID сообщения, на которое отвечают, если есть. |
| `command` | Имя команды, например `"/start"`. |
| `command_args` | Список аргументов. |
| `await message.reply(text, **kwargs)` | Ответить в том же чате. |
| `await message.reply_text(text, **kwargs)` | Псевдоним для `reply`. |

### `User` / `Chat`

Стандартные обёртки сущностей Telegram. `User.full_name` и
`Chat.display_name` — удобные свойства.

### `MTProxy`

См. [Настройка MTProto Proxy](#-настройка-mtproto-proxy).

### Исключения

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

MTPBOT поставляется с полноценным CLI.

```bash
mtpbot run bot.py            # Запустить файл бота
mtpbot check bot.py          # Проверить маркер, синтаксис, структуру
mtpbot version               # Показать версию
python -m mtpbot run bot.py  # Эквивалентная модульная форма
```

### `mtpbot check`

Проверяет, что целевой файл:

1. содержит маркер `# mtpbot run` в первой непустой строке,
2. парсится как корректный Python,
3. содержит создание `Bot(...)`,
4. вызывает `bot.run()`.

Код возврата: `0` при успехе, `1` при предупреждениях, `2` при фатальных
ошибках.

---

## 🛡 Обработка ошибок

Все ошибки наследуются от `MTPBOTError`, поэтому можно ловить широко или
узко.

```python
from mtpbot import Bot
from mtpbot.exceptions import InvalidSecretError, ConnectionError

try:
    bot = Bot(
        token="...",
        proxy={"server": "...", "port": 443, "secret": "bad"},
    )
except InvalidSecretError as exc:
    print("Неверный секрет прокси:", exc)

try:
    await bot.send_message(chat_id, "hi")
except ConnectionError as exc:
    print("Потеряно MTProto-соединение:", exc)
```

**Никогда не раскрывается в сообщениях исключений:**

- токен бота,
- секрет прокси,
- сырые MTProto-полезные нагрузки,
- креденшелы любого рода.

Сообщения исключений содержат только имя класса базовой ошибки.

---

## 🔒 Безопасность

MTPBOT относится к креденшелам как к первоклассным секретам.

- 🚫 **Токен бота никогда не логируется полностью.** `sanitize_token()`
  заменяет его на `<redacted-token>` до любой записи в лог.
- 🚫 **Секрет прокси никогда не логируется.** `MTProxy.__repr__` его
  пропускает, а `sanitize_secret()` заменяет его в строках лога.
- 🚫 **Никаких хардкод-креденшелов** в исходном дереве.
- ✅ **Поддержка переменных окружения** встроена.
- ✅ **Сообщения исключений** содержат только имя класса ошибки.
- ✅ **Сессии в памяти по умолчанию** — ничего не сохраняется на диск.

Если вы нашли проблему безопасности, **пожалуйста, не открывайте
публичный issue.** См.
[SECURITY.md](https://github.com/CodeNev/MTPBOT/blob/main/SECURITY.md).

---

## 🛠 Разработка

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT

python -m venv .venv
source .venv/bin/activate         # Windows: .venv\Scripts\activate

pip install -e ".[dev]"
pre-commit install
```

### Контроль качества

```bash
ruff check .          # Линтинг
ruff format --check . # Форматирование
mypy mtpbot           # Строгая проверка типов
pytest -q             # Тесты
```

Все четыре должны проходить до слияния PR.

---

## 🧪 Тестирование

```bash
pytest -q                    # Все тесты
pytest -q --cov=mtpbot       # С покрытием
pytest tests/test_mtproxy.py # Один модуль
```

### Карта покрытия

| Модуль | Что тестируется |
|---|---|
| `mtproxy.py` | Разбор секрета, валидация, выбор класса соединения, скрытие в `repr` |
| `handlers.py` | Регистрация обработчиков, сопоставление команд, принудительный async, порядок диспетчеризации |
| `types.py` | `Message.command`, `command_args`, защита `reply`, `User.full_name` |
| `exceptions.py` | Полная иерархия исключений |
| `bot.py` | Валидация токена, прокси словарём/экземпляром, конфиги по умолчанию |

Все тесты, затрагивающие сеть, используют mock. **Никакие реальные
креденшелы никогда не хранятся в репозитории.**

---

## 🗺 Планы развития

| Этап | Статус |
|---|---|
| v0.1 — MTProxy `dd` + `plain`, обработчики команд и сообщений, CLI | ✅ Выпущено |
| v0.2 — Нативная поддержка FakeTLS (`ee`) | 🚧 В работе |
| v0.3 — Инлайн-клавиатуры и callback-запросы | 📋 Запланировано |
| v0.4 — Медиа-методы (`send_photo`, `send_document`, `send_video`) | 📋 Запланировано |
| v0.5 — Постоянные хранилища сессий (SQLite, Redis) | 📋 Запланировано |
| v0.6 — Система плагинов | 📋 Запланировано |
| v1.0 — Стабильный API + полные типовые стабы | 🎯 Цель |

Голосуйте за приоритеты в
[Обсуждениях](https://github.com/CodeNev/MTPBOT/discussions).

---

## ❓ FAQ

<details>
<summary><b>MTPBOT — это замаскированный HTTP-клиент?</b></summary>

**Нет.** MTPBOT выполняет настоящее MTProto-рукопожатие через прокси с
помощью Telethon. Секрет прокси никогда не передаётся `requests`,
`aiohttp` или любой HTTP-библиотеке. Байты на проводе — это MTProto-кадры,
зашифрованные ключами AES-256-CTR, выведенными из секрета.
</details>

<details>
<summary><b>Можно ли использовать обычный токен Telegram Bot API?</b></summary>

Да. MTPBOT аутентифицируется как бот (`bot_token=...`) через MTProto,
поэтому вы используете тот же токен, что и с `python-telegram-bot` или
`aiogram`.
</details>

<details>
<summary><b>Нужен ли настоящий номер телефона?</b></summary>

Нет. Авторизация бота обходит интерактивный сценарий входа.
</details>

<details>
<summary><b>Почему мой `ee` (FakeTLS) прокси не подключается?</b></summary>

Telethon не реализует FakeTLS из коробки. MTPBOT разбирает и проверяет
секреты `ee`, но откатывается к randomized intermediate. Если ваш прокси
принимает только FakeTLS, установите FakeTLS-транспорт и переопределите
`MTPClient._resolve_connection_class`. Нативная поддержка — в планах.
</details>

<details>
<summary><b>Можно ли использовать SOCKS5-прокси?</b></summary>

В принципе да — но это *другая* задача и вне области проекта. MTPBOT
конкретно про MTProto-прокси.
</details>

---

## 🤝 Вклад в проект

Вклад приветствуется — от исправлений опечаток до полноценных функций.

1. Форкните репозиторий: https://github.com/CodeNev/MTPBOT/fork
2. Создайте ветку: `git checkout -b feat/my-feature`.
3. Добавьте тесты для своих изменений.
4. Запустите `ruff check .`, `mypy mtpbot` и `pytest -q`.
5. Откройте Pull Request с понятным описанием.

Сначала прочтите
[CONTRIBUTING.md](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
и
[CODE_OF_CONDUCT.md](https://github.com/CodeNev/MTPBOT/blob/main/CODE_OF_CONDUCT.md).

**Хорошие первые задачи** помечены меткой
[`good first issue`](https://github.com/CodeNev/MTPBOT/labels/good%20first%20issue).

---

## 📄 Лицензия

MTPBOT выпускается под **лицензией MIT**. Полный текст см. в
[LICENSE](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE).

```
MIT License — Copyright (c) 2026 MTPBOT Contributors
```

[![Лицензия: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)

---

## 🙏 Благодарности

MTPBOT стоит на плечах необычайного сообщества открытого исходного кода.
Искренняя благодарность:

- **[Telegram](https://telegram.org)** — за протокол MTProto, спецификацию
  рукопожатия obfuscated2 и дизайн MTProto Proxy, который делает
  устойчивую инфраструктуру ботов возможной.
- **[Telethon](https://github.com/LonamiWebs/Telethon)** — библиотека
  MTProto-клиента от [Lonami](https://github.com/LonamiWebs), которая
  обеспечивает настоящий криптографический транспорт, на котором построен
  MTPBOT. Без Telethon этот проект не существовал бы.
- **[Cryptg](https://github.com/cher-nov/cryptg)** — C-расширение,
  ускоряющее AES-IGE операции Telegram и делающее высоконагруженный
  трафик практичным.
- **[python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)**
  и **[aiogram](https://github.com/aiogram/aiogram)** — за вдохновение
  API обработчиков на декораторах, которое перенял MTPBOT.
- **[shields.io](https://shields.io)** — за красивые прозрачные бейджи,
  украшающие этот README.
- **[Astral](https://astral.sh)** — за **[Ruff](https://github.com/astral-sh/ruff)**
  и **[uv](https://github.com/astral-sh/uv)**, которые делают
  инструментарий Python быстрым и приятным.
- **[pytest](https://github.com/pytest-dev/pytest)** и
  **[pytest-asyncio](https://github.com/pytest-dev/pytest-asyncio)** — за
  опыт тестирования, который приносит удовольствие, а не burden.
- **[mypy](https://github.com/python/mypy)** — за то, что проверка типов
  стала первоклассной в Python.
- **Каждого контрибьютора, тестировщика и репортёра багов**, помогавшего
  формировать MTPBOT. Ваши issues, pull requests и терпение — то, что
  делает этот проект настоящим.

И наконец — **спасибо тебе, дорогой читатель**, за то, что рассматриваешь
MTPBOT для своего проекта. Пусть твои боты всегда остаются онлайн.

<div align="center">

---

**MTPBOT** · Сделано с ❤️ и здоровым уважением к криптографии.

Репозиторий: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

[⬆ Наверх](#mtpbot)

</div>
