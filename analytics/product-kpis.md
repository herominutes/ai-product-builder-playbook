# 📊 Product KPIs — AI Product Builder Playbook

> **A framework for defining, organising, and operationalising the key performance indicators that measure product health and team effectiveness**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The KPI Framework Model](#the-kpi-framework-model)
- [KPI Category 1: Acquisition](#kpi-category-1-acquisition)
- [KPI Category 2: Activation](#kpi-category-2-activation)
- [KPI Category 3: Retention](#kpi-category-3-retention)
- [KPI Category 4: Revenue](#kpi-category-4-revenue)
- [KPI Category 5: Referral](#kpi-category-5-referral)
- [AI Product KPIs](#ai-product-kpis)
- [KPI Governance](#kpi-governance)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

KPIs are not dashboards. A team with 47 metrics tracked across six dashboards does not have 47 KPIs — it has measurement infrastructure and no clarity. KPIs are the small set of metrics that a team commits to moving, that leadership uses to assess health, and that change what the team does when they move in the wrong direction.

> **Core Principle:** A KPI you cannot act on is not a KPI — it is a report. Every KPI must have a clear owner, a target, and a defined response when the target is missed. If missing the target produces no change in behaviour, the metric is decorative.

For AI products, the standard AARRR KPI framework requires significant modification. AI introduces new categories of product health — model performance, AI adoption, delegation depth, and output quality — that do not exist in traditional product frameworks. A product team that only tracks acquisition and retention will systematically miss the signals that matter most.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| New product or feature launch — need a KPI set | 🔴 Critical — define before launch |
| Current KPI set is too large or not actionable | 🔴 Critical — reduce and sharpen |
| Team is measuring activity instead of outcomes | 🟠 High — redesign the KPI framework |
| Quarterly planning — aligning team on success metrics | 🟠 High |
| Investor or board reporting — need a coherent KPI story | 🟠 High |
| New team member onboarding — what does success look like? | 🟡 Medium |

---

## The KPI Framework Model

Product KPIs are organised across five categories — the AARRR framework — extended with AI-specific metrics for AI products.

```
ACQUISITION
  ↓ how users find and arrive at the product
ACTIVATION
  ↓ how users experience first value
RETENTION
  ↓ how users return and form habits
REVENUE
  ↓ how the product generates business value
REFERRAL
  ↓ how users spread the product
[AI PERFORMANCE]
  ↓ how the AI component performs (AI products only)
```

| Category | Core Question | Primary Owner | Review Cadence |
|---|---|---|---|
| **Acquisition** | Are we reaching the right users? | Growth / Marketing | Weekly |
| **Activation** | Are users experiencing value quickly? | PM | Weekly |
| **Retention** | Are users coming back? | PM | Weekly |
| **Revenue** | Are we converting value to revenue? | PM / Finance | Monthly |
| **Referral** | Are users recommending us? | PM / Growth | Monthly |
| **AI performance** | Is the AI delivering quality? | PM / AI team | Weekly |

> **Rule of thumb:** Define no more than 2–3 KPIs per category. A team tracking 30 metrics tracks nothing. A team tracking 12 metrics across six categories can actually move the needle.

---

## KPI Category 1: Acquisition

### 1.1 Core Acquisition KPIs

| KPI | Definition | Target Range | Alert Threshold |
|---|---|---|---|
| **New users** | Unique new users per week/month | Depends on stage | < 80% of prior period |
| **Acquisition channel mix** | % of new users from each channel | Balanced across 2–3 channels | Single channel > 70% |
| **Cost per acquisition (CPA)** | Total acquisition cost ÷ new users | Product-specific | > 150% of target |
| **Organic acquisition rate** | % of new users from organic sources | > 40% | < 20% |
| **Qualified traffic rate** | % of visitors who sign up / activate | > 15% | < 8% |
| **Time to signup** | Time from first visit to account creation | < 5 minutes | > 15 minutes |

### 1.2 Acquisition KPI Design Principles

```
ACQUISITION KPI DESIGN

Select 2–3 acquisition KPIs based on your growth stage:

Early stage (< 1,000 users):
Primary: New users per week (volume signal)
Secondary: Source of new users (channel signal)
Skip: CPA (too early to optimise cost)

Growth stage (1,000–100,000 users):
Primary: New qualified users per week (quality > volume)
Secondary: CPA by channel (efficiency signal)
Counter: Activation rate of acquired users (quality check)

Scale stage (> 100,000 users):
Primary: Organic acquisition rate (sustainability signal)
Secondary: CPA trend (efficiency trend)
Counter: Cohort quality of recent vs prior acquisitions
```

---

## KPI Category 2: Activation

### 2.1 Defining Activation

Activation is the moment a new user first experiences the core value of the product. It is the most important early-stage KPI — and the most commonly measured incorrectly.

| Common Mistake | Better Approach |
|---|---|
| Activation = completed signup | Activation = completed the action that delivers first value |
| Activation = viewed the dashboard | Activation = created or completed the core job |
| Same activation definition for all users | Activation differs by user segment and use case |
| One activation event | Staged activation: first value moment + habit formation moment |

### 2.2 Core Activation KPIs

| KPI | Definition | Target | Alert |
|---|---|---|---|
| **Day 1 activation rate** | % of new users who reach the activation event on Day 1 | > 40% | < 20% |
| **Time to first value (TTFV)** | Time from signup to first activation event | < 10 minutes | > 30 minutes |
| **Onboarding completion rate** | % of new users who complete the onboarding flow | > 60% | < 35% |
| **Aha moment identification** | Specific action that predicts retention (validated by cohort analysis) | Defined and instrumented | Not yet identified |
| **Activation-to-retention rate** | % of activated users who return in Week 2 | > 50% | < 30% |
| **Drop-off step** | The step in onboarding with the highest abandonment | Identified and improving | Worsening trend |

### 2.3 Activation Funnel Analysis

```
ACTIVATION FUNNEL DESIGN

Step 1: [First action after signup]
  Completion rate: ___%  |  Drop-off: ___%

Step 2: [Core setup action]
  Completion rate: ___%  |  Drop-off: ___%

Step 3: [First core job action]
  Completion rate: ___%  |  Drop-off: ___%

Step 4: [First value experienced]
  Completion rate: ___%  |  Drop-off: ___%

Activation event: [specific event that signals first value]
  Activation rate: ___%

Overall funnel conversion: Signup → Activation = ___%
Biggest drop-off step: Step ___  |  Drop-off: ___%
Priority: Fix Step ___ (largest drop-off with highest downstream retention impact)
```

---

## KPI Category 3: Retention

### 3.1 Retention Framework

Retention is the most important KPI category for product health. No acquisition or activation rate compensates for poor retention.

| Retention KPI | Definition | Healthy Range | Alert |
|---|---|---|---|
| **Day 1 retention** | % of new users who return on Day 1 | > 25% | < 12% |
| **Day 7 retention** | % of new users who return on Day 7 | > 15% | < 7% |
| **Day 30 retention** | % of new users who return on Day 30 | > 8% | < 4% |
| **Weekly active users (WAU)** | Unique users who take the core action in a 7-day window | Growing | Declining for 2+ weeks |
| **WAU/MAU ratio** | WAU ÷ MAU — measures engagement frequency | > 0.4 for daily value | < 0.2 |
| **Churn rate** | % of active users who become inactive in a period | < 5% monthly | > 10% monthly |
| **Resurrection rate** | % of churned users who return | > 10% | < 5% |
| **Retention curve flattening** | The point at which the retention curve stabilises | Defined and above 0% | Curve reaches 0% |

### 3.2 Cohort Retention Analysis

```
RETENTION COHORT TABLE

Cohort | D0 | D1 | D7 | D14 | D30 | D60 | D90
Jan    | 100%| ___| ___| ___ | ___ | ___ | ___
Feb    | 100%| ___| ___| ___ | ___ | ___ | ___
Mar    | 100%| ___| ___| ___ | ___ | ___ | ___

Reading the table:
- Horizontal: how does one cohort retain over time?
- Vertical: are recent cohorts retaining better or worse than older ones?

Key questions:
1. Is the D7 retention improving cohort over cohort? (product improvement signal)
2. Is the D30 curve flattening above 0%? (product-market fit signal)
3. Is any recent cohort significantly underperforming? (regression signal)
```

### 3.3 Churn Analysis Framework

```
CHURN ANALYSIS FRAMEWORK

Step 1 — Define churn
Churned user = user who [was active in last N days] but [has not been active in last M days]
Typical: Active = last 7 days / Churned = inactive for 30 days

Step 2 — Segment churned users
By: when they churned (new user churn vs long-term user churn)
By: what they did before churning (last action before churn)
By: what they never did (which activation events they missed)

Step 3 — Interview churned users (8–12)
"What caused you to stop using [product]?"
"What were you using before? What did you go back to?"
"What would have to change for you to come back?"

Step 4 — Identify churn predictors
Which user behaviours in Week 1 predict churn by Week 4?
Build a churn risk model: users who [did not complete X] churn at [N]× the rate of users who did.

Step 5 — Design churn interventions
For each churn predictor: what product or communication change prevents it?
Run A/B test on each intervention; measure impact on D30 retention.
```

---

## KPI Category 4: Revenue

### 4.1 Core Revenue KPIs

| KPI | Definition | Note |
|---|---|---|
| **Monthly Recurring Revenue (MRR)** | Monthly subscription revenue | Core SaaS metric |
| **Annual Recurring Revenue (ARR)** | MRR × 12 | For annual planning |
| **Average Revenue Per User (ARPU)** | MRR ÷ paying users | Pricing health signal |
| **Customer Lifetime Value (LTV)** | ARPU × average customer lifespan | Should be > 3× CAC |
| **Customer Acquisition Cost (CAC)** | Total sales & marketing cost ÷ new customers | Efficiency metric |
| **LTV:CAC ratio** | LTV ÷ CAC | Target: > 3:1 |
| **Payback period** | CAC ÷ monthly gross profit per customer | Target: < 12 months |
| **Net Revenue Retention (NRR)** | (Starting MRR + expansion - contraction - churn) ÷ Starting MRR | > 100% = growth without new customers |
| **Conversion rate** | % of free/trial users who convert to paid | Benchmark: 2–5% freemium |

### 4.2 Revenue KPI Priorities by Stage

| Stage | Primary Revenue KPI | Secondary | Skip |
|---|---|---|---|
| Pre-revenue | Activation rate (proxy for revenue readiness) | Time to close first paying customer | CAC, LTV |
| Early revenue | MRR growth rate | Conversion rate | NRR (too few customers) |
| Growth | NRR | LTV:CAC | None |
| Scale | NRR + Payback period | Gross margin | None |

---

## KPI Category 5: Referral

### 5.1 Core Referral KPIs

| KPI | Definition | Target | Note |
|---|---|---|---|
| **Net Promoter Score (NPS)** | % Promoters minus % Detractors | > 30 B2B; > 50 consumer | Survey 10% of users monthly |
| **Organic referral rate** | % of new users who came via referral | > 15% | Viral coefficient signal |
| **Viral coefficient (K)** | Average new users per existing user per period | > 1.0 = viral growth | K < 0.5 = referral not working |
| **Referral program conversion** | % of invited users who sign up | > 20% | If referral program exists |
| **Product reviews and ratings** | Average rating on G2, Capterra, App Store | > 4.0 | Public trust signal |
| **Social mentions** | Volume of organic product mentions | Growing trend | Brand health signal |

---

## AI Product KPIs

### 6.1 Why AI Products Need Additional KPIs

The AARRR framework captures user behaviour but not AI performance. An AI product that acquires, activates, and retains users while producing poor AI outputs is a ticking trust problem. AI-specific KPIs close this gap.

### 6.2 AI Performance KPIs

| KPI | Definition | Target | Alert |
|---|---|---|---|
| **AI feature adoption rate** | % of eligible users who use the AI feature per week | > 50% | < 25% |
| **AI output acceptance rate** | % of AI outputs accepted without modification | > 60% | < 35% |
| **AI task completion rate** | % of AI-initiated tasks that reach a successful outcome | > 85% | < 70% |
| **AI quality score** | Average quality rating from automated evaluation | > 4.0 / 5 | < 3.5 |
| **AI refusal rate** | % of requests the AI declines (out of scope / safety) | 2–8% | < 1% or > 15% |
| **AI latency P99** | 99th percentile response time | < 5 seconds | > 10 seconds |
| **Cost per AI interaction** | Total AI cost ÷ total AI interactions | Within budget model | > 150% of budget |
| **Hallucination rate** | % of outputs flagged as containing ungrounded claims | < 2% | > 5% |

### 6.3 AI Trust KPIs

| KPI | Definition | Target | Note |
|---|---|---|---|
| **AI trust score** | Survey: "How much do you trust this AI's outputs?" (1–5) | > 3.8 | Monthly survey of active users |
| **AI correction rate** | % of AI outputs that users manually correct | < 15% | High = AI not meeting quality bar |
| **AI bypass rate** | % of users who skip the AI feature and complete manually | < 10% | High = AI not providing value |
| **AI session share** | % of sessions that include at least one AI interaction | > 60% | Habit formation signal |
| **First AI interaction retention lift** | Retention rate of users who use AI vs those who don't | AI users > 15% higher | Value proof signal |

---

## KPI Governance

### 7.1 KPI Ownership Matrix

```
KPI OWNERSHIP MATRIX

| KPI | Owner | Reviewer | Cadence | Alert goes to |
|-----|-------|----------|---------|---------------|
| Activation rate | PM | CPO | Weekly | PM + Design |
| D7 retention | PM | CPO | Weekly | PM |
| MRR | PM | CFO | Monthly | PM + CEO |
| NPS | PM | CPO | Monthly | PM |
| AI quality score | PM + AI lead | CPO | Weekly | PM + AI lead |
| AI adoption rate | PM | CPO | Weekly | PM |
```

### 7.2 KPI Review Structure

```
WEEKLY KPI REVIEW (30 minutes)
Attendees: PM + Engineering lead + Data analyst
Agenda:
  1. Red metrics (any KPI below alert threshold): root cause + action
  2. Yellow metrics (trending toward alert): early intervention
  3. Green metrics (on target): note and move on
Output: Action items assigned for the week

MONTHLY KPI REVIEW (60 minutes)
Attendees: PM leads + CPO + Finance
Agenda:
  1. Monthly trend across all KPI categories
  2. Cohort analysis: how are recent cohorts performing vs older ones?
  3. Leading indicator check: are activation KPIs predicting next month's retention?
  4. AI performance deep dive
Output: Updated targets, resource reallocation decisions

QUARTERLY KPI RESET (2 hours)
Attendees: Full leadership
Agenda:
  1. Are current KPIs still the right ones?
  2. Have any KPIs been gamed or lost meaning?
  3. Are there new product areas requiring new KPIs?
  4. Set targets for next quarter
Output: Refreshed KPI set with Q targets
```

---

## Templates

### Template A: Product KPI Dashboard

```
# Product KPI Dashboard — [Product Name]
Week of: ___  |  Owner: ___

## Traffic Light Summary
🟢 On track  🟡 Watch  🔴 Investigate

| Category | KPI | Current | Target | Status | vs. Last Week |
|----------|-----|---------|--------|--------|--------------|
| Acquisition | New users | | | | |
| Activation | D1 activation rate | | | | |
| Retention | D7 retention | | | | |
| Retention | WAU | | | | |
| Revenue | MRR | | | | |
| Referral | NPS | | | | |
| AI | AI adoption rate | | | | |
| AI | AI quality score | | | | |

## This Week's Focus
Red metrics requiring action: _______________________________________________
Owner: ___  |  Action: ___  |  Due: ___

## Highlights
What went well: _______________________________________________
What concerns me: _______________________________________________
```

### Template B: KPI Definition Card

```
## KPI: [Name]
Category: Acquisition / Activation / Retention / Revenue / Referral / AI
Owner: _______________________________________________

Definition:
Numerator: _______________________________________________
Denominator: _______________________________________________
Time window: _______________________________________________
Measurement: _______________________________________________

Current value: _______________________________________________
Target (Q___): _______________________________________________
Alert threshold: _______________________________________________
Alert action: _______________________________________________

Why this KPI matters:
_______________________________________________

What moves this KPI:
_______________________________________________

What this KPI does NOT measure (important distinction):
_______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Too many KPIs (> 15) | Max 2–3 per category; 12–15 total |
| Metrics with no owner | Every KPI has one named owner |
| Metrics with no target | Every KPI has a specific quarterly target |
| Activity metrics mistaken for outcome metrics | Every KPI must be traceable to user value |
| No alert threshold defined | Every KPI has a specific alert condition and response |
| AI products using only traditional AARRR | Add AI-specific KPI category for all AI features |
| KPI review that produces no action | Every red metric must produce an assigned action item |
| KPIs that can be improved without improving user value | Run the gaming test on all KPI candidates |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| KPI dashboard review | Weekly | PM |
| Red metric investigation | As triggered | PM + Data |
| Monthly cohort analysis | Monthly | PM + Data |
| KPI targets review | Quarterly | PM + Leadership |
| Full KPI framework review | Annually | CPO + PM leads |
| AI KPI calibration | Monthly | PM + AI team |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Define a Complete Product KPI Set

> **Best for:** Establishing the full KPI framework for a new product or resetting a KPI set that has grown too large or lost focus.

```
You are a product analytics expert helping me define a focused, actionable KPI set.

Design the complete KPI framework across all six categories:

1. Acquisition (2–3 KPIs) — how users find and arrive
2. Activation (2–3 KPIs) — how users experience first value
3. Retention (2–3 KPIs) — how users return and form habits
4. Revenue (2–3 KPIs) — how the product generates business value
5. Referral (1–2 KPIs) — how users spread the product
6. AI performance (2–3 KPIs) — how the AI component performs [if applicable]

For each KPI:
- Write the precise definition (numerator / denominator / time window)
- Set a benchmark target for my stage
- Define the alert threshold that triggers investigation
- Name the primary owner
- Explain what moving this KPI requires in product terms

After designing the full set:
- Confirm the total is ≤ 15 KPIs
- Identify which 3 KPIs matter most at my current stage
- Run the gaming test: how could each KPI be improved without improving user value?

My product: [describe]
Stage: [early / growth / scale]
Current metrics tracked: [list what you already measure]
Primary business model: [freemium / subscription / usage-based / enterprise]
Is this an AI product: [yes/no]
```

---

### Prompt 2 — Design the Activation KPI and Funnel

> **Best for:** Identifying the true activation event and mapping the onboarding funnel that gets users there.

```
You are a product growth expert helping me define the right activation KPI and onboarding funnel.

Guide me through activation KPI design:

1. Activation event identification
   - What specific user action represents "first value experienced" in my product?
   - How is this different from "completed signup" or "logged in"?
   - How do I validate this is the right event? (cohort analysis approach)

2. Activation correlation test design
   - Write the analysis: do users who complete [activation event] retain at a higher rate?
   - What data do I need and how do I run this?
   - At what retention lift does this confirm [event] as the right activation metric?

3. Activation funnel design
   - Map the 4–6 steps between signup and first activation event
   - For each step: what is the typical completion rate benchmark?
   - Identify: which step has the highest drop-off and what causes it?

4. Activation KPI set
   - Write 3 activation KPIs with precise definitions
   - Set targets appropriate to my product stage
   - Define alert thresholds

5. Activation improvement roadmap
   - What are the top 3 changes most likely to improve activation rate?
   - How do I prioritise between reducing time to activation vs improving activation rate?

My product: [describe]
Current signup to activation flow: [describe the current onboarding steps]
Known drop-off points: [where do users leave?]
Current activation rate (if known): ____%
```

---

### Prompt 3 — Build a Retention Cohort Analysis

> **Best for:** Understanding how well the product retains users over time, and whether retention is improving or declining.

```
You are a data analyst helping me build and interpret a retention cohort analysis.

Design the complete retention analysis:

1. Cohort definition
   - How should I define cohorts? (weekly / monthly / by acquisition channel / by activation behaviour)
   - What event defines the start of a cohort? (signup / first purchase / activation event)
   - How do I define "retained" for this cohort? (returns within N days / completes core action)

2. Cohort table construction
   - Write the SQL or analytics query structure for building the cohort table
   - What time intervals should the columns represent for my product? (D1/D7/D30 vs W1/W2/W4)

3. Retention curve interpretation
   - What does a healthy retention curve look like for my product type?
   - How do I identify if the curve has "flattened" (achieved product-market fit signal)?
   - How do I diagnose if recent cohorts are underperforming older cohorts?

4. Retention driver analysis
   - How do I identify which user actions in Week 1 predict D30 retention?
   - Write the analysis approach for finding the "magic actions" that predict retention

5. Retention intervention design
   - Based on the analysis, what are the top 3 product changes most likely to improve D7 retention?
   - How do I A/B test each intervention?
   - How do I measure the impact on retention without waiting 30 days?

My product: [describe]
Current retention data (if available): [D1 / D7 / D30 retention rates]
Key user actions tracked: [list what events you have in your analytics]
User segment of interest: [which segment to focus on]
```

---

### Prompt 4 — Design AI-Specific KPIs

> **Best for:** Adding AI performance metrics to a product KPI framework for features that involve LLMs or AI agents.

```
You are an AI product metrics specialist helping me design the AI-specific KPI layer for my product.

Design a complete AI performance KPI set:

1. AI adoption KPIs
   - How do I measure whether users are actually using the AI feature?
   - How do I distinguish voluntary AI adoption from forced AI exposure?
   - What adoption rate target is appropriate for my feature type?

2. AI quality KPIs
   - How do I measure output quality without manual review of every output?
   - Design the automated quality scoring approach for my use case
   - What quality metrics are most predictive of user trust?

3. AI trust KPIs
   - What behavioural signals indicate users trust the AI? (acceptance rate, bypass rate, correction rate)
   - How do I measure trust without directly surveying users every week?
   - What is the relationship between AI trust and long-term retention?

4. AI efficiency KPIs
   - How do I measure the time saved by AI for my users?
   - How do I measure the cost efficiency of AI delivery?
   - What AI cost per interaction target is sustainable at my growth trajectory?

5. AI counter-metrics
   - What metrics must NOT decline as AI adoption increases?
   - How do I detect if AI is reducing user skill rather than augmenting it?

After designing the KPI set:
- Rank the AI KPIs by importance for my stage
- Identify which are leading indicators vs lagging indicators
- Write the weekly AI health check template

My AI feature: [describe what the AI does]
User's core job: [what are users trying to accomplish?]
AI interaction model: [chat / embedded / autonomous / assistant]
Current AI metrics tracked: [list if any]
```

---

### Prompt 5 — Investigate a KPI Decline

> **Best for:** When a key metric has declined and you need a structured approach to diagnosing the root cause.

```
You are a product analytics expert helping me investigate a KPI decline.

Guide me through a structured root cause investigation:

1. Scope the decline
   - Is this decline concentrated in a specific user segment, channel, device, or geography?
   - When exactly did it start? What product changes were made around that time?
   - Is this a one-time drop or a gradual trend?

2. Metric tree analysis
   - Which input metrics in the metric tree drove this decline?
   - Is this driven by fewer users entering the funnel (acquisition) or fewer completing it (conversion)?
   - Is this affecting all users equally or a specific cohort?

3. Hypothesis generation
   Based on the above, generate 3–5 specific hypotheses for the root cause.
   For each hypothesis: what data would confirm or refute it?

4. Investigation plan
   - In what order should I test the hypotheses? (start with highest likelihood + easiest to confirm)
   - Write the specific query or analysis for each hypothesis
   - What is the decision: if hypothesis is confirmed, what is the fix?

5. Prevention
   - What monitoring alert would have caught this decline 1–2 weeks earlier?
   - Add this to the monitoring system

The KPI that declined: [name and define it]
The extent of decline: [by how much, over what time period]
Other metrics during the same period: [what moved up or down at the same time?]
Recent product changes: [anything deployed in the relevant window]
Current metric tree inputs: [what are the L1 drivers of this KPI?]
```

