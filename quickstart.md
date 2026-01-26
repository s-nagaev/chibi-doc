---
title: Quickstart
description: Get Chibi up and running in less than 5 minutes.
---

## Prerequisites

*   **Docker** installed on your machine.
*   **Telegram Bot Token** from [@BotFather](https://t.me/BotFather).
*   **OpenAI API Key** (or another provider).

## One-Liner (Linux/macOS)

Run this command in your terminal, replacing the placeholders with your actual keys:

```bash
docker run -d --name chibi \
  -e TELEGRAM_BOT_TOKEN="your_bot_token" \
  -e OPENAI_API_KEY="sk-..." \
  -v chibi_data:/app/data \
  pysergio/chibi:latest
```

## Verify Installation

1.  Open Telegram and find your bot.
2.  Send `/start`.
3.  If the bot replies, you're live!

## Next Steps

*   **Recommended:** Switch to [Docker Compose](/installation/docker-compose) for a more permanent setup.
*   **Configure:** Add more [AI Providers](/configuration/ai-providers).
*   **Secure:** Set up [Whitelists](/guides/secure-your-bot) to protect your bot.
