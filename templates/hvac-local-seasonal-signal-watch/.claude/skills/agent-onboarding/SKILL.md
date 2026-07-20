# Skill: agent-onboarding

## Purpose

Walk a new user through configuring the Local / Seasonal Signal Watch agent for their trade contracting business. Gather everything needed to start watching the right signals and delivering a useful weekly outreach list — service area, signal preferences, temperature thresholds, data source connections, and delivery settings — then write the configuration to `CLAUDE.md` and `config.json`.

Run this skill automatically when the workspace is first opened, before any other tasks are attempted.

---

## Onboarding Sections

Work through the following sections in order. Ask each section's questions conversationally — don't dump all questions at once. Confirm answers before moving on.

---

### Section 1: Business Basics

Understand the business and its territory.

**Questions to ask:**

1. What trade(s) does your company work in? (HVAC, plumbing, electrical, or a combination — this shapes which signals matter most.)
2. What's your primary service area? List the ZIP codes or counties you serve. (You can paste a list — we'll use this to filter permit data, weather events, and new-mover records.)
3. How do you primarily reach customers for outreach — phone (CSR calls), email, text, or a mix?
4. What's your company name, and who should receive the weekly outreach list?

---

### Section 2: Signal Preferences

Decide which signal types to watch and set relevant thresholds.

**Questions to ask:**

**Weather signals:**
1. Do you want to track heat events for AC outreach? If yes, what temperature threshold should trigger it? (Default: 90°F for 5+ consecutive days — adjust if your market runs hotter or cooler.)
2. Do you want to track freeze events for furnace/pipe outreach? What temperature threshold? (Default: 32°F — first night of the season below this.)
3. Which storm types should trigger an outreach flag? Options: flooding, ice storms, high-wind events (50+ mph gusts), hail. (Select all that apply to your trade and market.)

**Permit signals:**
4. Do you want to watch building permit filings? If yes, which permit types are relevant for you: major renovation permits, new construction, or homeowner-pulled trade permits (DIY conversions)?

**New-mover signal:**
5. Do you want to flag new homeowners in your service area as leads? These are typically people who moved in within the past 6 months. (This requires a new-mover data provider — see Section 3.)

**Maintenance window signal:**
6. Do you have a maintenance-agreement customer base you want surfaced for scheduling before their tune-up window? How many days in advance should we flag them? (Default: 60 days.)

---

### Section 3: Data Sources

Connect the data feeds that power the signals.

**Questions to ask:**

1. **Weather data:** We'll use a weather service for your service area ZIPs. Do you have a preferred weather data provider, or should we use a default public feed?

2. **Building permits:** Which county or counties do you operate in? Do you have access to a permit portal or data feed (e.g., your county's public permit search, a third-party permit data service like BuildZoom or PermitPulse)? If yes, provide the portal URL or data source name.

3. **New-mover data:** Do you have a new-mover data provider already (e.g., a list broker, a data service like Melissa Data or USPS NCOALink, or a marketing platform that provides mover lists)? If not, we can flag this as a "to connect later" item and you can manually paste new-mover lists for now.

4. **Maintenance customers:** Are you using ServiceTitan or FieldEdge to manage your maintenance agreements? If yes, confirm the integration is set up in Gamut's integrations panel, or provide API credentials. If not, we can use a manually uploaded customer list — you can paste or upload it now.

If any data source isn't ready yet, note it as a pending connection and move on — the agent will work with available signals and prompt to add more later.

---

### Section 4: Outreach List Delivery

Configure how and when the weekly list reaches your team.

**Questions to ask:**

1. What day of the week should the outreach list be delivered? (Monday morning is common — gives the CSR team the week to work through it. Some contractors prefer Friday afternoon to prep for the following week.)
2. What time? (Provide timezone.)
3. How should the list be delivered — email (provide address), Slack (provide channel), or both?
4. Would you like the agent to pre-draft a brief outreach note for each contact on the list, specific to the signal that triggered them? (Default: yes — CSRs can personalize before sending.)

---

### After Questions Are Answered

Once all sections are complete:

**1. Write `## Your context` to CLAUDE.md**

Append a filled-in `## Your context` section to the bottom of `CLAUDE.md`. Include:
- Company name
- Primary trade(s)
- Service area (ZIPs or counties)
- Active signal types and thresholds
- Data source connection status for each signal type
- Outreach list delivery day, time, and recipient
- Pre-drafted templates preference

Example format:

```
## Your context

**Company:** Blue Ridge Comfort Systems
**Trade:** HVAC and plumbing
**Service area:** Buncombe County, Henderson County, NC — ZIPs 28801, 28803, 28805, 28792

**Active signals:**
- HEAT_EVENT: 90°F threshold, 5 consecutive days
- FREEZE_EVENT: 32°F threshold, first night of season
- STORM_EVENT: ice, high-wind, flood
- RENO_PERMIT: major renovation and new construction
- DIY_PERMIT: homeowner-pulled HVAC/plumbing permits
- NEW_MOVER: 6-month window, source = manually uploaded list
- MAINTENANCE_WINDOW: 60-day advance flag, source = ServiceTitan

**Data sources:**
- Weather: public NWS feed (configured)
- Permits: Buncombe County permit portal (URL on file)
- New movers: manual upload (pending data provider)
- Maintenance customers: ServiceTitan (connected)

**Outreach list delivery:** Monday 8:00 AM ET → Slack #dispatch + email ops@blueridgecomfort.com
**Pre-drafted templates:** Yes, one per signal type
```

**2. Create `config.json`**

Write a `config.json` file at the workspace root with the structured configuration:

```json
{
  "company": "<company name>",
  "trade": ["<trade1>", "<trade2>"],
  "service_area": {
    "zips": ["<zip1>", "<zip2>"],
    "counties": ["<county1>"]
  },
  "signals": {
    "heat_event": {
      "enabled": true,
      "threshold_f": 90,
      "consecutive_days": 5
    },
    "freeze_event": {
      "enabled": true,
      "threshold_f": 32
    },
    "storm_event": {
      "enabled": true,
      "types": ["flood", "ice", "high_wind", "hail"]
    },
    "permit_watch": {
      "enabled": true,
      "types": ["renovation", "new_construction", "diy_trade_permit"]
    },
    "new_mover": {
      "enabled": true,
      "lookback_months": 6,
      "source": "<provider name or manual>"
    },
    "maintenance_window": {
      "enabled": true,
      "advance_days": 60,
      "source": "<servicetitan|fieldedge|manual>"
    }
  },
  "data_sources": {
    "weather": "<provider>",
    "permits": "<portal URL or provider>",
    "new_mover": "<provider or manual>",
    "field_software": "<servicetitan|fieldedge|none>"
  },
  "outreach_list": {
    "delivery_day": "<Monday>",
    "delivery_time": "<08:00>",
    "timezone": "<America/New_York>",
    "channel": "<email|slack|both>",
    "recipients": ["<email or channel>"],
    "include_drafted_templates": true
  }
}
```

**3. Give the first example task**

End onboarding with a concrete next step:

"You're all set. Here are a few things you can ask me:
- 'What signals are active this week in my service area?'
- 'Build me an outreach list — there was a big storm last night'
- 'It's the first freeze of the season — who should we call for furnace checks?'
- 'Show me new-mover leads added this month'
- 'Which signal type has booked the most jobs this quarter?'
- 'Update the heat event template to mention our summer maintenance special'"
