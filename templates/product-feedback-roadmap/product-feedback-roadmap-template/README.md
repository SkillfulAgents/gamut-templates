# Product Feedback-to-Roadmap

> Turn scattered customer feedback into prioritized roadmap inputs — automatically clustered, revenue-weighted, and drafted into PRD-ready insight packs.

## What it does

Pull feedback from multiple channels, categorize and cluster it into themes, draft insight packs and PRD stubs for the top requests, and mine CRM signals to tie features to revenue impact.

The agent ingests tickets, deal notes, and Slack messages on a configurable cadence, merges duplicate signals across channels, and ranks themes by both frequency and ARR exposure so product teams know which requests matter most to the business. Each week it delivers a digest to Slack and generates structured deliverables — insight packs with representative quotes and a lightweight PRD stub per theme — that PMs can take directly into planning without manual synthesis.

## What you'll need

- **Accounts:** Helpdesk (Zendesk or Intercom), CRM (HubSpot or Salesforce), project tracker (Jira or Linear), Slack
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
