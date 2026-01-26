---
title: 'Docker Compose Installation'
description: 'The recommended way to deploy Chibi using Docker Compose.'
---

# Docker Compose Installation

This is the recommended method for deploying Chibi. It ensures your data is persistent and allows for easy configuration.

## Prerequisites

-   **Docker & Docker Compose:** [Install Docker](https://docs.docker.com/get-docker/).
-   **Telegram Bot Token:** Get one from [@BotFather](https://t.me/BotFather).
-   **API Keys:** At least one provider key (OpenAI, Gemini, Anthropic, etc.).

## Installation

### 1. Create a Project Directory

Create a folder for your bot and enter it:

```bash
mkdir my-chibi-bot
cd my-chibi-bot
```

### 2. Create Configuration File (.env)

Create a file named `.env` and add your credentials.

```bash
touch .env
```

**Example `.env` content:**

```dotenv
# .env

# --- Telegram Bot ---
TELEGRAM_BOT_TOKEN=your_telegram_bot_token_here

# --- AI Providers (Add the ones you have) ---
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=AIza...
ANTHROPIC_API_KEY=sk-ant-...

# --- Security ---
# Comma-separated list of allowed Telegram User IDs
USERS_WHITELIST=123456789
```

### 3. Create Docker Compose File

Create a file named `docker-compose.yml` with the following content. This tells Docker how to run Chibi.

```yaml
version: '3.8'

services:
  chibi:
    image: pysergio/chibi:latest
    container_name: chibi
    restart: unless-stopped
    env_file:
      - .env
    volumes:
      - chibi_data:/app/data

volumes:
  chibi_data:
```

### 4. Start the Bot

Run the following command to download the image and start the bot in the background:

```bash
docker-compose up -d
```

Check the logs to ensure everything is running smoothly:

```bash
docker-compose logs -f
```

## Updating

To update Chibi to the latest version:

```bash
# Download the latest image
docker-compose pull

# Restart the container with the new image
docker-compose up -d
```

## Troubleshooting

*   **Container keeps restarting:** Check logs with `docker-compose logs`. Usually indicates a missing API key or invalid token.
*   **Permissions errors:** Ensure the user running docker has permissions to create volumes.
