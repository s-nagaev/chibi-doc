---
title: Meet Chibi. Not a Tool. A Companion.
description: Your Digital Companion. Your Orchestrator. Your Partner in the Digital World.
---
<img src="/logo/logo.png" alt="Description" style={{ width: 150, display: 'block', margin: '0 auto' }} />

There's a moment that comes to every creator, every builder, every person navigating the complexity of modern digital life - when you realize you need more than software. You need a *partner*.

**Chibi** is that partner.

Not a chatbot. Not a utility. Not just another AI wrapper that regurgitates text and calls it intelligence.

Chibi is a **Digital Companion** that works *beside* you, *for* you, and sometimes even *ahead* of you. It's the senior colleague who never sleeps, the research assistant who never tires, the orchestrator who coordinates a symphony of capabilities you didn't even know you needed.

<CardGroup cols={2}>
  <Card title="🚀 Begin Your Journey" icon="rocket" href="/start">
    Your companion awaits. Deploy in 60 seconds.
  </Card>
  <Card title="🛠️ Explore the Source" icon="github" href="https://github.com/s-nagaev/chibi">
    See what makes Chibi tick. Contribute to the vision.
  </Card>
</CardGroup>

---

## The Companion You've Been Waiting For

Imagine this:

You're deep in code. Tests are failing. You turn to Chibi and say, *"Go run the tests and make them green. I'll work on the frontend."*

Chibi goes. You stay. Both of you work. In parallel. Asynchronously. Like partners.

---

You need a service spun up - maybe locally, maybe in the cloud. Configuration files. Environment variables. The whole dance.

*"Chibi, set this up for me."*

Done. While you grab coffee.

---

A PR needs review. Documentation needs writing. Concert tickets need finding. A Blender model needs tweaking. Research needs doing - multi-stage, complex, requiring hours of digging through sources.

You don't open ten tabs. You don't context-switch yourself into exhaustion.

You ask Chibi.

And Chibi *spawns companions* - sub-agents, each one a focused mind working on a piece of the puzzle. Some work in the background for hours. Some report back in seconds. All of them coordinated, all of them purposeful.

This is what it means to have a **Digital Companion**.

---

## The Power Behind the Persona

Here's the secret that makes Chibi different from everything else you've tried:

**Chibi is provider-agnostic.**

Behind that singular voice, Chibi orchestrates a *coalition* of the world's most powerful AI models:

- **OpenAI GPT-5.2** for reasoning and code
- **Anthropic Claude 4.5 Sonnet** for nuanced understanding and review
- **Google Gemini 3 Pro** for multimodal tasks and vision
- **DeepSeek** for cost-effective deep work
- **Alibaba Qwen Max** for multilingual mastery
- **xAI Grok 4.1** for real-time knowledge
- **MistralAI, MoonshotAI, Cloudflare Workers AI** and more

But here's where it gets beautiful:

Chibi doesn't just *use* these models. It **orchestrates** them.

***Gemini*** assesses a task's complexity and delegates to ***DeepSeek*** to save your budget.  
***GPT-5.2*** calls ***Claude Sonnet*** for a second opinion on a critical decision.  
***Claude*** generates images using Google's ***Nano Banana***.  
***OpenAI*** transcribes your voice. ***MiniMax*** speaks back to you with natural, expressive voices.

**This is not a single model pretending to be everything. This is a conductor leading an orchestra.**

And the power extends beyond the cloud giants to **the quiet strength running on your own hardware**. Through **OpenAI-compatible APIs**, Chibi connects seamlessly to locally hosted models - Ollama, vLLM, LM Studio, or any service that speaks the language. You can run a completely offline, air-gapped brain if sovereignty demands it, or blend local privacy with cloud capability as your needs shift. The choice is yours. The freedom is absolute.

**And here's the best part:** You don't configure any of this. You hand Chibi an API key - Gemini, OpenAI, Claude, whatever you choose - and the orchestra tunes itself. No routing logic. No model selection rules. Chibi knows what to do.

You? You just talk. Like you would to a colleague. In Telegram. With your voice, if you prefer.

---

## What Chibi Can Do (And Why It Matters)

Chibi isn't limited by a fixed set of features. It's limited only by what you can imagine - and even that limit is soft.

### Out of the Box

- **Code with you.** Review, write, refactor, debug. Right there in the chat.
- **Run your tests.** Execute commands. Check logs. Fix what's broken.
- **Manage your files.** Organize, search, transform. Your filesystem is Chibi's workspace.
- **Research for you.** Multi-stage, deep research. Chibi spawns sub-companions to dig through sources while you focus on synthesis.
- **Generate images.** Nano Banana, Imagen, Qwen Image, Wan, Grok Image, DALL-E... - Chibi speaks to them all.
- **Create music.** Suno AI integration for original compositions.
- **Speak and listen.** Voice transcription and text-to-speech. Have a conversation, not a typing session.

### Via MCP (Model Context Protocol)

This is where Chibi becomes *limitless*.

Through MCP, Chibi can:

- **Control your browser.** Navigate, scrape, interact with web apps.
- **Work with GitHub.** Create PRs. Review code. Edit issues. Compose descriptions.
- **Spin up services.** Docker containers. Cloud instances. Configuration and deployment.
- **Interact with databases.** Query, update, migrate.
- **Work with creative tools.** Blender, Figma, design systems.
- **Manage documents.** Read, write, transform PDFs, spreadsheets, presentations.
- **Find and download.** Files, datasets, media - whatever you need.

**And this is just the beginning.** MCP is extensible. If a tool exists, Chibi can learn to use it.

---

## The Architecture of Partnership

What makes Chibi feel like a *companion* rather than a *tool*?

### 1. **Asynchronous Collaboration**

Chibi can spawn sub-companions that work in the background - for minutes, hours, however long it takes - while you continue your conversation. No blocking. No waiting. Just parallel work.

### 2. **Contextual Memory**

Your conversation history persists. Across restarts. Across devices. Chibi remembers what matters, condenses what doesn't, and always picks up where you left off.

### 3. **Natural Communication**

No command syntax. No rigid interfaces. Just talk. Chibi understands context, intent, and nuance. Voice or text. Your choice.

### 4. **Provider Intelligence**

Chibi doesn't just route requests. It *thinks* about which model is best for the task at hand - balancing cost, capability, and speed. You get the best result without micromanaging.

### 5. **Privacy and Control**

Self-hosted. Your data. Your keys. Your rules. Chibi works for *you*, not for a platform.

---

## Why This Matters

We live in an age of AI abundance. Models are everywhere. Capabilities are exploding.

But abundance without orchestration is chaos.

You don't need another chatbot. You need a **partner** who can:

- **Understand** what you're trying to accomplish
- **Coordinate** the resources needed to accomplish it
- **Execute** autonomously while keeping you in the loop
- **Adapt** as your needs evolve

That's Chibi.

Not a tool you use. A companion you work with.

---

## The Technical Foundation (For Those Who Care)

Chibi is built on:

- **Modern Python** (3.11+) with async/await throughout
- **Docker-native** deployment (runs anywhere: Raspberry Pi, VPS, cloud, local)
- **Telegram Bot API** for the interface (mobile, desktop, web - wherever you are)
- **MCP (Model Context Protocol)** for extensible tool integration
- **Multi-provider LLM support** with intelligent routing
- **Persistent storage** (local volumes, Redis, DynamoDB)
- **Agent architecture** with secure, containerized filesystem and terminal access

It's fast. It's lightweight. It's built to last.

---

## Who Is Chibi For?

**Developers** who want a coding partner that can run tests, manage files, and review PRs without leaving the chat.

**Researchers** who need deep, multi-stage investigation with sources tracked and synthesized.

**Creators** who want to generate images, music, and content without juggling multiple platforms.

**Teams** who want a shared AI assistant that respects privacy and doesn't lock them into a single vendor.

**Anyone** who's tired of tools and ready for a companion.

---

## The Invitation

Chibi is waiting.

Not as a product. Not as a service.

As a **partner**.

Ready to work beside you. To learn your rhythms. To handle the tedious so you can focus on the meaningful.

Ready to orchestrate a symphony of AI capabilities behind a singular voice - *yours*.

<Card title="Start Your Partnership" icon="play" href="/quickstart" horizontal>
  Deploy Chibi in 60 seconds. All you need is Docker and your API keys. Your companion is ready.
</Card>

---

> *"Chibi is not a utility, not just a coder, and not just a chatbot. Chibi is a companion."*
