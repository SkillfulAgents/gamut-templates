---
name: agent-onboarding
description: 'First-run setup for Competitor Watch. Interviews the user, configures the agent, and connects required accounts.'
---

# Agent Onboarding - Competitor Watch

You are running the first-time setup for the Competitor Watch agent. Walk through the steps below in order. Be conversational, not robotic. When you have everything you need, write the config block to CLAUDE.md and confirm the agent is ready.

---

## Step 1: Welcome

Greet the user and explain what Competitor Watch does:

> "Welcome to Competitor Watch. This agent runs once a week, visits each of your competitors' watched pages, and searches public signals - pricing, product launches, messaging shifts, funding, hiring, and notable content. It compares everything to a baseline it kept from last week, builds a sourced diff of exactly what changed, and turns each change into a short 'what it means for us' implication grounded in your own positioning. Then it posts one digest to your team.
>
> Two promises: it only watches public information, and every change it reports carries a source link and a date. If it cannot source a change, it does not report it - no speculation.
>
> It works for SaaS vendors, marketing teams and agencies, CPG/DTC brands, product managers, and investors tracking a market.
>
> I need to ask you a few setup questions. This takes about 15-20 minutes and you won't have to redo it."

---

## Step 2: Onboarding interview

Ask the following questions. You can ask them together in a single message grouped by topic. Do NOT ask more than two groups at once.

**Group A - Your competitors and what to track**

1. "Who are your competitors? For each one, give me:
   - **Name**
   - **URLs / pages to watch** - e.g. pricing page, product or features page, changelog, blog, careers page. List the specific pages, not just the homepage, so I diff the right things.

   List as many as you want to track."

2. "Which dimensions should I track? The defaults are: **pricing**, **product/launches**, **messaging/positioning**, **funding**, **hiring signals**, and **notable content**. Tell me if you want to drop any or add others."

**Group B - Your positioning, cadence, sources, and storage**

3. "Describe your own positioning in a few sentences - your category, your ICP, what you lead with, and where you think you win or lose against this set. This is what lets me turn each competitor move into a real 'what it means for us' line instead of a generic note."

4. "When should the weekly digest run, and where should it post?
   - **Day / cadence** - which day of the week (default: Monday), weekly by default
   - **Slack channel or DM** for the digest"

5. "Any sources to always include or always exclude? For example, always include a specific analyst blog or a competitor's changelog, or exclude unreliable rumor sites or social posts. If you have no preference, I'll use mainstream, sourceable public sources only."

6. "Where should I keep the baseline snapshots? I save one snapshot per competitor each week so I can diff against it next time. Options: Google Drive, Notion, Airtable, Google Sheets, Dropbox, or something else - and which folder/base/page."

---

## Step 3: Clarify and confirm

After the user answers, summarize what you heard and confirm before writing config:

> "Here's what I'm setting up:
> - Competitors: [N competitors, names] with [count] watched pages
> - Dimensions tracked: [tracked_dimensions]
> - Our positioning: [1-line summary]
> - Digest: [digest_day], weekly, posted to [digest_channel]
> - Sources: include [sources_include], exclude [sources_exclude]
> - Snapshot storage: [snapshot_storage_system] at [snapshot_storage_location]
>
> Does that look right, or anything to adjust?"

Wait for confirmation before writing.

---

## Step 4: Write config to CLAUDE.md

Once confirmed, append the following block under `## Your context` in CLAUDE.md. Fill in every field from the user's answers. Use the exact YAML format below - do not skip fields.

```yaml
## Your context

competitor_list: |
  [One block per competitor, e.g.:
  - Name: Acme Corp
    Pages to watch:
      - https://acme.example/pricing
      - https://acme.example/product
      - https://acme.example/blog
      - https://acme.example/careers
  - Name: Globex
    Pages to watch:
      - https://globex.example/pricing
      - https://globex.example/changelog ]

tracked_dimensions: |
  [The dimensions the user chose, e.g.:
  - pricing
  - product/launches
  - messaging/positioning
  - funding
  - hiring signals
  - notable content]

our_positioning: |
  [The user's positioning in their own words - category, ICP, what they lead
  with, where they win/lose vs this set. Used to write the implication lines.]

digest_day: "[Monday | Tuesday | ... ]"
digest_cadence: "weekly"
digest_channel: "[Slack channel or DM]"

sources_include: |
  [Sources to always include, or "None specified - use mainstream sourceable public sources."]
sources_exclude: |
  [Sources to always exclude, or "None specified."]

snapshot_storage_system: "[Google Drive | Notion | Airtable | Google Sheets | Dropbox | other]"
snapshot_storage_location: "[folder / base / page name and path]"

sourcing_rules: |
  Every reported change must carry a source link and an observation date.
  Public information only - no logins, no paywalled or private data.
  Never report a change that cannot be sourced; drop it or note it as a
  watchlist gap. Capture old -> new values from the stored snapshot and the
  live page so each diff is concrete.
```

---

## Step 5: Connect accounts

After writing the config, guide the user to connect each required account through Gamut's account connection flow:

> "Now let's connect what I need:
> 1. **[snapshot_storage_system]** - to save and read the weekly baseline snapshot per competitor
> 2. **Browser** - to visit the watched pages (built into Gamut, no key needed)
> 3. **Web search** - to find funding, hiring, and content signals (built in)
> 4. **Slack** - to post your weekly digest
>
> Connect [snapshot_storage_system] and Slack via the Accounts panel in Gamut. Let me know when they're connected and I'll run a quick read-only check."

Once accounts are connected, run a dry-run check:
- Confirm you can write to and read from {{snapshot_storage_system}} at the configured location.
- Visit the first watched page of the first competitor and confirm you can read it.
- Run one web search to confirm search access.
- Confirm the Slack digest channel is reachable.

Report back what you found:

> "Connected and verified:
> - Snapshot storage: [snapshot_storage_system] reachable at [location]
> - Browser: loaded [first competitor]'s [page] successfully
> - Web search: working
> - Slack: [digest_channel] is reachable
>
> Everything looks good. You're set up."

If any watched page failed to load, report it now so the user can fix the URL before the first run.

---

## Step 6: First task and verification run

Close with a suggested first action:

> "Your agent runs every [digest_day], weekly. The very first run is a baseline capture - there's nothing to diff against yet, so the first real diff lands next week.
>
> To kick it off and see exactly what I capture before anything is posted, try this prompt:
>
> *'Capture a baseline snapshot of every competitor now and show me what you captured per page and source, but do NOT post anything to the team yet.'*
>
> Once the baseline looks right, the next weekly run will produce your first sourced diff."

You can re-run onboarding at any time by asking the agent to run the `agent-onboarding` skill.
