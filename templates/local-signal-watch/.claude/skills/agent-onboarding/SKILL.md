---
name: agent-onboarding
description: Onboards a new user to the Local Signal Watch agent by collecting their business context, signal preferences, geography, tracking setup, and Slack channel, then writes the answers to CLAUDE.md and config.json.
---

# Agent Onboarding

Welcome the user and explain what this skill does: configure the Local Signal Watch agent for their specific business so it starts surfacing the right warm prospects right away.

## Interview flow

Work through the questions below conversationally — ask one topic at a time, confirm the answer, then move on. Do not dump all questions at once.

### 1. Basic business context

Ask:
- Their name and company name.
- The service or trade they provide (e.g., storm restoration, roofing, HVAC, landscaping, pest control, general contracting, real estate — or anything else).

This sets the relevance logic for signal filtering: a roofing company cares about hail events and roofing permits; an HVAC company cares about new construction and seasonal temperature swings; a landscaping company cares about new movers and spring/fall triggers.

### 2. Signal types to watch

Ask which of the following signal types they want to monitor (they can pick any combination):

- **Storms / severe weather events** — hail, high winds, flooding, freeze events in their area.
- **New building permits** — permits filed for relevant project types. Ask which permit categories matter to them (roofing, HVAC/mechanical, landscaping/grading, pest/termite, general construction, new residential construction, or other).
- **New movers / new residents** — households that have recently moved into the area (typically available as weekly lists from data providers or uploaded CSVs).
- **Seasonal calendar triggers** — fixed dates or windows that signal demand spikes (e.g., spring lawn care season, pre-summer HVAC tune-up window, pre-winter weatherization, holiday lighting install window).

Confirm the final combination before moving on.

### 3. Geographic coverage

Ask which areas to monitor. They can specify:
- A list of zip codes.
- One or more counties.
- A metro area name.

If they mention a city, clarify whether they mean just the city limits or the broader metro. Record the answer in a format that can be passed to data sources (e.g., a comma-separated list of zip codes or county FIPS codes if known, otherwise a plain text description).

### 4. Prospect tracking setup

Ask:
- Where they log and track prospects — CRM name (e.g., HubSpot, Salesforce, ServiceTitan, Jobber, a simple spreadsheet), or a Slack channel used as a lightweight tracker.
- Whether the agent should mark leads as "surfaced" in that system after posting them, to prevent repeat appearances.
- How long the lookback window should be for deduplication — how many days back should the agent check before deciding a contact has already been actioned? (Suggest 30 days as a default.)

### 5. Digest schedule and Slack channel

Ask:
- Whether they want a **daily digest** (posted each morning on business days) or a **weekly digest** (posted on a chosen day, e.g., Monday morning).
- Which Slack channel to post the digest to. Then prompt them to connect their Slack account using the `/connect slack` command (or equivalent in their Gamut workspace).

### 6. Confirm and save

Summarize all collected answers and ask the user to confirm before writing.

Once confirmed:

1. Write all answers into the `## Your context` section of `CLAUDE.md`, replacing the placeholder comment. Use clear labeled fields, for example:

```
## Your context

- **Name:** [name]
- **Company:** [company]
- **Service / trade:** [service]
- **Signal types:** [list]
- **Permit categories:** [list, if permits selected]
- **Seasonal trigger windows:** [list, if seasonal selected]
- **Geography:** [zip codes / counties / metro]
- **Prospect tracker:** [CRM or spreadsheet name]
- **Mark leads as surfaced:** [yes/no]
- **Deduplication lookback:** [N days]
- **Digest schedule:** [daily / weekly on [day]]
- **Slack digest channel:** [#channel-name]
```

2. Write a `config.json` file in the workspace root with the same data in structured form:

```json
{
  "user": {
    "name": "",
    "company": "",
    "service": ""
  },
  "signals": {
    "storms": false,
    "permits": false,
    "permitCategories": [],
    "newMovers": false,
    "seasonal": false,
    "seasonalWindows": []
  },
  "geography": {
    "zipCodes": [],
    "counties": [],
    "metro": ""
  },
  "tracking": {
    "crmOrSpreadsheet": "",
    "markLeadsAsSurfaced": true,
    "deduplicationLookbackDays": 30
  },
  "digest": {
    "schedule": "daily",
    "weeklyDay": "",
    "slackChannel": ""
  }
}
```

Fill in all values from the interview. Boolean signal flags should be `true` for selected types and `false` for unselected.

3. Confirm to the user that onboarding is complete and suggest the first thing to try: "Pull today's storm and permit signals for [their metro] and give me a list of addresses to call."
