> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/hvac-shift-coverage-scheduler)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical - Shift / Coverage Scheduling

When a technician calls out sick or has an emergency, HVAC, plumbing, and electrical shops typically end up with a dispatcher making rapid-fire phone calls, hoping to find someone qualified and available before the customer window passes. This agent automates that entire process — detecting the callout, finding the right licensed technician, sending tiered outreach, and logging the fill outcome, so the dispatcher only gets pulled in when the agent genuinely cannot resolve it.

## Who this is for

Dispatchers and service managers running HVAC, plumbing, or electrical service businesses who schedule licensed technicians across multiple jobs per day, deal with last-minute callouts that create customer satisfaction risk, and need a consistent, auditable process for finding coverage without tying up dispatch capacity.

Relevant subsegments: HVAC

Best fit for businesses running 5–50 field technicians with a daily job board managed in ServiceTitan or FieldEdge.

## What it does

1. **Callout detection** — monitors for callout notifications via email, SMS, or ServiceTitan/FieldEdge push notifications; parses the job type, schedule window, and service zone; and immediately flags the affected job as pending coverage
2. **Candidate ranking** — queries ServiceTitan or FieldEdge for available, licensed technicians; filters by trade certification and territory; and ranks candidates by recent coverage load, proximity to the job site, and historical acceptance rate
3. **Tiered outreach** — contacts candidates one at a time via SMS or ServiceTitan/FieldEdge in-app message, with a clear job summary and reply deadline; waits the configured window before moving to the next candidate
4. **Shift logging** — records every outreach attempt with timestamp and outcome; updates the job record in ServiceTitan or FieldEdge when a replacement is confirmed; and attaches the full log for dispatcher audit
5. **Manager escalation** — if the job is still unfilled within the configured lead time (default: 2 hours before start), sends an alert to the dispatcher or service manager via Slack or email with the full outreach history
6. **Daily scheduling summary** — posts a daily report of callouts received, jobs filled vs. unfilled, average fill time, and any recurring coverage gaps by technician, zone, or trade type

## Key integrations

- **ServiceTitan** — job scheduling, technician roster, dispatch board, certification records, and in-app messaging
- **FieldEdge** — job and technician management, dispatch scheduling, and notification delivery
- **SMS** — outreach to technicians for coverage requests and manager escalation alerts
- **Slack** — dispatcher and manager alerts, daily scheduling summary
- **Email** — manager escalation alerts and daily summary delivery
- **Spreadsheet roster** (fallback) — import and maintain technician availability and certification records if not stored in the field service system

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your scheduling system, trade types, callout detection setup, outreach preferences, and escalation contacts
3. Give the agent its first task: *"A callout just came in from [tech name] — their job is at [time] tomorrow in [zone]. Find coverage."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update your scheduling system connection, trade certification matching rules, outreach channel, wait window, blackout hours, escalation contact, or daily summary destination.

## Pattern

Vertical / NON-TECH — HVAC, plumbing, and electrical field service scheduling
