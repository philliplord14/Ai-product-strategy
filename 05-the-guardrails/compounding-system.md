# Compounding System Design

## Feedback Loops

## Compounding System Design

### Feedback Loops

## Compounding System Design

### Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|------------|--------|
| **Recursive Learning** — outputs and corrections feed the model | K.i Pro config data (sector, business goals, target skills) + chatbot and strategy builder intent signals (repeated queries, reformulated questions, dismissed outputs) + individual skill levels, objectives and accepted/rejected recommendations over time | Sector-specific model improvements; better strategy builder outputs for similar organisations; more accurate nudge timing and content per individual | Y | broken (intent signals captured via dismissal and feedback triggers but not yet fed back into model training — manual monthly checks only, no automated retraining pipeline) |
| **Cross-Domain Transfer** — a win in one area lifts the next | Skill gap identified in a 1-2-1 conversation; manager acts on a performance risk signal and it resolves; compliance completion linked to a specific learning intervention | Better skill recommendations informed by performance outcomes; compliance nudge timing improved by what worked in development context; learning pathway suggestions lifted by what resolved risk signals for similar profiles | Y | missing (learning, performance and compliance data only integrated at data layer level in last 6–9 months — cross-domain inference not yet operational, siloed by product area) |
| **Network Intelligence** — fleet patterns, privacy-gated | Anonymised sector and role-level signals across all customer organisations (with explicit opt-in) — what skills correlate with performance outcomes in manufacturing, what compliance patterns predict attrition in healthcare | Sector-specific benchmark recommendations that improve for all customers in a sector as each new customer adds signal; role-level nudge templates that reflect what has actually worked across the fleet, not just within one organisation | Y | missing (25-year dataset exists as a static asset — no aggregation pipeline to turn live multi-customer signals into improving fleet-level recommendations yet) |

**Broken loop identified by partner:** Recursive Learning.  
**Fix plan:** Build an automated retraining pipeline that ingests dismissal type 
(snooze / reject / edit), intent signals from repeated chatbot queries, and 
golden dataset failures as labelled samples. Replace monthly manual drift 
checks with a continuous feedback-to-training loop. Define minimum signal 
volume before a model update is applied. Target: correction loop score 
moves from 3/5 to 4/5 by Q2 FY27.

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

## Governance Policy

**Scope:**
**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
