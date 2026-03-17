# 📝 Decision Log — AI Product Builder Playbook

> **A framework for capturing, organising, and surfacing product decisions so that teams learn from them, avoid relitigating them, and maintain institutional knowledge across team changes**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Decision Log Model](#the-decision-log-model)
- [What to Log](#what-to-log)
- [Decision Entry Format](#decision-entry-format)
- [Decision Categories](#decision-categories)
- [Decision Log Governance](#decision-log-governance)
- [Decision Log for AI Products](#decision-log-for-ai-products)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Every product team makes hundreds of decisions. Most of them are made once, documented nowhere, and then made again six months later when the context is lost, the team has changed, or a new stakeholder challenges the rationale. The decision log exists to break this cycle.

> **Core Principle:** A decision that is not documented will be made again. The second time, it will take longer, involve more people, and produce a less informed outcome — because the team will not know why the first decision was made, what alternatives were considered, or what evidence drove the choice.

For AI products, the decision log carries additional weight. AI product decisions — model selection, architecture choices, quality thresholds, guardrail design — are often made under uncertainty, with tradeoffs that are not obvious until production. Documenting these decisions, including the uncertainty at the time, is essential for responsible AI governance and for learning as the field evolves.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Any significant product, architecture, or strategy decision | 🔴 Critical — log before or immediately after |
| A decision that involves explicit tradeoffs | 🔴 Critical — the tradeoffs must be recorded |
| A decision that will be hard to reverse | 🟠 High — high reversibility cost = high documentation value |
| A decision that multiple stakeholders disagree on | 🟠 High — document the rationale and what was not chosen |
| Onboarding a new team member who asks "why did we do X?" | 🟡 Medium — the log should answer this without human intervention |
| A prior decision is being challenged | 🟡 Medium — the log should provide the context to evaluate the challenge |

---

## The Decision Log Model

A decision log is not a meeting minutes document. It is a structured record of what was decided, why, what alternatives were considered, and how to evaluate whether the decision was correct over time.

```
DECISION IDENTIFICATION
  ↓ recognise when a decision is significant enough to log
DECISION DOCUMENTATION
  ↓ capture the context, options, rationale, and outcome
DECISION CATEGORISATION
  ↓ tag for discoverability and pattern analysis
DECISION REVIEW
  ↓ periodically evaluate whether the decision was correct
DECISION SURFACING
  ↓ route the right decision context to the right person at the right time
```

| Component | Purpose | Cadence |
|---|---|---|
| **Identification** | Recognise which decisions to log | At time of decision |
| **Documentation** | Capture while context is fresh | Within 24 hours of decision |
| **Categorisation** | Enable search and pattern analysis | At time of logging |
| **Review** | Learn from outcomes | 3–6 months post-decision |
| **Surfacing** | Prevent re-making the same decision | On trigger (new feature, new hire, challenge) |

---

## What to Log

Not every micro-decision needs a log entry. The test is: **would a new team member benefit from knowing this decision was made, and why?**

### Log These Decisions

| Decision Type | Examples | Why to Log |
|---|---|---|
| **Strategic direction** | Product positioning, target market, pricing model | High impact; long-lasting; often challenged later |
| **Architecture choices** | Model selection, RAG vs fine-tune, vector store choice | Hard to change; affects cost and quality |
| **Feature inclusion/exclusion** | What was explicitly not built and why | Prevents scope creep; explains gaps |
| **Quality thresholds** | What quality bar was set and why | Evidence of responsible AI practice |
| **Tradeoffs made** | Speed vs quality, coverage vs safety | Explicit tradeoffs need recorded rationale |
| **Rejected alternatives** | What options were considered and why they were not chosen | Prevents relitigating the same options |
| **Governance decisions** | Policy choices, compliance decisions, risk acceptance | Regulatory and accountability record |
| **Failures and pivots** | What was tried, failed, and changed | The most valuable learning category |

### Skip These

| Decision Type | Why to Skip |
|---|---|
| Micro-implementation details | Too granular; use code comments instead |
| Routine sprint prioritisation | Too frequent; use backlog + sprint notes |
| Individual task assignments | Not strategic; use project management tools |
| Stylistic preferences | Not consequential enough |

---

## Decision Entry Format

### Standard Entry

```
DECISION ENTRY

ID: [D-001] (sequential, unique)
Date: [ISO-8601]
Author: [who made or facilitated this decision]
Status: Decided / Under review / Superseded / Invalidated
Category: [see Decision Categories below]
Reversibility: Easy / Moderate / Hard / Irreversible

Decision:
[One clear sentence stating what was decided — not why, not how, just what]

Context:
[2–3 sentences: what situation prompted this decision? What problem were we solving?]

Options considered:
Option A: [describe] — Pros: ___ — Cons: ___
Option B: [describe] — Pros: ___ — Cons: ___
Option C: [describe] — Pros: ___ — Cons: ___
[If only one option was considered, this is a flag — document why alternatives were not evaluated]

Decision rationale:
[Why was Option [X] chosen over the alternatives? What evidence, principles, or constraints drove the choice?]

Key assumptions:
[What must be true for this decision to remain correct?]
1. _______________________________________________
2. _______________________________________________

Uncertainty acknowledged:
[What did we not know at the time? What could change this decision?]

Impact:
Affected teams: _______________________________________________
Affected users: _______________________________________________
Affected systems: _______________________________________________

Review trigger:
[What event or date should prompt a review of this decision?]
Date: ___ OR Event: _______________________________________________

Links:
Related PRD: _______________________________________________
Related decisions: [D-00X, D-00Y]
Evidence referenced: _______________________________________________
```

### Lightweight Entry (for lower-stakes decisions)

```
LIGHTWEIGHT DECISION ENTRY

ID: [D-001]
Date: ___
Author: ___
Category: ___
Reversibility: Easy / Moderate / Hard

Decision: [One sentence]
Rationale: [2–3 sentences — why this, not the alternative]
Alternative rejected: [What was the main alternative and why was it not chosen?]
Review trigger: ___
```

---

## Decision Categories

Tag every decision with one primary category to enable search and pattern analysis:

| Category | Description | Examples |
|---|---|---|
| **Strategy** | Direction, positioning, market, pricing | Target market selection, pricing model |
| **AI architecture** | AI-specific technical decisions | Model selection, RAG design, memory architecture |
| **Product design** | Feature design, UX, interaction design | AI interaction pattern, failure state design |
| **Quality and safety** | Quality thresholds, guardrails, governance | Minimum quality score, content filter settings |
| **Data** | Data strategy, collection, usage | Data source selection, retention policy |
| **Build vs buy** | Make-or-buy decisions | API vs self-hosted, build vs partner |
| **Tradeoff** | Explicit tradeoff decisions | Speed vs quality, coverage vs cost |
| **Organisational** | Team structure, process, governance | Team structure, review cadence |
| **Failure and pivot** | What was tried and changed | Feature that was deprioritised, approach that failed |

---

## Decision Log Governance

### 4.1 Logging Discipline

```
DECISION LOGGING STANDARDS

Timing: Log decisions within 24 hours of making them.
  After 24 hours, context starts to decay.
  After a week, the decision is often partially forgotten.
  After a month, only the outcome is remembered — not the rationale.

Completeness: Every log entry must include:
  [ ] What was decided (one sentence)
  [ ] Why (rationale with evidence)
  [ ] What was considered and rejected (alternatives)
  [ ] What assumptions underpin the decision
  [ ] When to review

Ownership: Every decision has one named author.
  The author is not necessarily the decision-maker —
  they are the person responsible for ensuring it is documented.

Review: Decisions are reviewed quarterly or on trigger.
  Review question: "Was this decision correct, given what we know now?"
```

### 4.2 Decision Review Process

```
DECISION REVIEW PROTOCOL

Trigger: Either the review date has passed OR the review event has occurred.

Review questions:
1. Were the key assumptions still valid?
2. Did the decision produce the expected outcome?
3. Do we still agree with the rationale?
4. Has anything changed that would lead to a different decision today?

Possible review outcomes:
  [ ] Confirmed — decision stands; update review date
  [ ] Updated — decision partially revised; log the update
  [ ] Superseded — a new decision replaces this one; link the new entry
  [ ] Invalidated — the decision was wrong; log the learning

Most valuable review: decisions that were wrong.
These generate the richest learning — document the failure mode and what was missed.
```

### 4.3 Decision Log as Governance Record

For AI products specifically, the decision log serves as evidence of responsible AI practice:

```
AI GOVERNANCE RECORD — DECISIONS TO FLAG

The following decision categories should be tagged for the governance record
and included in the AI risk register:

[ ] Model selection decisions (why this model, not an alternative)
[ ] Quality threshold decisions (what quality bar was set and why)
[ ] Guardrail design decisions (what was allowed and prohibited, and why)
[ ] Risk acceptance decisions (what risk was accepted and by whom)
[ ] Data handling decisions (what user data enters the AI and how)
[ ] Bias and fairness decisions (what testing was done and what was accepted)
[ ] Human oversight decisions (where human review was required vs automated)

These decisions must be:
  - Logged with full rationale (not lightweight format)
  - Reviewed at each major release
  - Available on request for compliance audit
```

---

## Decision Log for AI Products

### AI-Specific Decision Entry

AI decisions often involve higher uncertainty and higher stakes than traditional product decisions. The standard entry is extended for AI:

```
AI DECISION ENTRY

[Standard fields as above, plus:]

AI decision type:
  [ ] Model selection
  [ ] Architecture (RAG / agent / chain / fine-tune)
  [ ] Quality threshold
  [ ] Guardrail design
  [ ] Risk acceptance
  [ ] Data handling
  [ ] Human oversight level

Model / technology involved: _______________________________________________

Quality / safety evidence:
  Evaluation dataset run: Yes / No
  Quality score at time of decision: ___ / 5
  Safety evaluation passed: Yes / No / Not applicable

Risk accepted:
  Risk description: _______________________________________________
  Risk score (likelihood × impact): ___
  Accepted by: ___ (name + role)
  Reason for acceptance: _______________________________________________

Regulatory / compliance consideration:
  [ ] Legal reviewed: Yes / No / Not applicable
  [ ] Privacy assessment completed: Yes / No / Not applicable
  Notes: _______________________________________________

Post-deployment validation plan:
  How will we know if this decision was correct?
  Metric: _______________________________________________
  Review date: _______________________________________________
```

### High-Frequency AI Decisions to Log

| Decision | Why It Matters | Review Trigger |
|---|---|---|
| Which model to use | Quality/cost/latency tradeoff; changes when models evolve | New model release |
| Quality threshold for launch | Defines acceptable risk; must be evidence-based | Post-launch quality data |
| Hallucination tolerance | Risk acceptance for the domain | Any hallucination incident |
| Maximum response length | Cost and quality tradeoff | Token usage data |
| Fallback behaviour when AI fails | User experience when AI is unavailable | First production failure |
| Whether to use RAG or parametric knowledge | Architecture decision with significant cost implications | Retrieval quality data |
| Data sent to external model providers | Privacy decision | Any data handling change |

---

## Templates

### Template A: Decision Log Index

```
# Decision Log — [Product Name]
Last updated: ___  |  Total decisions: ___

## Active Decisions (current status)
| ID | Date | Category | Decision (one line) | Author | Review date |
|----|------|----------|---------------------|--------|-------------|
| D-001 | | Strategy | | | |
| D-002 | | AI architecture | | | |

## Recently Reviewed
| ID | Original date | Review date | Outcome | Learning |
|----|--------------|-------------|---------|---------|
| | | | Confirmed / Updated / Superseded / Invalidated | |

## Superseded Decisions
| ID | Original decision | Superseded by | Date | Reason |
|----|------------------|--------------|------|--------|
| | | | | |

## Search tags
[List all category tags used in this log for quick filtering]
```

### Template B: Decision Retrospective

```
# Decision Retrospective — [Decision ID]

Original decision: [restate the decision]
Original date: ___
Review date: ___

Outcome assessment:
What actually happened: _______________________________________________
What we expected to happen: _______________________________________________
Were the assumptions correct? Yes / Partially / No

If assumptions were wrong:
Which assumption failed: _______________________________________________
Why it failed: _______________________________________________
What we would do differently: _______________________________________________

Verdict: Confirmed / Updated / Superseded / Invalidated
Learning (one sentence): _______________________________________________
This learning should inform: [future decisions / team training / process change]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Logging decisions after the context has decayed | Log within 24 hours — context is the most perishable element |
| Logging only decisions that turned out well | Failures and pivots are the most valuable log entries |
| Decision log that nobody reads | Route decisions to team members when relevant; surface at onboarding |
| No alternatives documented | Always record what was considered and rejected — this is the most relitigated content |
| No review trigger | Every decision must have a review date or trigger event |
| AI decisions without risk acceptance documentation | All AI risk acceptance decisions must have a named accountable person |
| Decision log as a bureaucratic exercise | The log exists to prevent re-litigation and surface learnings — use it that way |
| No lightweight option for smaller decisions | Two-tier format: full entry for high-stakes; lightweight for others |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Log new decisions | Within 24 hours of decision | Decision author |
| Review scheduled decisions | Monthly (triggered by review date) | PM |
| Decision log audit (are we logging?) | Quarterly | PM lead |
| Failure and pivot retrospectives | After every significant failure | PM |
| AI governance record review | Quarterly | PM + Legal |
| Decision log onboarding (new hires) | First week | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Document a Product Decision

> **Best for:** Capturing a significant product decision while the context is fresh.

```
You are a product documentation specialist helping me write a clear, complete decision log entry.

Using the standard entry format, help me document this decision:

1. Clarify the decision statement — restate it as a single, unambiguous sentence
2. Reconstruct the context — what situation prompted this decision?
3. Identify all options that were or should have been considered — challenge me if I only considered one option
4. Articulate the rationale — what evidence, principles, or constraints drove the choice?
5. Surface the key assumptions — what must remain true for this decision to stay correct?
6. Name the uncertainty — what did we not know at the time?
7. Set the review trigger — when should this decision be revisited?

After the entry:
- Flag any element of the decision that might be challenged later and pre-empt it with documentation
- Identify if this decision has AI-specific governance implications (should it be in the AI governance record?)
- Suggest related decisions that should be linked

Decision I am documenting: [describe what was decided and the general context]
Stakeholders involved: [who was in the room or consulted?]
My best recollection of the rationale: [describe]
Alternatives I know were considered: [list]
```

---

### Prompt 2 — Reconstruct and Document a Past Decision

> **Best for:** When a decision was made in the past without documentation and needs to be reconstructed before it is challenged or revisited.

```
You are a product historian helping me reconstruct and document a product decision that was made without a formal log entry.

Based on the information I provide, help me:

1. Reconstruct the probable decision statement (what was actually decided)
2. Infer the likely context (what was happening that prompted this decision?)
3. Identify the alternatives that were probably considered given the context
4. Reconstruct the probable rationale based on what I know
5. Flag: which elements of this reconstruction are uncertain vs confirmed?
6. Write the log entry with appropriate uncertainty flagging

After the reconstruction:
- Identify what I should verify with people who were present
- Identify what the implications are if the reconstructed rationale is wrong
- Recommend whether this decision should be reviewed given current context

What I know about the decision:
  What was decided: _______________________________________________
  Approximate date: _______________________________________________
  People involved: _______________________________________________
  Context at the time: _______________________________________________
  What I don't know: _______________________________________________
```

---

### Prompt 3 — Review a Decision Log Entry

> **Best for:** Periodically reviewing a past decision to determine whether it was correct and whether it should be updated.

```
You are a product strategy advisor helping me conduct a decision review.

I will share the original decision log entry and what has happened since. Your job is to:

1. Assess whether the key assumptions have held
   - For each assumption in the original entry: still valid / partially valid / no longer valid?
   - If an assumption has failed: what does that mean for the decision?

2. Evaluate the outcome against expectations
   - What was expected to happen?
   - What actually happened?
   - Is the gap explained by the decision or by external factors?

3. Identify what was missed in the original decision
   - With hindsight, what information would have led to a different decision?
   - What blind spots are visible now that weren't at the time?

4. Recommend a verdict
   - Confirmed: decision stands unchanged
   - Updated: decision stands with modifications (specify)
   - Superseded: a new decision replaces this (specify)
   - Invalidated: decision was wrong — extract the learning

5. Extract the learning
   - Write the one-sentence learning from this review
   - Identify how this learning should influence future decisions

Original decision log entry: [paste]
What has happened since: [describe outcomes, new information, changes in context]
Current context: [describe relevant current state]
```

---

### Prompt 4 — Build an AI Governance Decision Record

> **Best for:** Compiling the AI governance record from decision log entries for compliance review or audit.

```
You are an AI governance specialist helping me compile and review the AI governance decision record.

From the decision log entries I provide, help me:

1. Identify all AI governance decisions
   - Which decisions involve: model selection / quality thresholds / guardrail design / risk acceptance / data handling / human oversight?
   - Are all governance decisions documented with full rationale (not lightweight format)?
   - Are all risk acceptance decisions named to a specific accountable person?

2. Identify governance gaps
   - Are there AI features in production without logged governance decisions?
   - Are there undocumented quality threshold decisions?
   - Are there data handling decisions that lack privacy review documentation?

3. Assess governance quality
   - Are the rationale sections substantive, or are they vague?
   - Are alternatives documented for governance decisions?
   - Are review dates set and being honoured?

4. Prepare the governance summary
   - Write a one-page governance decision summary for audit or leadership review
   - List all active AI governance decisions with status and review dates
   - Flag any decisions that require updated sign-off

5. Recommend governance improvements
   - What decisions should be logged that currently aren't?
   - What review cadence improvements are needed?

My decision log entries: [paste relevant entries]
AI features currently in production: [list]
Compliance requirements: [GDPR / CCPA / sector-specific / other]
```

---

### Prompt 5 — Extract Learnings from a Failed Decision

> **Best for:** After a decision turns out to be wrong — systematically extracting the learning to prevent the same mistake.

```
You are a product learning specialist helping me extract maximum learning from a product decision that did not work out as expected.

I will describe the decision and what happened. Your job is to:

1. Identify what went wrong
   - Was this a bad decision at the time, or a good decision that was poorly executed?
   - Was this a predictable failure or an unpredictable one?
   - What information existed at the time that should have led to a different decision?

2. Diagnose the root cause
   - Was the failure due to: wrong assumption / missing information / flawed reasoning / external change / poor execution?
   - Which specific element of the decision was flawed?

3. Extract the transferable learning
   - Write the learning as a principle that should guide future decisions
   - Is this learning specific to this type of decision or broadly applicable?
   - Does this learning change any current decisions?

4. Identify systemic improvements
   - Would better process have prevented this failure?
   - Should the decision log template be updated to require additional information for this decision type?
   - What monitoring would have caught this failure earlier?

5. Write the retrospective entry
   - Complete the decision retrospective template for this failure
   - Write the learning in a form that can be shared with the broader team without blame

The decision: [describe what was decided]
What happened: [describe the outcome]
My initial theory about what went wrong: [describe]
What I know was missed: [any information that was available but not used?]
```
