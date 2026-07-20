---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Commercial Construction Signal Watch configured. I'll ask about your geography, the signal types you want to monitor, your CRM, and how you want the digest delivered. About 7 minutes.

---

## Geography and focus

1. What counties, cities, or metro areas do you want to monitor for permit filings and development activity?
2. What types of commercial construction work do you primarily pursue — new ground-up, tenant improvement, industrial, healthcare, education, or a mix?
3. Is there a minimum estimated project value for permits you want to track? (Example: only permits estimated over $250K.) What threshold makes sense for your business?

---

## CRM and deduplication

4. What CRM or pipeline tracker do you use — Procore CRM, Salesforce, a spreadsheet, or another system? Is it connected to Gamut?
5. How far back should the agent look in the CRM before showing a prospect as "new"? (Example: skip any owner contacted in the past 90 days.)

---

## Signal sources

6. Do you have access to a permit data service like BuildZoom, PermitData, or a local portal? Or should the agent pull directly from your county/city permit portals?
7. Are there specific local business journals, commercial RE databases, or city council feeds you want the agent to monitor for development announcements?
8. Which large local employers, healthcare systems, or municipalities should the agent track for seasonal capital budget cycles?

---

## Digest and delivery

9. How often do you want the digest — daily or weekly?
10. Which Slack channel should receive the prospect digest?
11. Who is the primary BD lead to tag in Slack when a high-priority prospect appears?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: company name, monitored jurisdictions, work types, value threshold, CRM and connection status, lookback window, permit data source, announcement sources, budget-cycle targets, digest cadence, Slack channel, and BD lead.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "company_name": "",
  "monitored_jurisdictions": [],
  "work_types": [],
  "permit_value_threshold": 250000,
  "crm_system": "procore | salesforce | spreadsheet | other",
  "crm_connected": true,
  "lookback_days": 90,
  "permit_data_source": "",
  "announcement_sources": [],
  "budget_cycle_targets": [],
  "digest_cadence": "daily | weekly",
  "digest_channel": "",
  "bd_lead": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Pull this week's commercial permit filings and post the digest."

   or

   > "Find any new development announcements in [jurisdiction] from the past 7 days."
