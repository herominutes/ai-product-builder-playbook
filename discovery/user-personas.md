# 👤 User Personas — AI Product Builder Playbook

> **Building AI-product-ready personas that capture trust, autonomy, and AI fluency — not just demographics**

---

## Table of Contents

- [Overview](#overview)
- [Why Standard Personas Fall Short for AI Products](#why-standard-personas-fall-short-for-ai-products)
- [The AI Persona Framework](#the-ai-persona-framework)
- [The AI Fluency Spectrum](#the-ai-fluency-spectrum)
- [Persona Research Process](#persona-research-process)
- [The Full Persona Template](#the-full-persona-template)
- [Lightweight Persona Formats](#lightweight-persona-formats)
- [Using Personas in Product Decisions](#using-personas-in-product-decisions)
- [Persona Maintenance](#persona-maintenance)
- [Anti-Patterns](#anti-patterns)

---

## Overview

Personas are only useful if they drive decisions. In AI product development, the most important persona dimensions are the ones that rarely appear in standard templates: AI familiarity, trust level, failure tolerance, and autonomy preference. Without these, you'll design an AI product for an imaginary user who doesn't reflect your actual user base.

> **Core Principle:** Your persona must capture not just who the user is, but how they relate to AI — because that relationship determines everything about how you design.

---

## Why Standard Personas Fall Short for AI Products

Standard persona dimensions (age, job title, goals, frustrations, tech savviness) are insufficient for AI products because they don't capture:

| Missing Dimension | Why It Matters |
|---|---|
| **AI Fluency** | How much does this user understand about how AI works? |
| **Trust Baseline** | Do they trust AI by default, or need to be convinced? |
| **Failure Tolerance** | How do they react when AI is wrong? Will they churn or recover? |
| **Autonomy Preference** | Do they want AI to act, advise, or just inform? |
| **Current AI Behavior** | Are they already using AI tools? Which ones and how? |
| **Identity Relationship** | Does using AI feel like enhancement or a threat to their professional identity? |

---

## The AI Persona Framework

Every AI product persona needs three layers:

### Layer 1: Foundation (Standard)
- Name, role, industry, experience level
- Goals and frustrations
- A day in their life (workflow context)

### Layer 2: AI Profile (Required)
- AI Fluency Level (1–5)
- Current AI tool usage
- Trust Baseline: Skeptic / Cautious / Open / Enthusiast
- Failure Tolerance: Zero / Low / Medium / High
- Autonomy Preference: Inform / Suggest / Assist / Delegate / Automate
- Identity Relationship: Empowered / Neutral / Threatened

### Layer 3: Behavioral Signals
- What triggers them to reach for AI?
- What makes them trust an AI output?
- What makes them distrust or stop using AI?
- How do they talk about AI to colleagues?

---

## The AI Fluency Spectrum

Segment your user base by AI fluency. Design decisions differ significantly across these levels.

```
LEVEL 1 — AI SKEPTIC
"I don't trust it. I've seen it hallucinate."
Uses: None or minimal; tried it once and had a bad experience
Design for: Transparency first, automation last, easy correction

LEVEL 2 — AI CURIOUS
"I know it exists. I've played with it a bit."
Uses: Occasional, low-stakes tasks
Design for: Guided first experience, visible confidence levels, early wins

LEVEL 3 — AI PRACTITIONER
"I use it daily for specific tasks. I know its limits."
Uses: Regular, task-specific, knows when NOT to use AI
Design for: Speed, reliable outputs, customization options

LEVEL 4 — AI POWER USER
"I've built prompts, workflows, and integrations around AI."
Uses: AI central to workflow; chains tools together
Design for: Control, extensibility, keyboard shortcuts, advanced settings

LEVEL 5 — AI BUILDER
"I build with AI. I think in models and pipelines."
Uses: Evaluates AI tools technically, builds on top of them
Design for: API access, model transparency, developer experience
```

---

## Persona Research Process

### Step 1: Write Persona Hypotheses (Pre-Research)

```
## Persona Hypothesis: [Archetype Name]

WHO WE THINK THEY ARE:
Role: _______________
AI Fluency: Level ___
Trust: _______________
Autonomy: _______________

WHAT WE THINK THEY NEED:
Job: _______________
Key frustration: _______________

WHAT WE'RE TESTING IN RESEARCH:
- Is this archetype real? How large is this segment?
- Are our assumptions about their AI relationship accurate?
- What did we get wrong?
```

### Step 2: Research Methods

| Method | What It Reveals | Target N |
|---|---|---|
| Structured interviews | AI fluency, trust, behavior, mental models | 6–10 per persona |
| Survey (quantitative) | Segment size, AI tool usage, trust distribution | 100–500 |
| Session replay analysis | Actual behavior with AI features | 20+ per feature |
| Support ticket mining | Failure modes and trust breakdown moments | All tickets, tagged |
| NPS segmentation | Trust correlation with satisfaction | Full user base |

### Step 3: Persona Interview Guide

```
## Persona Interview Guide (AI Focus)

BACKGROUND (5 min)
- Tell me about your role and what a typical workday looks like.
- What are the most time-consuming parts of your job?

AI RELATIONSHIP (15 min)
- What AI tools do you use regularly?
- How did you start using them?
- Can you walk me through how you use AI on a typical day?
- What do you use AI for that you absolutely trust?
- What would you never let AI do without checking?
- When was the last time AI surprised you — positively or negatively?

TRUST & FAILURE (10 min)
- When AI gives you a wrong answer, what do you do?
- Has an AI mistake ever caused a real problem for you?
- How do you know when to trust an AI output?
- What would make you trust an AI tool more?

IDENTITY (5 min)
- How do you feel about using AI in your work?
- Does using AI change how you feel about your role?
- What do your colleagues think about AI?

CLOSING (5 min)
- If you could change one thing about AI tools you use, what would it be?
- Is there anything you wish AI could do that it can't yet?
```

### Step 4: Synthesis Process

```
1. INDIVIDUAL SUMMARIES
   Write a 3-sentence summary of each interview subject.

2. PATTERN CLUSTERING
   Group by: AI fluency level, trust level, autonomy preference.

3. ARCHETYPE IDENTIFICATION
   Name 2–4 archetypes that emerge from clusters.

4. VALIDATION CHECK
   - Is this archetype large enough to design for?
   - Is it distinct enough from other archetypes?
   - Do we have direct quotes to make it vivid?

5. PRIORITIZATION
   Primary persona: [Design for]
   Secondary personas: [Design to not exclude]
```

---

## The Full Persona Template

```
## Persona: [Name]
Version: ___  |  Date: ___  |  Based on: ___ interviews + ___ survey responses

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

FOUNDATION
Role: _______________
Industry: _______________
Experience: _______________

QUOTE (from research):
"_______________"

GOALS
Primary: _______________
Secondary: _______________

FRUSTRATIONS
1. _______________
2. _______________
3. _______________

A DAY IN THEIR LIFE
[3–5 sentences describing workflow and when AI could appear]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

AI PROFILE

AI Fluency: Level [1/2/3/4/5] — [Skeptic / Curious / Practitioner / Power User / Builder]

Current AI Tools: _______________
How they use AI today: _______________

Trust Baseline:      [ ] Skeptic  [ ] Cautious  [ ] Open  [ ] Enthusiast
Failure Tolerance:   [ ] Zero  [ ] Low  [ ] Medium  [ ] High
Autonomy Preference: [ ] Inform  [ ] Suggest  [ ] Assist  [ ] Delegate  [ ] Automate

Identity Relationship:
[ ] Feels empowered by AI  [ ] Neutral  [ ] Worried AI will replace them

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

BEHAVIORAL SIGNALS

Reaches for AI when: _______________
Trusts AI output when: _______________
Stops using AI when: _______________
Talks about AI to colleagues by saying: _______________

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DESIGN IMPLICATIONS

Must have: _______________
Must never do: _______________
Onboarding priority: _______________
Trust-building priority: _______________
Default autonomy ceiling: _______________

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SEGMENT SIZE
Estimated % of user base: ___%
Estimated % of revenue: ___%
Priority: [ ] Primary  [ ] Secondary  [ ] Edge case
```

---

## Lightweight Persona Formats

### 1-Page Sprint Wall Card

```
┌──────────────────────────────────────────────────────┐
│  [NAME] — [Role] at [Industry]                       │
│                                                      │
│  GOAL: _______________                               │
│  FRUSTRATION: _______________                        │
│                                                      │
│  AI PROFILE                                          │
│  Fluency: ⬛⬛⬛⬜⬜  Level 3 — Practitioner          │
│  Trust: Cautious    Autonomy: Assist                 │
│  Failure Tolerance: Low                              │
│                                                      │
│  "Real quote from research here."                    │
│                                                      │
│  ✅ Design for: Clear explanations, easy correction  │
│  ❌ Never: Full automation, opaque AI decisions      │
└──────────────────────────────────────────────────────┘
```

### Proto-Persona (Pre-Research, Hypothesis Only)

```
## Proto-Persona: [Archetype Name]

Based on: [ ] Pure hypothesis  [ ] Anecdotes  [ ] Some data

Who we think they are: _______________
AI fluency hypothesis: Level ___
What we think they need: _______________
What we're NOT sure about: _______________
How we'll validate: _______________
Validation deadline: _______________
```

---

## Using Personas in Product Decisions

### The Persona Pressure Test

```
DECISION: _______________

PRIMARY PERSONA IMPACT
- Serves their core job?                    [ ] Yes  [ ] No  [ ] Neutral
- Matches their AI autonomy preference?     [ ] Yes  [ ] No  [ ] Exceeds it
- Could break trust given their trust level? [ ] Yes  [ ] No

SECONDARY PERSONA IMPACT
- Harms any secondary persona?              [ ] Yes  [ ] No
- If yes — is the trade-off acceptable?    _______________

DECISION: [ ] Proceed  [ ] Modify  [ ] Reject
```

### Persona-Driven Feature Defaults

```
## Default Settings by Persona

| Feature / Setting         | Skeptic (L1)    | Practitioner (L3)  | Power User (L4) |
|--------------------------|-----------------|-------------------|-----------------|
| AI auto-suggestions       | Off by default  | On by default     | On + shortcuts  |
| Confidence scores         | Always shown    | Shown on hover    | Hidden          |
| Autonomy default          | Inform only     | Assist            | Delegate        |
| Explanation depth         | Always full     | On demand         | Off             |
```

---

## Persona Maintenance

| Trigger | Action |
|---|---|
| New model or AI feature launched | Re-interview 5+ users; update AI Profile |
| User base grows significantly | Re-run quantitative segmentation |
| Major churn spike | Run exit interviews; update Behavioral Signals |
| Quarterly roadmap planning | Full persona review |
| NPS drops > 10 points | Check if trust breakdown maps to a specific persona |

---

## Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Personas built from assumptions, not research | Validate every persona with at least 6 user interviews |
| Generic "tech savvy 3/5" instead of AI fluency | Replace with the full AI Profile (trust, autonomy, fluency level) |
| One persona for the whole product | Most AI products need 2–3 personas with different autonomy needs |
| Personas that never get updated | Review quarterly; personas go stale as AI literacy increases |
| Designing for the most enthusiastic AI user | Design for the cautious majority; delight enthusiasts with optional features |
| Personas used only at project kickoff | Reference personas in every sprint planning and design review |

---

*Part of the [AI Product Builder Playbook](../README.md)*
