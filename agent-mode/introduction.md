---
title: 'Agent Mode: Introduction'
description: 'Introduction to Chibi Agent Mode'
---

**Agent Mode** transforms Chibi from a reactive chatbot into a proactive, autonomous agent capable of interacting with your local system.

## What is Agent Mode?

In standard mode, Chibi is sandboxed and can only interact with you via text/images. In **Agent Mode**, Chibi gains access to powerful system-level tools:

*   **Filesystem Access:** Read, write, create, and delete files.
*   **Terminal Execution:** Run shell commands directly.*   
*   **Command Moderation:** All terminal commands are pre-moderated by an AI system supporting 9 providers (Alibaba, Anthropic, DeepSeek, Gemini, Grok, MiniMax, Mistral, Moonshot, OpenAI) to ensure safety and prevent dangerous operations. Optional settings `moderation_provider` and `moderation_model` allow customization.
*   **Task Delegation:** Spawn sub-agents to handle specific subtasks.

This allows Chibi to perform tasks like:
*   Refactoring codebases.
*   Writing and executing tests.
*   Managing system configurations.
*   Analyzing large datasets locally.

## How it Works

Agent Mode is not a separate application. It is simply Chibi with the `FILESYSTEM_ACCESS` configuration enabled.

When enabled, Chibi receives a set of tools (like `run_command_in_terminal`, `create_file`, `replace_in_file`) that allow it to manipulate its environment.

### Task Delegation
While not strictly required, using the **Task Delegation** capability is highly recommended for complex workflows. It allows the main agent to spawn sub-agents for specific units of work (e.g., "Research this library" or "Write tests for this file"). This keeps the main agent's context clean and focused on the high-level objective.

## The Risks

Enabling Agent Mode gives an AI model access to your computer's shell and files.
*   **It can delete files.**
*   **It can run dangerous commands.**
*   **It can hallucinate and make mistakes.**

Therefore, it is recommended to run Agent Mode in an isolated environment (like Docker) rather than directly on your host machine's root filesystem.

### Loop Detection (`LoopDetectedException`)

Agent Mode includes built-in protection against infinite tool call loops that can occur when an AI model gets stuck in repetitive patterns (e.g., repeatedly reading the same file, retrying failed commands, or calling the same tool with slightly different arguments).

**What it prevents:**
*   Infinite loops that would consume API credits and system resources
*   Recursive tool calls that never terminate
*   Models getting stuck in retry cycles

**When it triggers:**
The system uses a `CallTracker` to monitor how many times each tool is called by a specific model:
- **Warning threshold (5 calls):** The system logs a warning and returns an `ABORTED` status to the model, suggesting it might be stuck in a loop.
- **Break threshold (7 calls):** A `LoopDetectedException` is raised, terminating the execution loop.

**How to handle it:**
*   If you encounter this exception, review your task - it may need to be broken down into smaller steps.
*   For complex multi-step tasks, consider using **Task Delegation** to split work across multiple agents.
*   The thresholds can be customized per tool via `loop_warning` and `loop_break` class attributes if needed (advanced).

> **Next:** [Threat Model & Risks](/agent-mode/threat-model-risks)
