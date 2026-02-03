---
title: 'Core Settings'
description: 'Essential configuration for Chibi: Telegram connection, access control, and agent behavior.'
---

## Telegram Connection

These variables define how your bot connects to the Telegram platform. A `TELEGRAM_BOT_TOKEN` is always required.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `TELEGRAM_BOT_TOKEN` | **Required.** Your Telegram Bot API token from `@BotFather`. This is the key to your bot's identity. | - |
| `BOT_NAME` | The name the bot uses for itself in prompts and messages. Helps in personalizing the bot's identity. | `Chibi` |
| `TELEGRAM_BASE_URL` | For advanced use cases, like running a local Telegram Bot API server. This directs API traffic to your server instead of Telegram's. | `https://api.telegram.org/bot` |
| `TELEGRAM_BASE_FILE_URL` | Similar to the above, but for file downloads. Change this only if you have a local Bot API server. | `https://api.telegram.org/file/bot` |
| `PROXY` | If your server is behind a proxy, specify it here to ensure the bot can communicate with the Telegram API. | `None` |

> [!WARNING]
> **Security Advisory**
> Your `TELEGRAM_BOT_TOKEN` is highly sensitive. Treat it like a password. Do not expose it in public repositories or client-side code.

## Access Control

Control who can interact with your bot. By default, the bot is private.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `USERS_WHITELIST` | A comma-separated list of Telegram usernames (e.g., `@user1,user2`) or numeric IDs. Only these users can interact with the bot. | `None` (disabled) |
| `GROUPS_WHITELIST` | A comma-separated list of Telegram group chat IDs. The bot will only operate in these groups. | `None` (disabled) |
| `ANSWER_DIRECT_MESSAGES_ONLY` | If `True`, the bot will not respond to messages in groups it's added to unless the group is whitelisted. | `True` |
| `MESSAGE_FOR_DISALLOWED_USERS` | The specific message sent to a user who tries to interact with the bot but is not on the whitelist. | Standard rejection message |
| `ALLOW_BOTS` | If `True`, the bot will respond to messages sent by other bots. | `False` |

## General Behavior

These settings control the bot's core functionality and user interface elements.

| Variable              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                    | Default    |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------|
| `PUBLIC_MODE`         | If `True`, the bot won't use its master API keys. Instead, each user must provide their own API key via the `/key` command. This is ideal for public-facing bots to shift API costs to the user.                                                                                                                                                                                                                                               | `False`    |
| `LOG_PROMPT_DATA`     | Set to `True` to log the full prompt data sent to the AI provider. Useful for debugging but can be verbose.                                                                                                                                                                                                                                                                                                                                    | `False`    |
| `HIDE_MODELS`         | If `True`, hides the model selection buttons from the user interface. Simplifies the UI if you want users to stick to the default model.                                                                                                                                                                                                                                                                                                       | `False`    |
| `HIDE_IMAGINE`        | If `True`, hides the `/image` and other image generation commands.                                                                                                                                                                                                                                                                                                                                                                             | `False`    |
| `SHOW_LLM_THOUGHTS`   | When enabled, the bot will show its internal reasoning or "thoughts" before providing a final answer. Great for transparency and debugging.                                                                                                                                                                                                                                                                                                    | `False`    |
| `WORKING_DIR`         | The default directory the bot's filesystem tools will operate in.                                                                                                                                                                                                                                                                                                                                                                              | `~/chibi`  |
| `HOME_DIR`            | The directory considered as the "home" for the AI agent.                                                                                                                                                                                                                                                                                                                                                                                       | `~/chibi`  |
| `SKILLS_DIR`          | Absolute path to the directory containing LLM skills/prompts.                                                                                                                                                                                                                                                                                                                                                                                  | `./skills` |
| `MODERATION_PROVIDER` | Optional. Specifies the AI provider to use for command moderation. If a moderation provider is not explicitly set by the user, it will be chosen automatically. The system attempts to select a moderation provider that DOES NOT coincide with the default primary provider. If the default primary provider is taken from the beginning of the list of available providers, the moderation provider will be taken from the end of that list. | `None`     |
| `MODERATION_MODEL`    | Optional. Specifies the AI model to use for command moderation. If a model is not specified, a default model specifically recommended for moderation will be used (rather than the current model of the primary provider).                                                                                                                                                                                                                     | `None`     |

## Agent Capabilities

These settings define what the AI agent is allowed to do.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `FILESYSTEM_ACCESS` | **High Risk.** If `True`, allows the bot to use tools that can read from and write to the local filesystem. See [Agent Mode](/agent-mode/introduction) for details. | `False` |
| `ALLOW_DELEGATION` | If `True`, the agent can spawn sub-agents to handle complex tasks in the background. | `True` |
| `TOOLS_WHITELIST` | A comma-separated list of specific tools the agent is allowed to use. If not set, all available tools are enabled (subject to other flags like `FILESYSTEM_ACCESS`). | `None` (All allowed) |

## MCP (Model Context Protocol)

Settings for the Model Context Protocol integration.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `ENABLE_MCP_SSE` | Enable MCP servers via Server-Sent Events (SSE). | `True` |
| `ENABLE_MCP_STDIO` | Enable MCP servers via Standard I/O (stdio). | `False` |

---

## Next Steps

- **Configure AI providers:** Set up your [AI provider API keys](/configuration/ai-providers).
- **Enable persistent storage:** Learn about [storage and database options](/configuration/storage-database).
- **Secure your bot:** Follow the [security guide](/guides/secure-your-bot) to protect your deployment.
