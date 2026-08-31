# Delphi MCP installation

The required server is [`tina4stack/pascal-mcp`](https://github.com/tina4stack/pascal-mcp), exposed to the agent as `pascal-mcp`.

## Prerequisites

- Windows with RAD Studio/Delphi for Delphi builds
- Python 3.11 or newer
- [`uv`](https://docs.astral.sh/uv/)

## Codex

Add this to the user Codex configuration and restart Codex:

```toml
[mcp_servers.pascal-mcp]
command = "uvx"
args = ["--from", "git+https://github.com/tina4stack/pascal-mcp", "pascal-mcp"]
```

For a local development clone:

```toml
[mcp_servers.pascal-mcp]
command = "uv"
args = ["run", "--directory", "C:/path/to/pascal-mcp", "pascal-mcp"]
```

## Claude Code

```bash
claude mcp add --transport stdio pascal-mcp -- uvx --from git+https://github.com/tina4stack/pascal-mcp pascal-mcp
```

## Cursor

Add this to `~/.cursor/mcp.json`, or to `.cursor/mcp.json` inside a project:

```json
{
  "mcpServers": {
    "pascal-mcp": {
      "type": "stdio",
      "command": "uvx",
      "args": ["--from", "git+https://github.com/tina4stack/pascal-mcp", "pascal-mcp"]
    }
  }
}
```

## Claude Desktop or project `.mcp.json`

```json
{
  "mcpServers": {
    "pascal-mcp": {
      "command": "uvx",
      "args": ["--from", "git+https://github.com/tina4stack/pascal-mcp", "pascal-mcp"]
    }
  }
}
```

Restart the host after registration, then call `mcp__pascal_mcp__get_compiler_info`. Do not begin Delphi edits until the server responds and the required compiler is listed.
