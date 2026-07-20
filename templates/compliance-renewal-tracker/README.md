> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/license-permit-renewals/compliance-renewal-tracker)** — one-click deploy, no setup.

# Compliance / Renewal Tracker

> Tracks expiring licenses, COIs, certifications, and registrations across a business or network, nudges the responsible owners on a lead-time schedule, flags lapses, and posts a status digest.

## What it does

Compliance / Renewal Tracker runs every weekday morning, reads your compliance tracker, and recomputes how many days are left before each license, certificate of insurance (COI), professional certification, or registration expires. As items cross your lead-time thresholds (for example 90 / 60 / 30 / 7 days), it emails the person responsible for that item, consolidating everything they own into a single nudge with exact expiry dates and a link to the document currently on file. Anything that lapses gets flagged and escalated the same day, and you get a status digest so nothing expires quietly.

It works for a single business or a whole network -- franchises and multi-unit operators tracking per-location licenses, trades carrying licenses and insurance, subcontractors and general contractors managing COIs, healthcare and logistics operators tracking certifications and registrations, and any organization that has to keep paperwork current across many owners and jurisdictions.

The agent never files, submits, or renews anything. It tracks status and nudges the right people. This is operational tracking, not legal or compliance advice.

## What you'll need

- **Accounts:**
  - Tracker: Airtable, Notion, Google Sheets, Smartsheet, or similar
  - Document storage: Google Drive, Dropbox, SharePoint, Box, or similar (where the actual certs and COIs live)
  - Email: Gmail or Outlook
  - Slack (for the status digest and escalation alerts)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your renewal lead-time tiers, who owns each item type, and 1-2 sample nudge emails so the tone sounds like you

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - The scope you're tracking (one business, or a network/franchise of locations)
   - Which compliance item types apply (licenses, COIs, certifications, registrations, permits)
   - Which tracker, document storage, email provider, and Slack channel to use, plus your tracker's columns
   - Your renewal lead-time tiers (for example 90 / 60 / 30 / 7 days) and nudge cadence
   - Who owns each item type and who the escalation owner is for lapses and stalled renewals
3. Once setup finishes, give the agent its first task: *"Read my tracker but do NOT send any nudges and do NOT update any rows. Show me what you'd do today -- which items are due for renewal, which would get a nudge, which are lapsed, and which you'd escalate."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` -- the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` -- first-run setup interview.

## Notes

- Nothing auto-sends until you've confirmed the first dry-run looks correct.
- The agent never files, submits, pays for, or renews anything -- it nudges the responsible owner and tracks status only.
- When a renewed document comes in, the agent logs it and marks the item "Renewal submitted" for a human to confirm the new expiry date. It does not mark items current on its own.
- Lapses are always flagged and escalated the same day, regardless of cadence.
- Nudges are sent as individual emails from your connected email account -- the agent does not send from a shared or Gamut-owned address.
- Slack is recommended but optional; if not connected, escalation alerts will surface in the digest only.
- This is operational tracking, not legal or compliance advice. Whether an item is legally required or sufficient is a decision for the owners and your escalation owner, not the agent.

Relevant subsegments: FRNC, MULT, HVAC, PEST, RSTR, LAND, PNTG, ALRM, SUBC, GCON, INSR, FNTK, HLTK, LGST, AGRI, FOOD, AEC, LAWF, CYBR
