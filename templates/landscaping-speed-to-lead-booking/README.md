> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/landscaping-speed-to-lead-booking)** — one-click deploy, no setup.

# Landscaping/Lawn - Speed-to-Lead & Booking

Landscaping and lawn care businesses lose jobs every day not because they lack capacity, but because a competitor replied faster. This agent monitors every inbound lead channel — web forms, phone/voicemail, Thumbtack, Angi, HomeAdvisor — sends a personalized first reply within seconds, qualifies the job with targeted questions, and books the estimate or appointment directly in Jobber or Aspire. Unworked leads are nudged automatically so nothing sits ignored until it goes cold.

## Who this is for

Owner-operators and small office teams running residential or commercial landscaping, lawn maintenance, or lawn care businesses who receive inbound leads from multiple channels, have no dedicated sales staff, and need a consistent, fast-response process that converts inquiries into booked estimates without requiring the owner to be available at all hours.

Relevant subsegments: LAND

Best fit for businesses running 2–20 crews, booking 10–100+ estimates per month, and fielding leads from at least two channels (e.g., website + Thumbtack).

## What it does

1. **Capture & triage inbound leads** — monitors web forms, voicemail/call transcripts, and marketplace leads (Thumbtack, Angi, HomeAdvisor); extracts contact info and service details; checks Jobber or Aspire for existing client records; logs every lead immediately
2. **Send sub-minute first reply** — responds within 60 seconds of lead arrival by the correct channel (SMS or email), greeting the prospect by name and referencing the specific service they asked about
3. **Qualify the job** — asks up to three targeted questions scoped to the service type (lawn maintenance, install, cleanup, irrigation) to gather what estimators need; skips re-asking details the prospect already provided
4. **Check availability & book** — pulls the live schedule from Jobber or Aspire, offers two or three specific estimate slots, creates the job record on confirmation, and sends the prospect a booking confirmation
5. **Nudge unworked leads** — checks every few hours for leads that haven't advanced; sends a single follow-up to non-responsive prospects; flags stale leads in the daily digest
6. **Daily lead digest** — sends the owner a morning summary of new leads, booked estimates, unworked leads, stale leads, and the week's upcoming estimate calendar

## Key integrations

- **Jobber** — job and client management, scheduling, and booking for residential and commercial landscaping operations
- **Aspire** — commercial landscaping operations, estimating, and CRM for larger crews or contract-heavy businesses
- **Thumbtack / Angi / HomeAdvisor** — marketplace lead sources; leads are captured and responded to through the agent's lead intake flow
- **Email** — outreach for web form and marketplace leads
- **SMS** — outreach for phone and text-in leads (requires opt-in configured)
- **Slack** — owner notifications and daily lead digest (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your business, lead channels, scheduling system, and booking preferences to configure the agent
3. Give the agent its first task: *"Show me all leads from the past 48 hours and tell me which ones are unworked."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update lead channels, qualification question sets, booking system (Jobber vs. Aspire), reply channel preferences, follow-up intervals, stale-lead thresholds, or the digest destination.

## Pattern

Vertical / NON-TECH — Landscaping & lawn care lead response and booking
