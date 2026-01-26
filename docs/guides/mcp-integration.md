# MCP (Model Context Protocol) Integration

## What is MCP?

The Model Context Protocol (MCP) is an open standard that enables AI assistants to securely connect to external data sources and tools. It provides a standardized way for language models to interact with various services, databases, APIs, and local resources beyond their built-in capabilities.

## How it Works in Chibi

Chibi integrates MCP to dynamically extend the bot's capabilities. When an MCP server is connected, its tools become available to the AI assistant. The assistant can then use these tools to:

*   Access filesystems, databases, or APIs
*   Execute specialized operations (e.g., image processing, data analysis)
*   Integrate with third-party services

MCP servers communicate with Chibi via two transport methods: **SSE (Server-Sent Events)** for remote servers and **Stdio (Standard Input/Output)** for local processes.

## Configuration

MCP integration is controlled by environment variables:

*   `ENABLE_MCP_SSE` (default: `True`): Enables SSE-based MCP server connections.
*   `ENABLE_MCP_STDIO` (default: `False`): Enables Stdio-based MCP server connections (for local processes).

Set these in your `.env` file or environment:

```env
ENABLE_MCP_SSE=True
ENABLE_MCP_STDIO=False
```

## Using MCP Servers

### Connecting an SSE Server

To connect to a remote MCP server via SSE, ask the AI assistant:

```
Connect to MCP server "my-server" at https://example.com/mcp
```

The assistant will use the `initialize_sse_mcp_server` tool with the server name and URL.

### Connecting a Stdio Server

To connect to a local MCP server via Stdio, ask the AI assistant:

```
Connect to MCP server "local-fs" using command "node" with args ["/path/to/server.js"]
```

The assistant will use the `initialize_stdio_mcp_server` tool to start the local process and establish communication.

## Examples

### Example 1: Filesystem Server

Connect to an MCP filesystem server to allow the assistant to read/write files in a specific directory:

```
Initialize MCP server "filesystem" via stdio with command "npx" and args ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed/directory"]
```

### Example 2: Database Server

Connect to a database MCP server (e.g., PostgreSQL):

```
Initialize MCP server "postgres" via SSE at https://my-mcp-db-server.com/mcp
```

### Example 3: GitHub Integration

Connect to the official MCP GitHub server:

```
Initialize MCP server "github" via stdio with command "npx" and args ["-y", "@modelcontextprotocol/server-github"]
```

This requires `GITHUB_PERSONAL_ACCESS_TOKEN` environment variable to be set.

## Available MCP Servers

The MCP ecosystem includes many pre-built servers:

- **@modelcontextprotocol/server-filesystem** - Local filesystem access
- **@modelcontextprotocol/server-github** - GitHub API integration
- **@modelcontextprotocol/server-postgres** - PostgreSQL database access
- **@modelcontextprotocol/server-sqlite** - SQLite database access
- **@modelcontextprotocol/server-google-drive** - Google Drive integration
- And many more community-built servers

Visit [MCP Servers Directory](https://github.com/modelcontextprotocol/servers) for a full list.

## Troubleshooting

*   **"Moderator is not configured" error:** Ensure `GEMINI_API_KEY` is set (required for command moderation if using Stdio servers with shell access).
*   **Connection failures:** Check server URL/command, network connectivity, and server logs.
*   **Tools not appearing:** Verify the MCP server is running and correctly implements the protocol. Check Chibi logs for registration errors.
*   **Permission errors (Stdio):** Ensure the command/script has execute permissions and required dependencies are installed.
*   **Server crashes:** Check that all required environment variables for the MCP server are set (e.g., API tokens, database credentials).

## Security Considerations

- **Stdio servers** run as local processes with the same permissions as the bot
- **SSE servers** communicate over HTTP/HTTPS - ensure secure connections
- Only connect to trusted MCP servers
- Review the tools exposed by each server before connecting
- MCP servers can access resources based on their configuration - be mindful of what you expose

## Further Reading

- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Building Custom MCP Servers](https://modelcontextprotocol.io/docs/building-servers)
