# 🏛️ Product Governance — AI Product Builder Playbook

> **A framework for designing the oversight structures, accountability mechanisms, and review processes that keep AI products safe, aligned, and continuously improving**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Governance Model](#the-governance-model)
- [Governance Layer 1: Policy and Standards](#governance-layer-1-policy-and-standards)
- [Governance Layer 2: Review and Approval](#governance-layer-2-review-and-approval)
- [Governance Layer 3: Monitoring and Accountability](#governance-layer-3-monitoring-and-accountability)
- [Governance Layer 4: Learning and Adaptation](#governance-layer-4-learning-and-adaptation)
- [AI-Specific Governance](#ai-specific-governance)
- [Governance for Different Organisation Sizes](#governance-for-different-organisation-sizes)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Governance is the least glamorous and most underinvested part of building AI products. It is also the part most likely to determine whether an AI product survives long enough to matter. The teams that skip governance because they are moving fast discover — usually through an incident — that ungoverned AI systems create liabilities that no amount of speed can outrun.

> **Core Principle:** Governance is not bureaucracy. Bureaucracy is process for its own sake — it slows things down without making them better. Governance is accountability infrastructure — the structures that ensure someone is responsible for each decision, each risk, and each outcome. Good governance makes teams faster by reducing the chaos that comes from ungoverned systems.

For AI products specifically, governance must address challenges that traditional software governance does not: probabilistic outputs that can fail in ways not anticipated at design time, data practices that affect user privacy in novel ways, and algorithmic behaviour that can create or perpetuate bias without any individual intending it.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Launching AI products in regulated industries | 🔴 Critical — governance is a legal requirement |
| Scaling AI features to large user populations | 🔴 Critical — ungoverned AI at scale is high risk |
| An AI incident has occurred with unclear accountability | 🔴 Critical — governance gap is the root cause |
| Enterprise customers require AI governance documentation | 🟠 High |
| Preparing for AI regulatory compliance (EU AI Act, etc.) | 🟠 High |
| Building the AI team's operating model | 🟡 Medium |
| Annual governance review | 🟡 Medium |

---

## The Governance Model

AI product governance operates across four layers, from policy through learning. Each layer requires the layers below it to function — monitoring without policy is measurement without standards; policy without review is aspiration without enforcement.

```
POLICY AND STANDARDS
  ↓ the rules that define acceptable AI behaviour
REVIEW AND APPROVAL
  ↓ the checkpoints that enforce standards before deployment
MONITORING AND ACCOUNTABILITY
  ↓ the ongoing oversight that catches what reviews miss
LEARNING AND ADAPTATION
  ↓ the mechanisms that improve governance over time
```

| Layer | What It Does | Without It |
|---|---|---|
| **Policy** | Defines what is acceptable | Teams make inconsistent decisions |
| **Review** | Enforces policy pre-deployment | Policy is aspirational, not operational |
| **Monitoring** | Catches what reviews miss in production | Problems discovered by users, not teams |
| **Learning** | Improves governance from experience | Same mistakes are made repeatedly |

---

## Governance Layer 1: Policy and Standards

### 1.1 Core AI Policy Areas

```
AI POLICY FRAMEWORK — REQUIRED POLICY AREAS

1. AI Use Policy
   Defines: what AI can and cannot be used for within the organisation.
   Covers: approved use cases, prohibited applications, third-party AI tools.
   Owner: CPO + Legal

2. AI Data Policy
   Defines: how user data may be used in AI systems.
   Covers: data minimisation, retention limits, training data consent, third-party sharing.
   Owner: Legal + Privacy officer

3. AI Quality Policy
   Defines: the minimum quality standards for AI features before production.
   Covers: evaluation requirements, quality thresholds, monitoring requirements.
   Owner: CPO + AI lead

4. AI Safety Policy
   Defines: the safety requirements for AI features.
   Covers: prohibited content, guardrail requirements, human-in-the-loop triggers.
   Owner: CPO + Legal

5. AI Transparency Policy
   Defines: disclosure requirements for AI-generated content and decisions.
   Covers: user disclosure, labelling, limitation communication.
   Owner: CPO + Legal

6. AI Incident Policy
   Defines: how AI incidents are classified, escalated, and remediated.
   Covers: severity levels, response procedures, communication requirements.
   Owner: CPO + Engineering lead
```

### 1.2 Standards Library

```
AI STANDARDS LIBRARY

Evaluation standards:
  Minimum evaluation dataset size: ___ examples
  Minimum quality score threshold: ___ / 5
  Required safety pass rate: ___%
  Human review sample: ___% of outputs

Deployment standards:
  Required pre-launch checklist completion: 100%
  Required sign-offs before launch: [list]
  Rollout approach: internal → beta → gradual → full
  Monitoring activation: required before any user exposure

Data standards:
  Maximum data retention for AI inputs: ___ days
  PII handling: strip before model call
  DPA requirement: mandatory for all third-party model providers
  User deletion: complete within ___ business days of request

Prompt standards:
  Version control: mandatory for all production prompts
  Regression testing: required before any prompt change deployment
  Change log: mandatory — includes rationale for every change
  Sign-off: PM approval required for system prompt changes
```

---

## Governance Layer 2: Review and Approval

### 2.1 AI Feature Review Gates

Every AI feature must pass through defined review gates before reaching users. Gates are not optional checkboxes — they are launch blockers when not passed.

```
AI FEATURE REVIEW GATES

Gate 1 — Problem and Design Review (before engineering begins)
  Reviewers: PM + Design + AI lead
  Checklist:
  [ ] Validated user problem with evidence
  [ ] AI approach justified (not just "we can use AI here")
  [ ] AI PRD complete — all sections filled, no "TBD" in critical fields
  [ ] Risk assessment completed — no unmitigated critical risks
  [ ] Privacy review completed
  Output: Approved to build / Revise and resubmit

Gate 2 — Technical Review (before engineering starts)
  Reviewers: Engineering lead + AI lead + PM
  Checklist:
  [ ] AI architecture validated
  [ ] Data dependencies confirmed (data exists and is accessible)
  [ ] Model evaluation plan designed
  [ ] Cost model validated against budget
  [ ] Monitoring design confirmed
  Output: Approved to build / Architecture change required

Gate 3 — Quality and Safety Review (before any user exposure)
  Reviewers: PM + AI lead + Legal (if regulated domain)
  Checklist:
  [ ] Evaluation dataset pass rate ≥ threshold
  [ ] Safety evaluation pass rate ≥ threshold
  [ ] All failure modes have designed responses
  [ ] Monitoring dashboard live
  [ ] Privacy checklist complete
  Output: Approved for soft launch / Not approved — specific gaps listed

Gate 4 — Full Launch Review (before 100% rollout)
  Reviewers: PM + CPO
  Checklist:
  [ ] Soft launch quality metrics meet target
  [ ] No P1/P2 incidents in soft launch period
  [ ] User feedback sentiment positive
  [ ] Cost per interaction within budget model
  Output: Approved for full launch / Hold at current rollout %
```

### 2.2 Review Cadence Calendar

```
GOVERNANCE REVIEW CALENDAR

Weekly:
  AI quality monitoring review (PM + AI lead)
  Content: Quality scores, filter trigger rates, cost per interaction

Monthly:
  Product governance review (PM + CPO + Legal)
  Content: Policy compliance, open risks, incident review, upcoming launches

Quarterly:
  AI governance committee (CPO + CTO + Legal + Board rep if applicable)
  Content: Strategic AI risks, regulatory updates, governance framework effectiveness

Annually:
  Full governance framework review
  Content: Policy refresh, standards update, regulatory alignment
```

---

## Governance Layer 3: Monitoring and Accountability

### 3.1 Accountability Register

```
AI ACCOUNTABILITY REGISTER

For every production AI feature, document:

| Feature | Quality owner | Safety owner | Privacy owner | Incident owner |
|---------|--------------|--------------|---------------|----------------|
| [Feature A] | PM name | PM + Legal | Legal + DPO | PM + Eng lead |
| [Feature B] | | | | |

Rules:
  Every accountability role has exactly ONE named person — not a team
  Named accountability must be updated within 5 business days of role change
  Accountability register is reviewed quarterly
```

### 3.2 Governance Dashboard

```
GOVERNANCE DASHBOARD — KEY INDICATORS

Policy compliance:
  [ ] Features without completed risk assessment: ___
  [ ] Features without DPA for model providers: ___
  [ ] Open compliance issues: ___

Quality governance:
  [ ] Features with quality score below threshold: ___
  [ ] Features with no active monitoring: ___
  [ ] Open quality incidents: ___

Safety governance:
  [ ] Content filter trigger rate (fleet average): ___%
  [ ] Safety incidents in last 30 days: ___
  [ ] Features without completed safety evaluation: ___

Privacy governance:
  [ ] User deletion requests outstanding > 30 days: ___
  [ ] Data retention violations: ___
  [ ] Third-party data sharing without DPA: ___

Accountability:
  [ ] Features without named quality/safety owner: ___
  [ ] Open incident post-mortems overdue: ___
```

### 3.3 Incident Governance Protocol

```
INCIDENT GOVERNANCE PROTOCOL

Severity classification:
  P0 — Existential: Data breach, widespread harmful output, regulatory breach
       → CEO + CPO + Legal + Board notified within 1 hour
  P1 — Critical: Significant user harm, safety failure, privacy violation
       → CPO + Legal notified within 2 hours
  P2 — Serious: Quality degradation affecting many users, cost overrun > 200%
       → PM + CPO notified within 4 hours
  P3 — Minor: Quality below threshold for a small subset, transient issue
       → PM tracks and resolves

Post-incident requirements by severity:
  P0: External communication + regulatory notification (if required) + board report
  P1: Post-mortem within 48 hours + policy review + CPO sign-off on remediation
  P2: Post-mortem within 72 hours + policy update if systemic
  P3: Root cause noted in monitoring log + fix within sprint
```

---

## Governance Layer 4: Learning and Adaptation

### 4.1 Governance Effectiveness Review

```
QUARTERLY GOVERNANCE EFFECTIVENESS REVIEW

Questions to answer:

Are the policies being followed?
  % of launches that passed all gates without exception: ___%
  Number of gate exceptions requested and granted: ___
  Most common reason for gate exception: _______________________________________________

Are the standards set correctly?
  Quality threshold: producing good outcomes? Too strict (many exceptions)? Too loose (quality issues)?
  Safety threshold: catching real issues? Generating too many false positives?

Are reviews adding value?
  Average review meeting duration: ___
  Average number of significant findings per review: ___
  Reviews that produced no actionable findings: ___% (if > 50%, reviews are too light)

Are incidents informing policy?
  Last quarter's incidents: ___
  Incidents caused by policy gaps: ___
  Policy changes made in response to incidents: ___

What needs to change?
  Policies that are unclear, outdated, or consistently misapplied: _______________________________________________
  Standards that are too high or too low given experience: _______________________________________________
  Review process that is creating friction without commensurate safety value: _______________________________________________
```

### 4.2 Regulatory Monitoring

```
AI REGULATORY MONITORING

Key regulations to monitor:
  EU AI Act — Implementation timeline and compliance requirements
  GDPR / CCPA — AI-specific interpretations and enforcement actions
  Sector-specific regulations — [list applicable regulations for your industry]

Monitoring approach:
  Legal counsel briefing: Quarterly
  Regulatory update digest: Monthly (internal circulation)
  Proactive compliance review: 6 months before any major regulatory deadline

Current regulatory status:
  Compliance requirements we are meeting: _______________________________________________
  Gaps requiring action: _______________________________________________
  Timeline for gap resolution: _______________________________________________
```

---

## AI-Specific Governance

### 5.1 AI Risk Register

```
ORGANISATIONAL AI RISK REGISTER

| Risk ID | Risk description | Category | Likelihood | Impact | Score | Owner | Mitigation | Status |
|---------|-----------------|----------|------------|--------|-------|-------|------------|--------|
| R001 | Hallucination in [feature] | Quality | | | | | | |
| R002 | Bias in [feature] | Fairness | | | | | | |
| R003 | Data privacy — [provider] | Privacy | | | | | | |
| R004 | Model provider outage | Operational | | | | | | |
| R005 | Regulatory change — [reg] | Compliance | | | | | | |

Review frequency: Monthly
Escalation: Any risk scoring > 15 escalates to CPO within 1 week
```

### 5.2 AI Ethics Committee

For organisations with significant AI exposure, an ethics committee provides independent oversight:

```
AI ETHICS COMMITTEE

Composition:
  [ ] CPO (chair)
  [ ] Legal / Compliance
  [ ] Senior PM representative
  [ ] External ethics advisor (independent)
  [ ] User advocate / community representative (if applicable)

Meeting frequency: Quarterly

Mandate:
  Review high-risk AI features before launch
  Review AI incidents post-resolution
  Monitor responsible AI principle compliance
  Advise on emerging ethical issues
  Recommend policy updates

Escalation trigger to committee:
  Any feature categorised as High or Critical risk
  Any P0 or P1 incident
  Any novel AI use case without precedent in current policy
  Any significant regulatory development
```

---

## Governance for Different Organisation Sizes

### 6.1 Governance by Scale

```
GOVERNANCE AT DIFFERENT SCALES

Startup (< 20 people):
  Minimum viable governance:
  [ ] AI Use Policy (1 page)
  [ ] Pre-launch checklist (PM + Eng lead review)
  [ ] Risk register (PM-maintained)
  [ ] Incident response protocol
  Who owns it: PM (all governance owned by the PM)

Growth stage (20–200 people):
  Standard governance:
  [ ] Full policy library
  [ ] Formal review gates (3-gate model)
  [ ] Monthly governance review
  [ ] AI accountability register
  [ ] Quarterly compliance review
  Who owns it: PM + Legal + CPO

Scale (200+ people):
  Mature governance:
  [ ] Full policy library with versioning
  [ ] AI Ethics Committee
  [ ] Automated governance monitoring
  [ ] External audit capability
  [ ] Regulatory compliance programme
  Who owns it: Dedicated governance function + CPO accountability
```

---

## Templates

### Template A: Governance Charter

```
# AI Product Governance Charter
Organisation: _______________________________________________
Effective date: ___  |  Review date: ___  |  Owner: ___

## Purpose
[1 paragraph: why this governance framework exists and what it protects]

## Scope
This governance framework applies to: _______________________________________________

## Core Principles
[Reference to responsible AI principles]

## Policy Summary
[List each policy with owner and review date]

## Review Gates
[Summarise the gate structure with trigger and approvers]

## Accountability Structure
[Reference to accountability register]

## Incident Protocol
[Reference to incident governance protocol]

## Governance Review Cadence
[Reference to review calendar]

## Amendment Process
[How this charter is updated and who must approve changes]

## Sign-off
[ ] CPO  [ ] Legal  [ ] CTO  [ ] Board (if applicable)
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Governance as a post-launch activity | Gates must be passed before any user exposure |
| Policy documents nobody reads | Governance embedded in launch checklists and review processes |
| Governance owned by Legal alone | PM owns product governance; Legal advises on compliance |
| Review gates as rubber stamps | Gates must be able to block a launch — or they are not gates |
| No named accountability for AI features | Every feature has named owners in the accountability register |
| Incident response designed during an incident | Incident protocols written before any launch |
| Governance that never adapts | Quarterly review + post-incident policy updates |
| Governance only for regulated industries | All AI products with real users require baseline governance |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Gate reviews | Per feature, pre-launch | PM |
| AI quality monitoring | Weekly | PM + AI lead |
| Governance review | Monthly | PM + CPO + Legal |
| Risk register review | Monthly | PM |
| Ethics committee meeting | Quarterly | CPO |
| Regulatory monitoring | Quarterly | Legal |
| Full governance framework review | Annually | CPO + Legal |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Product Governance Framework

> **Best for:** Building the governance framework for an AI product from scratch — policies, gates, monitoring, and accountability.

```
You are an AI governance specialist helping me design a product governance framework.

Design the complete framework across all four layers:

1. Policy and standards
   - What policies are required for my product and regulatory context?
   - Write the key policy statements for each required area
   - What standards should govern evaluation, deployment, data, and prompts?

2. Review and approval gates
   - What gates are required before an AI feature reaches users?
   - For each gate: what is reviewed, by whom, with what checklist?
   - What constitutes a gate failure (launch blocker)?

3. Monitoring and accountability
   - Design the accountability register for my AI features
   - Design the governance dashboard with key indicators
   - Design the incident protocol with severity classification

4. Learning and adaptation
   - How does governance improve based on incidents and experience?
   - What regulatory monitoring is required for my context?
   - How often is the framework reviewed and by whom?

After all four layers:
- Scale to my organisation size (startup / growth / scale)
- Identify the minimum viable governance for immediate implementation
- Write the governance charter

My organisation: [size and structure]
AI products in scope: [describe]
Industry: [any regulated industries]
Regulatory context: [key regulations that apply]
Current governance state: [what governance exists today, if any]
```

---

### Prompt 2 — Design AI Feature Review Gates

> **Best for:** Creating the specific review checkpoints that ensure AI features meet quality, safety, and privacy standards before launch.

```
You are a product governance designer helping me create AI feature review gates.

Design a four-gate review process:

Gate 1 — Problem and Design Review (before engineering)
   - What is reviewed at this gate?
   - Who are the reviewers?
   - Write the complete checklist
   - What constitutes a pass vs a failure?

Gate 2 — Technical Review (before engineering starts)
   - What is reviewed at this gate?
   - Who are the reviewers?
   - Write the complete checklist
   - What constitutes a pass vs a failure?

Gate 3 — Quality and Safety Review (before any user exposure)
   - What is reviewed at this gate?
   - Who are the reviewers?
   - Write the complete checklist
   - What constitutes a pass vs a failure?

Gate 4 — Full Launch Review (before 100% rollout)
   - What is reviewed at this gate?
   - Who are the reviewers?
   - Write the complete checklist
   - What constitutes a pass vs a failure?

After all four gates:
- Estimate the time each gate adds to the development cycle
- Identify which gate catches the most significant issues in practice
- Write the exception process (when and how a gate can be bypassed)
- Write the escalation path when a gate failure is disputed

My product type: [describe the AI feature types]
Team structure: [who is on the team]
Industry: [regulated or general]
Current launch process: [describe what reviews happen today]
```

---

### Prompt 3 — Write an AI Governance Policy

> **Best for:** Drafting a specific AI governance policy — for data, quality, safety, transparency, or incidents.

```
You are an AI policy writer helping me draft a governance policy for my organisation.

Write a complete, operational policy document that:
- Is specific to my context — not a generic template
- Is written for practitioners — actionable, not aspirational
- Specifies what must be done at each stage — not just what is encouraged
- Has clear ownership and enforcement mechanisms

Policy structure:
1. Purpose (1 paragraph — what this policy protects and why)
2. Scope (who and what this policy applies to)
3. Core requirements (the specific obligations — written as "must" statements)
4. Roles and responsibilities (who owns what)
5. Compliance and exceptions (how compliance is verified; how exceptions are granted)
6. Review and updates (when and how this policy changes)

After writing the policy:
- Identify the 2–3 requirements most likely to be violated without enforcement
- Write the enforcement mechanism for those requirements
- Write the employee-facing summary (1 page, plain language)

Policy area: [AI Data Policy / AI Quality Policy / AI Safety Policy / AI Transparency Policy / AI Incident Policy]
My organisation: [describe]
Industry: [any regulated industries]
Regulatory requirements: [key regulations that apply]
Current practices to codify: [what do you already do that this policy should reflect?]
```

---

### Prompt 4 — Build the AI Accountability Structure

> **Best for:** Defining who is responsible for what across all AI features — preventing the "the algorithm decided" accountability vacuum.

```
You are an organisational accountability expert helping me build the AI accountability structure for my product team.

Design the complete accountability structure:

1. Accountability register design
   - What accountability roles are needed for each AI feature?
   - Write the register format with all required fields
   - How is the register maintained and reviewed?

2. Role definitions
   For each accountability role, define:
   - What they are responsible for
   - What decisions they own
   - What they must be consulted on
   - How they are notified of incidents or issues
   - What the escalation path is when they cannot resolve an issue

3. Accountability gaps
   - Where are the most common accountability gaps in AI products?
   - How do we prevent "the algorithm decided" as an accountability shield?

4. Incident accountability
   - When an AI incident occurs, who is accountable for what?
   - Write the incident accountability matrix

5. Accountability culture
   - How do we build a culture where accountability is exercised rather than avoided?
   - What does healthy accountability look like vs blame culture?

My team: [structure and roles]
AI features in scope: [describe]
Current accountability gaps: [where is accountability unclear today?]
Incident history: [any past incidents where accountability was unclear]
```

---

### Prompt 5 — Prepare for AI Regulatory Compliance

> **Best for:** Assessing compliance with AI regulations and building the roadmap to close compliance gaps.

```
You are an AI regulatory compliance advisor helping me assess and plan for AI regulatory compliance.

Guide me through a compliance assessment and planning process:

1. Regulatory landscape
   - What AI regulations apply to my organisation given my industry and geography?
   - What are the key requirements of each regulation?
   - What are the enforcement timelines?

2. Current state assessment
   - For each regulation: what are my current compliance gaps?
   - Rate each gap: Critical (blocks operation) / Significant (near-term risk) / Minor (long-term)

3. Compliance roadmap
   - Prioritise gaps by: regulatory timeline + business risk + implementation effort
   - For each gap: what specific action closes it, by when, owned by whom?

4. Documentation requirements
   - What documentation must I maintain to demonstrate compliance?
   - What audit capabilities must I build?

5. Ongoing compliance
   - How do I stay informed of regulatory changes?
   - What governance structures ensure ongoing compliance?
   - When should I engage external legal counsel?

My organisation: [describe]
Industry: [what sector]
Geography of users: [EU / US / global — key jurisdictions]
Current AI products: [describe what AI features are deployed]
Known compliance concerns: [anything you already know is an issue]
```
