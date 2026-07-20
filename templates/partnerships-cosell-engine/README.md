> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/partnerships-cosell-engine)** — one-click deploy, no setup.

# Partnerships Co-Sell Engine

> Find warm co-sell paths through partner overlap, keep joint pipeline moving, and automate partner-facing updates — all without manual coordination.

## What it does

Surface partner–account overlap to find warm co-sell paths, track deal registrations and joint pipeline, and automate partner-facing updates.

The agent connects your CRM and partner overlap tools (Crossbeam, Reveal, or a shared spreadsheet) to identify which open opportunities have a partner relationship that can warm an introduction. It monitors deal registrations for stale or expiring entries, delivers joint pipeline summaries on a cadence you choose, and drafts status updates to partner contacts whenever a co-sell deal advances or closes — reducing manual coordination between your partnerships and sales teams.

## What you'll need

- **Accounts:** CRM (HubSpot or Salesforce), partner overlap tool (Crossbeam, Reveal, or an exported spreadsheet), Slack
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
