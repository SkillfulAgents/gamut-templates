# HVAC / Plumbing / Electrical — License & Credential Renewal Agent

Never get caught with a lapsed EPA card, an expired contractor license, or an overdue COI again. This agent watches every credential for every technician and entity on your team — and makes sure you know about renewals before they become emergencies.

## Who this is for

HVAC, plumbing, and electrical contractors with licensed technicians who have ever been blindsided by a lapsed license or expired certificate of insurance — or who are growing fast enough that tracking renewals across the whole team has become a real job on its own.

**Relevant subsegments: HVAC**

This template is built for field service contractors in the trades: companies running 5 to 200+ technicians, pulling permits regularly, carrying commercial clients who demand proof of insurance, and operating in states with strict licensing boards.

## What it does

1. **Maintains a credential registry** — every technician and business entity, every credential type (state contractor licenses, EPA 608, NATE, journeyman/master, liability COI, workers' comp COI, vehicle registrations, municipal permits), with expiration dates and renewal lead times
2. **Sends tiered renewal reminders** — automated nudges at 90, 60, 30, and 14 days before each expiration, with escalating urgency as the date approaches
3. **Fires an immediate lapse alert** — if a credential expires without a renewal recorded, the owner and office manager are notified right away
4. **Detects job conflicts** — when connected to ServiceTitan or FieldEdge, cross-references expired or expiring credentials against the dispatch schedule and surfaces any tech-job mismatches before they cause a compliance problem
5. **Logs every renewal action** — who started it, when it was submitted, when the new credential was received — so the record is always current and auditable
6. **Generates an on-demand compliance summary** — current status of all credentials, upcoming expirations in the next 90 days, open conflicts — formatted to share with clients, insurers, or auditors

## Key integrations

- **ServiceTitan** — technician roster and job schedule for conflict detection
- **FieldEdge** — same capability for FieldEdge shops
- **Email / Slack** — reminder and alert delivery to techs, office staff, or both
- Works standalone (registry only) if no field service platform is connected

## Getting started

1. **Import this workspace** into your Gamut environment
2. **Run the `agent-onboarding` skill** — the agent will walk you through your tech roster, credential types, reminder preferences, escalation contacts, and integration setup
3. **Send your first prompt** — try: "Show me all credentials expiring in the next 90 days" or "Add EPA 608 Universal for [Tech Name], expires [date]"

## Configuration

During onboarding the agent collects and stores:

- Business name, trade(s), and operating states
- Technician roster and initial credential inventory (can be imported from a spreadsheet)
- Credential types to track
- Reminder lead times (default: 90/60/30/14 days)
- Escalation contacts for lapse alerts
- Reminder delivery channel (email or Slack) and recipients
- ServiceTitan or FieldEdge connection details
- Compliance summary frequency (on-demand or recurring monthly digest)

All configuration is written to the `## Your context` section of CLAUDE.md and to `config.json` at the end of onboarding.

## Pattern

**Vertical / NON-TECH — HVAC, plumbing & electrical compliance and licensing**
Built on the Gamut platform by Datawizz.
