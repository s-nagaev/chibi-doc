# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]
### Added
- New features that are not yet in a stable release.

## [1.6.3] - 2026-02-15
### Changed
- **ZhipuAI Provider:** Renamed env variable containing API Key.
- **Config Generator:** Added `ZHIPUAI_API_KEY` variable with short description.

## [1.6.2] - 2026-02-15
### Added
- **ZhipuAI Provider:** Added support for ZhipuAI (GLM models) as a new LLM provider.
- **MiniMax Image Generation:** Enabled image generation capabilities for the MiniMax provider.
- **Loop Detection:** Implemented `LoopDetectedException` to prevent infinite loops in tool calls.

### Changed
- **Documentation:** Updated README with new providers and API key links.

## [1.6.1] - 2026-02-11
### Added
- **Pre-start security checks** to prevent dangerous bot configurations that could lead to serious security issues.

## [1.6.0] - 2026-02-10
### Added
- **CLI Interface & Pip Installation:** New `chibi` command for easy bot management (`start`, `stop`, `restart`, `config`, `logs`)
- **MiniMax Provider:** Added chat completion support via Anthropic-compatible API
- **Chinese Localization:** Complete README translations for Simplified (zh-CN) and Traditional (zh-TW) Chinese

### Changed
- **Command Moderation System:** Upgraded feature allowing terminal commands to be validated by LLM providers before execution
- **Dependencies Updated:** anthropic 0.75.0 → 0.79.0, google-genai 1.53.0 → 1.62.0, mcp 1.23.1 → 1.26.0, redis 5.2.1 → 7.1.0, and more
- **Thinking Models:** Improved `reasoning_content` preservation for DeepSeek-Reasoner and Moonshot KIMI models
- **MoonshotAI:** Default temperature changed from 0.3 to 1.0 for better reasoning
- **Provider Defaults:** Gemini → `gemini-2.5-pro`, Grok → `grok-4-1-fast-reasoning`, OpenAI → `gpt-5.2`

### Fixed
- **Anthropic Messages:** Fixed loading messages with tools usage when switching providers
- **Telegram Reaction:** Bot now sets `OK` reaction to user message when bot doesn't answer immediately

## [1.5.2] - 2026-01-18
### Added
- **Telegram message reaction:** Bot now will set `OK` reaction to user message bot doesn't answer immediately.

## [1.5.1] - 2026-01-15
### Added
- **System Prompt Versioning:** Introduced system prompt versioning to enable smoother updates.
- **Custom System Prompt:** Added ability to override the default system prompt via `CUSTOM_SYSTEM_PROMPT` variable.
- **Telegram Message Bubbles:** Implemented Telegram message bubbles rendering support.

### Changed
- **Documentation:** Updated README with Telegram message bubbles rendering.
- **Anthropic SDK:** Upgraded to 0.74.0 for better provider support.

## [1.5.0] - 2026-01-12
### Added
- **New Provider: Google Gemini 2.0 (Experimental):** Added support for Gemini 2.0 Flash experimental model.
- **Google Gemini (Nano Banana):** Added image understanding capabilities for Gemini models via `nano-banana` prompting technique.

### Changed
- **Google Gemini:** Updated to use `google-genai` SDK instead of `google-generativeai`.
- **Prompt Engineering:** System prompt refactored for improved performance and clarity.

### Fixed
- **Web Search Tool:** Fixed search results parsing error.

## [1.4.0] - 2026-01-05
### Added
- **New Provider: ElevenLabs:** Integrated ElevenLabs for high-quality Text-to-Speech (TTS).
- **Voice Messages Support:** Bot can now process incoming voice messages by transcribing them using STT.

### Changed
- **Dependencies Updated:** Updated `anthropic`, `openai`, `google-generativeai`, and other dependencies to latest versions.
- **Prompt Engineering:** Improved prompt for better conversation handling and tool use.

### Fixed
- **Tool Use:** Fixed tool use preservation issue when switching between providers.
- **Message Handling:** Fixed issues with message editing and deletion.

## [1.3.0] - 2025-12-20
### Added
- **MCP Support:** Added support for MCP (Model Context Protocol) servers.
- **Telegram Message Editing:** Users can now edit their messages, and the bot will process the edited version.
- **Auto-Delete Messages:** Added option to auto-delete bot messages after a specified timeout.

### Changed
- **Chatbot Personality:** The chatbot's personality and guidelines has undergone a significant overhaul for improved performance and clarity.
- **Updated Existing AI Provider Integrations:** Updated integrations for Alibaba, Grok, and OpenAI to align with their latest APIs and introduce new features.
- **Revised Tool Initialization and Web Search:** The process for initializing tools has been overhauled, and the web search tool (`web_search.py`) specifically refactored for improved performance and reliability.
- **Project Configuration and Dependencies Refresh:** Updated `pyproject.toml`, `Taskfile.yml`, and managed dependencies (`poetry.lock`, `requirements-dev.txt`, `requirements.txt`).

### Removed
- **Unnecessary Dependencies and Configurations:** Cleaned up unneeded dependencies and configurations as part of the overall project restructuring.

### Chore
- **GitHub Actions Workflows Refinements:** Added new steps to GitHub Actions workflows (`.github/workflows/main.yml`) and updated the GitHub setup action (`.github/actions/setup/action.yml`) for optimized CI/CD processes.
- **ARMv7 Dockerfile Experimentation:** Included `armv7.Dockerfile` as part of ongoing experimental efforts to restore ARMv7 platform support. This work is still in progress.
- **Linter and Test Configuration Fixes:** Addressed issues within linter configurations and made improvements to test setup for greater accuracy and coverage.
- **New Comprehensive Test Suites:** Introduced new test files covering database interactions (`test_database.py`), file editor functionalities (`test_file_editor.py`), and model integrity (`test_models.py`).

## [1.2.1] - 2025-04-21
### Added
- Optional heartbeat functionality. The bot can now periodically fetch a specified URL (e.g., a healthchecks.io endpoint or a custom monitoring system endpoint) to signal that it is operational.

## [1.2.0] - 2025-04-20
### Added
- Implemented **initial** support for LLM function calling (tool use).
- Added initial tools available for LLM invocation:
  - `web_search`
  - `search_news`
  - `read_web_page`
  - `get_current_datetime`
- Integrated Vulture for dead code detection in the development workflow.

### Changed
- Updated core project dependencies to their latest compatible versions.
- Replaced Flake8, isort, and Black with Ruff for linting and formatting, streamlining the development toolchain.
- Updated GitHub Actions CI workflow (`Quality Gate`) to use Ruff and Vulture, and optimized setup steps.

### Fixed
- Addressed issues with Telegram Markdown rendering when LLM responses were split into multiple messages.

## [1.1.0] - 2025-04-13
### Added
- Integrated support for new LLM providers:
  - `MoonshotAI (Kimi)`
  - `Cloudflare` (available in the private mode only: temporary unavailable in the public mode)

### Changed
- Project dependencies updated.

## [1.0.0] - 2025-04-01
### Added
- Integrated support for new LLM providers:
  - `Alibaba (Qwen)`
  - `Deepseek`
  - `xAI (Grok)`
  - `Google (Gemini)`

---
[Full Release Notes](https://github.com/s-nagaev/chibi/releases/tag/v1.0.0)
