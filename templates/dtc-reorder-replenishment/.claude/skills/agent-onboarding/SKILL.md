---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your DTC Reorder / Replenishment agent. I'll ask about your catalog, vendors, and inventory setup. About 7 minutes.

---

## Store and catalog basics

1. What is your brand name, and how many active SKUs are you managing?
2. What is your primary fulfillment model — in-house warehouse, 3PL, or Shopify fulfillment network?

---

## Inventory data

3. What is your primary inventory source — Shopify, a connected 3PL WMS (ShipBob, ShipHero, etc.), or a separate inventory management system? Is it connected to Gamut?
4. Do you use a separate inventory or ERP system (e.g., Cin7, Skubana/Extensiv, NetSuite) in addition to Shopify?

---

## Vendor and lead time data

5. Where are your vendor records stored — a spreadsheet, your inventory system, or another location? We need vendor name, MOQ, order increment, lead time (days), and last purchase price per SKU.
6. Do you have approved backup vendors for any key SKUs? If yes, are those records in the same place?

---

## Reorder parameters

7. What is your target days-of-supply after a reorder — how many days of stock do you want on hand after a PO arrives? (Default: 60 days.)
8. What safety stock buffer do you want to keep — in days? (Default: 14 days. This means reorder triggers when days of supply falls below lead time + 14 days.)
9. At what days-of-supply level should a SKU be flagged as overstocked? (Default: 120 days.)

---

## Output and approvals

10. Where should draft POs be saved — a Google Drive folder, a SharePoint path, or another location?
11. Which Slack channel should receive the daily replenishment digest?
12. Who is the buying or inventory lead who needs to approve POs before they are sent to vendors?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: brand name, SKU count, fulfillment model, inventory source and connection status, vendor data location, target days of supply, safety stock, overstock threshold, PO output folder, digest channel, and buying lead.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "brand_name": "",
  "sku_count": 0,
  "fulfillment_model": "in_house | 3pl | shopify_network",
  "inventory_source": "shopify | shipbob | shiphero | extensiv | cin7 | netsuite | other",
  "inventory_connected": true,
  "vendor_data_location": "",
  "velocity_window_days": 14,
  "target_days_of_supply": 60,
  "safety_stock_days": 14,
  "early_warning_days": 14,
  "overstock_threshold_days": 120,
  "po_output_folder": "",
  "digest_channel": "",
  "buying_lead": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Run today's inventory check and show me everything that needs to be reordered."

   or

   > "Which SKUs are going to stock out in the next 30 days if I don't order today?"
