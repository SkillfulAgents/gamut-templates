---
name: agent-onboarding
---

# Agent Onboarding

This skill runs once when the workspace is first imported. It collects the configuration needed to operate the Retail Shift / Coverage Scheduling agent for your brand, saves the answers to `config.json`, and writes a plain-text summary into the `## Your context` section of `CLAUDE.md`.

## Instructions

Greet the user and explain that you will ask 8 questions to configure the agent. Let them know answers are saved to `config.json` and written into `CLAUDE.md` so the agent has full context on every future run. Ask the questions one at a time and wait for each answer before continuing.

---

**Q1 - Brand and locations**
What is your retail brand name, and how many store locations do you manage scheduling for? Please list the location names or IDs you use internally (e.g., "Store 1 - Downtown, Store 2 - Westside Mall").

Collect: brand name, number of locations, list of location names/IDs.

**Q2 - Scheduling system**
Which scheduling system do you use: When I Work, Homebase, Deputy, or something else? If you have an API key or integration already set up, please share the connection details. If not, note the system name and we can configure the connection separately.

Collect: scheduling system name, API key or integration method if available, and whether shift assignments should be written back automatically.

**Q3 - POS system**
Which POS system do your stores use: Lightspeed Retail or Shopify POS? Do you want the agent to use POS data to flag high-traffic periods where you may need extra coverage before a callout happens? (yes/no)

Collect: POS system name, whether POS-driven demand alerting is enabled (yes/no).

**Q4 - Shift types and roles**
What are the shift types and associate roles at your stores that need coverage scheduling? For example: cashier, floor associate, floor lead, key holder, store manager. Are there any roles that require special certification or credentials before an associate can be offered that shift?

Collect: list of shift types and roles, any credentialed roles that restrict which associates qualify.

**Q5 - Outreach method**
How should the agent contact associates when a shift opens up - SMS, email, or both? If SMS, which provider do you use (e.g., Twilio, SimpleTexting, or built into When I Work)? Do you also use a shift-posting board like Snagajob or Indeed Flex for open coverage?

Collect: outreach channel (SMS / email / both), SMS provider name, whether a posting board is used (and which one).

**Q6 - Outreach window**
How many minutes should the agent wait for an associate to respond before moving to the next person on the list? The default is 20 minutes. You can set it shorter (e.g., 10 minutes for urgent same-day gaps) or longer if your associates tend to have slower response times.

Collect: outreach window in minutes (default: 20).

**Q7 - Store managers per location**
For each location, who is the store manager and what is their preferred contact for escalation alerts - SMS, email, or both? Please provide their name and contact details for each store. If there is also a district manager or regional lead who should receive escalations when a shift is within a few hours of starting, include their info as well.

Collect: per-location manager name, phone, and email; optional district manager name, phone, and email.

---

## Saving Configuration

Once all questions are answered:

1. Write a `config.json` file in the workspace root with this structure:

```json
{
  "brand": "<brand name>",
  "locations": [
    {
      "name": "<location name>",
      "id": "<internal ID>",
      "managerName": "<name>",
      "managerPhone": "<phone>",
      "managerEmail": "<email>"
    }
  ],
  "schedulingSystem": "<When I Work | Homebase | Deputy | other>",
  "schedulingApiKey": "<key or 'configure separately'>",
  "writeBackEnabled": true,
  "pos": "<Lightspeed Retail | Shopify POS>",
  "posAlertingEnabled": <true | false>,
  "shiftTypes": ["<role 1>", "<role 2>"],
  "credentialedRoles": ["<role if any>"],
  "outreachChannel": "<sms | email | both>",
  "smsProvider": "<provider name or 'not configured'>",
  "postingBoard": "<board name or 'none'>",
  "outreachWindowMinutes": <number>,
  "storeManagers": [
    {
      "location": "<location name>",
      "name": "<name>",
      "phone": "<phone>",
      "email": "<email>"
    }
  ],
  "districtManager": {
    "name": "<name or ''>",
    "phone": "<phone or ''>",
    "email": "<email or ''>"
  }
}
```

2. Open `CLAUDE.md` and replace the placeholder text inside `## Your context` with a plain-text summary of the config. Format it as labeled lines:

```
Brand: [brand name]
Locations: [number] - [location list]
Scheduling system: [name]
POS: [system] - demand alerting=[yes/no]
Shift types and roles: [list]
Credentialed roles: [list or 'none']
Outreach channel: [SMS/email/both] via [provider]
Posting board: [name or 'none']
Outreach window: [X] minutes
Store managers: [location - name - phone/email for each]
District manager: [name - contact or 'not configured']
```

3. Confirm to the user: "Setup complete. Your configuration has been saved to config.json and your context has been updated in CLAUDE.md. To start using the agent, describe a callout (e.g., 'Maria at the downtown store just called out for tomorrow 2-8pm') or ask it to check for open shifts ('Any uncovered shifts in the next 24 hours?')."
