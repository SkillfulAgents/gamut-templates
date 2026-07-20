> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/retail-multi-location-shift-coverage-scheduler)** — one-click deploy, no setup.

# Retail (Multi-Location) - Shift / Coverage Scheduling

Detects shift callouts and coverage gaps across retail locations, finds qualified available associates from the scheduling system, runs a fair outreach sequence, confirms the fill, and escalates to the store manager if the shift stays open.

---

## What it does

1. **Monitors for callouts and gaps** - Picks up inbound callout messages (SMS or email) and polls the scheduling system for unconfirmed or dropped shifts within a configurable lookahead window.
2. **Identifies qualified, available candidates** - Queries the scheduling system for associates who are not already scheduled, meet the role's skill or certification requirements, and fall within weekly hour caps and rest-period rules.
3. **Ranks candidates fairly** - Sorts by who has covered the fewest shifts in the current pay period, then by stated availability, then by proximity to the location needing coverage.
4. **Runs a structured outreach sequence** - Sends an SMS (or email) to each candidate in order, waits a configurable timeout, and moves to the next person if there is no response or a decline.
5. **Confirms the fill and updates the schedule** - On a YES reply, immediately confirms with the associate, writes the assignment back to the scheduling system, and notifies the store manager.
6. **Escalates uncovered shifts** - If the full candidate list is exhausted, notifies the store manager (and optionally a district manager) with full context and flags the shift in the scheduling system.
7. **Logs every coverage event** - Records all outreach attempts, responses, and outcomes in a structured log for compliance and weekly reporting.
8. **Compiles weekly coverage summaries** - Reports fill rate, average resolution time, and gap reasons per location to operations and HR contacts.

---

## Key integrations

- **When I Work** - Primary scheduling system: source of shift data, candidate availability, and role qualifications; receives confirmed assignments written back automatically.
- **Lightspeed Retail** - Optional POS integration: flags upcoming high-traffic periods where scheduled headcount may fall short before gaps become critical.
- **Shopify POS** - Alternative POS integration for demand-driven staffing alerts; same function as Lightspeed when that is the store's POS system.
- **SMS (Twilio, SimpleTexting, or When I Work native)** - Primary outreach channel for associate notifications and confirmations.
- **Email** - Fallback outreach channel and delivery method for manager escalations and weekly coverage summaries.

---

## Getting started

1. **Import this workspace** into Gamut using the workspace-zip import option.
2. **Run the agent-onboarding skill** by typing `/agent-onboarding` - it will ask you 8 questions about your locations, scheduling system, POS setup, outreach preferences, labor rules, and escalation contacts, then save everything to `config.json` and fill in your context.
3. **Start using the agent** by describing a callout ("Maria at the downtown store just called out for tomorrow 2-8pm") or asking it to check for open shifts ("Any uncovered shifts in the next 24 hours?").

---

Relevant subsegments: RETL
