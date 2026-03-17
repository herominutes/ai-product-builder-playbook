# 📡 AI Monitoring — AI Product Builder Playbook

> **A framework for monitoring the health, quality, and safety of AI systems in production**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The AI Monitoring Model](#the-ai-monitoring-model)
- [Layer 1: Infrastructure Monitoring](#layer-1-infrastructure-monitoring)
- [Layer 2: Model Performance Monitoring](#layer-2-model-performance-monitoring)
- [Layer 3: Output Quality Monitoring](#layer-3-output-quality-monitoring)
- [Layer 4: User Experience Monitoring](#layer-4-user-experience-monitoring)
- [Layer 5: Safety and Compliance Monitoring](#layer-5-safety-and-compliance-monitoring)
- [Alerting Architecture](#alerting-architecture)
- [Incident Response](#incident-response)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Deploying an AI system without monitoring is not a product launch — it is a liability. AI systems fail in ways that traditional software does not: they degrade gradually rather than breaking suddenly, their failures are probabilistic rather than deterministic, and a single bad output reaching the wrong user can cause irreversible trust damage.

> **Core Principle:** You cannot improve what you do not measure. AI monitoring is not an engineering concern delegated to the infrastructure team — it is a product responsibility. The PM who owns the AI feature owns the monitoring that keeps it trustworthy.

AI monitoring differs from traditional software monitoring in three fundamental ways. First, correctness is probabilistic — a model can produce wrong outputs without throwing an error. Second, quality can drift over time without any system change — as user inputs evolve, model performance on real-world queries can degrade. Third, safety failures are often invisible until a user reports them — passive monitoring must catch what active testing misses.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Launching any AI feature to production | 🔴 Critical — monitoring is a launch requirement |
| AI feature generating unexpected user complaints | 🔴 Critical — investigate immediately |
| Model provider has changed or upgraded the underlying model | 🔴 Critical — quality can change silently |
| AI costs are higher than expected | 🟠 High — cost monitoring identifies the driver |
| Latency has increased without an obvious cause | 🟠 High |
| Designing the monitoring system before building the AI feature | 🟠 High — build monitoring alongside the feature |
| Quarterly AI product review | 🟡 Medium |

---

## The AI Monitoring Model

AI monitoring operates across five layers, from infrastructure to safety. Each layer catches failures the layers below it miss.

```
INFRASTRUCTURE MONITORING
  ↓ is the system available and performing?
MODEL PERFORMANCE MONITORING
  ↓ is the model behaving as expected?
OUTPUT QUALITY MONITORING
  ↓ are outputs accurate, grounded, and useful?
USER EXPERIENCE MONITORING
  ↓ are users getting value from the AI?
SAFETY AND COMPLIANCE MONITORING
  ↓ is the AI behaving safely and within policy?
```

| Layer | What It Catches | Key Metrics | Typical Alert Threshold |
|---|---|---|---|
| **Infrastructure** | Downtime, latency, errors | Availability, P99 latency, error rate | Availability < 99.5%, P99 > 5s |
| **Model performance** | Model drift, degradation, cost overrun | Quality score, cost per call, token usage | Quality < baseline by 10% |
| **Output quality** | Hallucination, irrelevance, format failures | Faithfulness, relevance, grounding | Faithfulness < 95% |
| **User experience** | Low adoption, dissatisfaction, churn signals | Usage rate, thumbs down %, session length | Negative feedback > 3% |
| **Safety** | Policy violations, harmful outputs, abuse | Filter trigger rate, violation incidents | Any confirmed violation |

---

## Layer 1: Infrastructure Monitoring

### 1.1 Core Infrastructure Metrics

| Metric | Definition | Measurement Method | Alert Threshold |
|---|---|---|---|
| **Availability** | % of time the AI endpoint is responsive | Synthetic probing every 60s | < 99.5% in 1-hour window |
| **Latency P50** | Median response time | Percentile on response time distribution | > 2s sustained |
| **Latency P95** | 95th percentile response time | Percentile on response time distribution | > 5s sustained |
| **Latency P99** | 99th percentile response time | Percentile on response time distribution | > 10s |
| **Error rate** | % of requests returning an error | Count of 4xx/5xx ÷ total requests | > 1% in 5-minute window |
| **Timeout rate** | % of requests exceeding timeout | Count of timeouts ÷ total requests | > 0.5% |
| **Throughput** | Requests per minute | Request counter | < 50% of baseline (drop) or > 150% (spike) |

### 1.2 Cost Monitoring

AI infrastructure cost is variable and can spike without warning. Monitor continuously:

```
COST MONITORING DASHBOARD

Daily metrics:
- Total token consumption (input + output)
- Total API cost ($)
- Cost per user session
- Cost per successful completion
- Cost breakdown by feature / endpoint

Weekly metrics:
- Cost trend vs prior week (+/-%)
- Cost per user (MAU basis)
- Most expensive queries (top 10 by token count)
- Cost efficiency: value delivered per dollar spent

Alert conditions:
- Daily cost exceeds 150% of 7-day average → Investigate
- Cost per session exceeds $[threshold] → Review token usage
- A single user generating > 10% of daily cost → Potential abuse
```

### 1.3 Provider Health Monitoring

When using third-party model providers, monitor their status independently:

```
PROVIDER MONITORING CHECKLIST

[ ] Subscribe to provider status page (OpenAI, Anthropic, etc.)
[ ] Implement provider health check probe (ping the API every 60s)
[ ] Configure automatic fallback to secondary provider on failure
[ ] Monitor provider latency independently from application latency
[ ] Track provider-introduced changes (model updates, deprecations)
[ ] Set calendar reminders for model deprecation dates
```

---

## Layer 2: Model Performance Monitoring

### 2.1 Model Drift Detection

Model drift occurs when the model's real-world performance degrades over time — not because the model changed, but because the distribution of user inputs shifted away from the model's strengths.

| Drift Type | Description | Detection Method |
|---|---|---|
| **Input drift** | User queries are becoming structurally different | Compare query embedding distribution over time |
| **Output drift** | Output characteristics are changing (length, format, confidence) | Monitor output statistics continuously |
| **Quality drift** | Real-world quality scores are declining | Periodic evaluation against quality dataset |
| **Domain drift** | Users are asking about topics outside the model's strengths | Topic classification + quality correlation |

### 2.2 Quality Baseline Establishment

Before monitoring can detect drift, you need a baseline:

```
QUALITY BASELINE PROTOCOL

Step 1 — Create evaluation dataset
100 representative queries with ground truth answers (human-labelled).
Include: common queries (60%), edge cases (20%), adversarial cases (20%).

Step 2 — Establish baseline metrics
Run evaluation dataset against current model.
Record: accuracy, faithfulness, relevance, format compliance, latency.
This is your baseline.

Step 3 — Set drift thresholds
Alert when any metric drops > 10% below baseline.
Investigate when any metric drops > 5% below baseline.

Step 4 — Schedule recurring evaluation
Run evaluation dataset against production model weekly.
Compare to baseline.
Track trend — gradual decline is as concerning as sudden drop.
```

### 2.3 Token Usage Monitoring

| Metric | What It Signals | Alert Condition |
|---|---|---|
| **Average input tokens** | Prompt size and context efficiency | Increasing trend → prompts growing unnecessarily |
| **Average output tokens** | Response verbosity | Increasing trend → outputs becoming less efficient |
| **Token variance** | Inconsistency in usage | High variance → outputs are unpredictable in size |
| **Max tokens triggered** | Truncation events | > 1% of requests → max_tokens limit is too low |
| **Input/output ratio** | Context vs generation balance | Ratio change → retrieval or prompt engineering issue |

---

## Layer 3: Output Quality Monitoring

### 3.1 Automated Quality Evaluation

Use an LLM as a judge to continuously evaluate a sample of production outputs:

```
OUTPUT QUALITY EVALUATION PIPELINE

Sampling rate:
< 1,000 daily outputs: Evaluate 20%
1,000–10,000: Evaluate 10%
10,000–100,000: Evaluate 5%
> 100,000: Evaluate 1% + all flagged outputs

LLM-as-judge prompt:
"Evaluate the following AI response on three dimensions.
Score each from 1–5 with 5 being best.

Question: [original user query]
AI Response: [generated output]
Retrieved Context (if RAG): [context provided to model]

Dimension 1 — Relevance: Does the response directly address the question?
  1 = Completely off-topic  5 = Precisely answers the question

Dimension 2 — Faithfulness: Are all claims in the response supported by the context?
  1 = Many unsupported claims  5 = Every claim is traceable to context
  (Score this 5 if no context was used and the response is factually accurate)

Dimension 3 — Completeness: Does the response fully address the question?
  1 = Major gaps  5 = Comprehensive and thorough

Return ONLY a JSON object: {relevance: N, faithfulness: N, completeness: N, flags: []}"
```

### 3.2 Quality Metrics Dashboard

```
QUALITY MONITORING DASHBOARD — DAILY VIEW

Overall quality score (avg across sampled outputs): ___/5
  Relevance: ___/5  |  Faithfulness: ___/5  |  Completeness: ___/5

vs. yesterday: +/-___
vs. 7-day average: +/-___
vs. baseline: +/-___

Output distribution:
  Excellent (4.5–5.0): ___%
  Good (3.5–4.4): ___%
  Acceptable (2.5–3.4): ___%
  Poor (< 2.5): ___%  ← Alert if > 5%

Top failure categories (from sampled poor outputs):
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

Hallucination flags: ___  |  Format failures: ___  |  Scope violations: ___
```

### 3.3 Hallucination Monitoring

```
HALLUCINATION DETECTION PIPELINE

Method 1 — Faithfulness check (for RAG systems):
For each output, check: "Is every factual claim in this output supported by
the retrieved context?" Use LLM judge scoring 1–5.
Alert when faithfulness score < 4.0 on more than 5% of sampled outputs.

Method 2 — Factual consistency check (for factual domains):
Maintain a ground truth fact database for your domain.
Periodically check: does the model's output contradict known facts?
Tool: FactScore, RAGAS, or custom LLM judge.

Method 3 — User-reported corrections:
Provide a "this is incorrect" button in the UI.
Track correction rate by output type and query category.
Alert when correction rate exceeds 2% on any category.
```

---

## Layer 4: User Experience Monitoring

### 4.1 User Behaviour Signals

| Signal | What It Indicates | Measurement |
|---|---|---|
| **Feature usage rate** | Are users engaging with the AI feature? | % of eligible users who trigger AI per week |
| **Session abandonment after AI output** | Did the AI cause the user to leave? | Session end rate within 30s of AI response |
| **Explicit negative feedback** | User directly signals dissatisfaction | Thumbs down, "report issue", correction count |
| **Explicit positive feedback** | User directly signals satisfaction | Thumbs up, copy rate, share rate |
| **Re-query rate** | Did the user have to ask again because the first answer failed? | Queries within 60s of prior AI response |
| **Output copy rate** | Did the user find the output useful enough to copy? | Clipboard copy events on AI output |
| **Feature bypass rate** | Is the user skipping the AI feature? | Users who navigate around the AI workflow |

### 4.2 Cohort Analysis

Monitor quality separately across user segments — a model that works well on average may be failing specific groups:

```
COHORT QUALITY BREAKDOWN

Segment by:
- New users (< 7 days) vs established users (> 30 days)
- Power users (> 10 AI interactions/week) vs casual users (< 3)
- Query complexity (short/simple vs long/complex)
- Domain (if multi-domain product)
- Device/platform

For each cohort, track:
- Quality score vs overall average
- Negative feedback rate vs overall average
- Session abandonment rate vs overall average

Alert when: any cohort's quality score is > 15% below the overall average
Action: investigate whether the model has a specific weakness with this cohort's query patterns
```

### 4.3 Trust Indicators

For AI products specifically, trust is the metric that underlies all others:

```
AI TRUST MONITORING FRAMEWORK

Proxy metrics for trust:
- Acceptance rate: % of AI outputs the user acts on without modification
- Verification rate: % of outputs the user checks against another source
- Override rate: % of AI decisions the user overrides
- Return rate: % of users who come back to use AI feature after first use

Trust trend signal:
If acceptance rate is declining + verification rate is increasing:
→ Users are losing trust in AI outputs — investigate quality issues

If override rate is increasing:
→ AI is making decisions users disagree with — review model behaviour

If return rate is declining:
→ First-session experience is failing — audit onboarding and first output quality
```

---

## Layer 5: Safety and Compliance Monitoring

### 5.1 Safety Metrics

| Metric | Definition | Alert Threshold |
|---|---|---|
| **Content filter trigger rate** | % of outputs flagged by safety filters | > 5% → filter may be over-triggering; < 0.1% → filter may be under-triggering |
| **Policy violation rate** | % of outputs confirmed to violate policy | Any confirmed violation → immediate review |
| **Abuse attempt rate** | % of inputs showing signs of adversarial use | > 1% → investigate and tighten input guardrails |
| **PII exposure rate** | Instances of PII detected in AI outputs | Any instance → immediate review and potential incident |
| **Refusal rate** | % of requests the AI declines to complete | > 10% → guardrails too restrictive; < 0.5% → may be too permissive |

### 5.2 Compliance Monitoring Checklist

```
COMPLIANCE MONITORING CHECKLIST — QUARTERLY

Data handling:
[ ] User data sent to third-party model providers is within policy
[ ] Data retention for AI inputs and outputs complies with privacy policy
[ ] PII is being stripped from inputs before reaching the model
[ ] User memory data retention limits are being enforced

Regulatory:
[ ] AI disclosures are visible and accurate for all AI-generated content
[ ] Right to erasure requests are being honoured in AI memory stores
[ ] If in regulated industry: AI output disclaimer is present and accurate
[ ] GDPR / CCPA compliance review completed

Safety:
[ ] Red team exercise completed in last 90 days
[ ] All P1/P2 safety incidents from last quarter have post-mortems
[ ] Guardrail calibration reviewed (not too tight, not too loose)
[ ] New model capabilities reviewed for new safety risks
```

### 5.3 Audit Trail Requirements

```
AI AUDIT TRAIL SCHEMA

For every AI interaction, log:
{
  interaction_id: "uuid",
  timestamp: "ISO-8601",
  user_id: "uuid" (or anonymised ID),
  session_id: "uuid",
  feature_id: "which AI feature",
  input_hash: "SHA-256 of input" (not the raw input — privacy),
  input_tokens: N,
  output_tokens: N,
  model_used: "model identifier",
  model_version: "version",
  latency_ms: N,
  cost_usd: N,
  safety_flags: [],
  quality_score: N (if sampled),
  user_feedback: "positive | negative | none"
}

Retention: 90 days minimum for operational review; 12 months for compliance
Access: Engineering (full), PM (aggregated), Legal (on request), User (own data)
```

---

## Alerting Architecture

### 6.1 Alert Severity Levels

| Severity | Definition | Response Time | Who Is Notified |
|---|---|---|---|
| **P1 — Critical** | Safety violation, data breach, complete outage | Immediate (< 15 min) | On-call eng + PM + Leadership |
| **P2 — High** | Quality degradation > 20%, error rate > 5% | < 1 hour | On-call eng + PM |
| **P3 — Medium** | Quality declining trend, cost spike > 150% | < 4 hours | PM + Eng lead |
| **P4 — Low** | Minor quality dip, informational trends | Next business day | PM |

### 6.2 Alert Routing

```
ALERT ROUTING MATRIX

Infrastructure alerts → Engineering on-call (PagerDuty / OpsGenie)
Cost alerts → PM + Engineering lead (Slack)
Quality alerts → PM + AI team (Slack)
Safety alerts → PM + Legal + Engineering on-call (PagerDuty + email)
User experience alerts → PM (Slack, daily digest)
```

---

## Incident Response

### 7.1 AI Incident Response Playbook

```
AI INCIDENT RESPONSE — FIRST 30 MINUTES

Minute 0–5: Detection and assessment
[ ] Confirm the incident is real (not a monitoring false positive)
[ ] Classify severity: P1 / P2 / P3
[ ] Notify appropriate team members

Minute 5–15: Immediate containment
[ ] If safety violation: consider rate limiting or disabling feature immediately
[ ] If quality degradation: increase output sampling to 100%
[ ] If cost spike: check for abuse or runaway pipeline; apply rate limit

Minute 15–30: Investigation
[ ] Identify which monitoring metric first showed the problem
[ ] Identify the timeline: when did it start?
[ ] Identify the scope: how many users affected?
[ ] Identify the cause: model change / input distribution shift / infrastructure issue / abuse

Minute 30+: Resolution and communication
[ ] Implement fix or workaround
[ ] If users were affected: draft communication (internal first, then user-facing if needed)
[ ] Schedule post-mortem for P1/P2 incidents
```

### 7.2 Post-Mortem Template

```
# AI Incident Post-Mortem — [Incident Name]
Date: ___  |  Severity: ___  |  Duration: ___

## Summary
[2–3 sentences: what happened, who was affected, how it was resolved]

## Timeline
[Minute-by-minute timeline from first signal to resolution]

## Root Cause
[Single root cause — not a list of contributing factors]

## Impact
Users affected: ___  |  Outputs affected: ___  |  Cost impact: $___

## What Went Well
[What detection, response, or mitigation worked]

## What Went Wrong
[What failed — in monitoring, response, or the system itself]

## Action Items
| Action | Owner | Due Date |
|--------|-------|----------|
|        |       |          |

## Monitoring Gap (if applicable)
[If this incident was not detected by monitoring: what new alert should be added?]
```

---

## Templates

### Template A: AI Monitoring Dashboard Specification

```
# AI Monitoring Dashboard — [Feature Name]
Date: ___  |  Owner: ___

## Real-Time Widgets (refresh every 60s)
- Availability (%)
- Current P99 latency (ms)
- Error rate (%)
- Active requests per minute

## Hourly Widgets
- Cost per hour ($)
- Token usage (input + output)
- Content filter trigger rate (%)
- Quality score (sampled outputs)

## Daily Widgets
- Quality score trend (7-day)
- User feedback sentiment (positive / negative %)
- Feature usage rate (% of eligible users)
- Top failure categories
- Cost per user session

## Weekly Widgets
- Quality baseline comparison
- Cohort quality breakdown
- Safety compliance checklist status
- Cost trend vs budget

## Alert Summary
Active alerts: ___
P1: ___  P2: ___  P3: ___  P4: ___
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Only monitoring infrastructure (uptime, latency) | Monitor all five layers — infrastructure alone misses quality and safety failures |
| No quality baseline before launch | Establish baseline on evaluation dataset before go-live |
| Sampling 0% of outputs | Sample at minimum 1% — automated systems miss nuanced failures |
| No user feedback mechanism | Give users a simple way to signal bad outputs — it is your best quality signal |
| Alerting on every small deviation | Set meaningful thresholds — alert fatigue leads to ignored alerts |
| No post-mortem process | Every P1/P2 incident must have a post-mortem — the learning is the value |
| Monitoring as an engineering-only responsibility | PM owns the quality and UX monitoring layers — delegate infrastructure only |
| Cost monitoring after the bill arrives | Real-time cost monitoring prevents surprises; monthly reviews are too late |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Dashboard review | Daily | PM |
| Alert threshold calibration | Monthly | PM + Engineering |
| Quality evaluation dataset run | Weekly | AI team |
| Cohort quality breakdown | Monthly | PM |
| Safety compliance checklist | Quarterly | PM + Legal |
| Red team exercise | Quarterly | Engineering + PM |
| Full monitoring architecture review | Annually | PM + Engineering |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Complete AI Monitoring System

> **Best for:** Building the monitoring architecture for an AI feature before or immediately after launch.

```
You are an AI operations specialist helping me design a complete monitoring system for my AI product feature.

Design the monitoring system across all five layers:

1. Infrastructure monitoring — availability, latency (P50/P95/P99), error rate, cost
2. Model performance monitoring — quality baseline, drift detection, token usage
3. Output quality monitoring — sampling rate, LLM-as-judge evaluation, hallucination detection
4. User experience monitoring — usage rate, feedback signals, trust indicators
5. Safety monitoring — content filter rates, policy violations, audit trail

For each layer:
- List every metric I should track with its measurement method
- Define the alert threshold for each metric
- Specify the alert severity (P1/P2/P3/P4) and who is notified

After all five layers:
- Design the alerting routing matrix (who gets what alert, via what channel)
- Write the first 30-minute incident response playbook
- Identify the top 3 monitoring gaps most AI teams miss

My AI feature: [describe what it does]
User volume: [daily active users]
Risk level: [Low / Medium / High / Critical]
Team structure: [who is on-call? PM and eng split?]
Current monitoring tooling: [Datadog / Grafana / CloudWatch / other / none]
```

---

### Prompt 2 — Build an LLM-as-Judge Quality Evaluation Pipeline

> **Best for:** Setting up automated, continuous output quality evaluation using an LLM to score production outputs.

```
You are an AI quality engineer helping me build an automated output quality evaluation pipeline.

Design the complete pipeline:

1. Sampling strategy — what % of outputs to evaluate at my volume; how to stratify the sample
2. Evaluation prompt — write the complete LLM-as-judge prompt for my use case, scoring:
   - Relevance (does the response address the question?)
   - Faithfulness (are claims supported by context? — if RAG)
   - Completeness (does it fully answer the question?)
   - Safety (does it comply with content policy?)
3. Scoring rubric — explicit criteria for each score level (1–5) for each dimension
4. Aggregation — how to aggregate scores across sampled outputs into dashboard metrics
5. Alert logic — at what aggregate score or distribution shift should I alert?
6. Feedback loop — how do evaluation findings get converted into prompt or model improvements?

After the pipeline design:
- Estimate the cost of running this evaluation at my output volume
- Write 5 test cases I can use to validate the evaluator itself
- Identify where LLM-as-judge is unreliable and recommend human review instead

My AI feature: [describe]
Output volume: [daily outputs]
Use case domain: [what topics does the AI handle?]
Whether I use RAG: [yes/no]
Budget for evaluation: $[monthly]
```

---

### Prompt 3 — Design User Trust Monitoring

> **Best for:** Going beyond standard UX metrics to track whether users actually trust and rely on AI outputs.

```
You are a product analyst helping me design a trust monitoring framework for my AI product.

Trust is the underlying metric that predicts retention for AI products. Help me measure it indirectly through proxy metrics.

Design the trust monitoring framework:

1. Trust proxy metrics — identify 6–8 behavioural signals that indicate trust level
   For each: what is it measuring, how is it measured, what does a change in this metric mean?

2. Trust cohort segmentation — how should I segment users by trust level?
   Design the cohort definitions: Skeptical / Cautious / Collaborative / Delegating

3. Trust trend monitoring — how do I detect when trust is declining before churn happens?
   Write the leading indicators of trust decline (what changes 2–4 weeks before a user churns?)

4. Trust recovery playbook — when trust drops, what interventions improve it?
   Design 3 interventions with measurable success criteria

5. Trust dashboard — design the weekly trust monitoring dashboard
   What 5 metrics go on the main view?

After the framework:
- Write the alert condition for "trust is declining" that I should add to my monitoring system
- Identify the single most important trust metric to optimise for my AI product

My AI product: [describe]
Current user behaviour signals available: [what events do I currently track?]
Known trust issues: [any existing complaints or patterns?]
User segment: [who uses this product?]
```

---

### Prompt 4 — Conduct a Model Drift Investigation

> **Best for:** When quality metrics have declined and you need to diagnose whether model drift, input drift, or a system change is responsible.

```
You are an AI systems diagnostician helping me investigate a model performance decline.

I will share my monitoring data. Guide me through a structured drift investigation:

Step 1 — Timeline analysis
When did the decline start? What system changes happened around that time?
Changes to investigate: model version, prompt changes, data pipeline changes, user composition changes.

Step 2 — Input drift analysis
Has the distribution of user queries changed?
How to measure: compare query embedding distributions (current 30 days vs prior 30 days).
What to look for: new topics, different query lengths, different user segments.

Step 3 — Output drift analysis
Has the statistical profile of outputs changed?
Metrics: average output length, format compliance rate, confidence score distribution.

Step 4 — Segment isolation
Is the decline uniform or concentrated in a specific cohort?
Check: by query type, by user segment, by feature, by time of day.

Step 5 — Root cause hypothesis
Based on the above: what is the most likely root cause?
Options: Model degradation / Input distribution shift / Prompt regression / Infrastructure change / User composition change

Step 6 — Fix and validate
Write the specific fix for the identified root cause.
Write the test to confirm the fix worked.

My monitoring data:
[paste quality metrics, timeline, any system change log]

My AI feature: [describe]
When decline started: [date or approximate]
Changes made around that time: [list any system, model, or prompt changes]
```

---

### Prompt 5 — Write an AI Incident Post-Mortem

> **Best for:** After any P1 or P2 AI incident — documenting what happened and preventing recurrence.

```
You are an engineering manager helping me write a thorough AI incident post-mortem.

Using the information I provide, write a complete post-mortem document that includes:

1. Executive summary — 3 sentences: what happened, who was affected, how it was resolved
2. Timeline — minute-by-minute from first signal to resolution
3. Root cause — single root cause (not a list), written with full technical specificity
4. Impact assessment — users affected, outputs affected, trust impact, cost impact
5. What went well — specific things that worked in detection, response, or mitigation
6. What went wrong — specific gaps in monitoring, response, or the system
7. Action items — specific, owned, time-bound improvements
8. Monitoring gap — if this incident was not detected by monitoring, what new alert should be added?

Rules:
- Root cause must be singular and specific — "our monitoring was insufficient" is not a root cause
- Action items must be specific enough that completion can be verified
- The post-mortem is blameless — systems fail, not people

My incident data:
What happened: [describe]
Timeline: [describe what you know]
Impact: [users, outputs, duration]
What we know about the cause: [describe]
What we did to resolve it: [describe]
```
