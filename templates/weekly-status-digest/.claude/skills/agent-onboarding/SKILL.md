---
name: agent-onboarding
description: 'First-run setup for Weekly Status Digest. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding — Weekly Status Digest

You are running the first-time setup for the Weekly Status Digest agent. Be conversational. Most questions have sensible defaults.

## Step 1: Welcome

> "Welcome to Weekly Status Digest. Every Monday at 8 AM, I pull your key metrics, compare them to a baseline, write a narrative of what changed and why, close out last week's flags, and post one digest wherever you want it.
>
> This works for any function: recruiting, marketing, sales, ops, engineering, CS. I just need to know which numbers matter and where to find them.
>
> I'll ask a few questions — about 15 minutes."

## Step 2: Interview

**Q1 — About you**
"What's your name and function? (e.g. 'Head of Recruiting', 'VP Marketing', 'Director of CS')"

**Q2 — Domain and metrics**
"What function is this digest for, and what are the 4–8 metrics that matter most? For each, tell me: the metric name, where to find it (system + query), and your preferred baseline (last week / 4-week average / plan / same week last quarter)."

(Give examples: "Applications submitted — Greenhouse — compare to 4-week avg", "MQLs — HubSpot — compare to plan")

**Q3 — Data sources to connect**
"Which systems should I connect to pull your metrics? (e.g. Salesforce, HubSpot, Greenhouse, Google Sheets, Looker, Snowflake, other)"

**Q4 — Where to save and post**
"Where should I archive each week's digest? (Google Drive folder, Notion page, or similar — this is what lets me close last week's flags.) And where should I post it? (Slack channel or DM)"

**Q5 — Audience and narrative style**
"Who reads this — just you, your team, or execs/board? And how do you want it to read: tactical detail with source links, or executive summary with just the highlights?"

**Q6 — Anomaly threshold**
"What % week-over-week change should I flag as an anomaly? (Default is 25% — lower for more sensitivity, higher for noisier metrics)"

## Step 3: Write answers to CLAUDE.md

Append this block to CLAUDE.md under `## Your context`:

```
## Your context

User: [name], [function]
Domain: [domain]
Metrics: [list with source + baseline per metric]
Data sources: [list of connected systems]
Baseline: [trailing_4wk | last_week | plan | same_week_last_quarter]
Anomaly threshold: [N]%
Audience: [ic | exec | board]
Narrative style: [their description]
Storage target: [Drive | Notion | other]
Storage location: [specific path/folder/page]
Output channel: [Slack channel or DM]
Timezone: [timezone]
```

## Step 4: Connect accounts

Walk the user through connecting each system they named:
1. Data sources (e.g. Salesforce, HubSpot, Greenhouse, Sheets)
2. Storage (Drive, Notion, or other)
3. Slack

Confirm each connection succeeds before proceeding.

## Step 5: Done

> "You're set. Next Monday at 8 AM I'll run the first digest and post it to [output_channel].
>
> To see a preview before Monday, ask me: 'Pull this week's metrics for [domain] — just the raw numbers, no narrative, don't post anything.' That confirms I'm reading from the right places."

Tell them they can re-run onboarding anytime to change metrics, sources, or settings.
