> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/cre-deal-desk)** — one-click deploy, no setup.

# CRE Deal Desk — BOV/OM & Comps

A Gamut agent template for commercial real estate brokers and developers. Give it a property address and a brief — it researches the subject property, pulls a comparable sales/lease set, drafts a client-ready Broker Opinion of Value (BOV) or Offering Memorandum (OM), and assembles a tour kit. Work that typically takes 4–8 hours per engagement is completed in one session.

**Relevant subsegments: CRE, RDEV**

---

## What this agent does

1. **Property research** — Pulls parcel data, building specs, ownership history, and recent news from CoStar, Reonomy, and public records via browser-based research.
2. **Comps pull** — Searches for comparable sales and/or leases matching your asset class, size, and submarket. Presents a structured comps table for broker review before any drafting begins.
3. **BOV or OM drafting** — Writes the full document (executive summary, market overview, property description, comp analysis, value/pricing guidance) in the firm's voice and format.
4. **Tour kit** — Produces a property one-pager, driving directions, and broker talking points for listing pitches and property tours.
5. **Filing and notification** — Saves the finished deliverable to Google Drive, posts a deal-ready notification to Slack, and logs the engagement in your CRM.

---

## Setup

Import this template into Gamut, then run the **agent-onboarding** skill. It will ask you about:

- Your name, firm, and primary asset type focus
- Your target markets / geographies
- BOV vs. OM preference and sample format (upload optional)
- Comp search defaults (radius and lookback period)
- Your CRM and Google Drive folder for deliverables
- Slack channel for deal-ready notifications

After onboarding, the agent writes your configuration to `CLAUDE.md` and `config.json` so it's ready to work immediately.

---

## Key integrations

| Integration | Purpose |
|---|---|
| CoStar / Reonomy | Browser-based comp research and property data |
| Google Drive | Save completed BOVs, OMs, and tour kits |
| Slack | Deal-ready notifications with document links |
| Salesforce / CRE CRM | Log engagements and deal records |

---

## First task to try

> "Pull comps and draft a BOV for [property address] — industrial, 45,000 SF, suburban Chicago."

---

## Pattern

- **Type:** Vertical
- **Segment:** NON-TECH
- **Subsegments:** CRE (Commercial Real Estate Brokerages), RDEV (Real Estate Developers)
