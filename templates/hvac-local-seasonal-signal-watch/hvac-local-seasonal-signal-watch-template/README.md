# HVAC/Plumbing/Electrical - Local / Seasonal Signal Watch

The best time to call a homeowner about a new HVAC system is the day after a heat wave — not six months later. This agent watches your service area around the clock and puts the right homeowner at the top of your list at exactly the right moment.

## Who it is for

HVAC, plumbing, and electrical contractors who want to grow through proactive outreach to high-intent homeowners rather than waiting for the phone to ring. If your team has ever said "we should have called that neighborhood right after the storm," this agent is built for you.

Relevant subsegments: HVAC

## What it does

1. **Monitors weather signals** in your service area — heat events (5+ consecutive days over your threshold), freeze events (first sub-32°F night of the season), and major storms (flood, ice, high wind) — and opens the outreach window automatically.
2. **Watches building permit filings** in your county for renovation permits, new construction, and homeowner-filed trade permits that signal upgrade or replacement opportunities.
3. **Pulls new-mover data** for your service area ZIP codes — new homeowners are among the highest-lifetime-value prospects and often need inspections or replacements within six months.
4. **Surfaces your own maintenance-agreement customers** who are within 60 days of their annual tune-up window as priority scheduling outreach.
5. **Compiles a prioritized weekly outreach list** every Monday morning, segmented by signal type: storm-triggered, tune-up window, permit-triggered, new-mover, and seasonal threshold.
6. **Drafts a one-paragraph outreach template** for each segment — ready for your CSR or tech to personalize and send by phone, email, postcard, or SMS.
7. **Tracks signal-to-booking conversion** over time so you know which triggers drive the most booked jobs and can tune your thresholds accordingly.

## Key integrations

- **ServiceTitan** or **FieldEdge** — maintenance-agreement customer list and outreach logging
- **County permit portal** — public permit search (browser-based or API, depending on county)
- **Weather data** — NWS public alerts or a connected weather API for the service area
- **New-mover data provider** — connected source or manual import (agent will flag the gap if not configured)
- **Delivery channel** — email, Slack, or in-chat weekly digest

## Getting started

1. **Import this workspace** into Gamut by Datawizz.
2. **Run the `agent-onboarding` skill** — the agent will ask you about your trade, service area, signal preferences, data sources, and delivery preferences, then write your configuration automatically.
3. **Send your first prompt** — try: "Run this week's signal check for my service area and show me the outreach list."

## Configuration

All configuration is written to `CLAUDE.md` and `config.json` during onboarding. Key settings include:

- **Service area** — ZIP codes or counties to monitor
- **Trade focus** — HVAC, plumbing, electrical, or combined
- **Temperature thresholds** — heat and freeze trigger points for your market
- **Permit types** — which permit categories are relevant to your trade
- **New-mover source** — connected provider or manual import cadence
- **Field service platform** — ServiceTitan, FieldEdge, or spreadsheet
- **Delivery day and channel** — when and where the weekly list arrives
- **Outreach channel** — phone, email, postcard, SMS, or combination

## Pattern

Vertical / NON-TECH — HVAC, plumbing & electrical demand signal monitoring
