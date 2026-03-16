# 🔭 Product Vision Narrative — AI Product Builder Playbook

> **Framework for crafting and communicating a compelling product vision that aligns teams, inspires execution, and attracts the right stakeholders**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Vision Narrative Model](#the-vision-narrative-model)
- [Phase 1: World Today](#phase-1-world-today)
- [Phase 2: The Problem](#phase-2-the-problem)
- [Phase 3: The Opportunity](#phase-3-the-opportunity)
- [Phase 4: The Product Vision](#phase-4-the-product-vision)
- [Phase 5: The Future State](#phase-5-the-future-state)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A Product Vision Narrative is not a mission statement. It is not a roadmap. It is the **story of why this product must exist** — told in a way that makes engineers want to build it, executives want to fund it, and users feel understood by it.

> **Core Principle:** Vision is not what you are building. It is the change in the world your product is fighting for. If your vision could belong to any company, it is not specific enough.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting a new product or major initiative | 🔴 Critical — before any roadmap work |
| Team alignment is breaking down | 🔴 Critical — reanchor to shared direction |
| Preparing for a board or investor presentation | 🟠 High |
| Onboarding a new senior hire or exec stakeholder | 🟠 High |
| Kicking off annual planning or strategy cycle | 🟡 Medium |
| Product has drifted from its original intent | 🟡 Medium |

---

## The Vision Narrative Model

Every compelling product vision follows a five-part arc:

```
WORLD TODAY → PROBLEM → OPPORTUNITY → VISION → FUTURE STATE
```

| Stage | Core Question | Common Mistake |
|---|---|---|
| **World Today** | What is true right now? | Starting with your product, not the world |
| **Problem** | Who is suffering and why? | Describing symptoms instead of root causes |
| **Opportunity** | Why is now the right moment? | Ignoring what has changed to make this possible |
| **Vision** | What will we build? | Writing a feature list instead of a destination |
| **Future State** | What does winning look like for the user? | Focusing on company outcomes, not user transformation |

---

## Phase 1: World Today

### 1.1 Context Setting

Ground the narrative in observable, specific reality. Avoid generic statements. The best World Today descriptions cite a tension — something that used to work but no longer does, or a new capability that has made old approaches obsolete.

**Strong example:**
> "Knowledge workers spend an average of 4.5 hours per day searching for, synthesising, and reformatting information — across tools that were designed before AI existed and have not been rebuilt since."

**Weak example:**
> "Users struggle with fragmented workflows and limited access to information."

### 1.2 World Today Diagnostic

Run this as a team exercise before writing. Answer each question with evidence:

```
WORLD TODAY CANVAS

1. What does our user's day look like before they use our product?
   ________________________________________________________________

2. What workaround are they using today? (There is always a workaround.)
   ________________________________________________________________

3. What does that cost them? (Time / money / quality / opportunity)
   ________________________________________________________________

4. What has changed in the last 2–3 years that makes this worse?
   ________________________________________________________________

5. What specific data point best illustrates the scale of this problem?
   ________________________________________________________________
```

---

## Phase 2: The Problem

### 2.1 Problem Framing

A well-framed problem statement has three components: **who** is affected, **what** they cannot do, and **why** it matters at a systems level.

| Component | Question to Answer |
|---|---|
| **Who** | Which specific user, in which specific context? |
| **What** | What outcome are they failing to achieve? |
| **Why it matters** | What downstream consequence does this create? |

### 2.2 Problem Depth Test

Before locking in your problem statement, pressure-test it:

```
PROBLEM DEPTH CHECKLIST

[ ] Is this a problem our specific user has — or a problem in general?
[ ] Can we point to evidence (data, interviews, support tickets)?
[ ] Is this the root cause or a symptom of something deeper?
[ ] Would our user describe this as a real problem in their own words?
[ ] Is this problem urgent enough to make someone change their behaviour?
```

> **Rule of thumb:** If your user has lived with this problem for years without urgently seeking a solution, you need to go one level deeper to find the real friction.

---

## Phase 3: The Opportunity

### 3.1 Why Now

The opportunity section answers the question every skeptic will ask: **"If this is such a clear problem, why hasn't it been solved?"** Your answer defines the strategic window.

| Opportunity Driver | Description | Example |
|---|---|---|
| **Technology shift** | A new capability now makes the solution possible | LLMs enabling natural language interfaces |
| **Behaviour shift** | Users are ready to adopt what wasn't acceptable before | Remote-first teams normalising async work |
| **Market shift** | Competitive or regulatory change creates an opening | Incumbent failure to adopt AI creates switching intent |
| **Cost shift** | Something that was expensive is now cheap | API costs dropping 10x enabling new use cases |
| **Distribution shift** | A new channel makes reaching users viable | Mobile-first penetration in emerging markets |

### 3.2 Opportunity Framing Template

```
## Why Now

The problem has existed for [X years / always].

What has changed:
1. [Technology / behaviour / market shift] means that [new capability or condition].
2. [Second driver] has made [old blocker] no longer a constraint.

The window:
This creates a [12–18 / 24–36] month window before [the market catches up / 
incumbents respond / the behaviour normalises].

Our advantage:
We are uniquely positioned because [specific reason — not generic].
```

---

## Phase 4: The Product Vision

### 4.1 Vision Statement Anatomy

A strong vision statement is **specific, directional, and time-bound**. It describes a state of the world — not a product feature.

```
Vision Formula:

For [specific user]
Who currently [struggle with / cannot / spend too much time on]
[Product name] is [category]
That [does something meaningfully different]
Unlike [current alternative]
Our product [key differentiator tied to the opportunity]
```

### 4.2 Vision Quality Rubric

Score your vision statement before presenting it:

| Criterion | 0 — Fails | 1 — Partial | 2 — Strong |
|---|---|---|---|
| **Specific user** | Any user / everyone | Named segment | Named segment in named context |
| **Clear destination** | Vague aspiration | General direction | Measurable future state |
| **Differentiated** | Could be any product | Hints at difference | Unmistakably ours |
| **Emotionally resonant** | Flat / corporate | Interesting | Makes someone want to build it |
| **Bounded** | Unlimited scope | Loosely scoped | Clear what is NOT included |

**Target score: 8–10. Do not present a vision below 6.**

### 4.3 Vision Stress Test

Before socialising your vision, run it through these questions with a skeptic:

```
VISION STRESS TEST

1. "So what you're saying is..." — Can someone restate it accurately in one sentence?
2. "Why not just use [obvious alternative]?" — Is the differentiation clear?
3. "What does success look like in 3 years?" — Is the destination concrete?
4. "What are you explicitly NOT doing?" — Are the boundaries clear?
5. "Who else could build this?" — Is the unique advantage obvious?
```

---

## Phase 5: The Future State

### 5.1 The User Transformation

The Future State is told from the **user's perspective**, not the company's. It describes a day-in-the-life **after** your product has worked — not the product itself.

**Strong example:**
> "A recovery coach working with 50 athletes can now generate personalised weekly programs, track adherence in real time, and surface injury risk signals before a problem develops — without adding a single hour to their workload. Athletes recover 30% faster. The coach takes on more clients. The practice grows."

**Weak example:**
> "Our platform enables coaches to manage athletes more efficiently using AI-powered recommendations."

### 5.2 Future State Narrative Canvas

```
FUTURE STATE CANVAS

Write this from the user's point of view, in plain language:

BEFORE (today):
"Every day I have to [painful task]. It takes [time/effort] and I still 
end up with [unsatisfactory outcome]. The cost of this is [consequence]."

AFTER (with your product):
"Now I can [new capability]. What used to take [old time] takes [new time].
I can finally [thing they couldn't do before]. This means [downstream impact
on their work/life/business]."

The metric that proves it:
[One number that shows the transformation is real]
```

---

## Templates

### Template A: Full Vision Narrative (for exec or board presentation)

```
# [Product Name] — Vision Narrative
Date: ___  |  Author: ___  |  Version: ___

## The World Today
[2–3 sentences grounded in observable reality, with one data point]

## The Problem
[1–2 sentences: who, what, why it matters]

## Why Now
[2–3 sentences: what has changed, what window this creates]

## Our Vision
[1 clear vision statement using the formula above]

## What Success Looks Like
[3–5 sentences from the user's perspective, after the product has worked]

## What We Are Not Building
[2–3 explicit boundaries — what this product will not do]

## The Metric That Proves We Won
[One north star metric tied to the user transformation]
```

### Template B: One-Sentence Vision Card (for team alignment)

```
## Vision Card — [Product Name]

We believe that [specific user] should be able to [transformed capability].

Today they [current painful reality].

We will change this by [product approach].

We will know we have succeeded when [measurable outcome].
```

### Template C: Sprint Story Card from Vision Finding

```
## Vision-Aligned Story

Vision connection: [Which part of the vision does this story serve?]

As a [persona at their current stage]
I want to [action]
So that [outcome tied to the future state]

Vision check:
[ ] Does this story move the user closer to the future state?
[ ] Does this story stay within the product boundaries?
[ ] Does this story address a root cause, not a symptom?

Success metric:
[How will we know this story delivered on the vision?]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Writing vision by committee | One author, broad input, single decision-maker |
| Confusing vision with roadmap | Vision = destination; roadmap = route |
| Using aspirational language without specifics | Ground every claim in evidence or a testable assumption |
| Making it about the product instead of the user | Start and end with the user's transformation |
| Setting a vision too broad to make tradeoffs | Add explicit "what we are not building" boundaries |
| Treating vision as a one-time exercise | Revisit every 6 months; update when the opportunity changes |
| Building to a vision no one has tested | Run the stress test with a skeptic before socialising |

---

## Cadence

| Review Type | Frequency | Trigger |
|---|---|---|
| Vision check | Every sprint planning | Does this sprint serve the vision? |
| Narrative refresh | Every 6 months | Strategy or market shift |
| Full rewrite | Annually or on major pivot | Fundamental change in user, problem, or opportunity |
| Emergency reset | As needed | Team alignment breaks down |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Full Vision Narrative from Scratch

> **Best for:** Starting a new product, preparing for a board presentation, or realigning a team around a shared direction.

```
You are an expert product strategist helping me craft a compelling Product Vision Narrative.

Use the five-part structure below to guide me through building a complete vision narrative for my product. Ask me one section at a time. After I answer each section, reflect back what I said in sharpened, specific language — cutting generic phrases and replacing them with precise claims. Then move to the next section.

The five sections are:
1. World Today — what is true right now for my user (ground in a specific observation or data point)
2. The Problem — who is affected, what they cannot do, and why it matters at a systems level
3. The Opportunity — what has changed (technology, behaviour, market, cost) that makes now the right moment
4. The Product Vision — a specific, differentiated statement of the future we are building toward
5. The Future State — a day-in-the-life narrative from the user's perspective after the product has worked

Apply these quality rules throughout:
- Replace any generic language with specific, verifiable claims
- Flag any vision statement that could belong to a competitor
- Ensure the future state describes user transformation, not product features
- After completing all five sections, write a final one-paragraph vision narrative that weaves them together

My product: [describe your product in 2–3 sentences]
My target user: [describe who they are and what they do]
```

---

### Prompt 2 — Stress-Test an Existing Vision

> **Best for:** Pressure-testing a vision you already have before presenting it to leadership, investors, or the team.

```
You are a skeptical but constructive product strategy advisor. Your job is to stress-test my product vision narrative and tell me exactly where it is weak, generic, or unconvincing.

Evaluate my vision against these five criteria:
1. Specificity — Is the user described precisely, or could this apply to anyone?
2. Differentiation — Could this vision statement belong to a competitor? If so, what is missing?
3. Clarity of destination — Is there a concrete, testable future state, or is it aspirational and vague?
4. Bounded scope — Does the vision make clear what this product will NOT do?
5. Emotional resonance — Would this make an engineer want to build it, or does it read like a corporate document?

For each criterion, give it a score from 1–3:
1 = Fails, needs rewriting
2 = Partial, needs sharpening
3 = Strong, leave it

Then rewrite the weakest sections and give me an improved version of the full narrative.

My current vision narrative:
[paste your vision narrative here]
```

---

### Prompt 3 — Generate the Future State Narrative

> **Best for:** Translating a dry vision statement into a vivid, user-centred story that resonates with stakeholders.

```
You are a product storyteller. Help me write a compelling Future State narrative for my product.

The Future State describes what a user's day-in-the-life looks like AFTER my product has worked — not what the product does, but how the user's world has changed.

Structure the narrative in two parts:

BEFORE (today):
Write 3–4 sentences in the user's voice describing their current reality — the friction, the workaround, the cost.

AFTER (with the product):
Write 3–4 sentences in the user's voice describing their transformed reality — what they can now do, what is gone, what has become possible.

Then add:
- One metric that proves the transformation is real
- One quote the user might say to a colleague about the product

Rules:
- Write in plain, specific language — no corporate jargon
- Every claim in the AFTER section must connect to a real capability the product provides
- The transformation should be meaningful, not marginal

My product: [describe what it does]
My target user: [who they are, what they do day-to-day]
The core capability: [the one thing the product does better than anything else]
```

---

### Prompt 4 — Rapid Vision Alignment (Team Workshop)

> **Best for:** Running a 30–60 minute team alignment session where multiple people have different views of where the product is going.

```
You are a product strategy facilitator running a team alignment session on product vision.

I will give you 3–5 different vision statements from different team members. Your job is to:

1. Identify what each statement gets right
2. Identify where they contradict each other
3. Extract the common ground — the shared beliefs about user, problem, and direction
4. Draft a single unified vision statement that incorporates the strongest elements of each
5. List the 2–3 questions the team still needs to resolve

Format your output clearly with headings for each step.

Team vision statements:
1. [Paste statement 1]
2. [Paste statement 2]
3. [Paste statement 3]
```
