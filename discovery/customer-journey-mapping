# 🗺️ Customer Journey Mapping — AI Product Builder Playbook

> **Framework for mapping end-to-end user experiences in AI-powered products**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The 5-Stage AI Journey Model](#the-5-stage-ai-journey-model)
- [Phase 1: Discovery & Research](#phase-1-discovery--research)
- [Phase 2: Journey Map Construction](#phase-2-journey-map-construction)
- [Phase 3: AI Touchpoint Audit](#phase-3-ai-touchpoint-audit)
- [Phase 4: Opportunity Mapping](#phase-4-opportunity-mapping)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)

---

## Overview

Customer Journey Mapping for AI products differs fundamentally from traditional SaaS. AI introduces **probabilistic outputs**, **model latency**, **hallucination risk**, and **trust calibration** as new dimensions that must be explicitly mapped.

> **Core Principle:** Map the experience, not the feature. Users don't interact with your model — they interact with outcomes, emotions, and trust signals.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Launching a new AI feature or product | 🔴 Critical — before sprint 1 |
| AI outputs generating user complaints | 🔴 Critical — immediate |
| Declining activation or D7 retention | 🟠 High |
| Planning a major model upgrade | 🟠 High |
| Quarterly product review | 🟡 Medium |

---

## The 5-Stage AI Journey Model

AI product journeys have 5 unique stages:

```
AWARE → ACTIVATE → TRUST-BUILD → DELEGATE → ADVOCATE
```

| Stage | User Mindset | AI Risk Zone | Your Job |
|---|---|---|---|
| **Aware** | "What is this?" | Overpromising | Set accurate expectations |
| **Activate** | "Let me try it" | First output quality | Nail the first interaction |
| **Trust-Build** | "Is this reliable?" | Inconsistency, hallucination | Show confidence scores, caveats |
| **Delegate** | "Do this for me" | Autonomy errors, data risk | Tight guardrails + undo flows |
| **Advocate** | "Let me tell others" | Unexplainable magic | Enable sharing, attribution |

---

## Phase 1: Discovery & Research

### 1.1 Stakeholder Alignment Canvas

Run a 30-minute alignment session with PM, Design, Engineering, and Data Science. Fill in together:

```
PRODUCT NAME: _______________________________________________

1. Who is the primary user persona? ________________________
2. What job are they hiring this product to do? _____________
3. What does "success" look like for the user in 5 min? _____
4. What does "success" look like for the user in 30 days? ___
5. What is the single biggest AI-specific risk in this journey?
   ________________________________________________________
6. What data do we have today to map this journey? __________
```

### 1.2 Research Priority Order

1. **Session recordings** (FullStory, Hotjar) — watch 20+ sessions minimum
2. **Support ticket analysis** — tag by journey stage; look for AI failure modes
3. **Activation funnel analysis** — where does drop-off happen post-AI first use?
4. **User interviews** — 8–10 participants, mix of active and churned users
5. **Trust survey** — NPS broken down by journey stage, not overall

### 1.3 Data Collection Checklist

- [ ] Pull activation funnel (Day 1, Day 3, Day 7)
- [ ] Export support tickets tagged to AI features (last 90 days)
- [ ] Pull session replay samples for failed AI interactions
- [ ] Collect qualitative quotes from user interviews
- [ ] Get model metrics from ML team: latency p50/p99, error rate, output quality scores

---

## Phase 2: Journey Map Construction

### 2.1 The AI Product Journey Map Template

```
## Journey Map: [Product Name] — [Persona Name]
Date: ___________  |  Version: ___________  |  Owner: ___________

| Dimension         | Aware | Activate | Trust-Build | Delegate | Advocate |
|-------------------|-------|----------|-------------|----------|----------|
| User Goal         |       |          |             |          |          |
| Actions           |       |          |             |          |          |
| Touchpoints       |       |          |             |          |          |
| Emotion (-2→+2)   |       |          |             |          |          |
| Pain Points       |       |          |             |          |          |
| AI Moments        |       |          |             |          |          |
| Trust Signal      |       |          |             |          |          |
| Opportunity       |       |          |             |          |          |
| Success Metric    |       |          |             |          |          |
```

### 2.2 Emotion Scoring Scale

```
-2  Frustrated / Ready to churn
-1  Confused / Uncertain
 0  Neutral
+1  Satisfied / Curious
+2  Delighted / Advocating
```

**Target:** No journey stage below -1 in steady state.

### 2.3 AI Moments of Truth

For each journey stage, explicitly identify:

| Moment | Pass Condition | Fail Condition |
|---|---|---|
| **First AI Output** | Accurate, fast, well-formatted | Hallucinated, slow, generic |
| **First AI Error** | User can easily correct/override | User is stuck or loses trust permanently |
| **Autonomy Escalation** | User feels safe, can undo | User feels exposed, no recovery path |
| **Explainability Moment** | Clear, honest explanation | Black box, user disengages |

---

## Phase 3: AI Touchpoint Audit

### 3.1 Touchpoint Inventory

```
## AI Touchpoint Inventory

| # | Touchpoint | AI Type | Latency SLA | User Control | Failure Mode |
|---|-----------|---------|-------------|--------------|--------------|
| 1 |           |         |             |              |              |
| 2 |           |         |             |              |              |
```

**AI Type options:** Generation, Classification, Recommendation, Summarization, Extraction, Planning, Search

**User Control options:** Full (user can edit/reject) | Partial (user can flag) | None (fully automated)

### 3.2 Trust & Control Matrix

Map each touchpoint:

```
                    HIGH USER CONTROL
                           |
        High Trust + High Control  |  Low Trust + High Control
        [IDEAL for autonomous AI]  |  [Over-engineered; simplify]
                           |
HIGH TRUST ----------------+---------------- LOW TRUST
                           |
        High Trust + No Control   |  Low Trust + No Control
        [DANGER ZONE — add controls] | [Fine for background AI]
                           |
                    LOW USER CONTROL
```

> **Action:** Any touchpoints in the High Trust + No Control quadrant are immediate sprint priorities.

### 3.3 Latency Impact on Journey

| Latency | User Perception | Journey Response |
|---|---|---|
| < 500ms | Instant | No impact |
| 500ms–2s | Slight pause | Acceptable with skeleton UI |
| 2s–5s | Waiting | Must show progress indicator |
| 5s–10s | Frustration | Consider async + notification |
| > 10s | Abandonment | Redesign the flow |

---

## Phase 4: Opportunity Mapping

### 4.1 Opportunity Scoring Template

```
## Opportunity: [Name]

Journey Stage: _______________
User Pain: _______________
Frequency: Daily / Weekly / Occasionally
Severity: Churns User / Frustrates / Mild
AI Solvability: High / Medium / Low
Effort: S / M / L / XL

Priority Score: (Frequency × Severity) / Effort = ___

Proposed Solution: _______________
Success Metric: _______________
Owner: _______________
```

### 4.2 Opportunity Backlog

```
| Opportunity | Stage | Score | Effort | Solution | Status |
|-------------|-------|-------|--------|----------|--------|
|             |       |       |        |          | 🔵 Backlog |
|             |       |       |        |          | 🟡 In Design |
|             |       |       |        |          | 🟢 In Sprint |
|             |       |       |        |          | ✅ Shipped |
```

---

## Templates

### Template A: Executive Summary (1-pager)

```
# [Product] Customer Journey — Executive Summary
Date: ___  |  Persona: ___  |  Version: ___

## What's Working
- [Top 3 positive moments]

## Critical Gaps
- [Top 3 pain points requiring immediate action]

## AI-Specific Risks
- [Top 2 AI trust/reliability issues]

## Key Metrics
- Activation Rate (D1): ___%
- D7 Retention: ___%
- AI Feature Adoption: ___%
- Trust Score (survey): ___/5

## Top 3 Opportunities (next 90 days)
1. _______________
2. _______________
3. _______________
```

### Template B: Sprint Story Card from Journey Finding

```
## User Story

As a [persona at journey stage]
I want to [action]
So that [outcome / job to be done]

Context from Journey Map: [Quote or finding that motivates this story]

AI Consideration: [How does AI affect this? Latency? Output quality? Trust?]

Acceptance Criteria:
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

Definition of Done:
- [ ] Journey map updated with new touchpoint
- [ ] Trust signal present in UI
- [ ] Error/fallback state designed
- [ ] Metric instrumented
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Mapping the happy path only | Map the "first failure" path explicitly |
| Treating all users the same | Segment by trust level and AI familiarity |
| Ignoring AI latency in the journey | Treat latency as a UX moment, not just an eng metric |
| Building journey maps in decks no one reads | Keep it as a living doc in GitHub, updated each sprint |
| Mapping features instead of emotions | Focus on what the user feels, not what the feature does |
| Skipping the "Delegate" stage | This is where AI products win or lose — always map it |

---

## Cadence

| Review Type | Frequency | Trigger |
|---|---|---|
| Micro-update | Every sprint retro | Any new finding |
| Full refresh | Quarterly | Roadmap planning |
| Emergency refresh | As needed | AI error rate spikes > 5% |

---

*Part of the [AI Product Builder Playbook](../README.md)*
