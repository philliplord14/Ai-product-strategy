
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



## Governance Policy

**Scope:** All K.i Pro AI features that generate customer-facing outputs — 
including nudges, recommendations, risk signals, strategy builder outputs 
and chatbot responses. Covers both automated and human-reviewed outputs 
across all confidence tiers.

**Autonomy boundaries:**
- High confidence (>90%): output surfaces to user; human approves before 
  any action executes (calendar booking, playlist creation)
- Medium confidence (70–90%): output surfaces with hedged language; 
  user must confirm before proceeding
- Low confidence (<70%): output withheld; routed to human review queue — 
  no customer-facing output generated autonomously
- Sensitive signals (burnout, performance risk): always human-in-loop 
  regardless of confidence score — framed as a prompt, never a conclusion
- Green light / red light governance model: low-risk, low-data features 
  follow a fast-track green light process; features involving sensitive 
  data, new inference types or high autonomy require full governance board 
  review — not every feature goes through the full process

**Escalation triggers:**
- User feedback: if ≥ 20% of outputs for a given feature receive a 
  thumbs-down or "This isn't right" signal within a 7-day rolling window, 
  that feature is flagged for immediate review and new outputs are paused 
  pending assessment
- Token spike: if daily token consumption exceeds 3x the rolling 7-day 
  average, an alert fires to engineering — indicates either a runaway 
  process, a prompt injection attempt, or unexpected usage surge
- Latency / timeout: if p95 response time exceeds 5 seconds or a feature 
  failure rate (timeout / no response) exceeds 2% of requests in a 24-hour 
  period, an alert fires and the feature is flagged for review
- Hallucination detection: any confirmed hallucination on a null or 
  insufficient data profile triggers an immediate feature pause — 
  not managed silently, escalated to engineering same day
- Reliability contract breach: if accuracy drops >5% vs. prior month 
  baseline on the golden dataset re-run, new releases are paused until 
  root cause is identified

**Audit cadence:**
- Golden dataset re-run: every model change and every new feature release
- Manual eval scoring: ongoing — outputs reviewed against "what good looks 
  like" rubric; two AI models score independently on the same scale without 
  seeing manual scores to prevent bias; scores reconciled and deltas reviewed
- Drift check: currently monthly manual — target is automated continuous 
  monitoring with threshold alerts by Q2 FY27
- Governance board review: quarterly for all active features; full review 
  required for any feature touching new data types, new inference patterns 
  or increased autonomy
- Feedback loop review: weekly dashboard review of thumbs-down rate, 
  dismissal type breakdown and intent signal patterns from chatbot and 
  strategy builder

**Regulatory exposure:**
- EU AI Act: K.i Pro features that inform employment decisions 
  (performance risk signals, skill gap assessments, compliance flags) 
  are classified as high-risk under the Act — human-in-loop requirements, 
  transparency obligations and audit trail requirements apply
- GDPR: all outputs derived from personal data require a lawful basis; 
  the 25-year proprietary dataset is non-PII but live organisational data 
  processing requires documented data agreements with each customer
- AI governance board to formally sign off on EU AI Act compliance 
  classification for each K.i Pro feature before commercial release — 
  this is a hard gate, not advisory
- Target: full regulatory review completed before Phase 1 commercial 
  launch 

## Agent Topology

<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

**Output generation agent (current):**
- Can: generate nudges, recommendations, risk signals, strategy builder 
  outputs and chatbot responses based on live organisational data
- Can't: execute any action autonomously — cannot book calendar slots, 
  create playlists or send communications without explicit user approval
- Who approves: user (learner / manager / L&D admin) approves before 
  any action executes; low confidence outputs routed to human review queue

**Eval agent — parallel, x2 (current):**
- Can: score any output against the defined quality rubric independently
- Can't: see each other's scores or the manual eval scores — bias prevention
- Who approves: engineering and product review reconciled scores; 
  deltas trigger a human decision on whether output meets the release bar

**Target (FY27): Orchestrator + specialist agents**
- Orchestrator routes inputs to the correct specialist agent 
  (nudge / chatbot / strategy builder / compliance / admin insights)
- Each specialist agent scoped to its domain only — cannot act 
  outside its defined feature boundary
- Human-in-loop approval sits between orchestrator and any 
  customer-facing output regardless of which agent generated it

## Shadow AI Audit

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|------------|----------|
| ChatGPT / Claude — L&D teams pasting in employee skill data and performance reviews to generate development plans | L&D Admins | H | kill — sensitive performance data leaving the platform or being added into a public LLM is typically not aloud under their data policy and use of data; K.i Pro's L&D Strategy feature absorbs this natively with the data advantage and works within the allowed boundries of data use |
| ChatGPT — managers pasting in 1-2-1 notes to get suggested follow-up actions and talking points | Managers | H | kill — K.i Pro's 1-2-1 intelligence feature directly replaces this and also as above it is not permitted in most companies to add PII in to public modals; unacceptable risk of personal performance data in a public model |
| Excel / manual spreadsheets — L&D teams building their own skill gap trackers because platform reporting isn't surfacing the right view | L&D Admins | M | kill — is is not a sustainable or scalable way for organisation to manage skills gap or performance data in a connected way |
| Zapier / Make — customers automating compliance reminder emails outside the platform because nudging isn't proactive enough | L&D Admins | M | govern — formalise as a supported integration until native calendar and nudge automation ships; document data flow and auth |
| Microsoft Copilot / Viva Insights — managers using Copilot to query content and data sources through an MCP | Managers & Learners | H | govern — structural threat confirmed in encroachment assessment; define MCP strategy and accelerate native burnout signal feature |

**Total tools found:** 5  
**Tools after triage:** 3 (kill: 2 / govern: 2 / keep: 1)  
**Estimated hidden spend:** unknown — recommend CX team surveys 
top 50 ARR customers to quantify external AI tool spend as a 
direct input to K.i Pro pricing model and urgency case for 
Phase 1 acceleration
