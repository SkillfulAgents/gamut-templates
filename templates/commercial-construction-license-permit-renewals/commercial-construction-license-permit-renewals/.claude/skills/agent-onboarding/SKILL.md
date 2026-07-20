---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's get your Commercial Construction/GC Compliance Tracker configured. This covers contractor licenses, sub COIs, certifications, bonding, and project permits. I'll ask about your company, your systems, and how you want reminders handled. Takes about 8 minutes.

---

## Company basics

1. What is your company name, and are you a general contractor, a construction manager, or a specialty trade contractor?
2. What states or jurisdictions do you operate in primarily? (Licenses and permit requirements vary by state.)
3. Roughly how many active subcontractors do you use across your projects — and do you need to track their COIs, or just your own company's licenses and certs?

---

## Systems

4. Do you use Procore, Sage/Viewpoint, or another platform for project management and document storage? Is it connected to Gamut, or should we start from a spreadsheet register?
5. Where are sub COIs currently stored — in Procore, a shared Drive folder, or another location? Provide the folder path or system name.

---

## Item types to track

6. Which of the following do you want the agent to track? (Select all that apply)
   - GC license and state contractor registrations
   - Subcontractor COIs (GL, workers' comp, auto)
   - OSHA certifications (10/30) for field staff
   - Operator and equipment certifications
   - Performance / payment / bid bonds
   - Project-specific building and trade permits
   - Other (describe)

---

## Lead times and cadence

7. When should the agent start sending renewal reminders? Default is 90/60/30/14 days before expiry — adjust any of these if your renewal lead times differ (e.g., bonding often needs 60+ days).
8. How aggressively should reminders repeat within a tier — every 14 days (gentle), every 7 days (standard), or every 3 days (aggressive)?

---

## Escalation and digest

9. Who is the compliance lead or project manager who should receive lapse alerts and the daily digest? Provide their name and Slack handle or email.
10. Which Slack channel should receive the daily compliance digest?
11. For sub COI lapses on active projects: should the project manager for that project receive a separate direct alert, or only the compliance lead?

---

## After Questions Are Answered

Once all questions have been answered:

1. **Update CLAUDE.md** — fill in `## Your context` with: company name, type, jurisdictions, sub count, system and connection status, COI storage location, item types tracked, lead times, nudge cadence, escalation contact, digest channel, and project-specific lapse alert preference.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "company_name": "",
  "company_type": "gc | cm | specialty_trade",
  "jurisdictions": [],
  "track_sub_cois": true,
  "sub_count": 0,
  "system": "procore | sage_viewpoint | spreadsheet | other",
  "system_connected": true,
  "coi_storage": "",
  "item_types": [],
  "lead_time_days": [90, 60, 30, 14],
  "nudge_cadence": "gentle | standard | aggressive",
  "compliance_lead": "",
  "digest_channel": "",
  "project_lapse_alert": true
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Run today's compliance check and post the digest."

   or

   > "Show me everything expiring in the next 30 days."
