---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Hospitality/Hotels Shift Coverage Scheduling agent. I'll ask about your property, departments, scheduling system, outreach preferences, and escalation contacts. About 8 minutes.

---

## Property and departments

1. What is your property's name and type (full-service hotel, select-service, resort, boutique)? Which departments need shift coverage management — front desk, housekeeping, food and beverage, banquet, maintenance, valet, or others?
2. How many total staff do you have across these departments? Roughly how many callouts do you handle per week?

---

## Scheduling system

3. What scheduling system do you use — HotSchedules, Sling, 7shifts, Opera, or a manual spreadsheet? Is it connected to an API or do you manage a roster file?
4. Where does your staff roster live — the scheduling app, a Google Sheet, or another system? What fields does it contain (name, role, department, certifications, availability, contact info)?

---

## Outreach

5. How do you prefer to contact staff for coverage — SMS, Slack, WhatsApp, or the scheduling app's push notification?
6. How long should the agent wait for a response from each candidate before moving to the next (default: 20 minutes)?

---

## Escalation

7. Who is the duty manager or department head who should be notified when a fill is confirmed or an escalation is needed? Provide name and preferred contact (Slack handle or phone number).
8. At what point should the agent escalate — if no fill is found 60 minutes before the shift, or earlier?

---

## Rules and constraints

9. Are there any departments or roles where the agent should not reach out to staff without manager approval first (e.g., banquet servers for high-profile events)?
10. How should overtime situations be handled — flag and hold for manager approval, or flag and continue contacting?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: property name, department list, staff count, scheduling system, roster source, outreach channel, response window, escalation contact and trigger, and overtime policy.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "property_name": "",
  "property_type": "full-service | select-service | resort | boutique | other",
  "departments": [],
  "scheduling_system": "hotschedules | sling | 7shifts | opera | spreadsheet | other",
  "roster_source": "",
  "outreach_channel": "sms | slack | whatsapp | scheduling-app",
  "response_window_minutes": 20,
  "escalation_contact": "",
  "escalation_contact_channel": "slack | sms | email",
  "escalation_trigger_minutes_before_shift": 60,
  "require_manager_approval_departments": [],
  "overtime_policy": "flag-and-hold | flag-and-continue"
}
```

3. **Give the user their first task prompt.** Suggest:

   > "[Role] called out for the [time] shift on [date] — find coverage."

   or

   > "We have an open housekeeping shift this Saturday 8 AM - 4 PM — who's available?"
