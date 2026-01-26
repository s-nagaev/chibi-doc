---
title: 'Agent Mode: Best Practices'
description: 'Practical tips for using Chibi Agent Mode effectively'
---

## 1. Start with a Clear, Specific Goal

The quality of your high-level objective directly impacts the agent's performance.

-   **Bad Goal:** "Fix my project."
-   **Good Goal:** "In the `./src` directory, refactor all Python files to use the `logging` module instead of `print` statements. Ensure all changes pass the existing pytest suite."

A specific goal reduces the chance of the agent misinterpreting the task and performing unintended actions.

## 2. Operate in a Version-Controlled Environment

This is your safety net. Always run Agent Mode on a project that is under version control (e.g., Git).

-   **Commit Before Starting:** Ensure you have a clean working directory.
-   **Review Changes:** Use `git diff` to see exactly what the agent modified.
-   **Revert if Needed:** If the agent messes up, you can instantly revert to the previous state.

## 3. Supervise the First Run

Before letting the agent run fully autonomously on a large task, supervise its initial steps.

-   **Ask for a Plan:** Before giving the go-ahead, ask Chibi: *"What is your plan to achieve this?"*.
-   **Check the "Thoughts":** If `SHOW_LLM_THOUGHTS` is enabled, read the agent's internal reasoning to ensure it understands the context correctly.
-   **Monitor:** Keep an eye on the output to ensure it's not going down a rabbit hole.

> **Return to:** [Agent Mode Introduction](introduction.md)
