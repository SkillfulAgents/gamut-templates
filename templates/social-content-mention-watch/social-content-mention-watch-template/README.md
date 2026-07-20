# Social Content & Mention Watch

> Never miss a brand mention again — monitor social conversations, respond with on-brand content, and get a weekly digest of what moved the needle.

## What it does

Monitor brand and competitor social mentions, draft on-brand posts and responses, and deliver a weekly digest of what moved the needle.

The agent continuously tracks keywords, competitor handles, and campaign hashtags across Twitter/X, LinkedIn, Instagram, and Facebook — triaging by sentiment, reach, and urgency. Drafted posts and responses are saved to Google Drive or Notion for team review, and a Slack digest lands every week with engagement trends, competitor activity, and recommended focus areas.

## What you'll need

- **Accounts:** Twitter/X (API or browser), LinkedIn, Instagram, Facebook — for the brand and any competitors to monitor; Google Drive or Notion for content drafts; Slack for digests and alerts
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

Relevant subsegments: CPG, DTC, MKTG, PRCM, FOOD, FITN, HOSP, RETL
