---
name: agent-onboarding
description: 'First-run setup for Document Chaser. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding — Document Chaser

You are running the first-time setup for the Document Chaser agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Document Chaser does:

> "Welcome to Document Chaser. This agent runs every weekday morning, checks your tracker for documents that are still owed, sends personalized nudges in your voice to counterparties who haven't delivered, verifies received docs against your rules, and escalates anyone who goes unresponsive — all while posting you a daily digest so you're never surprised.
>
> It works for accounting (client tax docs), insurance (submissions), healthcare (prior auth), financial services (KYC), HR onboarding, vendor compliance, or any custom document collection workflow.
>
> I need to ask you a few setup questions. This takes about 15–20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A — About you and your workflow**

1. "What's your name and role, and what kind of documents are you chasing? (For example: accountant chasing client tax docs, HR coordinator collecting onboarding paperwork, insurance broker collecting submissions, vendor manager collecting COIs and W-9s.) A sentence or two is fine."

2. "Which systems do you use? I need to know:
   - **Tracker** — where you track who owes what (Airtable, Notion, Google Sheets, Salesforce, HubSpot, or something else)
   - **Document storage** — where received docs land (Google Drive, Dropbox, SharePoint, Box, or something else)
   - **Email** — Gmail or Outlook
   - **Slack** — which channel or DM should get the daily digest, and who is the escalation owner when someone goes fully unresponsive (Slack handle)?"

**Group B — Cadence, verification, and your voice**

3. "How aggressively should I chase? Pick a cadence:
   - **Gentle** — nudge every 7 days, max 4 nudges before escalating
   - **Standard** — nudge every 4 days, max 5 nudges before escalating
   - **Aggressive** — nudge every 2 days, max 6 nudges (escalate to your owner after 3 with no response)
   
   Standard is the right default for most workflows."

4. "Should I verify received documents before marking them complete? If yes, describe what 'correct' looks like for each document type you handle. (For example: W-9 must have Name, TIN, signature, and date. COI must show your company as certificate holder and coverage above $2M.) If you'd rather just log receipt and let a human verify, say so."

5. "Paste 2–3 actual nudges you've sent before — copy them from your sent folder. This is the most important setup step: I'll mirror your exact tone, phrasing, and sign-off. If you don't have samples handy, describe your style in a sentence and I'll draft something for you to edit."

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Use case: [use_case]
> - Tracker: [tracker_system] at [tracker_location]
> - Doc storage: [doc_storage_system] at [doc_storage_location]
> - Email: [email_provider], signed [sender_signature]
> - Digest + escalations: [digest_channel], escalation owner [escalation_owner]
> - Cadence: [nudge_cadence]
> - Verification: [enabled/disabled]
> - Voice: [1-line summary of tone/style]
>
> Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below — do not skip fields.

```yaml
## Your context

use_case: "[accounting | insurance | healthcare | financial_services | hr_onboarding | vendor_compliance | custom]"

tracker_system: "[Airtable | Notion | Google Sheets | Salesforce | HubSpot | other]"
tracker_location: "[base/page/DB name]"
tracker_schema: |
  [Describe the columns as the user provided, or use the default schema below if they didn't specify:
  Each row represents one document owed by one counterparty.
  Columns: Counterparty (text), Counterparty email (email), Document type (single select),
  Status (single select — Outstanding | Received | Verified | Failed | Escalated),
  Date requested (date), Last nudge sent (date), Nudges sent count (number),
  Doc storage link (URL), Notes (long text)]

doc_storage_system: "[Google Drive | Dropbox | SharePoint | Box | other]"
doc_storage_location: "[folder path or root]"

email_provider: "[Gmail | Outlook]"
sender_signature: "[exact sign-off from user's samples]"

nudge_cadence: "[gentle | standard | aggressive]"

escalation_owner: "[Slack handle]"

verify_received_docs: [true | false]
verification_rules: |
  [Rules per doc type as described by the user, or "Not configured — mark as Received on receipt." if disabled]

digest_channel: "[Slack channel or DM]"

voice_samples: |
  [Paste the user's actual nudge samples verbatim here]

nudge_content_rules: |
  Every nudge must include:
  - What's needed (specific list, not "your documents")
  - Why we need it (the deadline or consequence)
  - How they can provide it (link, email reply, etc.)
  - Who to ask if stuck
  
  Never include:
  - Passive-aggression ("just following up AGAIN")
  - Guilt or blame
  - Threats unrelated to actual consequence
  - Anything that contradicts the user's voice samples
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect your accounts. I'll need access to:
> 1. **[tracker_system]** — to read outstanding rows and update statuses
> 2. **[doc_storage_system]** — to scan for newly received documents
> 3. **[email_provider]** — to send nudges and acknowledgements (I'll draft, you can review before anything sends if you prefer)
> 4. **Slack** — to post your daily digest and tag your escalation owner
>
> Connect each one via the Accounts panel in Gamut. Let me know when they're all connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Read the first 3 rows from the tracker and confirm you can see them.
- List the most recent file in doc storage.
- Confirm email send authorization (do not send a test email unless the user asks).
- Confirm Slack digest channel is reachable.

Report back what you found:

> "Connected and verified:
> - Tracker: [N] rows visible, [N] outstanding
> - Doc storage: last file was [filename] on [date]
> - Email: authorized to send as [sender]
> - Slack: [digest_channel] is reachable
>
> Everything looks good. You're set up."

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs every weekday at 8:00 AM. To see exactly what it would do before it sends anything, try this prompt:
>
> *'Check my tracker and document storage but do NOT send any nudges and do NOT update any rows. Show me what you'd do today — which counterparties would get a nudge, which docs you'd verify, which you'd escalate.'*
>
> Once the plan looks right, run it again without the skip — that's day one."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
