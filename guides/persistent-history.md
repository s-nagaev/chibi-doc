# How to Enable Persistent Conversation History

This guide will help you configure Chibi to maintain conversation history across restarts, ensuring continuity and context.

## Objective

To store conversation data persistently, allowing the bot to remember past interactions even after it has been restarted or redeployed.

## Prerequisites

*   Docker and Docker Compose installed and configured.
*   Access to your `docker-compose.yml` file.

## Steps

### 1. Define a Docker Volume

Open your `docker-compose.yml` file. In the top-level `volumes:` section, define a named volume. This volume will be managed by Docker and will persist data on your host machine.

**Example (docker-compose.yml):**
```yaml
volumes:
  chibi_data:
    # You can optionally specify a driver or external configuration here
```

### 2. Mount the Volume to the Container

Locate the service definition for your Chibi bot (usually named `chibi` or similar). Add a `volumes:` entry under this service to mount the named volume you defined in the previous step to the `/app/data` directory inside the container. This is where Chibi stores its persistent data.

**Example (docker-compose.yml):**
```yaml
services:
  chibi:
    # ... other configurations ...
    volumes:
      - chibi_data:/app/data
    # ... other configurations ...
```

### 3. Deploy the Stack

Save your `docker-compose.yml` file. Then, deploy your stack using Docker Compose. This command will create the volume if it doesn't exist and start the Chibi container with the volume mounted.

```bash
docker-compose up -d
```

> **Tip:** Using named volumes is the recommended way to handle persistent data for Docker containers as it abstracts away the host path and allows Docker to manage the volume lifecycle.

## Verification

After restarting the bot, send it a message that relies on previous context. If the bot responds correctly, acknowledging the prior conversation, your persistent history is working.

> **Warning:** Ensure you have sufficient disk space on your host machine for the Docker volume, as it will grow with the conversation history.