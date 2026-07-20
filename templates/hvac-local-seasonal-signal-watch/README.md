> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/local-lead-generation/hvac-local-seasonal-signal-watch)** — one-click deploy, no setup.

# HVAC/Plumbing/Electrical — Local / Seasonal Signal Watch

The homeowner whose AC just died in a heat wave isn't browsing Google — they're calling whoever reaches them first. The family that just moved into a 1987 ranch doesn't know their furnace is on borrowed time yet. The guy who pulled his own plumbing permit three weeks ago is about to realize he's in over his head. These moments exist every week in your service area. This agent finds them and puts a prioritized call list in front of your CSR before the competition does.

---

## Who this is for

HVAC, plumbing, and electrical contractors who want to generate more leads and book more jobs by timing outreach to real local demand signals — rather than blasting the same postcard campaign to the same list every quarter.

- Residential HVAC service and replacement contractors
- Plumbing contractors
- Electrical contractors
- Multi-trade shops serving a defined geographic territory
- Service businesses with a maintenance-agreement customer base to protect and grow

**Relevant subsegments: HVAC**

---

## What it does

1. Monitors weather in the configured service area and flags heat events (5+ days at or above threshold → AC outreach), freeze events (first sub-32°F night → furnace/pipe outreach), and major storms (flood, ice, high wind → post-storm inspection outreach).
2. Watches building permit filings in the service area for major renovation permits (trade upgrade opportunity), new construction (rough-in leads), and homeowner-pulled trade permits (DIY-to-pro conversion).
3. Pulls new-mover data for service area addresses and flags recent arrivals as warm leads — new homeowners are high-value prospects in their first six months.
4. Tracks maintenance-agreement customers within a 60-day tune-up window and surfaces them as priority scheduling outreach before the seasonal rush fills the calendar.
5. Compiles all active signals weekly into a single prioritized outreach list, segmented by signal type and ranked by conversion likelihood.
6. Drafts a brief, trigger-specific outreach note for each segment so CSRs can personalize and send without starting from scratch.
7. Logs outreach sent by trigger type and tracks conversion to booked jobs — so you know over time which signals are worth acting on.

---

## Key integrations

- **ServiceTitan** — maintenance-agreement customer list and tune-up window tracking
- **FieldEdge** — maintenance-agreement customer list and tune-up window tracking
- **Weather data feed** — heat, freeze, and storm event monitoring for configured service area
- **County permit portal / permit data feed** — building and trade permit filings
- **New-mover data provider** — address-level new homeowner data for service area ZIPs
- **Email / Slack** — weekly outreach list delivery

---

## Getting started

1. **Import this workspace** into Gamut using the workspace zip import flow.
2. **Run the `agent-onboarding` skill** — the agent will walk you through your service area, signal preferences, data source connections, and outreach list delivery settings before it starts watching anything.
3. **First task example:** "What signals are active this week in my service area?" — or after a storm: "There was a major freeze event last night — build me an outreach list for furnace check calls."

---

## Configuration

The following are set during onboarding and stored in `config.json`:

| Setting | Description |
|---|---|
| `trade` | Primary trade (HVAC, plumbing, electrical, multi-trade) |
| `service_area` | ZIP codes or counties to monitor |
| `heat_threshold_f` | Temperature that triggers a heat event (default: 90°F) |
| `heat_consecutive_days` | Days at or above threshold to trigger (default: 5) |
| `freeze_threshold_f` | Temperature that triggers a freeze event (default: 32°F) |
| `storm_types` | Which storm types to watch (flood, ice, wind, hail) |
| `permit_types` | Which permit categories to flag |
| `new_mover_source` | New-mover data provider name or feed |
| `maintenance_window_days` | Days before tune-up date to flag for scheduling (default: 60) |
| `field_software` | ServiceTitan, FieldEdge, or none |
| `outreach_list_day` | Day of week for weekly list delivery |
| `outreach_list_recipient` | Email or Slack channel for list delivery |
| `outreach_templates` | Customized templates per signal type |

---

## Pattern

Vertical skin — Local Signal Watch (Wave 4), specific to HVAC/plumbing/electrical trade contractors monitoring weather events, building permits, new-mover data, and maintenance windows in a defined residential service area.
