# My AI Product Strategy
> A living strategy built across 6 sessions. Each module adds one component. 
> By Module 6, this repo IS your strategy — version-controlled, board-ready, portable.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|--------------|
| The Bet | M1 | ✅ | 01-the-bet/ |
| The Moat | M2 | ✅ | 02-the-moat/ |
| The Margin | M3 | ✅ | 03-the-margin/ |
| The Contract | M4 | ✅ | 04-the-contract/ |
| The Guardrails | M5 | ✅ | 05-the-guardrails/ |
| The Pitch | M6 | ✅ | 06-the-pitch/ |

---

## The Bet (M1)
*What we're building, for whom, why now.*

- **Product:** K.i Pro — proactive AI intelligence layer for Kallidus's 
  learning, skills and performance platform
- **AI Value Archetype:** Proactive intelligence — AI that acts before 
  being asked, surfacing the right nudge, insight and action for learners, 
  managers and L&D teams based on live and historical data
- **Vulnerability Scores:** Moat 4/5 · Data 4/5 · Platform 3/5
- **Top Risk:** Competitor speed of AI development and unknown market 
  shift toward headless / chat-first product consumption
- **Confidence:** H
- **Prototype:** K.i Pro config dashboard + L&D Strategy Builder — 
  NL prompt returning a prioritised skills, employee and action strategy
- **Kill Criteria:** If inference costs at production scale make unit 
  economics unviable, or if MCP standardisation commoditises the 
  intelligence layer before the data moat is operationalised

→ Details: `01-the-bet/`

---

## The Moat (M2)
*Why this won't get copied in 6 months.*

- **Data Flywheel Score:** 7/20
- **Weakest Loop:** Preference (1/5) and Domain Context (1/5) — 
  product is not yet learning from individual preferences or across 
  data domains; feedback loops are broken across all three recursive 
  learning inputs
- **Competitive Position:** Strong contextual moat via connected 
  learning + performance data; data advantage via 25-year proprietary 
  non-PII dataset; platform exposure risk from MCP / headless shift 
  and Thrive's fully agentic Kiki (live, included at no extra cost)
- **Encroachment Defense:** Proprietary benchmark data (sector/role) 
  is the only capability competitors cannot replicate quickly; 
  cross-domain inference across learning, skills, performance and 
  compliance is the structural differentiator; 90-day defence plan 
  defined against Thrive as primary attacker
- **Vendor Portability:** Partial — Azure OpenAI is the single 
  provider with no abstraction layer or routing logic in place; 
  portability score is Low and must improve before Phase 1 ships

→ Details: `02-the-moat/`

---

## The Margin (M3)
*Will this make money or bleed it?*

- **Gross Margin (current):** TBC — inference costs at production 
  scale are unmodelled; early spike test ~£2.30 over 3 days for 
  skill recommendations but daily/weekly/monthly recurrence cadence 
  for nudges is undefined
- **Gross Margin (AI-adjusted):** TBC — dependent on cascading 
  strategy implementation and routing rule definition
- **Pricing Model:** TBC — seat-based or hybrid preferred; 
  advisory board commercial model recommended as discounted 
  annual fee (Option 1) to generate FY27 ARR; pure usage-based 
  rejected as incompatible with 30% ARR growth target
- **Cascading Strategy:** Lightweight triage model (GPT-4o-mini 
  equivalent) for simple queries; frontier model (GPT-4o) reserved 
  for high-complexity outputs — burnout signals, strategy generation, 
  performance risk; target cascade ratio 60/40 initially
- **Break-even at:** TBC — requires customer base size, attach rate 
  and confirmed price point; payback period modelled at 1–2 years 
  if targets are met

→ Details: `03-the-margin/`

---

## The Contract (M4)
*Why users will trust a probabilistic system.*

- **Reliability Target:** ≥ 90% accuracy vs golden dataset; 
  0% hallucination on null profiles; ≤ 3s latency (p95); 
  < 5% drift month-on-month
- **Golden Dataset:** 5 rows, 2 adversarial (rows 3 and 4 — 
  hallucination test and sensitive output framing test)
- **Confidence UX:** Tiered confidence with visible evidence panel 
  and human-in-loop trigger; priority ordering shown with per-item 
  confidence signal; user control surface on every output 
  (approve / edit / dismiss / snooze / "this isn't right")
- **HITL Architecture:** Pre-send review for all customer-facing 
  outputs; escalation path for <70% confidence; feedback capture 
  creates labelled samples fed into golden dataset backlog; 
  admin override controls to disable, pause or lock out features 
  without taking the whole system offline
- **Failure Mode Coverage:** Hallucination on empty profiles 
  (rule-based, zero tolerance); sensitive output tone on burnout 
  and performance risk signals (LLM-judged); fabricated compliance 
  alerts; timeout / no-response failure rate threshold 2%

→ Details: `04-the-contract/`

---

## The Guardrails (M5)
*What breaks when this scales — and what compounds.*

- **Compounding System:** 5 feedback loops defined — 3x recursive 
  learning (config data, intent signals, individual recommendation 
  signals), cross-domain transfer, network intelligence; all 
  recursive loops currently broken; cross-domain and network 
  missing; fix plan targets correction loop score 3/5 → 4/5 by Q2 FY27
- **Governance Posture:** Green light / red light model — fast-track 
  for low-risk features; full governance board review for sensitive 
  data, new inference types or increased autonomy; escalation 
  triggers defined for feedback rate (≥20% thumbs-down), token 
  spikes (3x 7-day average), latency breach, hallucination and 
  reliability contract breach
- **Shadow AI Status:** 5 tools found, 5 triaged 
  (kill: 3 / govern: 2 / keep: 0); dominant signal is capability 
  gap — customers are already solving the problem with generic AI 
  tools; the timer is running
- **Agent Boundaries:** Current — single output generation agent 
  (cannot act autonomously) + parallel dual eval agents 
  (cannot see each other's scores); Target FY27 — 
  orchestrator + specialist agents per feature domain
- **Regulatory Exposure:** EU AI Act high-risk classification 
  confirmed for employment-context outputs; GDPR lawful basis 
  required for live organisational data; legal review is a hard 
  gate before commercial launch; EU AI Act sign-off required 
  per feature before release

→ Details: `05-the-guardrails/`

---

## The Pitch (M6)
*How you get this funded, shipped, and adopted.*

- **Horizon 1 (Now):** AI capability audit + feedback loop 
  instrumentation; technology and cost review; legal and 
  governance hard gates
- **Horizon 2 (Next):** Learner chatbot beta + advisory board 
  launch; K.i Pro company profile builder; L&D Strategy Builder 
  as first chargeable feature
- **Horizon 3 (Bet):** Proactive nudging broad commercial launch; 
  admin insights and NL reporting; headless capability and 
  MCP strategy
- **Board Narrative:** K.i Pro turns Kallidus's 25 years of 
  proprietary performance and outcomes data into a proactive 
  intelligence layer that tells L&D teams, managers and employees 
  what to do next — before problems occur — shifting L&D from a 
  cost centre to a measurable driver of business performance.
- **Key Metric:** ARR from K.i Pro; nudge acceptance rate; 
  thumbs-down rate < 20% per feature; first paying advisory 
  board customers by Q2 FY27

→ Details: `06-the-pitch/`
