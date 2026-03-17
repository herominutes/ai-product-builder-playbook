# 🏗️ System Architecture Template — AI Product Builder Playbook

> **A template for documenting AI system architecture in a way that enables confident engineering decisions, reliable operations, and clear communication across technical and non-technical stakeholders**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Template](#when-to-use-this-template)
- [Architecture Documentation Principles](#architecture-documentation-principles)
- [Section 1: System Overview](#section-1-system-overview)
- [Section 2: Component Architecture](#section-2-component-architecture)
- [Section 3: Data Architecture](#section-3-data-architecture)
- [Section 4: AI-Specific Architecture](#section-4-ai-specific-architecture)
- [Section 5: Integration Architecture](#section-5-integration-architecture)
- [Section 6: Reliability and Operations](#section-6-reliability-and-operations)
- [Section 7: Security and Compliance](#section-7-security-and-compliance)
- [Full Architecture Document Template](#full-architecture-document-template)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

AI system architecture documentation serves a different purpose than traditional software architecture docs. In addition to the standard concerns — components, data flows, integrations, and reliability — AI systems require explicit documentation of the model layer, the retrieval infrastructure, the evaluation pipeline, the prompt management system, and the feedback loops that keep the system improving over time.

> **Core Principle:** An undocumented AI architecture is a liability, not just a knowledge gap. When the AI behaves unexpectedly, when costs spike, when quality degrades, or when the system needs to scale — the team that documented its architecture will respond in hours. The team that didn't will spend days reconstructing what they built before they can diagnose the problem.

---

## When to Use This Template

| Trigger | Priority |
|---|---|
| Starting to build an AI feature or system | 🔴 Critical — document before building, not after |
| Handing an AI system from one team to another | 🔴 Critical — undocumented handoffs cause production failures |
| Debugging an AI system failure in production | 🟠 High — architecture doc enables faster diagnosis |
| Scaling an AI system to higher load or new regions | 🟠 High — scaling without documentation creates fragile systems |
| Security or compliance review of an AI system | 🟠 High — architecture doc is the basis of any review |
| Onboarding a new engineer to an AI system | 🟡 Medium — architecture doc reduces ramp time |

---

## Architecture Documentation Principles

### What Makes Good AI Architecture Documentation

| Principle | Description | Anti-Pattern |
|---|---|---|
| **Current** | Reflects the actual system, not the intended system | Doc written during design, never updated |
| **Layered** | Different levels of detail for different audiences | One 60-page doc nobody reads |
| **Decision-linked** | Architecture choices link to decision log entries | Unexplained choices with no rationale |
| **Failure-inclusive** | Documents failure modes and recovery paths | Only shows the happy path |
| **AI-specific** | Explicitly documents the AI components | AI treated as a black box in the diagram |
| **Observable** | Describes what can be monitored and how | No mention of observability or alerting |

### Audience Layers

```
ARCHITECTURE DOCUMENTATION LAYERS

Layer 1 — Executive summary (1 page)
Audience: Non-technical stakeholders, leadership
Content: What the system does, its components at the highest level, key constraints

Layer 2 — System overview (2–4 pages)
Audience: Product managers, technical leads, new engineers
Content: Component diagram, data flows, key interfaces, AI layer overview

Layer 3 — Component deep-dives (per component)
Audience: Engineers building or operating the system
Content: Implementation details, APIs, configuration, failure modes

Layer 4 — Runbook
Audience: On-call engineers
Content: How to monitor, diagnose, and recover from specific failure scenarios
```

---

## Section 1: System Overview

### 1.1 System Purpose

```
SYSTEM PURPOSE

System name: _______________________________________________
System type: AI-native product / AI-enhanced existing product / AI backend service

What the system does (one paragraph, non-technical):
_______________________________________________

Primary users:
Internal: _______________________________________________
External: _______________________________________________

Core value delivered:
_______________________________________________

Key constraints:
  Latency SLA: _______________________________________________
  Availability SLA: _______________________________________________
  Cost budget: $_______________________________________________
  Data privacy requirements: _______________________________________________
  Regulatory requirements: _______________________________________________
```

### 1.2 High-Level Architecture Diagram

```
HIGH-LEVEL ARCHITECTURE — [System Name]

[Replace with actual diagram. Minimum components to show:]

User / Client
    ↓
API Gateway / Load Balancer
    ↓
Application Layer
    ↓
┌───────────────────────────────────┐
│           AI Layer                │
│  ┌─────────────┐ ┌─────────────┐  │
│  │ Orchestrator│ │ LLM/Model   │  │
│  └─────────────┘ └─────────────┘  │
│  ┌─────────────┐ ┌─────────────┐  │
│  │ Retrieval   │ │ Memory      │  │
│  └─────────────┘ └─────────────┘  │
└───────────────────────────────────┘
    ↓
Data Layer (databases, vector store, cache)
    ↓
External Services (APIs, model providers, integrations)
```

### 1.3 Technology Stack

```
TECHNOLOGY STACK

Frontend: _______________________________________________
Backend: _______________________________________________
Database(s): _______________________________________________
Cache: _______________________________________________
Message queue (if applicable): _______________________________________________
Infrastructure: _______________________________________________

AI-specific:
  Model provider(s): _______________________________________________
  Primary model: _______________________________________________
  Fallback model: _______________________________________________
  Embedding model: _______________________________________________
  Vector store: _______________________________________________
  Orchestration framework: _______________________________________________
  Prompt management: _______________________________________________
  Evaluation framework: _______________________________________________

Third-party services:
  Auth: _______________________________________________
  Monitoring / observability: _______________________________________________
  Logging: _______________________________________________
  Analytics: _______________________________________________
```

---

## Section 2: Component Architecture

### 2.1 Component Inventory

```
COMPONENT INVENTORY

For each major component, document:

Component name: _______________________________________________
Type: Service / Library / Database / Queue / AI component / External service
Owner (team or individual): _______________________________________________
Repository: _______________________________________________
Language / runtime: _______________________________________________
Deployment: _______________________________________________

Interfaces:
  Consumes: [list APIs or data sources this component reads]
  Produces: [list APIs or data outputs this component provides]

Dependencies:
  Hard dependencies (system fails without): _______________________________________________
  Soft dependencies (degrades without): _______________________________________________

SLAs:
  Availability: ___%
  Latency P99: ___ ms
  Error rate: < ___%

Failure mode:
  What happens when this component fails: _______________________________________________
  Fallback behaviour: _______________________________________________
  Recovery time objective (RTO): _______________________________________________
```

### 2.2 Request Flow Diagram

```
REQUEST FLOW — [Primary User Journey]

Step 1: User submits [action]
  → Component: [name]
  → Operation: [what happens]
  → Output: [what is produced]
  → Latency budget: ___ ms

Step 2: [Component] processes request
  → Component: [name]
  → Operation: [what happens]
  → Output: [what is produced]
  → Latency budget: ___ ms

Step 3: AI layer processes
  → Component: AI Orchestrator
  → Operation: [what the orchestrator does]
  → Model call: [which model, what prompt structure]
  → Retrieval: [if RAG — what is retrieved]
  → Output: [model output]
  → Latency budget: ___ ms

Step 4: Response assembled and returned
  → Component: [name]
  → Operation: [post-processing, formatting]
  → Output: [what the user receives]
  → Latency budget: ___ ms

Total latency budget: ___ ms
Critical path: Steps [X, Y, Z] (cannot be parallelised)
Parallelisable steps: Steps [A, B] (run concurrently)
```

---

## Section 3: Data Architecture

### 3.1 Data Flow Map

```
DATA FLOW MAP

Data source: _______________________________________________
  → What data enters the system: _______________________________________________
  → Where it goes first: _______________________________________________
  → Transformations applied: _______________________________________________
  → Where it is stored: _______________________________________________
  → Who / what can access it: _______________________________________________
  → Retention period: _______________________________________________
  → PII present: Yes / No / Possibly

User input data:
  Collected: _______________________________________________
  Sent to model provider: Yes / No — Provider: _______________________________________________
  Stored: Yes / No — Where: ___ — For how long: ___
  PII stripping applied: Yes / No

AI output data:
  Stored: Yes / No — Where: ___ — For how long: ___
  Linked to user: Yes / No
  Used for training: Yes / No — Provider policy: _______________________________________________

Memory / context data (if applicable):
  What is stored in memory: _______________________________________________
  Storage location: _______________________________________________
  User can view/delete: Yes / No
  Retention policy: _______________________________________________
```

### 3.2 Database Schema Overview

```
DATABASE SCHEMA OVERVIEW

[List primary tables/collections with key fields — not every field, just enough to understand the data model]

Table: [name]
  Key fields: _______________________________________________
  Relationships: _______________________________________________
  Volume: ___ rows / ___ GB
  Growth rate: _______________________________________________

Vector Store:
  Index name: _______________________________________________
  Dimensions: _______________________________________________
  Distance metric: _______________________________________________
  Estimated vectors: _______________________________________________
  Metadata schema: _______________________________________________
```

---

## Section 4: AI-Specific Architecture

### 4.1 AI Component Map

This is the section most architecture documents omit. Document the AI layer explicitly:

```
AI COMPONENT MAP

Orchestration layer:
  Framework: _______________________________________________
  Workflow pattern: Sequential / Parallel / Conditional / Loop / Hybrid
  State management: _______________________________________________
  Error handling: _______________________________________________

Prompt management:
  Prompts stored: In code / In database / In prompt management system
  Version control: Yes / No — System: _______________________________________________
  Deployment process: _______________________________________________
  Rollback process: _______________________________________________

Model layer:
  Primary model: _______________________________________________
  Model version: Pinned / Latest — Version: _______________________________________________
  Fallback model: _______________________________________________
  Failover trigger: _______________________________________________
  Context window: ___ tokens
  Temperature: ___  |  Max tokens: ___

Retrieval layer (if RAG):
  Vector store: _______________________________________________
  Embedding model: _______________________________________________
  Chunk size: ___ tokens  |  Overlap: ___%
  Top-K: ___  |  Similarity threshold: ___
  Re-ranking: Yes / No — Model: _______________________________________________
  Query optimisation: _______________________________________________

Memory layer (if applicable):
  Memory types implemented: Working / Episodic / Semantic / Procedural
  Storage: _______________________________________________
  Retrieval: _______________________________________________

Evaluation layer:
  Automated sampling: ___%
  Evaluation method: LLM-as-judge / Human / Automated metrics
  Monitoring dashboard: _______________________________________________
  Quality baseline: ___ / 5

Guardrail layer:
  Input guardrails: _______________________________________________
  Output guardrails: _______________________________________________
  Content filter: _______________________________________________
  Circuit breaker: _______________________________________________
```

### 4.2 AI Cost Architecture

```
AI COST ARCHITECTURE

Cost model:
  Input tokens per interaction: ___ (avg)
  Output tokens per interaction: ___ (avg)
  Cost per interaction: $___
  Retrieval cost per interaction: $___
  Total cost per interaction: $___

Volume:
  Current: ___ interactions/day
  Projected 6 months: ___ interactions/day
  Projected 12 months: ___ interactions/day

Monthly cost model:
  Current: $___/month
  Projected 6 months: $___/month
  Projected 12 months: $___/month

Cost controls:
  Daily budget limit: $___
  Alert threshold: $___/day
  Circuit breaker: Disable at $___/day
  Rate limiting: ___ requests/user/hour

Cost optimisation implemented:
  [ ] Prompt compression (saves ___% of input tokens)
  [ ] Response caching (saves ___% of interactions)
  [ ] Model routing (routes ___% of traffic to cheaper model)
  [ ] Batch processing (for non-real-time tasks)
```

---

## Section 5: Integration Architecture

### 5.1 External Integrations

```
INTEGRATION INVENTORY

Integration: [name]
  Type: REST API / Webhook / SDK / Database / File transfer
  Direction: Inbound / Outbound / Bidirectional
  Purpose: _______________________________________________
  Authentication: _______________________________________________
  Rate limits: _______________________________________________
  SLA from provider: _______________________________________________
  Failure behaviour: _______________________________________________
  Fallback: _______________________________________________
  Data sent: [describe — note any PII or sensitive data]
  Data received: _______________________________________________
  DPA in place: Yes / No / Not applicable
```

### 5.2 API Contract

```
API CONTRACT — [System Name]

Base URL: _______________________________________________
Authentication: _______________________________________________
Rate limits: _______________________________________________

Key endpoints:
  POST /[endpoint]
    Purpose: _______________________________________________
    Request: [describe key fields]
    Response: [describe key fields]
    Latency SLA: ___ ms
    Error codes: _______________________________________________

  GET /[endpoint]
    Purpose: _______________________________________________
    [same structure]
```

---

## Section 6: Reliability and Operations

### 6.1 Failure Mode Analysis

```
FAILURE MODE ANALYSIS

| Component | Failure Mode | Probability | Impact | Detection | Recovery |
|-----------|-------------|-------------|--------|-----------|---------|
| Model provider | API outage | Low | Critical | Latency spike + error rate | Failover to secondary model |
| Vector store | Unavailable | Low | High | Retrieval timeout | Degrade to no-RAG mode |
| Database | Connection failure | Medium | Critical | Error rate spike | Read replica; retry |
| Cache | Unavailable | Medium | Low | Latency increase | Pass through to database |
| [AI component] | [failure] | | | | |
```

### 6.2 Runbook

```
RUNBOOK — [System Name]

Alert: AI quality score below threshold
  Detection: Quality monitoring dashboard — average score < [threshold]
  Immediate action:
    1. Check model provider status (provider status page)
    2. Review last prompt deployment (compare to previous version)
    3. Sample 20 recent outputs manually
  Root cause options:
    A: Model provider issue → Wait for provider resolution; consider fallback model
    B: Prompt regression → Rollback to previous prompt version
    C: Input distribution shift → Review recent query types; adjust retrieval
  Resolution: _______________________________________________
  Escalation: If unresolved in ___ hours → notify [PM + Engineering lead]

Alert: Cost exceeds daily budget
  Detection: Cost monitoring alert
  Immediate action:
    1. Identify spike source (which endpoint / user / query type)
    2. Apply rate limit if abuse suspected
    3. Review query volume vs model cost
  Resolution: _______________________________________________

Alert: Latency P99 exceeds SLA
  Detection: Latency monitoring alert
  Immediate action:
    1. Check model provider latency (provider dashboard)
    2. Check retrieval latency (vector store dashboard)
    3. Check infrastructure (CPU, memory, network)
  Resolution: _______________________________________________
```

---

## Section 7: Security and Compliance

### 7.1 Security Architecture

```
SECURITY ARCHITECTURE

Authentication and authorisation:
  Method: _______________________________________________
  Token management: _______________________________________________
  Scope / permissions model: _______________________________________________

Data encryption:
  In transit: TLS ___ / Encrypted: Yes / No
  At rest: Encrypted: Yes / No — Method: _______________________________________________
  AI model API calls: Encrypted: Yes / No

AI-specific security:
  Prompt injection protection: _______________________________________________
  System prompt confidentiality: Yes / No — Method: _______________________________________________
  Output PII scanning: Yes / No
  Model API key management: _______________________________________________

Audit logging:
  What is logged: _______________________________________________
  Log storage: _______________________________________________
  Retention: ___ days
  Access: _______________________________________________
```

### 7.2 Compliance Checklist

```
COMPLIANCE CHECKLIST

Data privacy:
  [ ] Data processing agreement with model provider
  [ ] PII not sent to external APIs without consent
  [ ] User right to erasure implemented
  [ ] Data retention limits enforced
  [ ] Privacy policy updated for AI

AI-specific compliance:
  [ ] AI disclosure to users (users know they interact with AI)
  [ ] AI outputs labelled as AI-generated where required
  [ ] Human oversight implemented for high-stakes decisions
  [ ] Bias testing completed before launch
  [ ] Governance decision log maintained

Regulatory (if applicable):
  [ ] GDPR Article 22 (automated decision-making) compliance
  [ ] Sector-specific AI regulations reviewed
  [ ] Legal sign-off obtained
```

---

## Full Architecture Document Template

```
# System Architecture — [System Name]
Date: ___  |  Author: ___  |  Version: ___  |  Status: Draft / Reviewed / Approved

## Executive Summary
[2–3 sentences: what this system does, its key components, and its key constraints]

## 1. System Overview
[Complete Section 1]

## 2. Component Architecture
[Complete Section 2]

## 3. Data Architecture
[Complete Section 3]

## 4. AI-Specific Architecture
[Complete Section 4]

## 5. Integration Architecture
[Complete Section 5]

## 6. Reliability and Operations
[Complete Section 6]

## 7. Security and Compliance
[Complete Section 7]

## Open Questions
| Question | Owner | Due | Status |
|----------|-------|-----|--------|
| | | | |

## Change Log
| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | | | Initial version |
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Architecture doc written once and never updated | Update on every major system change; version-controlled |
| AI components treated as a black box ("AI layer") | Document every AI component explicitly — model, prompts, retrieval, evaluation |
| No failure mode analysis | Every component must have a documented failure mode and recovery path |
| No cost architecture | Document the cost model and controls before the bill arrives |
| Security section as a checkbox | Document the actual security implementation — not aspirational controls |
| Architecture doc only readable by engineers | Layered documentation with executive summary and component detail |
| No runbook | On-call engineers cannot operate what is not documented |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Architecture doc update | On every major change | New component, integration, or AI model |
| Full architecture review | Quarterly | Planned review |
| Security review | Annually + on major change | Scheduled + triggered |
| Runbook test | Quarterly | Simulate top 3 failure scenarios |
| Cost model review | Monthly | Budget management |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Write a Complete System Architecture Document

> **Best for:** Documenting a new or existing AI system architecture comprehensively before or after it is built.

```
You are a solutions architect helping me write a complete system architecture document for an AI system.

Guide me through each section:
1. System overview — purpose, high-level architecture diagram (text), technology stack
2. Component architecture — component inventory, request flow diagram
3. Data architecture — data flow map, database schema overview
4. AI-specific architecture — orchestration, prompt management, model layer, retrieval, memory, evaluation, guardrails
5. Integration architecture — external integrations, API contract
6. Reliability and operations — failure mode analysis, runbook
7. Security and compliance — security architecture, compliance checklist

For each section, ask me targeted questions, then draft the section based on my answers. Flag any gap in my description that could cause operational problems.

After all sections:
- Identify the top 3 architectural risks in what I've described
- Identify the top 3 documentation gaps (things I was unable to answer clearly)
- Write the executive summary

My AI system: [describe what it does, who uses it, what AI components it has]
Tech stack: [describe your technology choices]
Team: [who will operate this system?]
Current state: [is this being designed or already built?]
```

---

### Prompt 2 — Document the AI-Specific Architecture

> **Best for:** Filling the most common gap in AI system documentation — the AI layer itself.

```
You are an AI systems architect helping me document the AI-specific components of my system.

Document each AI component:

1. Orchestration layer
   - What orchestration pattern is used? (sequential / parallel / conditional / loop / agent)
   - How is state managed across steps?
   - How are errors handled at each step?

2. Prompt management
   - Where are prompts stored and how are they versioned?
   - What is the deployment process for prompt changes?
   - How are prompt changes rolled back?

3. Model layer
   - Which model is used, and why that model specifically?
   - Is the model version pinned or auto-updated?
   - What is the fallback model and failover trigger?
   - What are the key parameters (temperature, max_tokens)?

4. Retrieval layer (if RAG)
   - What are the data sources and how are they indexed?
   - What retrieval strategy is used?
   - How is query quality optimised?

5. Evaluation pipeline
   - How is output quality measured in production?
   - What monitoring exists for quality drift?
   - What triggers a quality investigation?

After documenting all components:
- Write the AI cost architecture section
- Identify the single highest operational risk in this AI layer
- Write the runbook entry for the most likely AI failure scenario

My AI system: [describe the components and how they work]
```

---

### Prompt 3 — Write a Failure Mode Analysis

> **Best for:** Systematically identifying and documenting every failure mode in an AI system.

```
You are a reliability engineer helping me write a failure mode analysis for my AI system.

For each component I describe, identify:
1. The most likely failure modes (at least 3 per component)
2. The probability of each: High / Medium / Low
3. The impact of each: Critical / High / Medium / Low
4. How to detect the failure (what monitoring signal indicates it?)
5. The recovery action (exactly what steps does the on-call engineer take?)
6. The fallback behaviour (what does the system do while recovering?)

Special attention to AI-specific failures:
- Model quality degradation (how detected? how recovered?)
- Prompt regression after a change (how detected? how rolled back?)
- Cost spike from unexpected usage (how detected? how limited?)
- Retrieval failure (how detected? what is the no-RAG fallback?)
- Hallucination rate increase (how detected? how investigated?)

After the full analysis:
- Rank failures by risk score (probability × impact)
- Write the runbook for the top 3 highest-risk failures
- Identify any single-point-of-failure in the architecture

My AI system components: [describe each component and what it does]
Current monitoring: [what do you already track?]
Team on-call structure: [who responds to alerts?]
```

---

### Prompt 4 — Review an Architecture Document for Gaps

> **Best for:** Quality-checking an existing architecture document before a system goes to production or undergoes a compliance review.

```
You are a senior solutions architect reviewing an AI system architecture document for completeness and correctness.

Review the document I share against these criteria:

1. Completeness
   - Are all major components documented?
   - Is the AI layer fully documented (orchestration, prompts, model, retrieval, evaluation, guardrails)?
   - Is the data flow complete — from user input to AI output to storage?

2. Accuracy risk
   - Are there claims in the document that seem inconsistent or implausible?
   - Are there components that are described without enough detail to be operational?

3. Operational readiness
   - Is there a runbook for the top failure scenarios?
   - Is the monitoring and alerting system described?
   - Is the rollback procedure documented?

4. Security and compliance
   - Is data flow to external AI providers documented?
   - Are DPAs mentioned for all external AI services?
   - Is PII handling documented?

5. Cost and reliability
   - Is the cost model present?
   - Are cost controls documented?
   - Are SLAs defined and realistic?

For each criterion: Pass / Needs work / Missing — with specific feedback.
End with: the top 5 gaps that must be addressed before this document is considered complete.

Architecture document: [paste your document]
Context: [what is this system? who will operate it?]
```

---

### Prompt 5 — Create the System Architecture Runbook

> **Best for:** Writing the operational runbook that on-call engineers use to diagnose and recover from AI system failures.

```
You are a site reliability engineer helping me write a complete runbook for my AI system.

For each failure scenario I describe, write a runbook entry:

Each entry must include:
1. Alert name and detection signal (what monitoring alert fires?)
2. Severity classification (P1 / P2 / P3)
3. Immediate action (first 5 minutes — stabilise before diagnosing)
4. Diagnostic steps (step-by-step investigation)
5. Root cause options (the 3 most likely causes and how to confirm each)
6. Resolution for each root cause (exact steps)
7. Verification (how do you know the fix worked?)
8. Escalation path (if unresolved in X minutes, notify...)
9. Post-incident action (what to log, what to review)

Failure scenarios to cover:
1. AI quality score drops below threshold
2. Cost exceeds daily budget
3. Latency P99 exceeds SLA
4. Model provider API is unavailable
5. Content filter trigger rate anomaly (too high or too low)
6. [Any AI-specific failure you want to include]

After all runbook entries:
- Write the alert routing matrix (who gets what alert, via what channel)
- Write the escalation path for P1 incidents
- Identify any gap in the runbook that leaves a failure scenario without a response procedure

My AI system: [describe the key components]
Current alerts configured: [list if any]
On-call team structure: [who is on-call and what hours?]
```
