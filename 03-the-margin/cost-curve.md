# Cost Curve & Pricing Strategy

# Cost Curve & Pricing Strategy
> **Status:** Work in progress — fields marked `[TBC]` require input from Finance and Engineering before this document is complete.

---

## Cost Model

| Cost Category | Per-User/Month | Notes |
|---|---|---|
| Inference (primary model) | [TBC] | Azure OpenAI. Token consumption at production scale is unknown. Early spike test: ~£2.30 over 3 days for skill recommendations however this was an intense prompt, output and AI evals included. Engineering to model at expected user volumes.Based on current costs it will be small however it is TBD whether the recommondations and nudges recur daily, weekly or monthly which will impact costs. Costs and infra costs are being considered as part of this decision|
| Inference (cascading/triage) | [TBC] | Cascading to a cheaper triage model before hitting the frontier model will reduce cost significantly. Routing rule needs defining first. |
| Infrastructure | [est. £0.05–0.15] | Azure hosting on existing Kallidus infrastructure. Not greenfield — relatively low incremental cost. |
| Data/storage | [est. £0.02–0.08] | 25-year dataset is existing. Incremental cost covers live data processing and logging. Data scientist to confirm. |
| Human-in-the-loop | [TBC] | Manual model drift checks currently in place. Cost depends on automation level vs manual review pre-launch. |
| **Total AI COGS** | **[TBC]** | Cannot be confirmed until inference at production scale is modelled. Biggest financial risk currently that needs to be investigated. |

---

## Cascading Strategy

**Triage model:** Lightweight, cheaper model (e.g. GPT-4o-mini or equivalent) — assesses query complexity and data type before routing.

**Frontier model:** Azure OpenAI GPT-4o (or equivalent) — reserved for high-complexity outputs: burnout signals, L&D strategy generation, performance risk analysis.

**Routing rule:** Route to frontier only when the output requires reasoning across multiple data sources or generates a recommendation with material consequence. Informational queries and simple compliance flags route to triage.

**Expected cascade ratio:** Industry benchmark ~70–80% triage / 20–30% frontier. Lower risk modelling likely conservatively at 60/40 initially given K.i Pro's proactive intelligence output complexity.

---

## Pricing Model

**Current pricing:** K.i Pro not yet priced. Existing Kallidus tiers are seat-based. Customer advisory board is a pre revenue strategy to secure early ARR and revenue intent. Below are the current pricing options being discussed 

**Proposed AI pricing model:** `seat-based` / `usage-based` / `hybrid`
Pre revenue options 
# Advisory Board — Pricing Options

> **Status:** Decision required — see recommendation and outstanding actions below.

---

## Context

A key decision is needed on the commercial model for advisory board participation. The table below evaluates five options against pros, cons, and strategic alignment.

**Key context:** Kallidus has a 30% ARR growth target for FY27. The primary goal of the advisory board commercial model is to generate early committed revenue or a strong ARR indicator signal. Strategy alignment is rated: `Weak` / `Moderate` / `Moderate–Strong` / `Strong` / `Very Strong`.

---

## Options Analysis

| Option | Pros | Cons | Strategy Alignment |
|---|---|---|---|
| **Discounted annual fee** — a reduced rate vs final K.i Pro pricing, locked in until contract renewal | Creates committed ARR immediately. Clean to forecast and model. Discount creates urgency to sign. Simple to transition to full pricing at renewal. | Discount may anchor expectations low, making full-price renewal harder. If final pricing isn't confirmed yet, the discount has no reference point. | ✅ **Strong** — directly generates ARR, counts toward 30% growth target, gives Finance a predictable revenue line. |
| **One-off upfront payment** — single fee giving K.i Pro access for the remainder of their current contract term | Immediate cash in. Simple commercial structure. No ongoing billing complexity during the advisory period. | Does not contribute to recurring ARR. Hard to size without knowing remaining contract length per customer. Can feel arbitrary. | 🟠 **Moderate** — good cash signal but weak ARR indicator. Doesn't support the 30% ARR growth story with PE or board. |
| **No upfront cost — usage triggered** — fees only triggered once specific features are actively being used | Removes barrier to joining. Easier customer yes. Good for getting real usage data quickly. | No early revenue signal. Usage thresholds are hard to define and enforce. Risk of customers joining but never triggering payment. Undermines 'paid product' positioning. | 🔴 **Weak** — misaligned with both early revenue priority and ARR growth target. Too much commercial risk for an advisory programme. |
| **No upfront cost — free access** — free K.i Pro access for the remainder of their current contract term | Easiest customer yes. Maximises advisory board cohort size quickly. Strong goodwill and engagement signal. | Zero revenue contribution. Directly contradicts the early revenue goal. May devalue K.i Pro before commercial launch. Sets a difficult precedent at renewal. | 🔴 **Weak** — conflicts directly with the commercial objectives of the advisory programme. |
| **Renewal discount** — K.i Pro discount applied at next contract renewal, locked in for the full new term | Strong incentive for at-risk and 2027 renewal accounts. Aligns advisory board with renewal pipeline. No pricing needed now — decision deferred. | No revenue recognised in FY27. Harder to count toward 30% ARR growth until renewal lands. Risk that customers join for the discount but stay passive. | 🟡 **Moderate–Strong** — excellent retention tool for at-risk and 2027 renewal accounts, but revenue recognition lag limits FY27 ARR contribution. |

---

## Recommendation

> **Option 1 (discounted annual fee)** is the strongest single choice for FY27 ARR growth and early revenue signal.
>

---

## Outstanding Actions

| Item | Owner | Priority |
|---|---|---|
| Confirm final K.i Pro pricing so advisory discount has a reference point | Finance + CPO | 🔴 Critical — Option 1 cannot be pitched without this |
| Legal to draft advisory board participation agreement covering chosen commercial model |

> **Recommendation:** Seat-based or hybrid preferred. Pure usage-based makes FY27 ARR forecasting unreliable and conflicts with the 30% ARR growth target. Hybrid (seat-based floor + usage uplift above threshold) offers the best balance of predictability and cost protection.

---

## Stress Tests

| Scenario | Impact on Margin | Response |
|---|---|---|
| Inference costs 3x | Significant — margin on lower price tiers eliminated if COGS doubles | Cascading strategy is primary mitigation. Volume commitments with Azure can lock in rates. |
| Heaviest usage segment doubles | Variable cost spike without revenue increase under seat-based pricing | Introduce fair use threshold or hybrid pricing with usage cap above which additional charges apply. |
| Model provider raises prices 50% | Material — Azure OpenAI price changes have precedent | Multi-model architecture reduces single-vendor dependency. Monitor Anthropic, Gemini as fallback options. |



---

*Last updated: June 2026 | Owner: TBC | Related: [GTM Programme Plan](../gtm/README.md)*
