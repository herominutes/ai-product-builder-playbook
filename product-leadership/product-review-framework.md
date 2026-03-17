# 🔍 Product Review Framework — AI Product Builder Playbook

> **A framework for running effective product reviews that drive alignment, surface risks early, and continuously improve product and team performance**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Review Architecture](#the-review-architecture)
- [Review Type 1: Sprint Review](#review-type-1-sprint-review)
- [Review Type 2: Monthly Product Review](#review-type-2-monthly-product-review)
- [Review Type 3: Quarterly Business Review](#review-type-3-quarterly-business-review)
- [Review Type 4: Feature Post-Mortem](#review-type-4-feature-post-mortem)
- [Review Type 5: AI Quality Review](#review-type-5-ai-quality-review)
- [Running High-Quality Reviews](#running-high-quality-reviews)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Reviews are the feedback loops that keep a product team calibrated to reality. Without reviews, teams drift — from the strategy, from user needs, from quality standards, from each other. With well-designed reviews, teams catch problems while they are still small, make better decisions because they have better information, and improve continuously rather than episodically.

> **Core Principle:** A review that produces no decision, no action, and no learning is not a review — it is a status meeting. Every review must produce at least one of three things: a decision made, an action assigned, or a learning documented. If none of these are produced, the review should be redesigned or cancelled.

For AI products, reviews require an additional layer. The standard product review cycle — sprint, monthly, quarterly — does not provide enough visibility into AI-specific risks: quality drift, hallucination rates, trust erosion, and cost trajectories. An AI product team that only runs standard reviews will discover AI problems through user complaints rather than proactive monitoring.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Reviews are happening but not producing decisions or actions | 🔴 Critical — redesign the review |
| AI quality issues are being discovered by users, not the team | 🔴 Critical — AI quality review is missing |
| Stakeholders are misaligned despite regular reviews | 🟠 High — review content or audience is wrong |
| Team is not learning from past performance | 🟠 High — review learning loop is broken |
| Setting up a new product team's review cadence | 🟡 Medium |
| Annual review of the review process itself | 🟡 Medium |

---

## The Review Architecture

A complete product review system has five review types, each operating at a different cadence and serving a different purpose.

```
SPRINT REVIEW (every 2 weeks)
  ↓ what was built; does it meet the standard?
MONTHLY PRODUCT REVIEW (monthly)
  ↓ is the product performing? what is being learned?
QUARTERLY BUSINESS REVIEW (quarterly)
  ↓ is the strategy working? are we investing in the right things?
FEATURE POST-MORTEM (after significant launches)
  ↓ what happened after launch? what do we now know?
AI QUALITY REVIEW (weekly for AI products)
  ↓ is the AI performing safely and within quality standards?
```

| Review Type | Cadence | Duration | Primary Output |
|---|---|---|---|
| **Sprint review** | Every 2 weeks | 45 min | Acceptance decision + demo |
| **Monthly product** | Monthly | 60–90 min | Performance insights + priorities |
| **Quarterly business** | Quarterly | 2–3 hours | Strategic decisions + investments |
| **Feature post-mortem** | After major launches | 60–90 min | Learning document + actions |
| **AI quality review** | Weekly | 30 min | Quality status + actions |

---

## Review Type 1: Sprint Review

### 1.1 Purpose and Principles

The sprint review is not a demo — it is an acceptance gate. The PM's role is to evaluate each delivered item against the agreed acceptance criteria and either accept it (done) or return it (not done). This distinction matters: a sprint review that always accepts everything provides no quality signal.

### 1.2 Sprint Review Format

```
SPRINT REVIEW FORMAT (45 minutes)

Preparation (before the review):
  Engineering has deployed all items to staging
  PM has reviewed acceptance criteria for each item
  Demo script is prepared for each item

Opening (5 minutes):
  Sprint goal reminder: what was this sprint trying to accomplish?
  Sprint commitment recap: what did the team commit to?

Demo and acceptance (30 minutes):
  For each item (5–7 minutes per item):
    Engineer demonstrates the feature, including edge cases
    PM evaluates against acceptance criteria
    PM decision: Accept / Accept with minor conditions / Return
    If returned: specific feedback on what is not meeting criteria

AI-specific demo additions:
    Show AI success case (happy path)
    Show AI failure case (what happens when the AI fails)
    Show the monitoring dashboard (confirm monitoring is active)
    Confirm: prompt is version-controlled; evaluation passed

Metrics check (5 minutes):
    Are any metrics from last sprint's shipped items available?
    Any early signal on adoption or quality?

Closing (5 minutes):
    Sprint goal achieved: Yes / Partially / No
    Items returned: ___ — will be pulled into next sprint
    One learning from this sprint
```

### 1.3 Acceptance Criteria Standards

```
ACCEPTANCE CRITERIA STANDARDS

Every backlog item must have specific, testable acceptance criteria.

Good acceptance criteria format:
  "Given [context], when [user action], then [expected outcome]"

For AI items, add:
  "Given [input], when [AI processes it], then [output meets quality threshold]"
  "Given [failure input], when [AI fails], then [user sees designed failure state]"
  "Given [adversarial input], when [AI receives it], then [guardrail activates correctly]"

PM acceptance decision:
  Accept: All acceptance criteria met. Item is done.
  Accept with conditions: Criteria mostly met; conditions documented; tracked to next sprint.
  Return: One or more criteria not met. Item goes back to engineering with specific feedback.

Standard: A PM who never returns items is not reviewing against criteria — they are managing relationships.
```

---

## Review Type 2: Monthly Product Review

### 2.1 Purpose

The monthly product review connects product performance to strategic intent. It answers: is what we shipped working? What are we learning? What should we change?

### 2.2 Monthly Review Format

```
MONTHLY PRODUCT REVIEW FORMAT (60–90 minutes)

Attendees: PM leads + Engineering lead + Design lead + CPO
Pre-read: Metrics dashboard distributed 48 hours before

Opening (5 minutes):
  The question for this month: [what is the most important question we are answering today?]

Metrics review (20 minutes):
  North Star: current vs target, trend
  L1 input metrics: each one vs target, traffic light
  AI-specific metrics (if AI product): quality score, adoption rate, acceptance rate
  Discussion: what do these numbers tell us? What are we learning?

Shipped features performance (15 minutes):
  For each significant feature shipped this month:
    What was the expected outcome?
    What is the actual outcome (with data)?
    What is the one-sentence learning?
  Pattern: is there a theme across the features that underperformed?

Risk and flag review (15 minutes):
  What risks are the PM leads tracking?
  Any risks that have materialised or escalated since last month?
  Any items that need CPO decision or awareness?

Next month priorities (15 minutes):
  What are the 2–3 most important things for next month?
  Are there any priority changes based on this month's learning?
  Any resource or dependency issues to resolve?

Closing (5 minutes):
  Decisions made this month: ___
  Actions assigned: ___
  One learning from this month: ___
```

### 2.3 Monthly Review Pre-Read Template

```
MONTHLY PRODUCT REVIEW PRE-READ

Month: ___  |  Author: ___  |  Distributed: 48 hours before review

PERFORMANCE SUMMARY
North Star: ___ (Target: ___ / Change: +/-___%)
Status: 🟢 On track / 🟡 Watch / 🔴 Behind

KEY METRICS
| Metric | Current | Target | vs Last Month | Status |
|--------|---------|--------|--------------|--------|
| | | | | |

WHAT WE SHIPPED
| Feature | Expected Outcome | Actual Result | Learning |
|---------|-----------------|--------------|---------|
| | | | |

AI QUALITY (if applicable)
AI quality score: ___  |  Acceptance rate: ___%  |  Any incidents: ___

RISKS AND FLAGS
1. _______________________________________________
2. _______________________________________________

DECISIONS NEEDED FROM THIS REVIEW
1. _______________________________________________
2. _______________________________________________
```

---

## Review Type 3: Quarterly Business Review

### 3.1 Purpose

The quarterly business review (QBR) answers the biggest questions: Is our strategy working? Are we investing in the right things? What do we need to change for next quarter?

### 3.2 QBR Format

```
QUARTERLY BUSINESS REVIEW FORMAT (2–3 hours)

Attendees: CPO + PM leads + Engineering leads + Design lead + Finance + Executive stakeholders

Pre-work (1 week before):
  PM leads prepare performance narratives (not just data)
  Finance prepares spend vs budget analysis
  CPO prepares strategic context update

Opening (15 minutes):
  Strategic context: what has changed in the market, competitive landscape, or user needs?
  The central question for this QBR: _______________________________________________

Performance review (45 minutes):
  North Star trajectory: is the trend positive, flat, or declining?
  OKR grades: for each objective, grade (0.0–1.0) with honest narrative
  What worked this quarter — specific features, decisions, or investments
  What did not work — honest accounting with root cause
  AI performance summary: quality, trust, adoption, cost trajectory

Strategic review (30 minutes):
  Is the current strategy still correct?
  Are there signals from this quarter that should change strategic direction?
  What assumptions did we make last quarter that proved wrong?

Investment review (30 minutes):
  What did we spend and what did we get for it?
  What is the highest-ROI investment category (people / AI infrastructure / features / research)?
  What should we stop, start, or continue in terms of investment?

Next quarter planning inputs (30 minutes):
  What are the top 3 outcomes we need to achieve next quarter?
  What are the resource implications?
  What are the biggest risks for next quarter?

Decision making (15 minutes):
  Named decisions made in this QBR
  Actions assigned with owners and deadlines

Closing (15 minutes):
  The single most important thing we learned this quarter
  The single most important thing we need to do differently next quarter
```

---

## Review Type 4: Feature Post-Mortem

### 4.1 Purpose

The feature post-mortem happens 30–60 days after a significant launch. Its purpose is to extract maximum learning from the gap between what we expected and what actually happened.

### 4.2 Post-Mortem Format

```
FEATURE POST-MORTEM FORMAT (60–90 minutes)

Attendees: PM + Engineering lead + Design lead + Data analyst
Timing: 30–60 days post-launch (enough data to be meaningful)

Pre-work: PM prepares the post-mortem document with quantitative data

Opening (5 minutes):
  What was the feature?
  What did we expect to happen?
  What actually happened?

Metric review (20 minutes):
  Primary metric: expected ___ / actual ___
  Secondary metrics: [review each]
  AI-specific (if applicable): quality, acceptance rate, trust indicators
  Segment breakdown: did it perform differently for different users?

The honest narrative (20 minutes):
  What went better than expected and why?
  What went worse than expected and why?
  What surprised us (positive and negative)?
  What do we know now that we wish we had known at launch?

Decision retrospective (15 minutes):
  Which decisions made during development proved correct?
  Which decisions proved incorrect?
  What would have led to a better decision?

Learning synthesis (15 minutes):
  The 3 most important learnings from this launch
  Which learnings apply to other features currently in development?
  What changes to our process would have produced a better outcome?

Action items (5 minutes):
  Specific changes to make based on this post-mortem
  Owner and deadline for each
```

### 4.3 Post-Mortem Document Template

```
FEATURE POST-MORTEM

Feature: _______________________________________________
Launch date: ___  |  Post-mortem date: ___  |  Author: ___

SUMMARY (3 sentences)
What we built, what we expected, what happened.

METRICS
| Metric | Expected | Actual at 30 days | Assessment |
|--------|---------|------------------|------------|
| Primary | | | On track / Below / Exceeded |
| AI quality | | | |
| Adoption | | | |
| Retention impact | | | |

WHAT WORKED
1. _______________________________________________

WHAT DIDN'T WORK
1. _______________________________________________

KEY LEARNINGS
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

DECISIONS THAT PROVED WRONG
Decision: ___  |  Better decision would have been: ___

PROCESS IMPROVEMENTS
What we will do differently on the next launch: _______________________________________________

FOLLOW-ON ACTIONS
| Action | Owner | Deadline |
|--------|-------|----------|
| | | |
```

---

## Review Type 5: AI Quality Review

### 5.1 Purpose

The AI quality review is a weekly 30-minute review that keeps AI product quality in front of the team. It is the earliest warning system for quality drift, safety issues, and cost anomalies.

### 5.2 AI Quality Review Format

```
AI QUALITY REVIEW FORMAT (30 minutes — weekly)

Attendees: PM + AI lead (+ Engineering lead if issues)
Timing: Same day and time each week — non-negotiable cadence

QUALITY SCORECARD (15 minutes)
For each production AI feature:
  Quality score this week: ___ / 5
  vs last week: +/- ___
  vs target: 🟢 Above / 🟡 At / 🔴 Below

  Acceptance rate: ___%  |  vs target: ___
  Filter trigger rate: ___%  |  vs expected: ___
  Latency P99: ___ ms  |  vs SLA: ___
  Cost per interaction: $___  |  vs budget: ___

FAILURE MODE ANALYSIS (5 minutes)
  Top failure category this week: _______________________________________________
  Root cause (if known): _______________________________________________
  Action: _______________________________________________

INCIDENTS AND FLAGS (5 minutes)
  Any confirmed user-reported quality issues: ___
  Any safety filter triggers requiring investigation: ___
  Any cost anomalies: ___

ACTIONS (5 minutes)
  Action 1: ___  |  Owner: ___  |  Due: ___
  Action 2: ___  |  Owner: ___  |  Due: ___
  Escalation needed: Yes / No — if yes, to whom: ___
```

---

## Running High-Quality Reviews

### 6.1 Review Facilitation Standards

```
REVIEW FACILITATION STANDARDS

Before the review:
[ ] Pre-read distributed 48 hours before
[ ] Data prepared and validated — no surprises from wrong numbers
[ ] Agenda sent with specific time allocations
[ ] Decisions needed are explicitly named in the agenda

During the review:
[ ] Start on time — late starts signal that preparation is insufficient
[ ] Facilitator keeps time ruthlessly — discussion without a decision is not review time
[ ] All data shared is honest — no smoothing of bad news
[ ] Decisions are named explicitly: "The decision we are making is: ___"
[ ] Action items are named: specific action, named owner, named deadline

After the review:
[ ] Written summary distributed within 2 hours
[ ] Action items added to tracking system
[ ] Decisions added to decision log
[ ] Pre-read for next review templated from this review's outputs
```

### 6.2 Signs of a High-Quality Review

| Signal | What It Indicates |
|---|---|
| Pre-read is read before the meeting | Participants are prepared; time is used for discussion, not information transfer |
| Bad news is shared directly | Psychological safety; reviews are honest |
| Decisions are made, not deferred | Reviews produce clarity, not more ambiguity |
| Actions have specific owners | Accountability is real, not diffused |
| Next review starts with action item follow-up | Continuity; reviews build on each other |
| The review ends on time | Discipline; preparation was adequate |

---

## Templates

### Template A: Review Calendar

```
# Product Review Calendar — [Team Name]

Weekly:
  AI Quality Review — [Day, Time] — PM + AI lead — 30 min

Bi-weekly:
  Sprint Review — [Day, Time] — Full squad — 45 min
  Retrospective — [Day, Time] — Full squad — 45 min

Monthly:
  Monthly Product Review — [Day, Time] — PM leads + CPO — 90 min

Quarterly:
  QBR — [Month, approximate week] — Full leadership — 3 hours
  Feature Post-Mortems — [Week after 30-day marks] — Feature team — 90 min

Annual:
  Annual operating model review — [Month] — CPO + PM leads — Full day
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Sprint review that always accepts everything | Acceptance requires criteria to be met — PMs must return items that fail |
| Monthly review that is only metrics — no decisions | Every review must produce at least one decision or action |
| QBR that does not address what went wrong | Honest accounting of what didn't work is the most valuable part |
| Feature post-mortem only for failures | Post-mortems are for learning — run them on successes too |
| No AI quality review | Weekly AI quality review is required for all AI products |
| Pre-read distributed in the meeting | Pre-reads distributed in the meeting are not pre-reads |
| Actions without named owners | "We should..." is not an action. "[Name] will... by [date]" is an action. |
| Reviews that drift in scope and time | Facilitator enforces time; scope is set in the agenda |

---

## Cadence

| Review | Frequency | Duration | Owner |
|--------|-----------|----------|-------|
| AI Quality Review | Weekly | 30 min | PM |
| Sprint Review | Bi-weekly | 45 min | PM |
| Retrospective | Bi-weekly | 45 min | PM (facilitator) |
| Monthly Product Review | Monthly | 90 min | PM |
| QBR | Quarterly | 3 hours | CPO + PM leads |
| Feature Post-Mortem | 30–60 days post-launch | 90 min | PM |
| Review cadence review | Annually | 60 min | CPO |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Complete Product Review System

> **Best for:** Building the full review architecture for a product team — all five review types with formats, cadences, and outputs.

```
You are a product operations expert helping me design a complete product review system.

Design all five review types for my team:

1. Sprint review — format, acceptance criteria standard, AI-specific additions
2. Monthly product review — format, pre-read template, decisions required
3. Quarterly business review — format, strategic questions, investment review
4. Feature post-mortem — format, timing, learning synthesis approach
5. AI quality review — weekly format, scorecard, escalation triggers

For each review type:
- Write the specific agenda with time allocations
- Write the pre-work required
- Define the output: what decisions, actions, or learnings must result?
- Identify what a successful vs unsuccessful review looks like

After all five types:
- Design the review calendar for my team
- Identify which reviews are currently missing or ineffective
- Write the 60-day plan for implementing the full review system

My team: [size, composition, remote/hybrid]
Current review cadence: [what reviews currently happen]
Current review problems: [what is not working]
Is this an AI product: [yes/no]
Product stage: [early / growth / scale]
```

---

### Prompt 2 — Run a Monthly Product Review

> **Best for:** Preparing for and facilitating a monthly product review that produces real insights and decisions.

```
You are a product review facilitator helping me prepare for and run a monthly product review.

Guide me through the full process:

1. Pre-work preparation (48 hours before)
   - What data must I gather and validate?
   - Write the pre-read document for this specific month
   - What are the 2 decisions I need from this review?

2. Facilitation guide
   - Write the minute-by-minute agenda
   - What questions should I ask at each point to generate insight, not just information sharing?
   - How do I handle discussion that drifts from the agenda?
   - How do I make decisions rather than ending with "we'll think about it"?

3. Honest narrative
   - Help me write the honest narrative for [feature/metric that underperformed]
   - How do I present bad news in a way that is credible and solution-oriented?

4. Post-review
   - Write the post-review summary template
   - How do I ensure action items are completed?

My metrics for this month:
[Paste your current performance data]

Key decisions needed:
[Describe what you need to decide]

Review audience:
[Who will be in the room — CPO / investors / team leads]
```

---

### Prompt 3 — Write a Feature Post-Mortem

> **Best for:** After a significant launch — extracting maximum learning from the gap between expectations and reality.

```
You are a product learning strategist helping me write a feature post-mortem.

Using the data I provide, write a complete post-mortem document:

1. Summary (3 sentences)
   - What we built, what we expected, what happened

2. Honest metrics analysis
   - Which metrics exceeded expectations and why?
   - Which metrics missed and why?
   - What does the segment breakdown reveal?

3. Learning synthesis
   - What are the 3 most important learnings from this launch?
   - Which learnings should change something currently in development?
   - What would we do differently if starting over?

4. Decision retrospective
   - Which product decisions proved correct?
   - Which proved incorrect?
   - What evidence, if we had sought it, would have led to a better decision?

5. Process improvements
   - What in our development or launch process would have produced a better outcome?
   - Write the specific process change with implementation plan

6. Action items
   - Based on the post-mortem: what specific actions should we take?

Feature context: [describe what was built and what the goals were]
Expected outcomes: [what did you predict?]
Actual outcomes: [what happened — metrics at 30 days]
Key surprises: [positive and negative]
Decisions made during development: [any you now think were wrong]
```

---

### Prompt 4 — Design and Run an AI Quality Review

> **Best for:** Setting up the weekly AI quality review and running it effectively with the PM and AI lead.

```
You are an AI quality specialist helping me design and run my weekly AI quality review.

Design the complete AI quality review system:

1. Review format
   - What should be covered in 30 minutes?
   - Write the specific agenda with time allocations
   - What is the minimum data required to run a meaningful review?

2. Quality scorecard
   - What metrics should appear on the scorecard?
   - What are the traffic light thresholds (green / amber / red) for each metric?
   - How do I calculate a composite AI quality score?

3. Failure mode analysis
   - How do I identify the top failure category each week?
   - How do I diagnose the root cause in 5 minutes?
   - What action types are available to improve each failure mode?

4. Escalation criteria
   - When does a quality issue escalate from PM to CPO?
   - When does it escalate from CPO to CEO?
   - What triggers an emergency response vs a standard fix?

5. Trend analysis
   - How do I distinguish normal variation from meaningful quality drift?
   - What week-over-week change should concern me?
   - How do I detect gradual drift before it becomes a significant problem?

After the design:
- Run a simulated review with the data I provide and produce the review output
- Identify the 2 most important actions for the next week

My AI features: [describe]
Current quality data: [paste quality scores, filter rates, cost, latency]
Known issues: [any existing quality concerns]
```

---

### Prompt 5 — Prepare for a Quarterly Business Review

> **Best for:** Preparing the QBR presentation — honest, strategic, and designed to produce decisions.

```
You are a product leadership advisor helping me prepare for a quarterly business review.

Help me prepare across five areas:

1. Performance narrative
   - Write the honest 3-paragraph narrative on this quarter's performance
   - How do I acknowledge what didn't work without undermining confidence in the team?
   - What is the single most important insight from this quarter's data?

2. OKR grades
   - For each OKR I share, help me write the honest grade with narrative
   - How do I distinguish "we fell short but learned something" from "this OKR was wrong"?
   - What pattern emerges across the grades?

3. Strategic questions
   - Based on this quarter's performance, what strategic questions must the leadership team answer?
   - Is the current strategy working, or do the data suggest a shift is needed?
   - What assumptions have been proved wrong this quarter?

4. Investment review
   - How do I present the return on our AI infrastructure investment?
   - Which investment category produced the most value?
   - Where did we over-invest relative to outcomes?

5. Next quarter positioning
   - What are the 3 most important outcomes for next quarter?
   - How do I connect this quarter's learnings to next quarter's plan?
   - What are the 2 biggest risks for next quarter and how do I plan for them?

My quarter's data:
[Paste key metrics, OKR grades, AI quality summary, investment summary]

Audience for the QBR:
[Who will be in the room — investors / board / exec team]

Key decisions needed from this QBR:
[What must be decided in the room]
```
