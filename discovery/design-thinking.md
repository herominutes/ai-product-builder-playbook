# 💡 Design Thinking — AI Product Builder Playbook

> **Adapting the classic 5-stage design thinking process for AI product development**

---

## Table of Contents

- [Overview](#overview)
- [Why AI Products Need a Modified DT Process](#why-ai-products-need-a-modified-dt-process)
- [The AI Design Thinking Sprint](#the-ai-design-thinking-sprint)
- [Stage 1: Empathize](#stage-1-empathize)
- [Stage 2: Define](#stage-2-define)
- [Stage 3: Ideate](#stage-3-ideate)
- [Stage 4: Prototype](#stage-4-prototype)
- [Stage 5: Test](#stage-5-test)
- [Templates & Worksheets](#templates--worksheets)
- [Anti-Patterns](#anti-patterns)

---

## Overview

Design Thinking for AI products follows the same five stages — **Empathize, Define, Ideate, Prototype, Test** — but each stage must be augmented to account for AI-specific constraints: model uncertainty, latency, data dependencies, and the need to design for both the expected *and* unexpected model outputs.

> **Core Principle:** You are designing for a system that is probabilistic, not deterministic. Every design decision must account for the range of possible AI outputs, not just the best case.

---

## Why AI Products Need a Modified DT Process

| Traditional Product | AI Product |
|---|---|
| Prototype with static mockups | Prototype requires live model or simulation |
| Define success as feature complete | Define success as output quality threshold |
| Test assumes deterministic outputs | Test must cover output variance and edge cases |
| Failure = bug | Failure = model hallucination, bias, or low confidence |
| User trust is assumed | User trust must be earned and measured |

---

## The AI Design Thinking Sprint

**Recommended format:** 5 days (one stage per day) or 2-week sprint (deeper research).

```
Day 1: EMPATHIZE — User research, session reviews, interviews
Day 2: DEFINE — Problem statement, How Might We, AI constraint mapping
Day 3: IDEATE — Brainstorm, AI capability mapping, feasibility filter
Day 4: PROTOTYPE — Wizard of Oz, prompt prototyping, storyboards
Day 5: TEST — Usability sessions, output quality review, trust scoring
```

---

## Stage 1: Empathize

**Goal:** Deeply understand users, their context, and their relationship with AI.

### 1.1 AI Empathy Additions

Beyond standard empathy research, specifically investigate:

- **AI Familiarity:** How comfortable is this user with AI tools? What's their mental model?
- **Trust Baseline:** Do they trust AI by default or are they skeptical?
- **Failure Tolerance:** How do they react when AI gets it wrong?
- **Autonomy Preference:** Do they want AI to act, assist, or advise?

### 1.2 Empathy Interview Guide (AI-Specific)

```
## AI Empathy Interview Guide

WARM-UP (5 min)
- Tell me about your current workflow for [task].
- What tools do you use today?

AI RELATIONSHIP (10 min)
- Have you used any AI tools for [task]? Which ones?
- Can you walk me through the last time you used one?
- What happened? What did you expect vs. what did you get?
- When the AI was wrong, what did you do?

TRUST & CONTROL (10 min)
- When would you trust AI to do [task] without checking?
- What would make you trust it more?
- What's your biggest concern about AI doing [task]?

IDEAL STATE (5 min)
- If AI could do anything to help with [task], what would be most valuable?
- What would "perfect" look like?

WRAP-UP
- Is there anything I didn't ask that you think is important?
```

### 1.3 Empathy Map (AI Edition)

```
## Empathy Map: [Persona Name]
Date: ___________  |  Based on: ___ interviews, ___ session replays

+---------------------------+---------------------------+
|         SAYS              |         THINKS            |
|                           |                           |
| Quotes from interviews    | Beliefs, assumptions,     |
| about AI tools            | mental models about AI    |
|                           |                           |
+---------------------------+---------------------------+
|         DOES              |         FEELS             |
|                           |                           |
| Actual behaviors when     | Emotions when interacting |
| using AI features         | with AI outputs           |
|                           |                           |
+---------------------------+---------------------------+

AI TRUST LEVEL: [Skeptic / Cautious / Neutral / Open / Enthusiast]
AUTONOMY PREFERENCE: [Act for me / Suggest / Advise only]
FAILURE TOLERANCE: [Zero / Low / Medium / High]
```

---

## Stage 2: Define

**Goal:** Crystallize the problem, constrain the AI opportunity, write a precise problem statement.

### 2.1 The AI Problem Statement Formula

Avoid vague AI problem statements. Use this format:

```
[Persona] needs a way to [accomplish goal] 
without [pain / risk they face today],
even when [AI uncertainty condition — e.g., "the model isn't 100% confident"].

We'll know we've solved this when [measurable outcome].
```

**Example:**
> A solo founder needs a way to get a competitive analysis done in under an hour without needing research expertise, even when the AI's market data is incomplete or uncertain. We'll know we've solved this when 70% of users complete a full analysis in their first session.

### 2.2 How Might We (AI Edition)

Generate HMW questions in three categories:

```
## How Might We Questions

CAPABILITY HMW (What could AI do?)
- HMW use AI to ___________________________?
- HMW automate ___________________________ for the user?

TRUST HMW (How do we earn trust?)
- HMW help users know when to trust the AI output?
- HMW make it easy to correct AI when it's wrong?
- HMW communicate AI confidence without overwhelming the user?

FALLBACK HMW (What if AI fails?)
- HMW design an experience that still works when the model fails?
- HMW prevent a bad AI output from destroying user trust permanently?
```

### 2.3 AI Constraint Canvas

Before ideating, map your actual constraints:

```
## AI Constraint Canvas

MODEL CAPABILITIES
- What can our current model actually do well? _______________
- What is it unreliable at? _______________
- What is the latency? (p50: ___ | p99: ___)

DATA CONSTRAINTS
- What data does the model need? _______________
- What data do we actually have? _______________
- What's the gap? _______________

REGULATORY / TRUST CONSTRAINTS
- Are there outputs we cannot show? (PII, medical, legal, financial) ___
- Do we need to disclose AI use? _______________

TIMELINE
- Can we fine-tune / prompt-engineer in this sprint? _______________
- What requires a model change (longer timeline)? _______________
```

---

## Stage 3: Ideate

**Goal:** Generate a wide range of ideas; filter for AI feasibility and user trust impact.

### 3.1 AI Ideation Techniques

**Technique 1: Capability-First Brainstorm**

Start with what the AI can do, work backward to the user need:
1. List 10 things your model can do reliably
2. For each: "What user problem does this solve?"
3. Vote on highest-value intersections

**Technique 2: Trust Ladder Brainstorm**

Brainstorm along the autonomy spectrum:

```
ADVISE          ASSIST          ACT
  |               |              |
"Here's what   "I drafted     "I did it.
 I'd suggest"   this, review"  Undo?"
```

For each idea, assign it to a rung of the ladder. Ensure you have ideas across all three rungs.

**Technique 3: Failure Mode Brainstorm**

Deliberately brainstorm AI failures and design around them:
- What if the AI is confidently wrong?
- What if the AI is slow (>10s)?
- What if the AI refuses to answer?
- What if the AI output is offensive or harmful?

For each: design the recovery experience.

### 3.2 Idea Prioritization Matrix

```
## Idea Prioritization

| Idea | User Value | AI Feasibility | Trust Risk | Effort | Score |
|------|-----------|----------------|------------|--------|-------|
|      | /5        | /5             | (lower=better) /5 | /5 | |
```

**Score formula:** (User Value + AI Feasibility) − Trust Risk − Effort

Top 3 ideas move to prototype.

---

## Stage 4: Prototype

**Goal:** Build the minimum artifact to test your AI design hypothesis.

### 4.1 AI Prototype Types (choose the right fidelity)

| Prototype Type | When to Use | Tools |
|---|---|---|
| **Storyboard** | Early concept validation, no model needed | Paper, Figma |
| **Wizard of Oz** | Test UX before building the model | Human responds as AI in real-time |
| **Prompt Prototype** | Test model output quality quickly | ChatGPT, Claude API, Jupyter |
| **Clickable Mockup** | Test UI flow with static AI outputs | Figma, Framer |
| **Live Prototype** | Test real model behavior end-to-end | Vercel, Replit, internal staging |

### 4.2 Wizard of Oz Protocol for AI

When testing AI UX before the model is built:

```
## Wizard of Oz Setup

ROLE ASSIGNMENTS
- Facilitator: Runs the session, talks to the participant
- Wizard: Hidden operator who plays the role of the AI
- Observer: Takes notes on reactions

WIZARD INSTRUCTIONS
- Respond to user inputs within [target latency — e.g., 3 seconds]
- Use these response templates: [attach prompt guide]
- Occasionally introduce a realistic error: [define error scenarios]
- Do NOT break character

WHAT TO OBSERVE
- [ ] Does the user understand what the AI is doing?
- [ ] Does the user trust the output without question?
- [ ] Does the user know how to correct the AI?
- [ ] What is their reaction to the error scenario?
```

### 4.3 Prompt Prototyping Template

When using a live model to prototype outputs:

```
## Prompt Prototype Log

Feature: _______________
Date: _______________
Model: _______________

| Test # | User Input | Prompt Used | Output | Quality (1-5) | Notes |
|--------|-----------|-------------|--------|---------------|-------|
| 1      |           |             |        |               |       |
| 2      |           |             |        |               |       |

BEST PROMPT VERSION:
[paste prompt here]

KNOWN FAILURE CASES:
- Input that breaks it: _______________
- Edge case to handle: _______________
```

---

## Stage 5: Test

**Goal:** Validate with real users. Measure both UX quality AND AI output quality.

### 5.1 AI Usability Test Plan

```
## Usability Test Plan

Product / Feature: _______________
Prototype Type: _______________
Participants: ___ (target: 5 minimum)
Duration: ___ minutes per session

TEST TASKS
1. [Task description] — Success Criteria: ___
2. [Task description] — Success Criteria: ___
3. [Task description] — Success Criteria: ___

ERROR SCENARIO (always include one)
- Trigger: _______________
- What we're testing: Can the user recover gracefully?

METRICS TO CAPTURE
- Task completion rate
- Time on task
- Error recovery rate
- Trust rating (post-task survey: "How much did you trust the AI response?" 1–5)
- Verbal reactions (think-aloud)

POST-TEST SURVEY
1. How confident were you in the AI's outputs? (1–5)
2. Would you use this feature again? (Yes / No / Maybe)
3. What would make you trust it more?
4. What surprised you?
```

### 5.2 AI Output Quality Rubric

Rate AI outputs during testing on these dimensions:

```
| Dimension     | 1 (Poor) | 3 (Acceptable) | 5 (Excellent) |
|---------------|----------|----------------|---------------|
| Accuracy      | Wrong    | Partially right | Correct       |
| Completeness  | Missing key info | Mostly complete | Full & thorough |
| Clarity       | Confusing | Understandable | Crystal clear |
| Tone          | Off-brand | Neutral | Perfectly calibrated |
| Safety        | Harmful content | No issues | Proactively safe |
```

### 5.3 Test Findings Template

```
## Design Thinking Test Findings

Date: _______________
Prototype Tested: _______________
Participants: ___

## What Worked
- [Finding 1 with evidence]
- [Finding 2 with evidence]

## What Didn't Work
- [Finding 1 — UX issue or AI output issue — with evidence]
- [Finding 2 — with evidence]

## Surprises
- [Anything unexpected from users or from the AI]

## AI-Specific Findings
- Output Quality Score (avg): ___/5
- Trust Rating (avg): ___/5
- Error Recovery Rate: ___%

## Next Iteration Decisions
- [ ] Change to prototype: _______________
- [ ] Change to prompt: _______________
- [ ] Change to model: _______________
- [ ] Ready to build: _______________
```

---

## Templates & Worksheets

### One-Page Design Sprint Planner

```
## Design Sprint: [Feature Name]
Sprint Dates: _______________  |  Team: _______________

EMPATHIZE (Day 1)
- Research method: _______________
- Key finding: _______________

DEFINE (Day 2)
- Problem statement: _______________
- Top HMW: _______________

IDEATE (Day 3)
- Ideas generated: ___
- Ideas selected: _______________

PROTOTYPE (Day 4)
- Prototype type: _______________
- Link: _______________

TEST (Day 5)
- Participants: ___
- Top finding: _______________
- Decision: Build / Iterate / Kill
```

---

## Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Designing only for the ideal AI output | Design for the full output distribution — best, average, and worst case |
| Skipping Wizard of Oz because "we have a model" | WoZ is faster and often reveals more; always use it for new flows |
| Testing with internal team only | AI outputs feel different to non-experts; always test with real users |
| Declaring done after one test round | AI products need continuous testing as models update |
| Treating latency as an engineering problem | Latency is a UX problem; design around it in the prototype |

---

*Part of the [AI Product Builder Playbook](../README.md)*
