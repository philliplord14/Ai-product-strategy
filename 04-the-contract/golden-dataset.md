# Golden Dataset & Reliability Contract

#InputExpected OutputEdge Case?Judge Type1Manager has a team member with a compliance course overdue by 3 days, no action takenProactive alert to manager naming the individual, days overdue, and a suggested action (schedule time / send reminder)Nrule2Employee has a skill gap in an area directly mapped to their current objective, no development activity in 60 daysPersonalised nudge to employee with a specific development recommendation linked to their goal — not generic contentNLLM3Employee profile with no performance data, no skills data, and no objectives setGraceful "insufficient data" response — must not fabricate a recommendation or surface a misleading insightYrule4Manager's calendar data shows 6 direct reports each averaging 12+ meetings per week for 3 consecutive weeksRisk signal flagged to manager dashboard with a suggested check-in prompt — framed as a signal to investigate, not a diagnosisYLLM51-2-1 conversation notes reference a skill the employee wants to develop; no existing learning pathway covers itK.i Pro identifies the gap, confirms no current content match, and suggests playlist creation or flags to L&D admin as a content gapNLLM

**Adversarial rows included:** __
**Coverage gaps identified by partner:**

## Confidence UX Design

**Approach:** show uncertainty / tiered confidence / human-in-loop trigger

**High confidence (>90%):**
**Medium confidence (70-90%):**
**Low confidence (<70%):**

**User control surface:**

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
