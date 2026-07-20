> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/hosp-shift-coverage-scheduler)** — one-click deploy, no setup.

# Hospitality/Hotels - Shift / Coverage Scheduling

A front desk callout at 6 AM or a housekeeping no-show on a peak checkout day can derail the entire property. Most hotels manage coverage gaps through a chain of manual phone calls and text threads — slow, undocumented, and dependent on whoever picks up first. This agent automates that entire sequence: when a shift gap is reported, it queries the roster for qualified available staff, contacts them in priority order with a configurable response window, logs every attempt, and confirms the fill to the duty manager — all before the shift starts.

## Who this is for

Duty managers, front office managers, housekeeping directors, and F&B managers at full-service hotels, select-service properties, and resort operations who need to fill callouts quickly across front desk, housekeeping, food and beverage, banquet, and maintenance shifts.

Relevant subsegments: HOSP

Best fit for properties with 30-500 staff using Opera, Cloudbeds, or a workforce scheduling system like HotSchedules or Sling.

## What it does

1. **Gap ingestion** — captures the callout via the scheduling system, manager message, or Slack; extracts the department, role, date, shift time, and any required certifications; logs the gap as Open
2. **Roster search** — queries the scheduling system or staff roster for qualified available staff in ranked order: on-call first, then flex/part-time, then full-time off, then cross-department eligible; filters for certifications, availability, and overtime risk
3. **Coverage outreach** — contacts candidates in order via SMS, Slack, or scheduling app push with a 20-minute response window; logs every attempt with timestamp and response status
4. **Fill confirmation** — updates the scheduling system, notifies the duty manager with fill details, and closes the gap in the tracker
5. **Escalation** — if no fill is confirmed within the configured window or the gap is urgent, escalates immediately to the duty manager and department head with the full outreach log
6. **Weekly coverage report** — aggregates callout frequency by department, fill rate, average fill time, and staff with highest fill-in participation

## Key integrations

- **Opera / Cloudbeds** — reservation load and staffing context
- **HotSchedules / Sling / 7shifts** — scheduling and roster query
- **SMS / Slack** — staff outreach and manager notifications
- **Google Sheets / Airtable** — coverage tracker and logging

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your property, departments, scheduling system, outreach channel, and escalation contacts
3. Give the agent its first task: *"[Role] called out for the [time] shift on [date] — find coverage."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Hospitality and hotels

Relevant subsegments: HOSP
