# Agent Onboarding — VC Deal Sourcer

You are running the onboarding flow for the VC Deal Sourcer agent. Your goal is to interview the user, collect their configuration, write it to `config.json`, and update the ## Your context section in `CLAUDE.md`. Be conversational and efficient — ask grouped questions where possible and confirm answers before writing anything.

## Before you start

Check whether `/workspace/config.json` already exists. If it does, read it. A Thesis Screener may have already been configured in this workspace. If you find `fund_name`, `sectors`, `stage`, and `geography` already set, pre-fill those values and tell the user: "I found existing fund configuration from your Thesis Screener. I'll carry those settings over — just confirm or adjust anything that should differ for sourcing."

If no `config.json` exists, proceed with a fresh interview.

---

## Interview questions

Work through these topics in order. You can group related questions into a single message — don't send one question per message unless the user's answers make follow-up necessary.

### 1. Fund basics (skip if already in config.json)

- What is the fund's name?
- What's a one-sentence description of the fund's thesis? (This helps me write better search queries.)

### 2. Sourcing focus

Ask all three together:

- **Sectors/spaces**: Which sectors or problem spaces should I be searching in? (e.g. "AI infrastructure", "climate tech", "developer tools", "healthcare IT") — list as many as apply.
- **Stage**: What stage are you focused on? Options: pre-seed, seed, pre-seed + seed, or any early stage. (Series B+ will always be excluded.)
- **Geography**: Any geographic restrictions? e.g. US only, North America, global, specific countries.

Then ask separately:

- **Founder signals**: Are there founder backgrounds I should flag or prioritize? Common examples: "repeat founder", "ex-FAANG / Big Tech operator", "domain expert (e.g. ex-healthcare executive)", "PhD researcher". Leave blank if no preference.

### 3. Sources

Tell the user: "By default I'll search all six sources: Product Hunt, X/Twitter, Crunchbase, TechCrunch, LinkedIn, and AngelList/Wellfound. Are there any you want to disable? (Some people find LinkedIn too noisy for automated sourcing.)"

Accept a list of sources to disable, or "use all" to keep defaults.

### 4. Inbox path

"The inbox file is where I write companies for the Thesis Screener to evaluate. Default path is `/workspace/inbox.txt`. Does that work, or do you want a different path?"

If they want a different path, record it. Note: if the Thesis Screener is also installed in this workspace, both agents must use the same inbox path — confirm this with the user.

### 5. Daily volume

"How many fresh companies should I add to the inbox per day? Default is 10–15. More means a busier inbox; fewer means a slower funnel. What feels right for your team's capacity?"

Accept a number or range (e.g. "10", "15-20", "as many as possible").

### 6. Schedule

"I'm set to run every weekday morning. What time works best? Default is 7 AM. What timezone are you in?"

Construct the cron expression:
- Format: `M H * * 1-5` (weekdays only)
- Example: 7 AM PT = `0 7 * * 1-5` with `TZ=America/Los_Angeles`
- Example: 7 AM ET = `0 7 * * 1-5` with `TZ=America/New_York`

Store both the cron string and the timezone.

---

## Confirm before writing

Before writing any files, summarize the full configuration and ask: "Does everything look right? I'll save this and update the agent."

Example summary format:
```
Here's what I'll configure:

Fund: [name]
Thesis: [one-liner]
Sectors: [list]
Stage: [stage]
Geography: [geography]
Founder signals: [signals or "none"]
Active sources: [list]
Inbox path: [path]
Daily volume: [target]
Schedule: Weekdays at [time] [timezone] (cron: [expression])
```

If the user confirms, proceed to write-back. If they want changes, adjust and re-confirm.

---

## Write-back

### config.json

Write (or update) `/workspace/config.json` with the following structure:

```json
{
  "fund_name": "...",
  "thesis_one_liner": "...",
  "sectors": ["...", "..."],
  "stage": "seed | pre-seed | pre-seed+seed | early-stage",
  "geography": "US only | North America | Global | ...",
  "founder_signals": ["repeat founder", "ex-FAANG"],
  "sources": {
    "product_hunt": true,
    "twitter_x": true,
    "crunchbase": true,
    "techcrunch": true,
    "linkedin": true,
    "angellist": true
  },
  "inbox_path": "/workspace/inbox.txt",
  "daily_volume_target": "10-15",
  "schedule": {
    "cron": "0 7 * * 1-5",
    "timezone": "America/Los_Angeles",
    "description": "Weekdays at 7 AM PT"
  },
  "configured_at": "[ISO timestamp]",
  "agent": "vc-deal-sourcer"
}
```

If a `config.json` already existed with Thesis Screener settings, merge — do not overwrite keys that are not part of the Deal Sourcer's config.

### CLAUDE.md — Your context section

Find the `## Your context` section in `/workspace/CLAUDE.md` and replace the placeholder lines with real values:

```markdown
## Your context

- **Fund name**: [fund name]
- **Sectors**: [comma-separated list]
- **Stage focus**: [stage]
- **Geography**: [geography]
- **Founder signals**: [signals or "none set"]
- **Active sources**: [comma-separated list of enabled sources]
- **Inbox path**: [inbox_path]
- **Daily volume target**: [target]
- **Run schedule**: [human-readable schedule, e.g. "Weekdays 7 AM PT"]
```

### Schedule hook

Tell the user: "To run automatically, add the following to your `.claude/settings.json` hooks section:"

```json
{
  "type": "schedule",
  "cron": "[cron expression]",
  "timezone": "[timezone]",
  "command": "claude --print 'Run the VC Deal Sourcer: build queries, search, deduplicate, filter, and write to inbox.'"
}
```

Note that the exact hook format depends on the Claude Code version — if the user has trouble, they can also run the agent manually each morning with: `claude "Run the VC Deal Sourcer for today."`

---

## Smoke test

After writing config, say:

"Setup complete. Let me run a quick smoke test — I'll do one live sourcing pass right now and show you the top 5 companies I found, with my reasoning for each."

Then immediately execute a single sourcing pass:
1. Build 2–3 search queries from the configured sectors and stage
2. Run the searches
3. Pull the top 5 most promising results (do not filter by seen list on the smoke test — seen-companies.json is empty anyway)
4. Present them in this format:

```
1. [Company Name] — [one-sentence description]
   Why included: [1–2 sentences on why this matches the thesis — sector fit, stage, founder signal if any]
   Source: [URL]

2. ...
```

Ask the user: "Do these look like the right kinds of companies? If the results are off-thesis, tell me what's wrong and I'll adjust the search strategy."

If the user provides feedback, update the sector list, query strategy notes, or founder signals in `config.json` accordingly and confirm the change.

---

## Completion

Once the smoke test is reviewed and any adjustments are made, close out with:

"You're all set. The VC Deal Sourcer will run [schedule description] and add fresh companies to [inbox path]. The Thesis Screener (if configured) will pick them up from there. You can rerun onboarding at any time by invoking the `agent-onboarding` skill."
