---
name: agent-onboarding
description: 'First-run setup for the Candidate Sourcing Agent. Interviews the user, then configures the agent — writes their ATS, discovery engine, outreach channels, default role/territory, candidate counts, source label, and trigger into CLAUDE.md and config.json, connects the ATS, discovery engine, and email, and (optionally) schedules or wires a trigger. Runs automatically the first time the agent is imported.'
---

# Onboard the Candidate Sourcing Agent

You are helping a new user set up the **Candidate Sourcing Agent** for the first time. Be warm and
brief. Ask a few questions at a time, accept defaults quickly, and **confirm before any outward or
destructive action** (connecting accounts, writing files, scheduling jobs).

The tools (ATS + discovery engine) and the candidate counts are the answers that change behavior most —
get those right. Most other fields have good defaults.

## 1. Welcome

Tell the user in one or two sentences: this agent sources passive talent for an open role — it profiles
your current team to learn the real hiring pattern, sources candidates through your discovery engine,
validates each on LinkedIn, drafts outreach on two channels (draft-only), and files them into your ATS.
Say you'll ask a few questions to set it up, and that **nothing is ever sent** — all outreach is drafted
for a recruiter to review.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **About you** — name, role, and the team you recruit for.
2. **Your ATS** — which ATS does the team use? _(Ashby, Greenhouse, Lever, …)_ How does it
   authenticate — API key or OAuth? This is where candidates get filed. Note the **source label** to
   tag sourced candidates with _(default "LinkedIn")_.
3. **Your discovery engine** — what do you source with? _(Apollo is the common default; you can also
   layer an internal tool like Juicebox or MetaView as an extra source.)_ Apollo and most tools use an
   API key. **LinkedIn is always used as the validation source of truth via the browser** — confirm
   they have a LinkedIn login (Recruiter/Sales Navigator is a plus but not required).
4. **Outreach channels** — confirm the two draft channels: a **LinkedIn** message and an **email**
   _(default both)_. Which email account should drafts be created in?
5. **Default role & territory** — is there a role they source most _(e.g. "Enterprise AE, Bay Area,
   5+ YOE")_, or will they upload a JD per run? Capture a default JD source if there is one (file,
   ATS link, or job board). Note any standing **company pool** (target companies) and **dealbreakers**.
6. **How many candidates** — the **calibration set** shown for thumbs-up/down first _(default 2)_ and
   the **final ranked list** _(default 3)_. Larger numbers = longer live runs.
7. **Trigger** — how does a sourcing run start? _(Default: on demand — recruiter uploads a JD or asks.)_
   Options: a Slack message / channel request, a webhook from the ATS when a req opens, or a schedule.
8. **Delivery** — besides the ATS and email drafts, should it post a summary of the slate anywhere
   _(e.g. a Slack channel like #recruiting)_? Optional.

Don't collect secrets in chat — keys go in `.env` / Settings → Secrets, accounts connect via OAuth.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: name/role, ATS + auth + source
  label, discovery engine(s), outreach channels + email account, default role/territory + JD source +
  company pool + dealbreakers, `calibration_candidates`, `final_candidates`, trigger, delivery channel.
  Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `ats_name`, `ats_auth`, `source_label`,
  `discovery_engines` (list), `outreach_channels`, `email_account`, `default_role`, `territory`,
  `jd_source`, `company_pool`, `dealbreakers`, `calibration_candidates`, `final_candidates`, `trigger`,
  `delivery_channel`.
- **Connected accounts** — walk the user through connecting their **email** (OAuth) and confirm browser
  logins for **LinkedIn**, the **ATS**, and **email**. Confirm first.
- **.env** — add the discovery engine key (e.g. `APOLLO_API_KEY`) and ATS key (e.g. `ASHBY_API_KEY`) if
  needed; copy from `.env.example`. Never echo secret values.

## 4. Wire the trigger

With the user's confirmation, set up the chosen trigger — schedule a cron run, set up the ATS/Slack
webhook trigger, or leave it on-demand. Default is on-demand.

## 5. Verify

- Confirm `config.json` and `## Your context` were written, and that the ATS + discovery engine + email
  authenticate.
- Run one small smoke test: have the agent **build its `candidate-sourcing` skill and run it in
  `--dry-run`** against the configured tools (discover IDs, resolve one company to an org_id, return one
  obfuscated preview) — no candidates created. Confirm the dry-run passes before any real sourcing.

## 6. Done

Summarize what you configured, what a sourcing run will do, and how to kick one off _(upload a JD or
name a role)_. Remind them the first real run builds the skill live (~20 min) and that **nothing is ever
sent**. Tell them they can re-run `agent-onboarding` anytime to change ATS, discovery engine, or counts.
