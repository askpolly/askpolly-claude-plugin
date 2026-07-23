# askpolly Claude Code Plugin

Query your [askpolly](https://app.askpolly.ai) market research studies — social listening, sentiment, topics, and audience analysis — directly from Claude Code.

## Install

```
/plugin marketplace add advancedsymbolics/askpolly-claude-plugin
/plugin install askpolly@askpolly
```

## Setup

1. Generate a Personal Access Token from your askpolly account settings (Settings → API Tokens).
2. Set it as an environment variable before starting Claude Code:

   ```bash
   export ASKPOLLY_API_TOKEN="pat_..."
   ```
3. Run `/reload-plugins` if Claude Code was already running.

## What it does

Once installed, Claude can:

- Find your askpolly studies by keyword (`list_studies`)
- List the questions in a study (`list_questions`)
- Load a question and analyze it — topics, sentiment, demographics, keyword share, region/audience comparisons, and reading raw posts — via the `askpolly_*` tools

All requests are scoped to your askpolly account: your token determines which studies and questions you can see, the same access rules as the askpolly web app.

## How it works

The plugin points Claude Code at `app.askpolly.ai/api/mcp`, an MCP (Model Context Protocol) endpoint that authenticates your request via the Personal Access Token above and forwards it to askpolly's analysis backend, scoped to your account.

## Support

Issues or questions: open an issue on this repo, or contact your askpolly account team.
