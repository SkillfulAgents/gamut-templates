---
name: agent-onboarding
---

# Agent Onboarding

Welcome — let's configure your Franchise Compliance Tracker. I'll ask about your network, the item types you track, and your compliance workflow. About 8 minutes.

---

## Network basics

1. What is the franchise brand name, and are you configuring this for the franchisor (tracking all locations) or a multi-unit franchisee (tracking your own locations)?
2. How many active locations does this instance need to track?
3. What states or jurisdictions do your locations operate in?

---

## Systems

4. Do you use a franchisor compliance portal, ServiceTitan, or another platform to track location documents? Or should we build from a spreadsheet register?
5. Where are COIs and location documents currently stored — in the portal, a shared Drive folder, or another location?

---

## Item types

6. Which compliance items do you want to track? (Select all that apply)
   - State/county/city business licenses
   - Health department and food facility permits
   - Fire inspection and fire suppression certificates
   - Franchisor training and brand certifications
   - Manager certifications
   - Certificates of insurance (GL, workers' comp, umbrella)
   - Equipment inspections (hood, elevator, etc.)
   - Other (describe)

---

## Lead times and escalation

7. When should renewal reminders begin — default is 90/60/30/14 days, but some health permits or COIs may need longer lead times. Any adjustments?
8. Should the franchisor compliance lead be copied on all nudges, or only on items within 30 days of expiry?
9. Who is the franchisor compliance lead who should receive lapse alerts and the digest? Provide their name and Slack handle or email.
10. Which Slack channel should receive the daily or weekly network digest?

---

## After Questions Are Answered

1. **Update CLAUDE.md** with: brand name, scope (franchisor vs. multi-unit), location count, jurisdictions, system and connection status, document storage location, item types tracked, lead times, escalation policy, compliance lead contact, and digest channel.

2. **Create config.json** at `.claude/skills/agent-onboarding/config.json`:

```json
{
  "brand_name": "",
  "scope": "franchisor | multi_unit_franchisee",
  "location_count": 0,
  "jurisdictions": [],
  "system": "franchisor_portal | servicetitan | spreadsheet | other",
  "system_connected": true,
  "document_storage": "",
  "item_types": [],
  "lead_time_days": [90, 60, 30, 14],
  "copy_compliance_lead_at_days": 30,
  "compliance_lead": "",
  "digest_channel": "",
  "digest_cadence": "daily | weekly"
}
```

3. **Give the user their first task prompt.** Suggest:

   > "Run today's compliance check and post the network digest."

   or

   > "Show me all locations with items expiring in the next 30 days."
