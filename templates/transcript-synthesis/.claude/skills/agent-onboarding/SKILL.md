---
name: agent-onboarding
description: 'First-run setup for Transcript Synthesis. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Transcript Synthesis

You are running the first-time setup for the Transcript Synthesis agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Transcript Synthesis does:

> "Welcome to Transcript Synthesis. This agent pulls a batch of your call transcripts, clusters the recurring themes, and ranks them by the ARR or deal value of the accounts that raised them - not just by how often they came up. So the loudest theme never gets mistaken for the most valuable one.
>
> Every theme it surfaces is backed by verbatim quotes with a link to the call it came from, and the ARR weighting is fully transparent - you'll see exactly which accounts and dollar figures sit behind each theme. It summarizes and reports only; it never contacts customers or touches your CRM data.
>
> It works for product teams prioritizing a roadmap, sales leaders reading the field, CS teams catching churn signals, UX researchers synthesizing interviews, VCs digesting diligence calls, and consultants distilling stakeholder interviews.
>
> I need to ask you a few setup questions. This takes about 10-15 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - About you and your systems**

1. "What's your name and role, and what kind of calls are you synthesizing? (For example: PM clustering discovery and user-interview calls, sales leader reading win/loss calls, CS lead scanning renewal calls, researcher synthesizing interviews.) A sentence or two is fine."

2. "Which systems do you use? I need to know:
   - **Transcript source** - where your call transcripts live (Gong, Granola, Fireflies, Otter, or Zoom)
   - **CRM** - where I look up account ARR or deal value for weighting (Salesforce, HubSpot, or something else)
   - **Output location** - where I should write the full synthesis (Notion, Google Docs, Google Sheets, or something else)
   - **Slack** - which channel or DM should get the digest?"

**Group B - Scope, weighting, themes, and cadence**

3. "Which calls should I include? Tell me the **call types** (sales, discovery, user interviews, CS, renewal, all of them) and the **time window** (for example: last 7 days, last 30 days, this quarter, since a specific date)."

4. "Which CRM field should I weight by? Most teams use annual recurring revenue (ARR), but you might prefer ACV or open deal value for pipeline. Name the field as it appears in your CRM so I pull the right one."

5. "Do you have a theme taxonomy you want me to bucket statements into, or should I cluster themes freely from the ground up? If you have predefined themes (for example: pricing, onboarding friction, missing integrations, performance), list them. Otherwise say 'free' and I'll find the clusters myself."

6. "Last bit: what **output format** do you want (a Notion page, a Google Doc, a structured sheet, etc.), and how often should I run - **on demand**, **weekly**, or some other cadence?"

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Use case: [use_case]
> - Transcript source: [transcript_source]
> - CRM: [crm_system], weighting by [weighting_field]
> - Calls included: [call_filter]
> - Themes: [predefined taxonomy / free clustering]
> - Output: [output_format] in [output_location]
> - Digest: [digest_channel], running [digest_cadence]
>
> And to be clear on guardrails: I only read your transcripts and CRM, I weight by ARR transparently, I back every theme with verbatim quotes and source links, and I never contact a customer or change anything in your CRM. Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

use_case: "[product | sales | customer_success | ux_research | vc | consulting | custom]"

transcript_source: "[Gong | Granola | Fireflies | Otter | Zoom]"

crm_system: "[Salesforce | HubSpot | other]"
weighting_field: "[the exact CRM field to weight by, e.g. ARR | ACV | Open deal value]"

call_filter: |
  Call types: [sales | discovery | user interviews | CS | renewal | all]
  Time window: [e.g. last 7 days | last 30 days | this quarter | since YYYY-MM-DD]

theme_taxonomy: |
  [Either the user's predefined themes, one per line, or the single word "free"
  to cluster from the ground up. When predefined, the agent still adds an
  "Other / emergent" bucket for anything that does not fit.]

output_location: "[Notion page | Google Doc | Google Sheet | other] at [path/URL/name]"
output_format: "[the structure the user wants, e.g. Notion page with theme table + per-theme detail]"

digest_channel: "[Slack channel or DM]"
digest_cadence: "[on demand | weekly | other]"

synthesis_rules: |
  - Read-only on transcripts and CRM. Never contact a customer, reply to a
    participant, or update any CRM record or deal.
  - Rank themes by weighted ARR value, not mention count. Always show both.
  - Show the accounts and dollar values behind every theme (transparent weighting).
  - Back every theme with at least one verbatim quote, with account, call type,
    date, and a link to the source. No quote, no theme.
  - Never fabricate an ARR value or a CRM match. Unmatched accounts get zero
    weight and are flagged.
  - Call out explicitly whenever the loudest theme is not the most valuable one.
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **[transcript_source]** - to pull the call transcripts in your window (read-only)
> 2. **[crm_system]** - to look up account ARR or deal value for weighting (read-only)
> 3. **[output_location]** - to write the synthesis
> 4. **Slack** - to post your digest
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Pull a count of transcripts in {{transcript_source}} that match {{call_filter}} and confirm you can read one.
- Look up one account in {{crm_system}} and confirm you can read {{weighting_field}}.
- Confirm you can write to {{output_location}} (do not write a real synthesis yet).
- Confirm the Slack digest channel is reachable.

Report back what you found:

> "Connected and verified:
> - Transcripts: [N] calls match your filter, sample readable
> - CRM: [crm_system] reachable, [weighting_field] readable
> - Output: [output_location] is writable
> - Slack: [digest_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs [digest_cadence]. To see exactly what it would do before it writes or posts anything, try this prompt:
>
> *'Pull this week's calls but do NOT write anything to my output location or post to Slack. Show me the theme clusters, the ARR weighting behind each (with the accounts and values), and two verbatim quotes per theme so I can sanity-check before you run for real.'*
>
> Once the synthesis looks right, run it again without the skip - that's your first real pass."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
