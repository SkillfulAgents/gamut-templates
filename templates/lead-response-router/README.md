> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/lead-response-router)** — one-click deploy, no setup.

# Lead Response & Router

> Sends an instant first-touch reply in your voice the moment a lead arrives, qualifies it against your criteria, routes it to the right person, logs it in your CRM, and nudges any lead that goes unworked.

## What it does

Lead Response & Router watches every channel your leads come in on - web form, email, Google Local Services, Facebook lead ads, phone/SMS - and reacts the instant a new lead lands. It fires a fast first-touch reply in your voice within your speed-to-lead target (for example, within 5 minutes), qualifies the lead against your criteria, routes it to the right rep or queue, logs it in your CRM, and nudges any lead that sits unworked. Speed-to-lead is the single biggest revenue lever for local services: a lead answered in the first few minutes is worth far more than one answered an hour later.

The instant first-touch is the one thing the agent sends automatically, and it is strictly bounded to your approved template and voice - it acknowledges the lead and sets expectations, but never quotes a price, books a time, or makes a commitment. Anything beyond first-touch (quotes, scheduling, technical answers) is drafted for a human to approve. Prefer to review everything? Turn on draft-only mode and the agent sends nothing without your sign-off.

Works for home and field services (HVAC, pest control, landscaping, painting, alarm/security, restoration), real estate, fitness studios and salons, auto services, recruiting, agencies, and any business where the first reply wins the deal.

## What you'll need

- **Accounts:**
  - Lead sources: web form provider, email, Google Local Services, Facebook lead ads, or a phone/SMS system - whichever you use
  - CRM or lead tracker: HubSpot, Salesforce, Pipedrive, Jobber, Housecall Pro, ServiceTitan, Airtable, Google Sheets, or similar
  - Email and/or SMS: Gmail, Outlook, Twilio, or your existing texting tool (for first-touch replies)
  - Slack (for routing alerts and unworked-lead nudges)
- **API keys:** none required (all accounts connected via Gamut during onboarding)
- **Other:** your real first-touch wording and 2-3 sample replies from your sent folder (these are what make the reply sound like you, not a bot)

## Getting started

1. Import this template into Gamut.
2. On import, the agent-onboarding skill launches automatically and asks:
   - What you do and the channels your leads come in on
   - Which CRM/tracker, email/SMS tools, and Slack channel to use
   - Your first-touch template and 2-3 real reply samples so the agent matches your voice
   - Your qualification criteria (service area, job size, urgency, what counts as out of scope)
   - Your routing rules (who or which queue gets a lead by type, territory, source, or round-robin)
   - Your speed-to-lead SLA target and your unworked-lead nudge threshold
   - Whether to run in draft-only mode or let the first-touch auto-send
3. Once setup finishes, give the agent its first task: *"Take this sample lead but do NOT send anything and do NOT update the CRM. Show me what you'd do - the first-touch you'd send, how you'd qualify it, who you'd route it to, and what you'd log."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` - the agent's instructions and your configuration (written by onboarding).
- `.claude/skills/agent-onboarding/` - first-run setup interview.

## Notes

- The first-touch reply is the one message that sends automatically, because speed is the entire point - but it is strictly bounded to your approved template and voice. It never quotes prices, books times, or makes commitments.
- Anything beyond first-touch (quotes, scheduling, technical answers) is drafted for a human to approve, never auto-sent.
- Prefer full control? Turn on draft-only mode and nothing sends without your approval, including the first-touch.
- Nothing auto-sends until you've confirmed the first dry-run looks correct.
- Replies are sent from your connected email/SMS account - the agent does not send from a shared or Gamut-owned address.
- The agent de-duplicates against your CRM so returning contacts don't get a cold first-touch.
- Spam and out-of-scope leads are logged with a reason but never routed to a rep.
- The agent respects opt-outs (STOP / do-not-contact) and halts messaging to those leads.

Relevant subsegments: HVAC, PEST, RSTR, LAND, PNTG, ALRM, RESI, FITN, AUTO, RECR, MKTG, CRE, MULT, FRNC, HOSP
