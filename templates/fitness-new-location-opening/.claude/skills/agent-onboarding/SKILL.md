# Skill: agent-onboarding

## Purpose

Walk the owner through a conversational setup interview to gather everything the New-Location Opening agent needs to manage the project. Ask questions in a natural, grouped conversation — not a form dump. At the end, write the configuration to CLAUDE.md and create config.json, then give the owner their first ready-to-use task prompt.

---

## How to Run This Skill

When the user types `run agent-onboarding`, begin the onboarding conversation below. Work through each section conversationally, pausing for answers before moving to the next group. You do not need to ask every sub-question if the owner has already answered it in passing.

---

## Onboarding Questions

### Section 1 — Business Basics

Start here:

> "Welcome — let's get your new location project set up. I'll ask a few questions so I can build your opening checklist and start tracking everything. This should take about 5 minutes.
>
> First, tell me about the business and the new location:"

Ask:
1. What is the name of your business? (brand name)
2. What type of business is it? (fitness studio, yoga/pilates, gym, hair salon, barbershop, blow-dry bar, nail salon, spa, med spa, or other — pick the closest)
3. What is the name or address of the new location? (e.g., "Downtown Denver" or "123 Main St")
4. What is your target opening date? (or a target month if the exact date is not set)
5. Have you signed the lease yet, or is that still in progress?
6. Is this your first location, or are you expanding from an existing location?

---

### Section 2 — Opening Checklist Scope

> "Now let me understand the scope of work so I can build the right checklist."

Ask:
1. Is the space a new build-out (raw shell) or an existing fitness/salon/spa space that just needs some refresh?
2. Do you have a general contractor already selected, or is that TBD?
3. Are you aware of any permits you'll need — for example, a certificate of occupancy, health department license, cosmetology board license, or signage permit?
4. How many staff do you expect to hire for this location? (rough range is fine — e.g., 5–10)
5. Are you planning a pre-sale membership or founding member campaign before opening? If yes, do you have a goal number in mind?

---

### Section 3 — Systems and Software

> "Let's talk about your booking and management software."

Ask:
1. Which platform do you use for scheduling and client management — Mindbody, Boulevard, or something else?
2. Do you already have an account, or will this be a new account for the new location?
3. Has the new location been added to your Mindbody/Boulevard account yet, or does that still need to happen?
4. Who on your team handles the software setup — you, a manager, or your software rep?
5. Have you scheduled an onboarding call with your Mindbody or Boulevard account rep for the new location? (If no, I'll remind you when the time comes.)

---

### Section 4 — Team and Ownership

> "A few quick questions about who owns what."

Ask:
1. Who is the primary owner or project lead for this opening? (name — could be you or a GM)
2. Is there a manager or ops lead who will handle day-to-day vendor and contractor coordination?
3. Who handles marketing and pre-sale campaigns — you, a staff member, or an agency?
4. Are there any other key stakeholders I should know about (e.g., a business partner, a contractor you've already committed to)?

---

### Section 5 — Communication Preferences

> "Last section — how do you want to work with this agent."

Ask:
1. How often do you want your Opening Brief? (Daily is the default; you can also choose every 2 days or on-demand only.)
2. Are there any workstreams you want me to skip or deprioritize? (e.g., "I already have the vendor side handled — focus on staffing and systems.")
3. Is there anything unusual about this opening I should know about? (e.g., unusual permit requirements, a very aggressive timeline, a key vendor you're locked into)

---

## After Questions Are Answered

Once all sections are complete:

### Step 1 — Write ## Your context to CLAUDE.md

Append the following section to the bottom of CLAUDE.md, replacing the `<!-- Filled in during onboarding -->` placeholder:

```
## Your context

**Business:** [Business name] — [Business type]
**New location:** [Location name/address]
**Target opening date:** [Date or month]
**Lease signed:** [Yes / Not yet]
**This is location #:** [1 / 2 / etc.]

**Space type:** [New build-out / Existing space refresh]
**General contractor:** [Name or TBD]
**Permits needed:** [List or "TBD — to be identified in checklist"]
**Hiring target:** [N staff]
**Pre-sale campaign:** [Yes — goal: N members / No / TBD]

**Software platform:** [Mindbody / Boulevard / Other]
**Account status:** [Existing account — new location to add / New account needed]
**Location added to platform:** [Yes / No — pending]
**Software setup owner:** [Name]
**Onboarding call scheduled:** [Yes / No]

**Project lead:** [Name]
**Ops/vendor coordinator:** [Name or same as above]
**Marketing lead:** [Name or agency]

**Brief frequency:** [Daily / Every 2 days / On-demand]
**Deprioritized workstreams:** [None / List]
**Special notes:** [Any unusual factors noted]
```

### Step 2 — Create config.json

Create a file at `config.json` in the workspace root with the following structure:

```json
{
  "business_name": "[Business name]",
  "business_type": "[Business type]",
  "new_location": {
    "name": "[Location name]",
    "address": "[Address if provided]",
    "target_opening_date": "[Date]",
    "lease_signed": true
  },
  "platform": "[mindbody|boulevard|other]",
  "platform_account_status": "[existing|new]",
  "location_added_to_platform": false,
  "pre_sale": {
    "active": true,
    "goal": 0,
    "current_count": 0
  },
  "team": {
    "project_lead": "[Name]",
    "ops_coordinator": "[Name]",
    "marketing_lead": "[Name]"
  },
  "brief_frequency": "daily",
  "deprioritized_workstreams": [],
  "task_owners": {},
  "vendor_contacts": [],
  "owner_decisions": [],
  "special_notes": "[Any notes]"
}
```

Fill in all values from the onboarding answers. Set `pre_sale.active` to `false` if no pre-sale campaign is planned. Set `pre_sale.goal` to the number the owner provided, or `0` if TBD.

### Step 3 — Give the First Example Task Prompt

Close onboarding with:

> "You're all set. Here's your first task — just send this (or something like it) to get started:
>
> **'Build the full opening checklist for [location name]. Opening target is [date]. Start with Phase 1 and Phase 2 and flag anything with a long lead time that I need to kick off this week.'**
>
> I'll generate your phased checklist, pre-populate the deadlines working backward from [date], and flag the first critical path items for you to act on today."
