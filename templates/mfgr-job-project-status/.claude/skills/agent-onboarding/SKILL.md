---
name: agent-onboarding
---

# Agent Onboarding

Welcome to the Job / Project Status agent for manufacturing companies. This onboarding configures the agent with your ERP system, shop schedule, and alert preferences. Ask the following questions in order, waiting for each answer before proceeding.

---

## Questions to ask

**1. Company name and production volume**
"What is your company's name? How many open production jobs or work orders do you typically have active at any given time? What are your primary manufacturing processes - CNC machining, stamping, fabrication, injection molding, assembly, or a mix?"

**2. ERP system**
"Which ERP system manages your production jobs and work orders - Epicor, SAP Business One, JobBOSS, Global Shop, Plex, or another system? Is it connected to this Gamut workspace, or will you provide work order data as a daily export?"

**3. Ship date and scheduling standards**
"How are ship dates set in the ERP - are they driven by customer PO due dates, finite scheduling, or a combination? What is your standard lead time from released work order to shipped part? How many days in advance do you want the agent to flag a job as 'at risk' of missing its ship date - 3 days, 5 days, or another window?"

**4. Outside processors**
"Do you use outside processors for operations like plating, heat treat, anodizing, or grinding? List your primary outside processors. What is the typical round-trip lead time for each? How is outside process status tracked in the ERP - a separate work order status, a subcontract PO, or another method?"

**5. Quality hold tracking**
"How are quality holds tracked in the ERP - open NCRs, a specific work order status code, or a separate quality management system? Should the daily brief include first article inspection holds separately from production NCRs?"

**6. Alert routing**
"Where should the daily ops brief be delivered - a Slack channel, the production manager's email, or a shared operations inbox? What time should it arrive each morning? Who should receive the weekly pattern summary - the plant manager, operations manager, or both?"
