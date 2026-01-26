---
title: 'Get API Keys'
description: 'Where to sign up and get API keys for supported providers.'
---

To use Chibi's full potential, you'll need API keys from various AI providers. Here is a list of supported services and where to get their keys.

## Major LLM Providers

| Provider | Key Variable | Sign Up Link | Notes |
| :--- | :--- | :--- | :--- |
| **OpenAI** | `OPENAI_API_KEY` | [platform.openai.com](https://platform.openai.com/api-keys) | GPT-4, DALL-E 3, Whisper. |
| **Anthropic** | `ANTHROPIC_API_KEY` | [console.anthropic.com](https://console.anthropic.com/) | Claude 3 models. |
| **Google Gemini** | `GEMINI_API_KEY` | [aistudio.google.com](https://aistudio.google.com/) | Gemini Pro/Flash. Often has a free tier. |
| **DeepSeek** | `DEEPSEEK_API_KEY` | [platform.deepseek.com](https://platform.deepseek.com/) | Strong coding models, very cost-effective. |
| **Mistral** | `MISTRAL_API_KEY` | [console.mistral.ai](https://console.mistral.ai/) | European open-weights models. |
| **Groq** | `GROQ_API_KEY` | [console.groq.com](https://console.groq.com/) | Extremely fast inference for Llama/Mixtral. |
| **Alibaba** | `DASHSCOPE_API_KEY` | [bailian.console.aliyun.com](https://bailian.console.aliyun.com/) | Qwen (text) and Wan (image) models. |
| **MiniMax** | `MINIMAX_API_KEY` | [platform.minimaxi.com](https://platform.minimaxi.com/) | Known for high-quality speech synthesis. |
| **Moonshot** | `MOONSHOT_API_KEY` | [platform.moonshot.cn](https://platform.moonshot.cn/) | Kimi models (long context). |

## Cloud & Infrastructure

| Provider | Key Variable | Sign Up Link | Notes |
| :--- | :--- | :--- | :--- |
| **Cloudflare** | `CLOUDFLARE_API_TOKEN` | [dash.cloudflare.com](https://dash.cloudflare.com/profile/api-tokens) | Workers AI. Requires `CLOUDFLARE_ACCOUNT_ID` too. |
| **AWS** | `AWS_ACCESS_KEY_ID` | [aws.amazon.com](https://aws.amazon.com/) | For DynamoDB (storage). |

## Specialized Services

| Provider | Key Variable | Sign Up Link | Notes |
| :--- | :--- | :--- | :--- |
| **ElevenLabs** | `ELEVENLABS_API_KEY` | [elevenlabs.io](https://elevenlabs.io/) | Premium Text-to-Speech. |
| **Jina AI** | `JINA_API_KEY` | [jina.ai](https://jina.ai/) | For "Reader" (web scraping) and embeddings. |
| **Suno** | N/A | [suno.com](https://suno.com) | Music generation. Uses unofficial API (see docs). |
