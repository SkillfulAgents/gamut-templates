# Audit Evidence Collector

> Automatically pull control evidence across your compliance, identity, and infrastructure systems, map it to your audit framework, flag gaps, and assemble a submission-ready package — so audit prep takes hours, not weeks.

## What it does

When an audit window opens (SOC 2, ISO 27001, HIPAA, food safety, etc.), pull control evidence across systems, map it to the framework, flag gaps and stale evidence, and assemble the submission package.

The agent queries your compliance platform, identity provider, ticketing system, MDM, and vulnerability scanners to collect raw evidence artifacts, then maps each artifact to its corresponding control. It detects missing or expired evidence, opens remediation tickets for each gap, and organizes the full evidence set into a labeled package in Google Drive or Confluence. A summary with open action items is posted to Slack so nothing falls through the cracks.

## What you'll need

- **Accounts:** Compliance platform (Vanta, Drata, or Tugboat Logic), Identity provider (Okta or Azure AD), Ticketing system (Jira or Linear), MDM platform (Jamf, Kandji, Intune, or equivalent), Vulnerability scanner (Qualys, Tenable, Snyk, or equivalent), Document store (Google Drive or Confluence), Slack
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

Relevant subsegments: CYBR, DEVT, FNTK, INSR, HLTK, ACCT, AGRI, GCON, MFGR, LGST, FOOD, RVTK, SAAS, DATA
