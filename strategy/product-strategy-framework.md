# 🧭 Product Strategy Framework — AI Product Builder Playbook

> **A structured approach for defining product direction and aligning every product decision with long-term outcomes**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Product Strategy Stack](#the-product-strategy-stack)
- [Layer 1: Product Vision](#layer-1-product-vision)
- [Layer 2: Strategic Pillars](#layer-2-strategic-pillars)
- [Layer 3: Product Initiatives](#layer-3-product-initiatives)
- [Layer 4: Roadmap Alignment](#layer-4-roadmap-alignment)
- [Layer 5: Execution](#layer-5-execution)
- [Strategy Evaluation](#strategy-evaluation)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Product strategy answers one fundamental question:

> **Where should the product go, why does it matter, and how will we know we are winning?**

Strategy is not a roadmap. It is not a list of features. It is the **decision-making framework** that tells your team what to build, what to deprioritise, and how to make tradeoffs when resources are constrained — which they always are.

> **Core Principle:** A strategy that cannot help you say no is not a strategy. It is a wish list.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting a new product or rebuilding from scratch | 🔴 Critical — before any roadmap work |
| Team is building features without clear direction | 🔴 Critical — realign immediately |
| Preparing for annual or quarterly planning | 🟠 High |
| Entering a new market or launching a new line | 🟠 High |
| Significant change in competitive landscape or technology | 🟠 High |
| Onboarding a new CPO, GM, or exec stakeholder | 🟡 Medium |
| Post-launch retrospective on a major initiative | 🟡 Medium |

---

## The Product Strategy Stack

Strategy is not a single document. It is a layered system where each level translates the one above it into more specific, actionable form:

```
VISION
  ↓ defines the destination
STRATEGIC PILLARS
  ↓ define the areas of investment
PRODUCT INITIATIVES
  ↓ define the bets we are placing
ROADMAP
  ↓ defines the sequence and timing
EXECUTION
  ↓ defines the sprint-level work
```

| Layer | What It Answers | Owner | Cadence |
|---|---|---|---|
| **Vision** | Where are we going and why? | CPO / Founder | Annually |
| **Strategic Pillars** | What are our core areas of investment? | CPO + Leadership | Annually |
| **Initiatives** | What specific bets will we place? | PM Lead | Quarterly |
| **Roadmap** | When and in what sequence? | PM | Quarterly |
| **Execution** | What are we building this sprint? | PM + Engineering | Weekly |

> **Rule of thumb:** If a sprint ticket cannot be traced back to an initiative, which connects to a pillar, which serves the vision — it should not be in the sprint.

---

## Layer 1: Product Vision

### 1.1 What Vision Does

Vision is the anchor that prevents strategy drift. When priorities conflict, when resources are cut, when a competitor launches — the vision is the tiebreaker. Without it, strategy becomes reactive.

| Strong Vision | Weak Vision |
|---|---|
| Specific to a user and a transformation | Generic and applicable to any company |
| Makes clear what you are NOT doing | Infinitely expandable |
| Inspires tradeoff decisions | Creates no useful constraints |
| Time-bound and testable | Aspirational with no success criteria |

### 1.2 Vision Statement Formula

```
Vision Statement Template

For [specific user persona]
Who currently [struggle with / cannot / spend too much time on X]
[Product name] enables [core transformation]
By providing [unique capability or approach]
Unlike [current alternative]
We [key differentiator]
```

### 1.3 Vision Diagnostic

Before proceeding to pillars, validate your vision:

```
VISION DIAGNOSTIC CHECKLIST

[ ] Can every team member restate the vision in one sentence?
[ ] Does the vision describe a user outcome — not a product feature?
[ ] Does the vision create useful constraints? (Can you say no to things?)
[ ] Is the vision differentiated from your closest competitor?
[ ] Does the vision survive a 3-year horizon without becoming obsolete?
```

---

## Layer 2: Strategic Pillars

### 2.1 What Pillars Are

Strategic pillars are the **long-term areas of investment** the product must sustain to achieve its vision. They are not themes. They are not values. They are the categories of work that, if compounded over time, will close the gap between today and the vision.

> **Core Principle:** Most products need 3–5 pillars. Fewer than 3 suggests insufficient thinking. More than 5 means everything is a priority — which means nothing is.

### 2.2 Common Pillar Categories

| Pillar Type | Description | Example |
|---|---|---|
| **User Acquisition** | Growing the addressable user base | New channel, new persona, new geography |
| **Activation** | Getting users to experience core value faster | Onboarding redesign, time-to-value reduction |
| **Engagement & Retention** | Deepening habit and reducing churn | Notification systems, power user features |
| **Monetisation** | Converting value delivered into revenue | Pricing model, upsell paths, enterprise tier |
| **Platform & Ecosystem** | Enabling third-party value creation | API, developer tools, marketplace |
| **AI Capabilities** | Embedding intelligence into core workflows | Model integration, personalisation, automation |
| **Trust & Safety** | Building the reliability layer users depend on | Guardrails, explainability, data privacy |

### 2.3 Pillar Definition Template

```
## Strategic Pillar: [Pillar Name]

Why this matters:
[1–2 sentences connecting this pillar to the vision]

What success looks like in 12 months:
[Specific, measurable outcome]

What we will invest in:
- [Initiative type 1]
- [Initiative type 2]
- [Initiative type 3]

What we will NOT invest in (within this pillar):
- [Explicit exclusion]

Owner: _______________
North Star Metric: _______________
```

---

## Layer 3: Product Initiatives

### 3.1 What Initiatives Are

Initiatives are the **specific, time-bound bets** the product team is placing within each pillar. An initiative is larger than a feature but smaller than a pillar. A well-written initiative has a clear hypothesis, a measurable outcome, and an explicit owner.

### 3.2 Initiative Scoring

Before committing to an initiative, score it:

| Dimension | Score 1 | Score 2 | Score 3 |
|---|---|---|---|
| **Strategic fit** | Tangentially related to a pillar | Supports a pillar | Core to a pillar |
| **User impact** | Nice to have | Meaningful improvement | Solves a critical pain |
| **Market timing** | No urgency | Some urgency | Time-sensitive window |
| **Confidence** | Low — mostly assumptions | Medium — some evidence | High — validated |
| **Effort** | XL | L–M | S |

**Priority Score = (Strategic Fit + User Impact + Market Timing + Confidence) / Effort**

> **Threshold:** Initiatives scoring below 2.0 should be deferred or deprioritised.

### 3.3 Initiative Definition Template

```
## Initiative: [Name]

Strategic Pillar: _______________
Hypothesis: If we [build / change / launch X], then [user outcome], 
            because [reason grounded in evidence].

User problem being solved:
_______________________________________________

Evidence this problem is real:
- [Data point 1]
- [User research finding]
- [Support ticket volume / NPS driver]

Success metric: _______________
Target: _______________  |  Timeline: _______________
Owner: _______________   |  Priority Score: _______________

Key dependencies:
- [ ] [Dependency 1]
- [ ] [Dependency 2]
```

---

## Layer 4: Roadmap Alignment

### 4.1 Strategy-to-Roadmap Translation

A roadmap is not a list of features with dates. It is a **sequenced, prioritised view of initiatives** that reflects strategic choices about timing and tradeoffs.

| Roadmap Anti-Pattern | Strategic Alternative |
|---|---|
| Features listed without pillar connection | Every item tagged to a pillar and initiative |
| Dates committed without confidence levels | Confidence tiers: Now / Next / Later |
| Stakeholder requests added ad hoc | All requests evaluated against initiative criteria |
| Roadmap never changes | Reviewed and updated every quarter |
| One roadmap for all audiences | Executive view / team view / customer view |

### 4.2 Roadmap Prioritisation Matrix

Before sequencing, map each initiative:

```
                    HIGH STRATEGIC IMPORTANCE
                              |
        High Impact + High Importance  |  Low Impact + High Importance
             [DO FIRST]               |       [Reconsider scope]
                              |
HIGH USER IMPACT -------------+------------- LOW USER IMPACT
                              |
        High Impact + Low Importance   |  Low Impact + Low Importance
          [Challenge the strategy]     |          [DROP]
                              |
                    LOW STRATEGIC IMPORTANCE
```

> **Action:** Any initiative in the bottom-right quadrant should be removed from the roadmap without ceremony.

### 4.3 Roadmap Confidence Tiers

| Tier | Horizon | Specificity | Commitment Level |
|---|---|---|---|
| **Now** | Current quarter | Sprint-level detail | High — committed |
| **Next** | Following quarter | Initiative-level | Medium — directional |
| **Later** | 6–12 months | Pillar-level | Low — subject to change |

---

## Layer 5: Execution

### 5.1 Strategy-to-Sprint Check

Every sprint planning session should include a 5-minute strategy check:

```
SPRINT STRATEGY CHECK

For each item entering the sprint:

[ ] Which initiative does this serve?
[ ] Which strategic pillar does that initiative belong to?
[ ] Is this the highest-leverage thing we could build right now?
[ ] If we had to cut one item, is this the last one we would cut?

If any item fails the first two checks, remove it from the sprint.
```

### 5.2 Execution Health Signals

| Signal | Healthy | Warning |
|---|---|---|
| Strategy awareness | Team can name all pillars | Team is unaware of pillars |
| Ticket traceability | 90%+ tickets link to an initiative | Less than 60% do |
| Roadmap drift | Roadmap changes quarterly | Roadmap changes weekly |
| Stakeholder requests | Evaluated against strategy | Accepted on seniority |
| Retrospective focus | Outcomes reviewed vs. strategy | Only velocity reviewed |

---

## Strategy Evaluation

Run this evaluation quarterly, and any time the team loses alignment:

| Evaluation Question | Strong Answer | Weak Answer |
|---|---|---|
| Does this solve a meaningful user problem? | Yes, with evidence | We believe it does |
| Does this strengthen competitive position? | Creates durable advantage | Matches what competitors have |
| Does this create long-term value? | Compounds over time | One-time lift |
| Can the team make tradeoffs using this strategy? | Yes — we say no regularly | Everything feels like a priority |
| Does the roadmap reflect the strategy? | 90%+ items trace to pillars | Many items are stakeholder-driven |

---

## Templates

### Template A: Full Strategy Document

```
# [Product Name] — Product Strategy
Date: ___  |  Author: ___  |  Version: ___  |  Horizon: ___

## Product Vision
[One paragraph: user, problem, transformation, differentiator]

## Strategic Context
Market opportunity: _______________
Key tailwind: _______________
Key risk: _______________

## Strategic Pillars
1. [Pillar Name] — [One sentence description]
2. [Pillar Name] — [One sentence description]
3. [Pillar Name] — [One sentence description]

## Key Initiatives (this quarter)
| Initiative | Pillar | Score | Owner | Target |
|------------|--------|-------|-------|--------|
|            |        |       |       |        |
|            |        |       |       |        |

## Strategic Metrics
| Metric | Current | Target | Timeline |
|--------|---------|--------|----------|
|        |         |        |          |

## What We Are Not Doing
- [Explicit exclusion 1]
- [Explicit exclusion 2]
- [Explicit exclusion 3]

## Success Criteria (12 months)
[What must be true for this strategy to be considered successful?]
```

### Template B: Strategy One-Pager (for exec alignment)

```
# [Product Name] Strategy — One Page
Date: ___  |  Owner: ___

## The Bet
We believe [market insight]. Therefore we will [strategic choice].
This will produce [outcome] by [date].

## Pillars
1. _______________
2. _______________
3. _______________

## This Quarter's Initiatives
1. [Initiative] → [Metric target]
2. [Initiative] → [Metric target]
3. [Initiative] → [Metric target]

## What We Are Not Doing
_______________________________________________

## How We Know It's Working
North Star: _______________  |  Target: _______________
```

### Template C: Quarterly Strategy Review

```
# Strategy Review — Q[X] [Year]

## What we said we would do
[Summary of last quarter's initiatives]

## What we actually did
[Honest account of output]

## Did it work?
| Initiative | Target | Actual | Verdict |
|------------|--------|--------|---------|
|            |        |        | ✅ / ⚠️ / ❌ |

## What we learned
[Top 3 insights that should update the strategy]

## Strategy updates for next quarter
[What changes, what stays the same, and why]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Strategy as a slide deck no one reads | Strategy as a living doc updated every quarter |
| Roadmap built before strategy is set | Lock the pillars before a single roadmap item is placed |
| Pillars that are vague aspirations | Pillars with specific metrics and explicit owners |
| Strategy set by the most senior person in the room | Strategy built from user evidence, stress-tested by skeptics |
| No explicit "what we are not doing" | Every strategy document includes an exclusion list |
| Initiatives added without scoring | Every initiative scored before it enters the roadmap |
| Strategy reviewed once a year | Quarterly review minimum; emergency review on major signals |

---

## Cadence

| Review Type | Frequency | Trigger |
|---|---|---|
| Sprint strategy check | Every sprint | Ticket enters planning |
| Initiative review | Monthly | Progress against targets |
| Roadmap refresh | Quarterly | Planning cycle |
| Full strategy review | Annually | Vision and pillar reset |
| Emergency reset | As needed | Competitive shift, pivot, or major misalignment |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Full Product Strategy from Scratch

> **Best for:** Starting a new product, kicking off annual planning, or rebuilding strategy after a significant market or team shift.

```
You are an expert product strategist helping me build a complete, structured product strategy using the five-layer Product Strategy Stack.

Work through each layer with me one at a time. After I provide input for each layer, sharpen my answers — replace vague language with specific claims, flag anything that sounds like a wish list rather than a strategy, and confirm before moving to the next layer.

The five layers are:
1. Vision — where we are going and why it matters (user, transformation, differentiator)
2. Strategic Pillars — the 3–5 core areas of investment that will get us there
3. Product Initiatives — the specific, time-bound bets we are placing this quarter
4. Roadmap Alignment — how we sequence those initiatives and at what confidence level
5. Execution — how we ensure sprint work traces back to strategy

Apply these rules throughout:
- Every pillar must have a specific metric and owner, not just a name
- Every initiative must have a hypothesis, evidence of the problem, and a success metric
- The strategy must include an explicit "what we are not doing" list
- If I suggest more than 5 pillars, push back and help me consolidate

My product: [describe in 2–3 sentences]
My target user: [who they are and what they do]
Current stage: [early / growth / scale / enterprise]
Biggest strategic challenge right now: [describe in 1–2 sentences]
```

---

### Prompt 2 — Define and Score Product Initiatives

> **Best for:** Quarterly planning where you need to evaluate a backlog of potential initiatives and decide what to build next.

```
You are a product strategy advisor helping me evaluate and prioritise a set of product initiatives.

For each initiative I give you, score it across five dimensions using a 1–3 scale:
1. Strategic fit — how directly does it serve a declared strategic pillar?
2. User impact — how meaningfully does it improve the user's outcome?
3. Market timing — is there urgency or a window of opportunity?
4. Confidence — how much evidence supports the hypothesis?
5. Effort — inverse score (S=3, M=2, L=1, XL=0.5)

Calculate a Priority Score: (Strategic Fit + User Impact + Market Timing + Confidence) / Effort

Then rank all initiatives by score and give me:
- Top tier: build now (score ≥ 3.0)
- Middle tier: schedule next quarter (score 2.0–2.9)
- Defer or drop (score < 2.0)

For any initiative scoring below 2.0, tell me what would need to change to make it worth prioritising.

My strategic pillars are:
1. [Pillar 1]
2. [Pillar 2]
3. [Pillar 3]

My initiatives to evaluate:
1. [Initiative name — brief description]
2. [Initiative name — brief description]
3. [Initiative name — brief description]
```

---

### Prompt 3 — Stress-Test an Existing Strategy

> **Best for:** Before presenting strategy to a board, new exec, or cross-functional team — find the gaps before someone else does.

```
You are a skeptical but constructive product strategy advisor. Your job is to stress-test my product strategy and identify where it is weak, incomplete, or unconvincing.

Evaluate my strategy against these six questions:
1. Can the team use this strategy to say no to something? (If not, it is not a strategy.)
2. Does every initiative connect to a declared pillar?
3. Does every pillar have a specific, measurable success metric?
4. Is there a clear "what we are not doing" list?
5. Are the initiatives sequenced based on evidence — or based on opinions and stakeholder pressure?
6. Would a new team member understand the strategy without needing to ask questions?

For each question, give a verdict: ✅ Strong / ⚠️ Needs work / ❌ Missing

Then give me the top 3 specific improvements I should make before presenting this strategy.

My strategy:
[paste your strategy document or summary here]
```

---

### Prompt 4 — Run a Quarterly Strategy Review

> **Best for:** End-of-quarter retrospective to assess what the strategy delivered, what it missed, and what needs to change.

```
You are a product strategy advisor helping me run a structured quarterly strategy review.

I will give you our declared initiatives from last quarter, what we actually shipped, and the metrics. Your job is to:

1. Assess each initiative: did we deliver it, and did it move the metric we expected?
2. Identify the gap between what we planned and what we executed — and diagnose why
3. Surface 2–3 strategic learnings that should update our thinking going into next quarter
4. Recommend specific changes to our pillars or initiative prioritisation based on what we learned
5. Flag any pillar that shows no initiative progress — this is a resource or commitment problem

Format the output as a clean review document I can share with leadership.

Last quarter's declared initiatives:
1. [Initiative — target metric — result]
2. [Initiative — target metric — result]
3. [Initiative — target metric — result]

What we actually shipped: [brief description]

Current strategic pillars: [list them]
Biggest surprise this quarter: [describe]
```

---

### Prompt 5 — Generate the "What We Are Not Doing" List

> **Best for:** Any time your strategy document lacks clear boundaries — the single most common gap in product strategy.

```
You are a product strategy advisor helping me define the explicit boundaries of our product strategy.

A strong strategy must say no to things. Help me generate a clear, specific "What We Are Not Doing" list based on my product, my pillars, and my vision.

For each exclusion you suggest, explain:
- Why this is tempting (why a team might want to do it)
- Why excluding it is the right strategic call given my direction

Generate 6–8 specific exclusions. Make them concrete — not "we will not build features outside our core" but "we will not build a native mobile app in the next 12 months because our web product has not yet reached the retention threshold that would justify the investment."

My product: [describe]
My strategic pillars: [list them]
My vision: [one sentence]
Stage: [early / growth / scale]
Biggest distraction we keep getting pulled toward: [describe]
```
