# 🎯 AI Capability Maturity Model — AI Product Builder Playbook

> **A framework for assessing, benchmarking, and advancing an organisation's capability to design, build, and operate AI-powered products**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Maturity Model Structure](#the-maturity-model-structure)
- [Capability Domain 1: Strategy and Vision](#capability-domain-1-strategy-and-vision)
- [Capability Domain 2: Data and Infrastructure](#capability-domain-2-data-and-infrastructure)
- [Capability Domain 3: AI Development and Deployment](#capability-domain-3-ai-development-and-deployment)
- [Capability Domain 4: Evaluation and Quality](#capability-domain-4-evaluation-and-quality)
- [Capability Domain 5: Governance and Ethics](#capability-domain-5-governance-and-ethics)
- [Capability Domain 6: Organisation and Talent](#capability-domain-6-organisation-and-talent)
- [Running a Maturity Assessment](#running-a-maturity-assessment)
- [Maturity Advancement Roadmap](#maturity-advancement-roadmap)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Most organisations believe they are further along in AI capability than they actually are. Leadership sees successful AI demos and assumes production readiness. Engineering teams build impressive prototypes but lack the operational infrastructure to maintain them. Product teams ship AI features without the evaluation frameworks to know whether they are working.

> **Core Principle:** AI capability is not binary — present or absent. It is a spectrum, and every organisation sits somewhere on that spectrum across multiple dimensions simultaneously. The maturity model makes that location explicit, surfaces the gaps that matter most, and provides a structured path forward.

The AI Capability Maturity Model (AI-CMM) assesses capability across six domains: strategy, data and infrastructure, AI development and deployment, evaluation and quality, governance and ethics, and organisation and talent. An organisation that scores highly on development but poorly on governance is not a mature AI organisation — it is an organisation with a visible risk accumulating in plain sight.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting an AI transformation initiative | 🔴 Critical — establish baseline before planning |
| Leadership wants to know "where we are" on AI | 🔴 Critical — provides structured, honest answer |
| AI investments are not producing expected returns | 🟠 High — likely a capability gap, not a strategy gap |
| Hiring or building an AI product team | 🟠 High — assess what capability you actually have |
| Evaluating a partner or acquisition target's AI readiness | 🟠 High |
| Annual planning — AI investment prioritisation | 🟡 Medium |
| Board or investor reporting on AI readiness | 🟡 Medium |

---

## The Maturity Model Structure

Each capability domain is assessed across five maturity levels. The levels are consistent across all domains:

```
LEVEL 1 — INITIAL
Ad hoc, undocumented, reactive. Success depends on heroics.

LEVEL 2 — DEVELOPING
Basic processes exist but are inconsistent. Some documentation.
Repeatable within teams but not across the organisation.

LEVEL 3 — DEFINED
Standardised, documented processes. Consistent execution across teams.
Organisation can onboard new members to AI practices reliably.

LEVEL 4 — MANAGED
Processes are measured. Decisions are data-driven.
Organisation can predict outcomes and detect problems early.

LEVEL 5 — OPTIMISING
Continuous improvement is embedded. Organisation learns systematically.
AI capability is a competitive differentiator, not just operational infrastructure.
```

| Level | Description | Key Signal |
|---|---|---|
| **1 — Initial** | Reactive, ad hoc | "We figure it out each time" |
| **2 — Developing** | Basic processes, inconsistent | "Some teams do this well" |
| **3 — Defined** | Standardised across the org | "Everyone follows the same process" |
| **4 — Managed** | Measured and data-driven | "We know how well we are doing" |
| **5 — Optimising** | Continuous improvement | "We get better automatically" |

---

## Capability Domain 1: Strategy and Vision

### 1.1 Domain Description

Strategy and Vision assesses whether the organisation has a coherent, actionable AI strategy that is connected to business outcomes and understood across the organisation.

### 1.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | No AI strategy. AI projects are reactive to vendor pitches or competitor announcements. | No documented strategy; projects chosen opportunistically |
| **2** | Informal AI vision exists in leadership. Individual teams pursue AI initiatives without coordination. | Vision in leadership heads; no cross-team alignment |
| **3** | Documented AI strategy aligned to business outcomes. Product teams understand how AI fits their roadmap. | Strategy doc exists; teams can explain AI's role in their work |
| **4** | AI strategy is measured against defined outcomes. Regular review cadence with adjustments based on results. | Strategy has metrics; quarterly review with data |
| **5** | AI strategy dynamically incorporates market signals, capability advances, and competitive intelligence. | Strategy evolves in response to learning; feeds back into capability investment |

### 1.3 Assessment Questions

```
STRATEGY AND VISION ASSESSMENT

1. Does a documented AI strategy exist?
   [ ] No documentation (L1)
   [ ] Informal / in leadership heads (L2)
   [ ] Documented and shared (L3)
   [ ] Documented with metrics (L4)
   [ ] Living document with defined review cadence (L5)

2. Do product teams understand how AI fits their roadmap?
   [ ] Most do not (L1–L2)
   [ ] Some do (L2–L3)
   [ ] Most do (L3)
   [ ] All do, with measurable KPIs (L4)
   [ ] Teams contribute to strategy evolution (L5)

3. Are AI investments connected to business outcomes?
   [ ] No explicit connection (L1)
   [ ] Loosely connected (L2)
   [ ] Explicitly connected with defined metrics (L3)
   [ ] Tracked and adjusted based on outcome data (L4)
   [ ] Outcomes inform strategy in real-time (L5)

4. Is AI prioritised against other technology investments?
   [ ] No formal prioritisation (L1)
   [ ] Ad hoc (L2)
   [ ] Structured prioritisation framework (L3)
   [ ] Data-driven with outcome history (L4)
   [ ] Portfolio optimisation based on measured returns (L5)

Domain score: ___ / 5
```

---

## Capability Domain 2: Data and Infrastructure

### 2.1 Domain Description

Data and Infrastructure assesses the organisation's ability to collect, manage, and serve the data that AI systems need — and to operate the infrastructure required to run them reliably.

### 2.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | Data is siloed, inconsistent, and difficult to access. No AI-specific infrastructure. | Teams export CSVs manually; no vector store; no MLOps |
| **2** | Basic data pipelines exist. Some teams can access structured data. Cloud infrastructure available but not standardised. | Data warehouse exists; pipelines inconsistent; no feature store |
| **3** | Centralised data platform. Consistent data quality standards. AI-specific infrastructure (vector store, embedding pipeline) deployed. | Data catalogue exists; quality monitored; retrieval infrastructure in production |
| **4** | Data quality is measured and SLAs are enforced. Infrastructure is observable and optimised. Cost per AI inference is tracked. | Data quality dashboards; infrastructure SLAs; cost monitoring |
| **5** | Data infrastructure automatically adapts to AI system needs. Proactive data quality improvement. Self-optimising pipelines. | Automated data quality; adaptive infrastructure; no manual intervention needed |

### 2.3 Assessment Questions

```
DATA AND INFRASTRUCTURE ASSESSMENT

1. Data accessibility
   [ ] Siloed in departments — requires manual extraction (L1)
   [ ] Basic data warehouse — some teams can query (L2)
   [ ] Centralised platform — all teams can access consistently (L3)
   [ ] Quality-monitored with SLAs (L4)
   [ ] Self-adapting pipelines (L5)

2. Data quality
   [ ] No standards — quality unknown (L1)
   [ ] Some validation — inconsistent (L2)
   [ ] Defined standards and monitoring (L3)
   [ ] Quality SLAs enforced with alerting (L4)
   [ ] Automated remediation (L5)

3. AI-specific infrastructure (vector store, embeddings, retrieval)
   [ ] Does not exist (L1)
   [ ] Prototyped in one project (L2)
   [ ] Standardised and deployed for production (L3)
   [ ] Observable with performance monitoring (L4)
   [ ] Self-optimising (L5)

4. MLOps / AI deployment infrastructure
   [ ] Manual deployment — no CI/CD for AI (L1)
   [ ] Basic CI/CD — inconsistent (L2)
   [ ] Standardised deployment pipeline (L3)
   [ ] Observable with automated rollback (L4)
   [ ] Automated optimisation and self-healing (L5)

Domain score: ___ / 5
```

---

## Capability Domain 3: AI Development and Deployment

### 3.1 Domain Description

AI Development and Deployment assesses how the organisation designs, builds, tests, and ships AI features — from prompt engineering discipline to architecture decisions to production deployment practices.

### 3.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | AI development is experimental. No standards. Individual developers make architecture decisions alone. | No prompt versioning; no shared patterns; no deployment standards |
| **2** | Some teams have established patterns. Architecture decisions made at team level. Basic prompt management. | Patterns documented in some teams; prompt changes ad hoc |
| **3** | Shared AI development standards across all teams. Prompt versioning enforced. Architecture review process exists. | AI design principles; prompt version control; cross-team review |
| **4** | Development practices are measured. Deployment is automated. Quality gates are enforced before production. | Metrics on development velocity and quality; automated deployment; quality gates |
| **5** | Development practices continuously optimise based on production feedback. Architecture self-adapts to emerging capabilities. | Learning loops from production to development; proactive architecture evolution |

### 3.3 Assessment Questions

```
AI DEVELOPMENT AND DEPLOYMENT ASSESSMENT

1. Prompt engineering standards
   [ ] No standards — individuals write prompts ad hoc (L1)
   [ ] Informal guidance — some teams follow best practices (L2)
   [ ] Formal standards — enforced across teams (L3)
   [ ] Standards with quality measurement (L4)
   [ ] Standards that evolve based on measured outcomes (L5)

2. Prompt version control
   [ ] No version control — prompts changed without tracking (L1)
   [ ] Some version tracking in individual projects (L2)
   [ ] All production prompts version-controlled (L3)
   [ ] Version control integrated with deployment pipeline (L4)
   [ ] Automated regression testing on prompt changes (L5)

3. AI architecture decisions
   [ ] Made ad hoc by individuals (L1)
   [ ] Made by team leads without cross-team input (L2)
   [ ] Architecture review process with documented decisions (L3)
   [ ] Decisions measured against outcomes (L4)
   [ ] Architecture proactively evolves based on learning (L5)

4. Production deployment
   [ ] Manual — engineers deploy directly (L1)
   [ ] Semi-automated — some CI/CD (L2)
   [ ] Fully automated with quality gates (L3)
   [ ] Automated with monitoring and rollback (L4)
   [ ] Zero-touch deployment with self-healing (L5)

Domain score: ___ / 5
```

---

## Capability Domain 4: Evaluation and Quality

### 4.1 Domain Description

Evaluation and Quality assesses whether the organisation has systematic methods for knowing whether its AI systems are working — before, during, and after deployment.

### 4.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | No systematic evaluation. Quality judged by "it looks good" subjectively. No monitoring in production. | No evaluation dataset; no automated testing; no production monitoring |
| **2** | Basic quality checks exist for some features. Ad hoc user testing. Manual monitoring. | Some manual testing; user complaints as primary signal; no automated eval |
| **3** | Evaluation datasets defined. Automated quality scoring in production. LLM-as-judge implemented. | Evaluation datasets; automated sampling; quality dashboards |
| **4** | Quality baselines established. Drift detected systematically. Evaluation informs development priorities. | Quality baselines; drift monitoring; evaluation findings in backlog |
| **5** | Continuous evaluation drives continuous improvement. Quality improves automatically through learning loops. | Learning loops from eval to prompt/architecture improvement; quality compounds |

### 4.3 Assessment Questions

```
EVALUATION AND QUALITY ASSESSMENT

1. Evaluation datasets
   [ ] None exist (L1)
   [ ] Exist for some features informally (L2)
   [ ] Defined, versioned, and used consistently (L3)
   [ ] Refresh cadence defined; correlated with production quality (L4)
   [ ] Automatically updated from production failures (L5)

2. Automated quality monitoring
   [ ] None — quality checked manually or via user complaints (L1)
   [ ] Some automated checks for format/schema (L2)
   [ ] LLM-as-judge sampling in production (L3)
   [ ] Drift detection with quality baseline monitoring (L4)
   [ ] Automated quality improvement actions triggered by monitoring (L5)

3. Safety and alignment evaluation
   [ ] No red teaming or adversarial testing (L1)
   [ ] Informal safety checks (L2)
   [ ] Red team exercises before launches (L3)
   [ ] Continuous safety monitoring + quarterly red team (L4)
   [ ] Automated adversarial testing in CI/CD pipeline (L5)

4. Evaluation-to-improvement feedback loop
   [ ] No loop — evaluation findings are noted but not acted on (L1)
   [ ] Occasional improvements from findings (L2)
   [ ] Evaluation findings systematically enter product backlog (L3)
   [ ] Findings prioritised by impact; improvement velocity tracked (L4)
   [ ] Automated learning loops — evaluation triggers prompt/architecture improvements (L5)

Domain score: ___ / 5
```

---

## Capability Domain 5: Governance and Ethics

### 5.1 Domain Description

Governance and Ethics assesses whether the organisation has the policies, processes, and accountability structures required to deploy AI responsibly — for users, regulators, and society.

### 5.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | No AI governance framework. No documented policies. Ethical considerations are informal. | No AI policy; no accountability structure; no risk process |
| **2** | Basic policies exist but are not consistently enforced. Governance is reactive — triggered by incidents. | Some policies; no enforcement mechanism; governance after-the-fact |
| **3** | Documented AI governance framework. Risk assessment process for new features. Clear accountability for AI decisions. | Governance framework; pre-launch risk assessment; named accountability |
| **4** | Governance is measured and audited. Compliance is demonstrable. Ethics considerations are embedded in the development process. | Audit trail; demonstrable compliance; ethics review in design phase |
| **5** | Governance proactively adapts to regulatory evolution and emerging ethical considerations. Organisation contributes to industry standards. | Proactive regulatory monitoring; industry participation; governance evolves ahead of requirements |

### 5.3 Assessment Questions

```
GOVERNANCE AND ETHICS ASSESSMENT

1. AI governance framework
   [ ] No documented framework (L1)
   [ ] Informal guidelines (L2)
   [ ] Documented framework with enforcement mechanism (L3)
   [ ] Framework with audit trail and compliance measurement (L4)
   [ ] Framework proactively updated ahead of regulation (L5)

2. Pre-launch risk assessment
   [ ] No formal risk review before AI features launch (L1)
   [ ] Informal checklist in some teams (L2)
   [ ] Mandatory risk assessment for all AI features (L3)
   [ ] Risk assessment with quantified scoring and escalation (L4)
   [ ] Risk assessment integrated into CI/CD — automated checks (L5)

3. Data privacy and security
   [ ] No AI-specific privacy controls (L1)
   [ ] Basic controls — inconsistently applied (L2)
   [ ] Consistent privacy controls with DPAs in place (L3)
   [ ] Privacy controls audited and certified (L4)
   [ ] Proactive privacy engineering — privacy by design (L5)

4. Bias and fairness
   [ ] No bias testing (L1)
   [ ] Informal awareness (L2)
   [ ] Systematic bias testing before launch (L3)
   [ ] Continuous bias monitoring in production (L4)
   [ ] Automated fairness improvement (L5)

Domain score: ___ / 5
```

---

## Capability Domain 6: Organisation and Talent

### 6.1 Domain Description

Organisation and Talent assesses whether the organisation has the people, roles, structures, and learning systems needed to build and sustain AI capability.

### 6.2 Maturity Level Descriptors

| Level | Descriptor | Key Indicators |
|---|---|---|
| **1** | AI capability concentrated in one or two individuals. No AI roles defined. Teams learn AI informally. | Key-person dependency; no AI PM or ML roles; ad hoc learning |
| **2** | Small AI team formed. Some AI-specific roles defined. Training is ad hoc. | Small dedicated team; roles defined but not filled; some training |
| **3** | AI capability distributed across product, engineering, and design. Clear AI career paths. Structured training programs. | AI literacy across functions; career paths; training cadence |
| **4** | AI literacy is measured across the organisation. Talent gaps are identified and closed systematically. | AI literacy assessments; gap analysis; systematic hiring and training plan |
| **5** | Organisation is a learning system for AI capability. Knowledge transfers systematically. External reputation attracts talent. | Learning loops; knowledge management; employer brand in AI |

### 6.3 Assessment Questions

```
ORGANISATION AND TALENT ASSESSMENT

1. AI role definition and filling
   [ ] No AI-specific roles (L1)
   [ ] Some roles defined but not consistently filled (L2)
   [ ] Clear AI roles defined and filled across key functions (L3)
   [ ] Roles with career progression paths and performance metrics (L4)
   [ ] Roles evolve dynamically as AI capability needs change (L5)

2. AI literacy across the organisation
   [ ] Limited to a small technical team (L1)
   [ ] Growing but concentrated in engineering (L2)
   [ ] Distributed across PM, design, engineering, and leadership (L3)
   [ ] Measured with literacy assessments; gaps tracked (L4)
   [ ] Continuous literacy improvement with learning loops (L5)

3. AI training and development
   [ ] No structured training (L1)
   [ ] Ad hoc training (L2)
   [ ] Structured program with defined curriculum (L3)
   [ ] Training outcomes measured; gaps addressed (L4)
   [ ] Learning is embedded in daily work — continuous and self-sustaining (L5)

4. Knowledge management for AI
   [ ] AI learnings siloed in individuals (L1)
   [ ] Some documentation in team wikis (L2)
   [ ] Centralised knowledge base with consistent tagging (L3)
   [ ] Knowledge actively routed to decision-makers when relevant (L4)
   [ ] Knowledge base self-organises and surfaces proactively (L5)

Domain score: ___ / 5
```

---

## Running a Maturity Assessment

### Assessment Process

```
MATURITY ASSESSMENT PROCESS — 2 WEEKS

Week 1 — Data collection

Day 1–2: Document review
Collect and review: AI strategy documents, governance policies, evaluation frameworks,
architecture diagrams, job descriptions, training materials.

Day 3–4: Stakeholder interviews (45–60 minutes each)
Interview: CPO, CTO, AI lead, PM representative, engineering lead, legal/compliance representative
Questions: For each domain, describe your current practice. What's working? What's missing?

Day 5: Team survey
Send the self-assessment questionnaire to all product, engineering, and AI team members.
Use for triangulation — where leadership perception differs from team reality.

Week 2 — Analysis and reporting

Day 6–7: Score each domain
Apply the assessment questions to the evidence gathered.
Resolve discrepancies between interview responses and documentation.

Day 8–9: Gap and priority analysis
Identify the highest-priority gaps — lowest maturity domains with highest strategic impact.
Design the advancement roadmap.

Day 10: Report preparation and executive presentation
Deliver the maturity scorecard and roadmap to leadership.
```

### Maturity Scorecard

```
MATURITY SCORECARD — [Organisation Name] — [Date]

| Domain | Current Level | Target Level (12 months) | Gap | Priority |
|--------|--------------|-------------------------|-----|----------|
| Strategy and Vision | ___ / 5 | ___ / 5 | ___ | H/M/L |
| Data and Infrastructure | ___ / 5 | ___ / 5 | ___ | H/M/L |
| AI Development and Deployment | ___ / 5 | ___ / 5 | ___ | H/M/L |
| Evaluation and Quality | ___ / 5 | ___ / 5 | ___ | H/M/L |
| Governance and Ethics | ___ / 5 | ___ / 5 | ___ | H/M/L |
| Organisation and Talent | ___ / 5 | ___ / 5 | ___ | H/M/L |

Overall maturity score: ___ / 5 (average across domains)

Strongest domain: _______________________________________________
Weakest domain (highest priority gap): _______________________________________________
Most urgent risk: _______________________________________________
```

---

## Maturity Advancement Roadmap

### Advancement Principles

```
ADVANCEMENT PRINCIPLES

1. Sequential within domains
   You cannot skip levels. Organisations at Level 1 must build Level 2 capabilities
   before Level 3 practices will stick. Skipping creates fragile capability.

2. Bottleneck focus
   The weakest domain caps overall effectiveness. A Level 5 development capability
   with a Level 1 governance capability is a liability.

3. Realistic timelines
   Moving one level in a domain typically requires 3–6 months.
   Moving two levels in 12 months is achievable. Three levels requires exceptional focus.

4. Quick wins first
   Within each domain, identify the Level 2→3 transitions.
   These are typically process improvements — faster and cheaper than infrastructure.

5. Measurement is the gateway to Level 4
   The gap between Level 3 and Level 4 is always measurement.
   Before investing in optimisation (Level 5), invest in knowing what to optimise (Level 4).
```

### 12-Month Advancement Plan Template

```
AI CAPABILITY ADVANCEMENT PLAN — [Organisation] — 12 MONTHS

Quarter 1 priorities:
Domain: _______________________________________________
Current level: ___  |  Target: ___
Key actions:
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________
Success criteria: _______________________________________________

Quarter 2 priorities:
[Same structure]

Quarter 3 priorities:
[Same structure]

Quarter 4 priorities:
[Same structure]

Resource requirements:
Headcount: _______________________________________________
Technology investment: $_______________________________________________
Training investment: $_______________________________________________
External support: _______________________________________________

Expected maturity score at 12 months: ___ / 5
```

---

## Templates

### Template A: Assessment Interview Guide

```
# AI Maturity Assessment Interview
Date: ___  |  Interviewee: ___  |  Role: ___

Opening:
"I'm going to ask about your organisation's AI practices across six areas.
For each, describe what currently happens — not what should happen or what you're planning.
Be as specific as possible."

Domain 1 — Strategy:
"How are AI investments decided? Who is involved? How do you know if they're working?"

Domain 2 — Data:
"If an AI team needs data for a new project, what happens? How long does it take?"

Domain 3 — Development:
"Walk me through how a new AI feature goes from idea to production. Who is involved at each step?"

Domain 4 — Evaluation:
"How do you know if an AI feature is working well? What happens when it's not?"

Domain 5 — Governance:
"Before an AI feature launches, what reviews or approvals are required? Who is accountable if something goes wrong?"

Domain 6 — Organisation:
"Who on the team can build and maintain an AI feature end-to-end? What would happen if that person left?"
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Assessing only technical capability | All six domains must be assessed — governance and organisation are equally critical |
| Self-assessment without evidence review | Triangulate with document review and stakeholder interviews |
| Targeting Level 5 across all domains immediately | Focus on the bottleneck domain; advance sequentially |
| Skipping Level 2→3 transitions to appear more advanced | Each level builds the foundation for the next |
| Assessment as a one-time exercise | Reassess annually or after major capability investments |
| Reporting the scorecard without an advancement plan | The assessment is only valuable if it produces an action plan |
| Focusing on average score and ignoring the weakest domain | The weakest domain caps effectiveness — fix the floor first |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Full maturity assessment | Annually | CPO / CTO |
| Domain-level progress check | Quarterly | AI lead |
| Advancement plan review | Quarterly | CPO + AI lead |
| Stakeholder interviews | Annually (full) + quarterly (key domains) | AI lead |
| External benchmark comparison | Annually | CPO |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Run a Full AI Maturity Assessment

> **Best for:** Conducting a comprehensive assessment of an organisation's AI capability before planning an AI transformation.

```
You are an AI transformation consultant helping me run a maturity assessment across my organisation.

Guide me through assessing each of the six capability domains:
1. Strategy and Vision
2. Data and Infrastructure
3. AI Development and Deployment
4. Evaluation and Quality
5. Governance and Ethics
6. Organisation and Talent

For each domain:
- Ask me the four assessment questions
- Based on my answers, assign a maturity level (1–5) with a clear rationale
- Identify the specific evidence or gap that determined the score
- Identify the single most important improvement needed to advance one level

After all six domains:
- Produce the maturity scorecard with current vs 12-month target levels
- Identify the bottleneck domain (lowest score with highest strategic impact)
- Identify the most urgent risk (lowest governance or safety score)
- Design the 12-month advancement plan prioritising the two highest-impact domains

My organisation: [describe — size, industry, current AI stage]
Current AI products or features: [describe what you have in production]
Team composition: [PM, engineering, data science headcount]
Known capability concerns: [areas you already suspect are weak]
```

---

### Prompt 2 — Design a Domain Advancement Plan

> **Best for:** After identifying a specific domain gap — designing a concrete, time-bound plan to advance capability.

```
You are an AI capability advisor helping me design an advancement plan for a specific maturity domain.

I will tell you my current maturity level and target level for a domain. Design a detailed quarter-by-quarter advancement plan.

For each quarter:
1. The specific practices to implement (be precise — not "improve data quality" but "implement automated schema validation on all data pipeline outputs")
2. The roles responsible for each practice
3. The technology or tooling required
4. The evidence that proves this level has been achieved
5. The risks that might prevent advancement and how to mitigate them

After the full plan:
- Estimate the resource investment: headcount, tooling cost, training cost
- Identify the quick wins (changes achievable in under 4 weeks with minimal investment)
- Identify the long-lead items (changes that require 3+ months of preparation)
- Write the success criteria for a quarterly progress review

Domain: [which domain]
Current level: [1/2/3/4]
Target level in 12 months: [2/3/4/5]
Organisational context: [team size, existing tooling, budget range]
Biggest constraint: [time / budget / talent / executive support]
```

---

### Prompt 3 — Conduct Stakeholder Assessment Interviews

> **Best for:** Preparing for and running the stakeholder interview component of the maturity assessment.

```
You are an AI strategy consultant helping me prepare for maturity assessment interviews with senior stakeholders.

For each stakeholder role I list, design a tailored interview guide:

For each guide:
1. Opening framing — how to set expectations and create psychological safety for honest answers
2. 6–8 specific questions tailored to this stakeholder's perspective and knowledge
3. Follow-up probes for each question — what to ask if the answer is vague or overly positive
4. Red flags to listen for — specific language or evasions that signal lower maturity than claimed
5. How to triangulate this interview against other data sources (documents, team survey)

After designing all interview guides:
- Design the team survey that runs alongside interviews (for triangulation)
- Write the scoring rubric for converting interview responses to maturity levels
- Identify the most common gap between leadership perception and team reality in AI assessments

Stakeholder roles to interview:
1. [e.g. CPO / Chief Product Officer]
2. [e.g. CTO / VP Engineering]
3. [e.g. AI or ML team lead]
4. [e.g. PM representative]
5. [e.g. Legal or compliance representative]

Organisation context: [describe size, industry, AI stage]
```

---

### Prompt 4 — Benchmark Against Industry Standards

> **Best for:** Contextualising your maturity score against what comparable organisations typically achieve.

```
You are an AI industry analyst helping me benchmark my organisation's AI maturity against relevant peers.

Based on the maturity scores I share, help me understand:

1. Relative positioning
   - For each domain, where does my score sit relative to: early-stage AI adopters / growth-stage companies / AI-native companies?
   - Which domains are above, at, or below typical levels for my industry and stage?

2. Benchmark context
   - What is the typical maturity profile for a company at my stage?
   - What is the most common bottleneck domain for companies like mine?
   - What does a Level 3 organisation typically look like in practice vs Level 4?

3. Advancement expectations
   - What is a realistic advancement expectation for each domain over 12 months?
   - What are the most common obstacles companies at my stage face?

4. Risk identification
   - Based on my profile, what are the two highest-risk gaps?
   - What specific failure modes are associated with these gaps?

5. Investment priority
   - Given my profile, where should I invest first?
   - What is the highest-ROI capability investment for a company with my maturity profile?

My maturity scores:
Strategy: ___ / 5
Data and Infrastructure: ___ / 5
AI Development: ___ / 5
Evaluation and Quality: ___ / 5
Governance and Ethics: ___ / 5
Organisation and Talent: ___ / 5

My organisation: [industry, size, stage, current AI products]
```

---

### Prompt 5 — Present Maturity Assessment to Leadership

> **Best for:** Translating the technical maturity scorecard into an executive presentation that produces investment and priority decisions.

```
You are a strategy consultant helping me present an AI maturity assessment to executive leadership.

Using my maturity scores and assessment findings, write the executive presentation narrative:

1. Executive summary (3 slides worth of content)
   - Where we are: our overall AI maturity score and what it means
   - Where we need to be: the target state for our strategy to succeed
   - What it will take: the top 3 investment priorities

2. The business case for advancement
   - For each priority domain: what is the cost of staying at the current level?
   - What specific business outcomes are blocked by the current capability gap?
   - What is the expected ROI of advancing to the target level?

3. The risk narrative
   - What is the most significant risk created by our current maturity profile?
   - What could go wrong in the next 12 months if we don't address it?

4. The advancement plan
   - Quarter by quarter: what changes, what gets built, what gets measured
   - Resource ask: headcount, technology, training, external support

5. The success metrics
   - How will leadership know the investment is working?
   - What maturity indicators should appear on the quarterly board report?

My maturity scores and key findings:
[paste your scorecard and key assessment findings]

My audience: [describe the executive team and their primary concerns]
Planned investment level: $[range]
Timeline for transformation: [months/years]
```

