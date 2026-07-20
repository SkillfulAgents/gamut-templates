# Quote / Estimate Follow-up

> Never let a sent quote go cold — automatically follow up with silent prospects, flag expiring estimates, and track win rates by rep and product line.

## What it does

Track sent quotes/estimates/proposals, nudge prospects who have gone quiet, flag expiring quotes, and surface win-rate by rep/product.

The agent runs on a configurable daily cadence, pulling all open quotes from your CRM or quoting tool, identifying which prospects haven't responded within your threshold, and sending (or drafting) follow-up emails on the rep's behalf. It also watches expiration dates and fires Slack alerts before a quote lapses. Every outcome — won, lost, expired, followed up — is logged to a spreadsheet tracker so you always have a live view of pipeline health and close-rate trends.

## What you'll need

- **Accounts:** Quoting tool or CRM (e.g. HubSpot, Salesforce, Jobber, or ServiceTitan), Email (Gmail or Outlook), Spreadsheet/Tracker (Google Sheets or Excel/OneDrive), Slack
- **API keys:** Listed in `.env.example` (fill in during setup)
- **Other:** Access to the relevant tools with read/write permissions

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask:
   - Your name, role, and company name
   - Which systems/accounts to connect
   - Your preferences (notification channel, cadence, thresholds)
3. Once setup finishes, give the agent its first task.

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions and role definition.
- `.claude/skills/agent-onboarding/` — first-run setup interview.
- `.env.example` — required environment variables (filled in during onboarding).

## Notes

This template is generic — it works for any organization in the relevant segments. All company-specific context is added during onboarding, not baked in.

Relevant subsegments: HVAC, RSTR, LAND, CLEN, PNTG, SUBC, GCON, MKTG, WHSL, MFGR, RECR, AEC, LGST
