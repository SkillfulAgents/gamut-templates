---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Cleaning/Janitorial Shift Coverage Scheduler configured. I'll ask a few quick questions so the agent knows your business, your scheduling setup, and how you want coverage handled. This takes about 5 minutes.

---

## Business basics

1. What is your business name, and what type of cleaning services do you primarily offer — residential, commercial, or both?
2. What city or region are you based in? (This sets the correct timezone for shift alerts.)
3. How many active staff do you schedule across all locations?

---

## Scheduling system

4. Do you use Swept, Janitorial Manager, or another scheduling tool to manage shifts and staff?
5. Is that system already connected to Gamut, or should we start from a spreadsheet roster you can share?

---

## Callout detection

6. How do your staff currently call out when they cannot make a shift — text to a shared number, email, a Swept notification, or another channel?
7. Should the agent watch a specific email inbox, phone number, or in-app notification stream for callouts? Please share the address or identifier.

---

## Outreach preferences

8. What channel should the agent use to contact staff for coverage — SMS, Swept in-app message, or another?
9. How long should the agent wait before moving to the next candidate if there is no reply? (Default is 20 minutes — let me know if you want something different.)
10. Are there any blackout windows when staff should not be contacted for coverage requests — for example, after 9pm or before 7am?

---

## Escalation and alerts

11. Who is the manager to alert if a shift cannot be filled? Please share their name and either an email address or Slack handle.
12. How many hours before shift start should the manager alert fire if the shift is still unfilled? (Default is 2 hours.)
13. Where should the daily scheduling summary go — email, Slack channel, or in-chat?

---

## After Questions Are Answered

Once all questions have been answered, do the following:

1. **Update CLAUDE.md** — fill in the `## Your context` section with a structured summary of the configuration, including: business name, service type, region/timezone, staff count, scheduling system and connection status, callout detection channel and identifier, outreach channel, wait window, blackout hours, escalation contact and method, escalation lead time, and daily summary destination.

2. **Create config.json** in the workspace root with all configuration values as a JSON object, using clear snake_case keys (e.g., `business_name`, `scheduling_system`, `callout_channel`, `outreach_channel`, `wait_window_minutes`, `blackout_start`, `blackout_end`, `escalation_contact`, `escalation_lead_time_hours`, `summary_destination`).

3. **Give the user their first example task prompt.** Suggest something like:

   > "A callout just came in from [staff name] — their shift is at [time] tomorrow at [location]. Find coverage."

   or

   > "Show me all open shifts for this week and flag any that still need coverage."

Let them know they can also ask the agent to run the daily summary at any time, adjust the candidate ranking rules, or update any configuration setting by asking in plain language.
