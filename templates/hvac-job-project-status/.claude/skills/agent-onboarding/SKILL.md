# agent-onboarding

You are onboarding a trade contractor — HVAC, plumbing, or electrical — onto the Job / Project Status agent. Your goal is to gather everything the agent needs to pull open jobs, flag at-risk work correctly, and deliver a daily ops brief that's immediately useful to the dispatcher or owner. Ask questions conversationally, one section at a time. Do not present the full list at once.

---

## Section 1: Trade type and business profile

Start here to understand the scale and nature of the operation.

- What trade(s) does the business run? (HVAC, plumbing, electrical, or multi-trade?)
- Is the work primarily residential service, commercial, new construction, or a mix?
- Roughly how many open jobs are active at any given time?
- How many technicians are in the field on a typical day?
- Is there a dedicated dispatcher, or does the owner or office manager handle scheduling?

---

## Section 2: Field service platform

Determine which platform holds the job data and confirm connectivity.

- Are you running ServiceTitan or FieldEdge? (Or another platform?)
- Do you have API access or an integration token available, or will you need help setting that up?
- How is job status tracked — do techs update status in the mobile app, or does the office update it?
- Are permits and POs tracked inside ServiceTitan/FieldEdge, or in a separate system?

---

## Section 3: Job volume and risk thresholds

Calibrate what counts as "at risk" for this business.

- How many days without a status update should trigger a "stalled" flag? (Default is 3 days — is that right for your business, or do some job types naturally take longer?)
- Are there job types (e.g., large commercial installs, planned maintenance with multi-week lead times) that should be excluded from the stall flag?
- What is your definition of "behind schedule" — past the estimated completion date, or past the scheduled appointment date?
- Do you have jobs with hard SLA deadlines (service agreement customers, emergency response contracts)?

---

## Section 4: Commercial vs. residential prioritization

Understand how to rank urgency across the job mix.

- Do you have commercial customers or service agreement (maintenance contract) customers?
- If so, can you list the key commercial accounts or describe how they're tagged in ServiceTitan/FieldEdge?
- Do service agreement customers have specific response time or completion time SLAs written into their contracts?
- Should commercial and service-agreement jobs always surface first in the daily brief, regardless of how overdue they are?
- Are there residential customers who should be treated as high-priority (e.g., property managers with multiple addresses)?

---

## Section 5: Parts and permits

Flag the most common sources of job delays specific to this business.

- How are parts orders tracked — through ServiceTitan/FieldEdge POs, or a separate supplier portal?
- Which suppliers do you use most, and are any of them known for frequent backorder issues?
- What trade permits are most common for your work? (HVAC mechanical permits, plumbing permits, electrical permits, low-voltage?)
- Is permit status tracked inside ServiceTitan/FieldEdge, or in a separate system or spreadsheet?
- Who pulls permits — the office, the tech, or a third party?

---

## Section 6: Daily brief format and delivery

Determine how and when the brief gets delivered.

- What time should the daily brief be ready? (e.g., 6:30am so the dispatcher has it before the first call?)
- Who receives the brief — dispatcher, owner, office manager, or all of them?
- How should the brief be delivered — pasted into the chat, drafted as an email, posted to a Slack channel?
- How many flagged jobs should appear in the brief before the agent offers to show the full list? (Default: all flagged jobs if under 10, offer to expand if more.)
- Any job information that should never appear in the brief for privacy or customer reasons?

---

## Section 7: Weekly summary preferences

- What day and time should the weekly summary be delivered?
- Should the weekly summary go to the same recipients as the daily brief, or a wider group (e.g., ownership)?
- Is average days-to-close tracked anywhere currently, or will this be a new metric?
- Are there specific patterns you've already noticed (a tech who frequently has stalled jobs, a part that's always on backorder) that the agent should watch for from day one?

---

## After Questions Are Answered

Once all sections are complete:

1. Summarize what you've learned: trade type, platform, job volume, stall threshold, commercial account list, brief delivery time and channel, and escalation preferences.
2. Ask the user to confirm or correct the summary.
3. Write the confirmed details into the `## Your context` section of `CLAUDE.md` — filling in every relevant field so the agent is fully configured.
4. Confirm that onboarding is complete and tell the user their first suggested task: "Pull today's open jobs and show me the daily ops brief."
