---
title: 'AI Providers & Models'
description: 'Configure API keys, models, and generation parameters for text, image, and voice.'
---

Chibi supports a wide range of AI providers. You can configure which models to use for text, images, and voice, as well as fine-tune their behavior.

## Master API Keys

To use a specific provider, you must set its corresponding API key in your `.env` file.

| Provider          | Variable                | Description                                           |
|:------------------|:------------------------|:------------------------------------------------------|
| **OpenAI**        | `OPENAI_API_KEY`        | Required for GPT-5, o3, DALL-E 3, Whisper.            |
| **Anthropic**     | `ANTHROPIC_API_KEY`     | Required for Claude 4.5 models.                       |
| **Google Gemini** | `GEMINI_API_KEY`        | Required for Gemini 2.5/3.0 and Imagen 4.0.           |
| **DeepSeek**      | `DEEPSEEK_API_KEY`      | Required for DeepSeek Chat.                           |
| **Mistral**       | `MISTRALAI_API_KEY`     | Required for Mistral models.                          |
| **xAI (Grok)**    | `GROK_API_KEY`          | Required for Grok models.                             |
| **Alibaba**       | `ALIBABA_API_KEY`       | Required for Qwen (text) and Wan (image) models.      |
| **Cloudflare**    | `CLOUDFLARE_API_KEY`    | Required for Workers AI models.                       |
| **Cloudflare**    | `CLOUDFLARE_ACCOUNT_ID` | **Required** if using Cloudflare. Your Account ID.    |
| **MiniMax**       | `MINIMAX_API_KEY`       | Required for MiniMax models (Text & Speech).          |
| **Moonshot**      | `MOONSHOTAI_API_KEY`    | Required for Kimi models.                             |
| **ElevenLabs**    | `ELEVEN_LABS_API_KEY`   | Required for ElevenLabs TTS.                          |
| **Suno**          | `SUNO_API_ORG_API_KEY`  | Required for Suno music generation (via sunoapi.org). |
| **Google Search** | `GOOGLE_SEARCH_API_KEY` | Required for Google Search tool.                      |
| **Google Search** | `GOOGLE_SEARCH_CX`      | Required Custom Search Engine ID.                     |

## Model Configuration

You can specify which models Chibi should use by default.

| Variable              | Description                                                        | Default              |
|:----------------------|:-------------------------------------------------------------------|:---------------------|
| `DEFAULT_MODEL`       | The default LLM for text chat.                                     | `None` (Auto-select) |
| `DEFAULT_PROVIDER`    | The default provider for text chat.                                | `None` (Auto-select) |
| `DEFAULT_IMAGE_MODEL` | The default model for image generation.                            | `None` (Auto-select) |
| `MODERATION_PROVIDER` | The provider for command moderation.                               | `None`               |
| `MODERATION_MODEL`    | The model used for command moderation.                             | `None`               |
| `MODELS_WHITELIST`    | Comma-separated list of allowed models. If empty, all are allowed. | `None`               |

### Available Models (Examples)
*   **OpenAI:** `gpt-5.2`, `gpt-5.1`, `o3`, `o4-mini`
*   **Anthropic:** `claude-sonnet-4-5-20250929`, `claude-haiku-4-5-20251001`
*   **Grok:** `grok-4-1-fast-reasoning`, `grok-beta`
*   **Gemini:** `gemini-2.5-pro`, `gemini-3-pro`
*   **Alibaba:** `qwen3-max`, `qwen-max`

## Text Generation Parameters

Fine-tune how the LLM generates text.

| Variable      | Description                               | Default |
|:--------------|:------------------------------------------|:--------|
| `TEMPERATURE` | Controls randomness (0.0 to 2.0).         | `0.5`   |
| `MAX_TOKENS`  | The maximum number of tokens to generate. | `32000` |
| `TIMEOUT`     | Request timeout in seconds.               | `600`   |
| `RETRIES`     | Number of retries on failure.             | `3`     |

## Image Generation Settings

Configure the quality and dimensions of generated images.

| Variable                  | Description                             | Default     |
|:--------------------------|:----------------------------------------|:------------|
| `IMAGE_SIZE`              | Default resolution (e.g., `1024x1024`). | `1024x1024` |
| `IMAGE_QUALITY`           | Quality setting (mostly for DALL-E 3).  | `standard`  |
| `IMAGE_ASPECT_RATIO`      | Aspect ratio (e.g., `16:9`).            | `16:9`      |
| `IMAGE_GENERATIONS_LIMIT` | Daily limit per user.                   | `5`         |

### Provider-Specific Image Sizes
Some providers require specific resolutions. You can override the default `IMAGE_SIZE` for them:
*   `IMAGE_SIZE_NANO_BANANA` (for Gemini Image models)
*   `IMAGE_SIZE_IMAGEN` (for Imagen 4.0)
*   `IMAGE_SIZE_ALIBABA` (for Wan/Qwen Image)

## Voice & Audio (STT/TTS)

Configure Speech-to-Text (STT) and Text-to-Speech (TTS) capabilities.

| Variable       | Description                               | Default              |
|:---------------|:------------------------------------------|:---------------------|
| `STT_PROVIDER` | Provider for transcribing voice messages. | `None` (Auto-select) |
| `STT_MODEL`    | Model used for transcription.             | `None` (Auto-select) |
| `TTS_PROVIDER` | Provider for generating voice responses.  | `None` (Auto-select) |
| `TTS_MODEL`    | Model used for speech generation.         | `None` (Auto-select) |
### MiniMax TTS Specific Settings
For MiniMax Text-to-Speech, you can configure the following:

| Variable      | Description                               | Default              |
|:--------------|:------------------------------------------|:---------------------|
| `MINIMAX_TTS_MODEL` | The specific MiniMax TTS model to use.    | `speech-2.8-turbo`   |
| `MINIMAX_TTS_VOICE` | The voice to use for MiniMax TTS.         | `Korean_HaughtyLady` |

