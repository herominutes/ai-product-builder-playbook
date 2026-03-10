# 🧑‍💻 Human-Centered Design — AI Product Builder Playbook

> **Keeping humans in control, informed, and empowered when building AI-powered products**

---

## Table of Contents

- [Overview](#overview)
- [HCD Principles for AI Products](#hcd-principles-for-ai-products)
- [The HCD Research Stack](#the-hcd-research-stack)
- [Designing for Human-AI Collaboration](#designing-for-human-ai-collaboration)
- [Trust-Centered Design Framework](#trust-centered-design-framework)
- [Transparency & Explainability Patterns](#transparency--explainability-patterns)
- [Inclusive AI Design](#inclusive-ai-design)
- [The HCD Review Checklist](#the-hcd-review-checklist)
- [Templates](#templates)
- [Anti-Patterns](#anti-patterns)

---

## Overview

Human-Centered Design (HCD) for AI products extends beyond traditional usability. When a system can act autonomously, make consequential decisions, and produce outputs users didn't explicitly request, the designer's responsibility deepens significantly.

The goal is not just to make AI easy to use — it's to make AI **trustworthy, legible, correctable, and equitable**.

> **Core Principle:** Design for the person, not the model. The AI is the means; human empowerment is the end.

---

## HCD Principles for AI Products

| # | Principle | What It Means in Practice |
|---|---|---|
| 1 | **Human in the loop** | Users can always review, override, and correct AI decisions |
| 2 | **Legibility** | Users understand what the AI is doing and why |
| 3 | **Graceful degradation** | When AI fails, the human experience degrades gracefully, not catastrophically |
| 4 | **Appropriate trust** | Design to calibrate trust accurately — neither overclaiming nor under-delivering |
| 5 | **Equitable outcomes** | AI outputs must not discriminate; reviews include bias audits |
| 6 | **User agency** | Users control how much AI involvement they want at every step |

---

## The HCD Research Stack

### Layer 1: Understanding the Human

| Method | What You Learn | When to Use |
|---|---|---|
| Contextual inquiry | How users actually work in their environment | Before any AI feature design |
| Diary studies | How AI fits into daily workflow over time | For ongoing / embedded AI features |
| Mental model interviews | What users think AI can and cannot do | Before designing autonomy features |
| Shadowing | Real-time observation of AI-assisted workflows | For enterprise / professional users |

### Layer 2: Understanding the AI-Human Interaction

| Method | What You Learn | When to Use |
|---|---|---|
| Think-aloud sessions | User comprehension of AI outputs in real time | Prototype and live feature testing |
| Error reaction testing | How users respond when AI is wrong | Before shipping any autonomous feature |
| Trust calibration surveys | Whether user trust matches actual AI accuracy | Ongoing, every major release |
| Task replay analysis | Where AI helps vs. hinders task completion | Post-launch with session recording tools |

### Layer 3: Systemic Understanding

| Method | What You Learn | When to Use |
|---|---|---|
| Stakeholder mapping | Who else is affected by the AI beyond the direct user | Before product launch |
| Harm scenario workshops | Potential negative consequences of the AI system | Before any AI feature ships |
| Accessibility audit | Whether AI outputs work for users with disabilities | Every release |
| Bias impact assessment | Whether outputs differ by user demographic | Quarterly or at model update |

---

## Designing for Human-AI Collaboration

### The Collaboration Spectrum

Place every AI feature at the right point:

```
HUMAN-LED <----------------------------------------> AI-LED

  INFORM      SUGGEST      ASSIST     DELEGATE    AUTOMATE

  Human       Human        Human      AI acts,    AI acts
  decides,    decides,     reviews,   human       fully
  AI informs  AI suggests  AI runs    verifies    autonomously
```

> **Rule:** Never design for a higher autonomy level than your trust data supports. Start left; move right only with evidence.

### Core Collaboration Patterns

#### Pattern 1: Suggest & Accept (for writing, code, recommendations)

```
User action → AI suggests inline → User accepts / edits / dismisses
```

Design requirements:
- Suggestion visually distinct from user content
- Accept, edit, dismiss are single-action operations
- AI does not re-suggest immediately after dismissal

#### Pattern 2: Draft & Review (for documents, emails, reports)

```
User provides intent → AI generates draft → User reviews → Accepts / Edits / Regenerates / Discards
```

Design requirements:
- Regenerate should accept a reason field ("make it shorter")
- User's original intent preserved and visible throughout
- Diff view available for complex documents

#### Pattern 3: Act & Confirm (for agents, automation, multi-step tasks)

```
User sets goal → AI plans → User approves plan → AI executes → User reviews result → Undo available
```

Design requirements:
- Plan shown in plain language, not technical terms
- Destructive actions (delete, send, purchase) require explicit step-by-step confirmation
- Undo available for minimum 60 seconds post-execution

#### Pattern 4: Monitor & Alert (for anomaly detection, risk flagging)

```
AI monitors → Threshold crossed → Alert surfaces → User investigates → User acts
```

Design requirements:
- Alerts include explanation ("This was flagged because...")
- False positive reporting is 1-click
- Alert frequency is user-configurable

---

## Trust-Centered Design Framework

### The Trust Calibration Model

```
                    ACTUAL AI ACCURACY
                    Low            High
                 +--------------+--------------+
   High           | OVER-TRUST   | APPROPRIATE  |
USER             | (Dangerous)  | TRUST        |
TRUST            +--------------+--------------+
   Low            | APPROPRIATE  | UNDER-TRUST  |
                 | DISTRUST     | (Missed      |
                 | (Careful)    |  Value)       |
                 +--------------+--------------+
```

**Over-trust:** User relies on AI that is wrong. Most dangerous — add uncertainty signals, prompt verification for high-stakes actions.

**Under-trust:** User ignores AI that is right. Missed value — show accuracy track record, provide comparisons.

### Trust-Building Design Patterns

| Pattern | Implementation |
|---|---|
| **Confidence indicator** | High / Medium / Low or percentage displayed near output |
| **Source citation** | Link to data or reasoning behind the output |
| **Track record** | "This AI has been accurate 94% of the time on this task" |
| **Audit trail** | Show what the AI did step by step |
| **Graceful correction** | Easy to fix AI errors, no friction, no dead ends |
| **Progressive autonomy** | Start with suggestions; earn higher autonomy over time |

---

## Transparency & Explainability Patterns

### Levels of Explainability

| Level | What It Looks Like | When to Use |
|---|---|---|
| **0 — None** | No explanation | Very low stakes, very high confidence |
| **1 — Label** | "AI-generated" badge | Default for all AI content |
| **2 — Summary** | "Based on your last 30 orders..." | Medium-stakes recommendations |
| **3 — Reasons** | Bulleted list of contributing factors | High-stakes decisions |
| **4 — Full trace** | Step-by-step reasoning chain | Expert users, regulated industries |

### Disclosure Pattern Library

```
Pattern A — Subtle label:
[✨ AI-generated]  content here

Pattern B — Attribution sentence:
This summary was generated by AI based on your uploaded document.

Pattern C — Confidence + label:
[AI suggestion — 87% confidence]

Pattern D — Expandable explanation:
AI generated this. [Why?] ↓
  └── Based on: your past preferences, current trends, and 3 similar users
```

---

## Inclusive AI Design

### Accessibility Checklist

- [ ] AI-generated text meets WCAG AA contrast standards
- [ ] AI actions triggerable by keyboard, not just mouse/touch
- [ ] Loading states communicate to screen readers (aria-live)
- [ ] AI error messages are descriptive, not just "Error"
- [ ] AI-generated images have alt text
- [ ] Long AI outputs are structured (headings, not walls of text)
- [ ] Users can opt out of AI features without losing core product access

### Bias Review Checklist

```
## Bias Review: [Feature Name]

1. What demographic groups could be affected by this AI output?
   _______________

2. Have we tested outputs across different user demographics?
   [ ] Gender  [ ] Race/ethnicity  [ ] Age  [ ] Language  [ ] Geography

3. Are there cases where AI produces worse outcomes for certain groups?
   _______________

4. How do users report biased outputs?
   _______________

5. Sign-off: ML Lead ___ | Legal ___ | PM ___
```

---

## The HCD Review Checklist

### Research
- [ ] Spoken with at least 8 users from the target persona
- [ ] Observed real usage (not just interviews) for this use case
- [ ] Understand users' existing mental model of AI for this task

### Design
- [ ] AI outputs clearly labeled as AI-generated
- [ ] Users can review AI output before it takes consequential effect
- [ ] Users can correct or reject AI output with minimal friction
- [ ] Confidence levels communicated appropriately
- [ ] Error state designed (not just the success state)
- [ ] Loading/latency state designed
- [ ] Progressive disclosure used for explanations

### Trust
- [ ] We are not overclaiming AI accuracy in copy or design
- [ ] Plan exists for what happens when the model degrades
- [ ] Feedback mechanism exists for users to report bad outputs

### Inclusion
- [ ] Accessibility review completed
- [ ] Bias impact assessment completed
- [ ] Opt-out path clearly communicated

---

## Templates

### HCD Feature Brief

```
## HCD Feature Brief: [Feature Name]
Date: ___ | PM: ___ | Design Lead: ___

USER NEED
Who: _______________
Job to be done: _______________
Current pain: _______________

AI ROLE
Autonomy level: [Inform / Suggest / Assist / Delegate / Automate]
What AI does: _______________
What human does: _______________
What happens if AI is wrong: _______________

TRUST DESIGN
How we communicate confidence: _______________
How users correct AI: _______________
How we label AI-generated content: _______________

SUCCESS CRITERIA
Primary metric: _______________
Trust metric: _______________
Accessibility: Passing WCAG AA by _______________
Bias review: Completed by _______________
```

---

## Anti-Patterns

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| "The AI knows best" — hiding outputs from user review | Always surface outputs before consequential actions are taken |
| Designing only for expert users | AI features must work for the full user spectrum, including low AI literacy |
| No error state designed | Every AI feature has three states: success, error, and loading |
| AI disclosure in fine print | AI disclosure should be clear and prominent |
| Designing to maximize trust | Design to calibrate trust accurately — high trust in bad AI is dangerous |
| Testing only with internal team | Internal teams are over-calibrated; always test with external users |

---

*Part of the [AI Product Builder Playbook](../README.md)*
