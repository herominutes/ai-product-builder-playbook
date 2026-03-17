# 🚀 Product Launch Playbook — AI Product Builder Playbook

> **A comprehensive framework for planning, coordinating, and executing successful product launches — from internal readiness to market impact**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Playbook](#when-to-use-this-playbook)
- [The Launch Framework](#the-launch-framework)
- [Phase 1: Launch Planning](#phase-1-launch-planning)
- [Phase 2: Internal Readiness](#phase-2-internal-readiness)
- [Phase 3: Soft Launch](#phase-3-soft-launch)
- [Phase 4: Full Launch](#phase-4-full-launch)
- [Phase 5: Post-Launch](#phase-5-post-launch)
- [AI Product Launch Specifics](#ai-product-launch-specifics)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A product launch is not a date. It is a process that begins weeks or months before the first user sees the feature and continues for weeks after. Teams that treat a launch as a single event — the moment code is deployed — consistently underperform teams that treat it as a phased campaign.

> **Core Principle:** The quality of a launch is determined by the decisions made before users see anything. By the time the feature is live, the opportunity to prevent most failures has already passed. Launch readiness is built in the weeks before, not fixed in the hours after.

For AI products, the launch calculus is more complex. AI features can fail in ways that traditional software cannot: quality can degrade gradually, hallucinations can damage trust before they are detected, and user expectations set by the launch narrative may not match what the AI can actually deliver. A good AI launch is deliberately conservative — shipping to fewer users, with more monitoring, for longer — before expanding.

---

## When to Use This Playbook

| Trigger | Priority |
|---|---|
| Any new feature launch — major or minor | 🔴 Critical — even small launches need a checklist |
| Any AI feature launch | 🔴 Critical — AI launches require additional readiness gates |
| Full product launch or rebrand | 🔴 Critical — full playbook applies |
| Beta or soft launch to a subset of users | 🟠 High — abbreviated playbook |
| Re-launch after a major incident | 🟠 High |
| Feature deprecation (inverse of launch) | 🟡 Medium — communication and migration plan needed |

---

## The Launch Framework

Product launches move through five phases. The depth of each phase scales with the launch size, but no phase should be skipped entirely.

```
LAUNCH PLANNING
  ↓ align on goals, owners, timeline, and success criteria
INTERNAL READINESS
  ↓ team, support, and systems are ready before any user sees it
SOFT LAUNCH
  ↓ validate with a small, controlled audience before full exposure
FULL LAUNCH
  ↓ expand to full audience with monitoring in place
POST-LAUNCH
  ↓ measure, iterate, and close the loop
```

| Phase | Duration | Goal | Gate to Next Phase |
|---|---|---|---|
| **Planning** | 4–6 weeks before launch | Alignment and readiness plan | Plan approved by all owners |
| **Internal readiness** | 2 weeks before launch | All systems and people ready | Pre-launch checklist complete |
| **Soft launch** | 1–2 weeks | Quality validation in production | Quality + safety metrics pass |
| **Full launch** | Launch day + 1 week | Maximum reach with monitoring | No critical issues in 72 hours |
| **Post-launch** | 2–4 weeks | Learn and iterate | 30-day review complete |

---

## Phase 1: Launch Planning

### 1.1 Launch Brief

```
LAUNCH BRIEF

Feature / Product: _______________________________________________
Launch date (target): _______________________________________________
Launch owner (PM): _______________________________________________

LAUNCH GOALS

Primary goal: _______________________________________________
  Success metric: _______________________________________________
  Target at 30 days: _______________________________________________

Secondary goals:
  1. _______________________________________________
  2. _______________________________________________

LAUNCH AUDIENCE

Who is this launch for?
  Internal users only → Internal launch
  Subset of external users → Soft launch / beta
  All users → Full launch
  New user segment → Acquisition-focused launch

Target audience: _______________________________________________
Size: _______________________________________________

LAUNCH NARRATIVE

In one sentence, what is this for the user?
_______________________________________________

What is the user's life better at after this launch?
_______________________________________________

LAUNCH RISK

Primary risk: _______________________________________________
Mitigation: _______________________________________________
Rollback plan: _______________________________________________
```

### 1.2 Launch Team and RACI

```
LAUNCH RACI

| Function | Responsible | Consulted | Informed |
|----------|-------------|-----------|---------|
| Product management | PM owner | CPO | Full product team |
| Engineering | Eng lead | CTO | Full eng team |
| Design | Design lead | | Full design team |
| Marketing / comms | Marketing lead | PM | Sales, CS |
| Customer success | CS lead | PM | CS team |
| Legal / compliance | Legal lead | PM | Exec team |
| Data / analytics | Data lead | PM | PM, eng |

Single decision owner for launch go/no-go: _______________________________________________
```

### 1.3 Launch Timeline

```
LAUNCH TIMELINE

T - 6 weeks: Launch brief approved
T - 5 weeks: Launch team assembled; marketing brief written
T - 4 weeks: Internal launch materials ready
T - 3 weeks: Beta group identified and invited
T - 2 weeks: Internal readiness checklist begins
T - 1 week: Soft launch (internal or beta)
T - 3 days: Final go/no-go review
T - 1 day: Final readiness check; on-call schedule confirmed
T = 0: Launch
T + 1 day: First monitoring review
T + 7 days: First-week retrospective
T + 30 days: 30-day review
```

---

## Phase 2: Internal Readiness

### 2.1 Pre-Launch Checklist

```
PRE-LAUNCH CHECKLIST

PRODUCT READINESS
[ ] Feature is code-complete and deployed to staging
[ ] All acceptance criteria from the PRD are met
[ ] Edge cases and error states are designed and implemented
[ ] Mobile / responsive design validated (if applicable)
[ ] Accessibility baseline met

QUALITY ASSURANCE
[ ] QA testing complete — all critical paths tested
[ ] Performance testing complete — load tested at 2× expected peak
[ ] Regression testing complete — no regressions in existing features
[ ] Browser / device compatibility tested
[ ] Data accuracy validated — analytics events firing correctly

MONITORING AND ALERTING
[ ] Feature flag / rollout controls in place
[ ] Monitoring dashboard live (latency, error rate, usage)
[ ] Alert thresholds configured (P99 latency, error rate, cost)
[ ] On-call schedule confirmed for launch week
[ ] Rollback procedure tested and documented

SUPPORT READINESS
[ ] Customer success team briefed with demo and FAQ
[ ] Help documentation written and published
[ ] Support ticketing tags added for this feature
[ ] Escalation path defined for complex issues
[ ] Known issues list shared with CS team

LEGAL AND COMPLIANCE
[ ] Privacy review completed
[ ] Terms of service updated (if applicable)
[ ] Compliance sign-off received (if regulated domain)
[ ] Data processing agreements updated (if new third-party)

COMMUNICATIONS
[ ] Internal announcement drafted and approved
[ ] User-facing announcement drafted and approved
[ ] In-product messaging / onboarding designed
[ ] Marketing materials (if external launch) approved

PRE-LAUNCH SIGN-OFF
[ ] PM sign-off
[ ] Engineering lead sign-off
[ ] Design lead sign-off
[ ] Legal sign-off (if applicable)
[ ] Go/no-go decision made by: ___ on: ___
```

### 2.2 Go / No-Go Decision Framework

```
GO / NO-GO DECISION CRITERIA

AUTOMATIC NO-GO (any single item = no-go):
[ ] Any open P0 or P1 bug in the feature
[ ] Monitoring not in place
[ ] Rollback procedure not tested
[ ] Legal sign-off not received (if required)
[ ] Pre-launch checklist < 90% complete

CONDITIONAL GO (proceed with documented mitigation):
[ ] P2 bug open — mitigation: _______________________________________________
[ ] Performance below SLA — mitigation: _______________________________________________
[ ] Support documentation incomplete — mitigation: _______________________________________________

GO:
All automatic no-go criteria are clear AND
All conditional go items have documented mitigations.

Decision: Go / No-Go / Conditional Go
Decision owner: _______________________________________________
Date: _______________________________________________
```

---

## Phase 3: Soft Launch

### 3.1 Soft Launch Audience Selection

```
SOFT LAUNCH AUDIENCE

Size: ___% of eligible users (typically 1–10% for first exposure)
Selection method:
  [ ] Random sample — for general validation
  [ ] Beta opt-in group — for motivated early adopters
  [ ] Internal team first — for maximum control
  [ ] Specific segment — for targeted validation: _______________________________________________

Soft launch goals:
  1. Validate quality in production (not just staging)
  2. Identify edge cases not caught in testing
  3. Confirm monitoring is detecting real issues
  4. Gather initial user feedback

Soft launch duration: ___ days
Gate to full launch:
  Quality metric > ___
  Error rate < ___%
  No P1 issues in 72 hours
  User feedback sentiment > ___
```

### 3.2 Soft Launch Monitoring Protocol

```
SOFT LAUNCH MONITORING PROTOCOL

Hour 0–4: Intensive monitoring
  Output sampling: 100% (if AI feature)
  Error rate: Check every 30 minutes
  Latency: Monitor P50, P95, P99 continuously
  User feedback: Review all feedback in real time

Hour 4–24: Standard monitoring
  Error rate: Check every 2 hours
  Quality score: Review at 12-hour mark
  User feedback: Review at 12-hour and 24-hour marks

Day 2–7: Normal monitoring
  Daily check of all launch metrics
  Compare to pre-launch baseline
  Look for gradual quality drift

Escalation triggers:
  Error rate > 2% → PM + engineering on-call immediately
  Quality score < threshold → PM + AI team immediately
  User reports of unexpected behaviour → Investigate within 2 hours
  Any P1 issue → Rollback consideration
```

---

## Phase 4: Full Launch

### 4.1 Launch Day Playbook

```
LAUNCH DAY PLAYBOOK

T-2 hours:
  [ ] Final monitoring check — all systems green
  [ ] On-call team confirmed and standing by
  [ ] Communications ready to send — not yet sent
  [ ] Feature flag at soft launch % — confirm readiness to ramp

T-0: Launch
  [ ] Ramp feature flag to target %
  [ ] Send internal announcement
  [ ] Send user-facing announcement (if external launch)
  [ ] Start intensive monitoring period

T+30 minutes:
  [ ] First metrics check — error rate, latency, initial adoption
  [ ] Confirm: events firing correctly (analytics sanity check)
  [ ] Any anomalies? → Investigate before continuing ramp

T+2 hours:
  [ ] Second metrics check
  [ ] Quality score review (if AI feature)
  [ ] Support ticket volume check
  [ ] Decision: hold at current %, ramp further, or investigate

T+24 hours:
  [ ] First-day review meeting
  [ ] Metrics vs launch targets
  [ ] Support issues summary
  [ ] Decision: continue rollout, hold, or rollback
```

### 4.2 Rollback Decision and Procedure

```
ROLLBACK DECISION CRITERIA

Rollback immediately if:
  [ ] Any confirmed data breach or privacy violation
  [ ] Any confirmed safety violation or harmful content reaching users
  [ ] Error rate > 10% sustained for > 30 minutes
  [ ] P99 latency > 30 seconds sustained

Consider rollback if:
  [ ] Error rate > 5% for > 2 hours with no fix in sight
  [ ] User negative feedback rate > 10%
  [ ] Quality metric below minimum threshold
  [ ] Critical bug that affects core functionality

ROLLBACK PROCEDURE

Step 1: PM makes the rollback decision (no committee needed in a crisis)
Step 2: Engineering lead executes — feature flag to 0% or previous version deployed
Step 3: Engineering confirms rollback is effective — metrics returning to baseline
Step 4: PM sends internal notification within 15 minutes
Step 5: User-facing communication within 1 hour (if users experienced issues)
Step 6: Root cause analysis within 24 hours
Step 7: Re-launch plan within 48 hours

Rollback execution time target: < 15 minutes from decision to completion
```

---

## Phase 5: Post-Launch

### 5.1 First-Week Review

```
FIRST-WEEK REVIEW (7 days post-launch)

Attendees: PM + Engineering lead + Design lead + CS lead

METRICS REVIEW
Primary launch metric: Target ___ / Actual ___
  On track / Below target — reason: _______________________________________________

Adoption:
  Feature adoption rate: ___%  (target: ___%)
  Day 1 retention of users who used feature: ___%

Quality (if AI feature):
  AI quality score: ___  (target: ___)
  AI acceptance rate: ___%

Issues:
  P1 bugs found: ___  |  Status: _______________________________________________
  P2 bugs found: ___  |  Status: _______________________________________________
  Support ticket volume: ___  |  Top issue: _______________________________________________

USER FEEDBACK
  Quantitative: _______________________________________________
  Qualitative highlights: _______________________________________________
  Unexpected use cases discovered: _______________________________________________

DECISIONS
  Continue as planned: [ ]
  Iterate on: _______________________________________________
  Accelerate rollout: [ ]  |  Slow rollout: [ ]  |  Hold at current: [ ]
  Bugs to fix before further rollout: _______________________________________________
```

### 5.2 30-Day Post-Launch Review

```
30-DAY POST-LAUNCH REVIEW

METRIC PERFORMANCE
| Metric | Launch Target | Actual at 30 days | Assessment |
|--------|--------------|------------------|------------|
| Primary | | | On track / Below / Exceeding |
| Adoption | | | |
| Retention impact | | | |
| Quality (if AI) | | | |

KEY LEARNINGS
What worked better than expected: _______________________________________________
What worked worse than expected: _______________________________________________
What surprised us: _______________________________________________

ITERATION PLAN
What will we change based on 30-day data?
1. _______________________________________________
2. _______________________________________________

KNOWLEDGE BASE UPDATE
[ ] Launch retrospective documented
[ ] Metrics added to product KPI dashboard
[ ] Learnings shared with broader team
[ ] Launch playbook updated with new learnings
```

---

## AI Product Launch Specifics

### 6.1 AI Launch Gate Requirements

AI features require additional readiness gates before any user sees them:

```
AI LAUNCH GATE CHECKLIST

Quality gate:
[ ] Evaluation dataset of minimum ___ examples tested
[ ] LLM-as-judge quality score ≥ ___ / 5
[ ] Human review of ___ sampled outputs completed
[ ] No catastrophic failures in evaluation (score 1/5) in > 1% of outputs

Safety gate:
[ ] Adversarial test dataset run — pass rate ≥ ___%
[ ] Red team exercise completed
[ ] Content filter configured and tested
[ ] Prompt injection defense validated

Monitoring gate:
[ ] AI quality monitoring dashboard live
[ ] Output sampling at ___% active
[ ] Alert thresholds configured for: quality score / filter trigger rate / cost
[ ] On-call team briefed on AI-specific escalation triggers

Privacy gate:
[ ] DPA in place with all model providers
[ ] PII handling policy implemented and tested
[ ] User-facing privacy disclosure updated
[ ] Legal sign-off received

AI launch is conservative by default:
  Week 1: Internal users only (100% of internal team)
  Week 2: Trusted beta users (1–5% of user base)
  Week 3–4: Gradual rollout (10% → 25% → 50% → 100%)
  Only accelerate if all quality and safety metrics are holding
```

### 6.2 AI-Specific Launch Communications

```
AI LAUNCH COMMUNICATION PRINCIPLES

1. Be specific about what the AI does — and does not do
   ✅ "AI summarises meeting transcripts into three sections: decisions, action items, and next steps"
   ❌ "AI automatically captures the most important insights from your meetings"

2. Set accurate expectations about quality
   ✅ "The AI gets it right most of the time. You can always edit the summary."
   ❌ "Our AI never misses a thing"

3. Make the feedback mechanism prominent
   "If the AI misses something, click [report issue] and we'll use your feedback to improve it."

4. Disclose that it is AI
   All AI-generated content must be clearly labelled as AI-generated.
   Never present AI output as human-created.

5. Communicate limitations proactively
   "The AI works best on meetings in English. Support for other languages is coming."
```

---

## Templates

### Template A: Launch Communication (internal)

```
Subject: Launching [Feature Name] — [Date]

Hey team,

We're launching [feature name] on [date].

What it does: [1–2 sentences — plain language]

Who it's for: [target user segment]

How to see it: [where to find it in the product]

What to watch: We're monitoring [primary metric] and [quality metric] closely.
If you see any issues, post in #[slack channel] immediately.

Known limitations: [1–2 known gaps or edge cases]

Support docs: [link]

Questions? Ping [PM name].

— [PM]
```

### Template B: Launch Communication (user-facing)

```
Subject: Introducing [Feature Name]

[Opening — what's new and why it matters to the user]

[Feature name] [does specific thing] so you can [user benefit].

[How to get started — 1–2 steps maximum]

[What to expect — set accurate expectations, including any limitations]

[Feedback invitation — "Let us know what you think"]

[Team sign-off]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Launching on a Friday | Launch Tuesday–Thursday — team is available to respond to issues |
| No rollback plan | Rollback procedure tested before launch day |
| 100% rollout on day one | Gradual rollout — internal → beta → full |
| Communications written the day of launch | Communications written and approved 1 week before launch |
| No support briefing | CS team briefed and confident before any user sees the feature |
| AI launch without quality gate | AI features require evaluation dataset pass before any user exposure |
| No 30-day review | Launch is not complete until the 30-day data is reviewed and acted on |
| Treating a launch as a finish line | A launch is the beginning of learning, not the end of work |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Launch brief review | Per launch, 4–6 weeks before | PM |
| Pre-launch checklist | Per launch, 2 weeks before | PM |
| Go/no-go decision | Per launch, 3 days before | PM + Eng lead |
| Launch day monitoring | Hourly for first 4 hours | PM + Eng on-call |
| First-week review | 7 days post-launch | PM + full launch team |
| 30-day review | 30 days post-launch | PM |
| Launch playbook retrospective | After each major launch | PM leads |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Complete Launch Plan

> **Best for:** Planning a product launch end-to-end — from pre-launch preparation through 30-day review.

```
You are a product launch specialist helping me build a complete launch plan.

Design the launch plan across all five phases:

1. Launch planning (4–6 weeks before)
   - Write the launch brief with goals, audience, narrative, and success metrics
   - Design the launch timeline with specific milestones
   - Build the launch RACI

2. Internal readiness (2 weeks before)
   - Write the complete pre-launch checklist tailored to my feature type
   - Design the go/no-go decision framework with specific criteria

3. Soft launch (1–2 weeks)
   - Design the soft launch audience selection
   - Write the monitoring protocol for the soft launch period
   - Define the gate criteria for advancing to full launch

4. Full launch (launch day)
   - Write the launch day playbook hour by hour
   - Design the rollback decision criteria and procedure

5. Post-launch (30 days)
   - Design the first-week review agenda
   - Design the 30-day review template

For AI features, add the AI launch gate requirements throughout.

My launch:
Feature / product: [describe]
Launch date target: [date]
Target audience: [who and how many]
Primary launch goal: [what success looks like]
Is this an AI feature: [yes/no — if yes, describe the AI component]
Team structure: [who is involved in the launch]
```

---

### Prompt 2 — Write the Launch Communications

> **Best for:** Drafting all launch communications — internal announcement, user-facing email, in-product messaging.

```
You are a product communications specialist helping me write all launch communications.

Write three communications for my product launch:

1. Internal announcement (for the team)
   - What the feature does (technical but human)
   - Who it's for and when it goes live
   - What to watch and escalate
   - Known limitations and edge cases
   - Support documentation link

2. User-facing announcement (email or in-product notification)
   - Hook: what's new and why it matters to them specifically
   - How to get started (maximum 2 steps)
   - Accurate expectations — what it does and what it doesn't
   - Feedback invitation
   - Appropriate AI disclosure if applicable

3. In-product onboarding (tooltip or empty state)
   - First impression when user encounters the feature
   - What it is in 1 sentence
   - How to use it in 1 action
   - Trust signal (what the AI can be relied on for)

AI communication principles (apply if AI feature):
- Be specific about what the AI does and doesn't do
- Set accurate quality expectations
- Make the feedback mechanism prominent
- Disclose AI involvement clearly
- Communicate limitations proactively

My feature: [describe what it does]
User benefit: [what is better for the user after launch]
Target user: [who are they, what do they care about]
Known limitations: [what doesn't it do yet]
Is this an AI feature: [yes/no — if yes, what does the AI do]
```

---

### Prompt 3 — Design the Rollback Plan

> **Best for:** Before any launch — defining the rollback criteria and procedure so decisions are made in advance, not in a crisis.

```
You are a platform reliability engineer helping me design the rollback plan for my product launch.

Design the complete rollback framework:

1. Automatic rollback triggers
   - Define the specific metric thresholds that trigger an immediate rollback (no decision needed)
   - Write these as precise, measurable conditions — not vague descriptions

2. Consider-rollback triggers
   - Define the conditions that require a human decision about rollback
   - Who makes that decision? How quickly must it be made?

3. Rollback procedure
   - Step-by-step procedure from rollback decision to complete execution
   - Who does what, in what order, and how long each step takes
   - Target: complete rollback in < 15 minutes from decision

4. Communication during rollback
   - Internal notification: who, what, when
   - User-facing notification: when is one needed? What does it say?
   - Post-rollback communication: what do we tell users happened?

5. Post-rollback process
   - Root cause analysis timeline (within 24 hours)
   - Re-launch plan (within 48 hours)
   - What must be true before re-launch?

For AI features, add:
   - AI quality degradation rollback threshold
   - AI safety violation immediate rollback trigger
   - What the user sees during AI rollback (graceful degradation to non-AI experience)

My launch:
Feature type: [describe — AI or non-AI, what it does]
Current monitoring in place: [describe]
Rollback mechanism: [feature flag / previous version deployment / other]
Rollback execution capability: [can you roll back in < 15 minutes?]
```

---

### Prompt 4 — Conduct a Post-Launch Review

> **Best for:** 7 or 30 days after launch — synthesising what happened and deciding what to do next.

```
You are a product analyst helping me conduct a structured post-launch review.

Guide me through a comprehensive review at [7 days / 30 days] post-launch:

1. Metrics assessment
   For each launch metric, compare actual to target:
   - Primary metric: hit / missed / exceeded — by how much?
   - Adoption: what % of eligible users have used the feature?
   - Quality (if AI): is the AI performing as expected?
   - Retention: are users who used the feature retaining better?

2. Issue analysis
   - What bugs or issues surfaced that were not anticipated?
   - What support volume came in and what were the top issues?
   - Did any of the pre-launch risk scenarios materialise?

3. User feedback synthesis
   - What qualitative feedback have we received?
   - What unexpected use cases have users found?
   - What is the sentiment overall?

4. Decision
   Based on the data:
   - Continue as planned / accelerate rollout / slow rollout / hold / rollback consideration
   - What specific changes should be made based on this data?
   - What should the team prioritise in the next sprint based on launch learnings?

5. Learning documentation
   - What worked that should be repeated in future launches?
   - What should be done differently?
   - What would have made this launch better?

My launch data:
Feature: [describe]
Launch date: [date]
Metrics at [7/30] days: [paste data]
Issues encountered: [describe]
User feedback received: [summarise]
```

---

### Prompt 5 — Plan an AI Feature Launch

> **Best for:** Launching specifically an AI feature — applying the additional quality, safety, and communication requirements.

```
You are an AI product launch specialist helping me plan the launch of an AI feature.

Design the complete AI-specific launch plan:

1. AI launch gate requirements
   - What evaluation dataset size and quality score threshold must be met?
   - What safety and adversarial testing is required before any user exposure?
   - What monitoring must be live before launch day?
   - What privacy and compliance gates must be cleared?

2. Conservative rollout plan
   - Design the 4-stage AI rollout: internal → beta → partial → full
   - For each stage: what quality and safety metrics must hold before advancing?
   - What is the maximum ramp speed (how quickly can I increase the %)? 

3. AI-specific monitoring protocol
   - What is monitored at each stage and how intensively?
   - What AI-specific metrics are most important in the first 48 hours?
   - What would trigger slowing or stopping the rollout?

4. AI launch communications
   - Write the user-facing launch message applying AI communication principles
   - How do I set expectations without over-promising or under-promising?
   - How do I handle the first AI failures users will inevitably encounter?

5. Post-launch AI quality management
   - How do I monitor AI quality in production beyond the first week?
   - How do I detect gradual quality drift before users notice?
   - What is the process for improving quality based on production data?

My AI feature: [describe what the AI does]
Target user: [describe]
AI quality baseline (from evaluation): [current quality score]
Expected daily AI interactions at full rollout: [number]
Primary quality risk: [what are you most worried about?]
```
