> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/sales-pipeline/crm-hygiene)** — one-click deploy, no setup.

# CRM Hygiene & Ops

> Keeps your CRM clean and current so the pipeline you report on is the pipeline you actually have.

## What it does

Every morning, CRM Hygiene & Ops audits your in-scope records against your data standards, logs
activity it can see in connected email and calendar, and fixes what it safely can. Low-risk fixes
(formatting, enrichment, attaching logged activity) apply automatically. Judgment calls (anything
touching money, stage, ownership, or merges) are proposed for one-click approval. It flags
duplicates, stale deals missing a next step, and records that violate your rules, then posts a
short hygiene digest to a channel you choose. Nothing irreversible happens without a gate.

## What you'll need

- **Accounts:** a CRM (Salesforce, HubSpot, Pipedrive, or similar) and Slack. Email and Calendar
  are recommended if you want the agent to log activity.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if your CRM needs
  a key.
- **Other:** a channel you actually check in the morning.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from
   the marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Which CRM and which channel to use
   - Your **audit scope** — which records to check each run
   - Your **field standards** — what a healthy record looks like (the heart of the setup)
   - Your **auto-fix policy** — what the agent may write on its own versus propose
   - Staleness thresholds, activity-logging and dedupe settings, proposal tone, and your schedule
3. Once setup finishes, run the dry-run verification before trusting any auto-writes:
   *"Audit my in-scope records but make NO changes — show me every AUTO change and every PROPOSE
   item you would raise, with current and proposed values."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (pull → audit → log → dedupe → sort → digest → apply).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if your CRM requires a key.

## Notes

- **The agent auto-changed something it should have asked about?** The rule lived in the AUTO
  section of your `auto_fix_policy`. Move it to PROPOSE and re-run. Anything touching Amount, Stage,
  Close Date, Forecast, ownership, or merges belongs in PROPOSE.
- **The digest is a wall of flags every morning?** Your `audit_scope` is too broad or
  `field_standards` too strict for your data's real state. Narrow to active pipeline and stage the
  standards — fix the highest-impact rule first. A daily run should surface a handful of items, not
  hundreds.
- **Activity logged to the wrong record?** Matching is ambiguous — usually shared aliases or
  contacts on multiple accounts. The agent should only auto-log confident single-record matches;
  everything else lands in "couldn't auto-match." If it still mis-attributes, lower
  `activity_lookback_days` and tighten what counts as a match.
- **It keeps proposing a duplicate you already rejected?** The agent has no cross-run memory, so it
  re-evaluates from scratch daily. It shouldn't re-raise a proposal rejected in the same week; for
  persistent false positives, refine `dedupe_confidence` (e.g. exclude subsidiaries that legitimately
  share a domain).
- **Nothing logged but you know reps had meetings?** Either `log_activity` is off, Email/Calendar
  isn't connected, or `activity_lookback_days` is shorter than the gap since the meeting. Confirm
  the connections and widen the lookback to cover a long weekend.
- **Approvals applied that nobody approved?** Approval detection is reading the thread too loosely.
  It must require an explicit approve with the item number and treat anything ambiguous as
  not-approved. A PROPOSE item is never written on a maybe.
