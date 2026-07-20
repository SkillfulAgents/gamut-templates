> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/reorder-replenishment/dtc-reorder-replenishment)** — one-click deploy, no setup.

# DTC/E-commerce - Reorder / Replenishment

DTC brands running on Shopify often discover stockouts after a product goes out of stock on the storefront — at which point the lost sales are already gone. This agent monitors sell-through rates and inventory levels daily, detects when SKUs are approaching reorder point before the stockout happens, drafts consolidated purchase orders by vendor, and flags substitution options when a reorder won't arrive in time. The buying team reviews and approves; the agent ensures nothing falls through the cracks.

## Who this is for

Inventory managers, buying leads, and DTC operators managing a multi-SKU catalog who want a daily view of what needs to be ordered and why, without building and maintaining manual spreadsheet systems.

Relevant subsegments: DTC

Best fit for DTC brands with 20-500 active SKUs, a 3PL or Shopify-native fulfillment model, and defined vendor lead times.

## What it does

1. **Inventory and velocity monitoring** — daily pull of on-hand quantities, average daily sell-through, and days-of-supply per SKU from Shopify and connected 3PL/warehouse systems
2. **Reorder point detection** — compares days-of-supply against vendor lead time + safety stock buffer; flags "reorder now" and "reorder soon" SKUs; prioritizes SKUs with active backorders
3. **PO drafting** — calculates recommended order quantity (to target days of supply), groups by vendor, drafts consolidated POs with unit costs and expected delivery dates, saves to Drive/SharePoint for buying-team approval
4. **Substitution flags** — for SKUs approaching stockout where the PO won't arrive in time, identifies in-catalog substitutes and surfaces a recommended action
5. **Overstock alerts** — flags SKUs above the configured overstock threshold with current velocity and a recommendation (pause reorder, promote, transfer)
6. **Daily replenishment digest** — structured Slack summary of reorder-now SKUs with draft PO links, reorder-soon watchlist, substitution flags, and open POs in transit

## Key integrations

- **Shopify** — SKU catalog, inventory levels, order velocity
- **ShipBob / ShipHero / Extensiv / Cin7** — 3PL inventory records and fulfillment data
- **Vendor records spreadsheet / NetSuite** — MOQ, lead times, pricing
- **Google Drive / SharePoint** — draft PO storage and buying-team review
- **Slack** — daily replenishment digest and alerts

## Getting started

1. Import this workspace into Gamut
2. Run the `agent-onboarding` skill — it will ask about your catalog, inventory source, vendor data, reorder parameters, and output preferences
3. Give the agent its first task: *"Run today's inventory check and show me everything that needs to be reordered."*

## Configuration

After onboarding, settings are stored in `.claude/skills/agent-onboarding/config.json` and the `## Your context` section of `CLAUDE.md`.

## Pattern

Vertical / NON-TECH - DTC/E-commerce brands

Relevant subsegments: DTC
