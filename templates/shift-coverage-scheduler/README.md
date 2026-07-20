> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/shift-coverage-scheduler)** — one-click deploy, no setup.

# Shift & Coverage Scheduler

A Gamut agent template that eliminates the group-text scramble every time a callout happens. When a shift gap or callout occurs, the agent automatically identifies qualified available staff, sends coverage outreach in priority order, logs who fills the shift, and alerts the manager if it goes unfilled — without any manual coordination.

## Who this is for

Operations managers and owners at shift-based businesses who spend too much time chasing coverage on their days off.

Relevant subsegments: CLEN, FITN, FOOD, RETL, HOSP, MULT, HVAC

Works for:
- Restaurants and QSR operators
- Fitness studios and wellness centers
- Cleaning and janitorial companies
- Retail stores (single or multi-location)
- Hotels and hospitality operations
- Multi-unit operators managing coverage across locations
- Home services and HVAC companies

## What it does

1. **Detects callouts** — monitors for incoming callout notifications (text, email, app, Slack)
2. **Finds qualified coverage** — queries your scheduling system for staff with the right role, certifications, and availability
3. **Reaches out in order** — contacts candidates one at a time, waits for a reply, escalates down the list if no response
4. **Logs the outcome** — records who filled the shift and when, or documents all failed attempts
5. **Alerts the manager** — if the shift is still unfilled N hours before start, sends an escalation alert with full context

## Key integrations

- **Scheduling/POS system** — Homebase, When I Work, Toast, Mindbody, 7shifts, or equivalent
- **SMS** — Twilio, OpenPhone, or your existing SMS tool (for staff outreach)
- **Slack** — for coverage status updates and manager escalation alerts

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask you about your business, staff roles, certifications, escalation timing, and connected tools, then configure the agent automatically
3. Try your first task:

> "We have a callout for the Friday 6am cleaning shift at the downtown location — find coverage."

Adjust the prompt to match your actual shift, role, and location.

## Configuration

Onboarding writes your settings to `config.json` and `CLAUDE.md`. You can edit either file directly to update:
- Escalation wait time (minutes before moving to next candidate)
- Manager alert threshold (hours before shift start)
- Staff roles and certification requirements
- Slack channel for alerts
- Outreach channel (SMS, Slack DM, or in-app)

## Pattern

Vertical / NON-TECH — Shift-based workforce operations
