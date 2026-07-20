> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/marketing-content/content-engine)** — one-click deploy, no setup.

# Content Engine

> Turns the raw material you already produce into a weekly slate of drafted content in your voice.

## What it does

Every week, Content Engine scans your connected sources — customer calls, product updates, blog posts,
internal wins — for the week's most postable moments. It drafts the formats you've configured (LinkedIn
posts, a newsletter blurb, outbound email snippets, whatever you choose), saves every draft to a review
queue, and posts a summary to a channel you pick. Each draft cites the source it came from and leads with
a hook.

It drafts only. It never publishes, posts, schedules, or sends anything — it fills a review queue you
approve from. Think of it as a content strategist that shows up every week with a stocked draft folder,
not an autopilot that posts to your feed.

## What you'll need

- **Accounts:** storage for drafts (Notion or Google Drive), and Slack for the review slate. A transcript
  source (sales/customer call recordings) is recommended, and web search is optional but lets the agent
  verify external stats.
- **API keys:** none by default (accounts connect via OAuth). See `.env.example` if a connected service
  needs a key.
- **Other:** a Slack channel you actually check at the start of the week, and source folders with real,
  specific material.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill will ask you:
   - Where drafts go (review channel, storage, location)
   - Which sources to mine and what to look for in each
   - Which formats to draft and how many of each
   - Your brand voice and content pillars (budget most of your time here — paste a real example post)
   - Your style rules, volume limits, and schedule
3. Once setup finishes, give it its first task, e.g.: *"Pull this week's strongest source moment and draft
   one LinkedIn post in our voice — show me the draft and its source, don't save it."*

You can re-run onboarding anytime by asking the agent to run the `agent-onboarding` skill.

## What's inside

- `CLAUDE.md` — the agent's role and method (mine → match to pillars → draft → verify → save → post).
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — environment variables, if a connected service requires a key.

## Notes

- **Every draft sounds like generic LinkedIn AI content?** Your `brand_voice` is too abstract. Replace it
  with a paragraph describing your actual cadence and diction, plus a real example post — the agent mimics
  the example more than the description.
- **The slate is full of vague, thin posts?** The source material was weak and the agent padded the counts.
  Confirm "quality over quota" is in place, lower your `count` values, and point `source_inputs` at folders
  with real, specific material.
- **Drafts wander off-topic or chase trends?** Tighten `content_pillars` to the 2–3 themes you want to be
  known for. The pillars are a gate, not a suggestion.
- **A draft included a stat you can't verify?** Connect web search and reinforce that every external number
  is verified or cut. For internal numbers, confirm they trace to a real source moment, not a rounded guess.
- **It used a customer's name without permission?** Keep customer-naming permission explicit in
  `style_rules`, and mark which stories in your wins folder are cleared for public use. When in doubt the
  agent should anonymize ("a 12-rep team") rather than name.
- **It re-drafted things you already posted?** Without cross-run memory the agent re-mines the same material.
  Keep a "what we posted" doc in the source folder it can check against, and have it skip moments older than
  the past week.
