# Linger MCP configuration and examples

> **Canonical documentation:** [withlinger.com/docs/mcp/](https://withlinger.com/docs/mcp/) ([Markdown](https://withlinger.com/docs/mcp.md))

[Install Linger](https://withlinger.com/download) on an Apple Silicon Mac running macOS 14 or later, and open it once to initialize a library (7-day full trial starts without sign-in; optional email sign-in adds 23 extra days for 30 days total). The bundled `linger-service` starts locally over stdio.

## Configure a client

| Client | Read-only by default | Enable writes |
| --- | --- | --- |
| Codex | [codex-config.toml](codex-config.toml) | [codex-config-write.toml](codex-config-write.toml) |
| Claude Code | [claude-code-mcp.json](claude-code-mcp.json) | [claude-code-mcp-write.json](claude-code-mcp-write.json) |
| Claude Desktop | [claude-desktop-config.json](claude-desktop-config.json) | [claude-desktop-config-write.json](claude-desktop-config-write.json) |
| Cursor | [cursor-mcp.json](cursor-mcp.json) | [cursor-mcp-write.json](cursor-mcp-write.json) |

- **Codex.** Merge one `[mcp_servers.linger]` block into `~/.codex/config.toml`. The read-only CLI equivalent is `codex mcp add linger -- /Applications/Linger.app/Contents/MacOS/linger-service --mcp`. Inspect the registration with `codex mcp get linger --json`. [Codex MCP settings](https://developers.openai.com/codex/mcp).
- **Claude Code.** Run `claude mcp add --transport stdio linger -- /Applications/Linger.app/Contents/MacOS/linger-service --mcp`, or copy [claude-code-mcp.json](claude-code-mcp.json) into your project's `.mcp.json`.
- **Claude Desktop.** Merge one `mcpServers.linger` entry into the config opened under **Settings → Developer → Edit Config**. The default macOS path is `~/Library/Application Support/Claude/claude_desktop_config.json`. Quit and reopen Claude Desktop after saving. [Claude Desktop setup](https://modelcontextprotocol.io/docs/develop/connect-local-servers).
- **Cursor.** Add [cursor-mcp.json](cursor-mcp.json) to Cursor Settings → MCP or your project's `.cursor/mcp.json`.

Keep one `linger` entry, preserve any other servers, and use the write variant only when you want the client to append machine analysis, save vocabulary suggestions, or process queued jobs. If Linger is installed elsewhere or uses custom data paths, copy the configuration in Linger's **Settings → Recall & AI → Model connection → External MCP** and use its path and environment values. In Codex, place environment values under `[mcp_servers.linger.env]`. In Claude Desktop, place them in the `env` object inside `mcpServers.linger`. Remove `--allow-write` from the copied args for read-only use.

## Read-only check

Verify service launch and tool discovery without asking a model to access your library. With Linger installed under `/Applications`, run:

```sh
/Applications/Linger.app/Contents/MacOS/linger-service --mcp <<'EOF_RPC'
{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-11-25","capabilities":{},"clientInfo":{"name":"linger-docs-check","version":"1"}}}
{"jsonrpc":"2.0","method":"notifications/initialized"}
{"jsonrpc":"2.0","id":2,"method":"tools/list"}
EOF_RPC
```

Expect a server named `linger` and 10 tools, including `get_library_summary` and `list_boards`. `save_analysis` and the four other write tools should be absent. In your configured client, ask it to call only `get_library_summary` with `{}` and report the counts. This checks access to the initialized library without reading individual notes or previews.

## Tool schemas and requests

- [tools.json](tools.json) records the 15 tool definitions returned by Linger 0.8.1 with `--allow-write`. The 10 read-only definitions have `annotations.readOnlyHint: true`. Query your installed build's `tools/list` for its current schemas.
- [read-reference.json](read-reference.json) holds three separate requests. Send them individually after initialization. Substitute an ID returned by `list_inspirations` before running either reference lookup. The query matches stored text.
- [save-analysis.json](save-analysis.json) shows a synthetic direct write. Use the actual reference ID, the current expected revision (`0` when no analysis exists), and accurate producer attribution. Inspect the reference before writing its analysis.

Use a disposable test library for write experiments. The service accepts `LINGER_APP_DATA_DIR` and `LINGER_LIBRARY_ROOT` for isolated data paths. See the [canonical MCP documentation](https://withlinger.com/docs/mcp/) and [GitHub MCP guide](../../docs/mcp.md) for the tools and data boundaries.
