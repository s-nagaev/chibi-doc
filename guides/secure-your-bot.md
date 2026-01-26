---
title: 'Secure Your Bot'
description: 'Essential security configurations for access control and privacy.'
---

By default, Chibi is a private bot. However, misconfiguration can expose it to unauthorized users. This guide covers the essential settings to keep your bot secure.

## Access Control (Whitelists)

The most effective way to secure your bot is to strictly limit who can use it.

### User Whitelist
Use `USERS_WHITELIST` to specify exactly which Telegram users are allowed to interact with the bot.

*   **By ID (Recommended):** `123456789,987654321`
*   **By Username:** `@myusername,@friend`

```dotenv
# .env
USERS_WHITELIST=123456789,@myusername
```

### Group Whitelist
If you add the bot to a group, use `GROUPS_WHITELIST` to ensure it only responds in authorized groups.

```dotenv
# .env
GROUPS_WHITELIST=-1001234567890
```

## Privacy & Behavior Flags

Fine-tune how the bot behaves in public or shared spaces.

### `ANSWER_DIRECT_MESSAGES_ONLY`
*   **Default:** `True`
*   **Effect:** If set to `True`, the bot will ignore messages in groups unless that specific group is in the `GROUPS_WHITELIST`. It will still respond to direct messages (DMs) from whitelisted users.
*   **Use Case:** Prevents the bot from being spammy or used by others if you accidentally add it to a public group.

### `ALLOW_BOTS`
*   **Default:** `False`
*   **Effect:** If set to `False`, Chibi will ignore all messages sent by other bots.
*   **Use Case:** Prevents infinite loops where two bots keep replying to each other. **Keep this disabled unless you have a specific reason.**

## Best Practices

1.  **Never share your `.env` file.** It contains your API keys and bot token.
2.  **Use IDs over Usernames.** Usernames can be changed; IDs are permanent. You can find your ID using bots like `@userinfobot`.
3.  **Review Logs.** Periodically check your logs for "Unauthorized access attempt" messages to see if strangers are trying to use your bot.
