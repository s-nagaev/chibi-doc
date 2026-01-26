---
title: 'Troubleshooting'
description: 'Common issues and how to fix them.'
---

# Troubleshooting

### Bot is not responding
1.  **Check Logs:** Run `docker-compose logs -f` to see if there are any errors.
2.  **Check API Keys:** Ensure your `.env` file has valid API keys for the selected provider.
3.  **Check Telegram Token:** Verify your `TELEGRAM_BOT_TOKEN` is correct.

### "Unauthorized access attempt" in logs
This means someone is trying to use your bot, but they are not in the `USERS_WHITELIST`.
*   **Fix:** Add their ID to the whitelist in `.env` if you want to grant them access.
*   **Ignore:** If it's a stranger, the bot is correctly blocking them.

### Bot doesn't reply in groups
1.  **Privacy Mode:** By default, bots in groups only see messages that mention them (`@botname`) or are replies to them.
2.  **Whitelist:** Ensure the group ID is added to `GROUPS_WHITELIST`.
3.  **Direct Messages Only:** Check if `ANSWER_DIRECT_MESSAGES_ONLY` is set to `True`. If so, the bot might be ignoring group messages intentionally.

### Docker container keeps restarting
*   **Database Error:** If you switched databases (e.g., from Local to Redis), ensure the new service is running.
*   **Port Conflict:** Check if another service is using the same ports.

### Need more help?
Join our support group: [t.me/chibi_support](https://t.me/chibi_support)
