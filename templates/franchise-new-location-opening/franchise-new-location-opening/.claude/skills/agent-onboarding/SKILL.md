---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Franchise New-Location Opening agent. This tracks one new franchise location from greenlight through grand opening. I'll ask about the location, the opening timeline, your checklist, and how you want updates delivered. About 8 minutes.

---

## Location basics

1. What is the franchise brand name, and what is the name or ID of the new location being tracked?
2. What is the target grand opening date for this location?
3. What phase is the location currently in — site selection, lease signed, permits applied, build-out in progress, pre-opening, or another stage?

---

## Checklist and project tracking

4. Do you have a standard opening checklist or project plan (a spreadsheet, a Notion page, a franchisor portal task list)? Please share the location or link so the agent can load the current items.
5. If you don't have a checklist yet, should the agent build one from the standard franchise opening template? (Yes/No — if yes, the agent will generate a checklist based on the phases described in CLAUDE.md.)

---

## Roles and contacts

6. Who is the franchisee or franchise owner for this location? Provide their name and email for reminder delivery.
7. Who is the franchisor field representative assigned to this opening? Provide their name and Slack handle or email.
8. Are there other parties (general contractor, equipment vendor, IT setup crew) who should receive task reminders directly?

---

## Reporting preferences

9. How often should the opening status digest be posted — daily or 3 times per week?
10. Which Slack channel should receive the digest and escalation alerts?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: brand name, location name/ID, target open date, current phase, checklist source, franchisee contact, field rep contact, other parties, digest cadence, and Slack channel.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "brand_name": "",
  "location_name": "",
  "target_open_date": "",
  "current_phase": "",
  "checklist_source": "",
  "franchisee_name": "",
  "franchisee_email": "",
  "field_rep_name": "",
  "field_rep_contact": "",
  "other_parties": [],
  "digest_cadence": "daily | 3x_week",
  "digest_channel": "",
  "overdue_escalation_days": 3,
  "schedule_slip_alert_days": 14
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Load the checklist for [location name] and post the current status."

   or

   > "What items are overdue or at risk for [location name]?"
