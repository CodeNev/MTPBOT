
<!--
  MTPBOT — کتابخانهٔ ساخت ربات تلگرام روی MTProto Proxy
  README.fa.md (فارسی)
  مخزن: https://github.com/CodeNev/MTPBOT
-->

<div align="center" dir="rtl">

# MTPBOT

**کتابخانهٔ ساخت ربات تلگرام روی MTProto Proxy — async، ماژولار و آمادهٔ تولید.**

<!-- ===================== سوییچر زبان ===================== -->
🌍 **زبان‌ها:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇸🇦 العربية](README.ar.md) ·
[🇨🇳 中文](README.zh.md) ·
[🇷🇺 Русский](README.ru.md)

---

<!-- ===================== نشان‌ها ===================== -->
[![نسخهٔ PyPI](https://img.shields.io/pypi/v/mtpbot.svg?style=for-the-badge&logo=pypi&logoColor=white&color=3775A9)](https://pypi.org/project/mtpbot/)
[![پایتون 3.14.7](https://img.shields.io/badge/python-3.14.7-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3147/)
[![مجوز: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/CodeNev/MTPBOT/ci.yml?branch=main&style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/CodeNev/MTPBOT/actions)
[![پوشش تست](https://img.shields.io/codecov/c/github/CodeNev/MTPBOT.svg?style=for-the-badge&logo=codecov&logoColor=white)](https://codecov.io/gh/CodeNev/MTPBOT)
[![دانلودها](https://img.shields.io/pypi/dm/mtpbot.svg?style=for-the-badge&logo=pypistats&logoColor=white&color=0A66C2)](https://pypistats.org/packages/mtpbot)
[![ستاره‌های گیت‌هاب](https://img.shields.io/github/stars/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white&color=yellow)](https://github.com/CodeNev/MTPBOT/stargazers)
[![فورک‌ها](https://img.shields.io/github/forks/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/network/members)
[![ایشوها](https://img.shields.io/github/issues/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/issues)

<!-- ===================== نسخهٔ وابستگی‌ها ===================== -->
[![Telethon](https://img.shields.io/badge/Telethon-1.44.0-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/Telethon/1.44.0/)
[![pytest](https://img.shields.io/badge/pytest-9.1.1-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest/9.1.1/)
[![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-1.4.0-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest-asyncio/1.4.0/)
[![Ruff](https://img.shields.io/badge/Ruff-0.15.20-000000.svg?style=for-the-badge&logo=ruff&logoColor=white)](https://pypi.org/project/ruff/0.15.20/)
[![mypy](https://img.shields.io/badge/mypy-2.1.0-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://pypi.org/project/mypy/2.1.0/)
[![cryptg](https://img.shields.io/badge/cryptg-0.6.0-2E8B57.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/cryptg/0.6.0/)

<!-- ===================== وضعیت ===================== -->
[![Async](https://img.shields.io/badge/async-await-2E8B57.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/asyncio.html)
[![MTProto](https://img.shields.io/badge/protocol-MTProto-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/mtproto)
[![بررسی نوع](https://img.shields.io/badge/type--checked-mypy-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://mypy-lang.org/)
[![خوش‌آمدید](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
[![ساخته‌شده با ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-red.svg?style=for-the-badge)](#-سپاسگزاری)

**یک رابط تمیز، async و شبیه Bot API برای ربات‌های تلگرامی که باید از طریق
MTProto Proxy به تلگرام متصل شوند — نه یک تونل HTTP.**

[مستندات](docs/) · [نمونه‌ها](examples/) · [تغییرات](CHANGELOG.md) · [گزارش باگ](https://github.com/CodeNev/MTPBOT/issues)

</div>

---

## فهرست مطالب

- [چرا MTPBOT؟](#-چرا-mtpbot)
- [قابلیت‌ها](#-قابلیتها)
- [معماری](#-معماری)
- [نصب](#-نصب)
- [شروع سریع](#-شروع-سریع)
- [پیکربندی MTProto Proxy](#-پیکربندی-mtproto-proxy)
- [متغیرهای محیطی](#-متغیرهای-محیطی)
- [هندلرهای دستور](#-هندلرهای-دستور)
- [هندلرهای پیام](#-هندلرهای-پیام)
- [مرجع API](#-مرجع-api)
- [CLI](#-cli)
- [مدیریت خطا](#-مدیریت-خطا)
- [امنیت](#-امنیت)
- [توسعه](#-توسعه)
- [تست](#-تست)
- [نقشهٔ راه](#-نقشهٔ-راه)
- [سؤالات متداول](#-سؤالات-متداول)
- [مشارکت](#-مشارکت)
- [مجوز](#-مجوز)
- [سپاسگزاری](#-سپاسگزاری)

---

## 🚀 چرا MTPBOT؟

در بسیاری از شبکه‌ها، نقطهٔ پایانی رسمی Bot API تلگرام (`api.telegram.org`)
فیلتر، محدود به نرخ، یا به‌طور کامل مسدود شده است. راه‌حل‌های سنتی از
پروکسی‌های HTTP یا SOCKS استفاده می‌کنند که پر سر و صدا، قابل‌شناسایی و
اغلب زودگذر هستند.

**پروکسی‌های MTProto خود پروتکل تلگرام را صحبت می‌کنند.** سریع، مقاوم، سخت
قابل شناسایی و به‌طور گسترده مستقر هستند. مشکل اینجاست: استفادهٔ مستقیم از
آن‌ها مستلزم پیاده‌سازی MTProto، دست‌دادن obfuscated2، استخراج کلید
AES-256-CTR و یک لایهٔ RPC کامل async است.

**MTPBOT دقیقاً همین را حل می‌کند.** این کتابخانه یک سطح تمیز و آشنا شبیه
Bot API روی یک کلاینت واقعی MTProto فراهم می‌کند، طوری که می‌توانید بنویسید:

```python
@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT در حال اجراست!")
```

…در حالی که در زیر کاپوت، ترافیک یک نشست واقعی، رمزنگاری‌شده و MTProto
است که از یک MTProto Proxy عبور می‌کند.

> ⚠️ **مهم:** MTPBOT یک wrapper روی HTTP **نیست**. این کتابخانه
> درخواست‌های `requests` یا `aiohttp` را از پروکسی عبور **نمی‌دهد**.
> این کتابخانه پروتکل واقعی MTProto را با استفاده از Telethon پیاده‌سازی
> می‌کند.

---

## ✨ قابلیت‌ها

| قابلیت | وضعیت |
|---|---|
| اتصال واقعی MTProto از طریق MTProto Proxy | ✅ |
| دست‌دادن obfuscated2 (سکرت `dd`) | ✅ |
| پارس سکرت FakeTLS (سکرت `ee`) | ✅ (پارس؛ بازگشت در زمان اجرا) |
| سکرت legacy abridged (`plain`) | ✅ |
| API مبتنی بر async (`async` / `await`) | ✅ |
| هندلرهای دکوراتوری (`@bot.command` و `@bot.on_message`) | ✅ |
| `message.reply(...)` و `bot.send_message(...)` | ✅ |
| `get_chat`، `get_user`، `get_me` | ✅ |
| خاموشی نرم و اتصال مجدد خودکار | ✅ |
| Timeout و Retry | ✅ |
| سلسله‌مراتب اختصاصی استثناها | ✅ |
| مخفی‌سازی Token و Secret در لاگ‌ها | ✅ |
| سازگار با متغیرهای محیطی | ✅ |
| CLI (`mtpbot run`، `mtpbot check`، `mtpbot version`) | ✅ |
| پایتون 3.14.7 به بالا | ✅ |
| تایپ کامل (`mypy --strict` بدون خطا) | ✅ |
| بدون وابستگی غیرضروری | ✅ |

---

## 🧭 معماری

```
┌─────────────────────────┐
│  ربات شما (پایتون async) │
└────────────┬────────────┘
             │  await bot.send_message(...)
             ▼
┌─────────────────────────┐
│        MTPBOT           │  ← سطح شبیه Bot API
│ (هندلرها، تایپ‌ها، CLI)  │
└────────────┬────────────┘
             │  MTProto RPC
             ▼
┌─────────────────────────┐
│     کلاینت MTProto      │  ← Telethon (obfuscated2، AES-256-CTR)
└────────────┬────────────┘
             │  TCP رمزنگاری‌شده
             ▼
┌─────────────────────────┐
│    MTProto Proxy        │  ← dd / ee / plain
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│      دیتاسنتر تلگرام    │
└─────────────────────────┘
```

### ساختار پکیج

```
mtpbot/
├── __init__.py        # سطح عمومی API
├── bot.py             # کلاس Bot، دکوراتورها، چرخهٔ حیات
├── client.py          # پوشش Telethon (آگاه از MTProxy)
├── mtproto.py         # پیکربندی پروتکل، نقاط پایانی دیتاسنتر
├── mtproxy.py         # MTProxy، parse_secret، proxy_from_dict
├── updates.py         # تبدیل رخداد به Message، توزیع‌کننده
├── methods.py         # send_message، get_chat، get_user، get_me
├── types.py           # User، Chat، Message، Update
├── handlers.py        # CommandHandler، MessageHandler، رجیستری
├── exceptions.py      # سلسله‌مراتب کامل استثناها
├── utils.py           # لاگ، پاک‌سازی، کمک‌کننده‌های env
├── cli.py             # نقطهٔ ورود CLI `mtpbot`
└── __main__.py        # `python -m mtpbot`
```

---

## 📦 نصب

### از PyPI

```bash
pip install mtpbot
```

### از سورس

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
pip install .
```

### حالت توسعه

```bash
pip install -e ".[dev]"
```

### تقویت اختیاری عملکرد

`cryptg` عملیات AES-IGE تلگرام را به‌طور چشمگیری سریع‌تر می‌کند:

```bash
pip install "mtpbot[fast]"
```

### پیش‌نیازها

| مؤلفه | حداقل | آخرین نسخه (تا این انتشار) |
|---|---|---|
| پایتون | 3.14.7 | 3.14.7 |
| Telethon | 1.44.0 | 1.44.0 |
| pytest | 9.1.1 | 9.1.1 |
| pytest-asyncio | 1.4.0 | 1.4.0 |
| Ruff | 0.15.20 | 0.15.20 |
| mypy | 2.1.0 | 2.1.0 |
| cryptg | 0.6.0 | 0.6.0 |

---

## ⚡ شروع سریع

فایلی به نام `bot.py` بسازید. **اولین خط غیرخالی باید خط نشانگر**
`# mtpbot run` باشد — این خط به CLI می‌گوید فایل یک اسکریپت معتبر
MTPBOT است.

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
    await message.reply("MTPBOT از طریق MTProto Proxy در حال اجراست!")

bot.run()
```

اجرا:

```bash
mtpbot run bot.py
```

اعتبارسنجی بدون اجرا:

```bash
mtpbot check bot.py
```

---

## 🔐 پیکربندی MTProto Proxy

می‌توانید پروکسی را به‌صورت دیکشنری یا نمونهٔ `MTProxy` بدهید.

### شکل دیکشنری

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

### نمونهٔ `MTProxy`

```python
from mtpbot import Bot, MTProxy

proxy = MTProxy(
    server="1.2.3.4",
    port=443,
    secret="dd0123456789abcdef0123456789abcdef",
)

bot = Bot(token="BOT_TOKEN", proxy=proxy)
```

### فرمت‌های سکرت

| پیشوند | فرمت | دست‌دادن | اتصال Telethon |
|--------|------|----------|----------------|
| `dd` | `dd` + ۳۲ کاراکتر hex | Randomized intermediate (obfuscated2) | `ConnectionTcpMTProxyRandomizedIntermediate` |
| `ee` | `ee` + ۳۲ کاراکتر hex + دامنه | FakeTLS | *بازگشت به randomized intermediate* |
| *(بدون پیشوند)* | ۳۲ کاراکتر hex | Legacy abridged | `ConnectionTcpMTProxyAbridged` |

> **نکته در مورد FakeTLS:** Telethon به‌طور بومی از FakeTLS پشتیبانی
> نمی‌کند. MTPBOT سکرت‌های `ee` را پارس و اعتبارسنجی می‌کند، هشدار
> می‌دهد و سپس به randomized intermediate بازمی‌گردد. پشتیبانی بومی از
> FakeTLS در [نقشهٔ راه](#-نقشهٔ-راه) قرار دارد.

### API کلاس `MTProxy`

```python
proxy.raw_secret        # bytes  (۱۶ بایت، بدون پیشوند)
proxy.secret_mode       # "dd" | "ee" | "plain"
proxy.connection_type   # نام کلاس اتصال Telethon
proxy.as_telethon_proxy()  # (server, port, secret)
proxy.to_dict()         # {'server': ..., 'port': ..., 'secret': ...}
```

---

## 🌱 متغیرهای محیطی

هرگز اعتبارنامه‌ها را hard-code نکنید. MTPBOT به‌طور طراحی‌شده با
متغیرهای محیطی سازگار است.

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

یا با استفاده از کمک‌کننده‌های داخلی:

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

## 🎯 هندلرهای دستور

هندلرهای دستور را با دکوراتور `@bot.command(...)` ثبت کنید.

```python
@bot.command("/start")
async def start(message):
    await message.reply("خوش آمدید!")

@bot.command("/help")
async def help_cmd(message):
    await message.reply(
        "دستورات موجود:\n"
        "/start — سلام\n"
        "/help  — همین پیام\n"
        "/whoami — نمایش شناسهٔ شما"
    )

@bot.command("/whoami")
async def whoami(message):
    user = message.from_user
    await message.reply(f"شما {user.full_name} هستید (id={user.id})")
```

هندلر یک شیء `Message` دریافت می‌کند که این‌ها را دارد:

- `message.text` — متن کامل
- `message.command` — مثلاً `"/start"`
- `message.command_args` — فهرست آرگومان‌ها
- `message.from_user` — یک `User`
- `message.chat_id`، `message.message_id`
- `await message.reply(...)`

دستورها با پسوند `@botname` نیز کار می‌کنند (`/start@mybot`).

---

## 💬 هندلرهای پیام

`@bot.on_message()` برای هر پیام ورودی که با یک هندلر دستور تطبیق داده
**نشده باشد** اجرا می‌شود.

```python
@bot.on_message()
async def echo(message):
    await message.reply(f"شما گفتید: {message.text}")
```

برای فیلتر کردن، predicate اضافه کنید:

```python
@bot.on_message(predicate=lambda m: m.text and "سلام" in m.text)
async def greet(message):
    await message.reply("سلام!")
```

> **قانون توزیع:** اگر یک دستور تطبیق داده شود، هندلرهای `on_message`
> برای آن پیام نادیده گرفته می‌شوند. این کار از حلقه‌های echo و
> پردازش مضاعف جلوگیری می‌کند.

---

## 📚 مرجع API

### `Bot`

| متد / ویژگی | توضیحات |
|---|---|
| `Bot(token, proxy=None, *, api_id=None, api_hash=None, timeout=30.0, connection_retries=5, retry_delay=5.0, log_level=20, session=None)` | ساخت یک ربات. |
| `bot.command(cmd)` | دکوراتور ثبت هندلر دستور. |
| `bot.on_message(predicate=None)` | دکوراتور ثبت هندلر پیام. |
| `await bot.start()` | اتصال و ثبت هندلرها. |
| `await bot.stop()` | قطع اتصال به‌صورت نرم. |
| `await bot.send_message(chat_id, text, reply_to=None, parse_mode=None, silent=False)` | ارسال پیام. |
| `await bot.get_chat(chat_id)` | بازگرداندن `Chat`. |
| `await bot.get_user(user_id)` | بازگرداندن `User`. |
| `await bot.get_me()` | بازگرداندن `User` مربوط به خود ربات. |
| `bot.run()` | نقطهٔ ورود مسدودکننده (با کنترل Ctrl-C). |
| `async with bot:` | مدیریت زمینهٔ async. |

### `Message`

| ویژگی / متد | توضیحات |
|---|---|
| `message_id` | شناسهٔ پیام تلگرام. |
| `chat_id` | شناسهٔ چت. |
| `text` | متن پیام. |
| `date` | `datetime`. |
| `from_user` | `User` یا `None`. |
| `chat` | `Chat` یا `None`. |
| `reply_to_message_id` | شناسهٔ پیام پاسخ‌داده‌شده، در صورت وجود. |
| `command` | نام دستور، مثلاً `"/start"`. |
| `command_args` | فهرست آرگومان‌ها. |
| `await message.reply(text, **kwargs)` | پاسخ در همان چت. |
| `await message.reply_text(text, **kwargs)` | نام مستعار برای `reply`. |

### `User` / `Chat`

پوشش‌های استاندارد موجودیت تلگرام. `User.full_name` و
`Chat.display_name` ویژگی‌های راحتی هستند.

### `MTProxy`

به بخش [پیکربندی MTProto Proxy](#-پیکربندی-mtproto-proxy) مراجعه کنید.

### استثناها

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

MTPBOT یک CLI درجه‌یک دارد.

```bash
mtpbot run bot.py            # اجرای یک فایل ربات
mtpbot check bot.py          # اعتبارسنجی نشانگر، سینتکس، ساختار
mtpbot version               # نمایش نسخه
python -m mtpbot run bot.py  # فرم ماژولی معادل
```

### `mtpbot check`

بررسی می‌کند که فایل هدف:

1. خط نشانگر `# mtpbot run` را به‌عنوان اولین خط غیرخالی داشته باشد،
2. به‌عنوان پایتون معتبر پارس شود،
3. شامل یک نمونه‌سازی `Bot(...)` باشد،
4. متد `bot.run()` را فراخوانی کند.

کد خروج در صورت موفقیت `0`، در صورت هشدار `1` و در خطاهای مهلک `2` است.

---

## 🛡 مدیریت خطا

همهٔ خطاها از `MTPBOTError` ارث‌بری می‌کنند، بنابراین می‌توانید به‌صورت
گسترده یا خاص بگیرید.

```python
from mtpbot import Bot
from mtpbot.exceptions import InvalidSecretError, ConnectionError

try:
    bot = Bot(
        token="...",
        proxy={"server": "...", "port": 443, "secret": "bad"},
    )
except InvalidSecretError as exc:
    print("سکرت پروکسی نامعتبر است:", exc)

try:
    await bot.send_message(chat_id, "hi")
except ConnectionError as exc:
    print("اتصال MTProto از دست رفت:", exc)
```

**هرگز در پیام‌های استثنا نمایش داده نمی‌شود:**

- توکن ربات،
- سکرت پروکسی،
- محتوای خام MTProto،
- اعتبارنامه‌ها به هر شکل.

پیام‌های استثنا فقط نام کلاس خطای زیرین را در خود دارند.

---

## 🔒 امنیت

MTPBOT اعتبارنامه‌ها را به‌عنوان دادهٔ حساس درجه‌یک در نظر می‌گیرد.

- 🚫 **توکن ربات هرگز به‌طور کامل لاگ نمی‌شود.** تابع
  `sanitize_token()` آن را قبل از هر لاگ با `<redacted-token>`
  جایگزین می‌کند.
- 🚫 **سکرت پروکسی هرگز لاگ نمی‌شود.** `MTProxy.__repr__` آن را حذف
  می‌کند و `sanitize_secret()` در خطوط لاگ جایگزینش می‌کند.
- 🚫 **هیچ اعتبارنامه‌ای hard-code نشده** در درخت سورس.
- ✅ **پشتیبانی از متغیرهای محیطی** به‌صورت داخلی.
- ✅ **پیام‌های استثنا** فقط شامل نام کلاس خطا هستند.
- ✅ **نشست‌های حافظه‌ای به‌طور پیش‌فرض** — چیزی روی دیسک ذخیره
  نمی‌شود.

اگر یک مشکل امنیتی پیدا کردید، **لطفاً issue عمومی باز نکنید.** به
[SECURITY.md](https://github.com/CodeNev/MTPBOT/blob/main/SECURITY.md)
مراجعه کنید.

---

## 🛠 توسعه

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT

python -m venv .venv
source .venv/bin/activate         # ویندوز: .venv\Scripts\activate

pip install -e ".[dev]"
pre-commit install
```

### دروازه‌های کیفیت

```bash
ruff check .          # لینت
ruff format --check . # فرمت
mypy mtpbot           # بررسی نوع سختگیرانه
pytest -q             # تست‌ها
```

هر چهار مورد باید قبل از ادغام PR پاس شوند.

---

## 🧪 تست

```bash
pytest -q                    # همهٔ تست‌ها
pytest -q --cov=mtpbot       # با پوشش
pytest tests/test_mtproxy.py # یک ماژول
```

### نقشهٔ پوشش

| ماژول | آنچه تست می‌شود |
|---|---|
| `mtproxy.py` | پارس سکرت، اعتبارسنجی، انتخاب کلاس اتصال، مخفی‌سازی در `repr` |
| `handlers.py` | ثبت هندلر، تطبیق دستور، اجبار async، ترتیب توزیع |
| `types.py` | `Message.command`، `command_args`، محافظ‌های `reply`، `User.full_name` |
| `exceptions.py` | سلسله‌مراتب کامل استثناها |
| `bot.py` | اعتبارسنجی توکن، پروکسی دیکشنری/نمونه، پیش‌فرض‌های پیکربندی |

تمام تست‌های مرتبط با شبکه از mock استفاده می‌کنند. **هیچ اعتبارنامهٔ
واقعی هرگز در مخزن ذخیره نمی‌شود.**

---

## 🗺 نقشهٔ راه

| مرحله | وضعیت |
|---|---|
| v0.1 — MTProxy `dd` + `plain`، هندلرهای دستور و پیام، CLI | ✅ منتشر شده |
| v0.2 — پشتیبانی بومی از FakeTLS (`ee`) | 🚧 در حال انجام |
| v0.3 — کیبوردهای inline و callback query | 📋 برنامه‌ریزی‌شده |
| v0.4 — متدهای رسانه (`send_photo`، `send_document`، `send_video`) | 📋 برنامه‌ریزی‌شده |
| v0.5 — بک‌اندهای نشست پایدار (SQLite، Redis) | 📋 برنامه‌ریزی‌شده |
| v0.6 — سیستم پلاگین | 📋 برنامه‌ریزی‌شده |
| v1.0 — API پایدار + type stub کامل | 🎯 هدف |

برای رأی‌دادن به اولویت‌ها به
[Discussions](https://github.com/CodeNev/MTPBOT/discussions) مراجعه کنید.

---

## ❓ سؤالات متداول

<details>
<summary><b>آیا MTPBOT یک کلاینت HTTP در لباس مبدل است؟</b></summary>

**خیر.** MTPBOT یک دست‌دادن واقعی MTProto را با استفاده از Telethon از
طریق پروکسی انجام می‌دهد. سکرت پروکسی هرگز به `requests`، `aiohttp` یا
هر کتابخانهٔ HTTP دیگری داده نمی‌شود. بایت‌های روی سیم فریم‌های MTProto
هستند که با کلیدهای AES-256-CTR مشتق‌شده از سکرت رمزنگاری شده‌اند.
</details>

<details>
<summary><b>آیا می‌توانم از یک توکن معمولی Telegram Bot API استفاده کنم؟</b></summary>

بله. MTPBOT به‌عنوان ربات (`bot_token=...`) از طریق MTProto احراز هویت
می‌کند، بنابراین همان توکنی را استفاده می‌کنید که با
`python-telegram-bot` یا `aiogram` استفاده می‌کردید.
</details>

<details>
<summary><b>آیا به شمارهٔ تلفن واقعی نیاز دارم؟</b></summary>

خیر. احراز هویت ربات فرایند ورود تعاملی را دور می‌زند.
</details>

<details>
<summary><b>چرا پروکسی `ee` (FakeTLS) من متصل نمی‌شود؟</b></summary>

Telethon به‌طور بومی FakeTLS را پیاده‌سازی نمی‌کند. MTPBOT سکرت‌های
`ee` را پارس و اعتبارسنجی می‌کند، اما به randomized intermediate بازمی‌گردد.
اگر پروکسی شما فقط FakeTLS را می‌پذیرد، یک transport FakeTLS نصب کنید و
`MTPClient._resolve_connection_class` را override کنید. پشتیبانی بومی
در نقشهٔ راه است.
</details>

<details>
<summary><b>آیا می‌توانم از پروکسی SOCKS5 استفاده کنم؟</b></summary>

بله، در اصل — اما این مسئلهٔ *دیگری* است و خارج از دامنهٔ این پروژه.
MTPBOT به‌طور خاص دربارهٔ پروکسی‌های MTProto است.
</details>

---

## 🤝 مشارکت

از مشارکت استقبال می‌شود — از اصلاح غلط تایپی تا فیچر کامل.

1. مخزن را فورک کنید: https://github.com/CodeNev/MTPBOT/fork
2. یک شاخه بسازید: `git checkout -b feat/my-feature`.
3. برای تغییر خود تست بنویسید.
4. `ruff check .`، `mypy mtpbot` و `pytest -q` را اجرا کنید.
5. یک Pull Request با توضیح شفاف باز کنید.

لطفاً ابتدا
[CONTRIBUTING.md](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
و
[CODE_OF_CONDUCT.md](https://github.com/CodeNev/MTPBOT/blob/main/CODE_OF_CONDUCT.md)
را بخوانید.

**مسائل مناسب شروع** با برچسب
[`good first issue`](https://github.com/CodeNev/MTPBOT/labels/good%20first%20issue)
علامت‌گذاری شده‌اند.

---

## 📄 مجوز

MTPBOT تحت **مجوز MIT** منتشر شده است. برای متن کامل به
[LICENSE](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
مراجعه کنید.

```
MIT License — Copyright (c) 2026 MTPBOT Contributors
```

[![مجوز: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)

---

## 🙏 سپاسگزاری

MTPBOT روی شانه‌های یک جامعهٔ خارق‌العاده از نرم‌افزار آزاد ایستاده است.
از صمیم قلب از این‌ها سپاسگزاریم:

- **[Telegram](https://telegram.org)** — برای پروتکل MTProto،
  مشخصات دست‌دادن obfuscated2 و طراحی MTProto Proxy که زیرساخت ربات
  مقاوم را ممکن می‌کند.
- **[Telethon](https://github.com/LonamiWebs/Telethon)** — کتابخانهٔ
  کلاینت MTProto از [Lonami](https://github.com/LonamiWebs) که transport
  رمزنگاری‌شدهٔ واقعی را فراهم می‌کند و MTPBOT بر پایهٔ آن ساخته شده.
  بدون Telethon این پروژه وجود نداشت.
- **[Cryptg](https://github.com/cher-nov/cryptg)** — افزونهٔ C که
  عملیات AES-IGE تلگرام را سرعت می‌بخشد و ترافیک پرحجم را عملی می‌کند.
- **[python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)**
  و **[aiogram](https://github.com/aiogram/aiogram)** — برای الهام‌بخشی
  به API هندلر مبتنی بر دکوراتور که MTPBOT آن را می‌پذیرد.
- **[shields.io](https://shields.io)** — برای نشان‌های زیبا و شفافی
  که این README را می‌آرایند.
- **[Astral](https://astral.sh)** — برای **[Ruff](https://github.com/astral-sh/ruff)**
  و **[uv](https://github.com/astral-sh/uv)** که ابزار پایتون را سریع و
  دلپذیر می‌کنند.
- **[pytest](https://github.com/pytest-dev/pytest)** و
  **[pytest-asyncio](https://github.com/pytest-dev/pytest-asyncio)** — برای
  تجربه‌ای از تست که لذت است، نه بار.
- **[mypy](https://github.com/python/mypy)** — برای اینکه بررسی نوع را
  در پایتون درجه‌یک کند.
- **هر مشارکت‌کننده، تست‌کننده و گزارش‌دهندهٔ باگ** که به شکل‌گیری
  MTPBOT کمک کرده. issue‌ها، pull request‌ها و صبر شما همان چیزی است
  که این پروژه را واقعی می‌کند.

و در پایان — **سپاس از شما، خوانندهٔ عزیز**، که MTPBOT را برای پروژهٔ
خود در نظر گرفته‌اید. باشد که ربات‌هایتان همیشه آنلاین بمانند.

<div align="center">

---

**MTPBOT** · ساخته‌شده با ❤️ و احترامی سالم به رمزنگاری.

مخزن: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

[⬆ بازگشت به بالا](#mtpbot)

</div>
```

---

## تغییرات کلیدی نسبت به نسخهٔ قبلی فارسی

| مورد | قبل | بعد |
|---|---|---|
| لینک مخزن | `github.com/mtpbot/mtpbot` | **`github.com/CodeNev/MTPBOT`** |
| لایسنس | فقط متن | نشان MIT با لینک مستقیم به فایل LICENSE + ایموجی اختصاصی |
| ستاره‌ها / فورک‌ها / ایشوها | نبود | سه نشان جدید اضافه شد |
| نسخهٔ پایتون | `pypi/pyversions` داینامیک | **`python-3.14.7`** استاتیک |
| نسخهٔ وابستگی‌ها | نبود | Telethon 1.44.0، pytest 9.1.1، pytest-asyncio 1.4.0، Ruff 0.15.20، mypy 2.1.0، cryptg 0.6.0 |
| سوییچر زبان | نبود | ۵ زبان با ایموجی پرچم، لینک‌شده به هم |
| جدول پیش‌نیازها | نبود | اضافه شد |
| `git clone` | آدرس اشتباه | آدرس درست `CodeNev/MTPBOT` |
| لینک‌های `SECURITY.md` و `CONTRIBUTING.md` و `LICENSE` | نسبی | مطلق با آدرس کامل گیت‌هاب |
| فوتر | بدون آدرس مخزن | شامل لینک مستقیم به مخزن |

### اتصال متقابل زبان‌ها

هر پنج فایل README باید سوییچر یکسانی داشته باشند. برای اینکه فارسی به بقیه هم لینک شود، این بلاک در ابتدای فایل قرار دارد:

```markdown
🌍 **زبان‌ها:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇸🇦 العربية](README.ar.md) ·
[🇨🇳 中文](README.zh.md) ·
[🇷🇺 Русский](README.ru.md)


و در فایل‌های دیگر هم دقیقاً همان بلاک تکرار می‌شود — فقط زبان فعال (پرچم فعلی) در همه یکسان است. این باعث می‌شود تمام READMEها به هم لینک شوند و کاربر بتواند آزادانه بین زبان‌ها جابه‌جا شود.
