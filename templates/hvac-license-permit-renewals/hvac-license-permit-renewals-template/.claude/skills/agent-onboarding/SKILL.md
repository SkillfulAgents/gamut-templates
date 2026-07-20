---
name: agent-onboarding
---

# Agent Onboarding

Welcome — this agent tracks every license, certification, insurance certificate, and vehicle registration across your technician team, and makes sure nothing lapses quietly. Let's get it configured for your business.

Work through the questions below at whatever pace you like. You can answer everything now or come back to fill in gaps later.

---

## Section 1: Business basics

1. What is your business name, and what trade(s) do you operate in — HVAC, plumbing, electrical, or a combination?
2. Which state(s) do you operate in? (Licensing requirements vary by state, so this helps track the right boards.)
3. How many licensed technicians are on your team right now?
4. Do you have multiple business entities — for example, a separate HVAC entity and a plumbing entity with different license numbers?

---

## Section 2: Credential inventory

5. Which credential types do you currently need to track? Common ones include:
   - State contractor license (HVAC, plumbing, electrical)
   - EPA 608 certification (Type I, II, III, or Universal)
   - NATE certification
   - Journeyman or master trade license
   - Liability insurance COI
   - Workers' compensation COI
   - Vehicle registrations
   - Municipal or county trade permits
   - Anything else?
6. Do you have an existing spreadsheet, document, or system listing your techs' credentials and expiry dates? If so, share it and the agent will use it for initial setup.
7. Are credentials currently stored in ServiceTitan, FieldEdge, or somewhere else?

---

## Section 3: Reminder preferences

8. The default reminder schedule is 90, 60, 30, and 14 days before expiration. Does that work for you, or would you like to adjust any of those intervals?
9. For liability insurance COIs — is there a client, lender, or property manager who needs to be listed as certificate holder on renewals? If so, who manages that relationship?

---

## Section 4: Escalation

10. If a tech's credential lapses without a renewal recorded, who should be notified immediately — you, your office manager, or both? Please provide their names and contact info (email or Slack handle).
11. If you are connected to ServiceTitan or FieldEdge, should the agent automatically flag that tech's upcoming jobs for reassignment when a credential lapses?

---

## Section 5: Reporting and delivery

12. Who should receive the renewal reminders — the technician directly, the office, or both?
13. Should reminders go by email, Slack, or both? If email, provide addresses. If Slack, provide channel or handle.
14. How often do you want the compliance summary — on-demand only when you ask for it, or also as a recurring monthly digest?

---

## After questions are answered

Once the user has answered the questions above, do the following:

1. **Write configuration to CLAUDE.md.** Populate the `## Your context` section at the bottom of CLAUDE.md with a structured summary of everything collected: business name and trade, operating states, technician count, entities, credential types to track, initial credential inventory (or note that import is pending), ServiceTitan/FieldEdge connection status, reminder intervals, escalation contacts, reminder delivery channel and recipients, and compliance summary frequency.

2. **Create config.json.** Write a `config.json` file in the workspace root with the same information in structured JSON form. Include keys for: `businessName`, `trades`, `states`, `technicianCount`, `entities`, `credentialTypes`, `integrations` (servicetitan, fieldedge — connected true/false), `reminderIntervals` (array of days), `escalationContacts` (array of name/contact objects), `reminderRecipients`, `reminderChannel`, `complianceSummarySchedule`.

3. **Give the user their first example task prompt.** After confirming setup is complete, suggest:

> "Show me all credentials expiring in the next 90 days" — or — "Add EPA 608 Universal for [Tech Name], expires [MM/DD/YYYY], license number [number]."
