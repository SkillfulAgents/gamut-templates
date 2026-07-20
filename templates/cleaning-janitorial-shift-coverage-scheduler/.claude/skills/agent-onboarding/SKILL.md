---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome — let's get your Shift Coverage Scheduling agent set up in about two minutes. I'll ask a few quick questions about your cleaning operation and your scheduling system, then I'll configure the agent so it's ready to handle real callouts.

## Onboarding Questions

Work through these sections conversationally. You can answer multiple questions at once if it's faster.

### 1. Your Business

- What is the name of your cleaning company?
- Do you run commercial accounts, residential accounts, or both?
- Roughly how many active employees are on your scheduling roster?
- How many active client sites do you cover on a typical week?

### 2. Scheduling System

- Which system holds your employee schedule and roster — **Swept**, **Janitorial Manager**, or both?
- Do your employees clock in and out through that same system? (This helps detect no-shows automatically.)
- Is there a specific way callouts typically come in today — employee app message, phone call to a manager, text? Knowing this helps route detection correctly.

### 3. Urgency and Response Windows

- How many hours before a shift starts does a callout become truly critical for you — the point where you need the fastest possible response? (Default is 6 hours.)
- What response window should the agent wait at each outreach tier before moving to the next group? For example, 30 minutes for critical shifts, 2 hours for next-day shifts. What works for your operation?

### 4. Staffing Rules and Overtime

- Do you have a weekly overtime threshold (hours) beyond which the agent should NOT offer a shift without manager approval?
- Are there any client sites that require specific certifications, background checks, or security clearances before an employee can be assigned? If so, are those clearances tracked in Swept or Janitorial Manager?

### 5. Escalation and Notifications

- Who should receive escalation alerts when a shift can't be filled? Please provide their name, role, and preferred contact method (email address or Slack handle).
- Should the agent ever notify the client directly when there is a last-minute coverage change? If yes, which accounts require client notification?

### 6. Coverage Log Storage

- Where would you like the agent to store the coverage event log? Options: a Google Sheet (provide the sheet name or URL), Swept's built-in reporting, Janitorial Manager's records, or another location.
- Who should receive the weekly Monday coverage digest — same escalation contact, or a different person?

### 7. Finish Up

- Is there anything unusual about how your scheduling works — seasonal crews, franchise sub-contractors, or union rules — that the agent should know about?

---

## After Questions Are Answered

Write the `## Your context` section in CLAUDE.md with the collected information. Use this format:

## Your context

- **Business name:** [name]
- **Business type:** [commercial / residential / both]
- **Active employees:** [number]
- **Active client sites:** [number]
- **Primary scheduling system:** [Swept / Janitorial Manager / both]
- **Clock-in tracking via scheduling system:** [yes / no]
- **Callout intake method:** [employee app / phone / text / other]
- **Critical urgency threshold:** [hours before shift start]
- **Outreach tier response windows:** [Critical: X min | Urgent: X hr | Standard: X hr]
- **Overtime threshold (weekly hours):** [number, or "none configured"]
- **Site-specific clearance tracking:** [yes — tracked in [system] / no]
- **Escalation contact:** [name, role, email or Slack handle]
- **Client notification accounts:** [list, or "none"]
- **Coverage log location:** [Google Sheet URL / Swept / Janitorial Manager / other]
- **Weekly digest recipient:** [name and email]
- **Special scheduling notes:** [any franchise, union, seasonal details, or "none"]

Then create a config.json at the workspace root with the same data in structured form.

Finally, tell the user their first suggested task prompt, e.g.: "Maria called out sick for tomorrow's 6am shift at Lakeside Corporate Center — find coverage and send outreach."
