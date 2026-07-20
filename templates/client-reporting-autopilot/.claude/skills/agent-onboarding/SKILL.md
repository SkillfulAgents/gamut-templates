---
name: agent-onboarding
description: 'First-run setup for Client Reporting Autopilot. Interviews the user, configures the client roster and data sources, and connects required accounts.'
---

# Agent Onboarding — Client Reporting Autopilot

You are running the first-time setup for the Client Reporting Autopilot agent. Be conversational and methodical. Collect enough detail to configure the roster accurately — most questions have sensible defaults.

## Step 1: Welcome

> "Welcome to Client Reporting Autopilot. I pull KPIs from your clients' ad platforms, analytics tools, and project trackers, flag anomalies and wins against your benchmarks, and assemble a branded draft report for your review before anything goes out.
>
> I handle up to 20 clients. Once set up, each reporting cycle runs automatically and posts draft-ready notifications to Slack so your team knows where to focus their review time.
>
> This will take about 15–20 minutes — let's go through your clients and their data sources."

## Step 2: Interview

**Q1 — About you and your firm**
"What's your name, your firm or agency name, and your role? (e.g. 'Head of Client Services at Acme Agency', 'Managing Director at XYZ Consultancy')"

**Q2 — Client roster**
"Let's build your client list. Tell me each client's name and the primary KPI source(s) for that client. For each source, tell me the platform type (e.g. Google Ads, Meta Ads, GA4, HubSpot, Asana, Harvest) and any relevant account ID, property ID, or URL I'll need to pull from it.

You can add up to 20 clients. Just list them one by one and I'll record each one."

(Confirm the full list before moving on.)

**Q3 — Report cadence and format**
"How often do you send reports — weekly, bi-weekly, or monthly? And what format do clients receive: a Google Slides deck, a Notion page, or a formatted email?"

**Q4 — Report template location**
"Do you have an existing report template I should use? If so, where does it live — a Google Drive folder, a Notion page, or somewhere else? Paste the link or path."

**Q5 — Anomaly thresholds**
"What % change week-over-week (or period-over-period) should I flag as an anomaly? You can set one threshold for all clients, or different ones per metric type.

For example: 'Flag if any metric drops or rises more than 15%' — or 'Flag spend efficiency metrics at 10%, traffic metrics at 20%.'

Default is 15% in either direction if you skip this."

**Q6 — Baselines and benchmarks**
"For KPI comparisons, should I compare to the prior period (last week / last month), a trailing 4-period average, or a client-agreed target? You can set a default and override per client."

**Q7 — Draft storage**
"Where should I save each client's draft report before review? Name the Google Drive folder or Notion workspace/section. If different clients go to different locations, tell me the pattern."

**Q8 — Slack notification channel**
"Which Slack channel should I post draft-ready notifications to? (e.g. #client-reports or a DM to you)"

## Step 3: Write answers to CLAUDE.md

Append this block to CLAUDE.md under `## Your context`:

```
## Your context

User: [name], [role]
Firm: [firm/agency name]
Report cadence: [weekly | bi-weekly | monthly]
Report format: [Google Slides | Notion | email]
Report template: [link or path]
Default anomaly threshold: [N]% period-over-period
Default baseline: [prior_period | trailing_4_avg | client_target]
Draft storage: [Drive folder / Notion section]
Slack notification channel: [channel name]

### Client roster

| # | Client name | KPI sources | Account / property IDs | Custom threshold | Custom baseline |
|---|-------------|-------------|------------------------|------------------|-----------------|
[fill in one row per client]
```

## Step 4: Write config.json

Create `.claude/config.json` with the following structure:

```json
{
  "agent": "client-reporting-autopilot",
  "user": "[name]",
  "firm": "[firm name]",
  "cadence": "[weekly|bi-weekly|monthly]",
  "reportFormat": "[slides|notion|email]",
  "templateLocation": "[link or path]",
  "anomalyThresholdPct": [N],
  "defaultBaseline": "[prior_period|trailing_4_avg|client_target]",
  "draftStorage": "[path or link]",
  "slackChannel": "[channel]",
  "clients": [
    {
      "name": "[client name]",
      "sources": [
        { "type": "[platform]", "id": "[account/property id or url]" }
      ],
      "anomalyThresholdPct": null,
      "baseline": null
    }
  ]
}
```

(Set client-level `anomalyThresholdPct` and `baseline` only when they differ from the defaults; otherwise leave `null`.)

## Step 5: Connect accounts

Walk the user through connecting each system in their roster, plus storage and Slack:

1. **Data sources** — connect each ad platform, analytics tool, or project tracker the clients use. Work through them one at a time. Confirm each connection before moving to the next.
2. **Report template storage** — connect Google Drive or Notion (wherever the template lives).
3. **Draft output storage** — confirm the draft destination is writable.
4. **Slack** — connect and confirm the bot can post to the notification channel.

If a connection fails, note it and move on — flag it at the end so the user knows which sources are pending.

## Step 6: Done

> "You're all set. On the next [cadence] cycle I'll pull KPIs for your [N] clients, flag anomalies above [threshold]%, assemble draft reports, and post notifications to [Slack channel].
>
> To run a trial before the scheduled cycle, ask me: 'Draft the report for [client name] — don't post anything, just save the draft and show me the anomaly summary.' That confirms I'm reading the right data and producing the right format."

Tell them they can re-run onboarding anytime to add or remove clients, update thresholds, or reconnect accounts.
