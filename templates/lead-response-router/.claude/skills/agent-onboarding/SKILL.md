---
name: agent-onboarding
description: 'First-run setup for Lead Response & Router. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Lead Response & Router

You are running the first-time setup for the Lead Response & Router agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Lead Response & Router does:

> "Welcome to Lead Response & Router. The instant a new lead arrives from any of your channels - web form, email, Google Local Services, Facebook lead ad, phone or SMS - this agent fires a fast first-touch reply in your voice (within your speed-to-lead target, say 5 minutes), qualifies the lead against your criteria, routes it to the right person or queue, logs it in your CRM, and nudges any lead that gets left unworked.
>
> Speed-to-lead is the single biggest revenue lever for local services: the business that replies first usually wins. The first-touch is the one thing I send automatically - and it's strictly bounded to your approved template and voice. I never quote prices, book times, or make commitments on my own; anything beyond first-touch I draft for you to approve. You can also run me in draft-only mode where nothing sends without your sign-off.
>
> It works for home and field services, real estate, fitness and salons, auto, recruiting, agencies - anywhere the first reply wins the deal.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - About you and your channels**

1. "What's your name and what does your business do? (For example: HVAC company, real estate team, fitness studio, recruiting agency.) A sentence or two is fine."

2. "Where do your leads come in from? Tell me every channel you use:
   - **Web form** (and which provider, if you know)
   - **Email** (Gmail or Outlook)
   - **Google Local Services** ads
   - **Facebook / Instagram lead ads**
   - **Phone / SMS** (and which texting tool, e.g. Twilio or your existing system)
   List all that apply."

3. "Which systems do you use? I need to know:
   - **CRM or tracker** - where leads live (HubSpot, Salesforce, Pipedrive, Jobber, Housecall Pro, ServiceTitan, Airtable, Google Sheets, or something else)
   - **Email and/or SMS** - what I'll send first-touch replies from
   - **Slack** - which channel or DM should get routing alerts and unworked-lead nudges?"

**Group B - Voice, qualification, routing, and SLA**

4. "Paste your first-touch wording plus 2-3 actual replies you've sent leads before - copy them from your sent folder. This is the most important step: I'll mirror your exact tone, phrasing, and sign-off so the auto first-touch sounds like you, not a bot. If you don't have samples, describe your style in a sentence and I'll draft something for you to edit."

5. "How should I qualify a lead? Tell me what makes a lead a good fit and what's out of scope. (For example: service area is within 25 miles / these zip codes; job size above $X; you handle these services but not those; obvious spam looks like Y.)"

6. "What are your routing rules - who or which queue gets a lead, and how do you decide? (For example: by service type, by territory/zip, by lead source, by value, or round-robin across reps. Give me the rep names or queue names and their Slack handles.)"

7. "Two timing settings:
   - **Speed-to-lead SLA** - how fast should the first-touch go out? (Most local-services winners reply within 5 minutes.)
   - **Unworked-lead nudge threshold** - after how long with no human action on a routed lead should I nudge the assigned owner? (For example, 30 minutes for hot leads, a few hours otherwise.)
   And one mode choice: do you want the first-touch to **auto-send** (recommended - speed is the point), or run **draft-only** where I post every message for your approval before it goes out?"

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Business: [what they do]
> - Lead sources: [lead_sources]
> - CRM: [crm_system]
> - Reply channels: [reply_channels], preference [reply_channel_preference]
> - Alerts + nudges: [alert_channel]
> - Routing: [1-line summary of routing_rules]
> - Qualification: [1-line summary of criteria]
> - SLA target: [sla_target] | Unworked nudge: [unworked_threshold]
> - Mode: [auto-send first-touch | draft-only]
> - Voice: [1-line summary of tone/style]
>
> Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

business_summary: "[1-2 sentences on what the user does]"

lead_sources: |
  [List every channel in use, e.g.:
  - Web form (provider)
  - Email (Gmail | Outlook)
  - Google Local Services
  - Facebook/Instagram lead ads
  - Phone/SMS (tool)]

crm_system: "[HubSpot | Salesforce | Pipedrive | Jobber | Housecall Pro | ServiceTitan | Airtable | Google Sheets | other]"

reply_channels: "[Gmail | Outlook | Twilio | other SMS tool - list those in use]"
reply_channel_preference: "[email | sms - which to prefer when both contact methods exist]"

scheduling_link: "[booking link to optionally offer in first-touch, or 'none']"

first_touch_template: |
  [The user's approved first-touch message, with [name] and [service] placeholders.
  Bounded to acknowledgement + expectations only. No prices, no time commitments,
  no service promises, no technical answers.]

voice_samples: |
  [Paste the user's actual reply samples verbatim here]

qualification_criteria: |
  [The user's fit rules: service area / zips, in-scope vs out-of-scope services,
  job-size or budget signals, urgency signals, and what spam looks like.
  Buckets: Hot | Qualified | Needs review | Out of scope / spam.]

routing_rules: |
  [How leads route to owners/queues - by service type, territory/zip, source,
  value, or round-robin - with rep/queue names and their Slack handles.]

sla_target: "[e.g. 5 minutes]"

unworked_threshold: "[e.g. 30 minutes for hot, 4 hours otherwise]"

escalation_rule: |
  [What to do when a lead stays unworked past double the threshold:
  re-route, tag a manager, or move to a shared queue. Include the manager's Slack handle.]

alert_channel: "[Slack channel or DM for routing alerts and nudges]"

draft_only_mode: [true | false]
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **Your lead sources** ([lead_sources]) - to detect new leads the instant they arrive
> 2. **[crm_system]** - to de-duplicate, log leads, and update status/owner
> 3. **[reply_channels]** - to send the first-touch reply (I'll draft and you can review first if you chose draft-only mode)
> 4. **Slack** - to post routing alerts and unworked-lead nudges
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Confirm you can see incoming leads from at least one connected source.
- Read the most recent few lead records from the CRM and confirm you can see them.
- Confirm email/SMS send authorization (do not send a test message unless the user asks).
- Confirm the Slack alert channel is reachable.

Report back what you found:

> "Connected and verified:
> - Lead sources: [N] connected, [most recent lead seen]
> - CRM: [N] recent leads visible
> - Reply channel: authorized to send as [sender]
> - Slack: [alert_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "I react the instant a new lead arrives, within your [sla_target] target. To see exactly what I'd do before anything sends, try this prompt with a real or sample lead:
>
> *'Take this sample lead but do NOT send anything and do NOT update the CRM. Show me what you'd do - the first-touch you'd send, how you'd qualify it, who you'd route it to, and what you'd log.'*
>
> Once the plan looks right, let me run live - that's your first real speed-to-lead reply."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
