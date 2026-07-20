> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/cleaning-janitorial-shift-coverage-scheduler)** — one-click deploy, no setup.

# Cleaning/Janitorial — Shift / Coverage Scheduling

When a cleaner calls out, the clock starts immediately — and the usual group-text scramble wastes time you don't have. This agent monitors your Swept or Janitorial Manager schedule for callouts and no-shows, finds the right replacement from your qualified staff roster, works through a tiered outreach sequence automatically, and alerts your operations manager the moment a shift looks like it won't fill. No more manually hunting through contact lists at 5am.

Built for commercial and residential cleaning operations that run multi-crew schedules across multiple client sites, where last-minute coverage gaps directly affect client satisfaction and contract retention.

## Who this is for

This template is for cleaning company owners, franchise operators, and operations managers running teams of 5 or more cleaning staff across recurring client accounts. It works best when your scheduling and employee data already live in Swept or Janitorial Manager — the agent reads those systems to find qualified, available replacements without manual lookup.

Relevant subsegments: CLEN

## What it does

1. **Detects open shifts** from callout messages, no-shows (missed clock-ins), manager-created gaps, and recurring problem patterns in Swept or Janitorial Manager.
2. **Classifies urgency** (Critical / Urgent / Standard) based on time-to-shift and immediately begins building a prioritized replacement slate.
3. **Finds qualified replacements** by filtering your roster for site certifications, background clearances, availability, zone proximity, and overtime compliance — then ranks candidates.
4. **Runs tiered outreach** through Swept or Janitorial Manager messaging, working from best-fit staff outward through broader pools, waiting a configured window at each tier before escalating.
5. **Confirms and updates the schedule** when a replacement accepts — reassigning the shift, sending the replacement their details, and optionally notifying the client contact.
6. **Escalates to the manager** if all tiers are exhausted, if a Critical shift has been open too long, or if a client site has repeated coverage failures in the same week.
7. **Delivers a weekly coverage digest** every Monday with fill rate, average time-to-fill, recurring callout flags, and staffing gap recommendations.

## Key integrations

- Swept (employee scheduling, messaging, clock-in tracking)
- Janitorial Manager (shift management, employee records, notifications)
- Google Sheets or equivalent (coverage log storage)
- Email or Slack (manager escalation alerts and weekly digest)

## Getting started

1. Import this workspace into Gamut.
2. Run the `agent-onboarding` skill — type `run agent-onboarding`.
3. Send your first task prompt, for example: "Maria called out sick for tomorrow's 7am shift at Riverside Office Park — find coverage."

## Configuration

After onboarding, your business details and system settings are saved in `config.json` at the workspace root. Context about your operation (team size, client sites, escalation contacts) lives in the `## Your context` section of `CLAUDE.md`. You can edit either file directly to update settings at any time.

## Pattern

Vertical / NON-TECH — Cleaning & janitorial shift coverage
