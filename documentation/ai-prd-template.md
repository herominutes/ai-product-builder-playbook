# 📋 AI PRD Template — AI Product Builder Playbook

> **A comprehensive product requirements document template designed specifically for AI-powered features and products**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Template](#when-to-use-this-template)
- [How an AI PRD Differs from a Standard PRD](#how-an-ai-prd-differs-from-a-standard-prd)
- [Section 1: Problem and Opportunity](#section-1-problem-and-opportunity)
- [Section 2: User and Context](#section-2-user-and-context)
- [Section 3: AI Solution Design](#section-3-ai-solution-design)
- [Section 4: AI-Specific Requirements](#section-4-ai-specific-requirements)
- [Section 5: Success Metrics](#section-5-success-metrics)
- [Section 6: Risks and Mitigations](#section-6-risks-and-mitigations)
- [Section 7: Launch and Rollout Plan](#section-7-launch-and-rollout-plan)
- [Full PRD Template](#full-prd-template)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A Product Requirements Document for an AI feature is not a traditional PRD with "AI" added to the technology section. AI introduces requirements that standard PRDs are not designed to capture: output quality thresholds, latency budgets, hallucination risk, model selection rationale, fallback behaviour, trust design, and the evaluation framework needed to know whether the AI is working.

> **Core Principle:** An AI PRD must answer questions that a traditional PRD never asks. What happens when the model is wrong? How will we know the quality is good enough before launch? What does the user experience when the AI fails? A PRD that cannot answer these is incomplete — and the gaps will surface in production.

This template is designed to be used before any AI feature development begins. It serves three audiences simultaneously: the product team (alignment on what to build), the engineering team (clarity on what to implement), and the business (confidence that the investment is sound).

---

## When to Use This Template

| Trigger | Priority |
|---|---|
| Starting any new AI feature or product | 🔴 Critical — complete before design begins |
| Existing feature is being enhanced with AI | 🔴 Critical — document the AI layer specifically |
| Handoff from product to engineering for an AI feature | 🔴 Critical — engineering needs AI-specific clarity |
| Stakeholder approval required for AI investment | 🟠 High — PRD is the approval document |
| Post-launch retrospective on an AI feature | 🟡 Medium — compare what was built vs what was specified |

---

## How an AI PRD Differs from a Standard PRD

| Standard PRD Section | AI PRD Addition |
|---|---|
| Problem statement | + AI appropriateness assessment (is AI the right solution?) |
| User requirements | + AI trust requirements (how does the user need to feel about AI outputs?) |
| Functional requirements | + AI behaviour requirements (what should the model do AND not do?) |
| Non-functional requirements | + Latency budget, quality threshold, hallucination tolerance |
| Success metrics | + AI-specific metrics (quality score, acceptance rate, refusal rate) |
| Risks | + AI-specific risks (hallucination, bias, trust erosion, cost explosion) |
| Launch plan | + AI evaluation gates (what must be true before AI goes to production?) |

---

## Section 1: Problem and Opportunity

### 1.1 Problem Statement

```
PROBLEM STATEMENT

Target user: _______________________________________________
Situation / context: _______________________________________________
Core problem: _______________________________________________
Root cause of the problem: _______________________________________________
Evidence the problem is real:
  - Data point: _______________________________________________
  - User research finding: _______________________________________________
  - Business signal: _______________________________________________

Consequence of the problem (what it costs users today):
  Time: _______________________________________________
  Quality: _______________________________________________
  Opportunity cost: _______________________________________________
```

### 1.2 AI Appropriateness Assessment

Before specifying the AI solution, confirm that AI is the right tool for this problem:

```
AI APPROPRIATENESS ASSESSMENT

[ ] The problem is well-defined enough for AI to solve consistently
    (If not: define the problem more precisely before specifying AI)

[ ] There is sufficient volume / frequency to justify AI investment
    Current volume: ___ [tasks/queries/interactions] per [day/week/month]
    Threshold for AI investment justification: ___

[ ] The required data is available or can be acquired
    Data needed: _______________________________________________
    Data availability: Available now / Buildable / Not available

[ ] The acceptable error rate is defined and AI can meet it
    Acceptable error rate: ___%
    Expected AI error rate: ___%

[ ] User control and override is designed for when AI is wrong
    Override mechanism: _______________________________________________

[ ] Accountability is defined for AI errors
    Who is responsible: _______________________________________________

AI appropriateness verdict:
[ ] Proceed with AI — all criteria met
[ ] Proceed with conditions — [specify conditions]
[ ] Do not use AI — [specify reason and alternative approach]
```

### 1.3 Opportunity Sizing

```
OPPORTUNITY SIZING

Time value opportunity:
  Current time to complete task manually: ___ [minutes/hours]
  AI-assisted time target: ___ [minutes/hours]
  Time saved per user per [day/week]: ___
  × Target user base: ___
  = Total time value: ___ hours/[period]
  At $___/hour: $___/[period]

Quality opportunity:
  Current quality/error rate: ___%
  Target AI quality/error rate: ___%
  Business impact of quality improvement: $___/[period]

Scale opportunity:
  Tasks currently impossible due to volume: _______________________________________________
  Value unlocked by AI enabling scale: $_______________________________________________

Total opportunity value: $_______________________________________________
AI investment required: $_______________________________________________
Expected ROI: ____%  |  Payback period: ___ months
```

---

## Section 2: User and Context

### 2.1 Primary Persona

```
PRIMARY USER PERSONA

Name / descriptor: _______________________________________________
Role and context: _______________________________________________
Core job to be done: _______________________________________________

AI literacy level: Naive / Curious / Confident / Expert
Trust propensity: Over-trusting / Calibrated / Under-trusting / Avoidant
Control preference: High autonomy / Collaborative / Delegating / Supervisory

Primary AI anxiety for this use case:
_______________________________________________

Primary AI motivation for this use case:
_______________________________________________

What would make this user adopt this AI feature:
_______________________________________________

What would make this user reject or abandon it:
_______________________________________________
```

### 2.2 User Journey with AI

```
USER JOURNEY — AI INTERACTION MAP

Pre-interaction:
  User's context when they arrive: _______________________________________________
  What they expect AI to do: _______________________________________________
  Trust level at arrival: Low / Medium / High

First AI interaction:
  What the user inputs: _______________________________________________
  What the AI should produce: _______________________________________________
  What success looks like: _______________________________________________
  What failure looks like: _______________________________________________
  Failure recovery path: _______________________________________________

Ongoing interaction (habit phase):
  How the interaction changes as trust builds: _______________________________________________
  What power-user behaviour looks like: _______________________________________________

Trust signals designed:
  How does the user know the AI is reliable? _______________________________________________
  How does the user know when to verify the AI output? _______________________________________________
  How does the user override or correct the AI? _______________________________________________
```

---

## Section 3: AI Solution Design

### 3.1 Solution Overview

```
AI SOLUTION OVERVIEW

Feature name: _______________________________________________
Feature type: Generation / Classification / Extraction / Summarisation / Recommendation / Planning / Search / Other

What the AI does:
  Input: [what enters the AI — user query, document, data, context]
  Process: [what the AI does — generate, classify, extract, etc.]
  Output: [what the AI produces — text, structured data, decision, recommendation]

What the AI does NOT do (explicit scope boundary):
_______________________________________________

How the user interacts with the AI output:
  [ ] Reads and acts on it
  [ ] Edits and publishes it
  [ ] Approves or rejects it
  [ ] Passes it to the next step in a workflow
```

### 3.2 AI Architecture Decision

```
AI ARCHITECTURE DECISIONS

Model approach:
  [ ] Single LLM call — simple task, one output
  [ ] Prompt chain — sequential multi-step processing
  [ ] RAG — retrieval-augmented generation (grounded in documents)
  [ ] Agent — autonomous multi-step task completion
  [ ] Fine-tuned model — domain-specific behaviour
  [ ] Hybrid — [describe combination]

Model selection:
  Recommended model: _______________________________________________
  Rationale: [quality threshold met at acceptable cost + latency]
  Alternative considered: _______________________________________________
  Why alternative was rejected: _______________________________________________

RAG design (if applicable):
  Knowledge sources: _______________________________________________
  Chunking strategy: _______________________________________________
  Retrieval method: Dense / Sparse / Hybrid
  Re-ranking: Yes / No

Cost model:
  Estimated tokens per interaction: Input ___ / Output ___
  Estimated cost per interaction: $___
  Estimated monthly cost at [N] interactions/day: $___
  Cost budget: $___/month — Within budget? Yes / No
```

### 3.3 System Prompt Requirements

```
SYSTEM PROMPT REQUIREMENTS

Role definition (what the AI must be):
_______________________________________________

Scope constraints (what the AI must only do):
_______________________________________________

Explicit prohibitions (what the AI must never do):
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

Tone and format requirements:
  Tone: _______________________________________________
  Output format: _______________________________________________
  Max response length: ___ tokens

Uncertainty handling:
  When uncertain, the AI must: _______________________________________________

Out-of-scope handling:
  When asked something outside scope, the AI must: _______________________________________________

Few-shot examples required: Yes / No
  If yes: [describe the examples to include]
```

---

## Section 4: AI-Specific Requirements

### 4.1 Quality Requirements

```
QUALITY REQUIREMENTS

Quality threshold for production deployment:
  Overall quality score (1–5): > ___
  Relevance score: > ___
  Faithfulness score (RAG): > ___
  Completeness score: > ___
  Format compliance rate: > ___%

Evaluation dataset:
  Size: ___ examples
  Source: _______________________________________________
  Ground truth: _______________________________________________

Evaluation method:
  [ ] LLM-as-judge (automated)
  [ ] Human evaluation (n = ___ evaluators)
  [ ] Automated schema validation
  [ ] Ground truth comparison

Quality gate: Feature does not launch until quality threshold is met and verified.
```

### 4.2 Latency Requirements

```
LATENCY REQUIREMENTS

User-facing latency:
  Target P50 latency: ___ ms
  Maximum acceptable P99 latency: ___ ms

Latency budget breakdown:
  Retrieval (if RAG): ___ ms
  Model inference: ___ ms
  Post-processing: ___ ms
  Infrastructure overhead: ___ ms
  Total budget: ___ ms

If latency target is exceeded:
  [ ] Show progress indicator at ___ ms
  [ ] Switch to async processing at ___ ms
  [ ] Return partial result at ___ ms
  [ ] Return cached result for similar queries
```

### 4.3 Safety and Guardrail Requirements

```
SAFETY AND GUARDRAIL REQUIREMENTS

Input guardrails required:
  [ ] Input length validation (max: ___ tokens)
  [ ] PII detection and handling
  [ ] Prompt injection detection
  [ ] Out-of-scope classification
  [ ] Content pre-screening

Output guardrails required:
  [ ] Toxicity / harmful content filter
  [ ] PII in output scanner
  [ ] Hallucination detection (for factual tasks)
  [ ] Format validation
  [ ] Output length limit (max: ___ tokens)

Content filter trigger rate target: < ___%
  (Too high = over-restrictive; Too low = under-protective)

Human review required:
  [ ] For all outputs above [risk threshold]
  [ ] For [specific output type] — always
  [ ] Sampled at ___%

Fallback behaviour (when AI fails or is filtered):
  [ ] Return canned response: [describe]
  [ ] Offer human escalation
  [ ] Return partial result with caveat
  [ ] Fail gracefully with error message
```

### 4.4 Reliability Requirements

```
RELIABILITY REQUIREMENTS

Availability SLA: > ___%
  If AI is unavailable: [fallback behaviour]

Error rate SLA: < ___%
  On breach: [alert and response]

Cost circuit breaker:
  Daily cost limit: $___
  On breach: [rate limit / disable / alert]

Model version pinning:
  [ ] Pin to specific model version (prevents silent quality changes)
  [ ] Auto-update to latest version
  [ ] Notify PM on model version change

Monitoring required from day 1:
  [ ] Quality score sampling (___% of outputs)
  [ ] Latency monitoring (P50, P95, P99)
  [ ] Cost per interaction tracking
  [ ] Content filter trigger rate
  [ ] User feedback signal (thumbs up/down)
```

---

## Section 5: Success Metrics

### 5.1 AI Feature Success Metrics

```
SUCCESS METRICS

Primary metric (North Star for this feature):
  Metric: _______________________________________________
  Definition: _______________________________________________
  Target: _______________________________________________
  Measurement: _______________________________________________

AI-specific metrics:
  AI adoption rate: ___% of eligible users use the feature per week — Target: ___%
  AI output acceptance rate: ___% of outputs used without modification — Target: ___%
  AI task completion rate: ___% of AI tasks reach successful outcome — Target: ___%
  AI quality score (automated): ___ / 5 — Target: > ___
  User satisfaction with AI: ___ / 5 — Target: > ___

Counter metrics (must not decline):
  Overall feature satisfaction: _______________________________________________
  Session length / engagement: _______________________________________________
  Support ticket volume: _______________________________________________

Leading indicators (for monitoring before primary metric matures):
  _______________________________________________

Timeline for primary metric to show impact: ___ weeks after launch
```

### 5.2 Launch Success Criteria

```
LAUNCH SUCCESS CRITERIA

Week 1 post-launch:
  [ ] Quality score > ___ on production sample
  [ ] Error rate < ___%
  [ ] No P1 safety incidents

Month 1 post-launch:
  [ ] AI adoption rate > ___%
  [ ] AI output acceptance rate > ___%
  [ ] User satisfaction score > ___

Month 3 post-launch:
  [ ] Primary metric improved by > ___% vs baseline
  [ ] Counter metrics within acceptable range
  [ ] Cost per interaction within budget model

If criteria not met at any checkpoint:
  Action: [iterate / investigate / rollback]
  Owner: _______________________________________________
```

---

## Section 6: Risks and Mitigations

### 6.1 AI Risk Register

```
AI RISK REGISTER

| Risk | Likelihood (1–5) | Impact (1–5) | Score | Mitigation | Owner |
|------|-----------------|-------------|-------|------------|-------|
| Hallucination in [domain] | | | | | |
| Model quality regression on upgrade | | | | | |
| Cost explosion from unexpected usage | | | | | |
| User trust erosion from AI failures | | | | | |
| PII in AI outputs | | | | | |
| Prompt injection attack | | | | | |
| Latency SLA breach | | | | | |
| [Domain-specific risk] | | | | | |

Critical risks (score > 15) must be mitigated before launch.
High risks (score 10–15) must have documented mitigation plans.
```

### 6.2 Contingency Plan

```
CONTINGENCY PLAN

If AI quality is below threshold at launch:
  Action: _______________________________________________
  Owner: _______________________________________________
  Timeline: _______________________________________________

If user adoption is below target at Month 1:
  Action: _______________________________________________
  Owner: _______________________________________________

If a P1 safety incident occurs:
  Immediate action: Disable AI feature / Rate limit / Alert on-call
  Communication: [internal / external / both]
  Owner: _______________________________________________

If cost exceeds budget by > 50%:
  Action: _______________________________________________
  Owner: _______________________________________________
```

---

## Section 7: Launch and Rollout Plan

### 7.1 Pre-Launch Evaluation Gate

```
PRE-LAUNCH EVALUATION GATE

The feature may not launch until ALL of the following are confirmed:

Quality gate:
  [ ] Evaluation dataset run — quality score > ___
  [ ] Safety evaluation — safety score > 95%
  [ ] Hallucination rate within acceptable threshold

Engineering gate:
  [ ] Latency P99 < ___ ms in staging
  [ ] Cost per interaction confirmed within budget
  [ ] All guardrails implemented and tested
  [ ] Monitoring dashboard live

Governance gate:
  [ ] AI risk assessment complete and approved
  [ ] Privacy / data flow audit complete
  [ ] Legal sign-off (if required by domain)

Product gate:
  [ ] User testing with target segment complete (minimum 5 users)
  [ ] Failure state and recovery path tested
  [ ] Rollback plan documented
```

### 7.2 Rollout Sequence

```
ROLLOUT SEQUENCE

Phase 1 — Internal / Dogfood (Week 1–2)
  Audience: Internal team members
  Purpose: Catch gross quality failures and edge cases
  Monitoring: 100% output review
  Gate to Phase 2: No P1 failures; quality score stable

Phase 2 — Beta (Week 3–6)
  Audience: __% of [segment / waitlist / power users]
  Purpose: Validate quality and adoption with real users
  Monitoring: 25% output sampling + feedback signal
  Gate to Phase 3: Quality > ___ / Adoption > ___% / No P1s

Phase 3 — General Availability (Week 7+)
  Audience: All eligible users
  Rollout: [% per day / per week]
  Monitoring: 10% output sampling ongoing
  Rollback trigger: Quality drops > 15% below beta benchmark

Feature flag: [name] — controlled by [system]
Rollback time to 0%: < ___ minutes
```

---

## Full PRD Template

```
# AI PRD: [Feature Name]
Status: Draft / In Review / Approved / In Development / Launched
Date: ___  |  Author: ___  |  Version: ___  |  Decision needed by: ___

## Executive Summary
[2–3 sentences: what, for whom, why now, and expected impact]

## Problem and Opportunity
[Complete Section 1 above]

## User and Context
[Complete Section 2 above]

## AI Solution Design
[Complete Section 3 above]

## AI-Specific Requirements
[Complete Section 4 above]

## Success Metrics
[Complete Section 5 above]

## Risks and Mitigations
[Complete Section 6 above]

## Launch and Rollout Plan
[Complete Section 7 above]

## Open Questions
| Question | Owner | Due Date | Status |
|----------|-------|----------|--------|
| | | | |

## Decision Log
| Decision | Rationale | Date | Decided by |
|---------|-----------|------|------------|
| | | | |

## Approvals Required
[ ] PM lead  [ ] Engineering lead  [ ] Design lead  [ ] Legal (if required)  [ ] CPO
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Standard PRD with "uses AI" in the technology section | AI PRD is a distinct document — use this template |
| No AI appropriateness assessment | Always confirm AI is the right solution before specifying it |
| Quality threshold not defined before development | Define the quality bar before engineering begins — not after |
| No failure state designed | Every AI PRD must include failure behaviour specification |
| No pre-launch evaluation gate | AI features must pass a quality gate before reaching users |
| Latency requirements missing | Define P50 and P99 latency budgets before architecture is chosen |
| Risk register omitted | AI risk register is mandatory — not optional |
| No rollback plan | Document the rollback procedure before launch, not after a P1 incident |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Write a Complete AI PRD

> **Best for:** Creating a full AI PRD for a new AI feature from scratch.

```
You are a senior product manager helping me write a complete AI PRD for a new feature.

Guide me through each section in sequence. For each section, ask me the key questions, then draft the section based on my answers. Flag any answer that contains an assumption not yet validated with users or data.

Sections to complete:
1. Problem and opportunity — including AI appropriateness assessment and opportunity sizing
2. User and context — persona, AI trust profile, and user journey with AI
3. AI solution design — architecture decision, system prompt requirements, cost model
4. AI-specific requirements — quality threshold, latency budget, safety guardrails, reliability
5. Success metrics — primary metric, AI-specific metrics, counter metrics
6. Risks and mitigations — AI risk register and contingency plan
7. Launch and rollout plan — pre-launch evaluation gate and rollout sequence

After all sections, write the executive summary and identify the top 3 open questions that must be resolved before engineering begins.

Feature I am building: [describe the AI feature — what it does, who it serves, what problem it solves]
Target user: [describe]
My current thinking on the AI approach: [describe if you have one]
Known constraints: [latency requirements, cost constraints, data availability, etc.]
```

---

### Prompt 2 — Define AI Quality Requirements

> **Best for:** Specifying the quality threshold, evaluation dataset, and measurement approach for an AI feature before development begins.

```
You are an AI quality engineer helping me define the quality requirements for an AI feature in my PRD.

Design the complete quality requirements section:

1. Quality threshold definition
   - What quality dimensions apply to my feature? (relevance, faithfulness, completeness, format compliance, calibration)
   - For each dimension, what is the minimum acceptable score for production launch?
   - Write the quality rubric (1–5 criteria) for each dimension specific to my use case

2. Evaluation dataset design
   - How many examples do I need for statistical significance?
   - What distribution of query types should the dataset contain? (common / edge case / adversarial)
   - Who should create the ground truth labels?

3. Evaluation method
   - Should I use LLM-as-judge, human evaluation, or automated metrics for this feature?
   - Write the LLM-as-judge prompt for my specific use case
   - How often should I run the full evaluation in production?

4. Quality gate specification
   - Write the exact pre-launch quality gate: what must be true before this feature goes to production?
   - What monitoring must be live on day 1?
   - What triggers an immediate rollback?

My AI feature: [describe what the AI does]
Feature domain: [what topic area — factual / creative / analytical / other]
Whether I use RAG: [yes/no]
Risk level: [low / medium / high — what's the consequence of a bad output?]
```

---

### Prompt 3 — Design the Failure State and Recovery Path

> **Best for:** Ensuring every failure mode of an AI feature is designed before engineering begins.

```
You are a UX designer specialising in AI failure states helping me design the failure experience for my AI feature.

Map every failure mode and design the user experience for each:

1. Quality failure — AI produces an output that is wrong or unhelpful
   - What does the user see?
   - How do they correct or override the AI?
   - How do they signal the failure to the product (feedback mechanism)?

2. Safety filter trigger — AI declines to complete the request
   - What does the user see? (non-judgmental, clear message)
   - What alternative do they have?
   - How do we avoid over-triggering? (if refusal rate > 10%, filters are too tight)

3. Latency failure — AI takes longer than expected
   - At what latency does a progress indicator appear?
   - At what latency does the experience switch to async?
   - What does the user see while waiting?

4. Complete failure — AI system is unavailable
   - What is the fallback experience? (non-AI version / manual path / error message)
   - Is the user notified? How?
   - How quickly is the fallback engaged?

5. Trust failure — user does not believe the AI output
   - What transparency features help the user evaluate the output?
   - How can the user see the source or reasoning?
   - What is the escalation path to human review?

For each failure mode: write the exact UI copy, the system behaviour, and the recovery action.

My AI feature: [describe]
User segment: [who uses it and how tech-savvy are they?]
Risk level: [what's the worst consequence of an AI failure?]
Current error handling: [what exists today, if anything?]
```

---

### Prompt 4 — Write the AI Risk Register

> **Best for:** Identifying and documenting all AI-specific risks in the PRD before engineering begins.

```
You are an AI risk specialist helping me write a complete risk register for an AI PRD.

Identify and assess risks across five categories:

1. Output quality risks — hallucination, outdated information, incomplete output, overconfidence
2. Safety and harm risks — harmful content, bias, manipulation risk
3. Privacy and data risks — PII in outputs, data sharing, cross-user leakage
4. Operational risks — cost explosion, latency SLA breach, model deprecation, provider outage
5. User trust risks — trust erosion from AI failures, adoption risk, bypass risk

For each risk:
- Rate likelihood (1–5) and impact (1–5) — calculate score (likelihood × impact)
- Write a specific mitigation (not generic — specific to my feature)
- Assign an owner
- Classify as: Critical (score > 15, must fix before launch) / High (10–15) / Medium (6–9) / Low (< 6)

After the full register:
- Identify the top 3 risks that must be resolved before this feature launches
- Write the contingency plan for the single highest-risk scenario
- Identify any risk that should escalate to Legal or CPO for sign-off

My AI feature: [describe what it does]
User segment: [who uses it]
Domain: [what topic area — medical / legal / financial / general]
Data processed: [what user data enters the AI system]
Model provider: [which provider]
```

---

### Prompt 5 — Review and Critique an Existing AI PRD

> **Best for:** Quality-checking a drafted AI PRD before it goes to engineering or stakeholder review.

```
You are a senior product leader reviewing an AI PRD before engineering kickoff.

Review the PRD I share against these criteria:

1. Problem clarity
   - Is the problem statement specific and evidence-backed?
   - Has AI appropriateness been confirmed? Or is AI assumed without justification?

2. AI solution completeness
   - Is the architecture decision documented with rationale?
   - Is the system prompt requirements section complete enough for an engineer to implement?
   - Is the cost model present and within budget?

3. Quality requirements
   - Is the quality threshold defined before launch?
   - Is the evaluation dataset and method specified?
   - Is the pre-launch quality gate written?

4. Safety and failure design
   - Is the failure state designed for every failure mode?
   - Are guardrail requirements specified?
   - Is the rollback plan documented?

5. Success metrics
   - Are AI-specific metrics included (not just standard product metrics)?
   - Are counter metrics defined?
   - Is the primary metric specific enough to determine success?

6. Risk completeness
   - Is the AI risk register present?
   - Are critical risks (score > 15) addressed?

For each criterion: verdict (Complete / Needs work / Missing) + specific feedback.
End with: the top 3 changes required before this PRD is ready for engineering kickoff.

PRD to review: [paste your PRD content]
```
