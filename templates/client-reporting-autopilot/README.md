> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/marketing-content/client-reporting-autopilot)** — one-click deploy, no setup.

# Client Reporting Autopilot

> Pulls per-client KPIs from ad platforms, analytics tools, and project trackers, flags anomalies and wins, assembles a branded draft report for review, and notifies your team in Slack — so reporting week stops being a manual copy-paste marathon.

## What it does

Client Reporting Autopilot runs on your configured cadence (weekly, bi-weekly, or monthly), iterates through your full client roster, and for each client:

- Pulls KPIs from the data sources you've connected — ad platforms (Google Ads, Meta Ads, LinkedIn Ads, etc.), analytics tools (GA4, Mixpanel, etc.), and project or time-tracking systems
- Compares current-period results to your chosen baseline (prior period, 4-period trailing average, or client-agreed target)
- Flags anomalies and standout wins against your configured threshold
- Populates your report template with data, narrative highlights, and anomaly callouts
- Saves the draft to Google Drive or Notion
- Posts a draft-ready notification to Slack with links and a summary of what needs review

No report is ever sent directly to a client — every draft goes to your team for review first.

## What you'll need

- **Accounts:** At least one ad platform or analytics tool per client, a report template in Google Drive or Notion, and Slack
- **API keys:** None required — all accounts are connected via Gamut during onboarding
- **Other:** Your client list (up to 20 clients), the KPI sources for each client, and an existing report template you want the agent to populate

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Your name, firm name, and role
   - Your client roster — up to 20 clients with their KPI source(s) and account/property IDs
   - Report cadence (weekly / bi-weekly / monthly) and format (Google Slides / Notion / email)
   - Your report template location (Google Drive or Notion link)
   - Anomaly thresholds (default: flag any metric that moves more than 15% period-over-period)
   - Comparison baseline per client (prior period, trailing 4-average, or client target)
   - Draft storage destination
   - Slack channel for draft-ready notifications
3. Once setup finishes, give the agent its first task: `"Pull this week's KPIs for [client name] and draft a client report."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill — use this to add or remove clients, update thresholds, or reconnect a data source.

## What's inside

- `CLAUDE.md` — the agent's instructions and your configured context.
- `.claude/skills/agent-onboarding/` — first-run setup interview.
- `.claude/config.json` — machine-readable config written during onboarding (created on first run).

## Notes

- The agent never sends reports to clients — it drafts and notifies. Distribution is always a human step.
- If a data source is unavailable during a run, the agent flags the gap in the draft and in the Slack notification rather than silently skipping that metric.
- Default anomaly threshold is 15% change period-over-period — tune down for tighter monitoring, up for noisier accounts.
- Client data is kept strictly separate — the agent will never mix one client's numbers into another client's report.
- Supports up to 20 clients per instance. For larger rosters, run multiple instances segmented by team or client tier.

Relevant subsegments: MKTG, PRCM, MGMT, AEC, CSTK
