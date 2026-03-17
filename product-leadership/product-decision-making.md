# 🧠 Product Decision-Making — AI Product Builder Playbook

> **A framework for structuring how product decisions are made, distributed, and improved across teams and leadership levels**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Decision-Making Model](#the-decision-making-model)
- [Layer 1: Decision Architecture](#layer-1-decision-architecture)
- [Layer 2: Decision Velocity](#layer-2-decision-velocity)
- [Layer 3: Decision Quality](#layer-3-decision-quality)
- [Layer 4: Decision Learning](#layer-4-decision-learning)
- [AI Product Decision-Making](#ai-product-decision-making)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Decision-making is the most important product management competency and the least deliberately designed. Most organisations make decisions the same way they always have — through hierarchy, habit, and whoever is in the room. The result is decisions that are too slow where speed matters, too fast where deliberation matters, and consistently unmemorable because they were never documented.

> **Core Principle:** Decision-making quality is an organisational capability, not an individual one. The goal is not to find the smartest person and put all decisions through them. The goal is to design a system where the right decisions get made at the right level, with the right information, at the right speed — regardless of who is in the room.

For AI products, decision-making carries additional weight. AI decisions — which model, what quality threshold, how much autonomy — compound over time. A poor AI architecture decision made in month one may constrain the product for years. A low quality threshold accepted under competitive pressure may take twelve months of trust-rebuilding to repair. Deliberateness in AI decision-making pays dividends at a rate that exceeds most other investments.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Decisions are consistently too slow | 🔴 Critical — structural problem |
| The wrong people are making decisions | 🔴 Critical — authority gap |
| Decisions are made but not followed | 🔴 Critical — alignment failure |
| Scaling team — decision-making has not scaled with it | 🟠 High |
| Same decisions are being relitigated repeatedly | 🟠 High — no record or learning |
| New leadership — need to establish decision norms | 🟠 High |
| Post-mortem reveals poor decision process | 🟡 Medium |

---

## The Decision-Making Model

Strong product decision-making operates across four layers. Architecture without velocity is bureaucracy. Velocity without quality is recklessness. Quality without learning is stagnation.

```
DECISION ARCHITECTURE
  ↓ who decides what, and how
DECISION VELOCITY
  ↓ decisions made at the right speed
DECISION QUALITY
  ↓ decisions made with the right information and process
DECISION LEARNING
  ↓ decisions improve over time
```

| Layer | Core Question | Common Failure |
|---|---|---|
| **Architecture** | Who should be making this decision? | Wrong level — too high or too low |
| **Velocity** | How fast should this decision be made? | Too slow for reversible; too fast for irreversible |
| **Quality** | Is the right information and process being applied? | Opinion over evidence; no pre-mortem |
| **Learning** | Are we getting better at decisions? | No documentation; no retrospective |

---

## Layer 1: Decision Architecture

### 1.1 Decision Categorisation

Not all decisions deserve the same process. The first step is categorising the decision correctly.

| Category | Characteristics | Process | Decision Maker |
|---|---|---|---|
| **Type 1: Irreversible** | High cost to undo, affects many, long-term consequences | Full framework + sign-off | CPO / CEO |
| **Type 2: Reversible-but-costly** | Can be undone, but reversal requires significant effort | Structured decision document | PM lead + stakeholders |
| **Type 3: Reversible** | Can be undone quickly with limited impact | Lightweight record | PM |
| **Type 4: Trivial** | Low stakes, easily corrected | Team discussion + log entry | Team |

> **Rule of thumb:** Most teams over-escalate Type 3 and Type 4 decisions (slowing everything down) while under-investing in Type 1 decisions (where the risk actually is). The goal is precise matching of process to stakes.

### 1.2 Decision Authority Matrix

```
DECISION AUTHORITY MATRIX

Define for your team — this is the single most leverage document for decision velocity.

| Decision | Who decides | Who is consulted | Who is informed |
|----------|-------------|-----------------|-----------------|
| Product vision | CPO | CEO, PM leads | All teams |
| Annual roadmap | CPO + PM leads | Engineering, Design | All |
| Quarterly roadmap | PM lead | Engineering lead, CPO | All teams |
| Feature scope (sprint) | PM | Engineering | Design, CS |
| UX/UI design direction | Design lead | PM, users | Engineering |
| AI model selection | PM + AI lead | CTO | Engineering |
| AI quality threshold | PM | AI lead, Legal | Engineering |
| AI launch decision | PM | Eng lead, AI lead | CPO, CS |
| Architecture decisions | Eng lead | CTO, PM | All engineering |
| Pricing | PM + Finance | CPO, Sales | CS |
| Hiring | Hiring manager | CPO, Team leads | Team |

Review this matrix quarterly — as the product and team evolve, so should authority.
```

### 1.3 Decision Escalation Protocol

```
ESCALATION PROTOCOL

When to escalate:
  [ ] The decision requires resources beyond the current decision-maker's authority
  [ ] The decision sets a precedent that affects other teams
  [ ] The decision has regulatory or legal implications
  [ ] The decision-maker is genuinely uncertain after consulting all available evidence
  [ ] The decision has been deadlocked for > 48 hours

How to escalate:
  1. Define the decision clearly (1 sentence)
  2. Identify the options with pros/cons
  3. State your recommendation with rationale
  4. State what you need from the escalation point
  5. Set a deadline for the escalated decision

Do NOT escalate to avoid accountability:
  If you have the authority to make the decision, make it.
  Escalation is for genuine authority gaps — not for cover.
```

---

## Layer 2: Decision Velocity

### 2.1 The Cost of Slow Decisions

```
DECISION VELOCITY AUDIT

For each major decision in the last quarter, measure:
  Time from "decision needed" to "decision made": ___
  Time from "decision made" to "team executing": ___

Target times by decision type:
  Type 4 (trivial): Same day
  Type 3 (reversible): 1–3 business days
  Type 2 (reversible-but-costly): 3–7 business days
  Type 1 (irreversible): 1–3 weeks

If actual times consistently exceed targets:
  Common cause 1: Wrong person in the decision chain (authority mismatch)
  Common cause 2: Insufficient information at decision time (research gap)
  Common cause 3: Too many people in the consultation list (over-inclusion)
  Common cause 4: No deadline set for the decision (indefinite by default)
```

### 2.2 The Two-Pizza Rule for Decision Teams

```
DECISION TEAM SIZING

A decision should be made by the smallest group that has:
  - The authority to make it
  - The expertise to make it well
  - The buy-in required to execute it

If the decision group exceeds 6 people:
  Is everyone adding unique information or perspective? (If not, remove them)
  Is everyone required to execute? (If not, move them to "informed")
  Is this a decision or an alignment session? (They are different — run them differently)

Decision group vs alignment group:
  Decision group: Makes the decision. Maximum 6 people.
  Alignment group: Receives and understands the decision. Can be the full team.
  These should be separate activities — do not conflate them.
```

### 2.3 Decision Timeboxing

```
DECISION TIMEBOX PROTOCOL

For any decision that has been open for more than 3 days without resolution:

Step 1: Name the decision explicitly
  "The decision we need to make is: [1 sentence]"

Step 2: Set a deadline
  "We will make this decision by [date/time]. If we cannot agree by then,
   [named person] will make the call."

Step 3: Identify what is needed to decide
  "We are waiting on: [specific information / input / research]"
  Assign: who will get that information by when.

Step 4: If deadline passes without consensus:
  The named decision owner makes the call.
  Others may disagree and commit.
  The decision is documented.

A decision delayed is a decision made by default — usually the worst option.
```

---

## Layer 3: Decision Quality

### 3.1 The Decision Quality Standard

A decision meets the quality standard when it answers four questions:

```
DECISION QUALITY STANDARD

1. What is decided?
   [One sentence — specific enough that two people would interpret it the same way]

2. What is not decided?
   [Explicit scope — what adjacent questions are NOT resolved by this decision]

3. Why was this decided?
   [Evidence-based rationale — not "we discussed it" but "we chose this because [evidence]"]

4. What would change this decision?
   [Specific conditions that would cause us to revisit]

A decision that cannot answer all four questions is not a complete decision.
```

### 3.2 Pre-Decision Checklist

```
PRE-DECISION CHECKLIST

Before making any Type 1 or Type 2 decision:

Evidence:
[ ] Have we collected evidence from the strongest available source?
[ ] Have we actively looked for evidence that contradicts our preference?
[ ] Is our evidence quality appropriate to the stakes of the decision?

Options:
[ ] Have we considered at least 3 genuinely distinct options?
[ ] Have we considered the "do nothing" option explicitly?
[ ] Have we considered a phased or reversible version of the preferred option?

Pre-mortem:
[ ] Have we imagined this decision failing and identified why?
[ ] Have we addressed the most likely failure mode in the decision?

Bias check:
[ ] Are we making this decision based on what we want to be true or what is true?
[ ] Is anyone in the decision group too close to this to be objective?
[ ] Is the loudest voice the most informed voice?

Reversibility:
[ ] Have we accurately assessed how reversible this decision is?
[ ] If it is irreversible, have we applied sufficient deliberation?
```

### 3.3 The RAPID Decision Model

For complex, cross-functional decisions, RAPID provides clear role assignments:

```
RAPID MODEL

R — Recommend: Proposes the decision and rationale. Does the analytical work.
A — Agree: Must agree before the decision is made. (Use sparingly — every A adds friction)
P — Perform: Executes the decision once made. Must be consulted.
I — Input: Provides information or expertise. Consulted but does not block.
D — Decide: Makes the final call. One person only.

Example — AI model selection:
  R (Recommend): AI lead + PM
  A (Agree): CTO (if cost implications), Legal (if compliance implications)
  P (Perform): Engineering team
  I (Input): Design (latency UX implications)
  D (Decide): CPO or delegated PM lead

Rules:
  Only one D — multiple D's produce deadlock or diffused accountability
  Minimum A's — every A is a veto point; use only when genuinely required
  P must always be consulted — "execute without input" produces poor implementation
```

---

## Layer 4: Decision Learning

### 4.1 Decision Documentation Standard

```
DECISION LOG ENTRY

Date: ___  |  Decision: ___  |  Owner: ___

The decision (1 sentence):
_______________________________________________

Why (evidence-based rationale):
_______________________________________________

What was rejected and why:
_______________________________________________

What would change this decision:
_______________________________________________

Review date: _______________________________________________
```

### 4.2 Decision Retrospective

```
DECISION RETROSPECTIVE (quarterly)

Review the last quarter's significant decisions.

For each decision:
  Was the decision made at the right level? (Too high / Right / Too low)
  Was the decision made at the right speed? (Too slow / Right / Too fast)
  Was the outcome what we expected? (Better / As expected / Worse)
  If worse than expected: what in the process would have produced a better outcome?

Patterns to look for:
  Type 1 decisions being made too quickly → Slow down the process
  Type 3/4 decisions being escalated → Clarify the authority matrix
  Decisions being relitigated → Decision log is not being used or trusted
  Decisions with poor outcomes consistently → Specific decision type or domain needs improved process

Action items from retrospective:
  _______________________________________________
```

### 4.3 Decision Improvement Metrics

```
DECISION QUALITY METRICS

Decision velocity:
  Average time from "decision needed" to "decision made" by type
  Target: Type 1 < 2 weeks / Type 2 < 5 days / Type 3 < 2 days / Type 4 < 1 day

Decision quality:
  % of decisions that were relitigated within 30 days
  Target: < 10% (relitigating suggests decision was not complete or not trusted)

Decision documentation:
  % of significant decisions with a complete decision log entry
  Target: > 90%

Decision accuracy:
  % of Type 1/2 decisions that produced the expected outcome
  Target: > 70% (some poor outcomes are unavoidable with good process)
```

---

## AI Product Decision-Making

### 5.1 AI-Specific Decision Types

AI products have a class of decisions that do not exist in traditional software:

| AI Decision | Reversibility | Stakes | Recommended Process |
|---|---|---|---|
| **AI approach** (RAG vs fine-tune vs prompt) | Low once built | High | Full framework + architecture review |
| **Model selection** | Medium (weeks to change) | High | Structured decision with evaluation |
| **Quality threshold** | High (can adjust) | Medium-High | PM decision with evidence |
| **Autonomy level** | High (can reduce) | Medium-High | PM decision with monitoring |
| **Launch gate** | Medium (delay is costly) | High | Go/no-go checklist |
| **Prompt change** | High (version control) | Medium | PM decision with regression test |
| **AI cost ceiling** | High | Medium | PM + Finance decision |

### 5.2 The AI Decision Pre-Flight

```
AI DECISION PRE-FLIGHT

Before any significant AI decision, answer:

1. What is the uncertainty we are navigating?
   AI decisions are more uncertain than traditional product decisions.
   Name the specific uncertainty and its implications.

2. What is the minimum quality threshold for this decision to be acceptable?
   Not "what would be great" but "what must be true for this to be correct?"

3. How reversible is this decision if the AI does not perform as expected?
   AI decisions often appear more reversible than they are.

4. What is the 6-month consequence of this decision if our assumptions are wrong?
   AI decisions compound. A wrong model selection compounds for months.

5. Who must be consulted who has not yet been included?
   AI decisions often require expertise not present in standard product teams:
   Legal (for regulated domains), AI safety specialists, domain experts.

6. What monitoring will tell us within 30 days if this decision was wrong?
   Every AI decision should include a measurement plan.
```

---

## Templates

### Template A: Decision Record

```
# Decision Record — [Decision Name]
Date: ___  |  Owner: ___  |  Type: 1 / 2 / 3 / 4  |  Status: Open / Made / Revised

## The Decision (1 sentence)
_______________________________________________

## Context
[Why does this decision need to be made now?]

## Options Considered
Option A: [pros / cons / risk]
Option B: [pros / cons / risk]
Option C (status quo): [pros / cons / risk]

## Decision Made
Option selected: _______________________________________________
Rationale: _______________________________________________
Evidence: _______________________________________________
Trade-offs accepted: _______________________________________________

## What Is Not Decided
_______________________________________________

## What Would Change This Decision
_______________________________________________

## Stakeholders
Decided by: ___  |  Consulted: ___  |  Informed: ___

## Review Date
_______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| HiPPO (Highest Paid Person's Opinion) decides | Authority matrix + evidence standard override seniority |
| Decisions by consensus (everyone must agree) | Named decision owner; disagree and commit for dissenters |
| No written record of decisions | Decision log for all Type 1–3 decisions |
| Over-escalation of trivial decisions | Authority matrix makes it clear what can be decided at each level |
| Decisions reopened without new evidence | New evidence required to revisit; document the precedent |
| No review date on significant decisions | Every Type 1/2 decision has a review trigger or date |
| AI decisions without uncertainty acknowledgement | AI pre-flight required for all AI decisions |
| Decision meetings that end without a decision | Set a timebox; if no consensus, owner decides |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Decision log review | Monthly | PM |
| Authority matrix review | Quarterly | PM + CPO |
| Decision velocity audit | Quarterly | PM + CPO |
| Decision retrospective | Quarterly | PM + team |
| AI decision pre-flight | Per significant AI decision | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Decision Authority Matrix

> **Best for:** Clarifying who decides what across a product team — the single highest-leverage tool for improving decision velocity.

```
You are an organisational design expert helping me build a decision authority matrix for my product team.

Design the complete authority matrix covering all significant decision types:

1. Product vision and strategy decisions
2. Roadmap and prioritisation decisions
3. Feature scope and design decisions
4. AI-specific decisions (model, quality, autonomy, launch)
5. Technical architecture decisions
6. Pricing and commercial decisions
7. Team and hiring decisions

For each decision type, specify:
- Who decides (one person only — the D in RAPID)
- Who must agree before the decision is made (the A in RAPID — use sparingly)
- Who must be consulted (the I and P in RAPID)
- Who is informed after the decision

After the matrix:
- Identify the decisions currently being made at the wrong level (too high or too low)
- Identify any decisions with no clear owner
- Write the 3 rules for using this matrix that the team should agree on

My team structure: [describe roles and reporting relationships]
Current pain points: [where are decisions too slow or unclear?]
Product stage: [early / growth / scale]
Is this an AI product: [yes/no]
```

---

### Prompt 2 — Accelerate a Stalled Decision

> **Best for:** When a decision has been open too long and needs a structured process to reach resolution.

```
You are a decision facilitation expert helping me resolve a stalled product decision.

The decision has been open for [N] days without resolution. Help me close it:

1. Decision diagnosis
   - Why is this decision stalled? (Authority gap / Information gap / Alignment gap / Fear of being wrong)
   - Is this the right decision to be making, or is there a prior decision that needs to be made first?

2. Information audit
   - What information is still outstanding?
   - Can the decision be made with current information, or must we wait?
   - If we must wait: what is the maximum acceptable wait time?

3. Decision group audit
   - Who is currently involved in this decision?
   - Is everyone adding unique value, or are some people creating friction without adding insight?
   - Who should be the named decision owner?

4. Timebox design
   - Set a specific deadline for this decision
   - What happens if consensus is not reached by the deadline?
   - Who makes the final call?

5. Pre-work for the decision meeting
   - What must be prepared before the meeting?
   - Write the 30-minute decision meeting agenda
   - Write the decision record template for this specific decision

The stalled decision: [describe what needs to be decided]
Who is involved: [list people and roles]
What information exists: [what evidence is available]
What is blocking resolution: [your assessment of why it is stalled]
```

---

### Prompt 3 — Run a Decision Quality Review

> **Best for:** Evaluating whether a significant decision was made well — process quality, not just outcome quality.

```
You are a decision quality analyst helping me evaluate whether a product decision was made well.

Assess the decision process across four dimensions:

1. Evidence quality
   - What type of evidence drove this decision?
   - Was the evidence quality appropriate to the decision stakes?
   - Was contradicting evidence considered?

2. Options considered
   - Were at least 3 genuinely distinct options considered?
   - Was the status quo explicitly evaluated?
   - Was a reversible or phased option considered?

3. Bias assessment
   - Was there HiPPO influence (seniority over evidence)?
   - Was there confirmation bias (seeking evidence that confirmed the preference)?
   - Was the decision group too homogeneous (same perspective)?

4. Process integrity
   - Was a pre-mortem conducted?
   - Were the right people involved (not too many, not too few)?
   - Was the decision made at the right level (not escalated unnecessarily, not decided too low)?

After the assessment:
- Rate the decision quality: Strong / Adequate / Weak
- Identify the top 2 process improvements that would have produced a better decision
- What principle should this retrospective add to our decision-making norms?

The decision: [describe what was decided and how]
The outcome: [what happened — did the decision produce the expected result?]
Context: [what was the timeline, who was involved, what evidence was used]
```

---

### Prompt 4 — Design the AI Decision Pre-Flight Process

> **Best for:** Before any significant AI product decision — ensuring the right questions are asked about uncertainty, reversibility, and measurement.

```
You are an AI product strategy advisor helping me design a pre-flight process for AI decisions.

For the AI decision I describe, run the complete pre-flight:

1. Uncertainty mapping
   - What are the specific uncertainties in this decision?
   - Which uncertainties can be reduced before deciding (research spikes)?
   - Which must be accepted as inherent to the decision?

2. Quality threshold definition
   - What is the minimum acceptable outcome if this decision is correct?
   - What is the maximum acceptable downside if this decision is wrong?

3. Reversibility assessment
   - How reversible is this decision in 30 days? In 6 months? In 12 months?
   - What would reversal cost (time, money, user trust, technical debt)?
   - Is there a more reversible version of this decision that still achieves the goal?

4. Compound consequence analysis
   - What constraints does this decision create on future decisions?
   - What opportunities does this decision close off?
   - What is the 12-month trajectory if this decision compounds in the wrong direction?

5. Measurement plan
   - What metric will tell us within 30 days if this decision was correct?
   - What will we look for in 90 days?
   - At what point do we escalate if the decision is not producing expected results?

The AI decision I need to make: [describe — model selection, quality threshold, architecture, etc.]
Options being considered: [describe each option]
My current leaning: [which option and why]
Stakes: [what is the consequence of getting this wrong?]
```

---

### Prompt 5 — Build a Decision Retrospective

> **Best for:** Quarterly review of the team's decision-making patterns — identifying systemic improvements.

```
You are a product leadership advisor helping me run a quarterly decision retrospective.

I will share a summary of our significant decisions from the last quarter. For each category, identify patterns and recommend improvements:

1. Decision velocity analysis
   - Which decisions took too long? What caused the delay?
   - Which decisions were made too quickly? What was the risk?
   - What is the single biggest structural cause of slow decisions on our team?

2. Decision quality analysis
   - Which decisions produced the expected outcome?
   - Which decisions produced unexpected outcomes (positive or negative)?
   - For unexpected negative outcomes: what in the process would have produced a better result?

3. Authority and escalation patterns
   - Were decisions made at the right level, or frequently escalated unnecessarily?
   - Were there decisions made too low that should have had broader input?
   - Does the current authority matrix reflect how we actually make decisions?

4. Documentation and learning
   - Are significant decisions being documented with full rationale?
   - Are we learning from decision outcomes, or repeating similar mistakes?

5. Recommendations
   - Top 3 changes to improve decision quality next quarter
   - Top 1 change to improve decision velocity next quarter
   - One decision that should be reviewed because the context has changed

My decisions last quarter: [summarise significant decisions, their process, and outcomes]
Current decision norms: [describe how decisions are currently made]
Known pain points: [where does the team struggle most?]
```
