---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the HVAC/Plumbing/Electrical - Speed-to-Lead & Booking agent. Explain that you are going to ask a few quick questions to configure the agent for their specific business, and that once setup is complete the agent will be ready to respond to inbound leads and book jobs automatically.

Ask the following questions. You may present them all together in a single message:

1. **Business name and trade focus** — What is the name of your business, and which trades do you cover? (HVAC, plumbing, electrical, or some combination — be specific so the agent knows what job types to qualify and book)
2. **Field service management system** — Which FSM do you use to schedule jobs and manage technician availability? (ServiceTitan, FieldEdge, or other — this is where the agent will create job records and check open slots)
3. **Active lead sources** — Which channels are you currently receiving inbound leads from? (e.g., web contact form, Google Local Services Ads, HomeAdvisor, Angi, Thumbtack, Yelp, phone/voicemail, or other — list all that apply)
4. **Service area** — What zip codes or cities does your business serve? The agent will use this to disqualify out-of-area leads before booking.
5. **Emergency escalation contact** — Who should be alerted immediately when an emergency lead comes in (no heat, active leak, electrical failure)? Provide a name, phone number for SMS, and/or Slack handle.
6. **Response time thresholds** — Do you want to use the default unworked-lead alert windows (30 minutes for standard leads, 10 minutes for emergencies), or would you like to adjust these?
7. **Dispatcher/owner name and outreach voice** — What name should sign off on customer-facing messages? (e.g., "Mike" or "Mike's HVAC Team" — this is what customers will see in first responses and follow-ups)

## After collecting answers

Write a `config.json` file at `.claude/skills/agent-onboarding/config.json` with this structure, filled in from the answers:

```json
{
  "businessName": "<business name>",
  "trades": ["<hvac | plumbing | electrical — list all that apply>"],
  "fsmSystem": "<ServiceTitan | FieldEdge | other>",
  "leadSources": ["<web-form | google-lsa | homeadvisor | angi | thumbtack | yelp | phone-voicemail | other>"],
  "serviceAreaZips": ["<zip1>", "<zip2>"],
  "emergencyEscalation": {
    "name": "<contact name>",
    "sms": "<phone number>",
    "slack": "<@handle or channel>"
  },
  "unworkedLeadThresholds": {
    "standardMinutes": 30,
    "emergencyMinutes": 10
  },
  "reEngagementWindowHours": 2,
  "dispatcherName": "<name for customer-facing sign-offs>",
  "dailySummaryDestination": "<email address or Slack channel>"
}
```

If the owner adjusted the unworked-lead thresholds, update `unworkedLeadThresholds` accordingly.

Then update the `## Your context` section at the bottom of `CLAUDE.md` with a plain-English summary:

```
## Your context

**Business:** [Business Name]
**Trades:** [HVAC / plumbing / electrical]
**FSM system:** [ServiceTitan | FieldEdge | other]
**Lead sources:** [list of active channels]
**Service area:** [zip codes or city/region description]
**Emergency escalation contact:** [name — SMS: phone | Slack: handle]
**Unworked lead alert thresholds:** [X] min standard / [Y] min emergency
**Customer re-engagement window:** 2 hours after no reply
**Dispatcher name for outreach:** [name]
**Daily summary destination:** [email or Slack channel]
```

Confirm that setup is complete and the agent is ready to use. Then give the owner their first task prompt to get started:

> "Show me all leads from the last 24 hours that haven't been booked and draft a follow-up for each one."
