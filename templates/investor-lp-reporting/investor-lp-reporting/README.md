# Investor & LP Reporting (RE/Funds)

Fund teams in real estate and private equity spend days each reporting period pulling numbers, filling in templates, and manually drafting notices for each limited partner. This agent automates the full cycle: pulling period-end data from the fund's accounting and admin systems, drafting the investor letter, computing per-LP distribution or capital-call amounts through the waterfall, assembling draw packages for development assets, and routing everything to the right people — so the fund manager reviews and releases rather than builds.

## Who this is for

Fund managers, CFOs, and investor relations teams running real estate funds, private equity vehicles, or development JVs who report to a roster of limited partners on a monthly or quarterly basis and want to dramatically compress the time from period-close to LP delivery.

Relevant subsegments: RDEV, PEVC

Best fit for funds with 5-100 LPs that use Juniper Square, Yardi, or spreadsheet-based fund models.

## What it does

1. **Period data pull** — at each reporting period, pulls financial data (P&L, cash position, NAV, capital accounts) from the connected fund admin or accounting platform, and asset-level metrics from the property or project management system
2. **Fund-level performance summary** — computes period and YTD returns, occupancy, debt metrics, and comparison to underwriting projections; drafts the investor letter in the fund's voice; flags anything materially off-projection for manager review
3. **Per-LP distribution notices** — calculates each LP's gross distribution through the configured waterfall (return of capital, preferred return, carry split), drafts a notice with the distribution amount and updated capital account balance, and attaches supporting schedules
4. **Capital call notices** — when a call is authorized, calculates each LP's pro-rata amount, drafts a capital call notice with wire instructions and due date, and flags any LP whose unfunded commitment is insufficient
5. **Draw packages** — for development assets, pulls the schedule of values, cross-references against the approved budget, assembles the full draw package (cover sheet, schedule of values, invoices list, lien waivers, inspection status), and routes to the manager and lender
6. **Review routing and release** — posts a review summary with all flagged items to Slack, waits for an explicit approval signal before sending any document to LPs, then delivers and archives upon release

## Key integrations

- **Juniper Square / Yardi** — LP capital accounts, fund financials, LP roster, and distribution records
- **Spreadsheet model (Google Sheets / Excel)** — fund-level financial model, schedule of values, and waterfall inputs
- **Google Drive / SharePoint** — investor letter templates, output folder for drafted documents, archive
- **Slack** — review summary, approval routing, delivery confirmations, and flagged-item alerts
- **Email** — LP notice delivery and fund manager review routing

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your fund structure, connected systems, LP roster, waterfall, and output preferences
3. Give the agent its first task: *"Run the Q[N] reporting package — pull the period data, draft the investor letter and LP notices, and send me the review summary."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`. Edit either file to update the fund structure, accounting system, waterfall parameters, authorized approver, or output destinations.

## Pattern

Vertical / NON-TECH - Real estate funds and private equity vehicles

Relevant subsegments: RDEV, PEVC
