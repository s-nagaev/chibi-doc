---
title: 'Deployment Modes'
description: 'Understanding Private vs. Public modes in Chibi.'
---
Chibi can operate in two distinct modes depending on your use case: **Private** (default) and **Public**.

## Private Mode (Default)

This is the standard mode for personal use or small teams.

*   **API Keys:** The bot uses the "Master API Keys" configured in the `.env` file (e.g., your personal OpenAI key).
*   **Access:** Restricted via `USERS_WHITELIST`. Only authorized users can interact with the bot.
*   **Cost:** You (the admin) pay for all API usage.
*   **Best for:** Personal assistants, home automation, small workgroups.

## Public Mode

This mode is designed for bots that serve many unrelated users.

*   **Activation:** Set `PUBLIC_MODE=True` in your `.env` file.
*   **API Keys:** The bot **doesn't ignore** the API Keys in `.env` file! You still can provide them for your users! 
*   **Access:** Open to anyone (unless restricted by other means).
*   **Cost:** Each user must provide their own API key using the `/key` command. The bot uses the user's key for their requests.
*   **Best for:** Public demo bots, community tools where you don't want to pay for everyone's tokens.

> [!NOTE]
> Even in Public Mode, some system-level functions (like initial moderation or specific tools) might still rely on the admin's keys if configured that way.
