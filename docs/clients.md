# Connecting your client

Server URL: `https://www.apptrendkit.com/mcp` · Transport: Streamable HTTP · Authentication: none.

## ChatGPT

1. Settings → Apps → Advanced settings → turn on **Developer mode**.
2. **Create app**: name `AppTrendKit`, MCP server URL above, authentication **No authentication**.
3. In a new chat, add AppTrendKit from the **+** menu and ask about an app, chart or keyword.

If an answer shows "couldn't be opened" instead of the results view after an update, open the app in Settings and choose **Refresh** so ChatGPT reloads the tool list.

## Claude (claude.ai, Claude Desktop, Claude mobile)

1. Settings → Connectors → **Add custom connector**.
2. Name `AppTrendKit`, URL above.
3. Turn it on in a chat from the tools menu.

## Claude Code

```bash
claude mcp add --transport http apptrendkit https://www.apptrendkit.com/mcp
```

## Cursor

Settings → MCP → **Add new MCP server**, or add [`examples/cursor-mcp.json`](../examples/cursor-mcp.json) to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project).

## VS Code (GitHub Copilot agent mode)

Command Palette → **MCP: Add Server** → HTTP → the URL, or add [`examples/vscode-mcp.json`](../examples/vscode-mcp.json) as `.vscode/mcp.json`.

## Gemini CLI

Add [`examples/gemini-cli-settings.json`](../examples/gemini-cli-settings.json) to `~/.gemini/settings.json`.

## OpenAI Codex CLI

Add [`examples/codex-config.toml`](../examples/codex-config.toml) to `~/.codex/config.toml`.

## Windsurf, Cline, Zed and others

Add a remote MCP server of type Streamable HTTP (sometimes called "HTTP" or `serverUrl`) with the URL above.

## Clients that only run local (stdio) servers

Use [`mcp-remote`](https://www.npmjs.com/package/mcp-remote) as a bridge, as in [`examples/claude-desktop-mcp-remote.json`](../examples/claude-desktop-mcp-remote.json). Needs Node.js 18+.
