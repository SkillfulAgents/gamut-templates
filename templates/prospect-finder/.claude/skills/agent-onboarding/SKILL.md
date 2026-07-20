---
name: agent-onboarding
description: 'First-run setup for Prospect Finder. Interviews the user, then configures the agent — writes their CRM, ICP, buying signals, COI framing, exclusion rules, delivery channel, and schedule into CLAUDE.md and config.json, connects the CRM and Slack, and schedules the weekly run. Runs automatically the first time the agent is imported.'
---

# Onboard Prospect Finder

You are helping a new user set up **Prospect Finder** for the first time. Be warm and brief. Ask a few
questions at a time, accept defaults quickly, and **confirm before any outward or destructive action**
(connecting accounts, writing files, scheduling jobs).

The ICP, buying signals, and COI framing are the heart of this agent — those are the most important
answers to get right, and worth slowing down for. Most other fields have good defaults.

## 1. Welcome

Tell the user in one or two sentences: this agent searches recent news and public signals each week for
events that mean it's a good time to reach out to a new prospect, cross-checks them against their CRM,
and posts a short ranked list with a COI-framed reason to act now. Say you'll ask a few questions to
set it up, and that the ICP / signals / COI framing are where their input matters most.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team/domain you work in.
2. **Your CRM** — which CRM to cross-check against? _(e.g. Salesforce, HubSpot, Pipedrive.)_ This is
   required so the agent can skip accounts already in your pipeline.
3. **Your ICP (Ideal Customer Profile)** — who are you targeting? Push for specifics: company size,
   industry, funding stage, team structure, buyer title. Vague ICPs produce vague results. Give them a
   concrete starter to react to and have them rewrite it in their own words, e.g.:
   _"B2B SaaS companies, Series B and above, 50–500 employees, with a sales team of 10+ reps. Primary
   buyers: VP of Sales, CRO, or Head of Revenue Operations. Exclude consumer companies, pre-product
   startups, and companies with fewer than 10 salespeople."_
4. **Buying signals** — which public events mean it's a good time for them to reach out? Each signal
   needs a **type** (label), a **description** (exactly what to search for), and **why_it_matters** (the
   business reason it creates an opening). 3–6 signals works best. Give them this concrete starter set
   to edit — add, cut, and reword to fit their real triggers:
   - _Leadership Hire_ — "New VP of Sales, CRO, RevOps, or Sales Enablement hire in the last 30 days" —
     "New leaders rebuild their stack in the first 90 days and have budget to act."
   - _Funding Event_ — "Series B, C, or D announced in the last 60 days" — "Post-funding = board
     pressure to show growth = new tooling budget."
   - _Headcount Expansion_ — "Company posted 5+ sales or RevOps roles in the last 30 days" — "Scaling a
     GTM motion without better process creates compounding drag."
   - _Missed Target Signal_ — "Public statement, earnings note, or article indicating a missed revenue
     target or slowdown" — "Status quo pain is highest after a miss."
   - _GTM Pivot_ — "Company announced a new GTM motion, market expansion, PLG launch, or sales-led
     pivot" — "New motion = new process gaps = urgent need."
   - _Competitive Displacement_ — "Company publicly mentioned leaving, switching from, or evaluating a
     direct competitor" — "Active evaluation means they're already in buying mode."
5. **COI framing** — how do they think about Cost of Inaction for their buyers? The agent uses this to
   generate a COI angle for every account. Be concrete — the sharper their framing, the sharper the
   output. Give them a concrete starter to rewrite in their own words, ideally with 2–3 worked examples
   of framings or calculations they've used in real deals, e.g.:
   _"COI for my buyers is the compounding cost of scaling a broken process — every new rep, every new
   market, every quarter without a fix makes it worse and harder to reverse. I connect the specific
   signal to a tangible consequence: revenue not captured, ramp extended, capacity burned on manual
   work, deals lost while they're distracted — quantified where I have context, e.g. 'hiring 8 reps onto
   your current onboarding at a 4-month ramp leaves $X in Q3 revenue on the table.'"_
6. **Exclusion rules** — skip accounts already in pipeline _(default yes)_, skip current customers
   _(default yes)_, and skip accounts touched in the last N days _(default 90)_.
7. **Search scope** — how far back to search for signals _(default 7 days)_ and how many accounts to
   return each week _(default 10; 5–10 is ideal)_.
8. **Delivery** — which Slack channel should the weekly list post to? _(e.g. #prospecting)_ And the
   format: "list" _(recommended)_ or "table".
9. **Schedule** — what day/time and timezone? _Default:_ Mondays 8:00 AM, cron `0 8 * * 1`, ask their
   timezone _(e.g. America/New_York)_.

Don't collect secrets in chat — accounts are connected via OAuth in step 3 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, CRM, the final ICP, the
  final buying_signals list, the final COI framing, exclusion rules, search scope, delivery channel,
  output format, and the schedule. Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `crm_name`, `icp`, `buying_signals` (type /
  description / why_it_matters), `exclude_existing_pipeline`, `exclude_existing_customers`,
  `exclude_recently_contacted_days`, `lookback_days`, `max_accounts_to_return`, `coi_framing`,
  `output_channel`, `output_format`, `schedule`, `timezone`.
- **Connected accounts** — walk the user through connecting their **CRM** and **Slack**. Confirm first.
- **.env** — only if the CRM needs an API key not covered by OAuth; copy from `.env.example` and have the
  user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the weekly run at their chosen day/time/timezone (default cron
`0 8 * * 1`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written and the CRM + Slack authenticate.
- Run one small smoke test, derived from the verification test: "Run your prospect search for one signal
  type only — [pick their strongest signal] — and return whatever you find without filtering against the
  CRM, so we can see what you're surfacing." Confirm raw results come back and a post can reach the
  delivery channel.

## 6. Done

Summarize what you configured, what the agent will do each week, and how to give it its first task. Tell
the user they can re-run `agent-onboarding` anytime to reconfigure, and that the ICP, signals, and COI
framing are the fields to revisit if the output ever feels off.
