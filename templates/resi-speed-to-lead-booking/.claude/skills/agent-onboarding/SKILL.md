---
name: agent-onboarding
---

Welcome to the Residential Real Estate - Speed-to-Lead & Booking agent. This onboarding will configure the agent for your brokerage or team so it can start responding to leads, qualifying prospects, and booking showings right away.

I'll ask you a few setup questions. Take your time - the more detail you provide, the better the agent will perform.

## Setup questions

1. **Brokerage and agent identity** - What is your brokerage name? Who is the primary agent or team lead this agent will represent? Provide the name(s) and the phone number and email address to send from (or that leads should see in replies).

2. **CRM setup** - Are you using Follow Up Boss, kvCORE, or both? Provide your CRM API key(s) or webhook URLs so the agent can read and write lead records. If you use both, which is the primary system of record?

3. **Lead sources** - Which inbound lead sources should the agent monitor? Check all that apply: Zillow Premier Agent, Realtor.com, brokerage website form, other (please describe). For each source, provide the webhook, email alias, or API connection the agent should watch.

4. **MLS access** - Do you have an MLS data feed or IDX API connection? If yes, provide the API credentials or feed URL. This allows the agent to reference live listings and comps in qualification conversations. If not, the agent will work without live property data.

5. **Agent roster and routing** - List the agents on your team who should receive routed leads. For each agent, provide: name, phone, email, geographic farm area or specialty (e.g., "Westside buyers under $1M", "luxury listings", "first-time buyers"), and calendar link or availability feed URL. Also specify your routing method: round-robin, farm-area match, lead-source match, or agent tier.

6. **Follow-up sequence timing** - How many follow-up touches should the agent send to an unresponsive lead, and at what intervals? Example: touch 1 at 2 hours, touch 2 at 24 hours, touch 3 at 3 days, touch 4 at 7 days. Specify the timing and whether to use SMS, email, or both for each touch.

7. **Escalation rules** - If a lead goes uncontacted or unresponded for an extended period, who should be notified and how? Provide the escalation contact name, phone, and email, and the time threshold that should trigger escalation (e.g., 4 hours for new leads, 48 hours for cold leads in sequence).

8. **Appointment and reminder preferences** - When booking showings or consultations, should the agent send calendar invites, SMS confirmations, or both? What are your preferred reminder timing windows (e.g., 24 hours and 2 hours before)?

## After collecting answers

Once you have the answers above, do the following:

**1. Write config.json** to the workspace root with this structure:

```json
{
  "brokerage": {
    "name": "",
    "primaryAgent": "",
    "replyPhone": "",
    "replyEmail": ""
  },
  "crm": {
    "primary": "follow_up_boss",
    "followUpBoss": {
      "apiKey": ""
    },
    "kvCore": {
      "apiKey": "",
      "webhookUrl": ""
    }
  },
  "leadSources": {
    "zillowPremierAgent": {
      "enabled": false,
      "webhookUrl": ""
    },
    "realtorCom": {
      "enabled": false,
      "webhookUrl": ""
    },
    "websiteForm": {
      "enabled": false,
      "webhookUrl": ""
    },
    "other": []
  },
  "mls": {
    "enabled": false,
    "apiKey": "",
    "feedUrl": ""
  },
  "agents": [
    {
      "name": "",
      "phone": "",
      "email": "",
      "farmArea": "",
      "specialty": "",
      "calendarUrl": ""
    }
  ],
  "routing": {
    "method": "round_robin",
    "escalationContact": {
      "name": "",
      "phone": "",
      "email": ""
    },
    "escalationThresholdHours": 4
  },
  "followUpSequence": [
    { "touchNumber": 1, "delayHours": 2, "channels": ["sms", "email"] },
    { "touchNumber": 2, "delayHours": 24, "channels": ["sms", "email"] },
    { "touchNumber": 3, "delayHours": 72, "channels": ["email"] },
    { "touchNumber": 4, "delayHours": 168, "channels": ["email"] }
  ],
  "appointments": {
    "sendCalendarInvite": true,
    "sendSmsConfirmation": true,
    "reminders": [
      { "hoursBeforeAppointment": 24, "channels": ["sms", "email"] },
      { "hoursBeforeAppointment": 2, "channels": ["sms"] }
    ]
  }
}
```

**2. Update CLAUDE.md** - Find the `## Your context` section at the bottom of `CLAUDE.md` and replace the placeholder comment with a plain-English summary of the configuration. Example format:

```
You are operating for [Brokerage Name], representing [Primary Agent Name]. 
Your CRM is [Follow Up Boss / kvCORE]. 
Lead sources: [list]. 
MLS access: [yes/no]. 
Agent roster: [names and farm areas]. 
Routing method: [method]. 
Follow-up sequence: [summary of timing]. 
Escalation contact: [name] after [X] hours.
```

**3. Confirm setup and suggest a first task** - Tell the user setup is complete and suggest a first task to try, such as:

"Setup complete. Try this first task: 'A new Zillow lead just came in from Marcus Rivera - he's looking at 4-bed homes in [farm area] in the $600-750k range. Kick off the response workflow and qualify him.'"
