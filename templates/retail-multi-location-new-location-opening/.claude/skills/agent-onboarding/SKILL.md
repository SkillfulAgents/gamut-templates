---
name: agent-onboarding
---

# Agent Onboarding

This skill runs once when the workspace is first imported. It collects the configuration needed to operate the Retail New-Location Opening agent for your brand, saves the answers to `config.json`, and writes a plain-text summary into the `## Your context` section of `CLAUDE.md`.

## Instructions

Greet the user and explain that you will ask 8 questions to configure the agent. Let them know answers are saved to `config.json` and written into `CLAUDE.md` so the agent has context on every future run. Ask the questions one at a time and wait for each answer before continuing.

---

**Q1 - Brand and concept**
What is your retail brand name and what type of store is it (e.g., apparel, home goods, specialty food, beauty, sporting goods)? Also, how many locations do you currently operate?

Collect: brand name, store concept/category, current number of locations.

**Q2 - POS system**
Which POS system do you use: Lightspeed Retail or Shopify POS? If Lightspeed, which plan are you on (e.g., Standard, Advanced)? If Shopify POS, which plan (Lite or Pro)? Please also confirm whether you already have multiple locations set up in the system.

Collect: POS system name (Lightspeed or Shopify POS), plan/version, and whether multi-location is already configured.

**Q3 - Opening date and address**
What is the target opening date for the new location, and what is the store address (including city and state)?

Collect: target opening date (format: YYYY-MM-DD), full address, city, state.

**Q4 - Permitting jurisdiction**
Which city and state will this location be in for permitting purposes? Are there any known permit complexities for this jurisdiction (e.g., slow CO process, strict signage rules, required health inspection)?

Collect: jurisdiction (city, state/province), any known permitting flags.

**Q5 - Key vendors and lead times**
Who are your primary vendors for the initial inventory order, and what are their typical lead times? Please list the top 2-4 vendors with an estimated delivery window (e.g., "Vendor A - 30 days, Vendor B - 45 days").

Collect: list of key vendors and their lead times in days.

**Q6 - Scheduling and HR system**
Which scheduling or HR system will you use to staff the new location? Examples: When I Work, Homebase, Deputy, ADP, or a custom system. If you use multiple systems (one for scheduling, one for payroll), please name both.

Collect: scheduling system name, HR/payroll system name (may be the same).

**Q7 - Pre-opening marketing approach**
What is your marketing plan for this opening? Will you do a soft launch before the grand opening, a grand opening event, or both? Do you use email and SMS for customer announcements, and if so, which platforms (e.g., Klaviyo, Mailchimp, Attentive)?

Collect: soft launch (yes/no), grand opening event (yes/no), email platform, SMS platform (or "not configured").

**Q8 - Alert recipients**
Who should receive the daily opening brief and escalation alerts? Please provide the name and email (or phone number for SMS) for: (a) the opening project lead, and (b) the district manager or executive sponsor overseeing this opening.

Collect: opening lead name + email, district manager/sponsor name + email.

---

## Saving Configuration

Once all questions are answered:

1. Write a `config.json` file in the workspace root with this structure:

```json
{
  "brand": "<brand name>",
  "storeConcept": "<store type/category>",
  "existingLocations": <number>,
  "pos": "<Lightspeed Retail | Shopify POS>",
  "posPlan": "<plan or version>",
  "openingDate": "<YYYY-MM-DD>",
  "address": "<full address>",
  "city": "<city>",
  "state": "<state/province>",
  "jurisdiction": "<city, state>",
  "jurisdictionFlags": "<any known permit complexities or 'none'>",
  "vendors": [
    { "name": "<vendor name>", "leadTimeDays": <number> }
  ],
  "schedulingSystem": "<system name>",
  "hrSystem": "<system name>",
  "softLaunch": <true | false>,
  "grandOpeningEvent": <true | false>,
  "emailPlatform": "<platform name or 'not configured'>",
  "smsPlatform": "<platform name or 'not configured'>",
  "alertRecipients": {
    "openingLead": { "name": "<name>", "email": "<email>" },
    "districtManager": { "name": "<name>", "email": "<email>" }
  }
}
```

2. Open `CLAUDE.md` and replace the placeholder line inside `## Your context` with a plain-text summary. Format it as labeled lines:

```
Brand: [brand name] - [store concept]
Existing locations: [number]
POS: [system] ([plan])
Target opening date: [date]
Address: [full address]
Jurisdiction: [city, state] - [any permit flags]
Key vendors: [vendor list with lead times]
Scheduling system: [name]
HR/payroll system: [name]
Marketing: Soft launch=[yes/no] | Grand opening event=[yes/no] | Email=[platform] | SMS=[platform]
Opening lead: [name] - [email]
District manager: [name] - [email]
```

3. Confirm to the user: "Setup complete. Your configuration has been saved to config.json and your context has been updated in CLAUDE.md. To start your first opening project, say: Start a new opening for [Store Name] at [Address], opening [Target Date]."
