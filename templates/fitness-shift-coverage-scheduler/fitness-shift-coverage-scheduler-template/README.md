# Fitness/Wellness/Salon/Spa - Shift / Coverage Scheduler

Stop texting substitutes one by one at 6 AM. This Gamut agent detects instructor and stylist callouts, finds qualified available staff, sends tiered outreach, and only wakes the manager when nobody has taken the shift — so clients show up to a staffed class, not a cancellation notice.

---

## Who It Is For

Studio owners, salon managers, and spa directors who lose front-desk hours every time an instructor calls out or a stylist cancels last minute — and whose clients deserve better than a same-day "class cancelled" email.

**Relevant subsegments: FITN**

Whether you run a boutique yoga studio, a busy blow-dry bar, or a multi-room med spa, if your coverage process lives in a group text thread, this agent replaces it.

---

## What It Does

1. **Monitors for callouts** — watches your designated callout channel (text relay, email, Mindbody, or Boulevard) and parses the open shift details automatically.
2. **Pulls qualified candidates** — queries your scheduling system for staff who hold the right certification or service skill, are not already booked, and are within their availability window.
3. **Ranks by fairness** — sorts candidates by who has taken the fewest recent coverage shifts, spreading the burden equitably across your roster.
4. **Sends tiered outreach** — contacts one candidate at a time via SMS or in-app message with the class time, location, and a reply deadline (default: 20 minutes).
5. **Escalates automatically** — moves to the next candidate if there is no reply, and alerts the manager if the shift is still unfilled within your configured threshold (default: 2 hours before start).
6. **Logs everything** — records every outreach attempt, response, and timestamp against the shift record.
7. **Delivers a weekly summary** — callouts received, shifts filled vs. unfilled, average fill time, and top responders, delivered to the manager every Monday.

---

## Key Integrations

- **Mindbody** — staff roster, class schedule, booking status, in-app messaging
- **Boulevard** — service provider roster, appointment schedule, in-app messaging
- **SMS (Twilio or equivalent)** — direct staff outreach
- **Slack** — manager alerts and weekly summaries
- **Email** — manager alerts, callout intake, and weekly summaries
- **CSV / spreadsheet** — fallback roster or certification tracking

---

## Getting Started

1. **Import this workspace** into your Gamut environment.
2. **Run the `agent-onboarding` skill** — the agent will walk you through your business type, scheduling system, callout channel, outreach preferences, and escalation settings.
3. **Send your first prompt** — try: "Set up shift coverage monitoring for my studio" or "We just got a callout for the 9 AM yoga class — find a sub."

---

## Configuration

After onboarding, your settings are saved to `config.json` in the workspace. You can update any field at any time by telling the agent what changed (e.g., "Change the escalation window to 30 minutes" or "Alert the manager 3 hours before class instead of 2").

Key settings include: scheduling system, callout intake channel, outreach channel, escalation window, unfilled-alert threshold, manager contact, blackout hours for staff contact, and certification source.

---

**Pattern: Vertical / NON-TECH — Fitness, wellness, salon & spa shift coverage**
Built by Datawizz — powered by Gamut.
