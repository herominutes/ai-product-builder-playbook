# 🧪 Prompt Testing — AI Product Builder Playbook

> **A framework for systematically testing, iterating, and validating prompts before they reach production**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Prompt Testing Model](#the-prompt-testing-model)
- [Stage 1: Prompt Design](#stage-1-prompt-design)
- [Stage 2: Unit Testing](#stage-2-unit-testing)
- [Stage 3: Regression Testing](#stage-3-regression-testing)
- [Stage 4: A/B Testing](#stage-4-ab-testing)
- [Stage 5: Production Validation](#stage-5-production-validation)
- [Prompt Versioning and Management](#prompt-versioning-and-management)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Prompts are the most important engineering artefact in an AI product — and the most under-tested. A prompt change that takes 10 minutes to write can silently break a feature that took months to build. Without a systematic testing process, teams discover prompt regressions through user complaints rather than pre-deployment checks.

> **Core Principle:** A prompt is code. It should be version-controlled, tested before deployment, and evaluated against a fixed benchmark before any change goes to production. The intuition that "it seems better now" is not a test.

Prompt testing is also where the fastest quality improvements come from. Unlike model fine-tuning — which is expensive and slow — prompt iteration is cheap, fast, and directly controllable by the product team. A rigorous prompt testing framework turns this into a systematic improvement engine rather than a series of ad hoc experiments.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Writing a new system prompt for a new AI feature | 🔴 Critical — test before deployment |
| Making any change to an existing production prompt | 🔴 Critical — regression test before deploying |
| Quality metrics have declined after a recent prompt change | 🔴 Critical — bisect to find the regression |
| Evaluating whether a new prompt version is better than current | 🟠 High |
| Testing prompts across multiple model versions | 🟠 High |
| Building a prompt engineering culture on the team | 🟡 Medium |

---

## The Prompt Testing Model

Prompt testing moves through five stages. Each stage provides increasing confidence before a prompt reaches production.

```
PROMPT DESIGN
  ↓ structure the prompt with tested engineering principles
UNIT TESTING
  ↓ test the prompt against specific known cases
REGRESSION TESTING
  ↓ confirm the prompt does not break existing functionality
A/B TESTING
  ↓ compare new prompt against current in production
PRODUCTION VALIDATION
  ↓ confirm real-world performance after deployment
```

| Stage | Purpose | Environment | Confidence Level |
|---|---|---|---|
| **Prompt design** | Build prompts with proven structure | Development | Informed starting point |
| **Unit testing** | Verify specific behaviours | Development | High for tested cases |
| **Regression testing** | Confirm no existing behaviour broke | Staging | High for regression coverage |
| **A/B testing** | Compare against current prompt in production | Production | Statistically valid |
| **Production validation** | Monitor real-world quality after deployment | Production | Ground truth |

---

## Stage 1: Prompt Design

### 1.1 System Prompt Architecture

A well-structured system prompt is testable by design. Each section has a clear purpose and can be independently tested.

```
SYSTEM PROMPT ARCHITECTURE

Section 1 — Role definition
"You are [specific role] for [specific product]."
Test: Does the model stay in role when asked to act differently?

Section 2 — Scope definition
"Your purpose is to [specific task]. You only help with [explicit scope]."
Test: Does the model refuse out-of-scope requests? Does it accept in-scope requests?

Section 3 — Persona and tone
"Always respond in [tone]. Use [style]."
Test: Is tone consistent across varied inputs?

Section 4 — Format requirements
"Always format responses as [structure]. Maximum [N] words."
Test: Does every response follow the required format?

Section 5 — Safety and prohibitions
"Never [explicit prohibition 1]. Never [explicit prohibition 2]."
Test: Attempt each prohibition — does the model comply?

Section 6 — Uncertainty handling
"If uncertain, say so. Never present uncertain information as fact."
Test: Ask about something obscure — does the model express uncertainty or guess?

Section 7 — Edge case handling
"If asked [edge case], respond with [specific handling]."
Test: Test each documented edge case.
```

### 1.2 Prompt Engineering Principles

| Principle | Description | Test |
|---|---|---|
| **Specificity over ambiguity** | Specific instructions outperform vague ones | Compare specific vs vague instruction versions |
| **Positive instructions** | Tell the model what to do, not just what not to do | "Respond in bullet points" vs "Don't use prose" |
| **Ordered priority** | Earlier instructions take priority over later ones | Put most important constraints first |
| **Concrete examples** | Few-shot examples dramatically improve format compliance | Add 1–3 examples to critical format sections |
| **Single responsibility** | One clear task per prompt; decompose complex tasks | Measure quality vs task complexity |
| **Explicit output format** | Specify the exact output structure required | Validate output schema after every test |

### 1.3 Few-Shot Example Design

Few-shot examples are the most powerful prompt engineering technique available. Use them strategically:

```
FEW-SHOT EXAMPLE DESIGN

Number of examples: 1–3 (more is not always better — costs tokens)
Placement: After format instructions, before the user query
Selection criteria: Examples should represent the IDEAL output quality
Diversity: Cover different query types, formats, and difficulty levels

Example structure:
User: [representative user query]
Assistant: [ideal response that perfectly demonstrates the format and quality target]

Testing few-shot examples:
Test 1: Does the model follow the example format on similar queries?
Test 2: Does the model inappropriately copy content from examples?
Test 3: Does the model maintain the format on queries dissimilar to examples?
```

---

## Stage 2: Unit Testing

### 2.1 Unit Test Categories

A prompt unit test specifies an input and asserts a property of the output. Unlike traditional unit tests, LLM outputs are probabilistic — assertions must account for this.

| Test Category | What It Tests | Assertion Type |
|---|---|---|
| **Behaviour tests** | Does the prompt produce the right kind of output? | Contains / Does not contain / Matches pattern |
| **Format tests** | Does the output follow the required format? | Schema validation / Regex / JSON parse |
| **Safety tests** | Does the prompt correctly handle prohibited inputs? | Refusal detected / Prohibited content absent |
| **Edge case tests** | Does the prompt handle unusual inputs gracefully? | Output is reasonable / Uncertainty expressed |
| **Scope tests** | Does the prompt stay within intended boundaries? | Out-of-scope detected / In-scope accepted |
| **Length tests** | Does the output meet length constraints? | Token count within range |

### 2.2 Unit Test Specification

```
PROMPT UNIT TEST SPECIFICATION

Test ID: _______________________________________________
Prompt version: _______________________________________________
Test category: Behaviour / Format / Safety / Edge case / Scope / Length

Input:
[The exact input to the prompt]

Expected behaviour:
[ ] Output contains: [required element]
[ ] Output does not contain: [prohibited element]
[ ] Output matches format: [schema or pattern]
[ ] Output expresses uncertainty (if applicable)
[ ] Output is within [N] tokens
[ ] Output is in [required language/format]

Pass condition: ALL checked assertions are met
Fail condition: ANY checked assertion is not met

Run N times: ___  (recommended: 5–10 runs for probabilistic outputs)
Pass threshold: ___% of runs pass (recommended: > 90%)

Notes: _______________________________________________
```

### 2.3 Test Suite Structure

```
PROMPT TEST SUITE — [Feature Name / Prompt Version]

Category 1: Core behaviour tests (mandatory passing)
  Test 1.1: [name] — [description]
  Test 1.2: [name] — [description]
  Test 1.3: [name] — [description]

Category 2: Format compliance tests (mandatory passing)
  Test 2.1: [name] — [description]
  Test 2.2: [name] — [description]

Category 3: Safety tests (mandatory passing — 100% required)
  Test 3.1: Out-of-scope request 1 — [input]
  Test 3.2: Out-of-scope request 2 — [input]
  Test 3.3: Prohibited content request — [input]
  Test 3.4: Prompt injection attempt — [input]

Category 4: Edge case tests (target 90% passing)
  Test 4.1: [name] — [description]
  Test 4.2: [name] — [description]

Minimum passing criteria for production deployment:
  Category 1: 100% pass
  Category 2: 100% pass
  Category 3: 100% pass (no exceptions)
  Category 4: 90%+ pass
```

---

## Stage 3: Regression Testing

### 3.1 Regression Test Dataset

A regression test dataset captures the full set of cases that have previously worked correctly. Every prompt change must pass this dataset before deployment.

```
REGRESSION TEST DATASET CONSTRUCTION

Include in regression dataset:
[ ] All historical prompt test cases that currently pass
[ ] All past production failures (cases that previously caused issues)
[ ] All edge cases that were fixed in previous prompt iterations
[ ] All cases from user-reported issues that were resolved by prompt changes

Dataset size target:
Minimum: 50 test cases
Recommended: 150–200 test cases
Large features: 300+ test cases

Dataset format:
{
  test_id: "RT-001",
  version_introduced: "prompt_v2.1",
  input: "exact test input",
  expected_behaviour: {
    contains: ["required element"],
    not_contains: ["prohibited element"],
    format: "json | bullet_list | prose | schema"
  },
  category: "core | format | safety | edge_case",
  severity: "critical | high | medium"
}
```

### 3.2 Regression Testing Protocol

```
REGRESSION TEST PROTOCOL

Before deploying ANY prompt change:

Step 1 — Run full regression suite against new prompt version
  Tool: [your evaluation framework / LangSmith / PromptFoo / custom]
  Environment: Staging (same model version as production)

Step 2 — Review results
  All critical tests pass: Yes / No (if No: do not deploy)
  All safety tests pass: Yes / No (if No: do not deploy)
  High severity tests pass > 95%: Yes / No (if No: investigate)
  Medium severity tests pass > 90%: Yes / No (if No: investigate)

Step 3 — Regression diff analysis
  New failures vs prior version: [list any new failures]
  For each new failure: is this acceptable regression or a bug?

Step 4 — Deployment decision
  All mandatory tests pass + no unacceptable regressions: Deploy
  Any mandatory test fails: Fix prompt; re-run regression before deploying
```

### 3.3 Bisecting a Regression

When production quality has declined and you need to find which prompt change caused it:

```
REGRESSION BISECTION PROTOCOL

Step 1 — Identify the regression window
  When did quality decline? (use monitoring data)
  What prompt changes were made in that window? (use version history)

Step 2 — Binary search
  If 4 changes in window: test the version at the midpoint
  If midpoint passes: regression is in the second half
  If midpoint fails: regression is in the first half
  Repeat until the single failing change is identified

Step 3 — Confirm the regression
  Run full regression suite on version before the failing change (should pass)
  Run full regression suite on version after the failing change (should fail)

Step 4 — Fix or revert
  Option A: Revert to pre-regression prompt version
  Option B: Fix the specific issue introduced by the failing change
  Option C: Accept the regression if the change's benefits outweigh the cost
```

---

## Stage 4: A/B Testing

### 4.1 A/B Test Design

```
PROMPT A/B TEST DESIGN

Hypothesis:
"Prompt version B will [specific improvement] compared to Prompt version A,
as measured by [specific metric]."

Control (Prompt A): [current production prompt — describe key characteristics]
Treatment (Prompt B): [new prompt — describe what changed]

Traffic split: 50% A / 50% B
Duration: ___ days (minimum: enough to reach statistical significance)
Minimum sample size per variant: ___ interactions

Primary metric: _______________________________________________
Secondary metrics: _______________________________________________
Guardrail metrics (must not degrade): _______________________________________________

Statistical threshold:
Significance level: 95% (p < 0.05)
Minimum detectable effect: ___% improvement in primary metric

Success criteria:
  Primary metric improves by > ___% with p < 0.05
  Guardrail metrics do not degrade by > 5%
  Safety metrics do not degrade at all
```

### 4.2 A/B Test Statistical Analysis

```
A/B TEST STATISTICAL ANALYSIS

Sample sizes:
  Variant A: ___ interactions
  Variant B: ___ interactions

Primary metric results:
  Variant A mean: ___
  Variant B mean: ___
  Absolute difference: ___
  Relative improvement: ___%

Statistical test: [t-test / Mann-Whitney / chi-square — appropriate to metric type]
p-value: ___
Statistically significant: Yes (p < 0.05) / No

95% Confidence interval: [lower bound] to [upper bound]

Guardrail metrics:
  Safety score: A = ___ / B = ___ — Acceptable? Yes / No
  Latency: A = ___ ms / B = ___ ms — Acceptable? Yes / No
  Cost: A = $___ / B = $___ — Acceptable? Yes / No

Decision:
[ ] Ship Prompt B — statistically significant improvement, all guardrails pass
[ ] Continue test — not yet significant; need more data
[ ] Do not ship — no significant improvement OR guardrail violation
```

---

## Stage 5: Production Validation

### 5.1 Post-Deployment Monitoring

After any prompt change is deployed, monitor closely for the first 48 hours:

```
POST-DEPLOYMENT MONITORING PROTOCOL

Hour 0–4: Intensive monitoring
  Output sampling rate: 100%
  Quality evaluation: 100% via LLM judge
  Latency: Monitor P50, P95, P99
  Error rate: Monitor 5xx responses and format failures

Hour 4–24: Standard monitoring
  Output sampling rate: 25%
  Quality evaluation: 25% via LLM judge
  Compare: rolling metrics vs pre-deployment baseline

Hour 24–48: Normal monitoring
  Output sampling rate: Return to standard rate
  Watch for: user feedback signal (thumbs down, correction requests)
  Compare: quality score vs 7-day pre-deployment average

Rollback trigger:
  Quality score drops > 10% below baseline: Rollback immediately
  Safety failure confirmed: Rollback immediately
  Error rate > 2%: Rollback immediately
  User negative feedback rate > 3%: Investigate; rollback if cause is prompt change
```

---

## Prompt Versioning and Management

### 6.1 Version Control for Prompts

```
PROMPT VERSION CONTROL STANDARD

File naming: [feature_name]_system_prompt_v[major].[minor].[patch].txt

Version numbering:
  Major (v1.0.0 → v2.0.0): Structural change to prompt — new sections added or removed
  Minor (v1.0.0 → v1.1.0): Behavioural change — new instruction or constraint added
  Patch (v1.0.0 → v1.0.1): Wording improvement — no behavioural change intended

Each version file must include:
  - The full prompt text
  - Date created
  - Author
  - What changed from previous version
  - Link to the regression test results for this version
  - Deployment status: Draft / Tested / Staging / Production / Deprecated

Version history log:
v2.1.0 — [date] — [author] — Added uncertainty handling section — regression passed
v2.0.0 — [date] — [author] — Restructured scope section — regression passed — deployed [date]
v1.3.2 — [date] — [author] — Tightened format instruction — regression passed
```

### 6.2 Prompt Change Log Template

```
PROMPT CHANGE LOG ENTRY

Version: _______________________________________________
Date: _______________________________________________
Author: _______________________________________________
Feature: _______________________________________________

Change summary:
[One paragraph describing what changed and why]

Specific changes:
- Added: _______________________________________________
- Removed: _______________________________________________
- Modified: _______________________________________________

Expected impact:
[What improvement is this change expected to produce?]

Test results:
Unit tests: ___/___  pass
Regression tests: ___/___  pass
New failures (if any): _______________________________________________
Acceptable? Yes / No — because _______________________________________________

Deployment decision: Deploy / Hold / Revert
Deployed to production: [date]
Post-deployment monitoring result: Pass / Fail
```

---

## Templates

### Template A: Prompt Test Plan

```
# Prompt Test Plan — [Feature Name] — [Prompt Version]
Date: ___  |  Author: ___

## Prompt Under Test
Version: _______________________________________________
Key changes from prior version: _______________________________________________

## Test Suite Summary
Total tests: ___
Critical (must pass 100%): ___
High severity (must pass 95%+): ___
Medium severity (must pass 90%+): ___

## Test Execution Results
Critical: ___/___  pass  → Deploy gate: Pass / Fail
High: ___/___  pass  → Deploy gate: Pass / Fail
Medium: ___/___  pass  → Deploy gate: Pass / Fail
Safety: ___/___  pass  → Deploy gate: Pass / Fail

## Deployment Recommendation
[ ] Approved for staging
[ ] Approved for production A/B test
[ ] Hold — [issues to resolve]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Testing prompts manually with 2–3 queries | Systematic test suite with 50+ cases run before every change |
| Deploying prompt changes without regression testing | Mandatory regression gate — no exceptions |
| No version control for prompts | Prompts in version control with change log; treat like code |
| Evaluating prompts with "it looks better to me" | Evaluation against fixed dataset with measurable metrics |
| Testing only happy path cases | Include safety, edge case, and adversarial tests in every suite |
| No A/B test before major prompt changes | A/B test any change expected to meaningfully alter user experience |
| Post-deployment monitoring for only 1 hour | Monitor intensively for 48 hours after any prompt deployment |
| Shared prompts with no ownership | Every prompt has a named owner responsible for testing and maintenance |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Unit test execution | Per prompt change | Before any prompt is deployed |
| Regression test execution | Per prompt change | Mandatory gate before staging |
| A/B test design | Per major prompt version | Before significant prompt changes |
| Post-deployment monitoring | 48 hours after deployment | After every prompt deployment |
| Regression dataset refresh | Quarterly | Add new cases from production failures |
| Prompt audit (unused / outdated prompts) | Quarterly | Clean up deprecated versions |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design and Test a System Prompt

> **Best for:** Writing a new system prompt and building the initial test suite to validate it before deployment.

```
You are a prompt engineer helping me design and test a system prompt for my AI feature.

Part 1 — Design the system prompt:
Using the seven-section architecture, write a complete system prompt for my feature:
1. Role definition — specific and bounded
2. Scope definition — explicit in and out of scope
3. Persona and tone — specific communication style
4. Format requirements — exact output structure
5. Safety and prohibitions — explicit list of what the model must never do
6. Uncertainty handling — how to communicate uncertainty
7. Edge case handling — specific handling for known edge cases

Part 2 — Design the test suite:
Write 15 test cases covering:
- 5 core behaviour tests (common, typical inputs)
- 3 format compliance tests (verify output structure)
- 4 safety tests (out-of-scope, prohibited content, prompt injection)
- 3 edge case tests (unusual but valid inputs)

For each test case:
- Write the exact input
- Write the expected behaviour (what the output must contain / not contain / look like)
- Classify as Critical / High / Medium severity

My AI feature: [describe what it does]
User segment: [who uses it]
Topic domain: [what subject area]
Key behaviours required: [list the most important things the model must do]
Key prohibitions: [list the most important things the model must never do]
```

---

### Prompt 2 — Run a Prompt Regression Analysis

> **Best for:** After making a prompt change — systematically checking whether existing functionality has broken.

```
You are a QA engineer helping me run a regression analysis on a prompt change.

I will give you the old prompt, the new prompt, and my regression test cases. Your job is to:

1. Identify what changed between the two prompts — list every difference and its likely behavioural impact

2. For each test case in my regression suite:
   - Predict whether the new prompt will pass or fail this test
   - Explain why (which prompt change affects this test case)
   - Rate your prediction confidence: High / Medium / Low

3. Identify which test cases are highest risk — where the prompt change is most likely to introduce a regression

4. Identify any test cases that are likely to improve with the new prompt

5. Write 5 additional test cases you recommend adding to the regression suite to cover the specific changes made

After the analysis:
- Give an overall recommendation: Is this prompt change safe to deploy?
- List any specific tests I must manually verify before deploying

Old prompt: [paste]
New prompt: [paste]
Regression test cases: [paste or describe]
```

---

### Prompt 3 — Design a Prompt A/B Test

> **Best for:** Before deploying a significant prompt change — designing a rigorous A/B test to validate it in production.

```
You are a product experimentation specialist helping me design a prompt A/B test.

Design the complete A/B test:

1. Hypothesis
   Write a clear, falsifiable hypothesis: "Prompt B will [specific improvement] compared to Prompt A, as measured by [metric], because [reason for believing this]."

2. Test design
   - Traffic split recommendation (50/50 or other — justify)
   - Duration needed for statistical significance (given my traffic volume)
   - Minimum sample size per variant
   - Primary metric (the one metric that determines success)
   - Secondary metrics (additional signals)
   - Guardrail metrics (metrics that must not degrade — if they do, stop the test)

3. Statistical analysis plan
   - Which statistical test should I use for my primary metric?
   - What significance level (alpha) should I use?
   - How do I interpret the results?
   - What should I do if the test is inconclusive after the planned duration?

4. Rollback criteria
   - At what point should I stop the test and revert?
   - Who makes the rollback decision?
   - How quickly can I roll back?

5. Post-test analysis template
   - Write the analysis template I should fill in after the test completes

Prompt A (control): [describe current prompt key characteristics]
Prompt B (treatment): [describe new prompt and what changed]
Expected improvement: [what specific improvement do you expect?]
Traffic volume: [daily interactions]
```

---

### Prompt 4 — Write a Prompt Improvement Plan

> **Best for:** When quality metrics are below target and you need a systematic plan to improve the prompt.

```
You are a prompt optimisation specialist helping me systematically improve a prompt that is underperforming.

I will share the current prompt, the evaluation results, and the specific failure patterns. Your job is to:

1. Root cause analysis
   - For each failure category: what in the current prompt is causing this failure?
   - Is this a prompt engineering problem, a model capability limitation, or an evaluation problem?

2. Improvement hypotheses
   - For each root cause: write a specific prompt change that should fix it
   - Rank changes by expected impact (high / medium / low)
   - Identify any changes that might have side effects on other test cases

3. Prioritised improvement plan
   - Change 1 (highest impact, lowest risk): [specific change]
   - Change 2: [specific change]
   - Change 3: [specific change]

4. For each proposed change, write:
   - The exact new wording or section to add
   - The test cases that should improve if this change works
   - The test cases that might regress (risk assessment)

5. Testing sequence
   - In what order should I test these changes?
   - Should I test them individually or can I batch them?

Current prompt: [paste]
Evaluation results: [describe what's failing and the scores]
Most common failure patterns: [describe]
Quality target: [what score or behaviour are you trying to achieve?]
```

---

### Prompt 5 — Build a Prompt Test Automation System

> **Best for:** Setting up automated prompt testing that runs before every deployment without manual effort.

```
You are a DevOps engineer specialising in AI systems helping me build an automated prompt testing system.

Design the complete automated testing pipeline:

1. Test definition format
   - Write the JSON schema for a prompt test case
   - Include: input, expected behaviour (contains / not_contains / schema / regex), category, severity, run_count, pass_threshold

2. Test runner design
   - Write the pseudocode or Python outline for a test runner that:
     - Loads the prompt under test
     - Loads the test suite
     - Runs each test N times (to handle probabilistic outputs)
     - Applies each assertion
     - Calculates pass rate per test and per category
     - Generates a pass/fail report

3. CI/CD integration
   - Where in the deployment pipeline should prompt tests run?
   - What should happen if tests fail? (block deploy / warn / log)
   - How should test results be stored for tracking over time?

4. Test result reporting
   - Design the test result report format
   - What should appear in the pass/fail summary?
   - How should regressions be highlighted (new failures vs existing)?

5. Tooling recommendations
   - Which existing tools should I use or build on? (PromptFoo / LangSmith / custom)
   - Estimated setup time for the complete system
   - Estimated ongoing maintenance effort

My tech stack: [describe your engineering environment]
Prompt deployment process: [how do prompts currently get to production?]
Team size: [how many engineers will maintain this?]
Budget for tooling: $[monthly]
```
