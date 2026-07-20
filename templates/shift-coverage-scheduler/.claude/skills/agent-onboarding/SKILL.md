---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user and explain that you'll ask a few quick questions to configure their Shift & Coverage Scheduler. Let them know this takes about 5 minutes and the agent will be ready to handle callouts as soon as onboarding is complete.

Work through the questions conversationally — do not present them as a numbered list all at once. Ask, get a response, confirm, then move on.

---

## Questions to ask

**1. Name and business**
Ask for:
- Their name (for personalization)
- Their business name
- Their business type (restaurant / fitness studio / cleaning company / retail store / hotel / other — ask them to describe if other)

**2. Scheduling system and callout method**
Ask:
- What scheduling system do they use? (Homebase, When I Work, Toast, Mindbody, 7shifts, paper/spreadsheet, other)
- How do callouts typically arrive? (Text to the manager, phone call, in-app notification, email — may be more than one)

**3. Staff roles and certification requirements**
Ask:
- What staff roles need coverage scheduling? (e.g., server, line cook, front desk, cleaner, lifeguard, technician)
- Are there any certifications or licenses required for any role before someone can work a shift? (e.g., ServSafe, food handler card, CPR/AED, trade license)
  - If yes: capture which certifications apply to which roles

**4. Outreach escalation timing**
Ask:
- After reaching out to a candidate, how many minutes should the agent wait before moving to the next person if there is no reply?
- Default is 20 minutes — accept the default or let them set a different value
- Store as `escalation_wait_minutes`

**5. Manager escalation trigger**
Ask:
- If the shift is still unfilled, how many hours before the shift start should the agent alert the manager?
- Default is 2 hours — accept the default or let them set a different value
- Store as `manager_alert_hours_before`

**6. Slack configuration**
Ask:
- What Slack channel should coverage status updates and manager alerts go to? (e.g., #shift-coverage, #ops-alerts)
- If they have Slack connected, confirm the channel. If not, prompt them to connect Slack now.

**7. SMS / outreach channel**
Ask:
- Will staff be reached by SMS text message, by Slack DM, by an in-app message (specify app), or a combination?
- If SMS: prompt them to connect their SMS tool (Twilio, OpenPhone, or similar) if not already connected.

---

## After collecting all answers

1. Summarize what you collected and ask the user to confirm before saving.

2. Write the following block to the `## Your context` section of `CLAUDE.md`, replacing the placeholder comment:

```
## Your context

- **Owner:** [Name] at [Business Name] ([Business Type])
- **Scheduling system:** [System name]
- **Callout method:** [How callouts arrive]
- **Staff roles:** [List of roles]
- **Certification requirements:** [Role → required certs, or "None"]
- **Outreach escalation window:** [N] minutes before moving to next candidate
- **Manager alert trigger:** [N] hours before shift start if unfilled
- **Coverage status Slack channel:** [#channel-name]
- **Staff outreach channel:** [SMS / Slack DM / in-app / combination]
```

3. Write a `config.json` file in the workspace root with the following structure:

```json
{
  "owner_name": "",
  "business_name": "",
  "business_type": "",
  "scheduling_system": "",
  "callout_method": [],
  "staff_roles": [],
  "certification_requirements": {},
  "escalation_wait_minutes": 20,
  "manager_alert_hours_before": 2,
  "slack_coverage_channel": "",
  "staff_outreach_channel": ""
}
```

Fill in all values from what was collected. Use arrays for multi-value fields. Use an object mapping role names to arrays of required certs for `certification_requirements` (empty object `{}` if none).

4. Tell the user onboarding is complete and give them their first task prompt from the README so they can test the agent immediately:

> "We have a callout for the Friday 6am cleaning shift at the downtown location — find coverage."

Encourage them to adjust the prompt to match their actual business situation.
