---
name: agent-onboarding
---

# Agent Onboarding

You are running the onboarding flow for the Restaurant/QSR New-Location Opening agent. Ask the user each question below, one at a time, in a conversational way. Wait for a clear answer before moving to the next question. When all questions are answered, save the results to `config.json` and update the "## Your context" section in `CLAUDE.md`.

---

## Questions to ask

1. **Location name and address**
   "What is the name of this location and its full address (street, city, state, zip)? This will be used as the project title throughout the opening checklist."

2. **Target opening date**
   "What is the target opening date for this location? And do you have a soft-open date planned? If so, what is it?"

3. **Toast POS account**
   "Is Toast POS already set up for this new location, or does the account still need to be created? If it exists, what is the location name or ID in Toast so I can reference it?"

4. **7shifts account**
   "Has the new location been added to 7shifts yet? If yes, what is the location name in 7shifts? If no, I will flag account creation as the first staffing task."

5. **Google Business Profile and Yelp status**
   "Have the Google Business Profile and Yelp listing been claimed for this location yet? If yes, are they currently live or set to 'Coming Soon'?"

6. **Opening manager or project lead**
   "Who is the primary person responsible for this opening? Please share their name, role, and preferred contact method (email or phone) so I can tag them on escalations and blockers."

7. **Headcount targets**
   "What is the expected headcount at opening - roughly how many FOH, BOH, and management positions need to be filled? This helps me flag staffing shortfalls early."

8. **Current permit status**
   "Where are you in the permitting process? For example: have any permits been applied for, are any already approved, or is permitting not yet started?"

---

## After collecting all answers

1. Save the answers to `config.json` in this format:

```json
{
  "locationName": "...",
  "locationAddress": "...",
  "targetOpeningDate": "...",
  "softOpenDate": "...",
  "toastStatus": "...",
  "toastLocationId": "...",
  "7shiftsStatus": "...",
  "7shiftsLocationName": "...",
  "googleBusinessProfileStatus": "...",
  "yelpStatus": "...",
  "openingManager": {
    "name": "...",
    "role": "...",
    "contact": "..."
  },
  "headcountTargets": {
    "foh": "...",
    "boh": "...",
    "management": "..."
  },
  "permitStatus": "..."
}
```

2. Update the "## Your context" section at the bottom of `CLAUDE.md` with a human-readable summary in this format:

```
## Your context

**Location:** [Name] - [Address]
**Target opening date:** [date]
**Soft open date:** [date or "Not set"]

**Toast POS:** [status and location ID if available]
**7shifts:** [status and location name if available]
**Google Business Profile:** [status]
**Yelp:** [status]

**Opening manager:** [Name], [Role] - [contact]

**Headcount targets:** [FOH count] FOH, [BOH count] BOH, [management count] management

**Permit status:** [summary]
```

3. Confirm to the user that setup is complete and tell them what to do next: "You're all set. Start with: 'Give me today's opening checklist status' or 'What are the blockers I need to act on today?'"
