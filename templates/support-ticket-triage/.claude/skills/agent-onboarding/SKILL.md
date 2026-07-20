---
name: agent-onboarding
description: 'First-run setup for Support Ticket Triage & Draft Reply. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Support Ticket Triage & Draft Reply

You are running the first-time setup for the Support Ticket Triage & Draft Reply agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what this agent does:

> "Welcome to Support Ticket Triage & Draft Reply. For every new ticket in your helpdesk, this agent categorizes it, sets a priority against your SLA, and drafts a reply grounded in your knowledge base, written in your support voice. The draft waits for an agent to review and send. If the knowledge base does not actually cover the question, the agent will not make something up. It flags a KB gap instead. Once a week it posts a Voice-of-Customer digest: volume, top themes, category and priority mix, SLA performance, recurring KB gaps, and the churn-risk tickets that need a human.
>
> Two things up front: replies are drafts by default (auto-send is opt-in, per category), and the agent will never promise a refund, credit, or date on its own.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - Systems and triage rules**

1. "Which systems do you use? I need to know:
   - **Helpdesk** - where your tickets live (Zendesk, Intercom, Freshdesk, Help Scout, or something else)
   - **Knowledge base** - where your support articles live (a public help center, Notion, Confluence, Google Docs, Guru, or something else), and a link or path to it
   - **Slack** - which channel or DM should get the weekly Voice-of-Customer digest, and a separate channel for escalation alerts if you want one"

2. "How should I categorize tickets? Give me your category list (for example: Billing, Bug/Outage, How-to, Account/Access, Feature request, Other). If you don't have one, I can start with that default set."

3. "How do you set priority, and what are your SLA targets? For example: Urgent = outage or payment failure, first response in 1 hour. High = blocked workflow, 4 hours. Normal = 1 business day. Low = 2 business days. Tell me your tiers, your SLA clocks, and any VIP accounts that always go Urgent."

**Group B - Voice, automation, and escalation**

4. "Paste 2-3 real replies your team has sent (copy them from your helpdesk). This is how I learn your voice. Also paste any saved replies or macros you want me to reuse. If you don't have samples handy, describe your tone in a sentence and I'll draft something for you to edit."

5. "By default I draft every reply for an agent to review and send. Are there any categories you'd like me to AUTO-SEND without review? (Most teams start with none, then opt in low-risk ones like simple how-to once they trust the drafts.) I will still never auto-send anything that's urgent, angry, ungrounded, or that makes a promise."

6. "How should escalations route, and what always needs human approval? For example: Urgent tickets get assigned to the on-call queue and pinged in #support-urgent. Refunds, credits, discounts, and committed dates always stay as a draft for a human. Tell me your routing and your no-auto-promise list."

7. "When and where should I post the Voice-of-Customer digest? (For example: every Monday 9 AM to #voice-of-customer.)"

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Helpdesk: [helpdesk_system]
> - Knowledge base: [kb_source] at [kb_location]
> - Categories: [category_taxonomy]
> - Priority + SLA: [priority_rules] / [sla_targets]
> - Voice: [1-line summary], macros: [yes/no]
> - Auto-send categories: [auto_send_categories or 'none - all drafts']
> - Escalation routing: [escalation_routing]
> - Always need approval: [approval_required]
> - VoC digest: [voc_cadence] to [voc_channel]
>
> Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

helpdesk_system: "[Zendesk | Intercom | Freshdesk | Help Scout | other]"

kb_source: "[help center | Notion | Confluence | Google Docs | Guru | other]"
kb_location: "[link or path to the knowledge base]"

category_taxonomy: |
  [The user's category list, one per line, or use the default below if they didn't specify:
  Billing, Bug/Outage, How-to, Account/Access, Feature request, Other]

priority_rules: |
  [The user's priority tiers and what lands a ticket in each, or use the default in CLAUDE.md Step 3 if they didn't specify]

vip_rules: |
  [Accounts or domains that always go Urgent, or "None configured."]

sla_targets: |
  [First-response SLA per priority tier, e.g. Urgent 1h, High 4h, Normal 1 business day, Low 2 business days]

reply_voice: |
  [1-2 line summary of tone, plus the user's pasted reply samples verbatim below:
  ...]

reply_macros: |
  [The user's saved replies / macros verbatim, or "None - draft fresh each time."]

auto_send_categories: "[comma-separated category names, or 'none' for all-drafts]"

approval_required: |
  [Actions that always stay a draft and need a human, e.g. refunds, credits,
  discounts, committed dates, policy exceptions. Default: refunds, credits,
  discounts, dates, policy exceptions.]

escalation_routing: |
  [How Urgent / churn-risk / ungrounded tickets get assigned or tagged, and
  which channel gets pinged.]

voc_channel: "[Slack channel or DM for the digest and escalation alerts]"
voc_cadence: "[e.g. weekly Monday 9 AM]"
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **[helpdesk_system]** - to read new tickets, set category and priority, and save draft replies and internal notes
> 2. **[kb_source]** - to search your knowledge base so every draft is grounded and cited
> 3. **Slack** - to post your weekly Voice-of-Customer digest and escalation alerts
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Read the most recent 3 tickets from the helpdesk and confirm you can see them.
- Run one test search against the knowledge base and confirm you can retrieve an article with its title and link.
- Confirm you can save a draft / internal note (do not post a draft on a real ticket unless the user asks).
- Confirm the VoC Slack channel is reachable.

Report back what you found:

> "Connected and verified:
> - Helpdesk: [N] recent tickets visible
> - Knowledge base: search returned [article title] - citations will work
> - Drafting: authorized to save drafts and internal notes
> - Slack: [voc_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "This agent runs on new tickets as they come in. To see exactly what it would do before anything sends or changes, try this prompt:
>
> *'Pull the last 10 tickets but do NOT send anything and do NOT change any ticket. Show me how you'd categorize and prioritize each one, the draft reply you'd write, which KB article you'd ground it in, and any KB gaps you'd flag.'*
>
> Once the drafts and citations look right, let it start triaging for real - everything will land as a draft for your team to review unless you opted a category into auto-send."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
