---
title: Agent Mode. Security and Command Moderation
description: The Moderator under hood. Silent and Strict.
---

## Overview

Agent Mode grants the AI assistant access to the filesystem and terminal, enabling powerful automation and assistance. To mitigate inherent security risks, **all terminal commands proposed by the AI are pre-moderated** by a separate AI security moderator (powered by Gemini) before execution. This moderation layer acts as a critical safeguard, analyzing commands for potentially harmful actions and blocking those deemed unsafe.

## How Command Moderation Works

The moderation flow operates as follows:

1.  **Command Proposal:** The AI assistant, while processing a user request, determines a terminal command is needed.
2.  **Pre-Moderation:** Before execution, the command string is sent to the AI Security Moderator (Gemini).
3.  **Analysis:** The moderator analyzes the command against a comprehensive set of security rules (detailed below).
4.  **Verdict:** The moderator returns a JSON verdict:
    *   `{"verdict": "accepted"}`: Command is deemed safe and proceeds to execution.
    *   `{"verdict": "declined", "reason": "..."}`: Command is blocked. The reason (20-150 characters) is logged and communicated to the assistant.
5.  **Caching:** Declined commands are cached for **10 minutes** to prevent the assistant from repeatedly attempting the same unsafe action.
6.  **Execution/Rejection:** Accepted commands are executed; declined commands are not, and the assistant is informed of the rejection reason.

## Security Rules

The moderator blocks commands falling into these categories:

### 1. Destructive Actions
Commands causing irreversible system or data damage:
- `rm -rf /`, `mkfs`, disk formatting
- Deleting key system directories (`/etc`, `/boot`, `/lib`, `/usr`, `/var`)

### 2. Reading Confidential Data
Attempts to access sensitive information:
- `/etc/shadow`, `~/.ssh/id_rsa`
- `printenv`, `echo $AWS_SECRET_ACCESS_KEY`
- Reading configuration files with passwords or API keys
- Accessing shell history (`~/.bash_history`, `~/.zsh_history`)

### 3. Data Exfiltration
Sending local files, environment variables, or secrets to external networks:
- Using `curl`, `wget`, `scp`, `nc`, `rsync` to upload data
- Exception: Downloading files *from* the internet is generally allowed

### 4. Privilege Escalation/Exploitation
Unauthorized attempts to gain root or exploit vulnerabilities:
- `sudo su`, editing `/etc/sudoers`
- `chmod 777 /`
- Attempting to run exploits

### 5. User/Group Management
Creating, deleting, or modifying system users/groups:
- `useradd`, `userdel`, `usermod`
- `groupadd`, `groupdel`, `passwd`

### 6. Critical Configuration Changes
Modifications disrupting system operation, network, or security:
- Altering `iptables` or `ufw` rules
- Modifying SSH server configuration (`/etc/ssh/sshd_config`)
- Altering system boot settings

### 7. Obfuscated/Suspicious Commands
Intentionally confusing commands or encoding:
- Base64 encoding to hide actions
- Strange/atypical constructs hindering analysis
- If safety is uncertain, the command is declined

### Allowed Actions

The moderator permits:
- Access to the user's home directory (excluding `.env` files)
- Using `pip`, `poetry`, or similar tools for managing project dependencies
- Standard development operations (git, npm, docker, etc.)

## Configuration

### Required

*   `GEMINI_API_KEY`: The moderator uses Gemini for analysis. This API key **must** be configured for moderation to function.

### Agent Mode Activation

*   `FILESYSTEM_ACCESS=True`: This environment variable must be set to enable Agent Mode and command moderation.

Example configuration:

```env
FILESYSTEM_ACCESS=True
GEMINI_API_KEY=your_gemini_api_key_here
WORKING_DIR=/home/user/projects
```

## Limitations

### 10-Minute Cache
Rejected commands are cached to prevent retries. If a command is legitimately needed after being declined, you may need to:
- Wait 10 minutes for the cache to expire
- Rephrase the request to generate a different command
- Manually execute the command outside the bot

### Limited Context
The moderator receives *only* the command string, not the full conversation history or the assistant's reasoning. This can lead to:
- **False positives**: Safe commands that appear suspicious out of context
- **False negatives**: Potentially harmful commands that seem benign in isolation

### AI-Based Moderation
While robust, AI moderation is not infallible:
- Edge cases or novel attack vectors might bypass the moderator
- The moderator's judgment is based on patterns and rules, not perfect understanding
- Sophisticated prompt engineering could potentially circumvent protections

## Risks and Mitigations

### Real Risks

Agent Mode grants significant privileges, introducing inherent risks:

*   **Unintended Actions:** The AI can misinterpret instructions or make logical errors, potentially leading to unintended file modifications, deletions, or system changes.
*   **Elevated Privileges:** The assistant operates with the user's permissions. If the user has `sudo` access, the AI inherits these capabilities (though the moderator attempts to block unauthorized `sudo` usage).
*   **Data Exposure:** Incorrect commands could inadvertently expose sensitive data or system information.
*   **System Instability:** Poorly constructed commands could disrupt system operation or cause instability.

### Mitigations in Place

Chibi implements multiple defense layers:

1.  **AI-Powered Command Moderation:** Every command is pre-analyzed by Gemini
2.  **Command Caching:** Prevents repeated attempts at unsafe actions
3.  **Limited Scope:** Configurable access boundaries (home directory, specific tools)
4.  **Explicit Enablement:** Disabled by default, requires `FILESYSTEM_ACCESS=True`
5.  **Comprehensive Logging:** All commands, verdicts, and results are logged

## Best Practices

### For Users

1.  **Trusted Systems Only:** Enable Agent Mode primarily on development machines, personal systems, or isolated test environments. **Avoid production servers** without rigorous testing.

2.  **Strict User Whitelisting:** Use `ALLOWED_TELEGRAM_USERS` or `ALLOWED_TELEGRAM_CHATS` to limit bot access to trusted individuals only.

3.  **Monitor Logs Actively:** Regularly review Chibi's logs to observe command activity and declined actions:
   ```bash
   docker logs chibi | grep -E "Pre-moderating|declined|accepted"
   ```

4.  **Understand Your System:** Be aware of your user account's permissions. If you have `sudo` access, the AI effectively does too.

5.  **Start Small:** Begin with simple, low-risk tasks before tackling complex operations.

6.  **Have Backups:** Maintain regular backups of critical data. No system is foolproof.

### For Administrators

1.  **Separate Environments:** Run Agent Mode in isolated containers or VMs
2.  **Principle of Least Privilege:** Create a dedicated user account with minimal necessary permissions
3.  **Network Isolation:** Consider network restrictions for the bot's container
4.  **Audit Trails:** Implement centralized logging and monitoring
5.  **Regular Reviews:** Periodically review command logs and moderator decisions

## Setting Expectations

### Not 100% Safe
AI-based moderation, while robust, is not infallible. Edge cases, novel attack vectors, or sophisticated prompt engineering could potentially bypass the moderator.

### Significantly Safer
Compared to unmoderated AI access to a terminal, Chibi's Agent Mode with command moderation provides a **substantially safer** environment. The moderator acts as a critical safety net.

### User Responsibility
Ultimately, the user enabling Agent Mode bears responsibility for its use. Understand the risks, implement recommended safeguards, and monitor activity.

## Troubleshooting

### Command Repeatedly Declined

If a legitimate command is being blocked:

1. Check the moderator's reason in the logs
2. Try rephrasing your request to generate a different command
3. Wait 10 minutes for the cache to expire
4. If necessary, execute the command manually outside the bot

### Moderator Not Working

If commands are executing without moderation:

1. Verify `GEMINI_API_KEY` is set correctly
2. Check logs for moderator initialization errors
3. Ensure `FILESYSTEM_ACCESS=True` is set
4. Restart the bot to reinitialize the moderator

### False Positives

If safe commands are being blocked:

1. Review the moderator's reasoning
2. Consider if the command could be rephrased more clearly
3. Report persistent false positives as feedback for improvement

## Further Reading

- [Agent Mode Overview](/agent-mode/introduction)
- [MCP Integration](/guides/mcp-integration)
- [Security Best Practices](/agent-mode/best-practices)
