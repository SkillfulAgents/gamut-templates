---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your HVAC/Plumbing/Electrical Shift Coverage Scheduler configured. I'll ask a few quick questions so the agent knows your business, your dispatch setup, and how you want technician coverage handled when someone calls out. This takes about 5 minutes.

---

## Business basics

1. What is your business name, and what trades do you primarily operate in — HVAC, plumbing, electrical, or a combination?
2. What city or region are you based in? (This sets the correct timezone for job alerts and dispatch windows.)
3. How many active field technicians do you have on your roster across all trade types?

---

## Scheduling system

4. Do you use ServiceTitan, FieldEdge, or another field service management platform to schedule jobs and manage technicians?
5. Is that system already connected to Gamut, or should we start from a spreadsheet roster you can share?

---

## Callout detection

6. How do your technicians currently call out when they cannot make a scheduled job — text to the dispatcher, call to the office, a ServiceTitan or FieldEdge notification, or another channel?
7. Should the agent watch a specific email inbox, phone number, or in-app notification stream to detect callouts? Please share the address or identifier so it knows where to listen.

---

## Trade certification matching

8. Do your technicians hold trade-specific licenses or certifications that determine which jobs they can cover — for example, EPA 608 certification for refrigerant work, a journeyman plumbing license, or an electrician's license?
9. Where are those certifications recorded — in ServiceTitan, FieldEdge, or a separate spreadsheet? This tells the agent where to look when filtering qualified candidates.

---

## Outreach preferences

10. What channel should the agent use to contact technicians for coverage requests — SMS, ServiceTitan in-app message, FieldEdge notification, or another method?
11. How long should the agent wait for a reply before moving to the next candidate? (Default is 20 minutes — let me know if you want something shorter or longer given the urgency of your typical callouts.)
12. Are there any blackout windows when technicians should not be contacted for coverage — for example, no texts after 9 PM or before 6 AM?

---

## Escalation and alerts

13. Who is the dispatcher or service manager to alert if a job cannot be filled? Please share their name and either an email address or Slack handle.
14. How many hours before the scheduled job start should the agent fire an unfilled-shift alert if coverage has not been confirmed? (Default is 2 hours.)
15. Where should the daily scheduling summary go — email, a Slack channel, or in-chat?

---

## After Questions Are Answered

Once all questions have been answered, do the following:

1. **Update CLAUDE.md** — fill in the `## Your context` section with a structured summary of the configuration, including: business name, trades operated, region and timezone, technician count, scheduling system and connection status, callout detection channel and identifier, certification matching enabled and source, outreach channel, wait window, blackout hours, escalation contact and method, escalation lead time, and daily summary destination.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json` with all configuration values as a JSON object using clear snake_case keys:

```json
{
  "business_name": "<business name>",
  "trades": ["hvac", "plumbing", "electrical"],
  "timezone": "<IANA timezone string>",
  "technician_count": 0,
  "scheduling_system": "servicetitan | fieldedge | csv",
  "scheduling_system_connected": true,
  "callout_channel": "sms | email | servicetitan | fieldedge",
  "callout_intake_identifier": "<email address, phone number, or stream name>",
  "certification_matching_enabled": true,
  "certification_source": "scheduling_system | spreadsheet | both",
  "outreach_channel": "sms | servicetitan | fieldedge",
  "wait_window_minutes": 20,
  "blackout_start": "21:00",
  "blackout_end": "06:00",
  "escalation_contact": "<name and email or Slack handle>",
  "escalation_lead_time_hours": 2,
  "summary_destination": "<email address or Slack channel>"
}
```

3. **Give the user their first example task prompt.** Suggest something like:

   > "A callout just came in from [tech name] — their job is at [time] tomorrow at [customer address]. Find coverage."

   or

   > "Show me all open jobs for today and flag any that still need a technician assigned."

Let them know they can also ask the agent to run the daily summary at any time, adjust candidate ranking rules, or update any configuration setting by asking in plain language.
