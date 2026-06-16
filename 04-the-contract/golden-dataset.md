# Golden Dataset & Reliability Contract

## Golden Dataset Spec
| # | Input | Expected Output | Edge Case? | Judge Type |
|---|-------|----------------|-----------|-----------|
| 1 | Manager has a team member with a compliance course overdue by 3 days, no action taken | Proactive alert to manager naming the individual, days overdue, and a suggested action (schedule time / send reminder) | N | rule |
| 2 | Employee has a skill gap in an area directly mapped to their current objective, no development activity in 60 days | Personalised nudge to employee with a specific development recommendation linked to their goal — not generic content | N | LLM |
| 3 | Employee profile with no performance data, no skills data, and no objectives set | Graceful "insufficient data" response — must not fabricate a recommendation or surface a misleading insight | Y | rule |
| 4 | Manager's calendar data shows 6 direct reports each averaging 12+ meetings per week for 3 consecutive weeks | Risk signal flagged to manager dashboard with a suggested check-in prompt — framed as a signal to investigate, not a diagnosis | Y | LLM |
| 5 | 1-2-1 conversation notes reference a skill the employee wants to develop; no existing learning pathway covers it | K.i Pro identifies the gap, confirms no current content match, and suggests playlist creation or flags to L&D admin as a content gap | N | LLM |


## Confidence UX Design

**Approach:** Tiered confidence with visible evidence panel and a human-in-loop trigger — 
K.i Pro shows users how certain it is and why, and always preserves the ability to override, 
dismiss or escalate. Priority ordering is shown but confidence in that ordering is surfaced 
explicitly so users are not misled by rank position alone.

**High confidence (>90%):** Full recommendation shown with supporting evidence — which data 
points drove the output (e.g. "Based on 3 missed deadlines and a skill gap in X"). 
Priority order displayed as ranked list. User can approve, edit, dismiss or snooze. 
No friction added — the UI trusts the output and presents it clearly.

**Medium confidence (70-90%):** Recommendation shown with hedged language — 
Evidence panel visible but flagged as partial. Priority order shown with a confidence indicator per item 
(e.g. a subtle visual signal that rank 1 is more certain than rank 3). 
User prompted to confirm before any action is taken on their behalf.

**Low confidence (<70%):** Recommendation withheld or shown as a question rather than 
a statement — "We noticed X, is this something you'd like to explore?". 
Priority order not shown — insufficient signal to rank meaningfully. 
Human-in-loop trigger fires: output is routed to a review state or escalated to 
the L&D admin / manager to make the call. No automated action taken.

**User control surface:** 
- Approve / edit / dismiss on every output regardless of confidence tier
- "Why did I get this?" — expandable evidence panel showing the data signals behind the recommendation
- Snooze — defer a nudge without dismissing it, preserving the signal for future use
- "This isn't right" — explicit feedback trigger that feeds directly into the correction loop
- Priority order override — user can manually reorder recommendations; 
  their choice is captured as a preference signal

## Reliability Contract

| Metric | Target | Measurement | Alert Threshold |
|--------|--------|-------------|-----------------|
| Accuracy | | | |
| Hallucination rate | | | |
| Latency (p95) | | | |
| Drift velocity | | | |

## HITL Architecture
<!-- When does a human step in? What's the escalation path? -->

## Red-Team Findings
*What failure mode did your partner find that you missed?*
