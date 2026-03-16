# 🎯 Product Opportunity Assessment — AI Product Builder Playbook

> **A structured framework for identifying, evaluating, and prioritising product opportunities before investing significant resources in development**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Opportunity Assessment Model](#the-opportunity-assessment-model)
- [Dimension 1: User Problem](#dimension-1-user-problem)
- [Dimension 2: Market Opportunity](#dimension-2-market-opportunity)
- [Dimension 3: Strategic Fit](#dimension-3-strategic-fit)
- [Dimension 4: Technical Feasibility](#dimension-4-technical-feasibility)
- [Dimension 5: Business Impact](#dimension-5-business-impact)
- [Opportunity Scoring Model](#opportunity-scoring-model)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Product teams move too quickly from ideas to execution. The cost is not wasted sprints — it is wasted months building something users do not want, in a market too small to matter, for a problem the team assumed but never validated.

> **Core Principle:** An opportunity is not a feature request, a competitor announcement, or an executive idea. It is a validated intersection of user pain, market potential, strategic fit, and buildable solution. All four must be present.

The Product Opportunity Assessment framework forces rigour before commitment. It does not slow teams down — it prevents the far greater slowdown of building the wrong thing.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| New product idea surfaced by exec, customer, or competitor | 🔴 Critical — assess before any design or eng work |
| Considering entry into a new market or user segment | 🔴 Critical — validate before committing resources |
| Quarterly planning — backlog of potential initiatives | 🟠 High — score all before roadmap is set |
| Partnership or acquisition opportunity with product implications | 🟠 High |
| AI capability has emerged that might change the product | 🟠 High |
| Existing feature underperforming — pivot or abandon decision | 🟡 Medium |
| Post-launch retrospective on a failed initiative | 🟡 Medium — identify which dimension was missed |

---

## The Opportunity Assessment Model

Every product opportunity must be evaluated across five dimensions in sequence. Skipping any dimension invalidates the assessment.

```
USER PROBLEM
  ↓ is there real, validated pain worth solving?
MARKET OPPORTUNITY
  ↓ is the addressable market large enough to matter?
STRATEGIC FIT
  ↓ does this strengthen our position?
TECHNICAL FEASIBILITY
  ↓ can we build it reliably, and at what cost?
BUSINESS IMPACT
  ↓ does this create durable value for the company?
```

| Dimension | Core Question | Kill Signal |
|---|---|---|
| **User Problem** | Is this pain real, frequent, and severe? | Users have lived with it for years without urgently seeking a fix |
| **Market Opportunity** | Is the market large enough and growing? | TAM is under $100M or declining |
| **Strategic Fit** | Does this extend our position or fragment it? | Requires building outside our core competency with no leverage |
| **Technical Feasibility** | Can we ship something reliable within 2 quarters? | Core dependency on unproven technology or unavailable data |
| **Business Impact** | Will this move a metric that matters? | Impact is marginal or cannibalises existing revenue |

> **Rule of thumb:** A strong opportunity clears all five dimensions. A weak score in any single dimension is grounds for pausing — not necessarily killing — the opportunity until that dimension can be validated.

---

## Dimension 1: User Problem

### 1.1 Problem Validation Standard

The user problem is the foundation. Every other dimension is irrelevant if the problem is not real, frequent, and painful enough to change behaviour.

| Validation Level | Description | Minimum Bar |
|---|---|---|
| **Assumed** | Team believes the problem exists | Not acceptable — must validate before proceeding |
| **Anecdotal** | A few users mentioned it | Proceed to structured research only |
| **Validated** | Evidence from interviews, data, and behaviour | Required to score this dimension |
| **Quantified** | Frequency, severity, and cost of the problem measured | Required for high-confidence opportunities |

### 1.2 Problem Diagnosis Checklist

```
USER PROBLEM DIAGNOSTIC

[ ] Who specifically is the user? (Not "anyone who..." — a named persona)
[ ] What are they trying to accomplish? (Job to be done)
[ ] What is blocking them from accomplishing it today?
[ ] How often does this problem occur? (Daily / Weekly / Monthly / Rarely)
[ ] How painful is it? (Churns users / Major frustration / Mild annoyance)
[ ] What is their current workaround? (There is always one)
[ ] What does the workaround cost them? (Time / money / quality / opportunity)
[ ] How many users experience this problem? (Segment size)
[ ] What evidence do we have? (Interviews / support tickets / NPS drivers / session data)
```

### 1.3 Problem Severity Matrix

Map your problem before scoring:

```
                    HIGH FREQUENCY
                          |
        High Pain + High Frequency  |  Low Pain + High Frequency
             [PRIORITISE]           |    [Automate or streamline]
                          |
HIGH PAIN ----------------+---------------- LOW PAIN
                          |
        High Pain + Low Frequency   |  Low Pain + Low Frequency
          [Validate segment size]   |        [DO NOT PURSUE]
                          |
                    LOW FREQUENCY
```

> **Action:** Only opportunities in the top-left quadrant should proceed to market assessment. Bottom-right is a definitive kill signal.

### 1.4 Research Methods by Confidence Need

| Method | Best For | Time Investment |
|---|---|---|
| Customer interviews (8–12) | Discovering unknown pain and workarounds | 2–3 weeks |
| Support ticket analysis | Quantifying known pain at scale | 3–5 days |
| Session recordings (20+ sessions) | Observing behaviour without bias | 1 week |
| Jobs-to-be-done analysis | Mapping motivation behind behaviour | 2–4 weeks |
| NPS driver analysis | Identifying pain tied to churn | 3–5 days |
| Problem survey (n ≥ 100) | Quantifying frequency and severity | 1–2 weeks |

---

## Dimension 2: Market Opportunity

### 2.1 Market Sizing Framework

```
MARKET SIZING — THREE LAYERS

TAM (Total Addressable Market)
The total global demand for this solution if every potential customer used it.
→ Use for investor conversations and long-term vision sizing.

SAM (Serviceable Addressable Market)
The portion of TAM your product can realistically reach given geography,
segment focus, and go-to-market model.
→ Use for strategic planning and resource allocation.

SOM (Serviceable Obtainable Market)
The share of SAM you can realistically capture in 12–24 months.
→ Use for revenue forecasting and initiative prioritisation.
```

### 2.2 Market Attractiveness Scorecard

| Signal | Strong | Weak |
|---|---|---|
| Market size (SAM) | > $500M | < $100M |
| Growth rate | > 15% YoY | Flat or declining |
| Competitive density | Few strong incumbents | Crowded with well-funded players |
| Incumbent weakness | Clear gap or failure mode | Incumbents well-entrenched |
| Switching cost for users | Low — users can move | High — users are locked in |
| Regulatory environment | Favourable or neutral | Restrictive or uncertain |

### 2.3 Competitive Landscape Template

```
## Competitive Landscape: [Opportunity Name]

| Competitor | Strength | Weakness | Our Differentiator |
|------------|----------|----------|--------------------|
|            |          |          |                    |
|            |          |          |                    |
|            |          |          |                    |

Key gap in the market:
_______________________________________________

Why incumbents are not filling this gap:
_______________________________________________

Our window of opportunity (how long before someone fills it):
_______________________________________________
```

---

## Dimension 3: Strategic Fit

### 3.1 Strategic Fit Dimensions

An opportunity with strong user pain and a large market can still be the wrong bet if it fragments your product, dilutes your team, or requires capabilities you do not have and cannot acquire quickly.

| Fit Dimension | Question | Strong Signal | Weak Signal |
|---|---|---|---|
| **Vision alignment** | Does this serve our declared user and transformation? | Core to vision | Tangential or contradicts |
| **Capability leverage** | Does this use our existing strengths? | Amplifies what we do well | Requires building from scratch |
| **Portfolio coherence** | Does this extend the product naturally? | Logical adjacency | Requires separate product motion |
| **Competitive positioning** | Does this widen our moat? | Creates durable advantage | Matches what competitors already have |
| **Ecosystem fit** | Does this strengthen platform or partner relationships? | Enables ecosystem growth | Isolated feature with no leverage |

### 3.2 Strategic Fit Test

```
STRATEGIC FIT TEST

Run this before scoring:

1. Can we draw a direct line from this opportunity to our declared vision?
   Yes / No / Partially

2. Does this play to our existing strengths — or require building something new?
   Existing strength / Adjacent / Entirely new

3. If we build this, does it make our other products stronger or weaker?
   Stronger / Neutral / Weaker (cannibalisation risk)

4. Would this opportunity make sense for a competitor to build?
   If yes — why are we better positioned than them?
   _______________________________________________

5. What do we explicitly give up by pursuing this?
   _______________________________________________
```

---

## Dimension 4: Technical Feasibility

### 4.1 Standard Feasibility Assessment

```
TECHNICAL FEASIBILITY CHECKLIST

[ ] Can we build an MVP within one quarter using existing capabilities?
[ ] What are the top 3 technical risks? (Rate each: Low / Medium / High)
[ ] What external dependencies exist? (APIs, data sources, third-party services)
[ ] What is the estimated engineering effort? (S / M / L / XL)
[ ] What does the failure mode look like — and how do we recover?
```

### 4.2 AI-Specific Feasibility (for AI product opportunities)

AI products carry additional feasibility dimensions that standard assessments miss:

| AI Feasibility Dimension | Question | Red Flag |
|---|---|---|
| **Model reliability** | Does a reliable model exist for this task? | Best available model accuracy < 80% on our use case |
| **Data availability** | Do we have the training or retrieval data needed? | Requires data we do not own and cannot acquire |
| **Latency** | Can the AI respond within user-acceptable time? | P99 latency > 5s for a synchronous user interaction |
| **Hallucination risk** | Can we detect and contain model errors? | No fallback or verification layer is feasible |
| **Retrieval architecture** | If using RAG — is the retrieval layer reliable? | No clean, structured data source to ground the model |
| **Cost at scale** | Is the inference cost sustainable at target volume? | Unit economics break at scale |
| **Regulatory risk** | Does this use case carry AI-specific legal exposure? | Regulated industry with no AI governance framework in place |

### 4.3 Technical Risk Register

```
## Technical Risk Register: [Opportunity Name]

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
|      | H / M / L  | H / M / L |          |
|      | H / M / L  | H / M / L |          |
|      | H / M / L  | H / M / L |          |

Highest risk item requiring immediate validation:
_______________________________________________

Spike or prototype needed before committing:
Yes / No — Description: _______________________________________________
```

---

## Dimension 5: Business Impact

### 5.1 Impact Dimensions

| Impact Type | Metric | How to Estimate |
|---|---|---|
| **Revenue** | New ARR, expansion revenue, conversion lift | Addressable users × conversion rate × ARPU |
| **Retention** | D7, D30, churn reduction | Cohort analysis on similar feature launches |
| **Acquisition** | New user growth, channel expansion | Comparable product launches in adjacent markets |
| **Strategic leverage** | Platform value, partner enablement, moat widening | Qualitative assessment with leadership |
| **Cost reduction** | Efficiency gains, support ticket reduction | Current cost × estimated reduction % |

### 5.2 Business Impact Scorecard

```
BUSINESS IMPACT ESTIMATE

Revenue impact (12 months):
Low: < $500K  |  Medium: $500K–$2M  |  High: > $2M
Estimate: _______________  |  Confidence: Low / Medium / High

Retention impact:
Low: < 2% improvement  |  Medium: 2–5%  |  High: > 5%
Estimate: _______________  |  Confidence: Low / Medium / High

Strategic leverage:
Low: Isolated feature  |  Medium: Platform enabler  |  High: Moat-widening
Assessment: _______________

Time to first impact:
< 3 months / 3–6 months / 6–12 months / > 12 months

Payback period on investment:
< 6 months / 6–12 months / > 12 months
```

---

## Opportunity Scoring Model

### Weighted Scoring Formula

Score each dimension 1–3, then calculate:

```
OPPORTUNITY SCORE

Dimension Scores (1 = Weak, 2 = Moderate, 3 = Strong):

User Pain Score:        ___ / 3
Market Size Score:      ___ / 3
Strategic Fit Score:    ___ / 3
Business Impact Score:  ___ / 3

Technical Complexity (inverse — 1 = Very complex, 3 = Straightforward):
Complexity Score:       ___ / 3

Opportunity Score = (User Pain + Market Size + Strategic Fit + Business Impact)
                    ÷ (4 - Complexity Score + 1)

Your Score: ___ / 3.0
```

### Score Interpretation

| Score | Interpretation | Recommended Action |
|---|---|---|
| **2.5 – 3.0** | Strong opportunity | Proceed to initiative definition |
| **2.0 – 2.4** | Promising — gaps exist | Identify weakest dimension; run targeted validation |
| **1.5 – 1.9** | Marginal | Do not commit resources; revisit in next planning cycle |
| **< 1.5** | Weak or premature | Do not pursue at this time |

---

## Templates

### Template A: Full Opportunity Assessment Document

```
# Opportunity Assessment: [Opportunity Title]
Date: ___  |  Author: ___  |  Version: ___  |  Decision Due: ___

## The Opportunity in One Sentence
[What we could build, for whom, and why it matters]

## Dimension 1 — User Problem
Target user: _______________
Job to be done: _______________
Core problem: _______________
Current workaround: _______________
Frequency: Daily / Weekly / Monthly
Severity: Churns users / Major frustration / Mild annoyance
Evidence: _______________
User Pain Score: ___ / 3

## Dimension 2 — Market Opportunity
TAM: _______________
SAM: _______________
SOM (12–24 months): _______________
Market growth rate: _______________
Key competitive gap: _______________
Market Size Score: ___ / 3

## Dimension 3 — Strategic Fit
Aligns with vision: Yes / Partially / No
Leverages existing strength: Yes / Partially / No
Widens competitive moat: Yes / Partially / No
Strategic Fit Score: ___ / 3

## Dimension 4 — Technical Feasibility
MVP buildable in one quarter: Yes / No / Needs spike
Top 3 technical risks: _______________
AI-specific risks (if applicable): _______________
Complexity Score (inverse): ___ / 3

## Dimension 5 — Business Impact
Revenue impact (12 months): _______________
Retention impact: _______________
Strategic leverage: Low / Medium / High
Business Impact Score: ___ / 3

## Opportunity Score
(User Pain + Market + Strategic Fit + Business Impact) ÷ Complexity
= ___ / 3.0

## Recommendation
[ ] Proceed — define as a product initiative
[ ] Validate further — [specific dimension needing more evidence]
[ ] Do not pursue — [reason]

## Next Steps (if proceeding or validating)
1. _______________
2. _______________
3. _______________

Owner: _______________  |  Review Date: _______________
```

### Template B: Rapid Opportunity Screen (30-minute version)

```
# Rapid Opportunity Screen: [Title]
Date: ___  |  Owner: ___

1. What is the problem and who has it?
   _______________________________________________

2. How do we know the problem is real? (Evidence)
   _______________________________________________

3. How large is the addressable market? (Best estimate)
   _______________________________________________

4. Does this align with our strategy and vision?
   Yes / Partially / No — Why: _______________________________________________

5. Can we build a first version in < 90 days?
   Yes / No — Blocker: _______________________________________________

6. What is the expected business impact?
   _______________________________________________

Gut score (1–3 per dimension):
Pain: ___  Market: ___  Fit: ___  Impact: ___  Complexity (inverse): ___

Provisional recommendation:
[ ] Worth a full assessment   [ ] Validate one dimension first   [ ] Drop
```

### Template C: Opportunity Backlog

```
| Opportunity | Pain | Market | Fit | Impact | Complexity | Score | Status |
|-------------|------|--------|-----|--------|------------|-------|--------|
|             |      |        |     |        |            |       | 🔵 New |
|             |      |        |     |        |            |       | 🟡 Assessing |
|             |      |        |     |        |            |       | 🟢 Approved |
|             |      |        |     |        |            |       | ⛔ Rejected |
|             |      |        |     |        |            |       | 🔁 Revisit |
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Skipping the user problem and starting with a solution | Always validate the problem before evaluating the solution |
| Using TAM to justify a weak SOM | Size the market you can actually reach in 24 months |
| Treating strategic fit as automatically satisfied | Explicitly test: does this widen the moat or fragment the product? |
| Ignoring AI-specific feasibility risks | Always run the AI feasibility checklist for AI-dependent opportunities |
| Scoring based on opinion, not evidence | Every score must be supported by at least one piece of evidence |
| Assessing opportunities in isolation | Compare scores across all live opportunities before committing |
| Never revisiting rejected opportunities | Set a review date — market conditions change |
| Building before the assessment is complete | No engineering work begins until all five dimensions are scored |

---

## Cadence

| Review Type | Frequency | Trigger |
|---|---|---|
| Rapid screen | As needed | New idea surfaces |
| Full assessment | Before quarterly planning | Opportunity shortlisted for roadmap |
| Backlog review | Quarterly | Planning cycle — rescore all open opportunities |
| Rejected opportunity revisit | Every 6 months | Market or technology condition has changed |
| Post-launch retrospective | 3 months post-launch | Did the assessment predict the outcome? |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Run a Full Opportunity Assessment

> **Best for:** Any new product idea, feature request, or market entry decision that needs structured evaluation before resources are committed.

```
You are an expert product strategist helping me run a structured Product Opportunity Assessment.

Walk me through each of the five dimensions below, one at a time. For each dimension, ask me targeted questions, listen to my answers, and then give me a score from 1–3 with a clear rationale. Flag any score below 2 as a potential kill signal and tell me what I would need to validate to raise it.

The five dimensions are:
1. User Problem — Is the pain real, frequent, and severe enough to change behaviour?
2. Market Opportunity — Is the addressable market large enough and growing?
3. Strategic Fit — Does this strengthen our position or fragment it?
4. Technical Feasibility — Can we build something reliable within two quarters?
5. Business Impact — Will this move a metric that matters for the company?

After scoring all five dimensions, calculate the Opportunity Score:
Score = (User Pain + Market Size + Strategic Fit + Business Impact) ÷ (4 - Complexity + 1)

Then give me a clear recommendation:
- Proceed (score ≥ 2.5) — define as an initiative
- Validate further (score 2.0–2.4) — identify the weakest dimension
- Do not pursue (score < 2.0) — explain why

My opportunity: [describe the idea or opportunity in 3–5 sentences]
My product and target user: [describe]
Evidence I already have: [what do I know so far?]
```

---

### Prompt 2 — Validate the User Problem

> **Best for:** Before committing to a full assessment — quickly determine whether the problem is real enough to be worth investigating.

```
You are a product researcher helping me validate whether a user problem is real, frequent, and painful enough to build a product around.

Ask me 8 diagnostic questions — one at a time — to probe the problem deeply. After each answer, reflect back what I said in sharpened language and identify any assumption I am making that still needs evidence.

After all 8 questions, give me a verdict:
- Validated: the problem is real, frequent, and severe — proceed to full assessment
- Partially validated: real problem, but frequency or severity is unclear — run targeted research first
- Not validated: insufficient evidence — do not proceed until [specific research is done]

Also tell me the single most important research action I should take before committing to this opportunity.

The problem I am investigating: [describe the user problem]
The user I believe has this problem: [describe]
Evidence I have today: [what do I know?]
```

---

### Prompt 3 — Score and Prioritise Multiple Opportunities

> **Best for:** Quarterly planning where you have a backlog of opportunities and need to decide which ones make it onto the roadmap.

```
You are a product strategy advisor helping me prioritise a backlog of product opportunities.

For each opportunity I give you, score it across five dimensions using a 1–3 scale:
1. User Pain — frequency × severity of the problem
2. Market Size — TAM/SAM attractiveness and growth
3. Strategic Fit — alignment with vision and competitive positioning
4. Business Impact — revenue, retention, or strategic leverage potential
5. Technical Complexity (inverse) — 3 = straightforward, 1 = very complex

Calculate an Opportunity Score for each:
Score = (User Pain + Market Size + Strategic Fit + Business Impact) ÷ (4 - Complexity + 1)

Then rank all opportunities and place them into tiers:
- Tier 1 (score ≥ 2.5): Proceed — define as initiatives for this quarter
- Tier 2 (score 2.0–2.4): Validate — identify the weakest dimension and the research needed
- Tier 3 (score < 2.0): Defer or drop

For any Tier 1 opportunity, suggest the first three steps to move it into initiative definition.

My strategic pillars: [list them]
My opportunities to evaluate:
1. [Opportunity name — brief description]
2. [Opportunity name — brief description]
3. [Opportunity name — brief description]
```

---

### Prompt 4 — AI-Specific Feasibility Assessment

> **Best for:** Any opportunity that involves an AI capability — before committing engineering resources to a solution that may not be technically viable.

```
You are an AI product architect helping me assess the technical feasibility of an AI-powered product opportunity.

Evaluate the opportunity across these seven AI-specific feasibility dimensions:
1. Model reliability — does a reliable model exist for this task at the required accuracy?
2. Data availability — do we have the training or retrieval data needed?
3. Latency — can the AI respond within user-acceptable time for this use case?
4. Hallucination risk — how severe is the risk, and can we mitigate it?
5. Retrieval architecture — if RAG is needed, is a reliable data source available?
6. Cost at scale — are the inference economics sustainable at target volume?
7. Regulatory risk — does this use case carry AI-specific legal or compliance exposure?

For each dimension, give a rating: Green (feasible), Amber (feasible with mitigation), Red (blocking risk).

Then give me:
- An overall feasibility verdict: Proceed / Proceed with spikes / Do not proceed yet
- The single highest-risk dimension and the specific spike or prototype that would de-risk it
- A recommended architecture approach (generation, RAG, classification, orchestration, or hybrid)

My opportunity: [describe what the AI needs to do]
My current data assets: [what data do I have access to?]
Target user and use case: [describe]
Acceptable latency: [what is the user's tolerance?]
```

---

### Prompt 5 — Write the Opportunity Assessment Document

> **Best for:** After you have done the research and scoring — turning your findings into a clean, stakeholder-ready assessment document.

```
You are a senior product manager helping me write a structured Opportunity Assessment document that I can share with leadership for a go / no-go decision.

Using the information I provide below, write a complete assessment document with these sections:
1. The opportunity in one sentence
2. User Problem — with evidence, frequency, severity, and a Pain Score (1–3)
3. Market Opportunity — TAM, SAM, SOM, growth rate, and competitive gap
4. Strategic Fit — alignment with vision, capability leverage, and moat impact
5. Technical Feasibility — key risks, complexity score, and any AI-specific considerations
6. Business Impact — revenue, retention, and strategic leverage estimates
7. Opportunity Score — calculated from the five dimension scores
8. Recommendation — Proceed / Validate Further / Do Not Pursue, with rationale
9. Next steps — three specific actions with owners and timelines

Write in clear, direct language. No jargon. Every claim should be supported by the evidence I provide. Where evidence is missing, flag it explicitly rather than filling in with assumptions.

My inputs:
Opportunity: [describe]
User research findings: [summarise]
Market data: [what do you know?]
Strategic context: [how does this fit the product strategy?]
Technical assessment: [what does the eng team say?]
Business impact estimates: [revenue, retention, etc.]
```
