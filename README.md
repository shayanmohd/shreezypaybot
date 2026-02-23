# 🤖 Automatic Multi-Escrow Mediation Bot

A scalable Telegram bot that automatically mediates conversations
between paired groups --- built for escrow operations, transaction
monitoring, and structured communication control.

This bot enables **multiple independent escrow channels** to run
simultaneously using configurable group-pair mappings, controlled user
access, keyword filtering, and reply-thread synchronization.

------------------------------------------------------------------------

## 🚀 Features

### 🔁 Multi-Group Escrow Pairing

-   Supports **unlimited group pairs**
-   Each pair has:
    -   Source group (Escrow Side A)
    -   Destination group (Escrow Side B)
    -   Allowed sender(s)

------------------------------------------------------------------------

### 👤 Controlled Sender Access

-   Only specific user IDs can send messages from the source group
-   Optional bot message allowance (Telegram Bot API limitations apply)
-   Prevents unauthorized message forwarding

------------------------------------------------------------------------

### 🚫 Keyword Filtering

-   Blocks forwarding of messages containing restricted words
-   Case-insensitive filtering
-   Fully customizable keyword list

------------------------------------------------------------------------

### 🧵 Reply Thread Synchronization

-   When a message is replied to in one group,
-   The bot mirrors the reply correctly in the paired group
-   Maintains escrow conversation context between parties

------------------------------------------------------------------------

### 📎 Media Support

Handles: - Text messages - Photos - Videos - Documents

Messages are **resent cleanly** instead of forwarded to preserve
anonymity and formatting.

------------------------------------------------------------------------

## 🏗 Architecture Overview

Group A (Escrow Side 1) ↓ \[ BOT \] ↓ Group B (Escrow Side 2)

The bot: 1. Listens to both groups 2. Applies filtering & permission
logic 3. Resends approved messages to paired group 4. Maintains message
ID mapping for reply consistency

------------------------------------------------------------------------

## ⚙️ Configuration

Edit the `GROUP_PAIRS` list in the code:

``` python
GROUP_PAIRS = [
    {
        "source_group_id": -100XXXXXXXXXX,
        "dest_group_id": -100YYYYYYYYYY,
        "allowed_user_ids": [123456789]
    },
]
```

### Variables

-   `source_group_id` → First escrow group\
-   `dest_group_id` → Paired escrow group\
-   `allowed_user_ids` → Users allowed to initiate messages

------------------------------------------------------------------------

## 🔐 Environment Variables

Store the bot token securely as an environment variable:

    TELEGRAM_TOKEN=your_bot_token_here

The bot reads it using:

``` python
BOT_TOKEN = os.getenv("TELEGRAM_TOKEN")
```

------------------------------------------------------------------------

## 🛠 Installation

### 1️⃣ Install dependencies

``` bash
pip install -r requirements.txt
```

### 2️⃣ Run locally

``` bash
python your_bot_file.py
```

------------------------------------------------------------------------

## 🌐 Deployment

Recommended platforms: - Render (Background Worker recommended) -
Railway - VPS (AWS, DigitalOcean, etc.)

Push updates using:

``` bash
git add .
git commit -m "Update"
git push
```

Deployment auto-triggers after push.

------------------------------------------------------------------------

## 🧠 Use Cases

-   Escrow transaction mediation\
-   Crypto trade coordination\
-   Marketplace dispute handling\
-   Broker-client communication\
-   Controlled deal-room messaging

------------------------------------------------------------------------

## ⚠️ Notes

-   Message ID mapping is stored in memory.
-   Restarting the bot resets reply history mapping.
-   For production-scale escrow systems, persistent storage
    (Redis/SQLite) is recommended.

------------------------------------------------------------------------

## 📜 License

Private/Internal Use\
Modify as needed.

------------------------------------------------------------------------

## 💎 Why This Bot?

✔ Supports unlimited escrow channels\
✔ Prevents unauthorized communication\
✔ Preserves reply context\
✔ Lightweight & scalable\
✔ Built using python-telegram-bot
