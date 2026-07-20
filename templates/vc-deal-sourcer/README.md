> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/vc-investing/vc-deal-sourcer)** — one-click deploy, no setup.

# VC Deal Sourcer

An automated top-of-funnel deal sourcing agent for venture capital funds. Every weekday morning it searches Product Hunt, X/Twitter, Crunchbase, TechCrunch, LinkedIn, and AngelList/Wellfound for new companies and founders matching your investment thesis — deduplicates against everything it has seen before — and drops fresh names into a shared inbox file for the Thesis Screener to evaluate.

No more manual trawling. The funnel feeds itself.

---

## How it pairs with the Thesis Screener

The VC Deal Sourcer and the Thesis Screener are designed to work as a two-agent pipeline:

```
[ VC Deal Sourcer ]  ──writes──▶  inbox.txt  ──reads──▶  [ Thesis Screener ]
     (top of funnel)                                        (evaluation layer)
```

The Deal Sourcer runs each morning and appends new company entries to `inbox.txt`. The Thesis Screener reads that file, evaluates each company against your thesis criteria, and produces a scored shortlist.

Both agents share:
- The same `inbox.txt` path (default `/workspace/inbox.txt`)
- The same `config.json` for fund settings (sectors, stage, geography)

If you install both agents in the same workspace, onboarding for the Deal Sourcer will detect the Thesis Screener's `config.json` and pre-fill shared settings automatically.

---

## Getting started

1. **Import this workspace** into Claude Code (File > Import Workspace or drag the zip into the project panel).
2. **Run onboarding**: Claude will automatically start the `agent-onboarding` skill on first launch. Answer the questions about your fund's sectors, stage, geography, and preferences. Takes 5–10 minutes.
3. **Confirm the smoke test**: After onboarding, the agent will run one live sourcing pass and show you the top 5 results. Confirm they look right.
4. **Set the schedule**: Onboarding will give you the hook configuration to add to `.claude/settings.json` so the agent runs automatically each morning.

That's it. The agent handles the rest.

---

## Inbox file format

Each daily run appends a dated section to `inbox.txt`:

```
=== Sourcer Run: 2026-06-16 | 12 companies added ===
Acme AI — Automates SOC 2 audit evidence collection for mid-market SaaS. https://acme.ai
Foundry Labs — Infrastructure for fine-tuning open-source LLMs at the edge. https://foundrylabs.io
Meridian Health — Patient scheduling copilot for independent medical practices. https://meridianhealth.co
...
```

The Thesis Screener reads entries from this file in order. Once it has processed an entry, it marks it — new entries from the Deal Sourcer are always appended at the bottom, so there is no collision.

---

## Deduplication

The agent maintains `/workspace/seen-companies.json` — a running list of every company it has ever encountered, including ones that were filtered out before reaching the inbox. This ensures the same company is never presented twice, even across weeks of runs.

The file is created automatically on first run. Do not delete it — it is the agent's memory of what it has already sourced. If you want to re-surface a company that was previously filtered, you can remove it from `seen-companies.json` manually.

---

## Tuning volume and sources

### Daily volume

Controlled by `daily_volume_target` in `config.json`. The default is `"10-15"`. A higher target means:
- More candidates reach the Thesis Screener each day
- The inbox grows faster
- The Screener needs more capacity to keep up

For most funds with a 1–2 person investment team, 10–15/day is a manageable throughput. Scale up only if the Thesis Screener is automated enough to handle the load.

### Sources

Each source can be toggled in `config.json` under the `sources` key:

```json
"sources": {
  "product_hunt": true,
  "twitter_x": true,
  "crunchbase": true,
  "techcrunch": true,
  "linkedin": false,
  "angellist": true
}
```

Common reasons to disable a source:
- **LinkedIn**: highest noise-to-signal ratio for automated search; disable if the inbox fills with irrelevant founder posts
- **Crunchbase**: lags real announcements by 2–4 weeks; disable if you only want leading-edge signals
- **TechCrunch**: skews toward Series A+; disable if you are pre-seed only

### Sector and stage adjustments

Edit the `sectors` and `stage` fields in `config.json` at any time. The agent picks up changes on the next run — no need to re-run onboarding for minor adjustments.

### Founder signals

If you want to flag or prioritize certain founder backgrounds (e.g. "repeat founder", "ex-Stripe", "PhD in ML"), add them to `founder_signals` in `config.json`. The agent will note matches in the inbox entry so the Thesis Screener can weight them.

---

## Running manually

To trigger an on-demand sourcing pass outside the scheduled run:

```
claude "Run the VC Deal Sourcer for today."
```

The agent will follow the same steps as a scheduled run: build queries, search, deduplicate, filter, and append to the inbox.

---

## Files in this workspace

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Agent system prompt and operating instructions |
| `.claude/skills/agent-onboarding/SKILL.md` | First-run setup interview |
| `config.json` | Generated by onboarding; stores all fund settings |
| `/workspace/inbox.txt` | Shared inbox — Deal Sourcer writes, Thesis Screener reads |
| `/workspace/seen-companies.json` | Deduplication memory; auto-created on first run |

---

## Limitations

- The agent uses web search, not direct API access to Crunchbase or AngelList. Results depend on what search engines surface, which may lag direct platform browsing by a few days.
- Very early stealth companies (no web presence at all) will not be found — by design. A company with zero public footprint cannot be sourced via web search.
- YC batch announcements are high-density sourcing moments but only happen twice a year. For those windows, consider running the agent more frequently (e.g. daily instead of weekdays only) and temporarily broadening the volume target.
