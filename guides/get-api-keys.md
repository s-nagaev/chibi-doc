---
title: 'Get API Keys'
description: 'Where to sign up and get API keys for supported providers.'
---

To use Chibi's full potential, you'll need API keys from various AI providers. This guide provides direct links to sign up and generate keys for each supported service.

## 🤖 Major LLM Providers
| Provider | Key Variable | Sign Up & Get Key | Notes |
| :--- | :--- | :--- | :--- |
| **OpenAI** | `OPENAI_API_KEY` | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) | GPT-4, GPT-4o, DALL·E 3, Whisper. |
| **Anthropic** | `ANTHROPIC_API_KEY` | [console.anthropic.com](https://console.anthropic.com/) | Claude 3.5 Sonnet, Claude 3 Opus. Navigate to "API Keys". |
| **Google** | `GEMINI_API_KEY` | [aistudio.google.com/apikey](https://aistudio.google.com/app/apikey) | Gemini Pro/Flash, Imagen, Nano Banana. Often has a generous free tier. |
| **DeepSeek** | `DEEPSEEK_API_KEY` | [platform.deepseek.com](https://platform.deepseek.com/) | Strong coding models (DeepSeek-V3), very cost-effective. |
| **xAI** | `GROK_API_KEY` | [console.x.ai](https://console.x.ai/) | Grok models. Check [docs.x.ai](https://docs.x.ai/) for API access. |
| **Mistral AI** | `MISTRALAI_API_KEY` | [console.mistral.ai](https://console.mistral.ai/) | European open-weights models. Navigate to "API Keys". |
| **Alibaba Cloud** | `ALIBABA_API_KEY` | [modelstudio.console.alibabacloud.com](https://modelstudio.console.alibabacloud.com?tab=playground#/api-key) | Qwen (text) and Wan (image) models via DashScope. |
| **Moonshot AI** | `MOONSHOTAI_API_KEY` | [platform.moonshot.cn](https://platform.moonshot.cn/) | Kimi models with long context (200K+ tokens). |
| **MiniMax** | `MINIMAX_API_KEY` | [platform.minimaxi.com](https://platform.minimaxi.com/) | Text generation (MiniMax-M2.x) and high-quality speech synthesis. |
## ☁️ Cloud & Infrastructure

| Provider | Key Variable | Sign Up & Get Key | Notes |
| :--- | :--- | :--- | :--- |
| **Cloudflare** | `CLOUDFLARE_API_KEY` | [dash.cloudflare.com/profile/api-tokens](https://dash.cloudflare.com/profile/api-tokens) | Workers AI (44+ open-source models). Requires `CLOUDFLARE_ACCOUNT_ID` and API token with `Account.Workers AI` permissions. |
| **AWS** | `AWS_ACCESS_KEY_ID` | [aws.amazon.com](https://aws.amazon.com/) | For DynamoDB storage backend. Also requires `AWS_SECRET_ACCESS_KEY`. |

## 🎨 Creative & Specialized Services

| Provider | Key Variable | Sign Up & Get Key | Notes |
| :--- | :--- | :--- | :--- |
| **ElevenLabs** | `ELEVEN_LABS_API_KEY` | [elevenlabs.io](https://elevenlabs.io/) | Premium Text-to-Speech and voice cloning. Navigate to profile → API Keys. |
| **Suno** | `SUNO_API_ORG_API_KEY` | [sunoapi.org](https://sunoapi.org/) | Music generation via unofficial API. Sign up and navigate to API Keys. |
| **Jina AI** | `JINA_API_KEY` | [jina.ai](https://jina.ai/) | For "Reader" (web scraping) and embeddings. |

## 🔧 Self-Hosted / Local Options

For **OpenAI-compatible endpoints** (Ollama, vLLM, LM Studio, etc.), you typically don't need external API keys:

| Service | Key Variable | Setup Link | Notes |
| :--- | :--- | :--- | :--- |
| **Ollama** | `CUSTOMOPENAI_API_KEY` | [ollama.com](https://ollama.com/) | Set `CUSTOMOPENAI_URL=http://localhost:11434/v1`. Key can be any non-empty string. |
| **vLLM** | `CUSTOMOPENAI_API_KEY` | [docs.vllm.ai](https://docs.vllm.ai/) | Point `CUSTOMOPENAI_URL` to your vLLM server. |
| **LM Studio** | `CUSTOMOPENAI_API_KEY` | [lmstudio.ai](https://lmstudio.ai/) | Default: `CUSTOMOPENAI_URL=http://localhost:1234/v1`. |

## 🔐 Security Tips

- **Never commit API keys to version control.** Use `.env` files and add them to `.gitignore`.
- **Use environment variables** or secret management tools (e.g., Docker secrets, AWS Secrets Manager).
- **Rotate keys regularly**, especially if they're exposed or shared.
- **Monitor usage** via provider dashboards to detect unauthorized access.
- **Set spending limits** where available (OpenAI, Anthropic, etc.) to avoid surprise bills.

## 💡 Public Mode

If you're running Chibi in **Public Mode** (`PUBLIC_MODE=True`), you don't need to provide master API keys. Instead, each user will be prompted to provide their own keys via private message when they first interact with the bot.

This is ideal for:
- Shared/community bots
- Avoiding centralized billing
- Letting users control their own API usage

See [Deployment Modes](../configuration/deployment-modes.md) for more details.

---

**Need help?** Check the [FAQ](../support/faq.md) or [Troubleshooting](../support/troubleshooting.md) guide.
