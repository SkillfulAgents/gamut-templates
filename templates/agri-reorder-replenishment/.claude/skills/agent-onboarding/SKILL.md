---
name: agent-onboarding
---

Welcome - I'm your Agriculture/AgriBusiness Reorder and Replenishment agent. Before we start monitoring your input levels and drafting purchase orders, I need to understand your operation and connect to your systems. This will take about 5-10 minutes. Let's go through it step by step.

1. **Farm management software** - Which farm management platform do you use to track inventory, crop plans, and field records? (e.g., Conservis, Granular, FarmQA, AgriWebb, Trimble Ag, or another system.) Do you have API access or can we connect via export/integration?

2. **ERP system** - Where do you create and track purchase orders, manage vendor contracts, and record receipts? (e.g., SAP, Microsoft Dynamics, Sage Intacct, AgriForce, QuickBooks, or another system.) What level of ERP access do I have - read-only, draft creation, or full submission?

3. **Supplier portals** - List the main supplier or cooperative portals you order from (seed companies, fertilizer distributors, chemical suppliers, feed mills, co-ops). For each, note whether you have an online ordering account and any contract or pre-pay arrangements active this season.

4. **Input categories and reorder thresholds** - Which input categories do you want me to monitor? (Seeds by variety, fertilizers by product, crop chemicals, animal feed by type, or a subset.) For each category, what is your target days-of-supply buffer - how many days of stock do you want on hand above and beyond the supplier lead time?

5. **Seasonal plan and critical windows** - What are the next major input deadlines in your plan? For example: planting start date by crop/field, planned fertilizer application windows, spray timing constraints, or continuous feeding requirements for livestock. If you have a crop plan or feeding schedule file, share it now or tell me where to pull it from.

6. **Lead times by supplier** - For each of your main suppliers, what is the typical order-to-delivery lead time? Note any that vary by season (e.g., longer lead times at peak planting demand).

7. **Escalation contacts and approval workflow** - Who should receive critical shortage alerts, and who has authority to approve purchase orders before submission? Provide names, roles, and preferred contact method (email, SMS, Slack, in-system notification).

8. **Locations and storage sites** - How many farm locations or storage facilities do you manage? List each site name and what categories of inputs it holds. Some products may need to be tracked and ordered separately by location.

## After collecting answers

Create a `config.json` file in the workspace root with this structure:

```json
{
  "operation": {
    "name": "",
    "locations": []
  },
  "systems": {
    "farm_management": {
      "platform": "",
      "connection_type": "",
      "api_endpoint": "",
      "credentials_env_var": ""
    },
    "erp": {
      "platform": "",
      "connection_type": "",
      "api_endpoint": "",
      "credentials_env_var": "",
      "po_creation_access": true
    },
    "supplier_portals": [
      {
        "name": "",
        "url": "",
        "categories": [],
        "has_api": false,
        "credentials_env_var": "",
        "contract_terms": ""
      }
    ]
  },
  "input_categories": [
    {
      "category": "",
      "unit": "",
      "reorder_point_days": 0,
      "coverage_target_days": 0
    }
  ],
  "supplier_lead_times": [
    {
      "supplier": "",
      "lead_time_days": 0,
      "seasonal_notes": ""
    }
  ],
  "critical_windows": [
    {
      "name": "",
      "date": "",
      "inputs_required": [],
      "locations": []
    }
  ],
  "escalation": {
    "critical_shortage_contacts": [
      {
        "name": "",
        "role": "",
        "contact_method": "",
        "contact_address": ""
      }
    ],
    "po_approvers": [
      {
        "name": "",
        "role": "",
        "contact_method": "",
        "contact_address": ""
      }
    ]
  },
  "settings": {
    "summary_cadence": "weekly",
    "lookahead_days_near": 30,
    "lookahead_days_far": 60,
    "auto_submit_pos": false,
    "urgent_threshold_days": 7
  }
}
```

Update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English paragraph summarizing: the operation name and number of locations, the farm management and ERP systems connected, the input categories being monitored, the key seasonal deadlines in the plan, supplier lead time ranges, and who approves POs and receives shortage alerts. This context will load at the start of every session.

Once config.json is written and CLAUDE.md is updated, confirm setup is complete and suggest a first task: "Setup complete. To kick things off, try: 'Pull current inventory levels for all tracked inputs and show me anything that will hit its reorder point before [next critical window date].'"
