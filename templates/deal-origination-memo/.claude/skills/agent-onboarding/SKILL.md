---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome the user to the Deal Origination & Memo agent and collect the configuration needed to personalize it for their firm. Work through the interview below conversationally — ask 2–3 questions at a time, confirm answers before moving on, and proceed at the user's pace.

## Interview Questions

Ask the following, grouping naturally:

**Round 1 — Firm basics**
1. What is your name?
2. What is your firm's name?
3. What type of firm are you? (PE buyout / venture capital / growth equity / investment banking / M&A advisory / other)

**Round 2 — Investment thesis or mandate**
4. Describe your investment thesis or current M&A mandate: target sectors, geographies, revenue/EBITDA size criteria, ownership preferences, and any deal strategy notes (e.g., founder-owned, platform vs. add-on, control vs. minority).

**Round 3 — Memo format**
5. What sections does your standard IC memo include, and in what order? (e.g., Executive Summary, Business Overview, Market & Competitive Landscape, Investment Thesis & Value Creation, Risks & Mitigants, Financial Summary, Recommendation)
6. Is there a preferred length or page target per memo?
7. Do you have a sample memo template you'd like to upload so the agent can match your firm's exact format? (If yes, share it now; if no, we'll use the section headings you provide.)

**Round 4 — Tools & integrations**
8. Which CRM does your team use to track deals and pipeline? (Affinity / Attio / HubSpot / spreadsheet / other)
9. What is the Google Drive folder URL where memos should be saved?
10. Which Slack channel should origination updates and deal alerts go to? (e.g., #origination, #deal-flow)

**Round 5 — Connections**
11. Connect Google Drive so the agent can save memos and retrieve documents.
12. Connect Slack so the agent can post origination alerts and diligence nudges to your channel.

Say: "I'll connect Google Drive now." and trigger the Google Drive connection flow.
Say: "I'll connect Slack now." and trigger the Slack connection flow.

## After the Interview

Once all answers are collected and connections are confirmed, write the configuration to two places:

### 1. Update CLAUDE.md

Append the collected context under the `## Your context` section of `/workspace/CLAUDE.md`. Use this format:

```
User: [name]
Firm: [firm name]
Firm type: [type]
Investment thesis: [thesis summary]
Memo format: [section headings in order, length target if provided]
CRM: [CRM name]
Drive folder: [URL]
Slack channel: [channel name]
```

If the user uploaded a sample memo, note the file path or Drive link.

### 2. Write config.json

Create or update `/workspace/.claude/config.json` with:

```json
{
  "firm": "[firm name]",
  "firmType": "[type]",
  "thesis": "[thesis summary]",
  "memoSections": ["[section 1]", "[section 2]", "..."],
  "memoLengthTarget": "[length or null]",
  "crm": "[CRM name]",
  "driveFolderUrl": "[Drive folder URL]",
  "slackChannel": "[channel name]",
  "onboardedAt": "[ISO timestamp]"
}
```

### 3. Confirm and orient

After saving, tell the user:
- Configuration is saved.
- Suggest their first action: "You're ready to go. Try asking: 'Source a list of 20 [sector] companies in [geography] with [size range] revenue for our mandate.'"
- Remind them they can update their thesis or memo format at any time by telling you directly.
