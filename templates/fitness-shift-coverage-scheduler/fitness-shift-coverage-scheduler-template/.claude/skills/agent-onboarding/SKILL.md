---
name: agent-onboarding
---

# Agent Onboarding

Welcome! I'm your Gamut shift coverage scheduling agent. I'll ask you a few questions to configure coverage monitoring for your business. This takes about 5 minutes and you only do it once.

---

## Business Basics

1. What is your business name and type? (For example: Sunrise Yoga Studio, hair salon, med spa, boxing gym.)
2. What city are you in, and what timezone does your business operate in?
3. Roughly how many instructors or service providers are on your roster?

---

## Scheduling System

4. Do you use Mindbody, Boulevard, or another scheduling platform?
5. Is that platform already connected to Gamut, or should we start by importing a roster CSV?

---

## Callout Detection

6. How do your staff currently call out — text to a manager, email, through Mindbody or Boulevard, or some other channel?
7. Should the agent watch a specific inbox, phone number, or notification stream for callouts? If so, which one?

---

## Skill and Certification Matching

8. Do you need the agent to match substitutes by class type or service skill — for example, only certified hot yoga instructors can cover hot yoga classes?
9. Where are those certifications or skill qualifications recorded — in Mindbody, Boulevard, or a separate spreadsheet?

---

## Outreach Preferences

10. What channel should the agent use to contact staff when a shift opens — SMS, Mindbody in-app message, Boulevard message, or another method?
11. How long should the agent wait for a reply before moving to the next candidate? (Default is 20 minutes — just confirm or give a different number.)
12. Are there any blackout hours when staff should not be contacted, regardless of shift urgency? (For example, no texts before 7 AM or after 10 PM.)

---

## Escalation and Alerts

13. Who is the manager to notify if coverage fails? Please share their email address or Slack handle.
14. How many hours before the class or appointment start should the agent send the unfilled-shift alert? (Default is 2 hours — confirm or adjust.)

---

## After Questions Are Answered

Once the user has answered the questions above, do the following:

1. **Write configuration to CLAUDE.md.** Append the collected answers under the `## Your context` section in CLAUDE.md, formatted as clean markdown with labeled fields (business name, type, timezone, roster size, scheduling system, callout channel, callout intake target, certification matching enabled, certification source, outreach channel, escalation window in minutes, blackout hours, manager contact, manager alert channel, unfilled alert threshold in hours).

2. **Create config.json** in the workspace root with the same values as structured JSON, using the field names defined in the CLAUDE.md Configuration Reference section.

3. **Confirm setup and give the user their first example prompt.**

Tell the user:

> You're all set. Here's a prompt to try right now:
>
> "We just got a callout for the [class name] at [time] — find a sub and send outreach."
>
> Or, if you want to test the system before a real callout:
>
> "Run a dry-run coverage search for tomorrow's 10 AM class and show me the ranked candidate list without sending any messages."
