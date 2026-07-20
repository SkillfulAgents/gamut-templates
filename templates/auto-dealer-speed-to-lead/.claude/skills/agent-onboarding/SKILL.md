---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user warmly and explain that this short setup will configure the Speed-to-Lead & Booking agent for their dealership. Tell them it takes about 5 minutes and covers their lead sources, scheduling system, response windows, and escalation contacts — after which the agent is ready to start working inbound leads.

Work through the following questions conversationally. Ask one or two at a time, not all at once. Acknowledge each answer before moving to the next.

---

## Onboarding Questions

**Question 1 — Dealership basics**

Ask:
- What is the full name of your dealership or service center? (e.g., "Eastside Ford" or "Valley Auto Group")
- What type of dealership is it — new car franchise, used-only, or both? And does your team also handle inbound service scheduling through this same workflow, or is service booked separately?
- Who is the BDC manager or sales manager who owns the lead response process?

**Question 2 — Lead sources connected**

Ask:
- Which lead sources should this agent monitor? Common options include: dealership website contact forms, AutoTrader, Cars.com, CarGurus, TrueCar, inbound call transcripts (via phone system integration), and trade-in valuation tools (e.g., KBB ICO, Carmax offers).
- For third-party marketplace leads, do they flow into your CRM/DMS automatically (via ADF/XML feed), or will you be connecting the marketplaces directly?
- Are there any lead sources you want to exclude or handle manually rather than having the agent respond first?

**Question 3 — DMS and CRM connections**

Ask:
- Which DMS and CRM systems are you using? We support CDK Global, Reynolds & Reynolds (ERA-IGNITE or FOCUS), and VinSolutions out of the box. Let me know what you have connected or what API credentials you'll be providing.
- For appointment booking, does your scheduling system live inside your DMS (CDK's service scheduler, Reynolds' appointment module), or do you use a separate tool (e.g., Xtime, TimeHighway, Google Calendar)?

**Question 4 — Response time target**

Ask:
- What is your target time for sending a first reply to a new inbound lead — in minutes? (Common targets: 2 minutes, 5 minutes, under 15 minutes.) This sets the SLA clock for escalation alerts.
- For leads that arrive outside business hours, what should the agent do? Options: send an immediate acknowledgment and queue for human follow-up at open, or wait until business hours to send the first outreach.
- What are your business hours? (Days of week and hours — e.g., Mon–Sat 8 AM–8 PM, Sun 10 AM–6 PM.)

**Question 5 — Outreach preferences and auto-send**

Ask:
- How should the agent contact new leads — SMS, email, or both? If both, which should go first?
- Should the agent send that initial acknowledgment and qualification message automatically (auto-send), or queue it for a human to review and approve before sending?
- Are there any lead types or sources where you want auto-send disabled — for example, high-value trade-in leads that should always go to a human first?

**Question 6 — Escalation contacts**

Ask:
- Who should receive alerts when a lead passes the response-time SLA without being contacted? Please provide the BDC manager's name and their preferred contact method: Slack channel, email address, or phone number for SMS.
- Who is the second-level escalation (e.g., sales manager) if the lead still hasn't been contacted after a second threshold? Same contact options apply.
- For the end-of-day lead digest, who should receive it, and in what format (email, Slack)?

---

## After Collecting Answers

Once you have all the answers, do the following:

### 1. Write the `## Your context` section in CLAUDE.md

Replace the `<!-- Filled in during onboarding -->` placeholder with a filled-in context block like this — substituting the user's actual answers:

```
## Your context

**Dealership:** [Full name]
**Type:** [New franchise / Used-only / Both]
**Service scheduling included:** [Yes / No]
**BDC / Sales manager:** [Name]

**Lead sources monitored:** [List: website forms, AutoTrader, Cars.com, CarGurus, etc.]
**Lead delivery method:** [ADF/XML to CRM / Direct API connection]
**Excluded sources:** [Any manual-only sources]

**DMS:** [CDK Global / Reynolds & Reynolds ERA-IGNITE / Reynolds FOCUS / Other]
**CRM:** [VinSolutions / Other]
**Scheduling system:** [DMS-native / Xtime / TimeHighway / Google Calendar / Other]

**First-response SLA:** [N] minutes
**After-hours handling:** [Immediate acknowledgment + queue / Wait until open]
**Business hours:** [Days and hours, timezone]

**Outreach channels:** [SMS / email / both — order: ...]
**Auto-send:** [Enabled / Disabled]
**Auto-send exceptions:** [Lead types or sources that require human review]

**First escalation:** [Name] — [Slack channel / email / SMS]
**Second escalation (sales manager):** [Name] — [Slack channel / email / SMS]
**End-of-day digest recipients:** [Name(s), email(s) or Slack]
```

### 2. Write config.json

Create `config.json` at the workspace root with the structured configuration:

```json
{
  "dealership": {
    "name": "",
    "type": "",
    "serviceSchedulingIncluded": false,
    "bdcManager": ""
  },
  "leadSources": {
    "websiteForms": true,
    "autoTrader": false,
    "carsDotCom": false,
    "carGurus": false,
    "trueCar": false,
    "inboundCallTranscripts": false,
    "tradeInTools": false,
    "deliveryMethod": "adf-xml"
  },
  "systems": {
    "dms": "",
    "crm": "",
    "schedulingSystem": ""
  },
  "sla": {
    "firstResponseMinutes": 2,
    "secondEscalationMinutes": 60,
    "afterHoursHandling": "immediate-ack-queue",
    "businessHours": {
      "timezone": "",
      "schedule": {}
    }
  },
  "outreach": {
    "channels": ["sms", "email"],
    "channelOrder": ["sms", "email"],
    "autoSend": false,
    "autoSendExceptions": []
  },
  "escalation": {
    "firstContact": {
      "name": "",
      "method": "",
      "address": ""
    },
    "secondContact": {
      "name": "",
      "method": "",
      "address": ""
    }
  },
  "digest": {
    "frequency": "daily",
    "sendTime": "18:00",
    "recipients": []
  }
}
```

Fill in all values from the onboarding answers before writing the file.

### 3. Confirm and hand off

Tell the user their configuration is saved and the agent is ready to monitor inbound leads. Then give them their first task prompt:

> "Check for any new leads from the last 24 hours and draft replies for any that haven't received a response."

Remind them they can edit `config.json` directly to adjust SLA thresholds, swap lead sources on or off, or update escalation contacts, and they can re-run `agent-onboarding` at any time to refresh the setup.
