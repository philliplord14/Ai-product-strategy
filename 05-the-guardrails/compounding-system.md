# Compounding System Design

## Feedback Loops

## Compounding System Design

### Feedback Loops

## Compounding System Design

### Feedback Loops

## Compounding System Design

### Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|------------|--------|
| **Recursive Learning** — K.i Pro config trains the model | Sector, business goals and target skills set during K.i Pro onboarding config | Sector-specific recommendation improvements over time — more customers in the same sector = better outputs for all of them | Y | broken (data captured but not fed back into model training — manual checks only) |
| **Recursive Learning** — intent signals from chatbot and strategy builder | Repeated queries, reformulated questions and abandoned sessions where the user didn't get the result they needed | Model learns what outputs are falling short for which query types and improves response quality for the same intent in future | Y | broken (intent signals not yet systematically captured or used for retraining) |
| **Recursive Learning** — individual skill, objective and recommendation signals | Accepted / rejected / edited recommendations per user over time, linked to their skill levels, target skills and objectives. Cross learning from learning and perfromance products data | Increasingly personalised nudges and development suggestions per individual and role — model improves the more a user interacts with it | Y | broken (dismissal types captured but not weighted and fed back into training pipeline) |
| **Cross-Domain Transfer** — a win in one area lifts the next | Skill gap identified in a 1-2-1 conversation; manager acts on a performance risk signal and it resolves; compliance completion linked to a learning intervention | Better skill recommendations informed by performance outcomes; compliance nudge timing improved by what worked in a development context; learning pathways lifted by what resolved risk signals for similar profiles | Y | missing (learning, performance and compliance data only integrated at data layer level in last 6–9 months — cross-domain inference not yet operational, siloed by product area) |
| **Network Intelligence** — fleet patterns, privacy-gated | Anonymised sector and role-level signals across all customer organisations with explicit opt-in | Sector-specific benchmark recommendations that improve for all customers in a sector as each new customer adds signal; role-level nudge templates reflecting what has worked across the fleet | Y | missing (25-year dataset exists as a static asset — no aggregation pipeline to turn live multi-customer signals into improving fleet-level recommendations yet) |

**Broken loop identified by partner:** Recursive Learning (all three inputs).  
**Fix plan:** Build an automated retraining pipeline that ingests config data, 
intent signals from repeated chatbot queries, and dismissal type 
(snooze / reject / edit) as labelled samples. Replace monthly manual drift 
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
