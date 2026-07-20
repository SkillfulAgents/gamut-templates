> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/candidate-sourcing-agent)** — one-click deploy, no setup.

# Candidate Sourcing Agent

> Profiles your current team to learn the real hiring pattern, sources passive talent, validates every person on LinkedIn, drafts two-channel outreach (draft-only), and files candidates into your ATS — with a full audit trail.

## What it does

This is the recruiting team's #1 workflow, run end to end. For an open role, the agent:

1. Reads the job description and extracts the sourcing criteria.
2. Creates the requisition in your ATS, **internal-only** (never posted publicly).
3. **Profiles current employees in that role** (via your discovery engine + LinkedIn) to learn the
   real ideal-candidate pattern — background, tenure, prior companies, path into the role — not just
   what the JD says.
4. Shows you the search profile and takes your edits.
5. Sources a small **calibration** set first, gets your thumbs-up/down on each, and uses that feedback
   to tune the full search.
6. Produces a ranked finalist list, each one **validated on LinkedIn** (the source of truth).
7. Drafts **both** a LinkedIn message and an email per finalist, files everyone into the ATS at the
   lead stage with the drafts attached as notes, marks them "Reached Out," and stages one LinkedIn
   message in the browser — **all draft-only, nothing sent.**

It uses APIs where it can (fast) and the browser where it must (LinkedIn has no API), exactly like a
human sourcer switching tools.

## Fully configurable

You set these during onboarding — the workflow stays the same, the pieces are yours:

- **ATS** — Ashby, Greenhouse, Lever, or similar.
- **Discovery engine** — Apollo, an internal sourcing tool (Juicebox/MetaView), or LinkedIn search.
  The agent can layer your internal tool *in addition to* Apollo as another candidate source.
- **Role, territory, and JD source** — your default opening, or upload one per run.
- **How many candidates** — the calibration set (default 2) and the final list (default 3).
- **Outreach channels & voice**, **source label**, and where to post a summary (e.g. Slack).

## What you'll need

- **Accounts:** your ATS, a discovery engine, and a connected email account (for drafts). Browser
  logins for LinkedIn, your ATS, and your email so on-screen showcases don't hit a login wall.
- **API keys:** your discovery engine key (e.g. `APOLLO_API_KEY`) and ATS key (e.g. `ASHBY_API_KEY`) if
  the ATS uses one — see `.env.example`. Email connects via OAuth.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill walks you through
   your ATS, discovery engine, channels, default role, and candidate counts, then connects accounts.
3. Give it its first role: *"Here's the JD for [role] — source it."* It will build its own
   `candidate-sourcing` skill on the first run (about 20 minutes) and then run the full workflow live.

## What's inside

- `CLAUDE.md` — the agent's role and method (profile → source → validate on LinkedIn → calibrate →
  draft → file to ATS), with tool-specific technical notes baked in.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — API keys for your discovery engine and ATS, if they need them.

## Notes

- **Nothing is ever sent.** Every LinkedIn message and email is a draft; the "Reached Out" stage and the
  staged composer are the recruiter's review-and-send point.
- **LinkedIn is the source of truth** — the agent only advances candidates whose profile it has opened
  and verified, even if the discovery engine looked promising.
- **Browser use is ~10% slower than a human on purpose** (to stay under bot protection), so the first
  live run feels deliberate. Once you trust it, it runs in the background while you do other work.
- **Calibration matters** — the more specific your thumbs-up/down feedback on the first set, the sharper
  the final list, and the agent remembers it for next time.
- **Internal-only by default** — the requisition is never posted to a public job board; the agent
  verifies 0 public postings.
