# Incident Post-Mortem & On-Call Pack

> Turns a closed incident into a complete documentation package — timeline, post-mortem, on-call handoff, and customer status update — in minutes, not hours.

## What it does

When an incident closes, compile the timeline, draft the post-mortem document and action items, write the on-call handoff brief, and draft the customer-facing status update.

The agent pulls alert history and escalation data from your on-call tool, correlates it with linked project tracker tickets, and produces a structured post-mortem with root cause analysis and prioritized action items. It also writes a concise handoff brief for the incoming on-call rotation and a polished, jargon-free customer-facing status update ready to publish to your status page — all without requiring responders to write from scratch after an exhausting incident.

## What you'll need

- **Accounts:** PagerDuty or OpsGenie (on-call / alerting), Jira or Linear (project tracker), Statuspage.io (status page), Slack
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

Relevant subsegments: RVTK, MTTK, CSTK, CYBR, DEVT, DATA, AICO, FNTK, INSR, HRTK, LGTK, PPTK, SCTK, ECTK, SAAS, EDTK, CLTK, HLTK
