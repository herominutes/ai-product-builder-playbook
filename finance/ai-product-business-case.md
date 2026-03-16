# 📊 AI Product Business Case — AI Product Builder Playbook

> **A framework for building, presenting, and defending a financial business case for AI product investment**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Business Case Structure](#the-business-case-structure)
- [Section 1: The Investment Ask](#section-1-the-investment-ask)
- [Section 2: The Problem and Opportunity](#section-2-the-problem-and-opportunity)
- [Section 3: The Proposed Solution](#section-3-the-proposed-solution)
- [Section 4: Financial Model](#section-4-financial-model)
- [Section 5: Risk and Sensitivity Analysis](#section-5-risk-and-sensitivity-analysis)
- [Section 6: The Recommendation](#section-6-the-recommendation)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Most product business cases fail not because the idea is bad — but because the financial narrative is weak. A CFO reading a product business case is asking four questions:

> 1. **How much do you need?** — and is the ask specific or vague?
> 2. **What will I get back?** — and how long will it take?
> 3. **What could go wrong?** — and have you thought it through?
> 4. **Why should I believe you?** — what assumptions are you making?

> **Core Principle:** A business case is not a pitch deck. It is a financial argument with evidence. Every number must have a source. Every assumption must be stated. Every risk must have a mitigation.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Requesting budget for a new AI product or feature | 🔴 Critical — CFO will not approve without it |
| Justifying headcount for an AI product team | 🔴 Critical |
| Evaluating a build vs buy vs partner decision | 🟠 High |
| Seeking board approval for a strategic AI initiative | 🟠 High |
| Responding to a CFO challenge on AI spend | 🟠 High |
| Quarterly review of ongoing AI investment | 🟡 Medium |
| Post-launch review — did the case hold? | 🟡 Medium — close the loop |

---

## The Business Case Structure

A strong AI product business case has six sections. Each section answers one of the CFO's core questions:

```
THE INVESTMENT ASK
  ↓ how much, for how long, for what?
THE PROBLEM AND OPPORTUNITY
  ↓ why does this matter and what is at stake?
THE PROPOSED SOLUTION
  ↓ what exactly are we building?
FINANCIAL MODEL
  ↓ what does the return look like?
RISK AND SENSITIVITY ANALYSIS
  ↓ what could go wrong and how bad is it?
THE RECOMMENDATION
  ↓ what should we do and why?
```

| Section | CFO Question Answered | Key Output |
|---|---|---|
| **Investment ask** | How much do you need? | Total investment, timeline, team |
| **Problem and opportunity** | Why does this matter? | Market size, user pain, urgency |
| **Proposed solution** | What are we building? | Scope, approach, milestones |
| **Financial model** | What do I get back? | ROI, payback period, NPV |
| **Risk analysis** | What could go wrong? | Scenarios, sensitivities, mitigations |
| **Recommendation** | What should we do? | Decision, conditions, next steps |

---

## Section 1: The Investment Ask

### 1.1 Investment Summary

Lead with the number. CFOs do not want to read five pages to find out what you are asking for.

```
INVESTMENT SUMMARY

Total investment requested:              $_______________
Investment period:                       ___ months
Recurring monthly cost post-build:       $_______________

Breakdown:
  Engineering (FTE × months × day rate): $_______________
  AI / model costs (build + ongoing):    $_______________
  Infrastructure:                        $_______________
  Third-party tools and licences:        $_______________
  Contingency (recommended: 15–20%):     $_______________

Headcount required:
  New hires:                             _______________
  Existing team reallocation:            _______________
```

### 1.2 Investment Phasing

Break the investment into phases. CFOs prefer staged commitment — it reduces risk and improves accountability.

| Phase | Duration | Investment | Milestone | Go/No-Go Decision |
|---|---|---|---|---|
| **Phase 1 — Validate** | 4–6 weeks | $___ | Prototype tested with users | ✓ |
| **Phase 2 — Build** | 8–12 weeks | $___ | MVP shipped to pilot group | ✓ |
| **Phase 3 — Scale** | Ongoing | $___/month | Full rollout | ✓ |

> **Rule of thumb:** Never ask for full investment upfront. A phased ask with clear go/no-go gates signals financial discipline and reduces the perceived risk of the approval.

---

## Section 2: The Problem and Opportunity

### 2.1 The Problem Statement

State the problem in financial terms — not just user terms. A CFO responds to cost, revenue, and risk.

| Problem Framing | User Terms | Financial Terms |
|---|---|---|
| **Weak** | Users struggle to find information quickly | — |
| **Strong** | Users spend 4.5 hours/week on manual research | $18K/user/year in lost productivity at average salary |

### 2.2 Market Opportunity Sizing

```
MARKET OPPORTUNITY

Total Addressable Market (TAM):         $_______________
Serviceable Addressable Market (SAM):   $_______________
Realistic capture in 24 months (SOM):   $_______________

Current revenue from this segment:      $_______________
Revenue left uncaptured:                $_______________

Evidence this opportunity is real:
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
```

### 2.3 Cost of Inaction

This is the section most product people skip — and it is the most persuasive section for a CFO.

```
COST OF INACTION

If we do not build this:

Revenue at risk (competitive displacement):   $_______________/year
Retention cost (expected churn without it):   $_______________/year
Opportunity cost (market share not captured): $_______________/year
Competitive risk:                             [describe]

Total annual cost of doing nothing:           $_______________
```

---

## Section 3: The Proposed Solution

### 3.1 Solution Summary

Keep this tight. One paragraph on what you are building, one paragraph on how it works, one paragraph on what is explicitly out of scope.

```
SOLUTION SUMMARY

What we are building:
_______________________________________________

How it works (non-technical):
_______________________________________________

What is explicitly out of scope:
_______________________________________________

Why this approach vs alternatives:
_______________________________________________
```

### 3.2 Milestone Plan

| Milestone | Target Date | Success Criteria | Investment to Date |
|---|---|---|---|
| Prototype complete | ___ | ___ | $___ |
| Pilot launch (n=___users) | ___ | ___ | $___ |
| Full launch | ___ | ___ | $___ |
| Break-even | ___ | ___ | $___ |

---

## Section 4: Financial Model

### 4.1 Revenue Model

```
REVENUE PROJECTION

Revenue driver: [new users / ARPU increase / churn reduction / cost saving]

Year 1:
  New users / units attributable to this investment: _______________
  ARPU:                                              $_______________
  Revenue contribution:                              $_______________
  AI + infrastructure cost:                          $_______________
  Gross profit contribution:                         $_______________

Year 2:
  New users / units:                                 _______________
  Revenue contribution:                              $_______________
  Cost (at optimised run rate):                      $_______________
  Gross profit contribution:                         $_______________

Year 3:
  New users / units:                                 _______________
  Revenue contribution:                              $_______________
  Cost:                                              $_______________
  Gross profit contribution:                         $_______________
```

### 4.2 Return on Investment

```
ROI SUMMARY

Total investment (all phases):          $_______________
Total gross profit (3 years):           $_______________

ROI = (Gross Profit - Investment) ÷ Investment × 100
    = ____%

Payback period:                         ___ months

Net Present Value (at ___% discount rate):
  Year 1 cash flow (discounted):        $_______________
  Year 2 cash flow (discounted):        $_______________
  Year 3 cash flow (discounted):        $_______________
  NPV:                                  $_______________

Internal Rate of Return (IRR):          ___%
```

### 4.3 Key Assumptions

State every assumption explicitly. A CFO will find them — better to declare them yourself.

```
KEY ASSUMPTIONS

| Assumption | Value Used | Basis | Sensitivity |
|------------|------------|-------|-------------|
| ARPU | $___ | Current average | High |
| User acquisition rate | ___ /month | Last 6-month trend | Medium |
| AI cost per user | $___ | Current model pricing | High |
| Churn rate | ___% | Current baseline | Medium |
| Conversion rate | ___% | Historical average | High |
| Model pricing stability | ___% change/year | Industry trend | Low |
```

---

## Section 5: Risk and Sensitivity Analysis

### 5.1 Risk Register

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Model cost increases significantly | Medium | High | Lock in volume pricing; evaluate fine-tuning at $25K/month |
| User adoption below projection | Medium | High | Pilot with 50 users before full launch; gate scale on activation |
| Quality below user expectations | Low | High | Define quality benchmark before build; test with 100 inferences |
| Competitor ships equivalent feature | Medium | Medium | 6-month head start; accelerate Phase 1 |
| Engineering cost overrun | Medium | Medium | 20% contingency built into ask; weekly burn tracking |

### 5.2 Scenario Analysis

Run three scenarios. Show the CFO you have stress-tested the model:

```
SCENARIO ANALYSIS

                        Optimistic    Base Case    Conservative    Stress Test
─────────────────────────────────────────────────────────────────────────────
ARPU assumption         +20%          Plan          -15%           -25%
User growth             +30%          Plan          -20%           -35%
AI cost per user        -10%          Plan          +20%           +40%
─────────────────────────────────────────────────────────────────────────────
Year 1 revenue          $___          $___          $___           $___
Year 1 gross profit     $___          $___          $___           $___
Payback period          ___ mo        ___ mo        ___ mo         ___ mo
3-year NPV              $___          $___          $___           $___
ROI                     ___%          ___%          ___%           ___%
─────────────────────────────────────────────────────────────────────────────
Viable?                 Yes           Yes           Yes            Review
```

> **Decision rule:** If the conservative scenario still shows a payback period under 18 months and a positive NPV, the investment is financially robust. If the stress test shows negative NPV, identify the single assumption driving it and address that risk specifically.

### 5.3 Breakeven Sensitivity

Show which variables have the most leverage on break-even:

```
SENSITIVITY: WHAT MOVES BREAK-EVEN THE MOST?

Variable              Change        Break-even impact
──────────────────────────────────────────────────────
ARPU                  -20%          + ___ months
User acquisition      -30%          + ___ months
AI cost per user      +25%          + ___ months
Conversion rate       -20%          + ___ months
Engineering overrun   +25%          + ___ months

Highest-risk variable: _______________
Mitigation plan: _______________
```

---

## Section 6: The Recommendation

### 6.1 The Decision

State your recommendation in one sentence. Then give three supporting reasons, each with a number attached.

```
RECOMMENDATION

We recommend [Proceed / Proceed with conditions / Do not proceed] with
[investment name] at a total investment of $[amount] over [timeline].

Three reasons:
1. [Financial reason with a number — e.g. "3-year NPV of $X at base case"]
2. [Strategic reason with evidence — e.g. "Addresses the #1 churn driver cited by 38% of churned users"]
3. [Risk reason — e.g. "Conservative scenario still delivers payback within 14 months"]

Conditions (if any):
[ ] [Condition 1 — e.g. "Proceed to Phase 2 only if Phase 1 pilot achieves X% activation"]
[ ] [Condition 2]

Decision needed by: _______________
If delayed beyond this date: [consequence — e.g. "miss Q3 launch window; competitive risk increases"]
```

### 6.2 The Ask

Close with the specific decision you need:

```
THE ASK

We are requesting approval to:
[ ] Proceed with Phase 1 investment of $_______________
[ ] Authorise headcount: ___ new hires / ___ reallocation
[ ] Approve ongoing monthly budget of $_______________ post-launch

Next step if approved: _______________  |  By: _______________
Review checkpoint: _______________      |  Reporting to: _______________
```

---

## Templates

### Template A: Executive One-Page Summary

```
# AI Investment Summary: [Project Name]
Date: ___  |  Author: ___  |  Presented to: ___

## The Ask
$[total] over [timeline] to build [what].
Ongoing cost post-launch: $[monthly].

## The Opportunity
[One sentence: user problem + market size + urgency]
Cost of inaction: $[annual] in [revenue at risk / churn / opportunity cost].

## The Return
Payback period: ___ months (base case)
3-year ROI: ___%
3-year NPV: $___

## The Risk
Biggest risk: [describe] — Mitigation: [describe]
Conservative scenario payback: ___ months

## The Decision
Recommended action: [Proceed / Phase 1 only / Conditions]
Decision needed by: _______________
```

### Template B: Monthly Investment Tracking

```
# AI Investment Tracker: [Project Name] — [Month Year]

## Spend to Date
Budgeted to date:    $_______________
Actual to date:      $_______________
Variance:            $_______________  (__%)

## Key Metrics vs Business Case
| Metric | Business Case Target | Actual | Variance |
|--------|---------------------|--------|----------|
| Users  |                     |        |          |
| ARPU   |                     |        |          |
| AI cost/user |              |        |          |
| Gross margin |              |        |          |

## Forecast to Break-Even
Original break-even: Month ___
Revised break-even:  Month ___
Change:              +/- ___ months

## Risks Materialised
[ ] None  [ ] [Describe risk and response]

## Recommendation
[ ] Continue as planned
[ ] Adjust [specific parameter]
[ ] Escalate — business case assumptions no longer hold
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Asking for the full investment upfront | Phase the ask with go/no-go gates at each milestone |
| Presenting only the optimistic scenario | Always present base, conservative, and stress test |
| Hiding assumptions in footnotes | State every assumption explicitly in the body of the case |
| Using revenue projections without a source | Every number needs a basis — historical data, comparable, or stated assumption |
| Ignoring the cost of inaction | Calculate what happens if you do nothing — CFOs respond to risk framing |
| Presenting NPV without a discount rate | Always state the discount rate and justify it |
| No tracking mechanism post-approval | Build a monthly tracker before the case is approved |
| Burying the ask in the appendix | Lead with the number — page one, section one |

---

## Cadence

| Review Type | Frequency | Trigger |
|---|---|---|
| Investment tracker update | Monthly | Post-approval |
| Assumption review | Quarterly | Significant metric deviation |
| Scenario reforecast | Quarterly | Market or cost change |
| Full business case review | At each phase gate | Before Phase 2 and Phase 3 approval |
| Post-investment review | 6 months post-launch | Did the case hold? What did we learn? |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Full Business Case

> **Best for:** Preparing a business case for CFO or board approval of an AI product investment.

```
You are a product finance advisor helping me build a rigorous business case for an AI product investment.

Structure the business case across six sections:
1. Investment ask — total amount, phasing, and headcount
2. Problem and opportunity — user pain in financial terms and cost of inaction
3. Proposed solution — what we are building and what is out of scope
4. Financial model — revenue projection, ROI, payback period, and NPV
5. Risk and sensitivity analysis — three scenarios and a risk register
6. Recommendation — one-sentence decision with three supporting reasons

Rules:
- Every revenue projection must be built from assumptions I explicitly state
- Calculate NPV using the discount rate I provide
- Always include a conservative scenario and a stress test — not just the base case
- Flag any number I give you that seems inconsistent with the others
- The recommendation section must state a specific dollar amount, a payback period, and a decision deadline

After completing all six sections, write a one-page executive summary I can use as a cover page.

My inputs:
What I am building: [describe the AI feature or product]
Total engineering estimate: $[number]
AI/model cost estimate (monthly): $[number]
ARPU (current): $[number]
Expected new users in Year 1: [number]
Discount rate for NPV: [%]
Biggest risk I am worried about: [describe]
```

---

### Prompt 2 — Calculate ROI and Payback Period

> **Best for:** Quickly validating whether an AI investment makes financial sense before building a full business case.

```
You are a financial analyst. Help me calculate the ROI and payback period for an AI product investment.

Build a simple three-year financial model with these outputs:
1. Total investment (upfront + ongoing over 3 years)
2. Annual gross profit contribution (revenue - AI cost - infrastructure)
3. Cumulative gross profit by year
4. Payback period (month when cumulative profit exceeds total investment)
5. 3-year ROI: (Total gross profit - Total investment) ÷ Total investment
6. NPV at the discount rate I provide

Then run two additional scenarios:
- Conservative: ARPU -20%, AI cost +25%, user growth -20%
- Stress test: ARPU -30%, AI cost +40%, user growth -35%

Show me the payback period and ROI for all three scenarios in a comparison table.

Tell me: at what ARPU or user growth rate does this investment stop making financial sense?

My inputs:
Total upfront investment: $[number]
Ongoing monthly AI + infrastructure cost: $[number]
ARPU (monthly per user): $[number]
New users attributable to this investment per month: [number]
Discount rate: [%]
```

---

### Prompt 3 — Write the Cost of Inaction Section

> **Best for:** The most commonly missed section in a product business case — quantifying what it costs to do nothing.

```
You are a product finance advisor. Help me quantify and articulate the cost of inaction for an AI product decision.

For each cost category below, help me estimate the annual financial impact of NOT building this product:

1. Revenue at risk — what revenue could we lose to competitors who build this?
2. Retention cost — what churn is likely if we do not ship this?
3. Opportunity cost — what market share will we fail to capture?
4. Productivity cost — what internal inefficiency continues without this?
5. Competitive risk — what is the strategic cost of falling behind?

For each category:
- Give me a formula to estimate the number
- Ask me the one data point I need to calculate it
- Produce a dollar estimate
- Rate my confidence in that estimate: High / Medium / Low

At the end, write a two-paragraph "cost of inaction" narrative I can include in my business case — written in plain language that a CFO would find credible.

My situation:
What I am considering NOT building: [describe]
Current ARR: $[number]
Current churn rate: [%]
Number of users affected by this problem: [number]
Closest competitor who might build this: [describe]
```

---

### Prompt 4 — Stress-Test a Business Case

> **Best for:** Before presenting to a CFO or board — find the weaknesses in your financial model before they do.

```
You are a skeptical CFO reviewing a product investment business case. Your job is to identify every weak assumption, missing number, and unconvincing claim — before this goes to the board.

Review my business case against these eight CFO questions:
1. Is the investment ask specific, phased, and bounded?
2. Are the revenue projections built from stated assumptions — or are they aspirational?
3. Is there a conservative scenario, not just a base case?
4. Is the cost of inaction quantified — or just described?
5. Are AI-specific costs (inference, model, infrastructure) modelled explicitly?
6. Is the payback period realistic given the acquisition assumptions?
7. Are the risks specific and mitigated — or generic and vague?
8. Is there a tracking mechanism post-approval?

For each question, give a verdict: ✅ Strong / ⚠️ Needs work / ❌ Missing

Then give me the top 3 specific improvements that would make this case materially stronger — with example language I can use.

My business case:
[paste your business case or summary here]
```

---

### Prompt 5 — Build the Sensitivity Analysis

> **Best for:** Adding rigorous scenario modelling to a business case that currently only has a single set of projections.

```
You are a financial modeller helping me build a sensitivity analysis for an AI product business case.

Build a sensitivity table showing how my payback period and 3-year ROI change when I vary the three highest-risk assumptions:

For each assumption, show the impact at:
- -30% from base
- -15% from base
- Base case
- +15% from base
- +30% from base

Then answer:
1. Which single variable has the most impact on payback period?
2. At what value of that variable does the investment stop making financial sense?
3. What is my "margin of safety" — how far can assumptions miss before NPV goes negative?

Format the output as a clean table I can paste directly into a PowerPoint or document.

My base case inputs:
ARPU: $[number]/month
New users per month: [number]
AI cost per user per month: $[number]
Total investment: $[number]
Discount rate: [%]

The three assumptions I want to sensitise:
1. [e.g. ARPU]
2. [e.g. User acquisition rate]
3. [e.g. AI cost per user]
```
