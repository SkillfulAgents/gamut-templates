> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/hvac-speed-to-lead-booking)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical - Speed-to-Lead & Booking

Inbound leads in the trades are ruthlessly time-sensitive: studies show the first company to respond wins the job the majority of the time, yet most HVAC, plumbing, and electrical shops still rely on a CSR or the owner to manually return calls and web forms. This agent responds to every inbound lead — phone voicemail, web form, HomeAdvisor, Angi, Thumbtack, Google LSA — within seconds, qualifies the job, and books it directly into ServiceTitan or FieldEdge before a competitor can call back. Leads that go unworked trigger automatic owner alerts so nothing falls through the cracks.

## Who this is for

Owner-operators and dispatch managers running residential or light-commercial HVAC, plumbing, or electrical businesses who receive leads from multiple channels, want sub-minute first responses at all hours, and need new jobs flowing into ServiceTitan or FieldEdge without a CSR manually handling every inquiry.

Relevant subsegments: HVAC

Best fit for shops running 2–20 technicians that are actively advertising on Google LSA, Angi, HomeAdvisor, or Thumbtack and are losing jobs to faster-responding competitors.

## What it does

1. **Capture & triage inbound leads** — monitors all configured lead sources (phone voicemail, web forms, HomeAdvisor, Angi, Thumbtack, Google LSA), logs every lead to the tracker, categorizes by trade, and flags emergency calls for immediate escalation
2. **Send a sub-minute first response** — replies within 60 seconds via the same channel the lead arrived on (marketplace messaging, email, or SMS for voicemail), using the business's name and a personal dispatcher voice
3. **Qualify the job** — collects service address, issue description, system type (HVAC), active damage status (plumbing), or panel/fixture details (electrical), preferred appointment window, and homeowner authorization
4. **Check availability and book** — queries ServiceTitan or FieldEdge for matching open slots, presents 2–3 windows to the customer, creates the job record with full notes on confirmation, and sends the customer a booking confirmation
5. **Nudge unworked leads** — alerts the owner or dispatcher via Slack or SMS when a lead sits unworked past the configured threshold (default 30 min standard, 10 min emergency) and sends a single customer re-engagement if no reply within 2 hours
6. **Daily lead and booking summary** — delivers an end-of-day report covering total leads by source, booked vs. unworked, average response time, and any open items that still need attention

## Key integrations

- **ServiceTitan** — primary FSM for job creation, customer records, and technician availability
- **FieldEdge** — alternative FSM for scheduling and job management
- **HomeAdvisor / Angi / Thumbtack** — marketplace lead sources (inbound messaging)
- **Google Local Services Ads** — inbound call and lead capture
- **Email** — lead response and booking confirmation for web form inquiries
- **SMS** — first response to voicemail leads and owner/dispatcher nudge alerts
- **Slack** — dispatcher alerts for unworked leads and emergency escalations (optional)

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will walk through your business details, trade focus, connected systems, and lead sources to configure the agent for your specific operation
3. Give the agent its first task: *"Show me all leads from the last 24 hours that haven't been booked and draft a follow-up for each one."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update your FSM connection (ServiceTitan vs. FieldEdge), lead source list, response time thresholds, emergency escalation contacts, service area zip codes, or the Slack/SMS destination for dispatcher alerts.

## Pattern

Vertical / NON-TECH — HVAC / Plumbing / Electrical field service
