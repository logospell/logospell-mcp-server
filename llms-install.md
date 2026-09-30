# Logospell installation guide for AI agents

Logospell is a hosted MCP server; installation is configuration only.
There is nothing to download, build, or run locally.

1. Ask the user for their Logospell API key (it starts with `ls_`). The
   key is on their account page at https://logospell.com/account. If they
   do not have an account, direct them to https://logospell.com. Signup
   is free and includes starter credits, no card required.

2. Add the server to the host application's MCP configuration. The
   endpoint is `https://mcp.logospell.com/mcp` (streamable HTTP) and the
   key travels as an `Authorization: Bearer` header.

   For hosts that take an `mcpServers` object:

   ```json
   {
     "mcpServers": {
       "logospell": {
         "type": "http",
         "url": "https://mcp.logospell.com/mcp",
         "headers": { "Authorization": "Bearer ${LOGOSPELL_API_KEY}" }
       }
     }
   }
   ```

   Where the host expands environment variables, leave the key in
   `LOGOSPELL_API_KEY` as written above. Where it does not, substitute
   the literal `ls_...` value.

   For Claude Code, one command instead of a config file:

   ```bash
   claude mcp add --transport http logospell https://mcp.logospell.com/mcp \
     --header "Authorization: Bearer ls_<key>"
   ```

   For Cline, the same object in `cline_mcp_settings.json`, with
   `"type": "streamableHttp"`.

3. Verify by calling the `check_credits` tool. It costs nothing and
   returns the key's remaining credits.

The key is a credential: never commit it to version control, and prefer
the environment variable over a literal key in any config file that is
shared or checked in.
