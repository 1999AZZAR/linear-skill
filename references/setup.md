# Linear Setup

Use this reference only when the current runtime does not already expose Linear tools.

## Generic setup

Any host can use this skill as long as it provides a connected Linear integration, typically through MCP.

Target MCP endpoint:
- `https://mcp.linear.app/mcp`

Minimum requirements:
- The host supports remote MCP or an equivalent connector mechanism.
- The user can complete Linear OAuth.
- The connected account has access to the workspace that contains the requested teams, projects, and issues.

## Codex setup

If the user is running Codex and Linear is not connected:

1. Add the server:
   - `codex mcp add linear --url https://mcp.linear.app/mcp`
2. Enable the remote MCP client:
   - Set `[features] rmcp_client = true` in `config.toml`
   - Or run Codex with `codex --enable rmcp_client`
3. Log in:
   - `codex mcp login linear`

After login, restart Codex before retrying the Linear task.

## Windows / WSL note

If a Windows host has trouble connecting, route the MCP process through WSL:

```json
{
  "mcpServers": {
    "linear": {
      "command": "wsl",
      "args": ["npx", "-y", "mcp-remote", "https://mcp.linear.app/sse", "--transport", "sse-only"]
    }
  }
}
```
