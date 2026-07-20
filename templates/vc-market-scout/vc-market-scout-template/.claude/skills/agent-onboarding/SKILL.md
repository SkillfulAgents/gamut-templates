# Skill: agent-onboarding

Runs automatically on first import. Interviews the user to configure the VC Market Scout, writes `config.json`, connects Gmail, and runs a smoke-test sweep.

---

## Steps

### 1. Check for existing config

Before asking any questions, check whether `/workspace/market-scout/config.json` already exists (e.g. carried over from another VC template in this workspace). If it does, read it and confirm with the user: "I found an existing config — want to reuse these settings or start fresh?"

If reusing, skip to Step 6 (connect Gmail). If starting fresh, continue below.

---

### 2. Fund context

Ask:

> "What sectors does your fund invest in? List as many as apply — e.g. 'B2B SaaS, climate tech, vertical AI, fintech infrastructure'. Be specific: the more precise the sector labels, the better the sweep results."

Then ask:

> "What are 3–5 thesis keywords that capture your fund's angle? These get woven into search queries to surface more relevant signals. Examples: 'workflow automation', 'AI-native infrastructure', 'emissions monitoring', 'embedded finance'."

---

### 3. Competitor funds to monitor

Ask:

> "Which funds are investing in your space that you want to keep tabs on? Could be large generalist funds (a16z, Sequoia, Bessemer, Lightspeed) or sector-specific ones. List the ones whose moves matter most to you."

Prompt for 3–8 funds. Explain: "Each week the agent will search for their recent investments and any public signals about where they're placing bets."

---

### 4. Companies to always track

Ask:

> "Are there specific companies — portfolio companies, competitors, or watchlist names — that should always be included in every sweep, regardless of sector match? These get a dedicated search pass each week."

This is optional. Accept a list or skip.

---

### 5. Digest recipients

Ask:

> "Who should receive the Monday digest? Enter one or more email addresses."

Accept a comma-separated list or a single address.

---

### 6. Schedule

Confirm the default schedule:

> "The digest runs every Monday at 7 AM. What timezone are you in?"

Record the timezone. The default cron is `0 7 * * 1`. If the user wants a different day or time, update the cron accordingly and note it.

---

### 7. Exclusions (optional)

Ask:

> "Anything you want the agent to always filter out? For example: 'crypto/web3', 'consumer hardware', 'anything pre-seed under $500K'. This is optional — leave blank to skip."

---

### 8. Write config.json

Create the directory if needed and write `/workspace/market-scout/config.json`:

```json
{
  "sectors": [],
  "thesis_keywords": [],
  "competitor_funds": [],
  "tracked_companies": [],
  "recipient_emails": [],
  "schedule": {
    "cron": "0 7 * * 1",
    "timezone": "America/Los_Angeles",
    "description": "Every Monday at 7 AM"
  },
  "exclude_topics": []
}
```

Fill in all fields from the user's answers.

---

### 9. Connect Gmail

Tell the user:

> "To deliver the digest, I need access to a Gmail account. I'll connect it now."

Use the available account-connection tools to connect Gmail (or confirm it's already connected). If a non-Gmail SMTP account is preferred, note the SMTP credentials needed and prompt accordingly.

---

### 10. Smoke test

Tell the user:

> "Setup is complete. Let me run a quick sweep right now so you can see what the digest looks like."

Run one full sweep using the configured sectors, competitor funds, and thesis keywords. Do not send the email — instead, print the draft digest inline in the chat so the user can review the format and signal quality.

After printing, ask:

> "Does this look right? Anything you'd adjust — sectors to add, funds to drop, format changes?"

Apply any requested tweaks to `config.json` before closing onboarding.

---

## Outputs

- `/workspace/market-scout/config.json` — full agent configuration
- Gmail connected for digest delivery
- One draft digest shown inline for review
