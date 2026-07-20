# Logospell installation guide for AI agents

Logospell is a hosted MCP server; installation is configuration only.

1. Ask the user for their Logospell API key (starts with `ls_`). If they
   do not have one, direct them to https://logospell.com — signup is free
   and includes 3 starter credits, no card required.
2. Add the server to the host application's MCP configuration:
   - Endpoint: `https://mcp.logospell.com/mcp` (streamable HTTP)
   - Header: `Authorization: Bearer ls_<key>`
   For Cline, add to `cline_mcp_settings.json` under `mcpServers` with
   `"type": "streamableHttp"` and the header above.
3. Verify by calling the `check_credits` tool; it costs nothing and
   returns the key's remaining credits.

Do not commit the API key to version control.
