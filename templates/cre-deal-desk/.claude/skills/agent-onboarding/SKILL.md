---
name: agent-onboarding
---

# Agent Onboarding — CRE Deal Desk

Welcome the broker and explain that this short setup (~5 minutes) configures the agent for their firm, market, and preferred deal format. After onboarding, the agent will be ready to pull comps and draft BOVs or OMs on demand.

## Interview

Ask the following questions conversationally — one topic at a time, not as a numbered list dump. Wait for each answer before moving to the next.

1. **Broker intro**
   - What is your name?
   - What is your brokerage or firm name?
   - What is your primary asset type focus? (office, industrial, retail, multifamily, mixed-use, or other)

2. **Market geography**
   - Which metro areas or regions do most of your deals fall in? (List as many as apply — e.g., "Chicago suburbs, Milwaukee, Indianapolis")

3. **BOV vs. OM preference**
   - Which deliverable do you produce more often — a Broker Opinion of Value (BOV) or an Offering Memorandum (OM)?
   - Do you have a sample BOV or OM you'd like to use as a format reference? If so, please upload it now (PDF or Word). If not, the agent will use a standard format.

4. **Comp search defaults**
   - What is your default comp search radius? (e.g., 1 mile, 3 miles, 5 miles, or "by submarket")
   - What is your default comp lookback period? (e.g., 12 months, 24 months, 36 months)

5. **CRM**
   - What CRM do you use to track deals? (Salesforce, Buildout, Apto, ClientLook, a spreadsheet, or other)
   - If Salesforce: do you have API access or use it via browser? Note any object names used for property listings or deal records.

6. **Google Drive folder**
   - What is the Google Drive folder where completed BOVs, OMs, and tour kits should be saved? Please share the folder name or URL.

7. **Slack channel**
   - What Slack channel should the agent post deal-ready notifications to? (e.g., #deal-desk, #listings, #team)

8. **Integrations**
   - Connect Google Drive so the agent can save deliverables. (Prompt the user to authorize via the Google Drive integration.)
   - Connect Slack so the agent can post notifications. (Prompt the user to authorize via the Slack integration.)

## After the interview

Summarize the collected configuration back to the broker for confirmation:

> "Here's what I've captured — let me know if anything needs adjusting before I save it:"
> - Name / firm / asset type
> - Markets
> - Primary deliverable format + sample template (if uploaded)
> - Comp defaults (radius + lookback)
> - CRM setup
> - Drive folder
> - Slack channel

Once confirmed:

1. **Write the `## Your context` section of `CLAUDE.md`** with all collected details in a clear, labeled format. Replace the placeholder comment entirely.

   Example structure:
   ```
   ## Your context

   - **Broker:** [Name], [Firm]
   - **Primary asset type:** [type]
   - **Markets:** [list]
   - **Preferred deliverable:** [BOV / OM]
   - **Sample format:** [filename or "standard format"]
   - **Comp defaults:** [radius], [lookback period]
   - **CRM:** [name and access method]
   - **Drive folder:** [folder name or URL]
   - **Slack channel:** [channel name]
   ```

2. **Write `config.json`** at the workspace root with the same data in structured form:

   ```json
   {
     "broker": {
       "name": "",
       "firm": "",
       "assetTypeFocus": ""
     },
     "markets": [],
     "preferredDeliverable": "BOV",
     "sampleFormatFile": null,
     "compDefaults": {
       "radiusMiles": null,
       "lookbackMonths": null
     },
     "crm": {
       "name": "",
       "accessMethod": ""
     },
     "drive": {
       "folderName": "",
       "folderUrl": ""
     },
     "slack": {
       "channel": ""
     }
   }
   ```

3. Confirm setup is complete and offer to run the first task:

   > "You're all set! To get started, try: 'Pull comps and draft a BOV for [property address].'"
