# Skill: agent-onboarding

## Purpose

Walk a new user through configuring the License / Permit / Cert Renewals agent for their trade contracting business. Gather everything needed to start tracking credentials accurately — trade type, states, tech roster, existing credentials, reminder preferences, escalation rules, and field software connections — then write the configuration to `CLAUDE.md` and `config.json`.

Run this skill automatically when the workspace is first opened, before any other tasks are attempted.

---

## Onboarding Sections

Work through the following sections in order. Ask each section's questions conversationally — don't dump all questions at once. Confirm answers before moving on.

---

### Section 1: Business Basics

Understand the shape of the business.

**Questions to ask:**

1. What trade(s) does your company work in? (HVAC, plumbing, electrical, or a combination)
2. Which states do you operate in — and do you hold separate licenses in each, or just one home state?
3. How many field technicians are on your roster right now? (Approximate is fine — we can add names in the next section.)
4. What's your company name, and who should be the primary contact for compliance alerts (owner, office manager, or both)?

---

### Section 2: Credential Inventory

Load the existing credential records. Give the user two options:

**Option A — Import from spreadsheet or document**
Ask them to paste in a CSV, table, or list of existing credentials. Accept any format and parse it into the registry structure. Confirm each record before saving.

**Option B — Enter manually**
For each tech (and the business entity), step through:
- State contractor license
- EPA 608 cert (HVAC techs only — ask for type: Type I, II, III, or Universal)
- NATE certifications (ask specialty area and expiry — NATE certs renew every 2 years)
- Journeyman / master license (plumbing and electrical)
- Any municipal/county trade permits the business holds

Also capture business-level credentials:
- General liability COI (carrier, policy number, expiry)
- Workers' comp COI (carrier, policy number, expiry)
- Vehicle registrations for company vehicles

Tell the user: "We can always add missing credentials later — just say 'add a credential for [tech name]' at any time."

---

### Section 3: Reminder Preferences

Set up how and when alerts are sent.

**Questions to ask:**

1. The default reminder windows are 90, 60, 30, and 14 days before expiration. Does that work for your business, or would you like to adjust any of those?
2. How should reminders be delivered? Options: email (paste address), Slack (channel or DM), or SMS (phone number). You can use more than one.
3. Do you want reminders sent directly to the tech whose credential is expiring, to a central office contact, or both?

---

### Section 4: Escalation Rules

Define what happens when something lapses.

**Questions to ask:**

1. If a credential expires without a renewal recorded, who should receive the immediate alert? (Name and contact — this should be the owner or operations manager, not just the tech.)
2. When a tech is flagged as non-deployable due to a lapsed credential, should the agent automatically suggest reassignment options, or just flag it for a human to handle?
3. Are there any credential types where you want earlier escalation — for example, should master licenses escalate at 30 days instead of 14?

---

### Section 5: ServiceTitan / FieldEdge Connection

Check whether job-conflict detection should be enabled.

**Questions to ask:**

1. Are you using ServiceTitan or FieldEdge to manage your jobs and dispatch?
2. If yes: do you want the agent to cross-reference upcoming job assignments when a credential lapses or hits the 14-day alert window? (This surfaces conflicts like a tech with a lapsed EPA 608 card assigned to a refrigerant recovery job.)
3. If connecting field software: provide your API credentials or confirm the integration is already set up in Gamut's integrations panel.

If the user isn't connecting field software right now, note: "You can add this later — just say 'connect ServiceTitan' or 'connect FieldEdge' and we'll set it up."

---

### Section 6: Reporting Delivery

Configure compliance report output.

**Questions to ask:**

1. How often would you like a standing compliance summary — weekly, monthly, or only on demand?
2. Who should receive standing reports? (Email addresses or Slack channels)
3. Is there a specific format your insurance provider or clients request for COI or license verification? (If yes, note any formatting requirements.)

---

## After Questions Are Answered

Once all sections are complete:

**1. Write `## Your context` to CLAUDE.md**

Append a filled-in `## Your context` section to the bottom of `CLAUDE.md`. Include:
- Company name
- Primary trade(s) and states of operation
- Tech roster (names and roles)
- All credential records collected
- Reminder windows and delivery channel
- Escalation contact
- Field software connection status
- Reporting schedule

Example format:

```
## Your context

**Company:** Riverside Mechanical LLC
**Trade:** HVAC and plumbing
**States:** Texas, Oklahoma
**Tech count:** 8 field technicians

**Credential registry:**
[Structured list of all credentials entered during onboarding]

**Reminder windows:** 90 / 60 / 30 / 14 days
**Reminder channel:** Email → ops@riversidehvac.com
**Escalation contact:** Owner — Dave Kowalski, dave@riversidehvac.com
**Field software:** ServiceTitan (job-conflict check enabled)
**Standing reports:** Monthly, emailed to owner
```

**2. Create `config.json`**

Write a `config.json` file at the workspace root with the structured configuration:

```json
{
  "company": "<company name>",
  "trade": ["<trade1>", "<trade2>"],
  "states": ["<state1>", "<state2>"],
  "techs": [
    { "name": "<tech name>", "role": "<journeyman|master|apprentice>" }
  ],
  "reminder_windows_days": [90, 60, 30, 14],
  "escalation_contact": {
    "name": "<name>",
    "email": "<email>",
    "phone": "<phone>"
  },
  "reminder_channel": "<email|slack|sms>",
  "field_software": "<servicetitan|fieldedge|none>",
  "job_conflict_check": true,
  "report_frequency": "<weekly|monthly|on_demand>",
  "report_recipients": ["<email or channel>"]
}
```

**3. Give the first example task**

End onboarding with a concrete next step:

"You're all set. Here are a few things you can ask me:
- 'Show me all credentials expiring in the next 60 days'
- 'Add EPA 608 Universal cert for [tech name], cert number [X], expires [date]'
- 'Marcus's NATE cert just renewed — new expiry is 2028-06-01, cert number NATE-44821'
- 'Generate a compliance summary for our insurance renewal'
- 'Are any techs with lapsed credentials assigned to jobs next week?'"
