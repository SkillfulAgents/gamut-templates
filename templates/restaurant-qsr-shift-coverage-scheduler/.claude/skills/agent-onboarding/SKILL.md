---
name: agent-onboarding
---

# Agent Onboarding

Welcome. This skill configures the Shift Coverage Scheduler for your restaurant or QSR operation. I will ask you a series of questions, then save your answers to `config.json` and update the "## Your context" section of `CLAUDE.md`.

Run this once before using the agent for the first time. You can re-run it at any time to update your configuration.

---

## Questions

Ask the user the following questions in order. Wait for each answer before proceeding. If the user skips a question, record the value as `null` and continue.

**1. Restaurant / brand name and location(s)**
"What is the name of your restaurant or brand? If you have multiple locations, list them now (name and address or location ID for each). I will use these to tag shifts and outreach messages correctly."

**2. Scheduling system**
"Which scheduling system do you use: 7shifts, HotSchedules/Fourth, or something else? If 7shifts or HotSchedules/Fourth, do you have an API key or integration token ready? Paste it now or describe where it is stored."

**3. POS integration**
"Do you use Toast POS and want to connect it for labor-vs-demand validation? If yes, provide your Toast API credentials or the location of your credentials file. If no, I will skip POS checks."

**4. Outreach channels and credentials**
"How should I contact staff for coverage: SMS, email, or both? Provide the SMS gateway API key (e.g., Twilio account SID + auth token + sending number) and/or the outbound email address and SMTP/API credentials I should use."

**5. Outreach timing rules**
"What are the do-not-contact hours for staff outreach (e.g., no messages before 7am or after 10pm)? What is the response window you want per candidate before moving to the next one (in minutes, default is 15)? What is the maximum number of candidates to contact before escalating to a manager?"

**6. Manager alert contacts**
"Who should receive escalation alerts when a shift cannot be filled? Provide name, role, and phone/email for each manager. List them in priority order if there is more than one."

**7. Roles and coverage rules**
"List the roles or positions at your location(s) that this agent should handle (e.g., Line Cook, FOH Server, Shift Lead, Bartender). For each role, note any required certifications (e.g., food handler card, alcohol service cert, key holder status). Also set a role priority order for when multiple shifts open at the same time."

**8. Weekly hour cap and overtime rules**
"What is the maximum number of hours per week an employee can be scheduled before I should exclude them from the outreach list? Should I also exclude employees who would go into overtime (above 40 hours or your local threshold) if they took the shift?"

---

## After collecting all answers

1. Write all answers to `/workspace/config.json` using this structure:

```json
{
  "restaurant_name": "",
  "locations": [],
  "scheduling_system": {
    "platform": "",
    "api_key": ""
  },
  "toast_pos": {
    "enabled": false,
    "credentials_path": ""
  },
  "outreach": {
    "channels": [],
    "sms": {
      "provider": "",
      "account_sid": "",
      "auth_token": "",
      "from_number": ""
    },
    "email": {
      "from_address": "",
      "smtp_host": "",
      "smtp_port": null,
      "credentials_path": ""
    },
    "do_not_contact_before": "07:00",
    "do_not_contact_after": "22:00",
    "response_window_minutes": 15,
    "max_candidates_before_escalation": 10
  },
  "managers": [],
  "roles": [],
  "hour_cap_weekly": 40,
  "exclude_overtime": true,
  "coverage_log": []
}
```

2. Update the "## Your context" section in `CLAUDE.md` with a plain-text summary of the configuration. Include: restaurant name, locations, scheduling system, outreach channels, manager contacts, roles covered, and hour cap. Use bullet points. Do not include raw API keys or credentials in this section.

3. Confirm to the user that setup is complete and the agent is ready to monitor for callouts and open shifts.
