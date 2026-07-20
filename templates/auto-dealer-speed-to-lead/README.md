> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/speed-to-lead/auto-dealer-speed-to-lead)** — one-click deploy, no setup.

# Auto Dealer/Service - Speed-to-Lead & Booking

Internet leads are won or lost in the first five minutes. When a car shopper submits an inquiry on your website, AutoTrader, Cars.com, or any other marketplace, they are simultaneously browsing three other dealerships. If your CRM sits on that lead for two hours, the sale is gone. This agent eliminates that gap — it detects every inbound lead the moment it arrives, sends a personalized reply within minutes, qualifies the buyer, books the test drive or service appointment against your real availability, logs every touchpoint to your DMS/CRM, and escalates anything that goes unworked past your defined SLA thresholds.

## Who this is for

Auto dealerships — new car, used car, franchise, or independent — that receive leads from web forms, third-party marketplaces, or inbound calls and want to guarantee a sub-minute first response without adding headcount. Also useful for service drive operations that want to automate inbound service scheduling and reduce no-shows.

Relevant subsegments: AUTO

## What it does

1. **Monitor and detect inbound leads** — polls or receives webhooks from your website, marketplace listings, and call transcripts; deduplicates against existing CRM records and stamps each lead with a received-at timestamp.
2. **Qualify and engage** — sends an immediate personalized acknowledgment within your configured response window (default: 2 minutes), then asks a short qualification script covering vehicle interest, budget, trade-in, timeline, and preferred contact method; scores leads as hot, warm, or cold.
3. **Book the appointment** — checks live calendar availability, offers two or three specific time slots, confirms the booking, sends a calendar invite with dealership details and prep instructions, and fires reminders 24 hours and 2 hours before.
4. **Log every outcome** — writes every interaction, response time, qualification answer, and booking status back to the CRM/DMS record in real time; tags lead source, type, assigned rep, and SLA performance.
5. **Escalate and nudge unworked leads** — checks every 15 minutes for leads past their first-contact SLA; alerts the assigned salesperson or BDC manager; escalates to the sales manager after a second threshold; sends an end-of-day digest with total leads, contacts, bookings, and average speed-to-lead.

## Key integrations

- **CDK Global** — DMS record creation, RO stub generation, inventory holds, scheduling module
- **Reynolds & Reynolds** (ERA-IGNITE / FOCUS) — CRM lead routing, contact deduplication, activity logging
- **VinSolutions** — CRM lead management, contact timeline, BDC workflow integration
- Additional integrations configurable during onboarding: AutoTrader/Cars.com/TrueCar lead feeds, Slack or SMS for internal alerts, dealership website form webhooks

## Getting started

1. **Import this workspace** into Gamut by uploading the zip through the Gamut workspace import flow.
2. **Run the `agent-onboarding` skill** — type `run agent-onboarding` in your first message. The skill will walk you through a short setup interview (dealership name, connected DMS/CRM, lead sources, SLA windows, notification channel) and write your configuration automatically.
3. **Send your first task prompt** — once onboarding is complete, try: *"Check for any unworked leads from the last 2 hours and send me a status report."*

## Configuration

All dealership-specific settings (DMS credentials, SLA thresholds, qualification script overrides, notification recipients, brand voice notes) are stored in `config.json` at the workspace root. The agent's core instructions and tone constraints live in `CLAUDE.md`. Both files are written automatically during onboarding and can be edited directly at any time.

## Pattern

Vertical / NON-TECH — Auto dealer lead response ops
