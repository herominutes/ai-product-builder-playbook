# ⭐ North Star Metrics — AI Product Builder Playbook

> **A framework for identifying, defining, and operationalising the single metric that best captures the value your product delivers to users**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The North Star Model](#the-north-star-model)
- [Stage 1: North Star Identification](#stage-1-north-star-identification)
- [Stage 2: North Star Validation](#stage-2-north-star-validation)
- [Stage 3: Metric Tree Design](#stage-3-metric-tree-design)
- [Stage 4: North Star Operationalisation](#stage-4-north-star-operationalisation)
- [North Star Metrics for AI Products](#north-star-metrics-for-ai-products)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Every product has dozens of metrics. The North Star is the one metric that, if it improves, you are confident the product is delivering genuine value to users — and that long-term business health will follow. It is the single point of alignment for the entire team: what are we ultimately trying to move?

> **Core Principle:** A North Star metric is not the metric you want to improve. It is the metric that proves you have improved something that matters to users. The distinction is critical — you can improve any metric by gaming it. You improve a North Star metric only by delivering real value.

For AI products, defining the right North Star is especially important — and especially difficult. AI enables new forms of value that traditional product metrics don't capture. A user who delegates a task entirely to AI may generate fewer clicks, fewer sessions, and less "engagement" — while receiving dramatically more value. Measuring activity rather than outcomes will systematically mislead you.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| New product or major initiative — need alignment on success | 🔴 Critical — define before any feature work begins |
| Team is optimising for different metrics and pulling in different directions | 🔴 Critical — metric misalignment is a team alignment failure |
| Current North Star has been gamed or is no longer meaningful | 🟠 High — refresh before next planning cycle |
| Launching an AI feature that changes the nature of user value | 🟠 High — traditional engagement metrics may be misleading |
| Annual strategy refresh | 🟡 Medium |
| Investor or board presentation requiring a single success metric | 🟡 Medium |

---

## The North Star Model

The North Star framework operates at three levels. The North Star sits at the top; below it, a metric tree shows the input metrics that drive it.

```
NORTH STAR METRIC
  ↓ the single metric that captures user value delivery
LEVEL 1 INPUT METRICS (3–5)
  ↓ the main drivers of the North Star
LEVEL 2 INPUT METRICS (2–4 per L1 metric)
  ↓ the levers that move the L1 metrics
TEAM METRICS
  ↓ what individual teams optimise day-to-day
```

| Level | What It Is | Who Owns It | Review Cadence |
|---|---|---|---|
| **North Star** | The single measure of user value | CPO / CEO | Quarterly |
| **L1 inputs** | 3–5 drivers of the North Star | Product leads | Monthly |
| **L2 inputs** | Tactical levers for each L1 | Feature teams | Weekly |
| **Team metrics** | Day-to-day execution metrics | Individual teams | Sprint |

> **Rule of thumb:** If everyone on the team can name the North Star without looking it up, it is embedded. If there is any disagreement about what the North Star is, it is not yet real.

---

## Stage 1: North Star Identification

### 1.1 The North Star Criteria

A metric qualifies as a North Star only if it meets all five criteria:

| Criterion | Definition | Test |
|---|---|---|
| **Value indicator** | Measures value delivered to users, not just activity | Remove one unit of value — does the metric drop? |
| **Leading indicator** | Predicts long-term business health | Does improving it correlate with retention and revenue? |
| **Team-influenceable** | The product team can move it through product decisions | Could a product change move this metric within 90 days? |
| **Measurable** | Can be tracked with current or buildable instrumentation | Is it instrumented today, or can it be? |
| **Understandable** | Every team member can explain it without qualification | Can a new engineer explain it on day one? |

### 1.2 North Star Candidate Generation

Generate candidates across three categories before narrowing:

```
NORTH STAR CANDIDATE GENERATION

Category 1 — Breadth metrics (how many users get value?)
Examples: Weekly active users, % of users who complete core job, unique users who hit "aha moment"
Best for: Products where growing the number of value-experiencing users is the primary goal

Category 2 — Depth metrics (how much value does each user get?)
Examples: Tasks completed per user per week, time saved per user per session, outcomes achieved per user
Best for: Products where depth of value per user predicts retention and expansion

Category 3 — Efficiency metrics (how efficiently do users achieve their goal?)
Examples: Time to first value, task completion rate, success rate on core job
Best for: Products where friction reduction is the primary value driver

Category 4 — Outcome metrics (what real-world outcome does the user achieve?)
Examples: Revenue generated by users, decisions made using product insights, quality of user output
Best for: Products that enable measurable user outcomes — particularly AI products

Candidates generated:
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
4. _______________________________________________
5. _______________________________________________
```

### 1.3 North Star Selection Workshop

Run this as a 90-minute cross-functional session:

```
NORTH STAR SELECTION WORKSHOP AGENDA

Attendees: CPO, PM leads, data lead, design lead, engineering lead

00:00 — Frame the question (10 min)
"What is the single behaviour that, if users do it regularly, proves our product is delivering genuine value?"
Not: "What metric makes us look good?"
Not: "What metric do investors care about?"

00:10 — Individual brainstorm (15 min)
Each participant writes 3 North Star candidates on sticky notes.
No discussion during this phase.

00:25 — Share and cluster (20 min)
Each participant presents their candidates.
Cluster similar suggestions.
Identify: the 2–3 most common themes.

00:45 — Criteria scoring (20 min)
Score each candidate against the 5 North Star criteria (1–3 each).
Total = max 15. Target: > 12 to qualify.

01:05 — Correlation test discussion (15 min)
For each surviving candidate: "Do we have evidence this correlates with retention/revenue?"
Eliminate candidates where the correlation is assumed, not evidenced.

01:20 — Decision (10 min)
Select the candidate with the highest criteria score AND the strongest retention/revenue correlation evidence.
Document: why we chose this metric and what we explicitly rejected.
```

---

## Stage 2: North Star Validation

### 2.1 The Correlation Test

A North Star that does not correlate with retention or revenue is not a North Star — it is a vanity metric with a good name.

```
NORTH STAR CORRELATION TEST

Step 1 — Define the correlation hypothesis
"Users who [North Star behaviour] at [frequency/threshold] retain at [target rate] and/or generate [target revenue]."

Step 2 — Segment users by North Star behaviour
Group A: Users who hit the North Star threshold (high)
Group B: Users below the North Star threshold (low)

Step 3 — Measure retention and revenue by group
Group A 30-day retention: ___%
Group B 30-day retention: ___%
Retention delta: ___%

Group A average revenue (if applicable): $___
Group B average revenue: $___
Revenue delta: $___

Step 4 — Evaluate
Strong North Star: Group A retention is > 20% higher than Group B
Weak North Star: Group A retention is < 10% higher than Group B
Not a North Star: No meaningful retention difference

Step 5 — Confirm with cohort analysis
Run this analysis across multiple monthly cohorts.
If the correlation is consistent across cohorts: strong evidence.
If the correlation varies significantly: the metric may be coincidental.
```

### 2.2 The Gaming Test

A North Star that can be improved without delivering user value will be gamed — intentionally or inadvertently.

```
GAMING TEST

For each North Star candidate, ask:
"How could we improve this metric without actually delivering more value to users?"

If the answer is easy:
→ The metric is gameable → Not a North Star → Choose a harder metric or add a quality qualifier

Examples:
"Weekly active users" — gameable with notifications that drive empty sessions → Fail
"Users who complete 3+ tasks per week" — gameable with trivial tasks → Add quality threshold
"Users who rate their AI output as useful" — gameable with leading questions → Fail
"Tasks where user acted on AI output within 24 hours" — harder to game → Pass

Gamed version of our candidate: _______________________________________________
If we achieved this gamed version, would user value actually improve? Yes / No
If No: the metric is gameable → iterate or reject
```

---

## Stage 3: Metric Tree Design

### 3.1 Metric Tree Structure

The metric tree decomposes the North Star into its drivers and sub-drivers. This is the most important product analytics artefact a team can build.

```
METRIC TREE TEMPLATE

North Star: _______________________________________________

Level 1 Input Metrics (what drives the North Star?):
  L1A: _______________________________________________
  L1B: _______________________________________________
  L1C: _______________________________________________

Level 2 Input Metrics (what drives each L1?):
  L1A → L2A1: _______________________________________________
  L1A → L2A2: _______________________________________________

  L1B → L2B1: _______________________________________________
  L1B → L2B2: _______________________________________________

  L1C → L2C1: _______________________________________________
  L1C → L2C2: _______________________________________________

Counter metrics (what should NOT decline if the North Star improves?):
  CM1: _______________________________________________
  CM2: _______________________________________________
```

### 3.2 Metric Decomposition Principles

| Principle | Description |
|---|---|
| **Multiplicative decomposition** | North Star = Metric A × Metric B × Metric C (if the product of the drivers equals the North Star) |
| **Additive decomposition** | North Star = Metric A + Metric B (if the sum of drivers equals the North Star) |
| **Funnel decomposition** | North Star = Users × Completion rate × Success rate (sequential funnel) |
| **Segment decomposition** | North Star = (Segment A × Rate A) + (Segment B × Rate B) (weighted by segment) |

### 3.3 Counter Metrics

Counter metrics prevent optimising one metric at the expense of another that matters equally:

| North Star | Counter Metric | Why |
|---|---|---|
| AI tasks completed per user | User satisfaction with AI outputs | Completing more tasks at lower quality is not progress |
| Weekly active users | 30-day retention | Growing WAU by acquiring churning users is not progress |
| Revenue per user | NPS / satisfaction score | Extracting more money from unhappy users is not progress |
| Time saved by AI | Accuracy of AI outputs | Saving time with wrong answers is not progress |

---

## Stage 4: North Star Operationalisation

### 4.1 Instrumentation Requirements

```
NORTH STAR INSTRUMENTATION CHECKLIST

[ ] The North Star event is tracked in the analytics system
[ ] The event definition is unambiguous — no interpretations between teams
[ ] The event fires only when the user genuinely achieves the measured behaviour (not a proxy)
[ ] The event is tracked at user level (not session level) for cohort analysis
[ ] Historical data is available for at least 12 months (or since product launch)
[ ] The metric can be segmented by: user segment, feature, cohort, geography
[ ] A data quality check runs daily (verify event firing correctly)
[ ] The metric is available in real-time or near-real-time (< 24 hour delay)
```

### 4.2 North Star Dashboard

```
NORTH STAR DASHBOARD DESIGN

Header: [North Star metric name] — [current value] — [vs. 7 days ago: +/-X%]

Section 1: North Star trend (primary view)
  - 90-day trend line
  - 7-day rolling average
  - vs. same period last year (if available)
  - Annotated with product changes that affected the metric

Section 2: Metric tree inputs (secondary view)
  - Each L1 input metric: current value + 7-day change
  - Traffic light: Green (on track) / Amber (watch) / Red (investigate)

Section 3: Segmentation
  - North Star by user segment
  - North Star by feature (for multi-feature products)
  - North Star by cohort (new users vs retained users)

Section 4: Counter metrics
  - Each counter metric: current value + 7-day change
  - Alert if any counter metric is declining while North Star improves
```

### 4.3 North Star Review Cadence

| Review Type | Frequency | Participants | Output |
|---|---|---|---|
| **Weekly check** | Weekly | PM + Data | Is the metric moving? Any anomalies? |
| **Monthly review** | Monthly | PM leads + Engineering lead | Root cause of movement; input metric analysis |
| **Quarterly deep dive** | Quarterly | Full leadership | Is this still the right North Star? Are inputs correctly identified? |
| **Annual reset** | Annually | CPO + Product leads | Formally reconfirm or change the North Star |

---

## North Star Metrics for AI Products

### The AI Value Measurement Challenge

Traditional engagement metrics (DAU, session length, clicks) were designed for products where more engagement = more value. AI products invert this — the best AI experience may have zero clicks and zero engagement if the AI completes the task perfectly on the first try.

| Traditional Metric | Why It Fails for AI | Better AI Alternative |
|---|---|---|
| Daily active users | AI that works well reduces return visits | Unique users who achieve their goal per week |
| Session length | Excellent AI is fast — long sessions signal failure | Goal achievement rate per session |
| Page views | AI reduces navigation — fewer views = better AI | Task completion rate |
| Feature engagement | AI replaces feature clicks with direct outcomes | Outcomes achieved via AI vs manually |

### AI-Appropriate North Star Candidates

| Product Type | North Star Candidate | Rationale |
|---|---|---|
| **AI writing assistant** | Users who publish AI-assisted content weekly | Publishing = outcome achieved; weekly = habit formed |
| **AI data analyst** | Insights acted upon per user per week | Action = value delivered; not just "insights viewed" |
| **AI customer support** | Issues resolved without human escalation per day | Resolution = value; human escalation = AI failure |
| **AI coding assistant** | PRs merged with AI assistance per developer per week | Merged code = outcome; per developer = scales correctly |
| **AI research tool** | Research tasks completed to user satisfaction per week | Satisfaction qualifier prevents gaming |
| **AI scheduling** | Meetings scheduled autonomously per user per week | Autonomy = AI doing the job; manual scheduling = AI not working |

### The AI Delegation Metric

For agentic AI products, the ultimate North Star is delegation depth — how much of the task the user trusts the AI to complete without intervention:

```
AI DELEGATION NORTH STAR

Definition: % of initiated AI tasks where the user accepts the AI output without modification

Measurement:
  Numerator: Tasks where output was used as-is (no edit, no regeneration, no manual completion)
  Denominator: All AI tasks initiated

Segmentation:
  By task type (some tasks warrant more user review than others)
  By user AI literacy (new users will edit more — this is expected)
  By output confidence (high-confidence outputs should be accepted more)

Target: > 60% acceptance rate for mature AI features in established users
Concern: < 30% acceptance rate (users are doing more work than AI is saving)
```

---

## Templates

### Template A: North Star Definition Document

```
# North Star Definition — [Product / Feature Name]
Date: ___  |  Owner: ___  |  Next review: ___

## North Star Metric
Name: _______________________________________________
Definition: _______________________________________________
Unit: [users / tasks / sessions / outcomes] per [day / week / month]
Measurement: _______________________________________________

## Why This Metric
Value indicator: _______________________________________________
Retention correlation: Group A (above threshold): ___% / Group B (below): ___%
Revenue correlation: _______________________________________________
Gaming resistance: _______________________________________________

## Current Value
Current: _______________________________________________
Target (90 days): _______________________________________________
Target (12 months): _______________________________________________

## Metric Tree
L1 inputs: _______________________________________________
Counter metrics: _______________________________________________

## What We Explicitly Rejected
[List the other metrics considered and why they were rejected]

## Instrumentation Status
[ ] Event tracked  [ ] User-level  [ ] Segmentable  [ ] Historical data available
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Multiple "North Stars" — one per team | One North Star for the product; team-level metrics below it |
| Using revenue as the North Star | Revenue is a lagging output — use the leading user behaviour that generates revenue |
| Using engagement metrics for AI products | AI success often reduces engagement — use outcome and delegation metrics |
| Choosing a North Star that can be gamed | Run the gaming test before finalising |
| North Star that is not correlated with retention | Validate correlation before committing |
| North Star defined by leadership without user research | North Star must reflect a behaviour that users themselves recognise as valuable |
| Never reviewing whether the North Star is still correct | Annual review minimum — products evolve, the right metric evolves too |
| Metric tree disconnected from North Star | Every L1 metric must have a statistically validated relationship to the North Star |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| North Star dashboard review | Weekly | Ongoing — every sprint |
| L1 input metric root cause analysis | Monthly | Any significant movement in North Star |
| North Star correlation re-validation | Quarterly | Retention and revenue analysis |
| Counter metric check | Monthly | Alongside North Star review |
| North Star definition review | Annually | Or when product fundamentally changes |
| Metric tree refresh | Annually | Or when new features significantly change the product |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Identify the Right North Star Metric

> **Best for:** Defining the North Star for a new product, a major new feature, or when the current North Star has stopped being meaningful.

```
You are a product strategy expert helping me identify the right North Star metric for my product.

Guide me through the full North Star identification process:

1. Generate candidates across four categories:
   - Breadth metrics (how many users get value?)
   - Depth metrics (how much value per user?)
   - Efficiency metrics (how fast do users get value?)
   - Outcome metrics (what real-world result does the user achieve?)
   Generate 2–3 strong candidates per category.

2. Score each candidate against the five North Star criteria:
   - Value indicator (1–3)
   - Leading indicator (1–3)
   - Team-influenceable (1–3)
   - Measurable (1–3)
   - Understandable (1–3)
   Total max = 15. Eliminate candidates below 12.

3. Gaming test: for each surviving candidate, describe how it could be gamed without delivering real value.

4. Recommend the strongest North Star with:
   - A precise definition (numerator / denominator / time window)
   - Why it is resistant to gaming
   - What user behaviour it represents
   - What retention/revenue correlation you would expect

5. Recommend the 3–5 L1 input metrics that most directly drive this North Star.

My product: [describe what it does]
Target user: [who uses it and what they are trying to accomplish]
Current metrics tracked: [list what you already measure]
Stage: [early / growth / scale]
Is this an AI product: [yes/no — if yes, describe the AI component]
```

---

### Prompt 2 — Validate a North Star with Correlation Analysis

> **Best for:** After selecting a candidate North Star — confirming it actually correlates with retention and revenue.

```
You are a data analyst helping me validate a North Star metric candidate through correlation analysis.

Design the complete validation study:

1. Correlation test design
   - Write the correlation hypothesis: "Users who [North Star behaviour] at [threshold] will retain at [rate]"
   - Define the user segmentation: how to split users into "above threshold" and "below threshold" groups
   - Define the dependent variables: 7-day retention, 30-day retention, 90-day retention, revenue

2. Analysis methodology
   - What data do I need to run this analysis?
   - What statistical method should I use to measure correlation?
   - What sample size do I need for statistical significance?
   - How do I control for confounders (e.g. power users might both hit the North Star AND retain better for other reasons)?

3. Result interpretation
   - At what correlation strength is this a strong North Star? (retention delta > X%)
   - At what strength is it weak but usable?
   - At what strength should I reject it and look for a different metric?

4. Cohort validation
   - How do I validate that the correlation is consistent across monthly cohorts?
   - What does it mean if the correlation is strong in one cohort but weak in another?

5. Gaming resistance validation
   - Design a test that checks whether the metric can be improved without improving retention

My North Star candidate: [define the metric precisely]
My product: [describe]
Data available: [what events and user data do I currently have?]
User base size: [total users available for analysis]
```

---

### Prompt 3 — Build a Metric Tree

> **Best for:** Decomposing the North Star into its input metrics to create a complete framework the team can use for prioritisation.

```
You are a product analytics expert helping me build a complete metric tree for my product.

Build the metric tree from North Star to team-level metrics:

1. North Star decomposition
   - Identify whether the North Star decomposes multiplicatively, additively, or as a funnel
   - Write the mathematical relationship between the North Star and its L1 inputs

2. L1 input metrics (3–5)
   For each L1 metric:
   - Define it precisely (numerator / denominator / time window)
   - Explain the causal mechanism: how does improving this metric improve the North Star?
   - Identify which team or squad owns this metric
   - Set a current baseline and target

3. L2 input metrics (2–4 per L1)
   For each L2 metric:
   - Define it precisely
   - Explain how it drives the L1 metric above it
   - Identify the specific product surface or feature it is most sensitive to

4. Counter metrics
   For each L1 metric, identify one counter metric that must not decline if the L1 improves.

5. Team metric alignment
   - Map each team or squad to the L1 and L2 metrics they are responsible for
   - Identify any metrics that have no clear owner (a gap)
   - Identify any teams that have overlapping metric ownership (a conflict)

My North Star: [define precisely]
My product areas / squads: [list the teams and what they own]
Current metrics tracked: [what is already measured?]
Product stage: [early / growth / scale]
```

---

### Prompt 4 — Design an AI Product North Star

> **Best for:** AI products specifically — where traditional engagement metrics fail to capture the value of AI delegation and task completion.

```
You are an AI product metrics specialist helping me define the right North Star for an AI-powered product.

Traditional engagement metrics fail for AI products. Help me find a North Star that captures genuine AI value delivery.

1. Diagnose why traditional metrics fail for my product
   - Which traditional metrics am I currently tracking?
   - How could each one decline as AI gets better at its job? (Less engagement = better AI)
   - Which ones am I at risk of optimising in the wrong direction?

2. AI value dimensions to consider
   Evaluate each for my specific product:
   - Task completion rate: did the AI finish the job?
   - Output acceptance rate: did the user use the AI output without modification?
   - Goal achievement rate: did the user achieve their underlying goal?
   - Delegation depth: how much of the task did the user trust the AI to handle?
   - Time saved: did the AI reduce the time to task completion?
   - Quality improvement: did the AI improve the quality of the user's output?

3. Recommended North Star
   For my specific AI product, recommend the North Star that:
   - Captures genuine AI value (not just activity)
   - Is difficult to game
   - Correlates with the user achieving their underlying job
   - Reduces to zero if the AI stops working

4. AI-specific counter metrics
   Recommend counter metrics that prevent gaming the AI North Star.

5. Measurement design
   Write the precise event specification for tracking this North Star in my analytics system.

My AI product: [describe what the AI does]
User's underlying job: [what is the user ultimately trying to accomplish?]
Current metrics: [what am I measuring today?]
AI interaction pattern: [how do users interact with the AI — chat / embedded / autonomous / other]
```

---

### Prompt 5 — Run a North Star Quarterly Review

> **Best for:** Quarterly review to assess whether the North Star is still the right metric and whether the metric tree inputs are correctly identified.

```
You are a product analytics advisor helping me run a quarterly North Star review.

Guide me through a structured quarterly review of our North Star framework:

1. North Star health check
   - Is the North Star still correlating with retention? (run the correlation test with last quarter's cohort)
   - Has the metric been gamed? (look for unusual patterns that improve the metric without improving retention)
   - Is the team still aligned on what the North Star means?

2. Input metric accuracy
   - For each L1 input metric: is there evidence that it actually drives the North Star?
   - Has any L1 metric become disconnected from the North Star (correlation weakened)?
   - Are there new input metrics that emerged from last quarter's product changes?

3. North Star movement analysis
   - Did the North Star improve, decline, or stay flat last quarter?
   - Which L1 input drove the most movement?
   - What product changes are most correlated with North Star improvement?

4. Metric tree gaps
   - Are there teams optimising for metrics not in the tree? (creates misalignment)
   - Are there L2 metrics that have no clear path to the L1 above them?

5. North Star evolution question
   - Has the product changed enough that the North Star should change?
   - Is there a new user behaviour that better captures value delivery than the current North Star?

My current North Star: [define]
Last quarter's performance: [North Star value + trend]
Input metric performance: [list L1 metrics and their Q-o-Q changes]
Major product changes last quarter: [describe]
```

