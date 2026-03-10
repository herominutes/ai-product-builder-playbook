# 🎯 Problem Framing Framework — AI Product Builder Playbook

> **How to define the right problem before building any AI solution**

---

## Table of Contents

- [Overview](#overview)
- [Why Problem Framing Is Critical for AI](#why-problem-framing-is-critical-for-ai)
- [The 5-Layer Problem Framing Model](#the-5-layer-problem-framing-model)
- [Problem Framing Techniques](#problem-framing-techniques)
- [The AI Feasibility Filter](#the-ai-feasibility-filter)
- [Problem Statement Formats](#problem-statement-formats)
- [From Problem to Bets](#from-problem-to-bets)
- [Templates](#templates)
- [Anti-Patterns](#anti-patterns)

---

## Overview

The most common failure mode in AI product development is not building the wrong solution — it's solving the wrong problem. AI amplifies this risk because it is powerful enough to produce convincing outputs for problems that don't matter, creating the illusion of progress.

Strong problem framing disciplines a team to answer: **"What specific human problem are we solving, for whom, and why does AI change what's possible?"** before a single prompt is written or model selected.

> **Core Principle:** A well-framed problem is already half-solved. A poorly framed problem cannot be solved, no matter how good your model is.

---

## Why Problem Framing Is Critical for AI

| AI-Specific Risk | What Happens Without Framing |
|---|---|
| **Technology-led building** | Teams build around what the model can do, not what users need |
| **Capability inflation** | AI demo looks impressive; real-world utility is marginal |
| **Misdiagnosed success** | Model accuracy is high but user outcomes don't improve |
| **Scope creep** | "AI can do anything" leads to features that solve no specific problem well |
| **Trust mismatch** | AI solves a problem users didn't want AI to solve; they reject it |

---

## The 5-Layer Problem Framing Model

Work through these layers in order. Each layer narrows the problem space.

```
LAYER 1: OBSERVATION
"What are we seeing? What symptom or signal triggered this work?"

LAYER 2: DIAGNOSIS
"Why is this happening? What are the root causes?"

LAYER 3: PROBLEM STATEMENT
"For whom? In what situation? With what consequence?"

LAYER 4: AI LENS
"Does AI change what's possible here? Why now, not before?"

LAYER 5: SUCCESS CRITERIA
"How will we know we solved it? What changes in the world?"
```

---

## Problem Framing Techniques

### Technique 1: The 5 Whys (AI Edition)

Start with a symptom. Ask "why" five times. Add an AI layer at the end.

```
## 5 Whys Template

Symptom: _______________________________________________

Why 1: _______________________________________________
Why 2: _______________________________________________
Why 3: _______________________________________________
Why 4: _______________________________________________
Why 5 (root cause): ___________________________________

AI LENS:
Could AI address this root cause? (Yes / Partially / No)
If yes — how specifically? ____________________________
Why hasn't AI solved this before? _____________________
What's different now? _________________________________
```

**Example:**

```
Symptom: Customer support response time is 48 hours

Why 1: Agents are overwhelmed with ticket volume
Why 2: 70% of tickets are asking the same 20 questions
Why 3: The help center exists but users don't find it
Why 4: Help center search is poor; articles are not written for how users ask
Why 5 (root cause): There is no intelligent bridge between user questions and existing knowledge

AI LENS:
Could AI address this? Yes — LLM-powered support that understands 
natural language questions and surfaces relevant answers instantly.
Why now? Modern LLMs can understand intent without keyword matching.
```

---

### Technique 2: Problem Tree Analysis

```
## Problem Tree

                    [ROOT PROBLEM]
                          |
          +---------------+---------------+
          |               |               |
    [Cause 1]       [Cause 2]       [Cause 3]
          |               |               |
   [Sub-cause]    [Sub-cause]    [Sub-cause]

EFFECTS (what happens because of the root problem):
    [Effect 1]     [Effect 2]     [Effect 3]
          \              |              /
           \             |             /
            [ROOT PROBLEM — same as above]

AI INTERVENTION POINTS:
Which causes or effects could AI address?
- Cause ___ → AI could: _______________
- Effect ___ → AI could: _______________
```

---

### Technique 3: Problem Reframing

Take your initial problem statement and reframe it 5 different ways. Often, one reframing reveals a better problem.

```
## Problem Reframing Exercise

INITIAL PROBLEM STATEMENT:
_______________________________________________

REFRAME 1 — FROM THE USER'S PERSPECTIVE:
"The user is trying to ___ but ___ stops them."
_______________________________________________

REFRAME 2 — FROM THE BUSINESS PERSPECTIVE:
"The business loses ___ because users can't ___."
_______________________________________________

REFRAME 3 — FROM THE SYSTEM PERSPECTIVE:
"The system fails to ___ which causes ___."
_______________________________________________

REFRAME 4 — AS AN OPPORTUNITY:
"There is an opportunity to ___ by enabling ___."
_______________________________________________

REFRAME 5 — AI-SPECIFIC:
"AI could uniquely solve ___ because it can ___ at ___ scale/speed."
_______________________________________________

BEST FRAMING SELECTED: ___  (number)
WHY: _______________________________________________
```

---

### Technique 4: The Problem Space vs. Solution Space Check

Teams frequently conflate the problem space (what's wrong) with the solution space (how to fix it). Use this check:

```
## Problem / Solution Space Check

WHAT WAS PROPOSED:
_______________________________________________

IS THIS A PROBLEM OR A SOLUTION?

A PROBLEM sounds like:
- "Users can't find what they need"
- "Agents spend 60% of their time on repetitive tasks"
- "Users abandon the flow after step 3"

A SOLUTION sounds like:
- "We need an AI chatbot"
- "We should build a recommendation engine"
- "We need to add a summarization feature"

IF IT'S A SOLUTION — restate as a problem:
"The problem this solution is trying to solve is: _______________"

NOW CHALLENGE IT:
- Is this the right problem to solve? _______________
- Is AI the right solution for this problem? _______________
- Is there a simpler non-AI solution that would work? _______________
```

---

## The AI Feasibility Filter

Before investing in an AI solution to a problem, run this filter:

```
## AI Feasibility Filter

PROBLEM: _______________________________________________

QUESTION 1 — DATA
Is there enough data to train or prompt a model for this problem?
[ ] Yes — we have labeled examples / sufficient training data
[ ] Partial — we have some data but it needs augmentation
[ ] No — we'd be starting from scratch
Notes: _______________

QUESTION 2 — ACCURACY THRESHOLD
What accuracy level is acceptable?
Required: ____% | Current AI benchmark: ____%
Is the gap bridgeable? [ ] Yes [ ] No [ ] Unknown
Notes: _______________

QUESTION 3 — HUMAN ALTERNATIVE
What is the human doing today? How does AI compare?
Human solution: _______________ | Speed: ___ | Cost: ___
AI solution: _______________ | Speed: ___ | Cost: ___
AI advantage: _______________

QUESTION 4 — FAILURE TOLERANCE
What happens when the AI is wrong?
Consequence: [ ] Trivial [ ] Annoying [ ] Costly [ ] Dangerous
Acceptable? [ ] Yes [ ] No (if no, need human-in-the-loop)

QUESTION 5 — LATENCY
What latency can the user tolerate for this job?
User tolerance: ___ seconds
Expected model latency: ___ seconds
Gap: _______________

QUESTION 6 — MOAT
Does AI create a defensible advantage, or is this table stakes?
[ ] Defensible — hard to replicate, data flywheel, unique training
[ ] Commoditized — any team with API access could build this
[ ] Unclear

FEASIBILITY VERDICT:
[ ] Green — Build with AI
[ ] Yellow — Build with AI but de-risk these concerns: _______________
[ ] Red — AI is not the right solution; revisit problem framing
```

---

## Problem Statement Formats

### Format 1: The Classic HMW (How Might We)

```
How might we [help/enable] [user] to [achieve goal] 
[in context] [without/despite constraint]?
```

### Format 2: The Outcome-First Statement

```
We believe that [user] in [situation] needs to [goal].
Today they [current behavior/workaround].
This costs them [time/money/emotional toll].

We'll know we've solved it when [measurable outcome changes].
```

### Format 3: The AI Problem Statement

```
[User] today struggles to [task/goal] because [root cause].
AI makes this newly solvable because [capability that didn't exist before or at scale].

A solution would let [user] achieve [outcome] 
in [time/effort] instead of [current time/effort],
with [quality level] they can trust.

We'll measure success by: [metric 1] and [metric 2].
```

### Format 4: The Opportunity Statement (for roadmap)

```
OPPORTUNITY: [Short title]

USER NEED: [1 sentence — the job to be done]

CURRENT STATE: [How users solve this today; what's broken]

AI-ENABLED FUTURE STATE: [What becomes possible with AI]

BUSINESS VALUE: [Why this matters for growth/retention/revenue]

ESTIMATED SIZE: [How many users, how often, how much impact]

CONFIDENCE LEVEL: [ ] Validated  [ ] Hypothesized  [ ] Speculative
```

---

## From Problem to Bets

Once the problem is framed, convert it to product bets for the roadmap.

### The Bet Framework

```
## Product Bet: [Name]

PROBLEM (from framing):
_______________________________________________

BET STATEMENT:
"We believe that [action we'll take] 
will result in [outcome we expect] 
for [user] 
because [our reasoning / evidence]."

ASSUMPTIONS (what must be true for this bet to work):
1. _______________
2. _______________
3. _______________

HOW WE'LL TEST IT:
Experiment: _______________
Timeline: _______________
Sample size: _______________

SUCCESS SIGNAL:
[ ] Strong signal: _______________
[ ] Weak signal: _______________
[ ] Failure signal: _______________

BET OWNER: _______________
Review Date: _______________
```

---

## Templates

### Problem Framing Workshop Agenda (2 hours)

```
## Problem Framing Workshop — [Topic]
Date: _______________  |  Facilitator: _______________
Team: PM, Design, Engineering, Data Science, Customer Success

00:00 — OPENING (10 min)
Context setting — why are we here? What triggered this work?

00:10 — SYMPTOM SHARING (20 min)
Each person shares: "The symptom I see is ___. The data behind it is ___."
Document on shared whiteboard.

00:30 — 5 WHYS (20 min)
Pick the top symptom. Run 5 Whys as a group.

00:50 — REFRAMING (20 min)
5 reframes of the problem statement. Vote on best framing.

01:10 — AI FEASIBILITY FILTER (20 min)
Run the filter together. Document answers.

01:30 — PROBLEM STATEMENT DRAFT (20 min)
Write 3 candidate problem statements. Vote on best.

01:50 — NEXT STEPS (10 min)
Assign: Who validates this problem with users?
When: _______________
How: _______________
```

### Problem Framing One-Pager

```
## Problem Framing: [Product/Feature Name]
Version: ___  |  Date: ___  |  Owner: ___

SYMPTOM
What are we seeing that triggered this? _______________

ROOT CAUSE
What's really causing this? _______________

PROBLEM STATEMENT
[Use Format 3 from above]

AI FEASIBILITY
[ ] Data available  [ ] Accuracy achievable  [ ] Latency acceptable
[ ] Failure tolerance manageable  [ ] Clear advantage over alternatives

BETS
1. _______________
2. _______________

WHAT WE DON'T KNOW YET
- _______________
- _______________

WHO VALIDATES THIS
User research owner: ___ | Timeline: ___
```

---

## Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Starting with a solution ("We should build an AI chatbot") | Start with the problem; let the solution follow |
| Framing the problem as a feature request | Restate feature requests as problems: "What is this feature trying to solve?" |
| Skipping the AI feasibility filter | AI is not always the right tool; validate before building |
| Problem statements without success criteria | Every problem statement must include how you'll know it's solved |
| Solving interesting problems instead of important ones | Prioritize by impact on users, not technical interest |
| Single-framing the problem | Always reframe at least 3–5 ways; the first framing is rarely the best |

---

*Part of the [AI Product Builder Playbook](../README.md)*
