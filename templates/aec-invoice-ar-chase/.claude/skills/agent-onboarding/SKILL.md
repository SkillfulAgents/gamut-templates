---
name: agent-onboarding
---

Welcome to the Architecture/Engineering/Design - Invoice and AR Chase agent. I will help you configure this agent for your firm so it can chase unpaid invoices and draw requests in your principal's voice, escalate aging AR by tier, and deliver weekly cash and AR digests.

Let me ask you a few questions to get set up. Answer each one, and I will save your configuration when we are done.

**Questions:**

1. **Firm name and principal(s):** What is the name of your firm, and who are the principals whose name(s) outreach should come from? (e.g., "Smith + Rivera Architecture, principal: Maria Rivera, AIA")

2. **Project accounting system:** Which system do you use as your primary project accounting and AR source - Deltek Vision, Deltek Vantagepoint, BQE Core, Ajera, or QuickBooks? If you use more than one (e.g., QuickBooks alongside Deltek), list both and indicate which is the AR-of-record.

3. **Billing types and invoice formats:** Do you bill on fixed fee, hourly, or a mix? Do you submit AIA G702/G703 draw requests for any construction-phase work? Are there any other billing formats (e.g., government SF-330 cost reimbursable, IDIQ task orders) the agent should recognize?

4. **AR aging thresholds and escalation policy:** Do you want to use the default aging buckets (0-30 days warm reminder, 31-60 moderate, 61-90 elevated, 90+ critical), or do you have different thresholds? At what point do you want the agent to flag an account for principal review before sending the next message?

5. **Retainage and lien policy:** Do any of your projects include retainage holdbacks? If so, what is the standard retainage percentage, and what triggers release? For construction-phase projects, which states or jurisdictions are you working in (affects preliminary notice and lien deadline tracking)?

6. **Client contacts and AP routing:** When escalating to 61+ days, should outreach go to both the client's project manager and their AP department by default, or only when you have the AP contact on file? Do you have a preferred format for the escalation message (e.g., cc the principal, use a firm letterhead template)?

7. **Weekly digest preferences:** What day and time should the weekly cash and AR digest be delivered, and who should receive it - just the managing principal, or the full project team? Should it include individual project-level detail, or a summary-only view?

8. **Principal email signature block:** What is the signature block the agent should use when drafting client-facing emails? (Name, title, firm, phone, and any licensure abbreviations - e.g., "Maria Rivera, AIA, Principal, Smith + Rivera Architecture, 415-555-0100")

---

## After collecting answers

Once the user has answered all questions, save the following config to `.claude/skills/agent-onboarding/config.json`:

```json
{
  "firm": {
    "name": "",
    "principals": []
  },
  "accounting": {
    "primary_system": "",
    "secondary_system": "",
    "ar_of_record": ""
  },
  "billing": {
    "types": [],
    "uses_aia_draw_requests": false,
    "other_formats": []
  },
  "ar_policy": {
    "aging_buckets": {
      "warm_reminder_days": 30,
      "moderate_days": 60,
      "elevated_days": 90,
      "critical_days": 91
    },
    "principal_review_threshold_days": 61,
    "retainage_holdback_pct": null,
    "retainage_release_trigger": ""
  },
  "lien_policy": {
    "construction_phase_active": false,
    "jurisdictions": []
  },
  "escalation": {
    "route_to_ap_by_default": true,
    "cc_principal_on_escalation": true
  },
  "digest": {
    "delivery_day": "Monday",
    "delivery_time": "08:00",
    "recipients": [],
    "include_project_detail": true
  },
  "signature_block": ""
}
```

Then update the `## Your context` section of `CLAUDE.md` with a plain-English summary covering: firm name and principal(s), primary billing system, billing types in use, AR escalation thresholds, retainage and lien jurisdiction notes, and digest schedule.

Finally, confirm setup is complete and suggest a first task. For example:

"Setup is complete. Here is a task to get started: 'Pull all open invoices past due more than 30 days from [system] and draft first-touch reminder emails for each one in [principal name]'s voice.' Or try: 'Generate this week's AR aging digest for the principal meeting.'"
