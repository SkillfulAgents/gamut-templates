---
name: agent-onboarding
---

# Agent Onboarding

Welcome — I'm going to ask you a few quick questions so I can configure your Job / Project Status agent. This takes about three minutes and I only ask once. After that, every morning brief will be tailored to your shop.

---

## Business basics

1. What is your business name, and what trade(s) do you run — HVAC, plumbing, electrical, or a combination?
2. What city and timezone are you in?
3. Do you serve residential customers, commercial customers, or both?
4. Roughly how many open jobs are on your board at any given time?

---

## Field service platform

5. Do you use ServiceTitan, FieldEdge, or another platform for your job board?
6. Is it already connected to Gamut? If not, can you export an open job report (CSV or similar) each morning?

---

## Risk thresholds

7. How many days past the estimated completion date should a job be flagged as "behind"? (Default: 1 day.)
8. How many days without a status update before a job is flagged as "stalled"? (Default: 3 days.)
9. Should commercial and service-agreement jobs be ranked above residential in the brief, or do you want everything sorted purely by days overdue?

---

## Brief delivery

10. Who should receive the daily ops brief — the dispatcher, the owner, or both? Please share their names and, if email or Slack, their addresses or handles.
11. What time should the brief arrive? (Default: 7:00 AM local.)
12. How should I deliver it — email, Slack, or in-chat?

---

## Weekly summary

13. Who gets the weekly summary, and on what day and time would you like it?
14. Are there any job types that should be excluded from risk flagging — for example, maintenance contracts with flexible timelines?

---

## After Questions Are Answered

Once the user has answered the questions above, do the following:

1. **Write their configuration to CLAUDE.md.** Populate the `## Your context` section at the bottom of `CLAUDE.md` with a clean summary of everything collected:
   - Business name and trade(s)
   - City and timezone
   - Customer segments (residential / commercial / both)
   - Typical open job count
   - Field service platform and connection status
   - Behind-schedule threshold (days)
   - Stalled threshold (days)
   - Commercial/service-agreement priority preference
   - Daily brief recipients, delivery time, and channel
   - Weekly summary recipients, day, and time
   - Excluded job types (if any)

2. **Create `config.json`** in the workspace root with the same values in machine-readable form, for example:

```json
{
  "business_name": "",
  "trade": [],
  "timezone": "",
  "customer_segments": [],
  "avg_open_jobs": null,
  "platform": "",
  "platform_connected": null,
  "behind_schedule_threshold_days": 1,
  "stalled_threshold_days": 3,
  "commercial_priority": true,
  "brief_recipients": [],
  "brief_time_local": "07:00",
  "brief_channel": "",
  "weekly_summary_recipients": [],
  "weekly_summary_day": "",
  "weekly_summary_time": "",
  "excluded_job_types": []
}
```

3. **Give the user their first example task prompt** to copy and run:

> "Pull today's open job board from [platform] and give me this morning's ops brief."

Let them know they can also ask: *"Show me all jobs stalled for more than [N] days"* or *"Give me this week's summary"* at any time.
