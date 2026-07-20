> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/access-jml-provisioning)** — one-click deploy, no setup.

# Access / JML Provisioning

> Automate joiner, mover, and leaver access workflows across your IdP, HRIS, MDM, and ticketing systems — eliminating manual provisioning errors and ensuring clean, auditable offboarding.

## What it does

For every joiner, mover, or leaver event, trigger the right access provisioning or deprovisioning steps across identity, HR, and MDM systems, and run periodic access-review campaigns.

The agent listens for lifecycle events from your HRIS, then orchestrates account creation or deactivation in your IdP, device enrollment or wipe in your MDM, and ticket creation in your IT service desk. For movers, it adjusts group memberships and application access to match the new role. On a configurable cadence, it also runs access-review campaigns — sending managers certification prompts via Slack and flagging or revoking uncertified access after the review window closes.

## What you'll need

- **Accounts:** IdP (Okta, Azure AD, or Google Workspace), HRIS (Rippling, BambooHR, or Workday), MDM (Jamf or Intune), ticketing (Jira or ServiceNow), Slack
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
