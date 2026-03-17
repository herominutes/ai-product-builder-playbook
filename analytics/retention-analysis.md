# 📈 Retention Analysis — AI Product Builder Playbook

> **A framework for measuring, diagnosing, and systematically improving user retention across the full product lifecycle**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Retention Analysis Model](#the-retention-analysis-model)
- [Layer 1: Retention Measurement](#layer-1-retention-measurement)
- [Layer 2: Retention Diagnosis](#layer-2-retention-diagnosis)
- [Layer 3: Churn Analysis](#layer-3-churn-analysis)
- [Layer 4: Retention Intervention Design](#layer-4-retention-intervention-design)
- [Layer 5: Retention Monitoring](#layer-5-retention-monitoring)
- [Retention for AI Products](#retention-for-ai-products)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Retention is the foundation of every product metric that matters. Without retention, acquisition is a leaky bucket. Without retention, revenue is temporary. Without retention, NPS is meaningless. A product that retains users compounds — each cohort adds to a growing base. A product that doesn't retain users requires increasingly expensive acquisition to stand still.

> **Core Principle:** Retention is not a metric to improve — it is a symptom to diagnose. Declining retention means something in the user's experience is not delivering on the product's promise. The analysis exists to find what that something is, not just to report that the number went down.

For AI products, retention analysis requires an additional lens: AI-specific failure modes. A user who stops returning after an AI hallucination, a user who abandons the product because the AI was too slow, and a user who never adopted the AI feature and churned for unrelated reasons are three completely different retention problems requiring three completely different interventions.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| D7 or D30 retention is below target | 🔴 Critical — diagnose immediately |
| User base is not growing despite strong acquisition | 🔴 Critical — leaky bucket problem |
| Churn rate is increasing quarter-over-quarter | 🔴 Critical |
| Launching a new feature intended to improve retention | 🟠 High — establish baseline before launch |
| New cohorts are retaining worse than older cohorts | 🟠 High — recent changes may be hurting quality |
| Quarterly planning — understanding retention drivers | 🟡 Medium |
| AI feature launched — assessing retention impact | 🟡 Medium |

---

## The Retention Analysis Model

Retention analysis operates across five layers, from measurement to intervention to monitoring.

```
RETENTION MEASUREMENT
  ↓ accurately measure what retention is and how it is trending
RETENTION DIAGNOSIS
  ↓ understand what is driving retention behaviour
CHURN ANALYSIS
  ↓ understand why users leave and what triggered the decision
RETENTION INTERVENTION DESIGN
  ↓ design and test changes that improve retention
RETENTION MONITORING
  ↓ track retention continuously and catch declines early
```

| Layer | Core Question | Key Output | Cadence |
|---|---|---|---|
| **Measurement** | What is our retention rate and how is it trending? | Cohort retention table | Weekly |
| **Diagnosis** | What drives high vs low retention? | Retention driver analysis | Monthly |
| **Churn analysis** | Why do users leave? | Churn root cause report | Monthly |
| **Intervention** | What changes improve retention? | A/B tested interventions | Per experiment |
| **Monitoring** | Are we catching declines early? | Retention dashboard + alerts | Continuous |

---

## Layer 1: Retention Measurement

### 1.1 Retention Definitions

Getting the definition right is the most important step. Different definitions measure different things:

| Definition | What It Measures | Best For |
|---|---|---|
| **N-day retention** | % of users active on exactly Day N | Mobile apps with daily use expectations |
| **N-day bracket retention** | % of users active any day in Days N–M | Products with variable use frequency |
| **Rolling retention** | % of users active on Day N or any later day | Best for most products — reduces noise |
| **Unbounded retention** | % of users still active after N months | Long-term health metric |
| **Action-based retention** | % of users who complete the core action again | Best North Star proxy |

```
RETENTION DEFINITION FOR [PRODUCT]

Core event: [the specific action that defines "active" for our product]
  Example: "completed one AI task" / "viewed dashboard" / "sent a message"

Retention type: [N-day / bracket / rolling / action-based]
  Rationale: [why this definition for this product]

Key retention windows:
  Day 1: ___  (short-term activation signal)
  Day 7: ___  (early habit signal)
  Day 14: ___  (habit formation signal)
  Day 30: ___  (product-market fit signal)
  Day 90: ___  (long-term value signal)
```

### 1.2 Cohort Retention Table

```
COHORT RETENTION TABLE

         D1     D7     D14    D30    D60    D90
Jan-24   47%    28%    22%    14%    9%     7%
Feb-24   43%    25%    19%    12%    8%     6%
Mar-24   51%    31%    24%    16%    11%    9%
Apr-24   49%    30%    23%    15%    —      —
May-24   52%    33%    —      —      —      —

Reading:
Horizontal trend (single cohort): Is this cohort retaining well over time?
Vertical trend (same time window): Are newer cohorts performing better or worse?
Diagonal (same calendar date): How is the overall user base performing today?

Key signals to identify:
✅ Improving vertical trend: each new cohort retains better (product improving)
⚠️ Stable horizontal: retention stabilises above 0% (healthy long-term curve)
❌ Declining vertical trend: new cohorts retain worse (regression — investigate)
❌ Horizontal curve reaches 0%: no long-term retained users (product-market fit issue)
```

### 1.3 Retention Curve Analysis

```
RETENTION CURVE SHAPE ANALYSIS

Shape 1 — Smiling curve: steep drop then flattens above 0%
Signal: Product-market fit exists for a subset of users; acquisition may be attracting wrong users
Action: Identify the retained segment; reposition acquisition to attract similar users

Shape 2 — Gradually declining (never flattens): curve approaches 0%
Signal: No long-term retained core; product does not form habits
Action: Identify what would need to be true for a user to return weekly; redesign around that behaviour

Shape 3 — Flat (high retention throughout): rare but ideal
Signal: Strong product-market fit; core action is deeply habitual
Action: Expand the user base aggressively while retention holds

Shape 4 — Saw-tooth (irregular dips and recoveries): noisy
Signal: Product use is event-driven (tax software, travel booking)
Action: Redefine retention window to match natural use cadence

My retention curve shape: _______________________________________________
Implied action: _______________________________________________
```

---

## Layer 2: Retention Diagnosis

### 2.1 Retention Driver Analysis

Identify which user behaviours in the first session or first week predict D30 retention:

```
RETENTION DRIVER ANALYSIS

Step 1 — Define the analysis
  Outcome: D30 retained (1) vs churned (0)
  Features: all user actions in Days 1–7

Step 2 — Run the correlation analysis
  For each user action, compare D30 retention rate:
    Users who did [action] in Week 1: ___%
    Users who did NOT do [action] in Week 1: ___%
    Retention lift: ___%

Step 3 — Identify the "magic actions"
  Sort by retention lift.
  Top 3 actions with highest lift are likely retention predictors.

Step 4 — Validate with causality test
  Do users who do [magic action] retain better because the action delivers value?
  Or do they retain better because they are already high-intent users who would have retained anyway?
  Test: A/B test — prompt the magic action for half of new users; compare D30 retention.

Magic actions identified:
1. [Action] — retention lift: ___%
2. [Action] — retention lift: ___%
3. [Action] — retention lift: ___%
```

### 2.2 Retention Segment Analysis

```
RETENTION SEGMENT BREAKDOWN

Segment by acquisition channel:
  Organic search: D30 = ___%  |  Paid: D30 = ___%  |  Referral: D30 = ___%
  Insight: _______________________________________________

Segment by activation behaviour:
  Completed activation event: D30 = ___%  |  Did not: D30 = ___%
  Insight: _______________________________________________

Segment by AI feature use (for AI products):
  Used AI feature in Week 1: D30 = ___%  |  Did not: D30 = ___%
  Insight: _______________________________________________

Segment by user persona:
  Persona A: D30 = ___%  |  Persona B: D30 = ___%
  Insight: _______________________________________________

Segment by device/platform:
  Desktop: D30 = ___%  |  Mobile: D30 = ___%
  Insight: _______________________________________________

Key finding: _______________________________________________
Priority action: _______________________________________________
```

### 2.3 The Engagement-Retention Matrix

Map users by engagement level and retention outcome to identify the most actionable segments:

```
ENGAGEMENT-RETENTION MATRIX

                    RETAINED (D30+)      CHURNED (< D30)
HIGH ENGAGEMENT    [Champions]          [Disappointed power users]
  (5+ sessions/wk) → Learn from them    → They wanted more — interview urgently

LOW ENGAGEMENT     [Passive retainers]  [Never engaged]
  (< 2 sessions/wk) → At risk — nurture → Acquisition quality or activation failure

Analysis:
Size of each quadrant: _______________________________________________
Biggest opportunity: _______________________________________________
Biggest risk: _______________________________________________
```

---

## Layer 3: Churn Analysis

### 3.1 Churn Classification

Not all churn is the same. Classify before intervening:

| Churn Type | Description | Detection | Intervention |
|---|---|---|---|
| **Immediate churn** | User never returns after first session | D1 retention = 0% | Activation problem |
| **Early churn** | User churns in Days 2–14 | D1 retained but D14 not | Onboarding or early value problem |
| **Habitual churn** | User established habit but then stopped | D30 retained but D90 not | Product evolution or competition |
| **Seasonal churn** | User stops due to life or business cycle change | Periodic dips aligned to calendar | Product use case is cyclical |
| **Competitive churn** | User switched to a competitor | Follows competitor launch or pricing change | Product differentiation problem |
| **AI-specific churn** | User stopped after negative AI experience | Follows AI failure event | AI quality problem |

### 3.2 Churn Interview Protocol

```
CHURN INTERVIEW GUIDE (30–45 minutes)

Recruitment: Contact all users who churned in the last 30 days. Offer incentive.
Target: 8–12 interviews per month.

Opening:
"Thank you for your time. I want to understand your experience with [product].
There are no wrong answers — honest feedback helps us build something better."

Section 1 — Context (5 min)
"Tell me how you were using [product] before you stopped."
"What were you trying to accomplish?"

Section 2 — The moment (10 min)
"Tell me about the moment you decided to stop using it."
"Was there a specific event that triggered the decision?"
"Had you been thinking about it for a while, or was it sudden?"

Section 3 — The problem (15 min)
"What was the main reason you stopped?"
"What would have needed to be different for you to keep using it?"
"Did [product] ever let you down in a specific way?"
AI-specific: "If you used the AI features — was there a moment the AI disappointed you?"

Section 4 — The alternative (10 min)
"What are you doing instead now?"
"What does [alternative] do better?"
"Is there anything you miss about [product]?"

Section 5 — The return (5 min)
"What would bring you back?"
"Is there a version of [product] you could imagine recommending to someone?"
```

### 3.3 Churn Root Cause Analysis

```
CHURN ROOT CAUSE TAXONOMY

After 8–12 interviews, categorise churn reasons:

Category 1 — Product value gap
User never found core value / value didn't match expectation
Count: ___  |  % of churned users: ___%
Representative quote: _______________________________________________

Category 2 — Activation failure
User wanted to use the product but couldn't get started
Count: ___  |  % of churned users: ___%
Representative quote: _______________________________________________

Category 3 — AI quality failure
AI produced outputs the user couldn't trust or use
Count: ___  |  % of churned users: ___%
Representative quote: _______________________________________________

Category 4 — Competitive switch
User found a better alternative
Count: ___  |  % of churned users: ___%
Competitor switched to: _______________________________________________

Category 5 — Life / business event
User's situation changed (job change, project ended, budget cut)
Count: ___  |  % of churned users: ___%
Action: [Typically low priority — difficult to address with product changes]

Primary churn driver: _______________________________________________
Intervention priority: _______________________________________________
```

---

## Layer 4: Retention Intervention Design

### 4.1 Intervention Framework

Match interventions to churn types:

| Churn Type | Intervention Strategy | Expected Timeframe |
|---|---|---|
| Immediate churn | Redesign first session; surface value faster | D1 retention impact |
| Early churn | Strengthen onboarding; add early habit triggers | D7 retention impact |
| Habitual churn | Add new value dimensions; deepen feature engagement | D30–D90 impact |
| AI-specific churn | Improve AI quality; add AI trust signals | Immediate + D30 impact |
| Competitive churn | Differentiation; competitive positioning | 1–2 quarter impact |

### 4.2 Retention Intervention Backlog

```
RETENTION INTERVENTION BACKLOG

| Intervention | Churn type addressed | Hypothesis | Expected lift | Effort | Priority |
|-------------|---------------------|-----------|--------------|--------|----------|
| [Name] | [Type] | [Hypothesis] | +___% D7 | S/M/L | H/M/L |

Prioritisation:
High: High expected lift + Low effort + Addresses largest churn category
Medium: Medium lift OR medium effort
Low: Low expected lift OR high effort

Top 3 interventions to test this quarter:
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
```

### 4.3 Retention Experiment Sequence

```
RETENTION EXPERIMENT SEQUENCE

Experiment 1: [Activation improvement]
  Hypothesis: Users who [magic action] in Week 1 retain at 3× the rate.
  If we [onboarding change], more users will complete [magic action].
  Primary metric: D7 retention
  Duration: 3 weeks

Experiment 2: [Habit trigger]
  Hypothesis: Users who receive [trigger] at [moment] return at higher rate.
  Primary metric: D14 retention
  Duration: 4 weeks

Experiment 3: [Value deepening]
  Hypothesis: Users who discover [feature] retain at higher D30 rate.
  Primary metric: D30 retention
  Duration: 6 weeks

Run in sequence (not parallel) for clarity on which change drives improvement.
If Experiment 1 succeeds: ship and move to Experiment 2.
If Experiment 1 fails: diagnose before moving to Experiment 2.
```

---

## Layer 5: Retention Monitoring

### 5.1 Retention Alert System

```
RETENTION ALERT THRESHOLDS

D1 retention:
  Green: > target × 0.9
  Yellow: target × 0.75 – target × 0.9
  Red: < target × 0.75
  Action if Red: Immediate investigation — likely activation regression

D7 retention:
  Green: > target × 0.9
  Yellow: target × 0.75 – target × 0.9
  Red: < target × 0.75
  Action if Red: Segment analysis + churn interviews triggered

D30 retention:
  Green: > target × 0.9
  Yellow: target × 0.85 – target × 0.9
  Red: < target × 0.85
  Action if Red: Escalate to leadership + retention sprint

Cohort regression alert:
Alert: Any new cohort shows D7 retention > 20% below the prior 3-month average
Action: Immediate investigation — recent product change may have caused regression
```

### 5.2 Predictive Churn Model

Build early warning before users fully churn:

```
CHURN PREDICTION SIGNALS

Early warning indicators (signal 1–2 weeks before churn):
- Session frequency drops by > 50% from baseline
- User has not completed their core action in > [N] days
- User's last AI interaction ended with a negative feedback signal
- User has not logged in for > 7 days (for daily value products)
- User has not completed the activation event after 3 sessions (early churn risk)

Churn risk score:
Assign each active user a weekly churn risk score based on the above signals.
High risk (score > 0.7): trigger re-engagement campaign
Medium risk (score 0.4–0.7): trigger feature discovery nudge
Low risk (score < 0.4): no intervention needed

Measurement:
Track: prediction accuracy (what % of high-risk users actually churned?)
Track: intervention effectiveness (what % of high-risk users were retained by intervention?)
```

---

## Retention for AI Products

### The AI Retention Hypothesis

AI products have a unique retention dynamic: the AI gets more valuable as the system learns the user's preferences and context. This creates a compounding retention effect — but only if the user stays long enough to experience it.

```
AI RETENTION DYNAMIC

Week 1–2: AI knows nothing about the user → generic outputs → lower acceptance rate → higher churn risk
Week 3–4: AI has learned basic preferences → improving outputs → acceptance rate rises → retention strengthens
Month 2+: AI has rich context → personalised outputs → strong habit → high long-term retention

Implication: The first 2 weeks are the highest churn risk period for AI products.
Intervention: Accelerate personalisation in Week 1 (onboarding that captures context faster).
```

### AI-Specific Retention Metrics

| Metric | Definition | What It Tells You |
|---|---|---|
| **AI retention lift** | D30 retention of AI users vs non-AI users | Does AI adoption drive retention? |
| **AI churn correlation** | Churn rate following AI quality events | Does AI failure drive churn? |
| **AI trust trajectory** | Acceptance rate by Week 1 / Week 4 / Month 3 | Is trust building over time? |
| **Post-AI-failure retention** | D30 retention of users who experienced AI failure | How damaging is AI failure to retention? |

```
AI RETENTION ANALYSIS

Do users who adopt AI retain better?
  AI adopters (used AI in Week 1): D30 = ___%
  Non-adopters: D30 = ___%
  AI retention lift: ___%
  Conclusion: _______________________________________________

Does AI quality drive retention?
  Users who rated AI outputs positively: D30 = ___%
  Users who rated AI outputs negatively: D30 = ___%
  Quality-retention correlation: _______________________________________________

Does AI failure cause churn?
  Users who experienced an AI failure event: churn rate = ___%
  Users who did not: churn rate = ___%
  Failure churn premium: ___%
  Conclusion: _______________________________________________
```

---

## Templates

### Template A: Monthly Retention Report

```
# Monthly Retention Report — [Month Year]
Author: ___  |  Product: ___

## Retention Summary
D1 retention: ___%  (Target: ___% / vs last month: +/-__%)
D7 retention: ___%  (Target: ___% / vs last month: +/-__%)
D30 retention: ___%  (Target: ___% / vs last month: +/-__%)

Status: 🟢 On track / 🟡 Watch / 🔴 Investigate

## Cohort Trend
Recent cohorts vs 3-month average: Better / Same / Worse
Biggest cohort improvement: _______________________________________________
Biggest cohort concern: _______________________________________________

## Churn Analysis
Top churn categories this month:
1. ___ — ___% of churned users
2. ___ — ___% of churned users

Churn interviews completed: ___  |  Key theme: _______________________________________________

## AI Retention (if applicable)
AI retention lift: +___%  |  AI failure churn premium: ___%

## Active Interventions
| Intervention | Status | Primary metric | Current result |
|-------------|--------|---------------|----------------|
| | | | |

## Next Month's Priority
Retention focus: _______________________________________________
Key experiment: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Measuring retention as "any login" | Define retention as completing the core value action |
| Reporting average retention across all cohorts | Analyse each cohort separately — averages hide regression |
| Ignoring the shape of the retention curve | Curve shape tells you more than the Day N number |
| Running retention interventions without A/B tests | Every intervention must be tested — correlation doesn't prove causation |
| Treating all churn the same | Classify churn type before designing the intervention |
| Interviewing too few churned users (< 8) | 8–12 interviews minimum for meaningful pattern detection |
| Ignoring AI failure as a churn driver | Track post-AI-failure retention for all AI products |
| Optimising D1 retention while ignoring D30 | Both matter — improving D1 at the cost of D30 quality is not progress |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Retention dashboard review | Weekly | PM |
| Cohort retention table update | Weekly | Data analyst |
| Churn interviews | Monthly (8–12) | PM + Research |
| Retention driver analysis | Monthly | Data analyst |
| Retention intervention A/B test | Per experiment | PM |
| Monthly retention report | Monthly | PM |
| AI retention analysis | Monthly | PM + AI team |
| Annual retention framework review | Annually | CPO + PM leads |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Retention Analysis Framework

> **Best for:** Setting up the full retention measurement, diagnosis, and intervention system for a product.

```
You are a product analytics expert helping me build a complete retention analysis framework.

Design the framework across all five layers:

1. Measurement — define the right retention metric for my product type, design the cohort table structure, and identify the key retention windows to track

2. Diagnosis — design the retention driver analysis (magic actions), the segment breakdown approach, and the engagement-retention matrix

3. Churn analysis — design the churn classification taxonomy, the churn interview protocol, and the root cause analysis structure

4. Intervention — design the intervention prioritisation framework and the experiment sequencing strategy

5. Monitoring — design the alert thresholds and the predictive churn model

For each layer:
- Give specific recommendations for my product type (not generic advice)
- Identify the data requirements
- Recommend the tool or query structure

After all layers:
- Identify the single retention metric that matters most at my stage
- Identify the highest-leverage intervention based on my current situation
- Design the monthly retention review meeting structure

My product: [describe what it does]
Current D7 retention: ___%  |  D30 retention: ___%
Stage: [early / growth / scale]
Current analytics tooling: [what data do I have?]
Is this an AI product: [yes/no]
Known retention problem: [what do you already suspect is causing churn?]
```

---

### Prompt 2 — Identify the Magic Actions that Drive Retention

> **Best for:** Finding which specific user behaviours in the first week most strongly predict long-term retention.

```
You are a data analyst helping me identify the "magic actions" — the specific user behaviours that predict D30 retention.

Design the complete analysis:

1. Analysis methodology
   - What is the statistical approach for identifying which Week 1 actions predict D30 retention?
   - How do I control for selection bias (high-intent users may both complete more actions AND retain better for unrelated reasons)?
   - What minimum sample size do I need for statistically meaningful results?

2. Feature list
   - Generate a list of 15–20 user actions I should include in this analysis, based on my product description
   - For each: explain why it might predict retention

3. Analysis template
   - Write the SQL or analytics query structure for this analysis
   - Design the output table format

4. Validation test
   - How do I validate that a "magic action" is genuinely causal (not just correlated)?
   - Design the A/B test that confirms causality for the top magic action

5. Activation redesign
   - Once I identify the magic action, how do I redesign onboarding to ensure more users complete it?

My product: [describe the core value and key user actions]
Analytics tool: [Amplitude / Mixpanel / SQL / other]
Current D7 retention: ___%
Users available for analysis: [sample size]
```

---

### Prompt 3 — Conduct a Churn Root Cause Analysis

> **Best for:** After gathering churn interview data — systematically identifying and prioritising the root causes of user churn.

```
You are a product researcher helping me conduct a structured churn root cause analysis.

I will share my churn interview findings. Your job is to:

1. Categorise each finding
   Using the churn taxonomy (product value gap / activation failure / AI quality failure / competitive switch / life event), classify each observation

2. Quantify the categories
   - What % of churned users does each category represent?
   - Which is the largest category?
   - Which is the most addressable with product changes?

3. Extract the key insight
   - What is the single most important thing churned users wanted that they didn't get?
   - Is there a specific moment or feature where the product failed them?
   - For AI products: was AI quality a factor, and how often?

4. Competitive intelligence
   - What alternatives did churned users move to?
   - What specifically does the alternative do better?
   - Is this a feature gap, quality gap, pricing gap, or positioning gap?

5. Intervention recommendations
   - For each major churn category: what is the most promising intervention?
   - Which intervention addresses the most churn with the least effort?
   - Write the hypothesis for the top 2 interventions in full format

Churn interview findings:
[paste quotes, themes, or a summary of what churned users told you]

Context:
My product: [describe]
Churn rate: ___%/month
Interviews conducted: ___
```

---

### Prompt 4 — Design a Retention Improvement Experiment

> **Best for:** Translating a retention hypothesis into a rigorous A/B test designed to definitively answer whether the intervention works.

```
You are an experimentation specialist helping me design a retention improvement experiment.

I have identified a retention hypothesis I want to test. Design the complete experiment:

1. Hypothesis validation
   - Is the hypothesis written in testable format? If not, rewrite it.
   - Is D7 or D30 retention the right primary metric, or should I use a leading indicator?
   - What is the minimum detectable effect I should power for?

2. Experiment design
   - Control: exactly what does the control experience?
   - Treatment: exactly what does the treatment experience?
   - Is there risk of contamination between groups? (e.g. if users are in the same team)
   - What is the right traffic split?

3. Statistical design
   - How many users do I need per variant for 95% significance?
   - How many days will the experiment need to run?
   - If D30 is my primary metric, can I use a leading indicator to get results faster?

4. Guardrail metrics
   - What metrics must not decline while testing this retention intervention?
   - How do I catch if the intervention helps short-term retention but hurts long-term?

5. Decision framework
   - Pre-register: exactly what result will cause me to ship?
   - Pre-register: exactly what result will cause me to abandon this intervention?
   - What do I do if the result is ambiguous?

My retention hypothesis: [write it out in full]
Current D7 retention: ___%  (target improvement: ___%)
Daily new users available for the experiment: ___
```

---

### Prompt 5 — Analyse AI-Specific Retention Dynamics

> **Best for:** Understanding how AI features specifically affect retention — both the positive compounding effect and the negative impact of AI failure events.

```
You are an AI product analyst helping me understand how AI features are affecting my product's retention.

Analyse the AI-specific retention dynamics across four questions:

1. Does AI adoption drive retention?
   - Design the analysis: how do I measure retention of AI users vs non-AI users?
   - How do I control for the fact that higher-intent users are more likely to both use AI and retain better?
   - What retention lift would confirm that AI is a genuine retention driver?

2. Does AI quality affect retention?
   - Design the analysis: how do I correlate AI output quality scores with subsequent retention?
   - How do I identify if there is a quality threshold below which retention suffers significantly?

3. Do AI failure events cause churn?
   - Define an "AI failure event" for my product
   - Design the analysis: what is the D30 retention rate of users who experienced an AI failure vs those who didn't?
   - How much of my current churn might be explained by AI failure events?

4. Is trust building over time?
   - Design the AI trust trajectory analysis: track acceptance rate at Week 1 / Week 4 / Month 3
   - If trust is not building: what does this indicate about the AI personalisation system?

After the analysis design:
- Recommend the top 2 AI-specific retention interventions based on the likely findings
- Design the monitoring that would catch an AI-driven retention decline before it shows in D30 numbers

My AI product: [describe]
Current retention rates: D7 = ___% / D30 = ___%
Known AI quality issues: [any existing awareness of AI failure patterns]
AI adoption rate: ___%
```

