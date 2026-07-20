---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Commercial Construction Quote / Estimate Follow-up agent. I'll ask about your systems, bid workflow, and how you want follow-up handled. About 7 minutes.

---

## Company and bid workflow

1. What is your company name, and what types of commercial projects do you primarily bid on — tenant improvement, new construction, industrial, healthcare, education, or a mix?
2. How many open bids or estimates do you typically have outstanding at any given time?

---

## Systems

3. What system do you use to track bids and estimates — Procore, Sage/Viewpoint, a CRM like Salesforce or HubSpot, or a spreadsheet? Is it connected to Gamut?
4. What email account should follow-up emails be sent from — the estimator's own Gmail or Outlook, or a shared company account?

---

## Follow-up preferences

5. How many business days should pass without a response before the agent sends a follow-up? (Default is 5 days for smaller bids and 10 for larger — let me know if you want different thresholds or a single window.)
6. Is there a bid value threshold above which the agent should queue the follow-up for the estimator's review rather than sending automatically? (Example: auto-send for bids under $500K, queue for rep approval above that.)
7. How far before a bid expires should the agent alert the estimator? (Default: 7 days.)

---

## Reporting

8. How often do you want the win-rate summary report — weekly or monthly?
9. Which Slack channel or email should receive the win-rate reports and the digest of expiring bids?
10. Who is the operations or estimating lead who should receive escalations for bids that have been silent for more than 30 days?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: company name, project types, system and connection status, email account, follow-up windows, high-touch threshold, expiration warning window, reporting cadence, report destination, and escalation contact.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "company_name": "",
  "project_types": [],
  "bid_system": "procore | sage_viewpoint | salesforce | spreadsheet | other",
  "bid_system_connected": true,
  "email_account": "",
  "followup_window_standard_days": 5,
  "followup_window_large_days": 10,
  "large_bid_threshold": 500000,
  "high_touch_threshold": 500000,
  "expiration_warning_days": 7,
  "reporting_cadence": "weekly | monthly",
  "report_destination": "",
  "escalation_contact": ""
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Check all open bids and send follow-ups to anyone who hasn't responded in the past [N] days."

   or

   > "Show me all bids expiring in the next 7 days."
