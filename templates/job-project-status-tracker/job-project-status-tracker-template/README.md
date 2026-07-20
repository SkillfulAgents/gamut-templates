# Job / Project Status Tracker

> Know what's broken before your customer does — a daily ops brief that flags every job behind schedule, unscheduled, missing parts or permits, or overdue for a customer update.

## What it does

Produce a daily ops brief identifying jobs or projects that are behind schedule, unscheduled, missing parts or permits, or overdue for a customer update.

Each morning the agent pulls all active jobs or projects from your scheduling or PM tool, applies your configured thresholds and rules, and posts a structured briefing to Slack (or a spreadsheet) that your ops lead can act on immediately. Items are grouped by flag type — behind schedule, unscheduled, missing requirements, overdue customer contact — and each entry includes the job name, owner, reason for the flag, and a suggested next action. The agent tracks status day over day so recurring problems surface as patterns, not surprises.

## What you'll need

- **Accounts:** Scheduling or PM/dispatch tool (ServiceTitan, Buildertrend, Procore, Asana, or Jira), Slack, and optionally Google Sheets or Excel for historical logging
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

Relevant subsegments: HVAC, RSTR, GCON, SUBC, AEC, MKTG, MFGR, MGMT, LAND, CLEN
