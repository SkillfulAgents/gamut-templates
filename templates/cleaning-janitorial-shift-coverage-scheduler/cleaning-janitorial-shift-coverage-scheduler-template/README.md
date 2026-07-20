# Cleaning/Janitorial Shift Coverage Scheduler

Stop losing 45 minutes to group texts every time a cleaner calls out. This Gamut agent handles last-minute coverage end-to-end — detecting callouts, ranking available staff, sending outreach in sequence, and paging the manager only when it truly cannot fill the shift.

## Who it is for

Operations managers and owners of cleaning and janitorial businesses who spend too much time coordinating last-minute replacements by text. If you manage residential, commercial, or mixed-service crews and a no-show can cost you a client, this template is built for you.

**Relevant subsegments: CLEN**

## What it does

1. Detects callout notifications arriving via email, SMS, Swept, or Janitorial Manager push notifications.
2. Queries your staff roster and ranks available, qualified candidates by fairness — fewest recent hours first.
3. Sends a coverage request to the top candidate via SMS or Swept in-app message, with a clear reply deadline.
4. Automatically escalates to the next candidate if no reply arrives within the configured window (default: 20 minutes).
5. Logs every outreach attempt, confirmation, decline, or non-response in the shift record.
6. Alerts the operations manager via Slack or email if the shift is still open N hours before start (default: 2 hours).
7. Posts a daily scheduling summary — open shifts, filled shifts, unfilled flags, and average fill-time — to your preferred channel.

## Key integrations

- **Swept** — shift schedules, staff roster, in-app messaging, assignment updates
- **Janitorial Manager** — job schedules, staff records, coverage logs
- **SMS / email** — staff outreach and manager escalation
- **Slack** — manager alerts and daily summary delivery
- **Spreadsheet roster** — fallback import if no scheduling system is connected

## Getting started

1. **Import this workspace** into Gamut using the workspace zip file.
2. **Run the agent-onboarding skill** — type `run agent-onboarding` in the chat to answer a short set of setup questions covering your business, scheduling system, callout channels, and escalation preferences.
3. **Send your first prompt** — for example: _"A callout just came in from Jamie — shift is at 10am tomorrow at the Riverside office. Find coverage."_

## Configuration

During onboarding the agent will ask about:

- Your business name, service type, region, and staff count
- Which scheduling system you use (Swept, Janitorial Manager, or spreadsheet)
- How staff call out and which channel the agent should monitor
- Outreach channel (SMS or Swept in-app), wait window before escalating, and blackout hours
- Manager name and contact for escalation alerts, escalation lead time, and daily summary destination

All configuration is saved to the `## Your context` section of CLAUDE.md and to `config.json` so you can review and edit it at any time.

## Pattern

**Vertical / NON-TECH — Cleaning & janitorial shift coverage**
Wave 4 vertical skin | Built with Gamut by Datawizz
