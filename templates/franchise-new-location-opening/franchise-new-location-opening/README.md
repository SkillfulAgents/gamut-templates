# Franchise Systems - New-Location Opening

Opening a new franchise location involves dozens of interdependent tasks across permits, construction, equipment, staffing, training, and franchisor sign-offs — and a slip in any one of them can push the opening date and delay the start of royalties. Most franchise systems track openings in spreadsheets that go stale the moment someone forgets to update them. This agent maintains a live opening tracker, sends reminders to responsible parties, escalates overdue critical-path items to the franchisor field rep, and posts a daily status digest so the whole team always knows where the opening stands.

## Who this is for

Franchisor development and operations teams, and multi-unit franchisees, who are managing one or more new location openings and need systematic tracking and timely escalation without relying on manual spreadsheet updates.

Relevant subsegments: FRNC

Best fit for franchise systems with a defined multi-phase opening process that spans 60-180 days from greenlight to grand opening.

## What it does

1. **Opening checklist load** — loads the master opening checklist (from the franchisor portal, a spreadsheet, or a template) organized into phases: pre-construction, build-out, pre-opening, staffing/training, franchisor sign-off, grand opening
2. **Daily status tracking** — checks for checklist updates each business day, flags overdue items and at-risk items (due in 7 days with no progress), and computes the projected open date based on current pace
3. **Reminders and nudges** — sends email reminders to assigned parties for upcoming and overdue items; escalates to the franchisor field rep via Slack for overdue critical-path items
4. **Status digest** — posts a structured Slack digest on the configured cadence showing phase completion, overdue items, at-risk items, and blocked items
5. **Field rep alerts** — immediate escalation to the franchisor field rep when critical-path items are 3+ days overdue, the projected open date slips 14+ days, or a permit is taking longer than expected

## Key integrations

- **Franchisor portal / ServiceTitan** — location records, opening tasks, inspection scheduling
- **Google Sheets / Notion** — opening checklist and project tracking
- **Slack** — daily status digest and escalation alerts
- **Email** — reminder delivery to franchisee, contractor, and field rep

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about the specific location, target open date, checklist source, and notification preferences
3. Give the agent its first task: *"Load the checklist for [location name] and post the current status."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Deploy one instance per location being tracked.

## Pattern

Vertical / NON-TECH - Franchise systems and multi-unit operators

Relevant subsegments: FRNC
