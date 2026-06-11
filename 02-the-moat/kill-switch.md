
| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** Azure open AI | stable | M | Review back up opens already idetified |
| **Abstraction** | | H / M / L | |
| **Routing** | | H / M / L | |
| **Eval** | | H / M / L | |


## Portability Score
<!-- Ready / Partial / Locked -->
<!-- Partial  -->

## If [Azure open AI] doubles pricing tomorrow:
<!-- What's your 48-hour response? -->
No response immediatly as its too woven in to all our AI product features. Strategic talks with SLT, CTO and CPO to discuss the impact and if there is another provider to give the same outcomes as our current AI vendor - which we montior continutously anyway in case of this or the modal/ vendor becomes unrealisable in output due to modal changes. 

## If [Azure open AI] ships a competing product:
<!-- What's defensible that they can't replicate? -->
Performance and specific recommondations vs generic industry wide data. No context of specific goals the company is trying to achieve (although this could be added) however not on a user by user or team level making it hard to switch



K.I PRO  ·  INTERNAL STRATEGY  ·  AI INFRASTRUCTURE
Provider dependency & portability risk
How exposed is K.i Pro if Azure OpenAI changes pricing, ships a competing product, or becomes unreliable — and what needs to change before that becomes a crisis.	PORTABILITY SCORE
LOW
Current state — must improve
before Phase 1 ships

DIMENSION ASSESSMENT

🔌  Provider   Azure OpenAI            ◆ Medium risk
CURRENT STATE
Stable. Azure OpenAI is the confirmed AI backbone powering all K.i features today. No immediate instability — but single-provider dependency creates exposure if pricing, reliability or competitive positioning shifts.
⚡  48-HOUR ACTION
Review backup providers already identified. For each K.i feature — chatbot, skills gap analysis, nudges, SMART objectives — confirm whether Anthropic Claude or Google Gemini can produce equivalent output quality. Document gaps per feature and flag any where an alternative cannot match output fidelity.

🧱  Abstraction   Provider-agnostic layer            ▲ High risk
CURRENT STATE
Likely low. K.i features are assumed to be tightly coupled directly to Azure OpenAI endpoints with no provider-agnostic abstraction layer in place in the architecture.
⚡  48-HOUR ACTION
Audit the codebase: are model calls made directly to Azure OpenAI endpoints or routed through a wrapper? If direct, abstraction is the single highest-priority build task before further investment. A thin LLM abstraction layer (e.g. LangChain or a custom adapter) makes every other row on this table solvable — and is a 2-4 week engineering task.

🔀  Routing   Model selection logic            ▲ High risk
CURRENT STATE
Not in place. All K.i features route to a single model with no intelligent selection logic — overbuying on capability for simpler tasks and creating significant cost exposure at scale.
⚡  48-HOUR ACTION
Design a routing spec: proactive nudges, skills gap analysis and performance recommendations need GPT-4 class capability. Simple chatbot Q&A and content search can route to a smaller, cheaper model. Routing reduces cost, increases resilience, and is essential if K.i Pro is to be profitably priced at scale.

🧪  Eval   Output quality framework            ▲ High risk
CURRENT STATE
Not established. No formal eval framework exists for K.i Pro outputs — no baseline for nudge accuracy, skills recommendation relevance, hallucination rate or consistency across model versions.
⚡  48-HOUR ACTION
Define minimum eval criteria per output type before any provider switch is attempted. Without evals you cannot know if an alternative provider produces equivalent output. Evals also directly answer the bias and hallucination governance questions that customers already raise — build the framework and get ahead of it.

WHAT HAPPENS IF AZURE OPENAI CHANGES?

If Azure OpenAI doubles pricing tomorrow
No immediate response is possible — K.i is currently too woven into all AI product features to move quickly. The short-term action is a strategic conversation between SLT, CTO and CPO to assess the full impact and identify whether an alternative provider can deliver equivalent outputs. This should be monitored continuously regardless of this scenario arising.
WHAT CHANGES THIS ANSWER
Abstraction and routing built now means a pricing shock becomes a 2-week provider swap, not a 6-month rebuild. This is the most actionable risk reduction available before Phase 1 ships.

If Azure OpenAI ships a competing product
K.i Pro's defence is specificity over genericism. Azure OpenAI has no access to 25 years of cross-customer, sector-specific learning-to-performance outcome data. Generic AI tells you what good looks like industry-wide — K.i Pro tells you what good looks like for your people, your goals, at team and individual level. That context cannot be replicated by a model provider.
ADDITIONAL RISK TO NAME EXPLICITLY
Zensai's deep Microsoft 365 and Azure Copilot integration means this scenario is already partially live via the Microsoft ecosystem. Worth naming directly in the board case rather than leaving the board to surface it.

⚠️  The portability score is LOW today — but this is fixable before it matters.
K.i Pro is early enough in build that abstraction and routing can be added without major rework. The risk is completing 12+ months of feature build on unabstracted Azure OpenAI dependencies and then facing a price increase or competitive move with no fast exit route. Abstraction is a 2-4 week engineering task. Without it, every row above stays High risk.

K.i Pro — AI Provider Risk Assessment     |     June 2026     |     Internal document — not for external distribution

