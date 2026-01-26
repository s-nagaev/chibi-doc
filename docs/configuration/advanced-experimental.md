# Advanced & Experimental Settings

This section covers advanced configuration for fine-tuning model behavior, image generation, and enabling experimental features like the Model Context Protocol (MCP).

## Image Generation

Control the behavior of the `/image` command and manage usage limits. For a complete guide, see [multimedia generation](/guides/multimedia-generation).

| Variable                      | Description                                                                                                                         | Default     |
|:------------------------------|:------------------------------------------------------------------------------------------------------------------------------------|:------------|
| `IMAGE_GENERATIONS_LIMIT`     | A monthly limit on the number of images a user can generate. Set to `0` for unlimited. This helps manage API costs.                 | `0`         |
| `IMAGE_GENERATIONS_WHITELIST` | A comma-separated list of users (usernames or IDs) who are exempt from the image generation limit.                                  | `None`      |
| `IMAGE_N_CHOICES`             | The number of image variations to generate per request.                                                                             | `1`         |
| `IMAGE_QUALITY`               | The quality of the generated image. Options like `standard` or `hd` can affect cost and detail.                                     | `standard`  |
| `IMAGE_SIZE`                  | The default dimensions for the generated image (e.g., `1024x1024`).                                                                 | `1024x1024` |
| `IMAGE_ASPECT_RATIO`          | The default aspect ratio (e.g., `16:9`, `1:1`). This provides a more intuitive way to control image shape than specific dimensions. | `16:9`      |

## Context & Sampling

Fine-tune the AI's responses by controlling context length and sampling parameters. These settings directly impact the creativity, coherence, and cost of the model's output.

| Variable                       | Description                                                                                                                                                                              | Default |
|:-------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------|
| `MAX_HISTORY_TOKENS`           | The maximum number of tokens from the conversation history to send with each new request. A lower value saves costs but may cause the bot to "forget" earlier parts of the conversation. | `64000` |
| `MAX_TOKENS`                   | The maximum number of tokens the model is allowed to generate in its response. Prevents overly long or expensive replies.                                                                | `32000` |
| `TEMPERATURE`                  | Controls the randomness of the output. A value closer to `0.0` makes the model more deterministic and focused, while a value closer to `2.0` makes it more creative and unpredictable.   | `1.0`   |
| `FREQUENCY_PENALTY`            | A value that penalizes new tokens based on their existing frequency in the text so far, discouraging the model from repeating the same lines verbatim.                                   | `0.0`   |
| `PRESENCE_PENALTY`             | A value that penalizes new tokens based on whether they appear in the text so far, encouraging the model to introduce new topics.                                                        | `0.0`   |
| `MAX_CONVERSATION_AGE_MINUTES` | The maximum time in minutes that a conversation context is considered "active." Older conversations will be pruned to manage memory.                                                     | `360`   |

## Model Context Protocol (MCP)

MCP allows Chibi to integrate with external tools and services, giving it powerful new capabilities. Learn more about [Agent Mode](/agent-mode/introduction) and MCP integration.

| Variable           | Description                                                                                                              | Default |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------|:--------|
| `ENABLE_MCP_SSE`   | Set to `True` to enable the Server-Sent Events (SSE) based MCP, allowing for real-time, asynchronous tool communication. | `True`  |
| `ENABLE_MCP_STDIO` | Set to `True` to enable the Standard I/O (stdio) based MCP, for integrating with local command-line tools.               | `False` |

## Heartbeat (Health Monitoring)

Configure a "heartbeat" to send periodic pings to an external monitoring service. This is a simple way to verify that your bot is alive and running.

| Variable | Description | Default |
| :--- | :--- | :--- |
| `HEARTBEAT_URL` | The endpoint URL of your monitoring service (e.g., Healthchecks.io, Uptime Kuma). | `None` |
| `HEARTBEAT_FREQUENCY_CALL` | The interval in seconds between each heartbeat ping. | `30` |
| `HEARTBEAT_RETRY_CALLS` | The number of times to retry a failed ping before considering the connection lost. | `3` |
| `HEARTBEAT_PROXY` | A proxy to use for sending heartbeat requests. | `None` |


---

## Next Steps

- **Enable Agent Mode:** Explore the [Agent Mode introduction](/agent-mode/introduction) for advanced automation capabilities.
- **Configure multimedia:** Set up [image and music generation](/guides/multimedia-generation).
- **Review core settings:** Check the [core settings](/configuration/core-settings) for essential configuration options.
- **Need help?** Visit the [troubleshooting guide](/support/troubleshooting) or [FAQ](/support/faq).
