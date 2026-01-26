---
title: 'FAQ'
description: 'Frequently Asked Questions about Chibi.'
---

# Frequently Asked Questions

### What is the difference between Chibi and other bots?
Chibi is designed as a **Digital Companion**, not just a tool. It features persistent memory, supports multiple AI providers (OpenAI, Anthropic, Gemini, etc.), and can perform autonomous tasks on your computer via Agent Mode.

### How do I change the bot's personality?
You can use **Skills**. Chibi comes with a set of built-in skills (like "Coder", "Translator", etc.) located in the `skills/` directory. You can also ask the bot to "remember" facts about you to personalize its responses.

### Can I run Chibi on my local machine without Docker?
Yes, but it is **not recommended for Agent Mode**. Docker provides a necessary security sandbox. For simple chat functionality, running locally via Python/Poetry is fine.

### Is my data safe?
Chibi stores data locally on your machine (or in your private database). It does not send your chat history to any third-party servers other than the AI providers you configure (e.g., OpenAI).

### How do I get help?
If you encounter issues or have feature requests:

*   **Telegram Group:** [t.me/chibi_support](https://t.me/chibi_support)
*   **GitHub Issues:** [Report a bug](https://github.com/s-nagaev/chibi/issues)
