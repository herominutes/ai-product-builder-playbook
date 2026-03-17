# 🎯 Prioritisation Framework — AI Product Builder Playbook

> **A structured framework for ranking product opportunities, features, and initiatives to maximise impact with available resources**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Prioritisation Model](#the-prioritisation-model)
- [Framework 1: RICE Scoring](#framework-1-rice-scoring)
- [Framework 2: Impact vs Effort Matrix](#framework-2-impact-vs-effort-matrix)
- [Framework 3: Opportunity Scoring](#framework-3-opportunity-scoring)
- [Framework 4: MoSCoW Method](#framework-4-moscow-method)
- [Framework 5: Strategic Pillar Alignment](#framework-5-strategic-pillar-alignment)
- [Prioritisation for AI Products](#prioritisation-for-ai-products)
- [Running a Prioritisation Session](#running-a-prioritisation-session)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Prioritisation is the hardest product management discipline and the most frequently done badly. The difficulty is not analytical — most teams can score a backlog. The difficulty is political. Every stakeholder believes their item is the highest priority. Prioritisation frameworks exist not to replace judgment but to make the judgment transparent, consistent, and defensible.

> **Core Principle:** Prioritisation is an act of saying no. A team that says yes to everything has no priorities — only a list. The purpose of a prioritisation framework is not to rank items from 1 to N. It is to generate clear, evidence-based justification for what will not be done, so the team can focus completely on what will.

For AI products, prioritisation has an additional dimension: AI-specific complexity and uncertainty. An AI feature that scores highly on traditional impact-effort frameworks may score differently once model reliability, data requirements, and evaluation overhead are factored in. This framework integrates AI-specific considerations throughout.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Quarterly planning — ranking initiatives for the next quarter | 🔴 Critical — defines what the team builds |
| Backlog has grown too large to manage | 🔴 Critical — needs a clear cut |
| Stakeholders are competing for the same engineering resources | 🔴 Critical — transparent scoring resolves political conflicts |
| New AI capability has been identified — should it be built now? | 🟠 High |
| Sprint planning — choosing between backlog items | 🟡 Medium |
| Executive asks "why are we building X before Y?" | 🟡 Medium — framework provides the answer |

---

## The Prioritisation Model

No single prioritisation framework is right for every decision. This playbook provides five, each suited to a different type of prioritisation challenge.

```
RICE SCORING
  ↓ quantitative ranking across Reach, Impact, Confidence, Effort
IMPACT vs EFFORT MATRIX
  ↓ visual quadrant for fast sorting of a large backlog
OPPORTUNITY SCORING
  ↓ JTBD-based scoring for user problem prioritisation
MoSCoW METHOD
  ↓ must/should/could/won't for release scoping
STRATEGIC PILLAR ALIGNMENT
  ↓ scoring against declared strategic priorities
```

| Framework | Best For | Time Required | Stakeholder Alignment |
|---|---|---|---|
| **RICE** | Ranking a backlog with mixed item types | 2–4 hours | Good — transparent formula |
| **Impact/Effort** | Fast sort of large backlog (20+ items) | 60–90 min | Good — visual and intuitive |
| **Opportunity scoring** | User problem prioritisation | 3–5 hours | Excellent — user-grounded |
| **MoSCoW** | Release scoping with fixed deadline | 60–90 min | Good — binary decisions |
| **Strategic pillar** | Annual planning and investment allocation | 2–3 hours | Excellent — tied to strategy |

---

## Framework 1: RICE Scoring

### 1.1 RICE Formula

RICE is the most widely used quantitative prioritisation framework. It scores each item on four dimensions and produces a comparable score.

```
RICE SCORE = (Reach × Impact × Confidence) ÷ Effort

Where:
  Reach    = Number of users affected in a given time period (e.g. per quarter)
  Impact   = Estimated impact on the primary metric (1 = minimal, 2 = low, 3 = medium, 4 = high, 5 = massive)
  Confidence = How confident are you in the Reach and Impact estimates? (100% = high, 80% = medium, 50% = low)
  Effort   = Total person-months required (across all roles)
```

### 1.2 RICE Scoring Calibration

```
RICE CALIBRATION GUIDE

Reach (users per quarter):
  Use the number of users who will be directly affected, not total user base.
  Example: A feature for enterprise admins = 500 (not 50,000 total users)

Impact multiplier:
  0.25 = Minimal — barely noticeable improvement
  0.5  = Low — small improvement
  1.0  = Medium — noticeable improvement
  2.0  = High — significant improvement
  3.0  = Massive — fundamental step change

Confidence %:
  100% = You have direct evidence (A/B test, validated research)
  80%  = You have indirect evidence (correlated data, customer interviews)
  50%  = You have an educated guess (logical reasoning, analogies)

Effort (person-months):
  Include: PM time + Design time + Engineering time + QA time
  Be honest — teams consistently underestimate effort by 30–50%
  Apply a 1.3× buffer to initial engineering estimates

RICE score examples:
  High priority: Score > 500
  Medium priority: Score 100–500
  Low priority: Score < 100
```

### 1.3 RICE Scoring Table

```
RICE SCORING TABLE

| Item | Reach | Impact | Confidence | Effort | RICE Score | Priority |
|------|-------|--------|------------|--------|------------|----------|
| [Feature A] | | × | × | ÷ | = | |
| [Feature B] | | × | × | ÷ | = | |
| [Feature C] | | × | × | ÷ | = | |

Sort by RICE score descending.
Items above [threshold] proceed to roadmap.
Items below threshold are deferred with documented rationale.
```

---

## Framework 2: Impact vs Effort Matrix

### 2.1 The 2×2 Matrix

The impact vs effort matrix is the fastest prioritisation tool for large backlogs. It sacrifices precision for speed and visual clarity.

```
                    HIGH IMPACT
                         |
    Quick wins           |        Major projects
    High impact,         |        High impact,
    low effort           |        high effort
    → DO FIRST           |        → PLAN AND RESOURCE
                         |
LOW EFFORT ──────────────+────────────────── HIGH EFFORT
                         |
    Fill-ins             |        Thankless tasks
    Low impact,          |        Low impact,
    low effort           |        high effort
    → DO IF TIME         |        → DO NOT DO
                         |
                    LOW IMPACT
```

### 2.2 Matrix Placement Protocol

```
MATRIX PLACEMENT PROTOCOL

Step 1: Define impact and effort scales before placing any items
  Impact scale: Effect on North Star metric or primary business outcome
  Effort scale: Total team time in weeks (include PM + Design + Engineering)

Step 2: Place items silently first
  Each participant places items independently (prevents anchoring)
  Use sticky notes on a physical or digital board

Step 3: Identify disagreements
  Items with high variance in placement (some high, some low): discuss these first
  Items with consensus: accept placement without discussion

Step 4: Draw the quadrant lines
  Set the midpoint based on your specific backlog context
  Midpoint is not always the centre of the scale — calibrate to your team's capacity

Step 5: Prioritise
  Quick wins: ship this quarter
  Major projects: plan for next quarter with proper resourcing
  Fill-ins: pick up when quick wins are complete
  Thankless tasks: explicitly reject with documented rationale
```

---

## Framework 3: Opportunity Scoring

### 3.1 The Opportunity Score Model

Opportunity scoring is grounded in Jobs to Be Done (JTBD) and rates user problems by their importance and how poorly existing solutions address them.

```
OPPORTUNITY SCORE = Importance + max(Importance - Satisfaction, 0)

Where:
  Importance: How important is it that users can accomplish this outcome? (1–10 scale)
  Satisfaction: How satisfied are users with their current ability to accomplish it? (1–10 scale)

Interpretation:
  Score > 15: Highly underserved opportunity — prioritise immediately
  Score 10–15: Significant opportunity — prioritise in current planning cycle
  Score 7–10: Moderate opportunity — monitor; address when capacity allows
  Score < 7: Not a meaningful opportunity at this time
```

### 3.2 Opportunity Survey Design

```
OPPORTUNITY SURVEY DESIGN

For each desired outcome, ask two questions to all target users (minimum 100 responses):

Question 1: "When [completing the relevant task], how important is it to [desired outcome]?"
  Scale: 1 (Not important) to 10 (Extremely important)

Question 2: "When using [current solution], how satisfied are you with your ability to [desired outcome]?"
  Scale: 1 (Very dissatisfied) to 10 (Very satisfied)

Calculate opportunity score for each outcome.
Rank all outcomes by opportunity score.
Top 5 outcomes with highest scores represent the priority opportunities.

Example outcomes for an AI writing assistant:
  "Produce a first draft in under 5 minutes" — Importance: 8.2, Satisfaction: 3.1, Score: 13.3
  "Ensure the draft matches our brand voice" — Importance: 9.1, Satisfaction: 2.4, Score: 15.8
  "Generate content in multiple languages" — Importance: 5.3, Satisfaction: 6.2, Score: 5.3
```

---

## Framework 4: MoSCoW Method

### 4.1 MoSCoW for Release Scoping

MoSCoW is most useful when prioritising within a fixed time window — a sprint, a release, or a quarter. It forces binary decisions rather than ranking.

| Category | Definition | Decision Rule |
|---|---|---|
| **Must have** | Without this, the release fails or is unusable | Include — no exceptions |
| **Should have** | Important but the release still works without it | Include if capacity allows; cut if needed |
| **Could have** | Nice to have — marginal value | Include only after Must and Should are done |
| **Won't have (this time)** | Explicitly out of scope for this release | Formally reject with documented rationale |

### 4.2 MoSCoW Application Rules

```
MoSCoW CALIBRATION RULES

Rule 1 — Limit Must Haves
If more than 60% of scope is "Must Have", the list is wrong.
Must Have should represent the absolute minimum viable release.

Rule 2 — Be specific about "Won't Have This Time"
"Won't Have" is not a rejection — it is a deferral with a future review date.
Document: why, and when it will be reconsidered.

Rule 3 — Won't Have requires explicit stakeholder agreement
Stakeholders who believe an item is Must Have must be consulted before it is moved to Won't Have.
Agreement in writing prevents "I thought we agreed to include X" disputes.

Rule 4 — Use MoSCoW after RICE or Impact/Effort
MoSCoW works best as the second step — after the ranked list exists,
use MoSCoW to confirm which ranked items make it into the current release.
```

---

## Framework 5: Strategic Pillar Alignment

### 5.1 Pillar Alignment Scoring

Strategic pillar alignment scoring ensures that the prioritised backlog serves the declared strategy — not just the most recent stakeholder request.

```
PILLAR ALIGNMENT SCORING

Step 1: Define your strategic pillars (2–5 max)
  Pillar 1: _______________________________________________
  Pillar 2: _______________________________________________
  Pillar 3: _______________________________________________

Step 2: Score each item against each pillar
  3 = Core to this pillar — directly advances the strategic priority
  2 = Supports this pillar — indirect but meaningful contribution
  1 = Tangential — loosely related
  0 = No alignment — does not serve this pillar

Step 3: Calculate weighted pillar score
  Weighted score = Σ (Pillar score × Pillar weight)
  Assign weights based on strategic priority:
    Primary pillar: 50% weight
    Secondary pillar: 30% weight
    Tertiary pillar: 20% weight

Step 4: Combine with impact/effort
  Final priority = (Pillar alignment score × impact) ÷ effort

Items scoring high on pillar alignment + high on impact + low on effort: prioritise immediately
Items scoring low on pillar alignment: require executive approval before prioritising
```

---

## Prioritisation for AI Products

### 6.1 AI-Specific Prioritisation Dimensions

Standard prioritisation frameworks miss three dimensions that matter specifically for AI features:

| Additional Dimension | Description | How to Score |
|---|---|---|
| **Data readiness** | Is the data required for this AI feature available and clean? | 3 = Ready now / 2 = Needs preparation / 1 = Not available |
| **Model reliability** | Is there a reliable model that can complete this task at the required quality? | 3 = Proven / 2 = Probable / 1 = Uncertain |
| **Evaluation overhead** | How much additional effort does AI evaluation add to the feature? | Subtract evaluation effort from effort score |

### 6.2 AI Feature Prioritisation Scorecard

```
AI FEATURE PRIORITISATION SCORECARD

Standard dimensions:
  Reach: ___  |  Impact: ___  |  Confidence: ___  |  Effort: ___
  RICE Score: ___

AI-specific adjustments:
  Data readiness: 3 / 2 / 1
    If score = 1: Add data preparation time to effort estimate
    If score = 1 and critical: Deprioritise until data is available

  Model reliability: 3 / 2 / 1
    If score = 1: Treat as a research spike, not a delivery commitment
    If score = 2: Add evaluation and iteration buffer to effort estimate

  Evaluation overhead: ___ additional person-weeks
    Add to effort estimate before calculating RICE

Adjusted RICE score with AI dimensions: ___

AI viability verdict:
  High (data ready + model proven): Proceed as planned
  Medium (data needs prep OR model uncertain): Proceed with explicit risk flag
  Low (data unavailable OR model unproven): Defer or treat as research
```

### 6.3 AI vs Non-AI Tradeoff

When prioritising a backlog containing both AI and non-AI items, apply this additional check:

```
AI vs NON-AI TRADEOFF ASSESSMENT

For each AI item in the backlog:
Could the same user outcome be achieved with a non-AI approach?
  Yes, and non-AI is simpler → Prefer non-AI
  Yes, but AI provides meaningfully better quality or scale → Justify AI
  No — only AI can do this → AI is the right approach

Is AI the fastest path to the outcome?
  No — non-AI would ship faster and AI can be added later → Ship non-AI first
  Yes — AI is required from day one → Proceed with AI

AI-first is justified when:
  The outcome is impossible without AI (scale, personalisation)
  OR AI meaningfully changes the quality of the outcome (not just speed)
  OR user trust in the AI feature itself is part of the product value
```

---

## Running a Prioritisation Session

### 7.1 Facilitation Guide

```
PRIORITISATION SESSION AGENDA (2 hours)

Preparation (before session):
  PM pre-populates the scoring table with items and available evidence
  All participants review the items list (no surprises in the session)
  Evidence is available: user research, analytics, market data

00:00 — Alignment on criteria (15 min)
  Confirm: what are we optimising for? (North Star metric or strategic pillar)
  Confirm: what is the time horizon? (This quarter? This half?)
  Confirm: what is the available capacity? (Engineering weeks)

00:15 — Silent scoring (30 min)
  Each participant scores items independently
  No discussion during this phase — prevents anchoring

00:45 — Share and discuss (45 min)
  For items with high consensus: accept without discussion
  For items with high variance: discuss only these
  Focus debate on evidence, not opinion: "what evidence suggests this is higher priority?"

01:30 — Stack rank the top items (15 min)
  Confirm the top 5–10 items in priority order
  Each item gets an explicit champion and a documented rationale

01:45 — Confirm the Won't Do list (15 min)
  Explicitly name items that are not being prioritised
  Assign a review date for each
  Get verbal confirmation from stakeholders whose items were not selected

Output: Documented priority stack with rationale for every item — included and excluded
```

---

## Templates

### Template A: Quarterly Prioritisation Document

```
# Quarterly Prioritisation — Q[X] [Year]
Date: ___  |  PM: ___  |  Capacity: ___ engineering weeks

## Top Priorities (commit)
| Rank | Item | RICE Score | Strategic pillar | Owner | Effort |
|------|------|------------|-----------------|-------|--------|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |

## Secondary Priorities (if capacity allows)
| Item | RICE Score | Condition for inclusion |
|------|------------|------------------------|
| | | |

## Explicitly Deferred
| Item | Reason for deferral | Review date |
|------|--------------------|-----------  |
| | | |

## Stakeholder Decisions Log
| Stakeholder | Item they wanted | Decision | Rationale shared |
|-------------|-----------------|----------|-----------------|
| | | Deferred / Included | |
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Prioritising everything as "high" | Force a ranking — no ties for the top 3 |
| Using one framework for all decisions | Match the framework to the decision type |
| Effort underestimation | Apply 1.3× buffer to all engineering estimates |
| No explicit "Won't Do" list | Every prioritisation session must produce a Won't Do list |
| Stakeholder pressure overriding the framework | Framework provides the justification to say no — use it |
| AI features scored without data readiness | Always score AI features on data readiness and model reliability |
| Prioritising without a time horizon | Always define the time window before scoring |
| Revisiting priorities every sprint | Commit to quarterly priorities; only change with evidence of significantly new information |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Full prioritisation session | Quarterly | PM + stakeholders |
| Backlog grooming | Bi-weekly | PM |
| Priority adjustment (evidence-triggered) | As needed | PM + CPO approval |
| Won't Do list review | Quarterly | PM |
| Stakeholder alignment | Before and after each quarterly prioritisation | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Score and Rank a Product Backlog

> **Best for:** Quarterly planning — applying RICE scoring to a backlog to produce a defensible ranked list.

```
You are a product strategy advisor helping me prioritise my product backlog using RICE scoring.

For each item I describe, assign scores on the four RICE dimensions:
- Reach: how many users are affected per quarter?
- Impact: what is the likely effect on the primary metric? (0.25 / 0.5 / 1 / 2 / 3)
- Confidence: how confident are we in the estimates? (100% / 80% / 50%)
- Effort: total person-months required across PM + Design + Engineering

Calculate the RICE score for each item.

After scoring all items:
1. Rank from highest to lowest RICE score
2. Flag items where my confidence is 50% — these need more research before committing
3. Flag AI items where data readiness or model reliability is uncertain — adjust their effective score
4. Identify the natural cut line given my capacity for this quarter
5. Write the rationale for the top 5 items (why these, why in this order)
6. Write the documented rationale for the bottom 5 items (why not this quarter)

My backlog items:
1. [Item name — describe what it is, who it affects, and what outcome it drives]
2. [Item name — describe]
3. [Item name — describe]
[continue for all items]

Available engineering capacity this quarter: ___ person-months
Primary metric we are optimising for: _______________________________________________
```

---

### Prompt 2 — Run an Impact vs Effort Sort

> **Best for:** Fast sorting of a large backlog (15+ items) when time is limited and a visual output is needed for stakeholder alignment.

```
You are a product prioritisation facilitator helping me sort a large backlog using an impact vs effort matrix.

For each item I describe:
1. Rate impact (1–5): effect on our North Star metric or primary business outcome
2. Rate effort (1–5): total team time, where 5 = very high (months of work)
3. Place in the correct quadrant:
   - Quick win (high impact, low effort) → Do first
   - Major project (high impact, high effort) → Plan and resource
   - Fill-in (low impact, low effort) → Do if time
   - Thankless task (low impact, high effort) → Do not do

After placing all items:
- List the Quick Wins in priority order — these are my immediate actions
- List the Major Projects — these need resource planning and quarterly commitment
- List the Thankless Tasks with a one-line rationale for why they should not be done
- Identify any item I have placed wrong — challenge my placement with evidence

My items:
[paste your backlog items — name + brief description for each]

Context:
North Star metric: _______________________________________________
Available capacity this quarter: _______________________________________________
Known constraints: _______________________________________________
```

---

### Prompt 3 — Facilitate a Prioritisation Session

> **Best for:** Preparing for and facilitating a cross-functional prioritisation session with stakeholders who have competing priorities.

```
You are a product facilitation expert helping me prepare for and run a prioritisation session with my stakeholders.

Design the complete session:

1. Pre-session preparation
   - What materials do I need to prepare before the session?
   - How should I share the items list in advance? (avoid surprises + anchoring)
   - What ground rules should I set at the start of the session?

2. Agenda design
   - Write the minute-by-minute agenda for a 2-hour session
   - Identify the highest-risk moments where conflict might arise and how to handle them

3. Conflict resolution
   - How do I handle a senior stakeholder who insists their item is highest priority?
   - How do I facilitate disagreement on scoring without the session becoming political?
   - What evidence types should I bring to resolve common prioritisation disputes?

4. Won't Do list facilitation
   - How do I get explicit agreement on the Won't Do list?
   - How do I handle stakeholders who refuse to accept their item is deprioritised?

5. Documenting the outcome
   - Write the documentation template for capturing the session's decisions
   - How do I communicate the outcome to stakeholders who were not in the room?

My context:
Stakeholders in the session: [list roles]
Known conflicts: [describe any items where you expect disagreement]
Available capacity: [engineering weeks this quarter]
Items to prioritise: [list or describe]
```

---

### Prompt 4 — Prioritise AI Features Specifically

> **Best for:** A backlog that mixes AI and non-AI items — applying AI-specific dimensions to make the comparison fair.

```
You are an AI product advisor helping me prioritise a backlog that includes both AI and non-AI features.

For each item I describe, apply a hybrid scoring model:

Standard dimensions (apply to all items):
- Reach: users affected per quarter
- Impact: effect on primary metric (0.25 / 0.5 / 1 / 2 / 3)
- Confidence: estimate confidence (100% / 80% / 50%)
- Effort: person-months

AI-specific adjustments (apply to AI items only):
- Data readiness: 3 = ready / 2 = needs prep / 1 = not available
  → If 1: add data preparation weeks to effort
- Model reliability: 3 = proven / 2 = probable / 1 = uncertain
  → If 1: treat as research spike; reduce confidence to 50%
- Evaluation overhead: add testing and evaluation weeks to effort

For each AI item, also answer:
- Could the same outcome be achieved non-AI? (simpler / faster / lower risk)
- Is AI justified? Yes / Prefer non-AI / AI-only

After scoring all items:
- Produce the final ranked list (AI and non-AI together)
- Identify any AI item I should replace with a non-AI approach
- Identify any AI item that needs a research spike before it can be committed to delivery

My backlog:
Non-AI items: [list with descriptions]
AI items: [list with descriptions — include what AI does and what data it needs]

Primary metric: _______________________________________________
Engineering capacity: ___ person-months
```

---

### Prompt 5 — Write Stakeholder-Facing Prioritisation Rationale

> **Best for:** After a prioritisation session — communicating the decisions clearly to stakeholders whose items were not selected.

```
You are a communication strategist helping me write clear, respectful, and persuasive prioritisation rationale for stakeholders.

For each stakeholder situation I describe, write:

1. The decision communication
   - State clearly what was decided and what was not included
   - Use evidence-based language, not opinion language
   - Acknowledge the stakeholder's perspective before explaining the decision

2. The rationale
   - Explain why the included items scored higher — specific, not generic
   - Explain why the deferred item is deferred — not rejected, deferred, with a reason
   - Connect the decision to the declared strategy and North Star metric

3. The next step for deferred items
   - When will this item be reconsidered?
   - What evidence, if available, could change the decision?
   - What could the stakeholder do to strengthen the case for next quarter?

4. The tone
   - Confident but empathetic
   - Data-driven but human
   - Not defensive — this is a good decision, not an apology

Stakeholder situations:
1. [Describe: who, what they wanted, what was decided, their likely reaction]
2. [Describe: who, what they wanted, what was decided, their likely reaction]

Prioritisation context:
What was prioritised this quarter: _______________________________________________
Scoring framework used: _______________________________________________
Primary metric being optimised: _______________________________________________
```
