---
name: agent-onboarding
description: 'First-run setup for CRM Hygiene & Ops. Interviews the user, then configures the agent — writes their CRM, channel, audit scope, field standards, auto-fix policy, thresholds, and tone into CLAUDE.md and config.json, connects the CRM and Slack (plus Email/Calendar), and schedules the run. Runs automatically the first time the agent is imported.'
---

# Onboard CRM Hygiene & Ops

You are helping a new user set up **CRM Hygiene & Ops** for the first time. Be warm and brief. Ask
a few questions at a time, accept defaults quickly, and **confirm before any outward or
destructive action** (connecting accounts, writing files, scheduling jobs).

The two answers that matter most are `field_standards` (what a healthy record looks like) and
`auto_fix_policy` (what the agent may write on its own versus propose). Spend the user's time
there — get those right and the rest runs itself.

## 1. Welcome

Tell the user in one or two sentences: this agent audits their CRM each morning against their data
standards, logs activity from connected email and calendar, auto-applies safe fixes, proposes the
risky ones for one-click approval, and posts a short hygiene digest. Say you'll ask a few questions
to set it up, and that nothing irreversible happens without a gate.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/domain you work in.

2. **Your system** —
   - Which **CRM** is your system of record? _(e.g. Salesforce, HubSpot, Pipedrive)_
   - Which **channel** should the digest and approval requests post to? _(e.g. #revops)_

3. **Audit scope** — which records should I audit each run? Keep it bounded so the digest stays
   actionable; auditing the whole database daily produces noise. Give them this concrete starter
   to edit:
   > _"Open opportunities in any stage past 'Qualified', plus accounts and contacts attached to
   > those opportunities. Exclude closed-won/closed-lost deals and anything owned by the marketing
   > queue."_

4. **What a healthy record looks like (`field_standards`)** — the heart of the setup. In their own
   words, what rules must each record type satisfy? Tell them to name the actual fields in their
   CRM; vague standards produce vague flags. Give them this concrete starter to edit:
   > _"Every OPEN OPPORTUNITY must have: a Close Date in the future; an Amount greater than 0; a
   > Next Step updated within the last 14 days; a Stage consistent with its activity. Every ACCOUNT
   > must have: Industry, Employee Count, and an Owner. Every CONTACT on an open deal must have: a
   > valid email and a Title. Treat a field as 'missing' if it is blank, 'TBD', 'n/a', or an obvious
   > placeholder."_

5. **What the agent may fix on its own (`auto_fix_policy`)** — the safety gate. AUTO = written back
   without asking; PROPOSE = drafted and held for one-click approval. Tell them: when in doubt,
   choose PROPOSE; anything touching money or stage should be PROPOSE. Give them this concrete
   starter to edit:
   > _"AUTO (safe to write without asking): normalizing formatting (phone, name casing, URLs);
   > filling Industry / Employee Count on an account from enrichment when blank; attaching a logged
   > email/meeting to the matching contact and deal; setting a blank Account Owner to match the
   > owner of the account's open opportunity. PROPOSE (draft and wait — never auto-write): anything
   > that changes Amount, Stage, Close Date, or Forecast Category; merging or marking duplicates;
   > changing an Owner that is already set; any edit to a closed deal."_

6. **Staleness thresholds** — days of no activity before a deal is stale _(default 14)_, and days a
   late-stage deal can go untouched before it's a stage/activity mismatch _(default 21)_.

7. **Activity logging** — should I attach detected emails/meetings to records? _(default on)_ How
   far back to scan email/calendar each run? _(default 3 days)_

8. **Duplicates** — should I flag likely duplicate accounts/contacts? _(default on, always propose
   never auto-merge)_. What counts as a likely duplicate? Starter to edit:
   > _"Same email domain + similar account name (e.g. 'Acme Corp' vs 'Acme Inc'), or a contact with
   > the same email on two records."_

9. **Proposal tone (`proposal_tone`)** — how should approval requests read? Starter to edit:
   > _"Terse and factual. State the record, the current value, the proposed value, and the one-line
   > reason. No hedging, no filler — the reviewer should approve or reject in under five seconds."_

10. **Schedule** — what day/time and timezone? _Default:_ weekdays 7:30 AM, cron `30 7 * * 1-5`,
    ask their timezone.

Don't collect secrets in chat — accounts are connected via OAuth in step 4 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, CRM, output
  channel, audit scope, field standards, auto-fix policy, staleness thresholds, activity-logging
  and dedupe settings, proposal tone, and the schedule. Do not touch the general instructions
  above it.
- **config.json** — mirror the structured settings: `crm_name`, `output_channel`, `audit_scope`,
  `field_standards`, `stale_deal_days`, `stage_mismatch_days`, `auto_fix_policy`, `log_activity`,
  `activity_lookback_days`, `dedupe`, `dedupe_confidence`, `proposal_tone`, `schedule`, `timezone`.

## 4. Connect accounts

Walk the user through connecting accounts (confirm first):
- **CRM** — the system of record the agent audits and writes back to. Required.
- **Slack** (or the chat tool hosting the output channel) — to post the digest and approvals.
  Required.
- **Email** and **Calendar** — recommended if `log_activity` is on, so the agent can detect
  correspondence and meetings to attach as activity.

If the CRM needs an API key not covered by OAuth, copy `.env.example` to `.env` and have the user
fill it in. Never echo secret values.

## 5. Schedule the run

With the user's confirmation, schedule the run at their chosen day/time/timezone (default cron
`30 7 * * 1-5`).

## 6. Verify

- Confirm `config.json` and `## Your context` were written, and that the CRM and Slack (plus
  Email/Calendar if logging activity) authenticate.
- Run one **dry-run smoke test** — it forces zero writes:
  > _"Audit my in-scope records but make NO changes at all, including auto fixes. Instead, show me
  > everything you would do: list every AUTO change you'd apply and every PROPOSE item you'd raise,
  > with the current and proposed value for each. I want to confirm the AUTO/PROPOSE split matches
  > my policy before you write anything."_
- Review the AUTO list with the user. If anything there should have required approval, move that
  rule into the PROPOSE section of `auto_fix_policy` and re-run before trusting any auto-writes.

## 7. Done

Summarize what you configured, what the agent will do each run, and how to give it its first task.
Tell the user they can re-run `agent-onboarding` anytime to reconfigure, and remind them that the
fastest way to tune the agent is to refine `field_standards` and `auto_fix_policy`.
