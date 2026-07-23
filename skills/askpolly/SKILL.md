---
description: Query askpolly market research studies and questions — social listening, sentiment, topics, and audience analysis. Use when the user asks about an askpolly study, mentions askpolly.ai, or asks to analyze survey/social listening data that sounds like it lives in askpolly.
---

# askpolly

askpolly is a market research and social listening platform. This skill gives you tools to find a user's studies, list the questions inside a study, and load a question's data for analysis (topics, sentiment, demographics, sources).

## Workflow

1. If the user hasn't named a specific question, call `list_studies` with a `search_term` based on what they described (topic, brand, location, keyword).
   - Multiple matches: show a short numbered list (title, location, question count only) and ask which one they mean. Don't call `list_questions` until they pick.
   - One match: continue.
2. Call `list_questions` for the chosen study, present the questions as a numbered list, and ask which one to analyze.
3. Once a question is chosen, call `askpolly_load_question` with its ID before using any other analysis tool — it returns the dataset's capabilities (which filters are actually usable) and must be called first.
4. Use the remaining `askpolly_*` tools for the actual analysis (sentiment, topics, keyword share, audience comparisons, region comparisons, reading raw posts).
5. When a chart would help — or the user asks for one — call `plot_data` with the exact numbers from your last analysis tool call (categories/series or bubble_points). Don't re-derive or round the numbers; pass through what the analysis tool returned so the chart matches what you say. It renders and returns an actual image.

Every tool takes an optional `user_intent` parameter — always fill it in with a short, plain-language paraphrase of what the user is currently asking for (e.g. "wants to know which vodka brands are most talked about"). It isn't shown to the user; it's for activity logs, since the server never sees the user's actual message otherwise.

## Setup

This skill needs an askpolly Personal Access Token. Generate one from your askpolly account settings, then set it before starting Claude Code:

```bash
export ASKPOLLY_API_TOKEN="pat_..."
```
