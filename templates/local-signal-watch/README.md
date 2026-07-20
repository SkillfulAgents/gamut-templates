> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/local-lead-generation/local-signal-watch)** — one-click deploy, no setup.

# Local Signal Watch

A Gamut agent template that monitors outreach-timing signals — storm events, new building permits, new-mover/new-resident lists, and seasonal triggers — then surfaces a prioritized daily or weekly prospect list for your team to act on. Eliminates manual permit-portal scraping and news monitoring.

Relevant subsegments: RSTR, HVAC, LAND, PEST, GCON, SUBC, CRE, RESI

---

## What this agent does

Local Signal Watch watches the data sources that matter for field-service and trades businesses — weather events, public permit filings, mover lists, and seasonal calendar windows — and turns them into a clean, ranked call list your team can act on immediately.

Each digest entry includes the address, the signal that triggered it, and a suggested first-contact action. The agent deduplicates against your existing CRM or tracker so your team never calls a contact that's already in the pipeline.

**Key capabilities:**
- Monitors severe weather events (hail, wind, flooding, freeze) in your geography.
- Queries public permit portals filtered to your relevant permit categories (roofing, HVAC, landscaping, general construction, etc.).
- Ingests new-mover / new-resident lists from a connected spreadsheet or CRM field.
- Fires on configurable seasonal calendar triggers (e.g., pre-summer HVAC season, spring lawn care window).
- Deduplicates against your CRM or spreadsheet before surfacing any lead.
- Posts a structured digest to a Slack channel on a daily or weekly schedule.

---

## Who it's for

This template is designed for:
- **Restoration contractors (RSTR)** — storm chasers who need to know about hail and wind events the same day they happen.
- **HVAC contractors (HVAC)** — seasonal demand spikes, new construction permits, and new-mover outreach.
- **Landscaping companies (LAND)** — new movers, spring/fall seasonal windows, and grading permits.
- **Pest control operators (PEST)** — new movers, seasonal trigger windows, and new construction.
- **General contractors and subcontractors (GCON, SUBC)** — permit filings for new residential and commercial construction.
- **Commercial and residential real estate (CRE, RESI)** — new permits and mover signals that indicate buying or listing activity.

---

## Setup (run once)

1. Import this workspace into your Gamut account.
2. The agent-onboarding skill runs automatically on first launch. It will ask you:
   - Your name, company, and the service or trade you provide.
   - Which signal types to monitor (storms, permits, movers, seasonal — pick any combination).
   - Which permit categories are relevant to your work.
   - The zip codes, counties, or metro area to cover.
   - Where you track prospects (CRM name or spreadsheet).
   - Your preferred digest schedule (daily or weekly) and Slack channel.
3. Connect your Slack account when prompted.
4. Connect your CRM or spreadsheet for deduplication (optional but recommended).

After onboarding, the agent writes your configuration to `CLAUDE.md` and `config.json` and is ready to run.

---

## Example first tasks

- "Pull today's storm and permit signals for [your metro] and give me a list of addresses to call."
- "Show me all new roofing permits filed in [county] this week."
- "Any new movers in [zip codes] from the last 7 days?"
- "What's on the list for this week's digest?"
- "Mark [address] as contacted in the tracker."

---

## Connected systems

| System | Purpose |
|--------|---------|
| Weather / storm data API or browser | Detect severe weather events by geography |
| Permit portal or permit data API | Pull new permit filings filtered by category and area |
| New-mover list source (spreadsheet, CSV, or data provider) | Identify recently relocated households |
| CRM or spreadsheet | Deduplication and lead status tracking |
| Slack | Deliver daily or weekly prospect digest |

---

## File structure

```
/
├── CLAUDE.md                              # Agent system prompt + your context (filled at onboarding)
├── config.json                            # Structured configuration (written at onboarding)
├── README.md                              # This file
└── .claude/
    └── skills/
        └── agent-onboarding/
            └── SKILL.md                   # Onboarding interview skill
```

---

## Pattern

Vertical — NON-TECH-lean. Field-service and trades operators, plus real estate professionals who need to time outreach to market signals.
