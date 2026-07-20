> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/productivity-internal-ops/document-chaser)** — one-click deploy, no setup.

# Document Chaser

> Tracks owed documents, sends personalized nudges in your voice, verifies received docs, and escalates unresponsive counterparties.

## What it does

Document Chaser runs every weekday morning, checks your tracker for documents that are still owed, and sends personalized follow-up emails to counterparties who haven't delivered — written in your voice, not a generic bot tone. When documents arrive, it verifies them against your rules and acknowledges receipt. Anyone who goes unresponsive past your nudge limit gets escalated automatically, and you get a daily digest so nothing falls through the cracks.

Works for accounting (client tax docs), insurance (submissions), healthcare (prior auth), financial services (KYC/AML), HR onboarding, vendor compliance (COIs, W-9s), and any other workflow where you're chasing people for paperwork.

## What you'll need

- **Accounts:**
  - Tracker: Airtable, Notion, Google Sheets, Salesforce, HubSpot, or similar
  - Document storage: Google Drive, Dropbox, SharePoint, Box, or similar
  - Email: Gmail or Outlook
  - Slack (for daily digest and escalation alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** 2–3 real nudge emails from your sent folder (these are what make the emails sound like you, not a bot)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - What kind of documents you're chasing and your role (accountant, HR coordinator, insurance broker, etc.)
   - Which tracker, document storage, email provider, and Slack channel to use
   - Your preferred nudge cadence (gentle / standard / aggressive)
   - Whether to verify received documents before marking them complete, and your verification rules
   - 2–3 actual nudge emails from your sent folder so the agent matches your voice exactly
3. Once setup finishes, give the agent its first task: *"Check my tracker and document storage but do NOT send any nudges and do NOT update any rows. Show me what you'd do today — which counterparties would get a nudge, which docs you'd verify, which you'd escalate."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` — first-run setup interview.

## Notes

- Nothing auto-sends until you've confirmed the first dry-run looks correct.
- Nudges are sent as individual emails from your connected email account — the agent does not send from a shared or Gamut-owned address.
- Slack is recommended but optional; if not connected, escalation alerts will surface in the digest only.
- Document verification (checking format and required fields) is optional — if disabled, the agent logs receipt and marks the doc Received without inspecting the content.
- The agent consolidates all outstanding docs per counterparty into a single nudge — no one gets bombarded with separate emails for each missing item.
- For healthcare and financial services workflows, set your voice samples accordingly; the agent will match the formality level you show it.

Relevant subsegments: ALL
