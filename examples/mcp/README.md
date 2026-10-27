# Synthetic MCP requests

These files illustrate the request shapes described in the [MCP guide](../../docs/mcp.md). They were checked against the implementation's tool definitions on October 28, 2026; they are not a live session transcript or a complete client.

- [`read-reference.json`](read-reference.json) contains three separate JSON-RPC messages, stored in an array for readability. Send each message individually through an initialized MCP client, not as a batch or an HTTP request.
- [`save-analysis.json`](save-analysis.json) shows a direct write after an item has been inspected. It requires writes to be enabled and current access to the library.

All IDs and analysis text are fictional. In a real session, replace `asset_id: 1` with an ID returned by the list call; use the latest analysis revision rather than copying `expected_revision: 0`. Zero applies only to an item with no existing analysis. Replace the example producer with accurate attribution to the client or model that performed the analysis.

The sample query `warm light` demonstrates stored-text search. It is not a semantic image search request. The write describes an imaginary image and must not be saved against a real reference without inspection.

The requests contain no credentials, file paths, private records, or server outputs. You may copy and adapt these synthetic request examples for integrations.
