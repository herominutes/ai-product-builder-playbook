# 📐 Technical Design Document — AI Product Builder Playbook

> **A framework for writing technical design documents that align engineering, product, and design before a line of code is written**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The TDD Model](#the-tdd-model)
- [Section 1: Problem and Goals](#section-1-problem-and-goals)
- [Section 2: Proposed Solution](#section-2-proposed-solution)
- [Section 3: Technical Design](#section-3-technical-design)
- [Section 4: AI Design Decisions](#section-4-ai-design-decisions)
- [Section 5: Implementation Plan](#section-5-implementation-plan)
- [Section 6: Testing and Validation](#section-6-testing-and-validation)
- [Section 7: Open Questions and Risks](#section-7-open-questions-and-risks)
- [Full TDD Template](#full-tdd-template)
- [Review Process](#review-process)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A Technical Design Document (TDD) is the engineering team's equivalent of the PRD. Where the PRD defines *what* to build and *why*, the TDD defines *how* to build it — the technical choices, architecture decisions, tradeoffs, and implementation plan that the engineering team commits to before writing the first line of code.

> **Core Principle:** A TDD is not a bureaucratic requirement — it is the cheapest engineering decision the team will make. An hour of design review catches failures that would take a week to fix in implementation and a month to fix in production. The TDD creates the shared understanding that prevents the most expensive engineering mistakes.

For AI systems, the TDD carries additional weight. AI introduces design decisions that have significant downstream consequences: model selection affects cost, latency, and quality simultaneously; prompt architecture affects maintainability and testability; retrieval design affects both accuracy and performance. These decisions deserve rigorous pre-implementation review.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Any new AI feature or significant technical change | 🔴 Critical — write before development begins |
| Architecture decision with significant tradeoffs | 🔴 Critical — get alignment before committing |
| Feature touching multiple teams or systems | 🟠 High — coordination requires shared design doc |
| Integrating a new AI model provider or component | 🟠 High |
| Significant refactor of existing AI components | 🟠 High |
| New engineer leading a complex feature | 🟡 Medium — TDD helps them get early feedback |

---

## The TDD Model

A TDD moves from problem clarity through solution design to implementation commitment.

```
PROBLEM AND GOALS
  ↓ what are we solving and what does success look like technically?
PROPOSED SOLUTION
  ↓ what approach are we taking and why?
TECHNICAL DESIGN
  ↓ how does it work in detail?
AI DESIGN DECISIONS
  ↓ what are the AI-specific technical choices?
IMPLEMENTATION PLAN
  ↓ how do we build it, in what sequence, and in how long?
TESTING AND VALIDATION
  ↓ how do we know it works before and after launch?
OPEN QUESTIONS AND RISKS
  ↓ what are we uncertain about and what could go wrong?
```

---

## Section 1: Problem and Goals

### 1.1 Problem Statement

```
PROBLEM STATEMENT

What problem are we solving technically?
[This is distinct from the product problem — this is the technical challenge]

Current state:
  How does the relevant part of the system work today?
  What are its limitations?

Desired state:
  How should it work after this change?
  What capabilities will be added or improved?

Why now?
  What makes this the right time to solve this? (product pressure / technical debt / scaling need)
```

### 1.2 Technical Goals

```
TECHNICAL GOALS

Primary goal (the one thing this TDD must achieve):
_______________________________________________

Secondary goals (important but not blocking):
1. _______________________________________________
2. _______________________________________________

Non-goals (explicitly out of scope for this TDD):
1. _______________________________________________
2. _______________________________________________
[Non-goals are as important as goals — they prevent scope creep]

Success criteria:
Technical: [what measurable technical outcome defines success?]
Performance: [latency, throughput, cost targets]
Quality: [for AI — quality score target, error rate target]
```

### 1.3 Constraints

```
CONSTRAINTS

Hard constraints (cannot be violated):
  [ ] Must be backward compatible with [system/API]
  [ ] Must not exceed $[X] per month in additional cost
  [ ] Must meet [latency] SLA
  [ ] Must comply with [regulation/policy]
  [ ] Must use existing [technology] stack

Soft constraints (strong preferences):
  [ ] Prefer [technology] to minimise team context-switching
  [ ] Minimise changes to [component] to reduce risk
  [ ] Prefer incremental over big-bang migration
```

---

## Section 2: Proposed Solution

### 2.1 Solution Overview

```
SOLUTION OVERVIEW

Chosen approach (one paragraph):
[Describe the solution in plain language — what you will build, how it works at a high level,
and why this approach was chosen over alternatives]

Why this approach:
[The rationale — what makes this the right choice given the constraints and goals]
```

### 2.2 Alternatives Considered

Always document alternatives. This is the most relitigated section — document it now.

```
ALTERNATIVES CONSIDERED

Alternative A: [name]
  Description: _______________________________________________
  Pros: _______________________________________________
  Cons: _______________________________________________
  Why rejected: _______________________________________________

Alternative B: [name]
  Description: _______________________________________________
  Pros: _______________________________________________
  Cons: _______________________________________________
  Why rejected: _______________________________________________

Alternative C (do nothing / status quo):
  Description: Continue with current approach
  Pros: _______________________________________________
  Cons: _______________________________________________
  Why rejected: _______________________________________________
```

### 2.3 Tradeoffs

```
TRADEOFFS ACCEPTED

Tradeoff 1: [what was traded off]
  We are accepting [downside] in exchange for [upside].
  This is the right tradeoff because: _______________________________________________
  We will know this was wrong if: _______________________________________________

Tradeoff 2: [what was traded off]
  [same structure]

Key question: If these tradeoffs turn out to be wrong, how difficult is it to reverse the decision?
Reversibility: Easy (days) / Moderate (weeks) / Hard (months) / Irreversible
```

---

## Section 3: Technical Design

### 3.1 System Design

```
SYSTEM DESIGN

[Describe the technical design with enough detail for an engineer to implement without constant questions.
Include: component interactions, data flows, API contracts, state management]

New components introduced:
  Component: [name] — Purpose: [what it does] — Location: [where it lives in the system]

Modified components:
  Component: [name] — Change: [what changes] — Impact: [what depends on this]

Removed components (if any):
  Component: [name] — Migration: [how existing data/users are handled]

Data model changes:
  New tables/fields: _______________________________________________
  Migrations required: _______________________________________________
  Backward compatibility: _______________________________________________
```

### 3.2 API Design

```
API DESIGN

New endpoints:
  POST /[path]
    Purpose: _______________________________________________
    Request body: [describe key fields with types]
    Response: [describe key fields with types]
    Error responses: [list error codes and meanings]
    Authentication: _______________________________________________
    Rate limiting: _______________________________________________

Modified endpoints:
  [Describe breaking vs non-breaking changes]
  Breaking changes: _______________________________________________
  Migration path: _______________________________________________

Deprecated endpoints:
  [Describe deprecation timeline and replacement]
```

### 3.3 Performance Design

```
PERFORMANCE DESIGN

Latency targets:
  P50: ___ ms — achievable because: _______________________________________________
  P95: ___ ms — achievable because: _______________________________________________
  P99: ___ ms — achievable because: _______________________________________________

Throughput:
  Expected peak requests/second: ___
  Current capacity: ___
  Required capacity change: _______________________________________________

Scalability approach:
  How does this scale as load increases: _______________________________________________
  Known scaling limits: _______________________________________________
  Scaling action when limit approached: _______________________________________________

Caching strategy:
  What is cached: _______________________________________________
  Cache invalidation: _______________________________________________
  Cache hit rate target: ___%
```

---

## Section 4: AI Design Decisions

This section is unique to AI features. It documents the AI-specific technical choices that have the largest downstream impact on quality, cost, and maintainability.

### 4.1 Model Design

```
MODEL DESIGN

Model selection:
  Selected model: _______________________________________________
  Version: Pinned to [version] / Latest
  Rationale: [quality threshold met + cost + latency — specific to this task]
  Evaluation evidence: Quality score on evaluation dataset = ___ / 5
  Alternative model evaluated: ___ — Rejected because: _______________________________________________

Prompt architecture:
  System prompt structure: [describe the sections and their purpose]
  Version control: [how prompts are versioned and deployed]
  Testing: [how prompts are tested before deployment]
  Rollback: [how to revert a prompt change]

Parameter design:
  Temperature: ___ — Rationale: _______________________________________________
  Max tokens: ___ — Rationale: _______________________________________________
  Other parameters: _______________________________________________

Context window management:
  Context window: ___ tokens
  Allocation: System prompt ___% / Retrieved context ___% / Conversation ___% / Output ___%
  Overflow handling: _______________________________________________
```

### 4.2 Retrieval Design (if RAG)

```
RETRIEVAL DESIGN

Data sources:
  Source 1: [name] — Format: ___ — Update frequency: ___ — Volume: ___
  Source 2: [name] — [same structure]

Ingestion pipeline:
  Cleaning: _______________________________________________
  Chunking: Strategy: ___ — Size: ___ tokens — Overlap: ___%
  Embedding: Model: ___ — Dimensions: ___
  Indexing: Vector store: ___ — Index type: ___
  Metadata: [key metadata fields for filtered retrieval]

Retrieval pipeline:
  Strategy: Dense / Sparse / Hybrid — Weights: ___
  Top-K: ___ — Similarity threshold: ___
  Query optimisation: _______________________________________________
  Re-ranking: Yes / No — Model: _______________________________________________

Quality validation:
  Context relevance target: > ___%
  Answer faithfulness target: > ___%
```

### 4.3 Evaluation Pipeline Design

```
EVALUATION PIPELINE DESIGN

Pre-launch evaluation:
  Dataset: ___ examples — Source: _______________________________________________
  Evaluation method: LLM-as-judge / Human / Automated metrics
  Quality threshold for launch: ___ / 5
  Safety threshold for launch: > ___%

Production monitoring:
  Sampling rate: ___%
  Evaluation cadence: Daily / Weekly
  Quality baseline: ___ / 5
  Alert threshold: < ___ / 5
  Drift detection: _______________________________________________

Feedback loop:
  How evaluation findings enter the improvement cycle: _______________________________________________
```

### 4.4 Guardrail Design

```
GUARDRAIL DESIGN

Input guardrails:
  PII detection: Yes / No — Method: _______________________________________________
  Prompt injection detection: Yes / No — Method: _______________________________________________
  Input classification: Yes / No — Method: _______________________________________________
  Rate limiting: ___ requests/user/hour

Output guardrails:
  Content filter: Yes / No — Filter: _______________________________________________
  PII scanner: Yes / No
  Format validation: Yes / No — Schema: _______________________________________________
  Hallucination detection: Yes / No — Method: _______________________________________________

Operational guardrails:
  Cost circuit breaker: $___/day → [action]
  Quality circuit breaker: Quality < ___ → [action]
  Error rate circuit breaker: > ___% → [action]
```

---

## Section 5: Implementation Plan

### 5.1 Implementation Phases

```
IMPLEMENTATION PHASES

Phase 1: [Name — e.g. Foundation]
  Duration: ___ days
  Scope: _______________________________________________
  Definition of done: _______________________________________________
  Dependencies: _______________________________________________
  Risk: _______________________________________________

Phase 2: [Name — e.g. Core feature]
  Duration: ___ days
  Scope: _______________________________________________
  Definition of done: _______________________________________________
  Dependencies: Phase 1 complete + _______________________________________________

Phase 3: [Name — e.g. Evaluation and hardening]
  Duration: ___ days
  Scope: _______________________________________________
  Definition of done: _______________________________________________

Total estimated duration: ___ days
Critical path: _______________________________________________
Buffer included: Yes (___ days) / No
```

### 5.2 Migration Plan (if applicable)

```
MIGRATION PLAN

What is being migrated: _______________________________________________
Migration strategy: Big bang / Phased / Parallel run
Rollback plan: _______________________________________________

Data migration:
  Volume: _______________________________________________
  Estimated time: _______________________________________________
  Validation: _______________________________________________

User impact:
  Downtime required: Yes (___ minutes) / No
  Breaking changes for existing users: Yes / No
  Communication required: Yes / No — Timeline: _______________________________________________
```

---

## Section 6: Testing and Validation

### 6.1 Testing Strategy

```
TESTING STRATEGY

Unit tests:
  Coverage target: ___%
  Key components to unit test: _______________________________________________
  AI-specific unit tests: [prompt behaviour tests, format compliance tests]

Integration tests:
  Components to integration test: _______________________________________________
  External dependencies to mock: _______________________________________________

End-to-end tests:
  Key user journeys to cover: _______________________________________________
  Environment: _______________________________________________

AI-specific testing:
  Prompt test suite: ___ test cases (see Prompt Testing framework)
  Evaluation dataset: ___ examples
  Quality gate: Feature does not deploy until quality score > ___
  Safety evaluation: Safety test suite ___ cases — must pass 100%

Performance testing:
  Load test target: ___ requests/second
  Latency test target: P99 < ___ ms
  Cost test: Estimate cost at [N] requests/day
```

### 6.2 Pre-Launch Checklist

```
PRE-LAUNCH CHECKLIST

Code quality:
  [ ] Code review completed by at least 2 engineers
  [ ] All unit tests passing
  [ ] Integration tests passing
  [ ] No critical or high-severity security issues

AI quality:
  [ ] Evaluation dataset run — quality score > ___
  [ ] Safety evaluation — all safety tests pass
  [ ] Prompt test suite — all mandatory tests pass
  [ ] Hallucination rate within acceptable threshold

Operations:
  [ ] Monitoring dashboards live and tested
  [ ] Alerts configured and tested
  [ ] Runbook written
  [ ] Rollback procedure tested in staging

Compliance:
  [ ] AI risk assessment complete
  [ ] Privacy review complete
  [ ] Legal sign-off (if required)

Performance:
  [ ] Load test completed at target traffic
  [ ] Latency P99 meets SLA in staging
  [ ] Cost per interaction confirmed within budget
```

---

## Section 7: Open Questions and Risks

### 7.1 Open Questions

```
OPEN QUESTIONS

| Question | Owner | Due Date | Blocking? |
|----------|-------|----------|-----------|
| [Technical uncertainty that must be resolved] | | | Yes/No |
| | | | |

Decision needed by: _______________________________________________
If question not resolved by [date]: [fallback approach]
```

### 7.2 Technical Risks

```
TECHNICAL RISK REGISTER

| Risk | Likelihood | Impact | Mitigation | Owner |
|------|------------|--------|------------|-------|
| AI model quality does not meet threshold | Medium | High | Run evaluation early; have fallback model | |
| Retrieval latency exceeds budget | Medium | High | Benchmark retrieval before integration | |
| Cost higher than estimated | Medium | Medium | Implement cost monitoring day 1; set circuit breaker | |
| Integration with [external system] is unstable | Low | High | Design fallback; implement retry with backoff | |
| [AI-specific risk] | | | | |
```

---

## Full TDD Template

```
# Technical Design Document: [Feature Name]
Status: Draft / In Review / Approved
Date: ___  |  Author: ___  |  Version: ___
Reviewers: _______________________________________________

## 1. Problem and Goals
[Complete Section 1]

## 2. Proposed Solution
[Complete Section 2]

## 3. Technical Design
[Complete Section 3]

## 4. AI Design Decisions
[Complete Section 4 — for AI features]

## 5. Implementation Plan
[Complete Section 5]

## 6. Testing and Validation
[Complete Section 6]

## 7. Open Questions and Risks
[Complete Section 7]

## Review Comments
[Space for reviewer comments during the review process]

## Approval
[ ] Engineering lead  [ ] PM  [ ] Security (if required)  [ ] Architecture (if required)
```

---

## Review Process

```
TDD REVIEW PROCESS

Author responsibilities:
  - Share draft at least 48 hours before review meeting
  - Specifically call out areas of uncertainty for reviewer input
  - List the questions you most want answered in the review

Reviewer responsibilities:
  - Read the full TDD before the meeting
  - Comment on the doc (async) before the meeting
  - In the meeting: challenge the alternatives section — were the right options considered?

Review meeting structure (60 minutes):
  00:00 — Author walks through the proposal (20 min, no interruptions)
  00:20 — Clarifying questions from reviewers (10 min)
  00:30 — Open discussion: concerns, risks, missing alternatives (20 min)
  00:50 — Decision: approve / approve with conditions / revise and resubmit (10 min)

Common review failure modes:
  - Reviewing the solution without reviewing the alternatives
  - Approving because "it seems fine" rather than because the tradeoffs are well-understood
  - Missing the AI-specific design decisions section
  - Not pushing back on vague non-goals
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| TDD written after implementation begins | Write TDD before the first line of code |
| No alternatives documented | Always document at least 2 alternatives and why they were rejected |
| Vague non-goals | Non-goals must be specific enough that scope creep is detectable |
| AI section missing from TDD for AI features | AI design decisions require their own explicit section |
| Pre-launch checklist as a rubber stamp | Every item must be verified — not just checked |
| TDD not updated when design changes during implementation | Update the TDD when the design changes — it is a living document |
| Open questions never resolved | Every open question has an owner, a due date, and a fallback |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Write TDD | Per significant feature | Before development begins |
| TDD review meeting | Per TDD | 48 hours after draft shared |
| TDD update | During development | When design deviates from TDD |
| Post-implementation TDD review | After launch | Did we build what we designed? |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Write a Complete Technical Design Document

> **Best for:** Creating a full TDD for a new AI feature before development begins.

```
You are a senior engineer helping me write a complete Technical Design Document for an AI feature.

Guide me through each section:
1. Problem and goals — technical problem, goals, non-goals, constraints, success criteria
2. Proposed solution — chosen approach, alternatives considered, tradeoffs accepted
3. Technical design — system design, API design, performance design
4. AI design decisions — model selection, prompt architecture, retrieval design, evaluation pipeline, guardrails
5. Implementation plan — phases, estimates, migration plan if needed
6. Testing and validation — test strategy, pre-launch checklist
7. Open questions and risks — technical risk register, unresolved questions

For each section:
- Ask me the key questions, then draft the section from my answers
- Challenge vague answers — push for specifics
- Flag any AI design decision that will have significant downstream consequences

After all sections:
- Identify the top 3 technical risks in this design
- Identify any missing alternatives that should have been considered
- Write the review agenda for the TDD review meeting

Feature I am designing: [describe the AI feature]
My current thinking on the approach: [describe if you have one]
Key constraints: [latency, cost, team, technology]
Key open questions: [what am I most uncertain about?]
```

---

### Prompt 2 — Review and Critique a Technical Design Document

> **Best for:** Providing structured feedback on a TDD before it is approved and implementation begins.

```
You are a technical lead reviewing a Technical Design Document before approving it for implementation.

Review the TDD I share across these criteria:

1. Problem clarity
   - Is the technical problem clearly distinct from the product problem?
   - Are success criteria measurable?
   - Are non-goals specific enough to prevent scope creep?

2. Solution completeness
   - Are at least 2 substantive alternatives documented?
   - Are the tradeoffs explicit and their consequences understood?
   - Is the reversibility of the decision assessed?

3. Technical design depth
   - Is there enough detail for an engineer to implement without constant questions?
   - Are the API contracts specific enough?
   - Is the data model impact documented?

4. AI design quality (for AI features)
   - Is the model selection justified with evaluation evidence?
   - Is the prompt architecture designed for maintainability?
   - Is the evaluation pipeline specified?
   - Are guardrails designed for all risk scenarios?

5. Implementation plan realism
   - Are the estimates realistic given the scope?
   - Is the critical path identified?
   - Is the migration plan (if needed) safe?

6. Testing completeness
   - Are AI-specific tests (prompt tests, quality evaluation) included?
   - Is the pre-launch checklist complete?

For each criterion: verdict (Strong / Needs work / Missing) + specific feedback.
End with: the top 3 changes required before this TDD should be approved.

TDD to review: [paste your document]
```

---

### Prompt 3 — Design the AI-Specific Technical Decisions

> **Best for:** Working through the hardest AI technical decisions before writing the TDD — model selection, prompt architecture, retrieval design.

```
You are an AI systems architect helping me make the key AI technical decisions for my feature.

Guide me through each decision:

1. Model selection
   - What task am I asking the model to do? (classify / generate / extract / summarise / reason)
   - What quality threshold must the model meet?
   - Which models should I evaluate against my evaluation dataset?
   - What is the cost-quality-latency tradeoff between the top candidates?
   - Which model do you recommend and why?

2. Prompt architecture
   - Should this be a single prompt or a multi-step chain?
   - What are the key sections of the system prompt?
   - How should I handle context window management?
   - How should uncertainty be communicated to the user?

3. Retrieval design (if RAG)
   - What data sources should be indexed?
   - What chunking strategy fits my document types?
   - Should I use dense, sparse, or hybrid retrieval?
   - Is re-ranking worth the latency cost for my use case?

4. Evaluation pipeline
   - What quality dimensions matter most for my specific task?
   - Write the LLM-as-judge prompt for my use case
   - What is the pre-launch quality gate?

5. Guardrail design
   - What are the most important input guardrails for my use case?
   - What output checks are most important?
   - What are the circuit breaker conditions?

For each decision: give me a specific recommendation with rationale, not "it depends."

Feature I am designing: [describe]
User segment: [who uses it]
Domain: [what topic area]
Quality requirements: [what does excellent output look like?]
Constraints: [latency budget, cost budget, data available]
```

---

### Prompt 4 — Write the Testing Strategy for an AI Feature

> **Best for:** Designing the comprehensive testing plan for an AI feature — including AI-specific tests that standard testing frameworks miss.

```
You are a QA engineer specialising in AI systems helping me write a complete testing strategy.

Design the testing strategy across all layers:

1. AI-specific testing
   - Prompt unit test suite: write 15 test cases covering core behaviour, format, safety, and edge cases
   - Evaluation dataset: how many examples, what distribution, what ground truth format
   - Quality gate: what score must be achieved on the evaluation dataset before deployment?
   - Safety evaluation: what adversarial test cases must pass 100%?

2. Integration testing
   - Which component integrations must be tested?
   - How do I mock the AI model layer for deterministic integration tests?
   - What end-to-end scenarios must pass?

3. Performance testing
   - What load test scenarios should I run?
   - How do I test latency under realistic load?
   - How do I estimate and verify the cost model?

4. Regression testing
   - What is the baseline to regress against?
   - How do I detect if a deployment causes a quality regression?
   - What monitoring must be live from day 1?

5. Pre-launch checklist
   - Write the complete pre-launch checklist for this specific feature
   - Include: code quality, AI quality, operations, compliance, performance gates

After the strategy:
- Identify which tests can be automated vs which require human review
- Estimate the total testing time and sequence
- Write the rollback criteria: at what point do we roll back this feature?

My AI feature: [describe]
Domain and risk level: [what is the consequence of a quality failure?]
Current testing infrastructure: [what testing frameworks and CI/CD do I have?]
```

---

### Prompt 5 — Resolve Technical Open Questions

> **Best for:** Working through technical uncertainties in a TDD before they block implementation.

```
You are a technical advisor helping me resolve the open questions in my Technical Design Document.

For each open question I share, help me:

1. Frame the question precisely
   - Is this a technical question, a product question, or a data question?
   - What is the actual decision that needs to be made?

2. Map the options
   - What are the possible answers to this question?
   - What are the implications of each answer for the design?

3. Identify what we would need to know
   - Is this answerable through reasoning, or does it require a prototype/spike?
   - If a spike: what is the smallest experiment that would answer this?
   - If reasoning: what information do I have vs what am I assuming?

4. Recommend an answer or approach
   - If there is a clear best answer: state it with confidence and rationale
   - If uncertain: design the spike (2–5 days maximum) that resolves the uncertainty
   - If it requires input from others: identify who and what to ask

5. Identify the fallback
   - If this question cannot be resolved before the deadline: what is the safest default?
   - How reversible is that default if the answer turns out to be different?

My open questions:
1. [Describe the question and what you know so far]
2. [Describe the question]
3. [Describe the question]

TDD context: [brief description of the feature being designed]
Timeline: [when does this decision need to be made?]
```
