---
title: 'Manual Installation'
description: 'Run Chibi directly from source code.'
---

# Manual Installation

This guide covers how to run Chibi directly from the source code. This is useful for development or if you cannot use Docker.

## Prerequisites

-   **Python 3.10+**: Ensure Python is installed (`python --version`).
-   **Poetry**: Chibi uses Poetry for dependency management. [Install Poetry](https://python-poetry.org/docs/#installation).
-   **Git**: To clone the repository.

## Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/s-nagaev/chibi.git
cd chibi
```

### 2. Install Dependencies

Use Poetry to install the required Python packages.

```bash
poetry install
```

### 3. Configure Environment

Copy the example configuration file and edit it.

```bash
cp .env.example .env
```

Edit `.env` with your API keys and settings:

```dotenv
TELEGRAM_BOT_TOKEN=your_token
OPENAI_API_KEY=sk-...
# ... other keys
```

### 4. Run the Bot

Start the bot using Poetry:

```bash
poetry run python main.py
```

> **Note:** We are working on simplifying the installation process. Soon you will be able to install Chibi with a single command via `pip install`.

## Troubleshooting

*   **Poetry not found:** Make sure Poetry is in your PATH.
*   **Python version mismatch:** Chibi requires Python 3.10 or newer.
