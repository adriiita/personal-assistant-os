---
name: fireflies
description: Sync meeting transcripts from Fireflies.ai via MCP server or manual export. Optional integration — requires Fireflies Business plan ($19/mo) for API access.
---

# Fireflies.ai Integration

USE WHEN the user mentions Fireflies, asks to sync meetings, or wants to pull transcripts from Fireflies.

## Two Approaches

### Approach 1: Manual Export (Free Plan)

If the user doesn't have API access:

1. Tell them to export the transcript from Fireflies web dashboard:
   - Log into app.fireflies.ai
   - Open the meeting transcript
   - Click Download → choose JSON or DOCX format
2. Have them paste the content or drop the file into `03_meetings/`
3. Process using the meetings skill

### Approach 2: MCP Server (Business Plan — $19/mo)

If the Fireflies MCP server is configured:

#### Check if Available
The MCP server should be configured in `.claude/settings.json` under the `mcpServers` key. If available, you can use these tools:

#### Available MCP Tools
- `fireflies_list_transcripts` — List all transcripts
- `fireflies_get_transcript` — Get full transcript by ID
- `fireflies_search` — Search across all transcripts by keyword

#### Sync Workflow

1. List recent transcripts:
   ```
   Use fireflies_list_transcripts to get recent meetings
   ```

2. For each unsynced transcript:
   - Check if a file already exists in `03_meetings/` with the same date and title
   - If not, fetch the full transcript
   - Process using the meetings skill
   - Save to the appropriate `03_meetings/` subfolder

3. After sync, report:
   - How many meetings were synced
   - Any new action items found
   - Offer to create Kanban tasks

#### MCP Configuration (for setup)

To enable Fireflies MCP, add to `.claude/settings.json`:

```json
{
  "mcpServers": {
    "fireflies": {
      "command": "npx",
      "args": ["-y", "fireflies-mcp-server"],
      "env": {
        "FIREFLIES_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

Get your API key from: https://app.fireflies.ai/integrations/custom/fireflies

## Alternative: Fireflies Claude Connector

If the user has Claude Pro/Max and Fireflies Business:
- They can connect Fireflies directly in Claude Settings → Connectors
- This gives Claude direct access to meeting data without MCP setup
- Useful for Co-Work users who can't run MCP servers locally

## Free Plan Limitations

- No API access
- No webhooks
- Manual export only (DOCX, PDF, SRT, VTT, JSON)
- 800 minutes storage limit
- Markdown is NOT a native export format — conversion needed
