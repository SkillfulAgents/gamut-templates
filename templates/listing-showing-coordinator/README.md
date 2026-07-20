> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/listing-showing-coordinator)** — one-click deploy, no setup.

# New-Listing & Showing Coordinator

A Gamut agent template for real estate agents and brokers who want to eliminate manual calendar juggling and document-chase emails across the full listing lifecycle.

## What this agent does

- **Listing monitoring** — watches your portfolio for new and updated listings and drafts announcement messages to leads and co-op agents
- **Showing coordination** — receives inbound showing requests, confirms times, sends reminders, and logs everything in your CRM
- **Post-showing follow-up** — sends automated follow-up messages to buyers/buyer's agents on your configured cadence (default: same-day + 3-day)
- **Document chasing** — tracks required transaction documents (disclosures, inspections, title, signatures) and nudges responsible parties when items are overdue
- **Closing countdown** — sends milestone reminders as closing dates approach and flags open items that could jeopardize closing
- **Daily pipeline brief** — posts a structured morning summary to Slack covering today's showings, new leads, outstanding documents, and upcoming closings

## Key integrations

- **CRM / MLS:** Follow Up Boss, kvCORE, LionDesk, or equivalent
- **Email / SMS:** Gmail or connected email for outbound communications
- **Document storage:** DocuSign or Google Drive
- **Slack:** Daily pipeline briefs and urgent lead/closing alerts

## Who it's for

Residential and commercial real estate agents, teams, and brokers who manage active listing portfolios and want automated coordination without giving up control over outbound communications.

**Relevant subsegments: RESI, CRE**

## Getting started

1. Import this template into your Gamut workspace.
2. Run the **agent-onboarding** skill — it will ask about your brokerage, CRM, preferred tone, follow-up cadence, and document SLA, then connect your email and Slack.
3. Once onboarding is complete, try your first task:

> "Show me all active listings and any showing requests that came in today."

## Configuration

All settings are written to `config.json` and summarized in `CLAUDE.md` during onboarding. You can re-run onboarding at any time or edit those files directly to update:

- Response tone (professional/formal or friendly/conversational)
- Post-showing follow-up cadence
- Document-chase SLA (days before first reminder)
- Slack channels for daily briefs and urgent alerts

## Notes

- The agent presents drafted outbound messages for your review before sending by default. You can grant auto-send permission during onboarding or at any time.
- Document-chase reminders escalate to Slack if an item remains outstanding 24+ hours after the first nudge.
- No real listing data, agent names, or brokerage information is included in this template — everything is configured fresh during onboarding.
