> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/fitness-shift-coverage-scheduler)** — one-click deploy, no setup.

# Fitness/Wellness/Salon/Spa — Shift & Coverage Scheduler

Stop scrambling when an instructor calls out at 6 AM or a stylist texts in sick an hour before their first appointment. This Gamut agent monitors for callouts, finds the most qualified available substitute, runs a fair one-at-a-time outreach sequence, and keeps your manager in the loop — so the class or appointment slot gets covered without a single frantic group text.

## Who this is for

Any fitness studio, yoga or pilates center, cycling or barre franchise, wellness clinic, salon, or spa that relies on Mindbody or Boulevard for scheduling and has staff whose roles require specific certifications, licenses, or skills.

**Relevant subsegments: FITN**

## What it does

1. Monitors callout signals across email, SMS relay, Mindbody/Boulevard push notifications, and internal messaging channels
2. Queries the staff roster and filters for substitutes who hold the right certification or service license for the specific class or appointment type
3. Ranks candidates by fairness — staff who have covered the fewest recent callouts go first — to keep the burden distributed across your team
4. Reaches out one at a time with a configurable escalation window (default 20 minutes), so staff aren't getting simultaneous offers for the same shift
5. Confirms the booking in Mindbody or Boulevard the moment a substitute accepts, and notifies both the sub and the manager
6. Escalates to the manager with full context if the list is exhausted or the shift is within a configurable hours-out threshold and still unfilled
7. Delivers a weekly summary with fill rate, time-to-fill averages, top subs, and recurring coverage problem spots

## Key integrations

- **Mindbody** — roster, certifications, schedule, shift updates
- **Boulevard** — roster, service skills, appointment calendar, shift updates
- **Email** — callout detection and staff outreach
- **SMS relay** — callout detection and staff outreach (via Twilio or similar)
- **Internal messaging** — Slack or Teams for manager alerts and escalation

## Getting started

1. **Import this workspace** into your Gamut environment
2. **Run the `agent-onboarding` skill** — the agent will ask you a short set of questions to configure your scheduling system, callout detection channels, certification structure, and escalation contacts
3. **First task example:** "A callout just came in from [instructor name] for the 7 AM spin class tomorrow. Find me a qualified sub."

## Configuration

The agent stores your settings in two places after onboarding:

- **`config.json`** — scheduling system credentials, outreach channel preferences, escalation threshold (hours before shift), escalation window (minutes per candidate), and manager contact info
- **`## Your context` in CLAUDE.md** — filled in during onboarding with your studio's certification taxonomy, class types, location structure, and any standing coverage policies

You can update either at any time by running the `agent-onboarding` skill again or editing directly.

## Pattern

**Horizontal pattern:** Shift & Coverage Scheduler — **Wave 4 vertical skin** for Fitness / Wellness / Salon / Spa (FITN)
