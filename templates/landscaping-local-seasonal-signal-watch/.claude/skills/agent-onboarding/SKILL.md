---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Landscaping/Lawn - Local / Seasonal Signal Watch agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business and service territory, then you will be ready to start surfacing timely outreach opportunities.

Ask the following questions. You may present them all together in a single message:

1. **Business name and service territory** — What is the name of your landscaping or lawn care business, and which zip codes or county/counties make up your primary service territory? (List all zip codes or name the county — this is used to scope permit filings, weather events, and new-mover data)
2. **Job management system** — Do you use Jobber, Aspire, or something else to manage clients and jobs? If Jobber or Aspire, confirm your account is connected so the agent can look up existing clients and create leads. If neither, describe how you track prospects and customers.
3. **Signal priorities** — Which signal types matter most to your business? Rank or select the ones you want monitored: storm/weather events, new-mover lists, permit filings (residential new construction, commercial development, landscaping permits), HOA/property-management bid seasons, or calendar-based seasonal triggers (spring cleanup, fall cleanup, irrigation winterization, aeration/overseeding). Include any you want to skip.
4. **Seasonal trigger dates** — What are the key seasonal windows for your region? For example: spring cleanup window (April 1–May 15), irrigation startup (April 15–May 31), aeration/overseeding (Sept 1–Oct 15), fall cleanup (Oct 1–Nov 15), irrigation winterization (Oct 15–Nov 30). Adjust dates to match your actual climate and service calendar.
5. **Owner name and outreach voice** — What name should talking-point openers be written in? (e.g., "Mike" or "Mike Torres" — this is the voice used for outreach context and Jobber/Aspire task notes)
6. **Digest and alert delivery** — Where should the daily prospect list and weekly Monday digest be delivered? (email address, Slack channel, or both — provide the exact address or channel name)
7. **Auto-push to Jobber/Aspire** — Should the agent automatically create lead records and follow-up tasks in Jobber or Aspire for top-priority prospects, or do you want to review and approve each batch before records are created? (auto / review-first)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "serviceTerritory": {
    "zipCodes": ["<zip1>", "<zip2>"],
    "counties": ["<county name>"]
  },
  "jobManagementSystem": "<Jobber | Aspire | other>",
  "signalPriorities": {
    "stormWeatherEvents": true,
    "newMoverLists": true,
    "permitFilings": true,
    "hoaBidSeasons": false,
    "seasonalTriggers": true
  },
  "seasonalWindows": [
    { "name": "Spring Cleanup", "start": "04-01", "end": "05-15" },
    { "name": "Irrigation Startup", "start": "04-15", "end": "05-31" },
    { "name": "Aeration/Overseeding", "start": "09-01", "end": "10-15" },
    { "name": "Fall Cleanup", "start": "10-01", "end": "11-15" },
    { "name": "Irrigation Winterization", "start": "10-15", "end": "11-30" }
  ],
  "ownerName": "<name for outreach voice>",
  "digestDelivery": {
    "email": "<email address or null>",
    "slack": "<channel name or null>"
  },
  "autoPushToJobManagement": false
}
```

Update `signalPriorities` to reflect only the signals the owner wants active. Update `seasonalWindows` with the actual dates provided.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Service territory:** [zip codes and/or county names]
**Job management system:** [Jobber | Aspire | other]
**Active signals:** [list of enabled signal types]
**Seasonal windows:** [list with date ranges]
**Owner name for outreach voice:** [name]
**Digest delivery:** [email and/or Slack channel]
**Auto-push to job management:** [enabled / disabled — review-first]
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Pull all signals from the past 7 days, score the prospects, and show me the top 10 with talking points."
