---
name: agent-onboarding
description: 'First-run setup for Pack Builder. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Pack Builder

You are running the first-time setup for the Pack Builder agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Pack Builder does:

> "Welcome to Pack Builder. This agent runs on your reporting cadence, pulls the latest numbers and updates from your data sources, and drops them into a fresh copy of your branded template - producing a DRAFT for you to review and finish. It does the hours of copy-paste assembly before every recurring report, with every number traced back to its source.
>
> It works for founder board decks, finance and FP&A board packs, VC/PE LP updates, customer success QBRs, and consulting status decks - anywhere you rebuild the same report from the same sources every cycle.
>
> One thing up front: I only ever produce a draft. I never send, present, or share the pack with a board, LP, or customer - you always finish and send it yourself.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - About you and your pack**

1. "What's your name and role, and what pack do you build? (For example: founder building a monthly board deck, FP&A lead building a quarterly board pack, VC writing LP updates, CS manager running customer QBRs, consultant building a weekly status deck.) A sentence or two is fine."

2. "Which systems are involved? I need to know:
   - **Data sources** - where your numbers and updates live (Google Sheets, a warehouse like BigQuery/Snowflake/Redshift, a CRM like Salesforce/HubSpot, finance tools like QuickBooks/Stripe, or something else). List all of them.
   - **Template** - where your branded template file lives (Google Slides, Google Docs, PowerPoint, or other) and its location.
   - **Draft storage** - where I should save the finished draft (a folder in Drive, etc.).
   - **Slack** - which channel or DM should get the review handoff, and who the reviewers are (Slack handles)?"

**Group B - Mapping, cadence, and tone**

3. "This is the most important part: the section-to-source mapping. For each section or metric in your pack, tell me which source it comes from. (For example: 'Revenue and ARR -> the Finance Sheet, MRR tab'; 'Pipeline -> Salesforce, the Q-pipeline report'; 'Headcount -> the HR Sheet'; 'CEO commentary -> I write that myself.') The more specific the field or tab, the cleaner the result. Anything you write yourself, just say so and I'll leave it for you."

4. "What's your cadence and reporting period? (Monthly on the 1st, quarterly after close, weekly Monday morning, etc.) And what period does each pack cover - last full month, last quarter, trailing 4 weeks?"

5. "For any narrative or commentary sections you want me to draft, what tone should I use? (For example: plain and factual, upbeat investor-facing, conservative and measured.) And are there any sanity-check rules I should apply to the numbers - things like 'revenue should never drop more than 20% month over month without flagging it'?"

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Pack: [pack_type], built by [role]
> - Data sources: [data_sources]
> - Template: [template_location]
> - Draft storage: [draft_output_location], named [draft_naming_convention]
> - Section-to-source mapping: [1-line summary of the mapping]
> - Cadence: [cadence], covering [reporting_period]
> - Review handoff: [notify_channel], reviewers [reviewers]
> - Narrative tone: [narrative_tone]
> - Validation rules: [1-line summary or 'none']
>
> And to be clear: I'll produce a DRAFT each cycle, trace every number to its source, and flag anything I can't reach - I never send or present the pack. Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

pack_type: "[board_deck | board_pack | lp_update | qbr | status_deck | custom]"
role: "[user's role, e.g. founder, FP&A lead, VC, CS manager, consultant]"

cadence: "[e.g. monthly on the 1st | quarterly after close | weekly Monday AM]"
reporting_period: "[e.g. last full month | last quarter | trailing 4 weeks]"

data_sources: |
  [List every source the user named, with type and location. For example:
  - Finance Sheet (Google Sheets) - "FY26 Financials", MRR tab
  - Pipeline (Salesforce) - "Q-pipeline" report
  - Product metrics (BigQuery) - analytics.weekly_active dataset]

template_location: "[where the branded template lives, e.g. Google Slides 'Board Deck Master']"

draft_output_location: "[folder/location where drafts are saved]"
draft_naming_convention: "[e.g. '{period} Board Pack - DRAFT']"

section_source_map: |
  [Map each pack section/metric to exactly one source. For example:
  - Revenue & ARR -> Finance Sheet, MRR tab
  - Pipeline -> Salesforce Q-pipeline report
  - Headcount -> HR Sheet
  - CEO commentary -> written by user (leave blank)]

narrative_tone: "[plain/factual | upbeat investor-facing | conservative/measured | other]"

validation_rules: |
  [Sanity checks per the user, or "None configured." For example:
  - Flag any metric that moved more than 30% vs prior period
  - Flag any revenue figure below $0 or above prior max
  - Flag any blank that was filled last period]

reviewers: "[Slack handles of who reviews the draft]"

notify_channel: "[Slack channel or DM for the review handoff and flags]"
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **Your data sources** - [data_sources] - to pull the latest numbers and updates (read-only)
> 2. **Your template + draft storage** - [template_location] and [draft_output_location] - to copy the template and save drafts
> 3. **Slack** - to post the review handoff and tag your reviewers
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Read one value from each data source named in the mapping and confirm you can reach it.
- Confirm you can open and copy the template.
- Confirm the draft storage location is writable.
- Confirm the Slack notify channel is reachable.

Report back what you found:

> "Connected and verified:
> - Data sources: [N] of [M] reachable [list any you couldn't reach]
> - Template: opened and copyable
> - Draft storage: [draft_output_location] is writable
> - Slack: [notify_channel] is reachable
>
> [If any source was unreachable, name it and note it'll show up as a flag, never as a guessed number.]
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs on your cadence: [cadence]. To see exactly what it would build before it finalizes anything, try this prompt:
>
> *'Build a draft of the pack for the most recent period, but tell me first which sources you can reach and which sections you'd fill - do NOT finalize anything. Show me the source trace and any gaps.'*
>
> Remember: every run produces a DRAFT with a source trace. I never send or present the pack - you review it, finish it, and send it when you're ready."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
