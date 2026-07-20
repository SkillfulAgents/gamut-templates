# Security Questionnaire Responder

> Draft complete, sourced responses to buyer security questionnaires in minutes — not days.

## What it does

When a buyer sends a security questionnaire or RFP security section, draft answers mapped to your answer library and latest SOC 2/policy docs, flag gaps the security team must fill, and return a ready-to-review response package.

The agent parses incoming questionnaires (spreadsheet, document, or pasted text), searches your answer library and compliance document repository for matching prior answers and policy language, and generates a complete draft response for each question with source citations. Questions that cannot be answered from existing materials are clearly flagged with a gap report, so the security team knows exactly what needs attention before the response goes out. The finished package is delivered to your configured Slack channel or email, ready for human review and sign-off.

## What you'll need

- **Accounts:** Google Drive, Confluence, or Notion (answer library and policy docs); Slack or Gmail (delivery and gap notifications)
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
