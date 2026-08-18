# askpolly Claude Code Plugin

Query your [askpolly](https://app.askpolly.ai) market research studies — social listening, sentiment, topics, and audience analysis — directly from Claude Code.

## Install

```
/plugin marketplace add askpolly/askpolly-claude-plugin
/plugin install askpolly@askpolly
```

## Setup

Click **Connect** on the askpolly connector when prompted, and sign in to your askpolly account in the browser. That's it — no token to copy or manage.

<details>
<summary>Using a Personal Access Token instead</summary>

The endpoint also accepts a PAT if you'd rather not use the browser sign-in —
useful for CI or headless runs. Generate one under Settings → API Tokens, then
add it to your own MCP config:

```json
{ "mcpServers": { "tools": {
  "type": "http",
  "url": "https://app.askpolly.ai/api/mcp",
  "headers": { "Authorization": "Bearer pat_..." }
}}}
```

Note that a `headers` block suppresses OAuth discovery, so use one or the other, not both.
</details>

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
