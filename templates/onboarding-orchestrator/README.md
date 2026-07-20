> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/onboarding-orchestrator)** — one-click deploy, no setup.

# Onboarding Orchestrator

> Runs a new-X checklist to completion across systems: new hire, new account, new member, or new unit/site.

## What it does

Onboarding Orchestrator runs a new-X checklist to completion — executing each step across the systems you specify, notifying stakeholders for human-required steps, logging progress, and closing the loop when the new subject is fully ready. One agent, four use cases: new hire (HR and IT), new financial account (KYC/AML, custodian, CRM), new membership (portal, dues, benefits), or new franchise unit (licensing, systems, staffing). The agent never skips a step — it marks blockers, notifies the right person, and continues with independent steps rather than stalling the whole checklist.

## What you'll need

- **Accounts:** Intake system (ATS, CRM, HRIS, or tracker where new subjects appear), systems involved in onboarding steps (HRIS, Okta/provisioning, CRM, KYC/custodian, etc.), progress tracker (Google Sheets, Airtable, or Notion), Slack
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** A written onboarding checklist (the agent needs a checklist to execute from)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - Which onboarding type you're configuring (new hire, account, member, or unit)
   - Your existing onboarding checklist (or where to find it)
   - Which systems to connect
   - Where to log progress and notify stakeholders
   - How the agent learns about new subjects to onboard
3. Once setup finishes, give the agent its first task: `"Onboard [name] as a [type] — start date [date]."`

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions.
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Irreversible actions (account creation, document submission) require explicit confirmation from the designated owner before the agent proceeds, unless the checklist marks them as auto-approved.
- The agent requires a written checklist — it will not improvise one. Use onboarding to point it to yours.
- Access provisioning is logged with timestamps and the agent as the actor for audit purposes.

Relevant subsegments: ALL
