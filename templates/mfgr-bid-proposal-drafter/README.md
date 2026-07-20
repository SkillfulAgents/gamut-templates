> ⚡ **Run this agent on [Gamut](https://www.gamut.so/agent-templates/bid-proposal-drafter/mfgr-bid-proposal-drafter)** — one-click deploy, no setup.

# Manufacturing - Bid / Proposal Drafter

Stop rebuilding quotes from scratch on every RFQ. This Gamut agent takes an inbound customer RFQ, contract manufacturing bid, or government solicitation and produces a structured first-pass proposal package - pulling production capabilities, active certifications, tooling history, and cost benchmarks from Epicor or SAP B1 - so the estimating and sales team can finalize a competitive bid in a fraction of the time.

---

## Who this is for

Manufacturing companies that regularly respond to customer RFQs or government solicitations and want a faster, more consistent quoting and proposal process.

- Job shops and contract manufacturers (machining, stamping, casting, injection molding, fabrication, assembly)
- Tier 1 and Tier 2 automotive and aerospace suppliers responding to OEM RFQs
- Defense and government contractors responding to solicitations (ITAR, CMMC requirements)
- Estimating teams managing high RFQ volume with limited administrative support

**Relevant subsegments: MFGR**

---

## What it does

1. Parses inbound RFQs and bid requests - extracts part numbers, material specifications, required processes, quantity and delivery requirements, quality requirements (FAI, PPAP level, SPC), required certifications, and submission deadline - and flags gaps immediately.
2. Confirms production capability by checking Epicor or SAP B1 for available processes, work center capacity, and tooling status - and flags any operations that require outside processing.
3. Pulls historical cost data by part number, material grade, and operation to establish a cost floor and quoted price range, including scrap rate history and tooling amortization where applicable.
4. Assembles the quality and certification package: active ISO/IATF/AS9100/NADCAP certificates with expiry dates, PPAP capability, quality KPIs - and flags any required certifications the company does not hold.
5. Produces a complete first-pass proposal: cover letter, capabilities overview, quality certifications, part-by-part quoted prices and lead times, cost breakdown (if requested), delivery terms, and references.
6. Delivers a prioritized missing-information checklist categorized as submission-blocking, proposal-critical, or quality-improving.

---

## What you need to set up

- Epicor or SAP Business One connected to this Gamut workspace (for job history, standard costs, and work center data), or ability to export relevant data as CSV
- Current quality certificates (ISO, IATF, AS9100, NADCAP, ITAR) with certificate numbers and expiry dates
- Standard cost model by cost element (material, labor by work center, overhead rate, outside process rates)
- Qualified outside processor list (plating, heat treat, anodizing, etc.) with typical lead time and cost
- Slack or email channel where proposal drafts and missing-information alerts should be sent

---

## What it does not do

- Submit proposals or bids on your behalf
- Perform engineering feasibility assessments or DFM reviews
- Generate tooling cost estimates without engineering input
- Pull live material commodity prices without a market data integration
