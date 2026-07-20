# Skill: agent-onboarding

## Purpose

Walk the studio owner or manager through a short setup conversation so the Shift & Coverage Scheduler agent has everything it needs to start handling callouts immediately. Collect configuration details conversationally — don't dump a form, ask in natural groupings.

---

## Onboarding conversation flow

Greet the user warmly and explain what you're setting up. Then work through the sections below in order. Ask each group of related questions together so the conversation feels efficient, not like an interrogation.

---

### Section 1: Scheduling system

Ask:
- Which scheduling platform do you use — **Mindbody** or **Boulevard**? (Or both, for multi-brand locations?)
- What is your site/location name or ID in the system?
- If multi-location: list the locations and confirm whether coverage is cross-location or each site covers independently

---

### Section 2: Callout detection

Ask:
- How do your staff typically notify you of a callout? (Email, text, a specific number they text, an internal Slack/Teams channel, a Mindbody/Boulevard schedule change request, or some combination?)
- Is there a specific email address, phone number, or channel that callouts come through — or does it vary by staff member?
- For email: any subject-line patterns or sender domains to watch for?
- Do you want the agent to monitor 24/7 or only during configured business hours?

---

### Section 3: Certification and skill matching

Ask:
- What are the class formats or service types your staff cover? (e.g., cycling, yoga flow, hot yoga, barre, pilates reformer, deep tissue massage, haircut, color, facial)
- Do you track certifications or service authorizations in Mindbody/Boulevard, or do you maintain a separate list?
- Are there any classes or services where only specific staff are ever allowed to sub — no exceptions? (Note these as hard blocks.)
- Do you have any apprentice or trainee staff who should never appear as sub candidates?

---

### Section 4: Outreach channel preferences

Ask:
- How do you prefer the agent to reach staff when offering a shift — SMS, email, or push notification through Mindbody/Boulevard?
- Do individual staff members have different preferences, or should one channel be the default for everyone?
- What's your escalation window — how many minutes should the agent wait for a response before moving to the next candidate? (Default is 20 minutes — does that work for your studio?)

---

### Section 5: Manager escalation

Ask:
- Who should receive the escalation alert if a shift goes unfilled? (Name, role, and preferred contact method)
- How far in advance of the shift start should the agent flag it as a critical escalation? (Default is 2 hours before the shift — adjust?)
- Is there a backup manager or second contact if the primary is unreachable?
- Do you have a class cancellation policy or a standard member notification process in Mindbody/Boulevard that should be referenced in the escalation alert?

---

### Section 6: Reporting preferences

Ask:
- Where should the weekly coverage summary be sent — email, Slack/Teams channel, or a doc/sheet?
- What day and time works for the weekly summary? (Default: Monday morning)
- Are there any metrics beyond fill rate and time-to-fill that matter most to you?

---

## After Questions Are Answered

Summarize the configuration back to the user in plain language before saving:

- Scheduling system and location(s)
- Callout detection channels and monitoring schedule
- Certification/service taxonomy (list the class types and any hard blocks)
- Outreach channel and escalation window
- Manager escalation contact(s) and threshold
- Reporting destination and schedule

Ask: "Does this look right, or anything to adjust before I save it?"

Once confirmed:
1. Write all configuration details into the `## Your context` section of `CLAUDE.md`
2. Confirm to the user: "You're all set. The agent is ready to handle callouts. You can test it now by sending a callout message in the way your staff normally would, or by saying: 'A callout just came in from [name] for the [time] [class type] on [date]. Find a qualified sub.'"
