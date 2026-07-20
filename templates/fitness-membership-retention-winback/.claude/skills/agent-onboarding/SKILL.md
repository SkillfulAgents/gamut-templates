---
name: agent-onboarding
---

# Agent Onboarding Skill

Welcome — let's get your Membership Retention & Win-back agent configured in a few minutes. I'll ask about your studio, your membership model, and your current retention setup, then configure the agent so it's ready to start catching at-risk members right away.

## Onboarding Questions

Work through these sections conversationally. You can answer multiple questions at once if it's easier.

### 1. Your Business

- What is the name of your business?
- What type of business is it — fitness studio, yoga/Pilates studio, wellness center, salon, spa, or something else?
- How many active members or recurring clients do you have approximately?
- Do you run one location or multiple?

### 2. Booking and Billing System

- Which system holds your member records, visit history, and bookings — **Mindbody**, **Boulevard**, or both?
- Does that same system handle your billing and EFT processing?
- Are you using Mindbody's or Boulevard's built-in messaging or marketing automation tools for member communications today? (This determines how the agent sends outreach.)

### 3. Membership Model

- What membership types do you offer? (e.g., EFT monthly unlimited, class packs, annual contracts, appointment-based memberships, punch cards)
- What is the typical expected visit cadence for your most common membership tier — for example, "3x per week" or "1 appointment per month"?
- Do you offer membership pauses or freezes? If so, what are the rules (e.g., maximum duration, how far in advance a member must request)?

### 4. At-Risk Thresholds

- How many days of no visits should trigger a Yellow (at-risk) flag for a typical member? (Default: 14 days)
- How many days of no visits should trigger a Red (high-risk) flag? (Default: 21 days)
- Is there a visit frequency drop percentage that concerns you — e.g., if someone who usually comes 3x/week drops to 1x/week for two consecutive weeks?

### 5. Retention Offers and Win-back Plays

- What retention plays are currently available to offer members? (e.g., one free session, first-month discount for reactivation, membership freeze, complimentary add-on service)
- Are there any offers you want to reserve for high-LTV members only, or any you never want automated?
- What defines a "high-LTV" member for your business — tenure, total spend, membership tier, or some combination?

### 6. Escalation and Notifications

- Who should receive escalation alerts for high-LTV members at Red status and for members expressing intent to cancel? Provide their name, role, and preferred contact method (email or Slack handle).
- Who should receive the weekly Monday retention digest — same person, or a different contact?

### 7. Finish Up

- Is there anything specific about your membership terms, local market, or member demographics that the agent should keep in mind? (e.g., seasonal traffic patterns, a lot of month-to-month vs. annual members, a specific service that drives most retention)

---

## After Questions Are Answered

Write the `## Your context` section in CLAUDE.md with the collected information. Use this format:

## Your context

- **Business name:** [name]
- **Business type:** [fitness studio / wellness center / salon / spa / other]
- **Active members / clients:** [number]
- **Number of locations:** [number]
- **Primary system:** [Mindbody / Boulevard / both]
- **Billing via same system:** [yes / no]
- **Built-in messaging active:** [yes / no]
- **Membership types:** [list]
- **Expected visit cadence (primary tier):** [e.g., 3x/week, 1x/month]
- **Pause/freeze available:** [yes — rules: [rules] / no]
- **Yellow flag threshold:** [X days no visit]
- **Red flag threshold:** [X days no visit]
- **Frequency drop flag:** [e.g., 50% drop over 2 consecutive weeks, or "not configured"]
- **Available retention offers:** [list]
- **Offers reserved for high-LTV only:** [list, or "none"]
- **High-LTV definition:** [tenure / spend threshold / tier / combination]
- **Escalation contact:** [name, role, email or Slack handle]
- **Weekly digest recipient:** [name and email]
- **Special notes:** [seasonal patterns, tenure mix, retention drivers, or "none"]

Then create a config.json at the workspace root with the same data in structured form.

Finally, tell the user their first suggested task prompt, e.g.: "Pull today's at-risk member list from Mindbody and send rebooking nudges to everyone who hasn't visited in 14 or more days."
