> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/reorder-replenishment/retail-multi-location-reorder-replenishment)** — one-click deploy, no setup.

# Retail (Multi-Location) - Reorder / Replenishment

Managing replenishment across multiple retail locations is a constant balancing act: too little stock means lost sales and frustrated customers, too much means tied-up capital and markdowns. This agent watches sell-through and par levels across every location, drafts reorder purchase orders against vendor minimums, flags active stockouts before they cost you sales, and surfaces approved substitutions and transfer options - so your buyers spend time making decisions, not pulling reports.

## Who this is for

Multi-location retailers running two or more physical stores (or a mix of physical and e-commerce locations) who need automated inventory monitoring and PO drafting. Works best for operations with defined par levels and vendor catalogs, using Lightspeed or Shopify POS at the store level and NetSuite for purchasing and financials. Fits specialty retail, apparel, hardware, home goods, and similar verticals where SKU counts and vendor relationships make manual reorder tracking error-prone.

## What it does

1. **Monitors inventory across locations** - Pulls on-hand quantities and sell-through velocity from your POS and inventory systems, compares against configured par levels, and calculates days-of-supply for every SKU at every location.

2. **Flags stockouts and near-stockouts** - Identifies zero-stock items with no open PO, items trending toward stockout within vendor lead time, and groups them by severity so buyers address the most urgent gaps first.

3. **Drafts purchase orders** - Calculates reorder quantities against vendor minimums and pack sizes, groups multi-SKU orders to the same vendor, and creates draft POs in NetSuite (or exports to vendor portals) for buyer approval before submission.

4. **Recommends transfers before external orders** - Checks whether a location with surplus stock can fill a gap at another location, drafting transfer orders as an alternative to vendor POs when the math works.

5. **Surfaces substitutions** - When a primary item cannot be replenished in time, checks the configured substitution map for approved alternatives and flags them for buyer or manager approval.

## Key integrations

- **Lightspeed** - Source of POS transaction data and on-hand inventory counts for Lightspeed-connected store locations
- **Shopify POS** - Source of POS transaction data and inventory levels for Shopify-connected locations; unified inventory across online and in-store channels
- **NetSuite** - ERP and purchasing system; receives drafted purchase orders and transfer orders, and is the source of truth for open PO status and vendor records
- **Inventory management systems** - Any additional warehouse or inventory platform (e.g., Cin7, Brightpearl, Fishbowl) connected to supplement POS data with warehouse-level counts and substitution maps

## Getting started

1. **Import this workspace** into Gamut using the workspace zip import flow.
2. **Run the `agent-onboarding` skill** - the agent will ask you a short set of questions about your locations, POS setup, vendors, and par-level thresholds to configure itself for your operation.
3. **Give your first task** - try "Show me everything below par across all locations" or "Draft reorder POs for any stockouts with no open PO."

## Configuration

During onboarding, the agent writes a `config.json` file with your location list, POS connections, vendor minimums, par levels, and budget caps. It also fills in the `## Your context` section of `CLAUDE.md` with a plain-English summary of your setup. You can edit either file directly to update thresholds or add new locations as your network grows.

---

Relevant subsegments: RETL
