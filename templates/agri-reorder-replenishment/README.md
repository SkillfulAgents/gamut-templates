> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/reorder-replenishment/agri-reorder-replenishment)** — one-click deploy, no setup.

# Agriculture/AgriBusiness - Reorder / Replenishment

Farmers and agribusiness operators work on hard seasonal deadlines. Running short on seed before planting, fertilizer before a narrow application window, or feed during a growth cycle is not just a cost problem - it stops operations. This agent watches your input consumption against your crop plans and feeding schedules, calculates when each item hits its reorder point relative to supplier lead times, drafts purchase orders before critical windows close, and surfaces shortages that need immediate action. It connects your farm management software, ERP, and supplier portals so procurement decisions are driven by your actual field and pen data, not spreadsheet estimates.

## Who this is for

Row-crop operations, livestock and poultry producers, mixed farming enterprises, and agribusiness procurement teams that manage a recurring budget of seeds, fertilizers, crop chemicals, and animal feed. Best suited for operations with more than one location or crop type, where keeping track of input levels and reorder timing across multiple products and suppliers is a real coordination challenge.

## What it does

1. **Consumption monitoring** - Pulls current on-hand quantities from your farm management system and compares them to planned usage rates from your crop calendar or feeding schedule, calculating days of supply remaining for each input.

2. **Critical window detection** - Maps each input against the next hard deadline in your seasonal plan (planting dates, spray windows, feeding continuity) and calculates the latest safe order date by working backward through supplier lead times.

3. **Supplier and contract lookup** - Checks your configured supplier portals and ERP contract records for current pricing, available inventory, pre-pay windows, and any forward contracts or blanket agreements already in place.

4. **Purchase order drafting** - Drafts reorder POs for items at or below their reorder point, applying contract pricing, meeting vendor minimums, and staging them in your ERP as drafts for manager approval before submission.

5. **Shortage escalation** - Flags any input where stock will not cover the next critical window even with an order placed today, generates a clear shortage alert with the shortfall and recommended action, and routes it to the appropriate decision-maker.

## Key integrations

- **Farm management software** (e.g., Conservis, Granular, FarmQA, AgriWebb) - Source of record for on-hand inventory, crop plans, planting and application schedules, and field-level usage data.
- **ERP** (e.g., SAP, Microsoft Dynamics, Sage Intacct, AgriForce) - Where purchase orders are drafted and staged, existing contracts and prepaid credits are tracked, and delivery confirmations are logged.
- **Seed/chemical/feed supplier portals** - External ordering systems for each supplier or cooperative, used to check real-time availability, pricing tiers, allocation limits, and to confirm PO submission.

## Getting started

1. **Import this workspace** into Gamut using the workspace zip import flow.
2. **Run the agent-onboarding skill** - type `run agent-onboarding` after the agent loads. It will walk you through connecting your farm management system, ERP, and supplier portals, and setting your reorder thresholds, coverage targets, and escalation contacts.
3. **Give your first task** - try something like: "Check all seed and fertilizer levels against this season's planting plan and show me anything we need to order in the next two weeks."

## Configuration

Onboarding writes a `config.json` file with your system connections, reorder point thresholds, supplier lead times, coverage targets, and escalation contacts. You can edit this file directly at any time. The `## Your context` section at the bottom of `CLAUDE.md` is also updated during onboarding with a plain-English summary of your operation that the agent uses for every session.

---

Relevant subsegments: AGRI
