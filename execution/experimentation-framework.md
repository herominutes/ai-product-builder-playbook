# 🧪 Experimentation Framework — AI Product Builder Playbook

> **A structured framework for designing, running, and learning from product experiments that produce reliable, actionable results**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Experimentation Model](#the-experimentation-model)
- [Stage 1: Hypothesis Formation](#stage-1-hypothesis-formation)
- [Stage 2: Experiment Design](#stage-2-experiment-design)
- [Stage 3: Statistical Foundations](#stage-3-statistical-foundations)
- [Stage 4: Experiment Execution](#stage-4-experiment-execution)
- [Stage 5: Analysis and Decision](#stage-5-analysis-and-decision)
- [Experimentation for AI Products](#experimentation-for-ai-products)
- [Building an Experimentation Culture](#building-an-experimentation-culture)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Experimentation is the only reliable method for distinguishing between changes that genuinely improve the product and changes that feel like improvements. Intuition, user feedback, and qualitative research generate hypotheses. Experiments validate them. A team without a rigorous experimentation practice is making product decisions based on the loudest voice in the room — which is rarely the user's.

> **Core Principle:** An experiment that does not change a decision is a waste. Before running any experiment, the team must pre-commit to the decision rule — what result will cause us to ship, what result will cause us to stop. Without this pre-commitment, experiments become post-hoc justifications for decisions already made.

For AI products, experimentation has an additional layer of complexity. AI outputs are probabilistic, which means the treatment and control experiences are not perfectly consistent. Measuring the impact of an AI feature change requires careful design to distinguish AI quality effects from other confounds.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Before shipping any significant product change | 🔴 Critical — validate before full rollout |
| A metric has moved and you need to understand why | 🔴 Critical — controlled experiment isolates cause |
| Two design options exist and the team cannot agree | 🟠 High — run the experiment instead of debating |
| A new AI feature or prompt change is ready for production | 🟠 High — AI changes require rigorous testing |
| Quarterly planning — validating assumptions before committing | 🟡 Medium |
| Building experimentation discipline in a new team | 🟡 Medium |

---

## The Experimentation Model

Rigorous experimentation follows five stages. Skipping any stage produces unreliable results.

```
HYPOTHESIS FORMATION
  ↓ what do we believe and why?
EXPERIMENT DESIGN
  ↓ how do we test it reliably?
STATISTICAL FOUNDATIONS
  ↓ how confident can we be in the result?
EXPERIMENT EXECUTION
  ↓ running the test with integrity
ANALYSIS AND DECISION
  ↓ what did we learn and what do we do?
```

| Stage | Core Question | Key Output | Common Failure |
|---|---|---|---|
| **Hypothesis** | What do we believe and why? | Testable hypothesis statement | Vague or untestable hypothesis |
| **Design** | How do we test it without bias? | Experiment spec with decision rules | No pre-registered decision rule |
| **Statistics** | How confident can we be? | Sample size + significance plan | Underpowered experiment |
| **Execution** | Are we running it with integrity? | Clean experiment with no interference | Peeking at results early |
| **Analysis** | What did we learn? | Decision + documented learning | Ignoring inconclusive results |

---

## Stage 1: Hypothesis Formation

### 1.1 The Hypothesis Standard

A hypothesis that cannot be falsified is not a hypothesis. Every experiment hypothesis must specify both the expected outcome and the counter-signal that would prove it wrong.

```
HYPOTHESIS FORMAT

"We believe that [specific user] will [specific behaviour change]
if [specific product change],
because [insight or evidence that supports this belief].

We will know this is true when [primary metric] improves by [minimum detectable effect]
with statistical significance (p < 0.05).

We will know this is false when [primary metric] shows no improvement
or degrades after [planned experiment duration]."
```

### 1.2 Hypothesis Quality Checklist

```
HYPOTHESIS QUALITY CHECKLIST

[ ] Testable: Can this be measured with available instrumentation?
[ ] Specific: Does it name the specific user, change, and outcome?
[ ] Falsifiable: Is there a result that would definitively prove it wrong?
[ ] Grounded: Is there a specific insight or evidence driving this belief?
[ ] Actionable: Will the result change what we do?
[ ] Independent: Is this the only change being made (no confounds)?
[ ] Pre-registered: Is the success criterion defined before looking at data?
```

### 1.3 Hypothesis Backlog Management

```
HYPOTHESIS BACKLOG

| ID | Hypothesis summary | Driving insight | Confidence | Expected impact | Effort to test | Priority |
|----|-------------------|----------------|------------|-----------------|---------------|----------|
| H1 | | | H/M/L | H/M/L | S/M/L | |
| H2 | | | | | | |

Prioritisation rule:
High priority: High confidence + High impact + Small/Medium effort
Medium priority: Medium on any two dimensions
Low priority: Low confidence OR low impact OR large effort

Maximum active experiments simultaneously: ___
(More simultaneous experiments = higher risk of interaction effects)
```

---

## Stage 2: Experiment Design

### 2.1 Experiment Types

| Experiment Type | Description | When to Use |
|---|---|---|
| **A/B test** | Two variants, random assignment | Default — comparing one change |
| **A/B/n test** | Multiple variants simultaneously | Comparing multiple options efficiently |
| **Multivariate test** | Multiple changes tested in combination | Understanding interaction effects (requires large sample) |
| **Holdout test** | A % of users never receive a feature | Measuring long-term impact of shipped features |
| **Switchback test** | Time-based randomisation | When user-level randomisation is not possible |
| **Bandit test** | Adaptive allocation to better-performing variant | When speed of learning matters more than statistical purity |

### 2.2 Experiment Specification Template

```
EXPERIMENT SPECIFICATION

Experiment ID: _______________________________________________
Hypothesis: [full hypothesis statement]
Owner: _______________________________________________  |  Start date: ___

DESIGN

Control (A): [exactly what does the control group experience?]
Treatment (B): [exactly what does the treatment group experience?]
  — Be precise. "Improved onboarding" is not a treatment. "Added an AI-generated
    task suggestion on the empty state screen" is a treatment.

Randomisation unit: User / Session / Account / Device
  Rationale: _______________________________________________

Traffic split: ___% Control  /  ___% Treatment
  Rationale for split: _______________________________________________

Eligible population: _______________________________________________
  Exclusions: _______________________________________________

METRICS

Primary metric: [one metric that determines the go/no-go decision]
  Definition: _______________________________________________
  Measurement: _______________________________________________

Secondary metrics: [supporting signals — do not use for the go/no-go decision]
  1. _______________________________________________
  2. _______________________________________________

Guardrail metrics: [metrics that must NOT degrade — if they do, stop the test]
  1. _______________________________________________
  2. _______________________________________________

DECISION RULES (pre-registered before experiment launches)

Ship if: Primary metric improves by ≥ [X]% with p < 0.05
Do not ship if: Primary metric shows no significant improvement after [N] days
Stop early if: Any guardrail metric degrades significantly (p < 0.05)
Extend if: Effect is directionally positive but not yet significant — extend by [N] days maximum
```

### 2.3 Randomisation and Assignment

```
RANDOMISATION CHECKLIST

[ ] Randomisation is at the correct unit (user, not session, for most product tests)
[ ] Assignment is truly random — not based on any user characteristic that could confound
[ ] Users stay in their assigned variant for the full experiment duration (no switching)
[ ] Control and treatment populations are balanced on key characteristics (run a balance check)
[ ] No other experiment is running on the same population that could interact
[ ] Internal team members are excluded from the experiment population
```

---

## Stage 3: Statistical Foundations

### 3.1 Sample Size Calculation

Running an experiment without calculating the required sample size first is the most common experimentation mistake. An underpowered experiment produces inconclusive results that cannot be acted on.

```
SAMPLE SIZE CALCULATION

Required inputs:
  Baseline metric value: _______________________________________________
  Minimum detectable effect (MDE): ___%
    (The smallest improvement worth shipping — be realistic)
  Statistical significance level (α): 0.05 (95% confidence — standard)
  Statistical power (1-β): 0.80 (80% power — standard)
  Number of variants: ___

Calculation (use a sample size calculator):
  Required users per variant: _______________________________________________
  Total users required: _______________________________________________
  Daily eligible users: _______________________________________________
  Estimated experiment duration: ___ days

Rules of thumb:
  Never run an experiment for less than 7 days (day-of-week effects)
  Never run for more than 6 weeks (novelty effects and user drift)
  If duration exceeds 6 weeks: reduce MDE or increase traffic allocation
```

### 3.2 Statistical Concepts for PMs

| Concept | Plain Language | Practical Implication |
|---|---|---|
| **p-value** | Probability that the result occurred by chance | p < 0.05 means < 5% chance it's a fluke |
| **Confidence interval** | Range where the true effect likely falls | Wide CI = uncertain result; narrow = precise |
| **Statistical power** | Probability of detecting a real effect | Low power = might miss a real improvement |
| **Type I error** | False positive — detecting an effect that isn't there | Caused by low significance threshold |
| **Type II error** | False negative — missing a real effect | Caused by low sample size (underpowered) |
| **MDE** | Minimum effect you have power to detect | Set based on what's business-meaningful, not what's easy |
| **Multiple testing problem** | Running many tests increases false positive rate | Use Bonferroni correction or limit secondary metrics |

### 3.3 Avoiding Common Statistical Mistakes

```
STATISTICAL INTEGRITY CHECKLIST

Before launching:
[ ] Sample size calculated and experiment duration set accordingly
[ ] MDE reflects a business-meaningful improvement (not just statistical convenience)
[ ] Only ONE primary metric designated for the go/no-go decision

During the experiment:
[ ] No peeking at results before the planned end date
[ ] No stopping early because the result "looks good" (inflates false positive rate)
[ ] No adding new metrics after seeing the data (p-hacking)
[ ] No changing the traffic split after launch

After the experiment:
[ ] Report the confidence interval, not just the p-value
[ ] Report the effect size alongside statistical significance
[ ] Report secondary metrics as context, not as the decision basis
[ ] Document the result even if inconclusive — this is a learning
```

---

## Stage 4: Experiment Execution

### 4.1 Pre-Launch Verification

```
PRE-LAUNCH VERIFICATION CHECKLIST

Instrumentation:
[ ] Primary metric event is firing correctly in both variants
[ ] Secondary and guardrail metric events are firing correctly
[ ] Variant assignment is being logged correctly
[ ] No metric events are double-firing

Balance check:
[ ] Run the experiment for 24–48 hours with 0% treatment traffic
[ ] Verify: control and treatment populations are balanced on key user characteristics
[ ] Verify: primary metric baseline is identical across variants before treatment

Sanity checks:
[ ] Treatment variant is confirmed to be correctly deployed
[ ] Control variant is unchanged from baseline
[ ] Internal team members are excluded
[ ] Known bot traffic is excluded
```

### 4.2 Experiment Monitoring During Runtime

```
RUNTIME MONITORING PROTOCOL

Daily checks (automated):
[ ] Sample size accumulation on track (will we reach required sample by planned end date?)
[ ] Guardrail metrics alert — any significant degradation in either variant?
[ ] Data quality — any anomalies in event firing rates?
[ ] Error rates — any elevated error rates in the treatment variant?

Do NOT check:
[ ] The primary metric result (avoid peeking — this inflates Type I error)

Weekly stakeholder update:
"The experiment is running as planned. We are at ___% of required sample size.
Guardrail metrics are [stable / showing a concern — describe].
Expected completion date: ___."
```

### 4.3 Handling Experiment Interference

| Interference Type | Detection | Response |
|---|---|---|
| **Novelty effect** | Early lift that decays over time | Extend experiment; look at later-week data separately |
| **Carryover effect** | Treatment variant affects control users (e.g. shared features) | Use holdout test instead of A/B |
| **Seasonal event** | External event distorts both variants | Note in analysis; consider rerunning outside event window |
| **Simultaneous launch** | Another change launches during experiment | Pause or extend; document potential confound |
| **Sample ratio mismatch** | Traffic split deviates significantly from intended | Pause experiment; investigate and fix assignment bug |

---

## Stage 5: Analysis and Decision

### 5.1 Results Analysis Template

```
EXPERIMENT RESULTS ANALYSIS

Experiment: _______________________________________________  |  Duration: ___ days
Sample: ___ users control  /  ___ users treatment

PRIMARY METRIC
  Control: ___  |  Treatment: ___
  Absolute change: ___  |  Relative change: ___%
  p-value: ___  |  95% CI: [___ to ___]
  Statistically significant: Yes / No

SECONDARY METRICS
  [Metric 1]: Control ___ / Treatment ___ → Positive / Neutral / Negative
  [Metric 2]: Control ___ / Treatment ___ → Positive / Neutral / Negative

GUARDRAIL METRICS
  [Metric 1]: Control ___ / Treatment ___ → Pass / Fail
  [Metric 2]: Control ___ / Treatment ___ → Pass / Fail

SEGMENT ANALYSIS (optional but recommended)
  [Segment A — e.g. new users]: Effect = ___  |  [Segment B — e.g. power users]: Effect = ___
  Notable heterogeneity: Yes / No — _______________________________________________

DECISION (per pre-registered rules)
  [ ] Ship — primary metric improved by > MDE, p < 0.05, all guardrails pass
  [ ] Do not ship — no significant improvement
  [ ] Iterate — result suggests a refinement; retest with [specific change]
  [ ] Inconclusive — underpowered; [extend / rerun with larger sample / accept uncertainty]
```

### 5.2 Learning Documentation

Every experiment produces a learning, regardless of outcome. This is the most underinvested step in experimentation.

```
EXPERIMENT LEARNING RECORD

Experiment: _______________________________________________
Result: Ship / Do not ship / Iterate / Inconclusive

Core learning (required — even for inconclusive results):
"This experiment [confirmed / invalidated / partially validated] the hypothesis that
[restate hypothesis in plain language].
The key learning is: [what we now know that we didn't before].
Confidence in this learning: High / Medium / Low — because [evidence quality]."

Implications for other hypotheses:
Does this result change our belief about any other current or planned experiment?
[ ] Yes — [which hypothesis and how]: _______________________________________________
[ ] No

Implications for the roadmap:
Does this result change the priority of any roadmap items?
[ ] Yes — [which item and what changes]: _______________________________________________
[ ] No

Follow-on experiment (if applicable):
"Because we learned [X], we now believe [Y]. The next experiment to run is:
[brief hypothesis statement]"

Knowledge base entry: [link / ID]
```

---

## Experimentation for AI Products

### 6.1 AI-Specific Experimentation Challenges

| Challenge | Description | Solution |
|---|---|---|
| **Probabilistic outputs** | Same input produces different outputs — control experience is not constant | Use quality scoring as the metric, not output content |
| **Model version changes** | Model provider updates model silently during experiment | Pin model version; monitor for model drift |
| **Prompt vs model effect** | Cannot tell if improvement came from the prompt change or model variation | A/A test first to establish variance baseline |
| **Latency confound** | Treatment may be slower — confounding quality and latency effects | Report latency separately; control for it in analysis |
| **Trust effects** | Users trust AI differently over time — early experiment doesn't capture long-term trust | Run longer experiments for AI trust hypotheses |

### 6.2 AI Experiment Metrics

Standard behavioural metrics are often the wrong primary metric for AI experiments. Use these instead:

| What You're Testing | Better Metric Than | Use Instead |
|---|---|---|
| AI output quality improvement | Clicks on AI output | Output acceptance rate (used without modification) |
| AI latency improvement | Session length | Task completion rate per session |
| AI prompt change | Page views | Quality score (LLM-as-judge on sampled outputs) |
| AI trust feature | Feature usage | AI output acted upon within 24 hours |
| AI onboarding change | Onboarding completion | Week 2 AI usage rate |

### 6.3 A/A Testing for AI Features

Before running A/B tests on AI features, always run an A/A test to establish the natural variance in AI outputs:

```
A/A TEST PROTOCOL FOR AI

Purpose: Establish baseline variance before any treatment is introduced.
This calibrates your MDE — how large a real improvement needs to be to
be detectable above natural AI output variance.

Design:
  Both variants receive identical prompt and model configuration.
  Run for 7 days on the target population.

Analysis:
  Primary metric variance: ___
  Expected natural swing in primary metric: +/- ___%
  Minimum detectable effect for subsequent A/B tests: > ___%
  (Set MDE above the natural variance to avoid false positives)

If A/A test shows p < 0.05: instrumentation error — fix before proceeding
If A/A test shows high variance: AI outputs are too inconsistent for precise measurement
  → Consider aggregating over longer time windows
  → Consider using quality scoring instead of behavioural metrics
```

---

## Building an Experimentation Culture

### 7.1 Experimentation Maturity Levels

| Level | Description | Signal |
|---|---|---|
| **1 — Ad hoc** | Experiments run occasionally without consistent process | No pre-registered decision rules; results rarely documented |
| **2 — Developing** | Some teams experiment consistently; no org-wide standards | Experiments in some squads; results inconsistently shared |
| **3 — Defined** | Org-wide experimentation standards; knowledge shared systematically | Pre-registration required; results in shared knowledge base |
| **4 — Managed** | Experimentation velocity tracked; learning compounds across teams | Experiment velocity metric; cross-team hypothesis sharing |
| **5 — Optimising** | Continuous improvement through experimentation is embedded in culture | Learning from failed experiments drives next hypothesis automatically |

### 7.2 Experimentation Velocity

```
EXPERIMENTATION VELOCITY TARGETS

Experiments completed per PM per month: ___
  Target for growth-stage product: > 2
  Target for scale-stage product: > 4
  Signal if below 1/month: Process bottleneck or hypothesis quality problem

Time from hypothesis to experiment launch: ___ days
  Target: < 5 business days for a simple A/B test
  Signal if > 10 days: Infrastructure or approval bottleneck

Experiment win rate: ___%
  Healthy range: 20–40%
  If > 60%: Hypotheses are too safe — increase ambition
  If < 15%: Hypotheses are poorly grounded — improve research input

Experiments that produce a documented learning: ___%
  Target: 100% — every experiment, win or loss
  Signal if < 70%: Learning culture is weak
```

---

## Templates

### Template A: Experiment Brief (1-page)

```
# Experiment Brief — [Experiment Name]
Date: ___  |  Owner: ___  |  Start: ___  |  End: ___

## Hypothesis
We believe [user] will [behaviour] if [change], because [insight].
Success: [primary metric] improves by > ___% with p < 0.05.

## Design
Control: _______________________________________________
Treatment: _______________________________________________
Split: ___% / ___%  |  Randomisation: User / Session / Account
Eligible population: _______________________________________________

## Metrics
Primary: _______________________________________________
Guardrails: _______________________________________________

## Sample Size
Required per variant: ___  |  Duration: ___ days

## Decision Rules
Ship if: _______________________________________________
Do not ship if: _______________________________________________
Stop early if: _______________________________________________

## Sign-off
[ ] PM  [ ] Engineering  [ ] Data analyst
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Peeking at results before the planned end date | Set the end date before launch; do not check primary metrics until then |
| No pre-registered decision rule | Pre-commit to the ship/no-ship threshold before launching |
| Using secondary metrics for the go/no-go decision | One primary metric only for the decision; secondary metrics are context |
| Stopping early when results look positive | Early stopping inflates false positive rate by 2–3× |
| Running too many simultaneous experiments | Maximum 2–3 simultaneous experiments on the same population |
| Treating inconclusive results as failures | Inconclusive results are a signal to repower or reframe — document the learning |
| No A/A test before AI experiments | Always establish natural variance baseline before testing AI changes |
| Never sharing failed experiment results | Failed experiments are the most valuable learnings — share them widely |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Hypothesis backlog refinement | Weekly | PM |
| Experiment status review | Weekly | PM + Data |
| Results analysis | At experiment end | PM + Data analyst |
| Learning documentation | Within 48 hours of results | PM |
| Experimentation velocity review | Monthly | PM + CPO |
| Experiment knowledge base review | Quarterly | PM leads |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Complete Experiment

> **Best for:** Designing a rigorous A/B test from hypothesis through to decision rules before a single line of code is written.

```
You are an experimentation specialist helping me design a rigorous product experiment.

Guide me through all five stages:

1. Hypothesis — help me write a testable, falsifiable hypothesis in the correct format
2. Experiment design — specify control, treatment, randomisation unit, traffic split, and eligible population
3. Statistics — calculate the required sample size, experiment duration, and MDE
4. Metrics — define the primary metric, secondary metrics, and guardrail metrics
5. Decision rules — pre-register the ship/no-ship/iterate/inconclusive decision rules

After the design:
- Identify the top 3 risks that could invalidate this experiment
- Write the pre-launch verification checklist specific to this experiment
- Write the stakeholder update template for weekly runtime communication
- Estimate the opportunity cost of running this experiment (what else could the team be doing?)

My hypothesis: [describe what you believe will happen and why]
Current baseline for primary metric: [current value]
Daily eligible users: [how many users could be in the experiment?]
Minimum improvement worth shipping: [what % improvement justifies the change?]
Is this an AI feature experiment: [yes/no — if yes, describe the AI component]
```

---

### Prompt 2 — Calculate Sample Size and Duration

> **Best for:** Determining how long an experiment needs to run before results are statistically meaningful.

```
You are a statistician helping me calculate the sample size and duration for my experiment.

Walk me through the calculation with clear explanations at each step:

1. Explain the inputs I need and why each matters
2. Calculate the required sample size per variant
3. Calculate the total experiment duration given my daily traffic
4. Identify whether my MDE is realistic given my traffic volume
5. Show the tradeoff: if I accept a smaller sample size, how does that change the MDE I can detect?

Also:
- Explain what happens if I stop the experiment early (and why it's a problem)
- Explain what Type I and Type II errors mean in the context of my specific experiment
- Recommend whether I should use a one-sided or two-sided test and why
- If my required duration exceeds 6 weeks, suggest options (increase traffic, accept larger MDE, redesign)

My experiment:
Baseline primary metric: [current value — e.g. "D7 retention is 18%"]
Minimum detectable effect: ___% relative improvement [e.g. "5% relative improvement = 18.9%"]
Daily eligible users: [number]
Desired significance level: 95% (p < 0.05)
Desired power: 80%
Number of variants: [2 for standard A/B / 3 for A/B/C]
```

---

### Prompt 3 — Analyse Experiment Results

> **Best for:** After an experiment completes — interpreting the results correctly and making the right decision.

```
You are a data analyst helping me interpret my experiment results and make the correct decision.

Analyse the results I provide across five dimensions:

1. Primary metric analysis
   - Is the result statistically significant? Interpret the p-value and confidence interval
   - Is the effect size business-meaningful? (Statistical significance ≠ practical significance)
   - What does the confidence interval tell me about the range of likely true effects?

2. Secondary metrics
   - Do the secondary metrics support or complicate the primary result?
   - Is there a pattern that suggests a more nuanced story than the primary metric tells?

3. Guardrail metrics
   - Have any guardrail metrics degraded? What does that mean for the decision?

4. Segment analysis
   - Are there significant differences in the effect across user segments?
   - If yes: should we ship to all users or only to certain segments?

5. Decision
   - Apply the pre-registered decision rules
   - Write the decision with full rationale
   - Write the learning that goes into the knowledge base regardless of outcome
   - If the decision is "iterate" — write the specific change that the result suggests

My results:
Control sample: ___ users  |  Treatment sample: ___ users
Primary metric — Control: ___  |  Treatment: ___
p-value: ___  |  95% CI: ___
Secondary metrics: [paste results]
Guardrail metrics: [paste results]
Pre-registered ship threshold: ___
```

---

### Prompt 4 — Design an AI Feature Experiment

> **Best for:** Experiments specifically on AI features — where standard A/B test design needs adaptation for probabilistic outputs.

```
You are an AI experimentation specialist helping me design an experiment on an AI product feature.

Address the AI-specific challenges in the design:

1. Metric selection
   - Why are standard engagement metrics (clicks, sessions) often wrong for AI experiments?
   - What metrics best capture genuine AI value for my feature type?
   - Write the precise definition of my primary metric for this AI experiment

2. A/A baseline test
   - Design the A/A test I should run before the A/B test to establish natural AI output variance
   - What variance level is acceptable? At what variance level should I reconsider the experiment design?

3. Experiment design for AI
   - How do I control for model version changes during the experiment?
   - How do I separate the effect of the prompt change from natural AI variance?
   - Should I pin the model version for this experiment?

4. Duration considerations
   - AI trust effects take longer to manifest than standard UX effects
   - How long should this experiment run to capture trust and habituation effects?

5. Analysis approach
   - How do I handle the fact that AI outputs in the treatment vary from user to user?
   - Should I use LLM-as-judge quality scoring as a supplement to behavioural metrics?

My AI feature experiment:
What I am changing: [describe the prompt change, model change, or AI feature change]
Target user behaviour I want to improve: [describe]
Current baseline: [primary metric current value]
Daily eligible users: [number]
```

---

### Prompt 5 — Extract and Share Experiment Learnings

> **Best for:** After any experiment — ensuring the learnings are documented, shared, and translated into future hypotheses.

```
You are a product learning strategist helping me extract and share the maximum learning from a completed experiment.

For the experiment results I share, produce:

1. Learning statement
   Write the core learning in the standard format:
   "This experiment [confirmed / invalidated / partially validated] the hypothesis that [restate].
   The key learning is [specific new knowledge].
   This was [expected / surprising] because [explain].
   Confidence: High / Medium / Low — because [evidence quality rationale]."

2. Implication mapping
   - Does this result change our belief about any other current hypothesis?
   - Does it change the priority of any roadmap item?
   - Does it challenge any assumption we are currently treating as fact?

3. Follow-on hypothesis
   Write the next experiment hypothesis that this result generates:
   "Because we learned [X], we now believe [Y].
   The next experiment should test whether [specific hypothesis]."

4. Knowledge base entry
   Write the structured knowledge base entry for this experiment:
   - Category tags (user segment / feature area / metric affected)
   - Summary (2 sentences)
   - Decision made
   - Key learning
   - Follow-on hypothesis

5. Team communication
   Write the internal Slack/email update sharing this result with the broader team:
   - Lead with the decision (ship / not ship)
   - Explain the result in plain language
   - Share the key learning
   - Invite others to connect this to their own work

My experiment: [describe the hypothesis and what was tested]
Results: [share the outcome — did it work? by how much? what surprised you?]
Team context: [who should hear about this and why it might matter to them]
```
