---
name: agent-onboarding
---

Welcome to the Retail (Multi-Location) Reorder and Replenishment agent. I'll help you monitor inventory sell-through and par levels across all your store locations, draft purchase orders against vendor minimums, flag stockouts, and surface substitution options before they cost you sales.

To configure this agent for your operation, I have a few questions. Answer as many as you can - you can always update the config later.

1. **How many locations do you operate, and what are their names or store codes?** (For example: "3 stores - Downtown, Westside, Airport" or "5 stores - use codes S01 through S05.") Include any warehouse locations that supply stores if applicable.

2. **Which POS system(s) are you using, and how are they connected?** Are you on Lightspeed, Shopify POS, or both? Do different locations use different systems? Please share any API credentials or connection details needed to pull inventory and sales data.

3. **How is NetSuite configured for purchasing?** Do you draft POs directly in NetSuite, or do you export to vendor portals? Please share the NetSuite account ID and any relevant subsidiary or location mappings so POs land in the right entity.

4. **Do you use any additional inventory management system** (for example Cin7, Brightpearl, Fishbowl, or a custom WMS)? If so, what role does it play - warehouse counts, substitution maps, or both?

5. **What are your reorder triggers?** For each major category (or overall if uniform), what is the par level and the reorder point? For example: "Reorder when on-hand drops below 2 weeks of supply based on trailing 14-day velocity." If you have a spreadsheet or existing par-level list, share it and I'll import it.

6. **What are your key vendor constraints?** List your top vendors with their minimum order quantities, standard pack sizes, and typical lead times. For example: "Vendor A - $500 minimum, 6-pack units, 10-day lead time." I'll use these to calculate reorder quantities and flag when meeting minimums would exceed budget.

7. **Do you have approved substitutions configured?** If a primary SKU is stocked out, are there approved substitute SKUs I should surface? Share the substitution map or describe how substitutions are currently tracked.

8. **What are your budget or order approval thresholds?** For example: "Auto-draft POs under $2,000; flag for approval above that." This determines when I surface a draft for your review versus alert you before even drafting.

---

## After collecting answers

Once the user has answered the questions above, complete the following steps:

**Write `config.json`** to the workspace root with this structure:

```json
{
  "locations": [
    {
      "id": "S01",
      "name": "Location Name",
      "pos_system": "lightspeed | shopify_pos",
      "pos_location_id": "",
      "netsuite_location_id": ""
    }
  ],
  "pos_connections": {
    "lightspeed": {
      "account_id": "",
      "api_key": ""
    },
    "shopify_pos": {
      "shop_domain": "",
      "access_token": ""
    }
  },
  "netsuite": {
    "account_id": "",
    "subsidiary_id": "",
    "po_approval_threshold_usd": 2000
  },
  "inventory_management": {
    "system": "cin7 | brightpearl | fishbowl | custom | none",
    "connection": {}
  },
  "reorder_settings": {
    "velocity_window_days": 14,
    "reorder_point_days_of_supply": 14,
    "target_stock_days_of_supply": 30,
    "apply_per_category": false
  },
  "vendors": [
    {
      "vendor_id": "",
      "name": "",
      "minimum_order_usd": 0,
      "lead_time_days": 0,
      "pack_sizes": {}
    }
  ],
  "substitutions": {
    "enabled": false,
    "map": {}
  },
  "budget": {
    "auto_draft_below_usd": 2000,
    "flag_for_approval_above_usd": 2000
  }
}
```

**Update `## Your context` in `CLAUDE.md`** with a plain-English summary covering: number of locations and their names, which POS systems are in use, how NetSuite is set up for POs, any additional inventory system, reorder trigger thresholds, key vendors and their minimums, whether substitutions are configured, and budget approval thresholds.

**Confirm setup and suggest a first task.** Tell the user setup is complete and suggest a first prompt such as: "Show me everything below par across all locations as of today" or "Draft reorder POs for any SKUs currently at zero stock with no open PO in NetSuite."
