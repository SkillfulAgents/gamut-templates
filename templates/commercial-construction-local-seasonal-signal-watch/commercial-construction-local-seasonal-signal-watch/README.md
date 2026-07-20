# Commercial Construction/GC - Local / Seasonal Signal Watch

Commercial GCs win work by showing up early — before the architect is hired or the GC list is set. The signals that indicate upcoming construction are public: permit filings, zoning approvals, development announcements, and the predictable capital budget cycles of large local employers. This agent monitors those streams for the configured geography, filters to relevant project types, deduplicates against the existing pipeline, and delivers a prioritized prospect list to the business development team before competitors have made contact.

## Who this is for

Business development leads and principals at commercial GCs who want to proactively identify upcoming projects in their market rather than waiting for RFPs or referrals.

Relevant subsegments: GCON

Best fit for GCs with a defined market geography who pursue commercial, industrial, or healthcare TI and ground-up work, using Procore, Salesforce, or a spreadsheet pipeline.

## What it does

1. **Permit filing monitoring** — pulls newly filed commercial building permits from local portals or permit data APIs, filtered to relevant types (new construction, TI over a value threshold, structural adds) and extracts property owner, estimated value, and filing date
2. **Zoning and land-use activity** — monitors zoning board agendas and rezoning approvals for parcels moving toward commercial or industrial use
3. **Development announcements** — monitors local business journals, city council meeting minutes, and commercial RE portals for new announced projects in the area
4. **Budget-cycle signals** — tracks the fiscal year windows of large local employers, municipalities, and healthcare systems that typically fund capital improvements at predictable times of year
5. **Deduplication and scoring** — cross-references all signals against the CRM, scores by project value, recency, and proximity, and removes anyone already in an active pursuit
6. **Digest delivery** — posts a structured Slack digest on the configured cadence with a recommended first-contact action for each prospect

## Key integrations

- **Procore / Salesforce / spreadsheet** — CRM and pipeline for deduplication
- **Permit data portals / BuildZoom / county permit systems** — new permit filings
- **Local business journals / RSS / city council feeds** — development announcements
- **Slack** — digest delivery and BD lead alerts

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your geography, work types, CRM, and digest preferences
3. Give the agent its first task: *"Pull this week's commercial permit filings and post the digest."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - Commercial construction and general contractors

Relevant subsegments: GCON
