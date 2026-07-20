> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/vc-investing/dealflow-portfolio-monitor)** — one-click deploy, no setup.

# Deal-Flow & Portfolio Monitor

A Gamut agent template for venture capital, private equity, growth equity, and investment banking/M&A advisory teams.

Relevant subsegments: PEVC, IBMA

---

## What this agent does

- **Triages inbound deal flow** from Gmail and Slack — scores each opportunity against your investment thesis and logs it to your CRM automatically.
- **Tracks deals through the funnel** — surfaces stale opportunities and flags high-score deals that have gone cold.
- **Monitors portfolio companies and watchlist targets** — runs weekly news and signal searches, posts findings to your CRM.
- **Delivers a weekly portfolio KPI digest** — a scannable Slack digest covering key metrics, notable news, and items requiring partner attention.

---

## Key systems

| System | Purpose |
|--------|---------|
| Gmail | Deal flow inbox monitoring |
| Affinity / Attio / HubSpot / spreadsheet | CRM logging and funnel tracking |
| Google Drive or Notion | Memo and deck storage |
| Slack | Digest delivery and high-score deal alerts |

---

## Getting started

When you first open this agent, it will run the **agent-onboarding** skill automatically. The skill will ask you to:

1. Describe your firm and investment thesis (used for triage scoring)
2. Specify your CRM and how deals arrive
3. List your portfolio companies and key KPIs (up to 30)
4. Add companies or sectors to your watchlist
5. Set your digest cadence and Slack channel
6. Connect Gmail and Slack

After onboarding, your first task:

> **"Triage today's inbound deal flow and tell me what's worth a first call."**

---

## Example prompts

- "What deals came in this week and how did they score?"
- "Give me a funnel snapshot — what's in diligence right now?"
- "Run a news scan on my portfolio companies."
- "Which portfolio companies have gone quiet in the last 30 days?"
- "Pull together the weekly digest early — I have an LP call this afternoon."
- "Add Acme Corp to my watchlist and start monitoring them."

---

## Customization notes

- **Triage scoring** is calibrated to your investment thesis entered during onboarding. You can refine the thesis at any time by updating `## Your context` in CLAUDE.md or telling the agent directly.
- **KPIs** are set per portfolio company during onboarding. Add or change them in `config.json` or by prompting the agent.
- **Digest cadence** defaults to weekly (Monday morning) but can be changed to bi-weekly or on-demand.
- **CRM write behavior** is additive by default — existing notes are never overwritten without confirmation.

---

## Pattern

Vertical — NON-TECH  
Investment operations for VC/PE/growth equity and IB/M&A advisory teams
