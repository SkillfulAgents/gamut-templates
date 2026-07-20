> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/shift-coverage-scheduler/restaurant-qsr-shift-coverage-scheduler)** — one-click deploy, no setup.

# Restaurant/QSR Shift Coverage Scheduler

Detects callouts and scheduling gaps, finds qualified available staff from the scheduling system, runs a fair one-at-a-time outreach sequence, confirms the fill, and alerts the manager if the shift stays open.

Built for restaurant and QSR operators who lose time manually chasing coverage every time someone calls out.

---

## What it does

1. Monitors your scheduling system (7shifts, HotSchedules/Fourth) for unassigned shifts, callouts, and dropped shifts within a configurable alert window.
2. Pulls the qualified candidate list automatically - matching on role, current schedule, weekly hour cap, and any required certifications (food handler, alcohol service, key holder).
3. Ranks candidates by fairness rotation - fewest recent fill-ins first - so the same people are not contacted every time.
4. Sends one-at-a-time outreach via SMS or email with a clear accept/decline prompt and a configurable response window (default: 15 minutes per candidate).
5. Confirms the fill by writing the assignment back to the scheduling system and sending confirmation details to the covering employee.
6. Notifies the manager immediately when a shift is filled, including who accepted and how many candidates were contacted.
7. Escalates to the manager with a full contact log if the candidate list is exhausted or the shift start is approaching without a fill.
8. Logs every outreach attempt and fill event for fairness auditing and coverage reporting.

---

## Key integrations

- **7shifts** - reads shift schedules, employee availability, and role assignments; writes confirmed coverage back to the schedule.
- **HotSchedules/Fourth** - reads and writes shift data, employee availability, and role/certification flags.
- **Toast POS** - optional; validates scheduled labor against expected covers or daypart demand to prioritize coverage urgency.
- **SMS (e.g., Twilio)** - primary outreach channel for staff; sends shift details, accept/decline prompt, and confirmation.
- **Email (SMTP or API)** - fallback outreach channel; also used for manager escalation alerts when configured.

---

## Getting started

1. Import this workspace into Gamut.
2. Run the `agent-onboarding` skill and answer the setup questions (scheduling system credentials, outreach channels, manager contacts, roles, and hour rules).
3. Trigger the agent with: "Check for open shifts" or "We have a callout for [Role] on [Date] at [Time] - find coverage."

---

Relevant subsegments: FOOD
