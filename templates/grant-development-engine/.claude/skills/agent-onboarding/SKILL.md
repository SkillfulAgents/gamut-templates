---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Grant & Development Engine configured. I'll ask a few questions about your organization, your funding portfolio, and your connected systems. This takes about 10 minutes and sets the agent up to run your full development cycle.

---

## Organization basics

1. What is your organization's legal name, and what are your primary program areas — for example, education, housing, workforce development, health, arts, environment?
2. What geographic area do you serve? (This helps filter grant prospects by geographic restrictions.)
3. What is your annual budget range? (Funders often restrict grants to organizations within a budget band.)

---

## Funder pipeline and CRM

4. Where do you currently track your grant pipeline — a spreadsheet, Salesforce NPSP, Bloomerang, Salesforce, or another CRM? Is it connected to Gamut or should we start from a spreadsheet?
5. Do you have access to a grant database like Candid/GuideStar, Instrumentl, or GrantStation? If so, which one, and do you have API or export access?

---

## Proposal library

6. Where are your past grant applications and proposals stored — Google Drive, SharePoint, Dropbox? Please share the folder path or link so the agent can search for reusable content.
7. Do you have a standard organizational narrative, program descriptions, or boilerplate sections (mission, history, financials summary) in a known location?

---

## Program data

8. Where is your current program data tracked — how many participants served, outcomes achieved, budget utilization? Is this in a spreadsheet, a program database, or a reporting tool?
9. Do you have a current-year budget template and audited financials available in a shared location?

---

## Deadlines and reporting

10. What is your current grant portfolio size (roughly how many active grants)? This helps calibrate the deadline tracking and digest volume.
11. What is the best place to post the weekly pipeline digest — a specific Slack channel, or an email address?
12. Who is the development director or team lead who should receive deadline alerts and draft reviews? Provide their name and Slack handle or email.

---

## Donor communications

13. Do you want the agent to manage major donor touchpoints and draft cultivation communications? If yes, where is your major donor list and touchpoint calendar maintained?
14. What is your target touchpoint cadence for major donors — monthly, quarterly, or based on giving level?

---

## After Questions Are Answered

Once all questions have been answered:

1. **Update CLAUDE.md** — fill in the `## Your context` section with: organization name, program areas, geography, budget range, CRM system and connection status, grant database access, proposal library location, program data location, budget/financials location, portfolio size, digest destination, development director contact, donor touchpoint management setup.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "org_name": "",
  "program_areas": [],
  "geography": "",
  "annual_budget_range": "",
  "crm_system": "salesforce_npsp | bloomerang | spreadsheet | other",
  "crm_connected": true,
  "grant_database": "candid | instrumentl | grantstation | other | none",
  "proposal_library_path": "",
  "program_data_location": "",
  "financials_location": "",
  "active_grant_count": 0,
  "digest_destination": "",
  "development_director": "",
  "manage_donor_touchpoints": true,
  "donor_list_location": "",
  "touchpoint_cadence": "monthly | quarterly | tier_based"
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Find new grant prospects for our [program area] work and add the top 5 to the pipeline."

   or

   > "Draft the application for [funder name] — the deadline is [date]."

   or

   > "Post this week's pipeline digest."
