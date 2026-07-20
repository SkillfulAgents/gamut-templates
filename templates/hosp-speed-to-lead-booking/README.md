> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/hosp-speed-to-lead-booking)** — one-click deploy, no setup.

# Hospitality/Hotels - Speed-to-Lead & Booking

The first hotel to respond to a booking inquiry wins the booking — but most properties are slow to reply to web form submissions, OTA messages, and email inquiries, especially after hours or on weekends. This agent monitors every inbound channel, sends a fast personalized first-touch reply in the property's voice within minutes, qualifies the lead (dates, party size, purpose of stay), checks availability against the PMS, routes groups and events to the right team, and nudges any inquiry that goes unworked — so no booking opportunity goes cold.

## Who this is for

Reservations managers, front office managers, and GM-operators at independent hotels, boutique properties, and select-service or full-service brands who receive booking inquiries through their website, OTAs, Google Business Profile, or email and want sub-5-minute first-touch response times without adding headcount.

Relevant subsegments: HOSP

Best fit for properties receiving 20-200 inbound booking inquiries per week across multiple channels, using Opera or Cloudbeds as the PMS.

## What it does

1. **Inquiry ingestion** — monitors the website contact form, email inbox, OTA message threads (Booking.com, Expedia), Google Business Profile messages, and SMS/text; extracts guest name, dates, party size, purpose, and special requests; classifies as transient, corporate, group, or event
2. **Availability check** — queries Opera or Cloudbeds for the requested dates and room type; identifies alternatives if the exact type is unavailable; flags the reservations team if PMS is not connected
3. **First-touch reply** — sends a personalized, on-brand reply within 5 minutes (during operating hours) via the same channel the inquiry arrived; confirms availability or routes to the next step; group inquiries are routed to the sales team without quoting rates
4. **Lead routing** — transient leads go to reservations link or direct booking; corporate leads go to the reservations team; groups and events route to sales or catering with full inquiry details
5. **Nudge workflow** — flags unworked inquiries to the reservations manager after the configured window; sends a single follow-up to leads that received a first reply but no booking confirmation after 3 days
6. **Lead log** — tracks every inquiry with source, timestamps, classification, routing, and status for weekly reporting

## Key integrations

- **Opera / Cloudbeds** — availability check and booking confirmation
- **Website contact form / Email** — inquiry ingestion
- **Booking.com / Expedia** — OTA message thread monitoring
- **Google Business Profile** — Google message ingestion
- **Slack / Email** — reservations team routing and nudge alerts

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your property, inquiry channels, PMS, brand voice, and routing preferences
3. Give the agent its first task: *"A new inquiry just arrived — draft a reply and check availability."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Hospitality and hotels

Relevant subsegments: HOSP
