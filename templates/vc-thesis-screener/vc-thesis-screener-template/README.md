# VC Thesis Screener

An agent template for early-stage VC analysts and partners who want to stop manually triaging inbound deal flow. Import this template, run a 5-minute setup, and the agent screens every company in your inbox each evening against your fund's investment thesis — automatically.

---

## What it does

Every evening (default: 6 PM weekdays), the agent:

1. Reads your inbox file — a plain text file where you drop company names and descriptions throughout the day
2. Looks up each company on Crunchbase, TechCrunch, and LinkedIn to enrich the one-liner with stage, funding, location, and notable investors
3. Screens each company against your thesis: sectors, stage range, geography, check size fit, must-haves, and dealbreakers
4. Returns a clear **FIT** or **NO-FIT** verdict with a 1–2 sentence reason for each company
5. Flags borderline cases separately so you can review them with context
6. Emails you an HTML report sorted by signal strength (FITs first, best signals at the top)
7. Archives all verdicts to a local JSON file for your records
8. Clears the inbox so nothing is double-screened tomorrow

---

## Who it's for

- **VC analysts** at early-stage funds who receive inbound deal flow from founders, scouts, syndicates, or LP referrals and need a fast first-pass filter before deeper diligence
- **Partners** who want a daily digest of what came in and how it stacks up against the fund's thesis — without spending an hour on it
- **Solo GPs and emerging managers** who don't have an analyst team and need to process inbound efficiently

Works best for funds with a defined thesis: clear sectors, a stage range, a check size band, and a short list of must-haves or dealbreakers. The tighter the thesis, the more useful the output.

---

## What it automates

Without this agent, a typical inbound screening workflow looks like:
- Manually reading founder cold emails or form submissions
- Googling each company to understand what they actually do
- Cross-referencing against the fund's thesis criteria (which may live in a deck or someone's head)
- Writing up a quick take in a CRM note or Slack message
- Deciding whether to pass or move to a first call

This agent handles steps 1–4 automatically and delivers the output in a single nightly email. You still make the call on whether to engage — the agent just eliminates the triage work.

---

## How to get started

### 1. Import the template

Import this workspace zip into Claude Code. This loads the agent and its onboarding skill.

### 2. Run onboarding

Type `/agent-onboarding` to start the setup interview. It takes about 5 minutes and covers:

- Your fund name and your name/role
- The sectors and spaces you invest in
- Stage range, geography focus, and check size range
- 1–3 must-haves (things that must be true for a pass)
- 1–3 dealbreakers (hard nos)
- Where to send the nightly report
- What time to run (default: 6 PM weekdays, your timezone)

Onboarding writes your thesis criteria to `config.json`, updates the agent's context in `CLAUDE.md`, connects your Gmail account for report delivery, and schedules the nightly cron trigger.

### 3. Add companies to your inbox

Open `/workspace/inbox.txt` and paste companies in, one per line. You can add entries throughout the day — the agent picks them all up at run time.

---

## Inbox format

One company per line. Each line is either:

**Name only:**
```
Acme AI
```

**Name + description (recommended):**
```
Acme AI — builds AI-powered contract review software for legal teams at mid-market companies
```

Use ` — ` (space-dash-dash-space) to separate the name from the description. Lines that start with `#` are treated as comments and ignored. Blank lines are ignored.

**Example inbox:**
```
# Companies to screen — week of June 16
Acme AI — AI-powered contract review for legal teams at mid-market companies
BuildFast — no-code app builder targeting non-technical founders
GridEdge — grid management software for commercial solar installers
Nota — AI meeting notes and CRM sync for enterprise sales teams
```

After the nightly run, the inbox is automatically cleared and reset to just the header comment.

---

## Output

The nightly report is an HTML email delivered to your configured address. It includes:

- Summary stats: total screened, fit count, no-fit count
- **FIT** section: passing companies sorted by signal strength, with stage, location, reason, and any standout signal
- **NO-FIT** section: failing companies with the specific reason each was cut
- **Borderline** section (if any): companies that missed one criterion by a small margin, with a note on what would need to change

Verdicts are also saved to `/workspace/verdicts.json` for historical reference.

---

## Updating your thesis

Re-run `/agent-onboarding` at any time to update your fund thesis, change the delivery email, or adjust the schedule. Onboarding overwrites the previous config — it won't duplicate entries.
