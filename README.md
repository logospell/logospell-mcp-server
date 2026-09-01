<p align="center"><img src="logo-400.png" width="140" alt="Logospell"></p>

# Logospell MCP Server

AI-agent image generation over MCP: cohesive image sets, transparent-background
sets, and single illustrations. PNG/WebP (optional transparency) or JPEG.

Logospell is a hosted MCP server. This repository carries the connection
docs; there is nothing to build or run locally.

## Connect

Endpoint: `https://mcp.logospell.com/mcp` (streamable HTTP, bearer API key).

Get a free API key at [logospell.com](https://logospell.com) — 3 free
credits to start, no card required.

```json
{
  "mcpServers": {
    "logospell": {
      "type": "http",
      "url": "https://mcp.logospell.com/mcp",
      "headers": { "Authorization": "Bearer ls_<your-key>" }
    }
  }
}
```

Agent-assisted setup: see [llms-install.md](llms-install.md).

Grok Build users: the plugin lives in [`grok/`](grok/).

## Tools

| Tool | What it does | Cost |
|---|---|---|
| `generate_image_set` | Cohesive SET of images on a solid-color background (icons, game assets, UI elements) from a style plus per-subject description list | 1 credit |
| `generate_transparent_image_set` | The same kind of set with TRANSPARENT backgrounds, drop-in ready | 1 credit |
| `generate_illustration` | A SINGLE composed picture (scene, hero image, banner, portrait) | 1 credit |
| `create_reference` | Upload slot for a style reference image; up to 3 define a set's style by example | free |
| `edit_image_set` | Re-cut a set you already have: size, canvas, margin, sizing, format, quality, background | free |
| `export_icons` | Export a set as icons for the web, iOS, Android and Flutter, every density each expects | free |
| `check_credits` | Remaining credits on your key | free |
| `list_recent_generations` | Re-fetch recent download URLs | free |

Docs: [logospell.com/docs](https://logospell.com/docs) ·
Registry: `com.logospell/logospell` on the
[official MCP registry](https://registry.modelcontextprotocol.io)
