---
title: 'Customize Personality'
description: 'How to shape Chibi''s behavior using Skills and Memory.'
---

Chibi is designed to be a flexible companion. You can customize its personality and capabilities through **Skills** and **User Info**.

## Bot Name
You can give your bot a unique identity by setting the `BOT_NAME` in your `.env` file.

```dotenv
BOT_NAME=Jarvis
```
The bot will use this name when referring to itself.

## Skills (The "System Prompt" Replacement)

Chibi uses a dynamic system called **Skills** to define its behavior. Instead of a single massive "System Prompt", you can load specific skills that contain instructions for different roles or tasks.

*   **Location:** Skills are Markdown files located in the `skills/` directory (default: `./skills`).
*   **Usage:** You can ask the bot to "load the Python coding skill" or "act like a travel agent," and it will look for the corresponding skill file.

> [!NOTE]
> **Custom System Prompt:** The ability to manually override the core system prompt via `ASSISTANT_PROMPT` is currently disabled. It will return in a future update with a more robust implementation.

## User Info (Memory)

Chibi has a persistent memory of who you are. This allows it to personalize responses without you having to repeat yourself.

*   **How it works:** The bot maintains a `user_info` block in its context.
*   **Updating Memory:** You can simply tell the bot: *"Remember that I am a Python developer living in Krakow."*
*   **Automatic Updates:** The bot may also proactively save important details from your conversation (e.g., your preferred language or tools).

This memory persists across sessions, making Chibi feel more like a partner than a stateless tool.
