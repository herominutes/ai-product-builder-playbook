# 🔧 Jobs To Be Done — AI Product Builder Playbook

> **Using JTBD theory to discover why users really hire AI products — and how to build ones they keep**

---

## Table of Contents

- [Overview](#overview)
- [JTBD Core Theory (AI Edition)](#jtbd-core-theory-ai-edition)
- [The Three Types of Jobs in AI Products](#the-three-types-of-jobs-in-ai-products)
- [JTBD Discovery Process](#jtbd-discovery-process)
- [Writing AI Job Stories](#writing-ai-job-stories)
- [The Competing Forces Diagram](#the-competing-forces-diagram)
- [JTBD to Product Decisions](#jtbd-to-product-decisions)
- [Templates](#templates)
- [Anti-Patterns](#anti-patterns)

---

## Overview

Jobs To Be Done (JTBD) is the most powerful framework for understanding why users adopt — and abandon — AI products. Users don't hire AI because it's impressive. They hire it when it does a job better than the alternative. Understanding *that job precisely* is the difference between a product that sticks and one that churns.

> **Core Principle:** Users don't want AI. They want progress. AI is the mechanism — the job is the goal.

---

## JTBD Core Theory (AI Edition)

### The Foundational Statement

> "When [situation], I want to [motivation], so I can [expected outcome]."

In AI products, there is often a **second layer**: the user wants to achieve the outcome *without the cost or risk* of doing it themselves. This is the AI value proposition.

```
When [situation],
I want to [job — the progress I'm trying to make],
So I can [outcome — what success looks like],
Without [the friction, risk, or cost I face today],
And I can trust the AI to [AI-specific expectation].
```

### Why JTBD Matters More for AI Products

AI products face a unique adoption challenge:

1. **The job existed before the AI** — users have an established way of doing it
2. **The AI must be hired away from** the current solution (their own effort, a human, a tool)
3. **The switch cost includes trust** — not just time/money, but willingness to rely on something uncertain
4. **The job has emotional and social dimensions** — users care how they feel and how they appear

---

## The Three Types of Jobs in AI Products

### Functional Jobs

The practical task the user needs to accomplish.

Examples:
- "Write a first draft of this email"
- "Find the answer buried in this 200-page report"
- "Generate 10 ad variations for A/B testing"
- "Identify anomalies in my dataset"

**How AI competes:** Speed, scale, availability (24/7), accuracy at scale.

### Emotional Jobs

How users want to feel while doing the task or after completing it.

Examples:
- "Feel confident that my work is high quality"
- "Feel less overwhelmed by the volume of work"
- "Feel like I'm keeping up with my more tech-savvy peers"
- "Feel in control, not replaced"

**How AI can fail:** If AI makes users feel dumb, exposed, or replaced — they churn even if the output is good.

### Social Jobs

How users want to be perceived by others as a result of using the product.

Examples:
- "Look like the person on the team who finds the best tools"
- "Be seen as productive and on top of things"
- "Demonstrate that I adopt AI responsibly"

**Design implication:** Give users ways to attribute, share, and show their AI-assisted work in ways that preserve their professional identity.

---

## JTBD Discovery Process

### Step 1: Recruit the Right Interview Subjects

JTBD research works best with **recent switchers** — people who recently adopted or abandoned a similar AI solution. Their memory of the switch decision is freshest.

Target mix:
- 40% — Users who recently adopted your product
- 30% — Users who recently churned from your product
- 30% — Users currently using a competitive AI solution

### Step 2: The JTBD Interview Guide

**Core structure: Timeline Interview**

```
## JTBD Interview Guide

OPENING
"I want to understand your experience adopting [product]. 
I'm not looking for feature feedback — I want to understand 
the story of how you decided to use it."

THE TIMELINE (work backward chronologically)
1. "When did you first start using [product]?"
2. "What were you doing before that? What was your old solution?"
3. "When did you first think, 'I need something different'? 
   What was happening at that moment?"
4. "Walk me through how you found [product]."
5. "What almost stopped you from trying it?"
6. "When did you first feel like it was actually working for you?"
7. "Is there a moment you almost gave up on it? What happened?"
8. "What would have to change for you to stop using it?"

EMOTIONAL PROBES (use these throughout)
- "How did that make you feel?"
- "What were you worried about?"
- "What were you hoping would happen?"
- "What did you tell your [colleague / manager / partner] about it?"

AI-SPECIFIC PROBES
- "When the AI was wrong, what did you do?"
- "Do you check the AI's work? When do you trust it without checking?"
- "Has the AI ever surprised you? Positively or negatively?"
- "Do you feel like the AI makes you look better or worse at your job?"
```

### Step 3: Synthesize Job Statements

From interview notes, extract:

```
## Job Extraction Template

Interview Subject: _______________  |  Date: _______________

FUNCTIONAL JOB
"When [trigger/situation], they need to [functional task]"
Example: _______________

EMOTIONAL JOB
"They want to feel [emotion] while/after doing this"
Example: _______________

SOCIAL JOB
"They want to be seen as [identity] by [audience]"
Example: _______________

CURRENT SOLUTION (what they're firing)
What: _______________
Why they're dissatisfied: _______________

SWITCHING TRIGGER
"The moment that pushed them to look for something new:"
_______________

ANXIETIES ABOUT AI
"What almost stopped them from switching:"
_______________
```

---

## Writing AI Job Stories

### The AI Job Story Format

Different from standard user stories. Job stories focus on situation and motivation, not persona and feature.

**Standard format:**

```
When [situation / trigger],
I want to [job / motivation],
So I can [expected outcome].

AI expectation: I trust the AI to [specific AI behavior],
and I can [what I retain control over].
```

**Examples:**

```
EXAMPLE 1 — Writing Assistant
When I have a client email to send but I'm stuck on how to phrase 
a difficult message,
I want to get a confident, professional first draft instantly,
So I can send it today without spending 45 minutes agonizing.

AI expectation: I trust the AI to match my tone and get the 
professional context right, and I can review and edit before sending.

---

EXAMPLE 2 — Research / Summarization
When I get handed a 150-page industry report before a board meeting,
I want to extract the 5 most relevant findings for my agenda,
So I can walk into the meeting fully prepared without reading the 
whole document.

AI expectation: I trust the AI to surface what's most relevant to 
my context, and I can drill into sources if I need to verify.

---

EXAMPLE 3 — Code Generation
When I'm building a feature and I hit a function I know exists 
but can't remember the implementation,
I want to get working code that I can drop in and test,
So I can keep my flow state and not spend 20 minutes searching Stack Overflow.

AI expectation: I trust the AI to produce syntactically correct 
code, and I will review it before committing.
```

---

## The Competing Forces Diagram

Use this to understand what pulls users toward and away from your AI product.

```
## Competing Forces: [Product Name]

PUSH (dissatisfaction with current solution)          PULL (attraction to AI solution)
"I'm frustrated because..."                           "I imagine this will..."
________________________________                      ________________________________
________________________________                      ________________________________
________________________________                      ________________________________

        CURRENT SOLUTION ←——— USER ———→ YOUR AI PRODUCT

ANXIETIES (what holds them back)                      HABITS (what they're used to)
"I'm worried that..."                                 "I'm comfortable with..."
________________________________                      ________________________________
________________________________                      ________________________________
________________________________                      ________________________________
```

**How to use this:**
- **Push + Pull** = Where to focus acquisition messaging
- **Anxieties** = What onboarding and UX must address directly
- **Habits** = What existing workflows the AI must accommodate or replace

---

## JTBD to Product Decisions

### Mapping Jobs to Features

For each major product feature, trace it back to a job:

```
## Feature-Job Mapping

| Feature | Functional Job | Emotional Job | Social Job | Evidence |
|---------|---------------|--------------|------------|----------|
|         |               |              |            |          |
|         |               |              |            |          |
```

**Rule:** If you can't trace a feature to a job, it's a feature looking for a problem. De-prioritize.

### Job-Driven Prioritization

Score each opportunity by job strength:

```
## Job-Driven Prioritization

| Opportunity | Job Frequency | Job Importance | AI Advantage | Priority |
|-------------|--------------|----------------|--------------|----------|
|             | How often is | How painful is | Does AI do   |          |
|             | this job?    | the current    | this much    |          |
|             | (1-5)        | solution? (1-5)| better? (1-5)|          |
```

**Formula:** Frequency × Importance × AI Advantage = Priority Score

### Jobs as Retention Anchors

Identify which jobs are "anchor jobs" — the ones users cannot do without your product. These predict retention:

```
## Retention Anchor Jobs

Core Anchor (the job that keeps them):
_______________

Secondary Jobs (nice to have):
_______________

At-Risk Jobs (competitor could take these):
_______________

Unserved Jobs (adjacent jobs we could win):
_______________
```

---

## Templates

### JTBD Research Plan

```
## JTBD Research Plan: [Product / Feature]

Objective: Understand the job users are hiring [product] to do.

PARTICIPANT RECRUITMENT
- N recent adopters: ___
- N recent churns: ___
- N competitor users: ___

INTERVIEW SCHEDULE
- Duration: 45 minutes each
- Format: Video call, recorded with consent
- Interviewer: _______________

SYNTHESIS APPROACH
- Job statement extraction after each interview
- Affinity mapping of jobs after all interviews
- Competing forces diagram per segment

DELIVERABLES
- [ ] Job statement library (top 5–10 jobs)
- [ ] Competing forces diagram (per key persona)
- [ ] Feature-job mapping update
- [ ] Top 3 product recommendations from findings

TIMELINE
Research complete: _______________
Synthesis complete: _______________
Readout to team: _______________
```

### Quick Job Discovery (for time-constrained teams)

When you can't run full interviews, use this fast alternative:

```
## Quick Job Survey (5 questions, in-product)

1. "What were you trying to do when you first used [feature]?" (Open text)
2. "What were you using before?" (Open text)
3. "What almost stopped you from trying it?" (Open text)
4. "What would have to happen for you to stop using it?" (Open text)
5. "If you described this to a colleague, what would you say it does?" (Open text)
```

Run this with 20+ users. Synthesize into job statements manually.

---

## Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Building features before identifying the job | Run JTBD discovery first; build to serve confirmed jobs |
| Conflating job with use case | A use case is what users do; a job is why they do it — go deeper |
| Only asking what users want | Users can't tell you what to build; they can tell you what they're trying to accomplish |
| Ignoring emotional and social jobs | Users churn for emotional reasons even when the functional job is done well |
| Writing job stories about AI features | Write job stories about human goals; AI is how you fulfill them |
| Assuming the job is obvious | The most dangerous assumption in product — always validate |

---

*Part of the [AI Product Builder Playbook](../README.md)*
