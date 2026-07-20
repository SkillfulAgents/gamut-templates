> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/recruiting-hr/interview-prep-kit)** — one-click deploy, no setup.

# Interview Prep Kit

> Builds a skimmable, cited prep kit for every upcoming interview — an interviewer dossier, scorecard-aligned questions tailored to the candidate, and an optional candidate prep note — so nobody walks in cold.

## What it does

For each upcoming interview, the agent:

1. Finds the interviews in scope (next 24h by default, a named interview, or an ATS stage change).
2. Pulls the **role context** from your ATS — the stage scorecard/competencies, the JD, and the panel.
3. Builds the **candidate picture** from the resume, LinkedIn, and the web — reconciled and cited, with
   anything unverifiable marked as such.
4. Assembles an **interviewer dossier**: a one-paragraph summary, validated highlights, fair "things to
   probe" framed as questions, and **scorecard-aligned questions tailored to this candidate** (labeled
   by interviewer when the panel splits competencies).
5. Optionally drafts a **candidate-facing prep note** (what to expect, who they'll meet, the focus) and
   a **preliminary-screen summary** against the JD must-haves for early-stage roles.
6. Delivers the kit to the panel (Slack and/or email) and **attaches it to the ATS record** — early
   enough to actually read it.

It never fabricates a fact, cites its sources, and keeps anything candidate-facing as a draft for the
recruiter to send.

## Fully configurable

You set these during onboarding; the workflow stays the same:

- **ATS** — Greenhouse, Ashby, Lever, or similar (candidate, role, stage, panel, scorecard).
- **Resume source** — ATS attachment, a Drive folder, wherever they live.
- **Outputs** — interviewer dossier (always), candidate prep note (optional), screening summary
  (optional, early-stage).
- **Scorecard / competencies source**, **lookahead window**, **delivery channel**, **candidate voice**,
  and the **trigger**.

## What you'll need

- **Accounts:** your ATS, the place resumes live (e.g. Google Drive), a delivery channel (Slack and/or
  email), plus LinkedIn login and web search for enrichment.
- **API keys:** only if your ATS uses one (e.g. `GREENHOUSE_API_KEY`) — see `.env.example`. The rest
  connect via OAuth; web search is platform-native.

## Getting started

1. Import this template into Gamut (drag the zip into the agent import dialog, or install it from the
   marketplace).
2. On import, a setup session starts automatically. The **agent-onboarding** skill walks you through
   your ATS, resume source, scorecard, which outputs you want, the lookahead window, delivery, and
   trigger, then connects accounts.
3. Test it: *"Build the prep kit for [candidate]'s [stage] interview — show me the dossier and the
   tailored questions."*

## What's inside

- `CLAUDE.md` — the agent's role and method (find interviews → pull role context → build candidate
  picture → assemble dossier → optional candidate note/screen → deliver + attach to ATS), with the
  no-fabrication and draft-only guardrails.
- `.claude/skills/agent-onboarding/` — the first-run setup interview.
- `.env.example` — an ATS API key, if your ATS needs one.

## Notes

- **No fabrication, everything cited** — the kit is only useful if interviewers can trust it; unverified
  claims are labeled, never asserted.
- **Tailored, not boilerplate** — questions map to the stage's scorecard and probe *this* candidate, not
  a generic bank.
- **Flags are framed as questions** — gaps and mismatches are surfaced neutrally for the interviewer to
  explore, not as verdicts.
- **The agent never decides or sends** — candidate notes are drafts and screen summaries are aids; a
  human advances, rejects, and messages candidates.
- **Pairs well with the Interview Scheduling agent** — the kit can ride along in the panel's calendar
  invite for the interview it just booked.
