# Golden Dataset & Reliability Contract

## Golden Dataset Spec
| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | Manager has a team member with a compliance course overdue by 3 days, no action taken | Proactive alert to manager naming the individual, days overdue, and a suggested action (schedule time / send reminder) | N | rule |
| 2 | Employee has a skill gap in an area directly mapped to their current objective, no development activity in 60 days | Personalised nudge to employee with a specific development recommendation linked to their goal - not generic content | N | LLM |
| 3 | Employee profile with no performance data, no skills data, and no objectives set | Graceful "insufficient data" response - must not fabricate a recommendation or surface a misleading insight | Y | rule |
| 4 | Manager's calendar data shows 6 direct reports each averaging 12+ meetings per week for 3 consecutive weeks | Risk signal flagged to manager dashboard with a suggested check-in prompt - framed as a signal to investigate, not a diagnosis | Y | LLM |
| 5 | 1-2-1 conversation notes reference a skill the employee wants to develop; no existing learning pathway covers it | K.i Pro identifies the gap, confirms no current content match, and suggests playlist creation or flags to L&D admin as a content gap | N | LLM |


## Confidence UX Design

**Approach:** Tiered confidence with visible evidence panel and a human-in-loop trigger - 
K.i Pro shows users how certain it is and why, and always preserves the ability to override, 
dismiss or escalate. Priority ordering is shown but confidence in that ordering is surfaced 
explicitly so users are not misled by rank position alone.

**High confidence (>90%):** Full recommendation shown with supporting evidence. Which data 
points drove the output (e.g. "Based on 3 missed deadlines and a skill gap in X"). 
Priority order displayed as ranked list. User can approve, edit, dismiss or snooze. 
No friction added. The UI trusts the output and presents it clearly.

**Medium confidence (70-90%):** Recommendation shown with hedged language.
Evidence panel visible but flagged as partial. Priority order shown with a confidence indicator per item 
(e.g. a subtle visual signal that rank 1 is more certain than rank 3). 
User prompted to confirm before any action is taken on their behalf.

**Low confidence (<70%):** Recommendation withheld or shown as a question rather than 
a statement - "We noticed X, is this something you'd like to explore?". 
Priority order not shown if insufficient signal to rank meaningfully. 
Human-in-loop trigger fires: output is routed to a review state or escalated to 
the L&D admin / manager to make the call. No automated action taken.

**User control surface:** 
- Approve / edit / dismiss on every output regardless of confidence tier
- "Why did I get this?" - expandable evidence panel showing the data signals behind the recommendation
- Snooze option to defer a nudge without dismissing it, preserving the signal for future use
- "This isn't right". explicit feedback trigger that feeds directly into the correction loop
- Priority order override where a user can manually reorder recommendations; 
  their choice is captured as a preference signal



## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | ≥ 90% of outputs match expected output in golden dataset | LLM judge + rule-based tests run on golden dataset after each model change | < 85% triggers immediate review before any release |
| Hallucination rate | 0% on empty or insufficient data profiles | Adversarial test rows (rows 3 and 4 of golden dataset) run on every build | Any hallucination on a null profile is an automatic release block |
| Latency (p95) | ≤ 3 seconds for nudge and insight outputs | 95th percentile response time measured in staging and production | > 5 seconds triggers engineering review — impacts trust in real-time use cases. However technical implentation could mitigate this metric through pre vectorised data |
| Drift velocity | No regression beyond 5% accuracy drop month-on-month | Monthly automated re-run of full golden dataset; delta tracked against baseline | > 5% drop vs. prior month triggers model review and pauses new feature releases and also heavily monitoring customer feedback on accuracy of suggestions, nudges and action taken |


## HITL Architecture

High level so you can drop into your architecture section / deck.

**Pre-send review:** For all customer-facing nudges and insights, K.i Pro outputs a 
recommendation and the user (learner, manager or L&D admin) must approve or dismiss 
before any action is executed - at least in early rollout / high-risk segments 
(burnout signals, performance risk, compliance flags).

**Escalation path:** If confidence is <70% or a sensitive/policy-violating output 
is detected, the system routes to:
- Queue, draft, and flag as "AI escalation" with original data evidence links 
  showing which signals drove the output


**Feedback capture:** Every "This isn't right" trigger or dismissed output:
- Creates a labelled sample with the original input, output and rejection signal
- Feeds back into the golden dataset backlog for future evaluation runs
- Dismissal type is preserved such as snooze / dismiss / reject treated as 
  different weighted signals

**Override controls:** Admin UI to:
- Disable K.i Pro nudges for specific user groups, teams or regions
- Lock out automated actions (e.g. calendar booking, playlist creation) 
  from executing without explicit user approval
- Pause specific feature outputs if a reliability threshold is breached 
  — without taking the whole system offline

## Red-Team Findings
*What failure mode did your partner find that you missed?*
