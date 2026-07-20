---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Investor & LP Reporting agent configured. I'll ask a few questions about your fund structure, connected systems, and reporting preferences. This takes about 10 minutes and sets up the agent to run your full reporting cycle from period-close data pull through LP delivery.

---

## Fund basics

1. What is the fund's legal name, and what type of vehicle is it — a real estate fund, a private equity fund, a development JV, or another structure?
2. What is your reporting cadence — monthly, quarterly, or event-driven (distributions and capital calls as they occur)?
3. How many limited partners are in the fund, and do they all receive the same report type or do different LP classes get different formats?

---

## Financial data sources

4. What system holds the fund's accounting and LP capital accounts — Juniper Square, Yardi, a spreadsheet model, or another platform? Is it already connected to Gamut?
5. Where do you track asset-level performance data (occupancy, NOI, debt metrics) — in the same platform, a separate property management system, or spreadsheets?
6. For development funds: where is the project schedule of values and draw tracking maintained?

---

## LP roster and waterfall

7. Where is the current LP roster stored — in Juniper Square, a spreadsheet, or another system? We need each LP's name, ownership percentage, preferred return tier, and distribution method (wire, ACH, check).
8. What is the waterfall structure for distributions — for example, return of capital first, then X% preferred return, then Y/Z profit split? I'll use this to calculate per-LP amounts correctly.

---

## Reporting template and voice

9. Do you have a standard investor letter template — a Word doc, a Drive file, or a past report you can share? If so, please share the file path or link so the agent uses your format and voice.
10. Are there specific metrics or highlights that always lead the investor letter — e.g., cash-on-cash, occupancy, a comparison to underwriting? Name the 2-3 you want the agent to feature.

---

## Draw packages (development funds only)

11. Do you have any active development or construction assets that require draw packages? If yes, where is the schedule of values tracked and who is the construction lender?
12. Is there a specific draw package format or cover sheet template your lender requires?

---

## Output and delivery

13. Where should draft reports and notices be saved before review — a specific Google Drive folder, SharePoint path, or Dropbox location?
14. Which Slack channel or email address should receive the review summary and flagged items when a reporting run is ready for approval?
15. Who is the authorized approver who must sign off before LP notices are released? Provide their name and Slack handle or email.

---

## After Questions Are Answered

Once all questions have been answered:

1. **Update CLAUDE.md** — fill in the `## Your context` section with a structured configuration summary including: fund name and type, reporting cadence, LP count and class structure, accounting system and connection status, LP roster location and waterfall structure, investor letter template reference, key metrics to feature, draw package setup (if applicable), output folder, review channel/email, and authorized approver.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "fund_name": "",
  "fund_type": "re_fund | pe_fund | development_jv | other",
  "reporting_cadence": "monthly | quarterly | event_driven",
  "lp_count": 0,
  "accounting_system": "juniper_square | yardi | spreadsheet | other",
  "accounting_system_connected": true,
  "lp_roster_location": "",
  "waterfall_structure": "",
  "investor_letter_template": "",
  "featured_metrics": [],
  "has_development_assets": false,
  "draw_tracking_location": "",
  "output_folder": "",
  "review_channel": "",
  "authorized_approver": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Run the Q[N] reporting package — pull the period data, draft the investor letter and LP notices, and send me the review summary."

   or

   > "A capital call was just approved for $[amount]. Draft the notices for all LPs."
