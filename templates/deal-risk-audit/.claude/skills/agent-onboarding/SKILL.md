---
name: agent-onboarding
description: 'First-run setup for Deal Risk Audit. Interviews the user, then configures the agent — writes their CRM, call recorder, deal scope, discovery criteria, risk thresholds, and delivery settings into CLAUDE.md and config.json, connects the CRM, call recorder, and chat accounts, and schedules the weekly audit. Runs automatically the first time the agent is imported.'
---

# Onboard Deal Risk Audit

You are helping a new user set up **Deal Risk Audit** for the first time. Be warm and brief. Ask a few
questions at a time, accept defaults quickly, and **confirm before any outward or destructive action**
(connecting accounts, writing files, scheduling jobs).

The single most important part of this setup is the **discovery criteria** — they are the core of the
agent. Take time there; everything else is quick.

## 1. Welcome

Tell the user in one or two sentences: this agent pulls their open deals each week, reads the call
recordings, scores each deal against their own discovery methodology, and posts the gaps — with specific
fixes — before they cost a deal. Say you'll ask a few questions to set it up, and flag that the
discovery criteria step is the one worth slowing down for.

## 2. Interview

Ask these, grouped. Keep only answers that change behavior; offer the defaults shown.

1. **Your systems**
   - Which **CRM**? _(e.g. Salesforce, HubSpot, Pipedrive — default Salesforce)_
   - Which **call recorder**? _(Gong, Chorus, Fireflies, Otter, … — default Gong)_

2. **Deal scope**
   - **Active stages to audit** — must match your CRM exactly; have them copy/paste from CRM settings.
     _Default:_ Discovery, Proposal, Negotiation, Verbal Commit.
   - **Stages to always skip.** _Default:_ Closed Won, Closed Lost, On Hold, Prospecting _(too early to
     audit discovery)_.
   - **Minimum deal value** to audit _(default 0 = all)_.
   - **Owner filter** — _"me"_ for the user's own deals (default), or a list of rep names.

3. **Discovery methodology (`discovery_criteria`) — the core.** Ask the user to define what "good
   discovery" looks like for them. Each criterion needs an `id` (no spaces), a `label` (shown in
   output), a `description` (what they're uncovering and why), and `evidence_needed` (what the agent
   should find in transcripts/CRM to confirm coverage). Tell them to start with **4–6** criteria and
   refine over time. Give them this **concrete starter to edit** — do not silently adopt it; have them
   confirm or replace each one:
   - `economic_buyer` — **Economic Buyer Identified.** Have we confirmed who controls the budget and can
     say yes without committee? Evidence: a note or quote naming the EB, their title, and that they own
     the budget. "Their VP Sales says she owns the decision" counts; "I think the VP is involved" does not.
   - `status_quo_cost` — **Cost of Status Quo Quantified.** Has the prospect described, in their own
     words, what staying the course costs them? Evidence: a direct quote with specifics ("losing ~2
     weeks per new hire to manual onboarding"), not "they seem frustrated."
   - `decision_process` — **Decision Process Mapped.** Do we know who signs off, the steps, and the real
     timeline — confirmed by the prospect, not assumed from stage? Evidence: confirmed steps + timeline
     in their words.
   - `compelling_event` — **Compelling Event Identified.** A real external deadline the prospect owns
     (renewal, board review, launch, FY reset) — not our quarter-end. Evidence: a specific dated event
     they described.
   - `alternatives` — **Alternatives Explored.** Do we know what they'll do if not us (status quo, build,
     a competitor)? Evidence: alternatives the prospect actually discussed.
   - `champion_strength` — **Champion Strength Assessed.** Can our champion sell internally — and have
     they taken concrete action (forwarded materials, arranged an exec intro, pushed for next steps)?
     Evidence: a specific action on our behalf, not "they seem enthusiastic."

   Have them edit, cut, or add so it matches their actual methodology — generic criteria produce generic
   suggestions.

4. **Risk thresholds (`risk_thresholds`)** — set based on how many criteria they defined. The score is
   the count of ✅ Covered criteria. _Example for 6 criteria:_ green = 5, yellow = 3, red = 1 (deals
   below the yellow threshold are Red). Warn them: if green is set higher than their criteria count, no
   deal can ever go green.

5. **Delivery**
   - Which **chat channel** should the audit post to? _(e.g. #deal-risk)_ — required.
   - **Include suggested actions** for each gap? _(default yes)_
   - **@mention the deal owner** in the post? _(default yes)_

6. **Schedule** — what day/time and timezone? _Default:_ Mondays 8:30 AM, cron `30 8 * * 1`; ask their
   timezone _(default America/New_York)_.

Don't collect secrets in chat — accounts are connected via OAuth in step 3 below.

## 3. Write the answers back

Persist everything — confirm before writing:

- **CLAUDE.md** — append the durable context under `## Your context`: CRM + call recorder, active/exclude
  stages, min deal value, owner filter, the final `discovery_criteria`, `risk_thresholds`, delivery
  channel + flags, and the schedule. Do not touch the general instructions above it.
- **config.json** — mirror the structured settings: `crm_name`, `call_recorder`, `active_stages`,
  `exclude_stages`, `min_deal_value`, `owner_filter`, `discovery_criteria`, `risk_thresholds`,
  `output_channel`, `include_suggested_actions`, `tag_owner`, `schedule`, `timezone`.
- **Connected accounts** — walk the user through connecting their **CRM**, their **call recorder**, and
  **chat**. Confirm first.
- **.env** — only if a system needs an API key not covered by OAuth; copy from `.env.example` and have
  the user fill it in. Never echo secret values.

## 4. Schedule the run

With the user's confirmation, schedule the weekly audit at their chosen day/time/timezone (default cron
`30 8 * * 1`).

## 5. Verify

- Confirm `config.json` and `## Your context` were written, and that the CRM, call recorder, and chat
  accounts authenticate.
- Run one small smoke test, derived from the deal-level audit: "Pick one deal from my pipeline and run
  the full discovery audit on it. Walk me through each criterion and show me exactly what evidence you
  found (or didn't find) before giving me a score." Confirm it reads the deal, pulls a transcript, and
  scores every criterion.

## 6. Done

Summarize what you configured, what the agent will now do each week, and how to give it its first task.
Tell the user they can re-run `agent-onboarding` anytime to reconfigure — and that the `discovery_criteria`
are the lever to pull if the audits feel off.
