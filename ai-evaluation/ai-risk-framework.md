# ⚠️ AI Risk Framework — AI Product Builder Playbook

> **A structured approach for identifying, assessing, mitigating, and governing the risks specific to AI-powered products**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The AI Risk Model](#the-ai-risk-model)
- [Risk Category 1: Output Quality Risks](#risk-category-1-output-quality-risks)
- [Risk Category 2: Safety and Harm Risks](#risk-category-2-safety-and-harm-risks)
- [Risk Category 3: Privacy and Data Risks](#risk-category-3-privacy-and-data-risks)
- [Risk Category 4: Operational Risks](#risk-category-4-operational-risks)
- [Risk Category 5: Strategic and Reputational Risks](#risk-category-5-strategic-and-reputational-risks)
- [Risk Assessment and Scoring](#risk-assessment-and-scoring)
- [Risk Governance](#risk-governance)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

AI products carry risks that traditional software does not. A bug in conventional software produces a deterministic, reproducible error. A risk in an AI system produces probabilistic, often invisible failures that may affect thousands of users before they are detected — and may be impossible to fully reproduce.

> **Core Principle:** AI risk management is not about preventing AI from being useful. It is about understanding the failure modes before they happen, designing systems that catch them, and building organisations that respond to them proportionally. The teams that do this well build more ambitious AI products, not less ambitious ones.

Risk management in AI requires thinking across five distinct categories simultaneously: the quality of what the model produces, the potential for harm to users or third parties, the privacy implications of data flows, the operational stability of the system, and the strategic and reputational exposure to the organisation. Missing any category produces a framework with critical blind spots.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Launching a new AI feature or product | 🔴 Critical — complete before launch |
| Entering a regulated industry with AI | 🔴 Critical — compliance requirements are non-negotiable |
| AI feature generating complaints or media attention | 🔴 Critical — active risk materialisation |
| Changing model providers or upgrading models | 🟠 High — new models have different risk profiles |
| Expanding AI feature to a new user segment or geography | 🟠 High — different contexts create different risks |
| Annual governance review | 🟡 Medium |
| Evaluating a third-party AI component for integration | 🟡 Medium |

---

## The AI Risk Model

AI risks fall into five categories. Each category requires a different assessment approach and a different mitigation strategy.

```
OUTPUT QUALITY RISKS
  ↓ risks from model outputs that are wrong, incomplete, or misleading
SAFETY AND HARM RISKS
  ↓ risks of causing harm to users, third parties, or society
PRIVACY AND DATA RISKS
  ↓ risks from how data flows through and is processed by AI systems
OPERATIONAL RISKS
  ↓ risks to system availability, performance, and cost
STRATEGIC AND REPUTATIONAL RISKS
  ↓ risks to the organisation's position, trust, and compliance standing
```

| Category | Primary Owner | Assessment Method | Governance Level |
|---|---|---|---|
| **Output quality** | PM + AI team | Evaluation dataset + monitoring | Sprint-level |
| **Safety and harm** | PM + Legal + AI team | Red team + policy review | Feature launch gate |
| **Privacy and data** | PM + Legal + Security | Data flow audit + DPA | Legal sign-off |
| **Operational** | Engineering + PM | Reliability assessment + load testing | Architecture review |
| **Strategic and reputational** | PM + Leadership | Scenario planning + stakeholder assessment | Executive sign-off |

---

## Risk Category 1: Output Quality Risks

### 1.1 Risk Inventory

| Risk | Description | Likelihood Factors | Impact Factors |
|---|---|---|---|
| **Hallucination** | Model generates factually incorrect information presented as fact | Complex queries, knowledge gaps, no RAG | User acts on false information |
| **Outdated information** | Model provides information that was correct at training but is now wrong | Time-sensitive domains | Incorrect decisions |
| **Incomplete output** | Model provides partial answer, omitting critical information | Complex multi-part questions | User proceeds with incomplete understanding |
| **Overconfident output** | Model presents uncertain information with inappropriate certainty | No uncertainty communication designed | Trust damage when errors discovered |
| **Format failure** | Model does not follow required output format | Complex formatting requirements | Downstream system failures |
| **Context window overflow** | Context is truncated, causing model to lose important information | Long conversations or documents | Inconsistent or confused outputs |

### 1.2 Quality Risk Assessment

```
QUALITY RISK ASSESSMENT — [Feature Name]

For each quality risk, rate:
Likelihood: 1 (Rare) → 5 (Almost certain)
Impact: 1 (Negligible) → 5 (Severe)
Risk Score = Likelihood × Impact

| Risk | Likelihood | Impact | Score | Mitigation |
|------|------------|--------|-------|------------|
| Hallucination | | | | |
| Outdated info | | | | |
| Incomplete output | | | | |
| Overconfidence | | | | |
| Format failure | | | | |
| Context overflow | | | | |

Risk priority:
Score 20–25: Critical — must be mitigated before launch
Score 12–19: High — strong mitigation required
Score 6–11: Medium — standard mitigation
Score 1–5: Low — monitor only
```

### 1.3 Hallucination Risk Profile

Not all hallucination risk is equal. Assess the specific profile:

| Dimension | Low Risk | High Risk |
|---|---|---|
| **Domain** | Creative or exploratory tasks | Factual, medical, legal, financial |
| **User action** | Informational, low-stakes | User acts on output — financial, medical, safety |
| **Verifiability** | User can easily check the output | Output is difficult or impossible to verify |
| **Audience** | Expert users who detect errors | Non-expert users who accept outputs as fact |
| **Volume** | Low usage, errors caught quickly | High usage, errors propagate widely |

---

## Risk Category 2: Safety and Harm Risks

### 2.1 Risk Inventory

| Risk | Description | Who Is Harmed | Severity |
|---|---|---|---|
| **Harmful content generation** | Model generates content that could harm the user or others | User or third parties | Critical |
| **Biased or discriminatory outputs** | Model produces outputs that unfairly disadvantage groups | Affected user groups | High |
| **Manipulation or deception** | AI is used to manipulate user beliefs or behaviour | User | High |
| **Enabling illegal activity** | AI assists with activities that are illegal | Third parties, society | Critical |
| **Vulnerable user harm** | AI interacts with vulnerable users (children, mental health) in harmful ways | Vulnerable users | Critical |
| **Autonomy erosion** | AI makes consequential decisions without adequate human oversight | User | High |
| **Safety-critical error** | AI provides wrong information in a safety-critical context (medical, safety) | User | Critical |

### 2.2 Safety Risk Assessment

```
SAFETY RISK ASSESSMENT — [Feature Name]

Product context:
[ ] This product may be used by minors
[ ] This product operates in a safety-critical domain (medical / legal / financial / safety)
[ ] This product may reach vulnerable user populations
[ ] This product is consumer-facing (vs enterprise B2B)
[ ] This product generates content that could be shared with third parties

For each safety risk, assess:
Could this risk materialise with our product? Yes / Possibly / No
If yes or possibly: what is the severity? Critical / High / Medium / Low
What is our current mitigation? [describe]
Is the mitigation sufficient? Yes / Partial / No

| Risk | Could materialise? | Severity | Current mitigation | Sufficient? |
|------|-------------------|----------|-------------------|-------------|
| Harmful content | | | | |
| Bias/discrimination | | | | |
| Manipulation | | | | |
| Illegal activity | | | | |
| Vulnerable user harm | | | | |
| Autonomy erosion | | | | |
| Safety-critical error | | | | |
```

### 2.3 Bias Risk Assessment

AI systems can perpetuate, amplify, or introduce bias. Assess systematically:

```
BIAS RISK ASSESSMENT

Bias types to evaluate:
1. Selection bias — is our training data representative of all user groups?
2. Confirmation bias — does the model reinforce existing user beliefs uncritically?
3. Demographic bias — does model performance differ across gender, race, age, language?
4. Socioeconomic bias — does the model assume a particular economic or cultural context?
5. Recency bias — does the model over-weight recent information?

For each bias type:
[ ] Could it affect our product?
[ ] Have we tested for it?
[ ] What is the mitigation?

Testing approach:
Run 50 identical queries with different demographic signals.
Measure: do outputs differ in quality, tone, or accuracy across groups?
Alert threshold: > 10% performance gap between any two demographic groups.
```

---

## Risk Category 3: Privacy and Data Risks

### 3.1 Risk Inventory

| Risk | Description | Regulatory Implication |
|---|---|---|
| **Training data exposure** | Model memorises and reveals training data | GDPR Art. 17 (right to erasure) |
| **User input exposure** | User inputs are retained or used for training without consent | GDPR Art. 13 (transparency) |
| **Third-party data sharing** | User data is sent to external model providers | GDPR Art. 28 (processor agreements) |
| **PII in model outputs** | Model generates or reveals personal information | GDPR Art. 5 (data minimisation) |
| **Cross-user data leakage** | Memory or context from one user surfaces in another's session | Critical data breach |
| **Inference attack** | Model outputs reveal information about individuals in training data | Potential breach |
| **Data retention violation** | AI interaction data retained longer than policy or regulation allows | Regulatory fine |

### 3.2 Data Flow Audit

```
AI DATA FLOW AUDIT — [Feature Name]

Map every data flow:

User input:
  Collected: Yes / No
  Contains PII?: Yes / Possibly / No
  Sent to: [list all destinations — your servers, model provider, retrieval system, logs]
  Retained: ___ days
  User notified: Yes / No
  Opt-out available: Yes / No

AI output:
  Stored: Yes / No
  Linked to user identity: Yes / No
  Retained: ___ days

Model provider data sharing:
  Provider: _______________________________________________
  Data processed: _______________________________________________
  Data Processing Agreement (DPA) in place: Yes / No
  Provider uses data for training: Yes / No (verify in terms)
  Data residency: _______________________________________________

Memory system (if applicable):
  What is stored: _______________________________________________
  User can view: Yes / No
  User can delete: Yes / No
  Retention policy: _______________________________________________

Risk findings:
[List any data flows that create privacy risk]
```

### 3.3 Privacy Risk Mitigation

| Risk | Primary Mitigation | Secondary Mitigation |
|---|---|---|
| **PII in user input** | Strip PII before sending to model | Log PII detection events for audit |
| **Third-party data sharing** | Execute DPA with all providers | Select providers with no-training-use option |
| **Training data exposure** | Use providers that commit to not training on user data | Avoid sending sensitive personal data |
| **Cross-user leakage** | Strict user-scoped memory isolation | Regular cross-user isolation testing |
| **Data retention violation** | Automated retention enforcement | Regular compliance audit |

---

## Risk Category 4: Operational Risks

### 4.1 Risk Inventory

| Risk | Description | Business Impact |
|---|---|---|
| **Provider dependency** | Single model provider; no fallback | Outage if provider has downtime |
| **Model deprecation** | Provider deprecates model version | Forced migration on provider's timeline |
| **Cost explosion** | Usage spikes beyond budget | Financial exposure |
| **Latency degradation** | Response times increase significantly | User experience failure |
| **Context window exhaustion** | Inputs exceed model's context limit | Silent truncation; quality degradation |
| **Retrieval failure** | Vector store or retrieval system outage | RAG system returns empty context; hallucination risk increases |
| **Model version regression** | Provider silently changes model behaviour | Quality degradation without system change |

### 4.2 Operational Resilience Design

```
OPERATIONAL RESILIENCE CHECKLIST

Provider resilience:
[ ] Primary and secondary model provider identified
[ ] Automatic failover between providers implemented
[ ] Provider status monitoring configured
[ ] Model deprecation dates tracked; migration plans exist

Cost resilience:
[ ] Per-request cost cap implemented
[ ] Daily cost budget alert configured
[ ] Rate limiting implemented to prevent cost explosion from abuse
[ ] Token optimisation reviewed and implemented

Latency resilience:
[ ] Request timeout configured for all AI calls
[ ] Graceful degradation designed (what happens when AI is slow or unavailable?)
[ ] Async processing implemented for non-real-time features
[ ] Caching implemented for high-frequency repeated queries

Data resilience:
[ ] Vector store backup configured
[ ] Recovery time objective (RTO) defined: ___ hours
[ ] Recovery point objective (RPO) defined: ___ hours
[ ] Disaster recovery tested in last 6 months
```

### 4.3 Cost Risk Scenarios

```
COST RISK SCENARIO PLANNING

Base case: ___ queries/day × $___/query = $___/month

Scenario 1 — 5× usage spike (viral moment or bot attack):
  Projected cost: $___ — within budget? Yes / No
  Mitigation: Rate limit at ___ requests/user/hour

Scenario 2 — Model price increase of 30%:
  Projected cost: $___ — within budget? Yes / No
  Mitigation: [model switch / token optimisation / pricing review]

Scenario 3 — Feature goes enterprise (100× usage):
  Projected cost: $___ — sustainable? Yes / No
  Mitigation: [volume discount negotiation / fine-tuning / architecture redesign]

Scenario 4 — Abuse (single user generating 10% of traffic):
  Detection: [monitoring alert at what threshold?]
  Response: [rate limiting / account suspension / CAPTCHA]
```

---

## Risk Category 5: Strategic and Reputational Risks

### 5.1 Risk Inventory

| Risk | Description | Stakeholders Affected |
|---|---|---|
| **Public AI failure** | AI output goes viral for wrong reasons | All users, media, investors |
| **Regulatory action** | Regulator investigates or sanctions AI use | Legal team, leadership |
| **Competitive AI failure** | Competitor's AI failure creates guilt by association | Users (AI trust in category) |
| **Partner/integration risk** | Third-party AI component causes a failure attributed to us | Users, partners |
| **Over-automation backlash** | Users or public object to AI replacing human judgment | Users, media |
| **Model obsolescence** | Faster-moving competitors ship dramatically better AI | Market position |
| **Talent risk** | AI expertise is concentrated in one or two individuals | Engineering continuity |

### 5.2 Reputational Risk Scenarios

```
REPUTATIONAL RISK SCENARIO PLANNING

Scenario: "Our AI gives a user medically dangerous advice"
  Probability: ___  |  Impact: Critical
  Prevention: [medical disclaimer, out-of-scope guardrails, no medical advice policy]
  Response plan: [immediate feature limitation, user notification, media statement]
  Owner: PM + Legal + Communications

Scenario: "Our AI is shown to produce biased outputs against a demographic group"
  Probability: ___  |  Impact: High
  Prevention: [bias testing before launch, diverse evaluation team]
  Response plan: [acknowledge, investigate, publish findings, remediation timeline]
  Owner: PM + Legal

Scenario: "A journalist publishes a story about our AI making up facts"
  Probability: ___  |  Impact: Medium-High
  Prevention: [hallucination monitoring, citation requirements, uncertainty communication]
  Response plan: [transparent acknowledgment of limitations, improvement timeline]
  Owner: PM + Communications
```

---

## Risk Assessment and Scoring

### 6.1 Risk Register

```
AI RISK REGISTER — [Product / Feature Name]
Date: ___  |  Owner: ___  |  Review date: ___

| ID | Category | Risk | Likelihood (1–5) | Impact (1–5) | Score | Mitigation | Status | Owner |
|----|----------|------|-----------------|-------------|-------|------------|--------|-------|
| R1 | Quality | Hallucination | | | | | | |
| R2 | Safety | Harmful content | | | | | | |
| R3 | Privacy | PII in outputs | | | | | | |
| R4 | Operational | Provider outage | | | | | | |
| R5 | Strategic | Public failure | | | | | | |

Risk priority tiers:
🔴 Critical (20–25): Must be mitigated before launch
🟠 High (12–19): Strong mitigation required at launch
🟡 Medium (6–11): Standard mitigation and monitoring
⚪ Low (1–5): Monitor only
```

### 6.2 Risk Appetite Statement

```
RISK APPETITE STATEMENT — [Product / Feature Name]

We will not launch this feature if any of the following risks are CRITICAL (score 20+) without adequate mitigation:
[ ] Hallucination in a safety-critical context
[ ] Any confirmed harmful content risk
[ ] PII exposure to third-party model providers without DPA
[ ] Cross-user data leakage potential

We accept the following risks as inherent to operating an AI product:
[ ] Occasional output quality failures (< 5% of interactions)
[ ] Provider latency variability within SLA
[ ] Cost variance within ±30% of budget

We will escalate to leadership for any risk that:
[ ] Could result in regulatory action
[ ] Could result in media coverage
[ ] Has unclear or unacceptable residual risk after mitigation
```

---

## Risk Governance

### 7.1 Launch Approval Gate

```
AI RISK REVIEW — LAUNCH GATE

Feature: _______________________________________________
Launch date: _______________________________________________

Required sign-offs:
[ ] PM: Risk register complete and reviewed
[ ] Engineering lead: Operational risks mitigated
[ ] Legal: Privacy risks assessed; DPAs in place
[ ] Security: Data flow audit complete
[ ] Leadership: Strategic risks accepted (if High or Critical)

Launch blocked if:
[ ] Any risk remains at Critical (score 20+) without documented mitigation plan
[ ] DPA not in place for any third-party model provider receiving user data
[ ] Safety red team not completed for consumer-facing features
[ ] No monitoring in place for top 3 identified risks

Decision: ✅ Approved for launch  |  ⚠️ Conditional (conditions listed)  |  ❌ Blocked
```

### 7.2 Ongoing Risk Governance Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Risk register review | Monthly | PM |
| New risk identification | Per sprint (if new features added) | PM + Engineering |
| Safety red team | Quarterly | Engineering + PM |
| Privacy compliance review | Quarterly | PM + Legal |
| Strategic risk scenarios | Annually | PM + Leadership |
| Full risk register refresh | Annually or on major model change | PM + Legal + Engineering |

---

## Templates

### Template A: AI Risk Register (abbreviated)

```
# AI Risk Register — [Feature Name]
Date: ___  |  Version: ___  |  Next review: ___

## Risk Summary
Total risks identified: ___
Critical: ___  |  High: ___  |  Medium: ___  |  Low: ___
Launch blocked by: [list any critical unmitigated risks]

## Top 5 Risks
[Complete risk register in spreadsheet — summarise top 5 here with mitigation status]

## Launch Approval Status
[ ] Approved  [ ] Conditional — [condition]  [ ] Blocked — [reason]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Risk assessment as a one-time pre-launch activity | Living risk register — reviewed monthly, updated with each major change |
| Only assessing output quality risks | All five categories must be assessed — operational and strategic risks are commonly missed |
| No data flow audit before launch | Audit every data flow before the first user interaction |
| Risk mitigation claimed without verification | Every mitigation must have a test that confirms it is working |
| No risk appetite statement | Teams need to know which risks are acceptable and which block launch |
| Legal sign-off treated as a rubber stamp | Legal must review the actual data flow audit, not just be notified |
| Risk assessment done by PM alone | Cross-functional: PM + Engineering + Legal + Security minimum |
| No scenario planning for strategic risks | The most damaging risks are often the ones no one thought to document |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Risk register review | Monthly | Ongoing |
| New feature risk assessment | Per feature | Before design begins |
| Safety red team | Quarterly | Systematic attempt to find new risks |
| Privacy audit | Quarterly | Regulatory compliance |
| Strategic risk scenarios | Annually | Planning cycle |
| Full risk framework refresh | Annually or on model change | Major system update |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Complete an AI Risk Assessment

> **Best for:** Running a comprehensive risk assessment before launching an AI feature or product.

```
You are an AI risk specialist helping me complete a comprehensive risk assessment before launching an AI feature.

Assess risks across all five categories:

1. Output quality risks — hallucination, outdated info, incomplete output, overconfidence, format failure
2. Safety and harm risks — harmful content, bias, manipulation, illegal activity, vulnerable user harm
3. Privacy and data risks — PII exposure, third-party data sharing, training data exposure, cross-user leakage
4. Operational risks — provider dependency, cost explosion, latency degradation, model deprecation
5. Strategic and reputational risks — public failure scenario, regulatory action, competitive risk

For each risk:
- Rate likelihood (1–5) and impact (1–5)
- Calculate risk score (likelihood × impact)
- Recommend a specific mitigation
- Assess whether the mitigation is sufficient given the score

After all categories:
- Identify the top 3 risks by score
- Identify any risks that should block launch
- Write the risk appetite statement for this feature
- Draft the launch approval gate checklist

My AI feature: [describe what it does]
User segment: [who uses it]
Domain: [what topic area — medical / legal / financial / general]
Data processed: [what user data enters the system]
Model provider: [which provider and model]
Regulatory environment: [any compliance requirements]
```

---

### Prompt 2 — Conduct a Bias Risk Assessment

> **Best for:** Evaluating whether an AI feature might produce systematically biased outputs across user groups.

```
You are an AI fairness specialist helping me assess the bias risk in my AI feature.

Evaluate bias risk across five dimensions:
1. Selection bias — is our training data or retrieval data representative of all user groups?
2. Demographic bias — might the model perform differently across gender, race, age, language, or location?
3. Confirmation bias — might the model reinforce existing user beliefs without appropriate challenge?
4. Socioeconomic bias — does the model assume a particular economic or cultural context?
5. Recency bias — might the model over-weight recent information or trends?

For each dimension:
- Rate the likelihood of bias affecting my feature: High / Medium / Low
- Describe specifically how the bias might manifest in outputs
- Write 5 test cases I should run to detect this bias
- Recommend a mitigation

After all dimensions:
- Design the bias testing protocol for my feature
- Write the threshold: at what level of performance difference between groups should I consider the feature biased?
- Recommend whether external fairness audit is needed before launch

My AI feature: [describe]
User segment: [describe the diversity of my user base]
Type of AI task: [generation / classification / recommendation / summarisation / other]
Data sources used: [describe training data or retrieval corpus]
Known bias concerns: [any existing awareness of potential bias]
```

---

### Prompt 3 — Complete a Privacy and Data Flow Audit

> **Best for:** Mapping every data flow through an AI system to identify privacy risks before launch.

```
You are a privacy specialist helping me audit the data flows in my AI product for privacy risk.

Map and assess every data flow across the AI system:

1. User input flows
   - What data does the user provide?
   - Where does it go? (Your servers / Model provider / Retrieval system / Logs)
   - What PII might it contain?
   - How long is it retained?
   - Is the user notified?

2. Model processing flows
   - Is user data sent to a third-party model provider?
   - Is there a Data Processing Agreement in place?
   - Does the provider use data for training?
   - What is the data residency?

3. Output and storage flows
   - Are AI outputs stored?
   - Are they linked to user identity?
   - How long are they retained?

4. Memory system flows (if applicable)
   - What is stored in the AI memory system?
   - Can the user view and delete it?
   - Is there a retention limit?

For each data flow:
- Identify the privacy risk
- Rate the risk: Critical / High / Medium / Low
- Recommend the mitigation
- Identify any regulatory requirement triggered (GDPR / CCPA / other)

After the audit:
- Identify the top 3 privacy risks requiring immediate action
- Write the user-facing privacy disclosure for this feature
- Draft the DPA requirements checklist for the model provider

My AI feature: [describe]
Data collected from users: [list]
Model provider: [name]
Geography of users: [EU / US / global]
Existing privacy framework: [GDPR / CCPA / none / other]
```

---

### Prompt 4 — Plan Operational Resilience

> **Best for:** Designing the operational risk mitigations that keep an AI feature running reliably under adverse conditions.

```
You are an AI reliability engineer helping me plan operational resilience for my AI feature.

Design the resilience plan across four areas:

1. Provider resilience
   - Which secondary provider should I use as a fallback?
   - How should automatic failover work? (describe the logic)
   - How do I monitor provider health independently from my application?
   - What is the migration plan if my primary provider deprecates the model?

2. Cost resilience
   - What per-request cost cap should I set?
   - At what daily cost threshold should I alert?
   - How do I detect and block cost-explosion abuse patterns?
   - What token optimisation should I implement to reduce baseline cost?

3. Latency resilience
   - What timeout should I set for each AI call?
   - What does the user experience when the AI times out? (design the graceful degradation)
   - Which features can be moved to async processing to protect UX?
   - What queries should be cached to reduce latency and cost?

4. Data resilience
   - What is my recovery plan if the vector store fails?
   - What is my RTO and RPO for the AI system?
   - When did I last test disaster recovery?

After the resilience plan:
- Run three cost risk scenarios: 5× usage spike, 30% price increase, 100× enterprise scale
- Identify the single highest operational risk and its mitigation
- Write the runbook for the most likely operational failure mode

My AI feature: [describe]
Current provider: [name]
Daily query volume: [number]
Current monthly cost: $[number]
SLA commitment to users: [uptime and latency]
```

---

### Prompt 5 — Prepare a Strategic Risk Scenario Plan

> **Best for:** Preparing for reputational, regulatory, and competitive AI risks before they materialise.

```
You are a strategic risk advisor helping me prepare for the AI-specific risks that could damage our organisation's reputation, regulatory standing, or competitive position.

Design a strategic risk scenario plan covering:

1. Public failure scenario
   "A journalist or user shares our AI's worst output publicly."
   - What is the most damaging single output our AI could produce?
   - What is our 24-hour response plan?
   - What preventive measures reduce the likelihood of this output being produced?

2. Regulatory risk scenario
   "A regulator investigates our use of AI."
   - What regulatory frameworks apply to us?
   - What evidence of responsible AI practice could we produce?
   - What is our worst-case regulatory exposure?

3. Bias or discrimination scenario
   "Our AI is shown to produce outputs that disadvantage a specific group."
   - How would this be discovered? (external researcher / user complaint / internal audit)
   - What is our response plan?
   - What evidence of bias testing would we produce?

4. Competitive risk scenario
   "A competitor ships AI that is dramatically better or cheaper."
   - What is our current AI differentiation?
   - How long would it take us to respond?
   - What would we have to sacrifice to respond quickly?

For each scenario:
- Rate probability: High / Medium / Low
- Rate impact: Critical / High / Medium
- Write the specific prevention measures
- Write the first 48-hour response plan

My AI product: [describe]
User base: [size and type]
Regulatory environment: [applicable regulations]
Competitive context: [describe the AI competitive landscape]
```
