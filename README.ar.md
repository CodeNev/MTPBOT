
<!--
  MTPBOT — إطار عمل بوتات تلگرام عبر MTProto Proxy
  README.ar.md (العربية)
  المستودع: https://github.com/CodeNev/MTPBOT
-->

<div align="center" dir="rtl">

# MTPBOT

**إطار عمل لبناء بوتات تلگرام عبر MTProto Proxy — غير متزامن، معياري، وجاهز للإنتاج.**

<!-- ===================== مبدل اللغات ===================== -->
🌍 **اللغات:**
[🇬🇧 English](README.md) ·
[🇮🇷 فارسی](README.fa.md) ·
[🇨🇳 中文](README.zh.md) ·
[🇷🇺 Русский](README.ru.md)

---

<!-- ===================== الشارات ===================== -->
[![إصدار PyPI](https://img.shields.io/pypi/v/mtpbot.svg?style=for-the-badge&logo=pypi&logoColor=white&color=3775A9)](https://pypi.org/project/mtpbot/)
[![بايثون 3.14.7](https://img.shields.io/badge/python-3.14.7-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads/release/python-3147/)
[![الرخصة: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
[![التنزيلات](https://img.shields.io/pypi/dm/mtpbot.svg?style=for-the-badge&logo=pypistats&logoColor=white&color=0A66C2)](https://pypistats.org/packages/mtpbot)
[![نجوم GitHub](https://img.shields.io/github/stars/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white&color=yellow)](https://github.com/CodeNev/MTPBOT/stargazers)
[![التفريعات](https://img.shields.io/github/forks/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/network/members)
[![المشاكل](https://img.shields.io/github/issues/CodeNev/MTPBOT.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/CodeNev/MTPBOT/issues)

<!-- ===================== إصدارات الاعتماديات ===================== -->
[![Telethon](https://img.shields.io/badge/Telethon-1.44.0-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/Telethon/1.44.0/)
[![pytest](https://img.shields.io/badge/pytest-9.1.1-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest/9.1.1/)
[![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-1.4.0-0A9EDC.svg?style=for-the-badge&logo=pytest&logoColor=white)](https://pypi.org/project/pytest-asyncio/1.4.0/)
[![Ruff](https://img.shields.io/badge/Ruff-0.15.20-000000.svg?style=for-the-badge&logo=ruff&logoColor=white)](https://pypi.org/project/ruff/0.15.20/)
[![mypy](https://img.shields.io/badge/mypy-2.1.0-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://pypi.org/project/mypy/2.1.0/)
[![cryptg](https://img.shields.io/badge/cryptg-0.6.0-2E8B57.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://pypi.org/project/cryptg/0.6.0/)

<!-- ===================== الحالة ===================== -->
[![Async](https://img.shields.io/badge/async-await-2E8B57.svg?style=for-the-badge&logo=python&logoColor=white)](https://docs.python.org/3/library/asyncio.html)
[![MTProto](https://img.shields.io/badge/protocol-MTProto-2CA5E0.svg?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/mtproto)
[![Type Checked](https://img.shields.io/badge/type--checked-mypy-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://mypy-lang.org/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
[![صُنع بـ ❤️](https://img.shields.io/badge/made%20with-%E2%9D%A4%EF%B8%8F-red.svg?style=for-the-badge)](#-شكر-وتقدير)

**واجهة نظيفة وغير متزامنة على نمط Bot API لبوتات تلگرام التي تحتاج إلى
الوصول إلى تلگرام عبر MTProto Proxy — وليس نفق HTTP.**

[التوثيق](docs/) · [الأمثلة](examples/) · [سجل التغييرات](CHANGELOG.md) · [الإبلاغ عن خطأ](https://github.com/CodeNev/MTPBOT/issues)

</div>

---

## جدول المحتويات

- [لماذا MTPBOT؟](#-لماذا-mtpbot)
- [الميزات](#-الميزات)
- [البنية المعمارية](#-البنية-المعمارية)
- [التثبيت](#-التثبيت)
- [البدء السريع](#-البدء-السريع)
- [إعداد MTProto Proxy](#-إعداد-mtproto-proxy)
- [متغيرات البيئة](#-متغيرات-البيئة)
- [معالجات الأوامر](#-معالجات-الأوامر)
- [معالجات الرسائل](#-معالجات-الرسائل)
- [مرجع واجهة البرمجة](#-مرجع-واجهة-البرمجة)
- [واجهة سطر الأوامر](#-واجهة-سطر-الأوامر)
- [معالجة الأخطاء](#-معالجة-الأخطاء)
- [الأمان](#-الأمان)
- [التطوير](#-التطوير)
- [الاختبار](#-الاختبار)
- [خارطة الطريق](#-خارطة-الطريق)
- [الأسئلة الشائعة](#-الأسئلة-الشائعة)
- [المساهمة](#-المساهمة)
- [الرخصة](#-الرخصة)
- [شكر وتقدير](#-شكر-وتقدير)

---

## 🚀 لماذا MTPBOT؟

في العديد من الشبكات، يتم حجب نقطة النهاية الرسمية لـ Bot API الخاصة
بتلگرام (`api.telegram.org`) أو تقييدها أو منعها تماماً. تستخدم الحلول
التقليدية وكلاء HTTP أو SOCKS، وهؤلاء صاخبون وسهل التعرف عليهم وغالباً
ما يتم إيقافهم.

**وكلاء MTProto يتحدثون بروتوكول تلگرام نفسه.** إنهم سريعون، مرنون،
صعب الكشف عنهم، ومنتشرون على نطاق واسع. المشكلة: استخدامهم مباشرة يتطلب
تنفيذ MTProto، ومصافحة obfuscated2، واشتقاق مفاتيح AES-256-CTR، وطبقة
RPC كاملة غير متزامنة.

**MTPBOT يحل هذا بالضبط.** يوفر لك سطحاً نظيفاً ومألوفاً على نمط Bot API
فوق عميل MTProto حقيقي، بحيث يمكنك كتابة:

```python
@bot.command("/start")
async def start(message):
    await message.reply("MTPBOT يعمل!")
```

…بينما تكون حركة المرور في الأسفل جلسة MTProto حقيقية ومشفرة يتم توجيهها
عبر MTProto Proxy.

> ⚠️ **مهم:** MTPBOT **ليس** غلافاً على HTTP. إنه **لا** يمرر طلبات
> `requests` أو `aiohttp` عبر الوكيل. بل ينفذ بروتوكول MTProto الحقيقي
> باستخدام Telethon تحت الغطاء.

---

## ✨ الميزات

| الميزة | الحالة |
|---|---|
| اتصال MTProto حقيقي عبر MTProto Proxy | ✅ |
| مصافحة obfuscated2 (سر `dd`) | ✅ |
| تحليل سر FakeTLS (سر `ee`) | ✅ (تحليل؛ تراجع أثناء التشغيل) |
| سر legacy abridged (`plain`) | ✅ |
| واجهة غير متزامنة أولاً (`async` / `await`) | ✅ |
| معالجات قائمة على المزخرفات (`@bot.command`، `@bot.on_message`) | ✅ |
| `message.reply(...)` و `bot.send_message(...)` | ✅ |
| `get_chat`، `get_user`، `get_me` | ✅ |
| إيقاف لطيف وإعادة اتصال تلقائية | ✅ |
| المهلات وإعادة المحاولات | ✅ |
| تسلسل هرمي مخصص للاستثناءات | ✅ |
| إخفاء الرمز والسر في السجلات | ✅ |
| متوافق مع متغيرات البيئة | ✅ |
| واجهة سطر الأوامر (`mtpbot run`، `mtpbot check`، `mtpbot version`) | ✅ |
| بايثون 3.14.7 أو أحدث | ✅ |
| مكتوب بالأنواع بالكامل (`mypy --strict` نظيف) | ✅ |
| بدون اعتماديات غير ضرورية | ✅ |

---

## 🧭 البنية المعمارية

```
┌─────────────────────────┐
│  بوتك (بايثون غير متزامن)│
└────────────┬────────────┘
             │  await bot.send_message(...)
             ▼
┌─────────────────────────┐
│        MTPBOT           │  ← سطح على نمط Bot API
│  (المعالجات، الأنواع، CLI)│
└────────────┬────────────┘
             │  MTProto RPC
             ▼
┌─────────────────────────┐
│   عميل MTProto          │  ← Telethon (obfuscated2، AES-256-CTR)
└────────────┬────────────┘
             │  TCP مشفر
             ▼
┌─────────────────────────┐
│    MTProto Proxy        │  ← dd / ee / plain
└────────────┬────────────┘
             │
             ▼
┌─────────────────────────┐
│    مركز بيانات تلگرام   │
└─────────────────────────┘
```

### هيكل الحزمة

```
mtpbot/
├── __init__.py        # سطح واجهة البرمجة العامة
├── bot.py             # فئة Bot، المزخرفات، دورة الحياة
├── client.py          # غلاف Telethon (مدرك لـ MTProxy)
├── mtproto.py         # إعدادات البروتوكول، نقاط مراكز البيانات
├── mtproxy.py         # MTProxy، parse_secret، proxy_from_dict
├── updates.py         # تحويل الأحداث إلى Message، الموزع
├── methods.py         # send_message، get_chat، get_user، get_me
├── types.py           # User، Chat، Message، Update
├── handlers.py        # CommandHandler، MessageHandler، السجل
├── exceptions.py      # التسلسل الهرمي الكامل للاستثناءات
├── utils.py           # السجلات، التنقية، مساعدات env
├── cli.py             # نقطة دخول سطر الأوامر `mtpbot`
└── __main__.py        # `python -m mtpbot`
```

---

## 📦 التثبيت

### من PyPI

```bash
pip install mtpbot
```

### من المصدر

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT
pip install .
```

### وضع التطوير

```bash
pip install -e ".[dev]"
```

### تحسين الأداء الاختياري

`cryptg` يسرّع عمليات AES-IGE الخاصة بتلگرام بشكل كبير:

```bash
pip install "mtpbot[fast]"
```

### المتطلبات

| المكوّن | الحد الأدنى | الأحدث (حتى هذا الإصدار) |
|---|---|---|
| بايثون | 3.14.7 | 3.14.7 |
| Telethon | 1.44.0 | 1.44.0 |
| pytest | 9.1.1 | 9.1.1 |
| pytest-asyncio | 1.4.0 | 1.4.0 |
| Ruff | 0.15.20 | 0.15.20 |
| mypy | 2.1.0 | 2.1.0 |
| cryptg | 0.6.0 | 0.6.0 |

---

## ⚡ البدء السريع

أنشئ ملفاً باسم `bot.py`. **يجب أن يكون أول سطر غير فارغ هو سطر العلامة**
`# mtpbot run` — هكذا تتعرف واجهة سطر الأوامر على ملف MTPBOT صالح.

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
    await message.reply("MTPBOT يعمل عبر MTProto Proxy!")

bot.run()
```

تشغيله:

```bash
mtpbot run bot.py
```

التحقق منه دون تشغيل:

```bash
mtpbot check bot.py
```

---

## 🔐 إعداد MTProto Proxy

يمكنك تمرير الوكيل إما كقاموس أو ككائن `MTProxy`.

### شكل القاموس

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

### كائن `MTProxy`

```python
from mtpbot import Bot, MTProxy

proxy = MTProxy(
    server="1.2.3.4",
    port=443,
    secret="dd0123456789abcdef0123456789abcdef",
)

bot = Bot(token="BOT_TOKEN", proxy=proxy)
```

### صيغ السر

| البادئة | الصيغة | المصافحة | اتصال Telethon |
|--------|--------|-----------|---------------------|
| `dd` | `dd` + 32 حرف hex | Randomized intermediate (obfuscated2) | `ConnectionTcpMTProxyRandomizedIntermediate` |
| `ee` | `ee` + 32 حرف hex + نطاق | FakeTLS | *التراجع إلى randomized intermediate* |
| *(بدون بادئة)* | 32 حرف hex | Legacy abridged | `ConnectionTcpMTProxyAbridged` |

> **ملاحظة حول FakeTLS:** لا يدعم Telethon بروتوكول FakeTLS بشكل أصلي.
> يقوم MTPBOT بتحليل أسرار `ee` والتحقق منها وتسجيل تحذير قبل التراجع
> إلى randomized intermediate. الدعم الأصلي لـ FakeTLS مدرج في
> [خارطة الطريق](#-خارطة-الطريق).

### واجهة `MTProxy`

```python
proxy.raw_secret        # bytes  (16 بايت، بدون بادئة)
proxy.secret_mode       # "dd" | "ee" | "plain"
proxy.connection_type   # اسم فئة اتصال Telethon
proxy.as_telethon_proxy()  # (server, port, secret)
proxy.to_dict()         # {'server': ..., 'port': ..., 'secret': ...}
```

---

## 🌱 متغيرات البيئة

لا تُضمّن بيانات الاعتماد مباشرة في الكود أبداً. MTPBOT مصمم ليكون متوافقاً
مع متغيرات البيئة.

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

أو باستخدام المساعدات المدمجة:

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

## 🎯 معالجات الأوامر

سجّل معالجات الأوامر باستخدام مزخرف `@bot.command(...)`.

```python
@bot.command("/start")
async def start(message):
    await message.reply("أهلاً وسهلاً!")

@bot.command("/help")
async def help_cmd(message):
    await message.reply(
        "الأوامر المتاحة:\n"
        "/start — ترحيب\n"
        "/help  — هذه الرسالة\n"
        "/whoami — عرض معرّفك"
    )

@bot.command("/whoami")
async def whoami(message):
    user = message.from_user
    await message.reply(f"أنت {user.full_name} (id={user.id})")
```

يستقبل المعالج كائن `Message` يحتوي على:

- `message.text` — النص الكامل
- `message.command` — مثلاً `"/start"`
- `message.command_args` — قائمة الوسائط
- `message.from_user` — كائن `User`
- `message.chat_id`، `message.message_id`
- `await message.reply(...)`

تعمل الأوامر أيضاً مع اللاحقة `@botname` (`/start@mybot`).

---

## 💬 معالجات الرسائل

يُفعَّل `@bot.on_message()` لأي رسالة واردة **لا تتطابق** مع معالج أمر.

```python
@bot.on_message()
async def echo(message):
    await message.reply(f"قلت: {message.text}")
```

أضف شرطاً للتصفية:

```python
@bot.on_message(predicate=lambda m: m.text and "مرحبا" in m.text)
async def greet(message):
    await message.reply("مرحباً!")
```

> **قاعدة التوزيع:** إذا تطابق أمر، يتم تخطي معالجات `on_message` لتلك
> الرسالة. هذا يمنع حلقات الصدى والمعالجة المزدوجة.

---

## 📚 مرجع واجهة البرمجة

### `Bot`

| الطريقة / السمة | الوصف |
|---|---|
| `Bot(token, proxy=None, *, api_id=None, api_hash=None, timeout=30.0, connection_retries=5, retry_delay=5.0, log_level=20, session=None)` | إنشاء بوت. |
| `bot.command(cmd)` | مزخرف لتسجيل معالج أمر. |
| `bot.on_message(predicate=None)` | مزخرف لتسجيل معالج رسالة. |
| `await bot.start()` | الاتصال وتسجيل المعالجات. |
| `await bot.stop()` | قطع الاتصال بلطف. |
| `await bot.send_message(chat_id, text, reply_to=None, parse_mode=None, silent=False)` | إرسال رسالة. |
| `await bot.get_chat(chat_id)` | إرجاع `Chat`. |
| `await bot.get_user(user_id)` | إرجاع `User`. |
| `await bot.get_me()` | إرجاع `User` الخاص بالبوت. |
| `bot.run()` | نقطة الدخول الحاجبة (مدركة لـ Ctrl-C). |
| `async with bot:` | مدير السياق غير المتزامن. |

### `Message`

| السمة / الطريقة | الوصف |
|---|---|
| `message_id` | معرّف رسالة تلگرام. |
| `chat_id` | معرّف الدردشة. |
| `text` | نص الرسالة. |
| `date` | `datetime`. |
| `from_user` | `User` أو `None`. |
| `chat` | `Chat` أو `None`. |
| `reply_to_message_id` | معرّف الرسالة المُجاب عليها، إن وُجد. |
| `command` | اسم الأمر، مثلاً `"/start"`. |
| `command_args` | قائمة الوسائط. |
| `await message.reply(text, **kwargs)` | الرد في نفس الدردشة. |
| `await message.reply_text(text, **kwargs)` | اسم بديل لـ `reply`. |

### `User` / `Chat`

أغلفة قياسية لكيانات تلگرام. `User.full_name` و `Chat.display_name`
خصائص تسهيلية.

### `MTProxy`

راجع [إعداد MTProto Proxy](#-إعداد-mtproto-proxy).

### الاستثناءات

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

## 🖥 واجهة سطر الأوامر

يوفر MTPBOT واجهة سطر أوامر من الدرجة الأولى.

```bash
mtpbot run bot.py            # تشغيل ملف بوت
mtpbot check bot.py          # التحقق من العلامة والبنية والنحو
mtpbot version               # طباعة الإصدار
python -m mtpbot run bot.py  # الصيغة المعيارية المكافئة
```

### `mtpbot check`

يتحقق من أن الملف المستهدف:

1. يحتوي على سطر العلامة `# mtpbot run` كأول سطر غير فارغ،
2. يُحلَّل كـ Python صالح،
3. يحتوي على إنشاء `Bot(...)`،
4. يستدعي `bot.run()`.

كود الخروج `0` عند النجاح، `1` عند التحذيرات، `2` عند الأخطاء القاتلة.

---

## 🛡 معالجة الأخطاء

جميع الأخطاء ترث من `MTPBOTError`، حتى تتمكن من الالتقاط بشكل عام أو محدد.

```python
from mtpbot import Bot
from mtpbot.exceptions import InvalidSecretError, ConnectionError

try:
    bot = Bot(
        token="...",
        proxy={"server": "...", "port": 443, "secret": "bad"},
    )
except InvalidSecretError as exc:
    print("سر الوكيل غير صالح:", exc)

try:
    await bot.send_message(chat_id, "hi")
except ConnectionError as exc:
    print("فُقد اتصال MTProto:", exc)
```

**لا تظهر أبداً في رسائل الاستثناء:**

- رمز البوت،
- سر الوكيل،
- بيانات MTProto الخام،
- أي بيانات اعتماد من أي نوع.

تحتوي رسائل الاستثناء على اسم فئة الخطأ الأساسي فقط.

---

## 🔒 الأمان

يعامل MTPBOT بيانات الاعتماد كأسرار من الدرجة الأولى.

- 🚫 **لا يتم تسجيل رمز البوت بالكامل أبداً.** يستبدله `sanitize_token()`
  بـ `<redacted-token>` قبل أي عبارة تسجيل.
- 🚫 **لا يتم تسجيل سر الوكيل أبداً.** يحذفه `MTProxy.__repr__` ويستبدله
  `sanitize_secret()` في سطور السجل.
- 🚫 **لا توجد بيانات اعتماد مضمّنة في الكود** في أي مكان في شجرة
  المصدر.
- ✅ **دعم متغيرات البيئة** مدمج.
- ✅ **رسائل الاستثناء** تحتوي على اسم فئة الخطأ فقط.
- ✅ **جلسات في الذاكرة افتراضياً** — لا شيء يُحفظ على القرص.

إذا وجدت مشكلة أمنية، **يُرجى عدم فتح قضية عامة.** راجع
[SECURITY.md](https://github.com/CodeNev/MTPBOT/blob/main/SECURITY.md).

---

## 🛠 التطوير

```bash
git clone https://github.com/CodeNev/MTPBOT.git
cd MTPBOT

python -m venv .venv
source .venv/bin/activate         # ويندوز: .venv\Scripts\activate

pip install -e ".[dev]"
pre-commit install
```

### بوابات الجودة

```bash
ruff check .          # التفتيش
ruff format --check . # التنسيق
mypy mtpbot           # فحص الأنواع الصارم
pytest -q             # الاختبارات
```

يجب أن تنجح الأربعة قبل دمج أي PR.

---

## 🧪 الاختبار

```bash
pytest -q                    # كل الاختبارات
pytest -q --cov=mtpbot       # مع التغطية
pytest tests/test_mtproxy.py # وحدة واحدة
```

### خريطة التغطية

| الوحدة | ما يتم اختباره |
|---|---|
| `mtproxy.py` | تحليل السر، التحقق، اختيار فئة الاتصال، إخفاء `repr` |
| `handlers.py` | تسجيل المعالج، مطابقة الأمر، فرض async، ترتيب التوزيع |
| `types.py` | `Message.command`، `command_args`، حراس `reply`، `User.full_name` |
| `exceptions.py` | التسلسل الهرمي الكامل للاستثناءات |
| `bot.py` | التحقق من الرمز، وكيل قاموس/كائن، إعدادات افتراضية |

جميع الاختبارات التي تلمس الشبكة تستخدم mock. **لا يتم تخزين أي بيانات
اعتماد حقيقية في المستودع** — أبداً.

---

## 🗺 خارطة الطريق

| المرحلة | الحالة |
|---|---|
| v0.1 — MTProxy `dd` + `plain`، معالجات الأوامر والرسائل، CLI | ✅ صدر |
| v0.2 — دعم FakeTLS (`ee`) الأصلي | 🚧 قيد التنفيذ |
| v0.3 — لوحات المفاتيح المدمجة واستعلامات الاستدعاء | 📋 مخطط |
| v0.4 — طرق الوسائط (`send_photo`، `send_document`، `send_video`) | 📋 مخطط |
| v0.5 — خلفيات الجلسة الدائمة (SQLite، Redis) | 📋 مخطط |
| v0.6 — نظام الإضافات | 📋 مخطط |
| v1.0 — واجهة مستقرة + stubs أنواع كاملة | 🎯 الهدف |

صوّت على الأولويات في
[المناقشات](https://github.com/CodeNev/MTPBOT/discussions).

---

## ❓ الأسئلة الشائعة

<details>
<summary><b>هل MTPBOT عميل HTTP متنكر؟</b></summary>

**لا.** يقوم MTPBOT بمصافحة MTProto حقيقية عبر الوكيل باستخدام Telethon.
لا يُسلَّم سر الوكيل أبداً إلى `requests` أو `aiohttp` أو أي مكتبة HTTP.
البايتات على السلك هي إطارات MTProto مشفرة بمفاتيح AES-256-CTR المشتقة
من السر.
</details>

<details>
<summary><b>هل يمكنني استخدامه مع رمز Telegram Bot API عادي؟</b></summary>

نعم. يصادق MTPBOT كبوت (`bot_token=...`) عبر MTProto، لذلك تستخدم نفس
الرمز الذي كنت ستستخدمه مع `python-telegram-bot` أو `aiogram`.
</details>

<details>
<summary><b>هل أحتاج إلى رقم هاتف حقيقي؟</b></summary>

لا. تفويض البوت يتجاوز تدفق تسجيل الدخول التفاعلي.
</details>

<details>
<summary><b>لماذا لا يتصل وكيل `ee` (FakeTLS) الخاص بي؟</b></summary>

Telethon لا ينفذ FakeTLS أصلياً. يقوم MTPBOT بتحليل أسرار `ee` والتحقق
منها لكنه يتراجع إلى randomized intermediate. إذا كان وكيلك يقبل فقط
FakeTLS، فقم بتثبيت transport FakeTLS وتجاوز
`MTPClient._resolve_connection_class`. الدعم الأصلي في خارطة الطريق.
</details>

<details>
<summary><b>هل يمكنني استخدام وكيل SOCKS5 بدلاً من ذلك؟</b></summary>

نعم، من حيث المبدأ — لكن تلك *مشكلة مختلفة* وخارج النطاق. MTPBOT يتعلق
تحديداً بوكلاء MTProto.
</details>

---

## 🤝 المساهمة

المساهمات مرحّب بها — من تصحيح الأخطاء المطبعية إلى الميزات الكاملة.

1. فرّع المستودع: https://github.com/CodeNev/MTPBOT/fork
2. أنشئ فرعاً: `git checkout -b feat/my-feature`.
3. أضف اختبارات لتغييرك.
4. شغّل `ruff check .`، `mypy mtpbot`، و `pytest -q`.
5. افتح Pull Request بوصف واضح.

يُرجى قراءة
[CONTRIBUTING.md](https://github.com/CodeNev/MTPBOT/blob/main/CONTRIBUTING.md)
و
[CODE_OF_CONDUCT.md](https://github.com/CodeNev/MTPBOT/blob/main/CODE_OF_CONDUCT.md)
أولاً.

**القضايا المناسبة للبدء** موسومة بـ
[`good first issue`](https://github.com/CodeNev/MTPBOT/labels/good%20first%20issue).

---

## 📄 الرخصة

يُصدر MTPBOT تحت **رخصة MIT**. راجع
[LICENSE](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)
للنص الكامل.

```
MIT License — Copyright (c) 2026 MTPBOT Contributors
```

[![الرخصة: MIT](https://img.shields.io/badge/License-MIT-97CA00.svg?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](https://github.com/CodeNev/MTPBOT/blob/main/LICENSE)

---

## 🙏 شكر وتقدير

يقف MTPBOT على أكتاف مجتمع استثنائي من البرمجيات مفتوحة المصدر.
خالص الشكر لـ:

- **[Telegram](https://telegram.org)** — على بروتوكول MTProto، ومواصفات
  مصافحة obfuscated2، وتصميم MTProto Proxy الذي يجعل البنية التحتية
  للبوتات المرنة ممكنة.
- **[Telethon](https://github.com/LonamiWebs/Telethon)** — مكتبة عميل
  MTProto من [Lonami](https://github.com/LonamiWebs) التي توفر النقل
  المشفر الحقيقي الذي بُني MTPBOT عليه. بدون Telethon، لما وُجد هذا
  المشروع.
- **[Cryptg](https://github.com/cher-nov/cryptg)** — امتداد C الذي يسرّع
  عمليات AES-IGE الخاصة بتلگرام ويجعل حركة المرور عالية الإنتاجية
  عملية.
- **[python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)**
  و **[aiogram](https://github.com/aiogram/aiogram)** — لإلهام واجهة
  المعالج القائمة على المزخرفات التي يتبناها MTPBOT.
- **[shields.io](https://shields.io)** — على الشارات الجميلة والشفافة
  التي تزيّن هذا README.
- **[Astral](https://astral.sh)** — على **[Ruff](https://github.com/astral-sh/ruff)**
  و **[uv](https://github.com/astral-sh/uv)**، اللذين يجعلان أدوات بايثون
  سريعة وممتعة.
- **[pytest](https://github.com/pytest-dev/pytest)** و
  **[pytest-asyncio](https://github.com/pytest-dev/pytest-asyncio)** — على
  تجربة اختبار ممتعة، وليست عبئاً.
- **[mypy](https://github.com/python/mypy)** — على جعل فحص الأنواع من
  الدرجة الأولى في بايثون.
- **كل مساهم ومختبر ومُبلِّغ عن خطأ** ساعد في تشكيل MTPBOT. قضاياك
  وطلبات السحب وصبرك هي ما يجعل هذا المشروع حقيقياً.

وأخيراً — **شكراً لك، عزيزي القارئ**، على التفكير في MTPBOT لمشروعك.
نسأل الله أن تبقى بوتاتك متصلة دائماً.

<div align="center">

---

**MTPBOT** · صُنع بـ ❤️ واحترام صحي للتشفير.

المستودع: **[github.com/CodeNev/MTPBOT](https://github.com/CodeNev/MTPBOT)**

[⬆ العودة إلى الأعلى](#mtpbot)

</div>
```

اگر خواستید، نسخه‌های **چینی** و **روسی** را هم با همین ساختار و سوییچر یکسان در پیام بعدی برایتان می‌نویسم.
