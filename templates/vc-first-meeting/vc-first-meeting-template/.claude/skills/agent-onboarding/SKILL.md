# Skill: agent-onboarding

Run this skill once when the VC First Meeting Agent is first imported. It collects fund context, preferences, and integrations, then writes everything to `config.json` so the main agent has what it needs to operate.

## When to run

Run automatically on first use if `config.json` does not exist or is empty. The user can also invoke it manually at any time to update their configuration ("re-run onboarding", "update my fund thesis", etc.).

## How to run

Work through the sections below conversationally — do not present them as a wall of questions. Ask one section at a time, confirm the answers, then move on. Keep it efficient: if a user's answer covers multiple fields, capture them all and don't re-ask.

After completing all sections, write `config.json`, confirm to the user, and run the smoke test.

---

## Section 1 — Fund context

**Check first**: look for an existing `config.json` in `/workspace/` or a `thesis-screener-config.json` in the workspace root. If found, read it and pre-fill what you can — tell the user what you imported and ask them to confirm or correct it.

Ask:

1. **Fund name**: "What's your fund's name?"

2. **Fund thesis**: "Describe your investment thesis in plain language — what does your fund invest in, and why?" (Encourage a 2–4 sentence answer. This will be used verbatim in briefs and deal records.)

3. **Thesis criteria**: "What are your must-have criteria for a deal? List them — things like stage, sector, check size, geography, team requirements, market size, business model, etc. Mark which are hard dealbreakers vs. strong preferences."

   Capture each criterion as:
   ```
   { "criterion": "[name]", "must_have": true/false, "notes": "[any clarification]" }
   ```

4. **Stage focus**: "What stages do you invest at?" (e.g., Pre-Seed, Seed, Series A)

5. **Sector focus**: "What sectors or verticals do you focus on? List them." (e.g., B2B SaaS, Climate, Fintech, Healthcare IT)

6. **Check size**: "What's your typical check size range?"

7. **Geography**: "Any geography focus or restrictions?"

8. **Partner name and email**: "What's your name, and what email address should be used for follow-up email drafts?" (Email is optional — skip if they don't want email drafts.)

---

## Section 2 — Deal record preferences

Ask:

1. **Custom fields**: "The default deal record captures: company basics, team assessment, problem/solution, business model, traction, funding, thesis fit, concerns, next steps, and follow-up questions. Are there any custom fields you want added — things your fund always tracks that aren't in that list?"

   If yes, capture each as `{ "field_name": "[name]", "description": "[what to capture]" }` and add to config as `custom_fields`.

2. **Most important fields**: "Are there fields you want highlighted or prioritized — e.g., you always care most about team, or market size is your first filter?" (Optional — used to order sections in the deal record output.)

---

## Section 3 — CRM integration

Ask:

1. "Do you use a CRM for tracking deals? If so, which one — Notion, Airtable, HubSpot, Salesforce, or something else?"

   - If **none** / files only: set `crm_name: null`. Note that deal records will be saved as markdown files only.
   - If **Notion**: ask for the database URL or ID where deals should be written. Ask if they want to map any custom properties. Guide them to connect the Notion integration if not already connected.
   - If **Airtable**: ask for the base ID and table name. Guide them to connect Airtable if needed.
   - If **HubSpot**: confirm the HubSpot integration is connected. Ask if deals should go to a specific pipeline/stage.
   - If **Salesforce**: confirm the Salesforce integration is connected. Ask for the object type (Opportunity, custom object, etc.).
   - If **other**: note the CRM name and set `crm_name` to the name. Flag that CRM push may require custom configuration.

2. After collecting CRM details: attempt a test connection. If the CRM is connected, confirm it. If not connected, tell the user what to do to connect it and set `crm_name: null` for now with a note to re-run onboarding after connecting.

---

## Section 4 — Follow-up email drafts

Ask:

1. "After a first meeting, should the agent automatically draft a follow-up email for you to review? It will reference specifics from the meeting and note any info requests. Default is yes — do you want this?"

   Set `draft_followup_emails: true` (default) or `false`.

2. If yes and `partner_email` was not collected in Section 1, ask for it now.

---

## Section 5 — File paths

Ask:

1. "Where should pre-meeting briefs be saved? Default is `/workspace/briefs/` — is that fine, or do you want a different path?"

2. "Where should deal records be saved? Default is `/workspace/deals/` — same question."

Create both directories if they don't exist.

---

## Write config

After collecting all sections, write `/workspace/config.json` with the following structure:

```json
{
  "fund_name": "",
  "fund_thesis": "",
  "thesis_criteria": [
    { "criterion": "", "must_have": true, "notes": "" }
  ],
  "stage_focus": [],
  "sector_focus": [],
  "check_size": "",
  "geo_focus": "",
  "partner_name": "",
  "partner_email": null,
  "custom_fields": [],
  "priority_fields": [],
  "crm_name": null,
  "crm_config": null,
  "draft_followup_emails": true,
  "briefs_path": "/workspace/briefs/",
  "deals_path": "/workspace/deals/",
  "_configured_at": "[ISO timestamp]",
  "_version": "1.0.0"
}
```

Confirm to the user: "Config saved. Here's a summary of what I recorded:" — then show a clean human-readable recap of the key settings (fund name, thesis summary, criteria count, CRM, email drafts on/off, file paths).

---

## Smoke test

After writing config, run a quick smoke test to confirm everything is working:

1. Tell the user: "Let me run a quick smoke test with a fake company to confirm everything is set up correctly."

2. **Pre-meeting test**: Research a clearly fictitious company — "Acme AI (fictional test company — a seed-stage AI infrastructure startup)" — and produce a brief. Use the fund's thesis criteria from config to generate the Thesis Fit section. Note clearly that this is a test with fake data.

3. **Post-meeting test**: Take the following minimal fake notes and produce a structured deal record:

   ```
   Met with Acme AI. Jane Doe (CEO, ex-Google Brain) and Bob Smith (CTO, ex-Stripe).
   Building AI infra for mid-market SaaS. $200K ARR, 12 customers. Raising $3M seed.
   No valuation discussed. Main concern: crowded space. Next step: send deck.
   ```

4. Show both outputs to the user and ask: "Does this look right? Any adjustments to the format or content?"

5. If the user requests changes, update config and/or note the preference, and confirm.

---

## Re-running onboarding

If the user runs onboarding again after initial setup, load the existing `config.json` and present the current values. Ask which sections they want to update rather than starting from scratch. Only overwrite fields that the user explicitly changes.
