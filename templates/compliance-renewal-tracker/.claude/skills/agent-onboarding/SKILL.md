---
name: agent-onboarding
description: 'First-run setup for Compliance / Renewal Tracker. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding -- Compliance / Renewal Tracker

You are running the first-time setup for the Compliance / Renewal Tracker agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what the agent does:

> "Welcome to Compliance / Renewal Tracker. This agent runs every weekday morning, reads your tracker, and recomputes how long each license, certificate of insurance, certification, or registration has before it expires. As items cross your lead-time thresholds, it nudges the person responsible -- consolidating everything they own into one email with exact dates and a link to the document on file. Anything that lapses gets flagged and escalated the same day, and you get a status digest so nothing expires quietly.
>
> It works for a single business or a whole network -- franchises and multi-unit operators, trades carrying licenses and insurance, contractors managing COIs, healthcare and logistics operators, or any org keeping paperwork current across many owners and jurisdictions.
>
> Two things up front: I never file, submit, or renew anything myself -- I track and nudge. And this is operational tracking, not legal or compliance advice.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A -- Scope, item types, and systems**

1. "What are you tracking, and at what scope? Is this one business, or a network/franchise of multiple locations? And which item types apply: licenses, certificates of insurance (COIs), professional certifications, registrations, permits, or a mix? A sentence or two is fine."

2. "Which systems do you use? I need to know:
   - **Tracker** -- where you track items and expiry dates (Airtable, Notion, Google Sheets, Smartsheet, or something else), and the name of the base/sheet
   - **Document storage** -- where the actual certs and COIs live (Google Drive, Dropbox, SharePoint, Box, or something else)
   - **Email** -- Gmail or Outlook
   - **Slack** -- which channel or DM should get the status digest, and who is the escalation owner for lapses and stalled renewals (Slack handle)?"

**Group B -- Lead times, cadence, owners, and voice**

3. "What renewal lead-time tiers do you want? This is how far ahead I start nudging. A common setup is **90 / 60 / 30 / 7 days** before expiry -- I nudge when an item crosses each threshold. Tell me your tiers, or take the default."

4. "How aggressively should I re-nudge within a tier? Pick a cadence:
   - **Gentle** -- re-nudge every 14 days within a tier; escalate at the 7-day tier
   - **Standard** -- re-nudge every 7 days within a tier; escalate at the 7-day tier
   - **Aggressive** -- re-nudge every 3 days; escalate once an item hits the 30-day tier with no response
   
   Standard is the right default for most teams. Note: lapses are always escalated the same day regardless of cadence."

5. "Who owns renewals? Tell me how to find the responsible owner for each item -- is there an Owner column in your tracker, or do certain item types map to certain people? And paste 1-2 actual nudge or reminder emails you've sent before so I match your tone. If you don't have samples, describe your style in a sentence and I'll draft something for you to edit."

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Scope: [org_scope]
> - Item types: [item_types]
> - Tracker: [tracker_system] at [tracker_location]
> - Doc storage: [doc_storage_system]
> - Email: [email_provider], signed [sender_signature]
> - Digest + escalations: [digest_channel], escalation owner [escalation_owner]
> - Lead-time tiers: [renewal_lead_times]
> - Cadence: [nudge_cadence]
> - Owner mapping: [1-line summary]
> - Voice: [1-line summary of tone/style]
>
> Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below -- do not skip fields.

```yaml
## Your context

org_scope: "[single business | network/franchise of N locations]"

item_types: "[which apply: licenses | COIs | certifications | registrations | permits | other]"

tracker_system: "[Airtable | Notion | Google Sheets | Smartsheet | other]"
tracker_location: "[base/sheet/page name]"
tracker_schema: |
  [Describe the columns as the user provided, or use the default schema below if they didn't specify:
  Each row represents one compliance item.
  Columns: Item (text), Type (single select -- license | COI | certification | registration | permit),
  Owner (person/email -- who is responsible for renewing it),
  Jurisdiction (text -- state/agency/carrier/location),
  Expiry date (date),
  Status (single select -- Current | Renewal due | Renewal submitted | LAPSED | Escalated | On hold | Not applicable),
  Last nudge sent (date), Nudges sent count (number),
  Doc link (URL -- to the cert/COI in storage), Notes (long text)]

doc_storage_system: "[Google Drive | Dropbox | SharePoint | Box | other]"

email_provider: "[Gmail | Outlook]"
sender_signature: "[exact sign-off from user's samples]"

renewal_lead_times: "[e.g. 90 / 60 / 30 / 7 days before expiry]"

nudge_cadence: "[gentle | standard | aggressive]"

escalation_owner: "[Slack handle]"

owner_mapping: |
  [How to find the responsible owner for each item -- e.g. "Owner column in tracker"
  or "COIs -> Jane (ops), licenses -> location manager per row"]

digest_channel: "[Slack channel or DM]"

voice_samples: |
  [Paste the user's actual nudge/reminder samples verbatim here, or a 1-line style description]
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **[tracker_system]** -- to read items, expiry dates, and update statuses
> 2. **[doc_storage_system]** -- to link the certs and COIs on file and log new ones
> 3. **[email_provider]** -- to send renewal nudges to owners (I draft, nothing sends until you've okayed the first dry-run)
> 4. **Slack** -- to post your status digest and tag your escalation owner
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Read the first 3 rows from the tracker and confirm you can see the Item, Owner, and Expiry date fields.
- Confirm you can reach the document storage location.
- Confirm email send authorization (do not send a test email unless the user asks).
- Confirm the Slack digest channel is reachable.

Report back what you found:

> "Connected and verified:
> - Tracker: [N] rows visible, [N] due within your top lead-time tier, [N] already lapsed
> - Doc storage: reachable
> - Email: authorized to send as [sender]
> - Slack: [digest_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs every weekday at 8:00 AM. To see exactly what it would do before it sends anything, try this prompt:
>
> *'Read my tracker but do NOT send any nudges and do NOT update any rows. Show me what you'd do today -- which items are due for renewal, which would get a nudge, which are lapsed, and which you'd escalate.'*
>
> Once the plan looks right, run it again without the skip -- that's day one."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
