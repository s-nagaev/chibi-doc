---
title: 'Pip Installation'
description: 'Install Chibi via pip and use the CLI commands.'
---
## Quick Install

```bash
pip install chibi-bot
```

## CLI Commands

After installation, use `chibi` command:

| Command         | Description                                             |
|-----------------|---------------------------------------------------------|
| `chibi start`   | Start the Chibi bot service as a daemon                 |
| `chibi stop`    | Stop the running Chibi bot service                      |
| `chibi restart` | Restart the Chibi bot service                           |
| `chibi config`  | Open the Chibi configuration file in the default editor |
| `chibi logs`    | Tail the Chibi log file                                 |

## First Time Setup

After installing via pip, run `chibi config` to set up your bot with required API keys:

```bash
chibi config
```

This will open the configuration file in your default editor where you can add your Telegram bot token and other settings.

## Need More Control?

If you need to customize the installation or run from source, see [Manual Setup](manual-setup.md).
