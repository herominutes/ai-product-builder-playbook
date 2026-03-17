# ⚖️ Responsible AI Principles — AI Product Builder Playbook

> **The ethical foundation for building AI products that are safe, fair, transparent, and accountable — to users, to society, and to the future**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [Principle 1: Do No Harm](#principle-1-do-no-harm)
- [Principle 2: Be Transparent](#principle-2-be-transparent)
- [Principle 3: Ensure Fairness](#principle-3-ensure-fairness)
- [Principle 4: Protect Privacy](#principle-4-protect-privacy)
- [Principle 5: Maintain Human Control](#principle-5-maintain-human-control)
- [Principle 6: Be Accountable](#principle-6-be-accountable)
- [Principle 7: Build for Long-Term Benefit](#principle-7-build-for-long-term-benefit)
- [Responsible AI in Practice](#responsible-ai-in-practice)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Responsible AI is not a constraint on what you can build. It is a quality standard for how you build it. The teams that take responsible AI seriously do not build slower or less ambitiously — they build things that users can actually trust, regulators can actually approve, and the world can actually benefit from. The teams that ignore it build fast and then spend years rebuilding trust they destroyed in weeks.

> **Core Principle:** Responsible AI is not a legal compliance function. It is a design discipline. The question is not "what are we allowed to do?" but "what is the right thing to do?" The distinction matters because regulations lag reality — what is legally permissible today may be clearly harmful, and what harms users is the problem responsible AI exists to prevent.

These seven principles are grounded in the emerging consensus of AI ethics — drawing from regulatory frameworks, industry standards, and the practical experience of building AI products that affect real people's lives. They are written for product builders, not ethicists — they are meant to be applied, not debated.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Designing any AI feature that affects consequential user decisions | 🔴 Critical — apply before design begins |
| Launching AI in a regulated domain (health, finance, legal, employment) | 🔴 Critical — regulatory and ethical review required |
| AI feature is generating user complaints or media attention | 🔴 Critical — ethical audit immediately |
| Considering training on user data or using user data to improve the AI | 🟠 High |
| Entering a new geography with different regulatory context | 🟠 High |
| Reviewing an AI vendor or third-party model for integration | 🟠 High |
| Annual ethics and governance review | 🟡 Medium |

---

## Principle 1: Do No Harm

### The Principle

The primary obligation of every AI builder is to ensure that what they build does not harm users, third parties, or society. This obligation supersedes business goals, competitive pressures, and user requests. An AI feature that generates revenue while causing harm is not a success — it is a liability that has not yet been discovered.

> **In practice:** Harm is not limited to obvious physical harm. It includes psychological harm, economic harm, reputational harm, and societal harm. An AI system that manipulates user decisions, amplifies misinformation, discriminates against protected groups, or erodes user autonomy is causing harm — even if no individual incident rises to the level of a scandal.

### Harm Assessment Framework

```
HARM ASSESSMENT

For every AI feature, identify potential harms:

Direct harms (harms to the user directly):
[ ] Could this AI output cause the user to make a harmful decision?
[ ] Could this AI output cause the user psychological distress?
[ ] Could this AI output deceive the user about something that matters?
[ ] Could this AI output violate the user's privacy or dignity?

Indirect harms (harms through the user to others):
[ ] Could this AI output facilitate harm to third parties?
[ ] Could this AI output enable illegal activity?
[ ] Could this AI output amplify misinformation?

Systemic harms (harms at scale or over time):
[ ] Could this AI system, at scale, harm groups or communities?
[ ] Could this AI system erode a social good (trust, privacy, truth)?
[ ] Could this AI system create or entrench inequality?

For each identified harm:
Severity: Critical / Significant / Moderate / Minor
Likelihood: High / Medium / Low
Mitigation: _______________________________________________
Residual risk after mitigation: Acceptable / Requires escalation / Unacceptable
```

### Harm Escalation Protocol

```
HARM ESCALATION PROTOCOL

Minor harm risk (no escalation required):
  Apply standard guardrails and monitoring.
  Document in risk register.

Moderate harm risk (PM escalation):
  PM must approve the mitigation plan.
  Legal review recommended.
  Enhanced monitoring required.

Significant harm risk (executive escalation):
  CPO and Legal must approve.
  External ethics review recommended.
  Launch contingent on mitigation.

Critical harm risk (board-level):
  Feature must not launch.
  Full executive review required.
  External ethics panel recommended.
```

---

## Principle 2: Be Transparent

### The Principle

Users have a right to know when they are interacting with AI, what the AI is using to generate its response, and what the AI's limitations are. Transparency is not optional — it is the foundation of informed consent and the basis of legitimate AI use. AI systems that deceive users about their nature, capabilities, or data use are fundamentally untrustworthy.

> **In practice:** Transparency has four dimensions: disclosure (users know they're interacting with AI), provenance (users know where AI outputs come from), limitation (users know what the AI cannot do), and data (users know what information the AI is using about them).

### Transparency Requirements

```
TRANSPARENCY REQUIREMENTS

Disclosure requirements:
[ ] Users are informed they are interacting with AI before the first interaction
[ ] AI-generated content is clearly labelled as AI-generated throughout
[ ] The AI does not present itself as human when directly asked
[ ] AI involvement in consequential decisions is disclosed to affected parties

Provenance requirements:
[ ] AI outputs that draw from sources cite those sources
[ ] AI outputs generated from user data acknowledge what data was used
[ ] When AI lacks grounding in evidence, this is stated explicitly

Limitation requirements:
[ ] The AI's scope limitations are communicated proactively
[ ] The AI communicates uncertainty honestly — not with false confidence
[ ] Known quality limitations are disclosed to users before they encounter them

Data use requirements:
[ ] Users are informed what data the AI has access to
[ ] Users are informed whether their data is used to improve the AI
[ ] Users can access, correct, and delete their data used by the AI

Minimum disclosure statement (for all AI features):
"This [response / summary / recommendation] was generated by AI.
[If RAG:] It is based on [source description].
The AI may make errors — please verify important information."
```

---

## Principle 3: Ensure Fairness

### The Principle

AI systems should treat all users equitably. They should not produce systematically worse outcomes for users based on race, gender, age, disability, socioeconomic status, or other protected characteristics. Fairness is not a demographic question — it is a performance question. An AI that is less accurate, less helpful, or less respectful for some groups than others is failing those groups, regardless of intent.

> **In practice:** Fairness is not achieved by ignoring demographic characteristics — it is achieved by measuring performance across them. An AI system that has never been tested for performance differences across demographic groups is not a fair system. It is a system whose unfairness has not yet been discovered.

### Fairness Assessment Protocol

```
FAIRNESS ASSESSMENT PROTOCOL

Step 1 — Identify affected populations
Who does this AI system affect? List all user groups.
Which groups are most at risk of disparate impact? (Historically underserved / underrepresented)

Step 2 — Define fairness metrics
What does fairness mean for this specific AI use case?
  Equal accuracy: The AI is equally accurate across groups
  Equal opportunity: The AI provides equally helpful outputs across groups
  Equal treatment: The AI responds with equal respect and quality across groups

Step 3 — Test for disparity
Run the AI on test cases that vary demographic signals while holding other variables constant.
Measure: is there a statistically significant difference in output quality across groups?

Step 4 — Set fairness thresholds
Alert threshold: > 5% performance gap between any two demographic groups
Action threshold: > 10% performance gap → feature must not launch until gap is addressed

Step 5 — Monitor in production
Track performance metrics segmented by user demographics (where available and legal).
Alert if disparity increases over time (model drift can introduce or worsen bias).
```

### Bias Types to Test

```
BIAS TESTING CHECKLIST

Training data bias:
[ ] Is the training data representative of all user groups?
[ ] Are underrepresented groups represented proportionally?
[ ] Is historical data used that encodes historical discrimination?

Output bias:
[ ] Do outputs differ in quality across demographic groups?
[ ] Do outputs differ in tone, respect, or helpfulness across groups?
[ ] Do outputs reflect stereotypes about any group?

Feedback loop bias:
[ ] Does user feedback come disproportionately from some groups?
[ ] Does improvement driven by feedback create disparate impact?

Algorithmic bias:
[ ] Does the model perform better on language patterns of dominant groups?
[ ] Does the model under-perform on non-standard dialects or languages?
```

---

## Principle 4: Protect Privacy

### The Principle

Users' personal information is not a resource to be extracted — it is information entrusted to the product team for a specific purpose. AI systems that collect, use, or retain personal information beyond what is necessary for the stated purpose violate user trust and, increasingly, the law. Privacy is not a legal compliance function. It is a user right that must be actively protected.

> **In practice:** Privacy protection in AI requires more than a privacy policy and a GDPR checkbox. It requires data minimisation (collecting only what is necessary), purpose limitation (using data only for stated purposes), retention limits (deleting data when no longer needed), and user control (giving users meaningful choices about their data).

### Privacy by Design for AI

```
PRIVACY BY DESIGN CHECKLIST

Data minimisation:
[ ] We collect only the data necessary for the stated purpose
[ ] No additional data is collected because it might be useful later
[ ] Data is anonymised or aggregated where possible

Purpose limitation:
[ ] User data is used only for the purpose stated at collection
[ ] User data is not used to train AI models without explicit consent
[ ] User data is not shared with third parties beyond what is disclosed

Retention limits:
[ ] Retention periods are defined for all AI-processed data
[ ] Automated deletion is enforced at the retention limit
[ ] Users can delete their data at any time — and deletion is complete

User control:
[ ] Users can access all data held about them in relation to AI
[ ] Users can correct inaccurate data
[ ] Users can opt out of AI data use without losing core functionality
[ ] Users are notified if their data is used in a new way

Security:
[ ] AI-processed data is encrypted at rest and in transit
[ ] Access to AI training data is role-restricted and audited
[ ] Model providers who receive user data have signed DPAs
[ ] Third-party model providers are evaluated for their data practices
```

---

## Principle 5: Maintain Human Control

### The Principle

Humans must remain meaningfully in control of consequential decisions — even when AI is making recommendations, taking actions, or operating autonomously. This is not a limitation on AI capability; it is a safeguard against AI errors compounding without correction. The moment human oversight becomes impossible, the accountability for AI errors becomes unresolvable.

> **In practice:** Human control does not require a human to approve every AI output. It requires that for every category of consequential action, there is a defined mechanism by which a human can understand, verify, override, or correct what the AI has done — and that this mechanism is accessible, usable, and exercised.

### Human Control Requirements

```
HUMAN CONTROL REQUIREMENTS

For consequential AI decisions, implement at least one of:

Level A — Approval gate (highest control):
  Human approves before AI action is taken.
  Required for: high-stakes, irreversible actions.

Level B — Notification with undo (medium control):
  AI acts; human receives notification and can undo within a defined window.
  Required for: moderate-stakes actions with a clear undo mechanism.

Level C — Audit trail (minimum control):
  AI acts; human can review in an audit log and correct downstream.
  Acceptable for: low-stakes, easily reversible actions with monitoring.

For each consequential AI action in your product:
Action: _______________________________________________
Stakes: High / Medium / Low
Control level: A / B / C
Control mechanism: _______________________________________________

Human control is NOT maintained when:
- AI takes irreversible actions without any human awareness
- AI makes consequential recommendations that users cannot override
- There is no mechanism to correct AI errors after they occur
- The explanation of AI actions is too complex for users to act on
```

---

## Principle 6: Be Accountable

### The Principle

For every AI decision that affects a user, there must be a named person who is accountable for that decision. Accountability cannot be diffused into "the algorithm" or "the model." If a user is harmed by an AI output, someone must be responsible for preventing it, detecting it, and remedying it. That person is, first and foremost, the PM who built the feature.

> **In practice:** Accountability requires: clarity on who is responsible for what, an audit trail that enables retrospective review, a mechanism for users to seek redress, and a culture in which accountability is exercised rather than avoided.

### Accountability Framework

```
ACCOUNTABILITY FRAMEWORK

For each AI feature, define:

Decision accountability:
  Who is accountable for the quality of AI outputs? _______________________________________________
  Who is accountable for AI safety and policy compliance? _______________________________________________
  Who is accountable for user data privacy? _______________________________________________
  Who is accountable if a user is harmed? _______________________________________________

Audit trail requirements:
[ ] Every AI interaction is logged with: timestamp, input hash, output hash, model version
[ ] Audit log is retained for minimum [N] months
[ ] Audit log is accessible to: engineering (full) / legal (on request) / user (own data)

User redress mechanism:
[ ] Users can report AI harms or errors through a clearly accessible channel
[ ] Response SLA for reported AI harms: ___ business days
[ ] Escalation path for serious harms: _______________________________________________

Incident accountability:
[ ] AI incidents have a named incident owner
[ ] Post-incident review is mandatory for P1/P2 AI incidents
[ ] User notification for incidents that affected their data: within ___ hours
```

---

## Principle 7: Build for Long-Term Benefit

### The Principle

AI products that extract short-term value at the expense of long-term user or societal wellbeing are not good products — they are extraction mechanisms with a shelf life. The responsible AI builder asks not just "does this create value today?" but "does this leave users, communities, and society better off over time?" This question is especially important for AI systems that operate at scale and shape behaviour across millions of users.

> **In practice:** Long-term benefit requires asking uncomfortable questions about the systemic effects of AI systems: Does this make users more capable or more dependent? Does this strengthen or weaken human relationships and skills? Does this create value for users or extract value from them?

### Long-Term Benefit Assessment

```
LONG-TERM BENEFIT ASSESSMENT

User capability question:
"Does this AI system make users more capable over time — or more dependent?"
  [ ] More capable: AI augments user skills and knowledge
  [ ] Neutral: No effect on user capability
  [ ] More dependent: Users lose capability as AI does more for them

If "more dependent": Is this acceptable? (Sometimes it is — automation of rote tasks is a benefit)
If "more dependent" in a domain where user capability matters: Re-evaluate the design.

Societal impact question:
"At scale, does this AI system make society better or worse?"
  Consider: information quality, social connection, economic opportunity, trust, wellbeing

Sustainability question:
"Is the value this AI creates sustainable — or does it depend on practices that cannot continue?"
  Consider: data practices, competitive practices, user manipulation, environmental cost

User relationship question:
"Does this AI system build a relationship where users genuinely benefit — or where they are used?"
  Signs of genuine benefit: Users achieve their goals; users have meaningful control; users understand the exchange
  Signs of extraction: Dark patterns; manufactured dependency; opaque value exchange
```

---

## Responsible AI in Practice

### Ethics Review Process

```
ETHICS REVIEW PROCESS — PRE-LAUNCH

Trigger: Any AI feature that is consumer-facing, operates in a sensitive domain,
or involves significant data processing.

Reviewers: PM (mandatory) + Legal (mandatory) + Design (recommended) + External ethics advisor (for high-risk)

Review checklist:
[ ] Harm assessment completed — no unmitigated critical or significant harms
[ ] Transparency requirements met — disclosure, provenance, limitations, data
[ ] Fairness testing completed — no performance disparity > 5% across groups
[ ] Privacy by design implemented — minimisation, limitation, retention, control
[ ] Human control mechanisms defined and implemented for consequential actions
[ ] Accountability framework defined — named owners, audit trail, redress mechanism
[ ] Long-term benefit assessment completed — no identified systemic harms

Decision: Launch approved / Conditional launch / Do not launch
```

### Responsible AI Incident Response

```
RESPONSIBLE AI INCIDENT CLASSIFICATION

Level 1 — Ethical incident (requires PM response):
  Minor harm to one or few users
  Quickly corrected with no lasting impact
  Response: Fix + document + improve guardrails

Level 2 — Ethical breach (requires executive response):
  Harm to multiple users or significant harm to one user
  Systemic issue suggesting broader risk
  Response: Fix + user notification + external review of practices

Level 3 — Ethical crisis (requires board and public response):
  Widespread harm or harm to vulnerable users
  Fundamental question about the product's right to exist
  Response: Feature suspension + full investigation + public accountability
```

---

## Templates

### Template A: Responsible AI Review Card

```
# Responsible AI Review — [Feature Name]
Date: ___  |  Reviewer: ___  |  Risk level: Low / Medium / High / Critical

P1 Do No Harm
  Critical/significant harms identified: _______________________________________________
  All mitigated: Yes / No / Partial — gaps: _______________________________________________

P2 Be Transparent
  Disclosure: _______________________________________________
  Limitations communicated: Yes / No
  Data use disclosed: Yes / No

P3 Ensure Fairness
  Groups tested: _______________________________________________
  Max disparity found: ___%  — Acceptable (< 5%): Yes / No

P4 Protect Privacy
  Data minimisation applied: Yes / No
  Retention limits defined: Yes / No
  User control implemented: Yes / No

P5 Maintain Human Control
  Consequential actions identified: _______________________________________________
  Control level assigned: A / B / C

P6 Be Accountable
  Accountability owners named: Yes / No
  Audit trail implemented: Yes / No
  Redress mechanism in place: Yes / No

P7 Long-Term Benefit
  User capability impact: Positive / Neutral / Negative
  Societal impact assessment: _______________________________________________

DECISION: Launch approved / Conditional / Blocked
Conditions: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Treating responsible AI as a legal compliance exercise | Responsible AI is a design discipline — applied before legal review, not instead of it |
| "We haven't been sued yet" as evidence of responsible practice | Absence of legal action does not indicate absence of harm |
| Fairness testing only on visible demographic variables | Test across all groups likely to be affected, including intersectional groups |
| Privacy policy as the privacy solution | Privacy by design requires technical implementation, not just disclosure |
| Human control as approval for everything | Human control means defined oversight for consequential actions — not bureaucracy |
| "The algorithm decided" as an accountability shield | A named person is accountable for every consequential AI decision |
| Optimising for engagement at the expense of wellbeing | Short-term engagement metrics must not override long-term user benefit |
| Ethics review as a one-time pre-launch activity | Ethics requires ongoing monitoring, not just a pre-launch checklist |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Responsible AI review | Per AI feature, pre-launch | PM + Legal |
| Fairness monitoring | Monthly (production AI features) | PM + Data |
| Privacy audit | Quarterly | PM + Legal |
| Ethics incident retrospective | After every Level 2+ incident | PM + Leadership |
| Full responsible AI framework review | Annually | CPO + Legal |
| Regulatory landscape monitoring | Quarterly | Legal + PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Run a Responsible AI Review

> **Best for:** Before launching any AI feature — systematically applying all seven responsible AI principles.

```
You are an AI ethics specialist helping me run a responsible AI review before launching a feature.

Apply all seven responsible AI principles to the feature I describe:

1. Do No Harm — identify all potential harms (direct, indirect, systemic) and their severity
2. Be Transparent — assess disclosure, provenance, limitation, and data transparency
3. Ensure Fairness — identify which groups might be affected and design a fairness testing plan
4. Protect Privacy — assess data collection, use, retention, and user control
5. Maintain Human Control — identify consequential actions and assign control levels
6. Be Accountable — define accountability owners, audit trail, and user redress
7. Build for Long-Term Benefit — assess user capability impact and societal effects

For each principle:
- Rate: Strong / Partial / Weak / Not addressed
- Identify specific gaps
- Recommend the specific change that addresses the gap

After all seven principles:
- Classify the overall risk level: Low / Medium / High / Critical
- Write the conditions that must be met before launch
- Identify any principle violation that should block launch entirely
- Write the responsible AI review card

My feature: [describe what the AI does, who uses it, and what data it processes]
Domain: [what industry or context — health / finance / general / other]
User population: [describe — including any vulnerable or at-risk groups]
Data involved: [what data does the AI receive, process, or store]
```

---

### Prompt 2 — Design a Fairness Testing Programme

> **Best for:** Building a systematic approach to testing an AI feature for bias and disparate impact across user groups.

```
You are an AI fairness specialist helping me design a fairness testing programme for my AI feature.

Design the complete fairness testing programme:

1. Affected population mapping
   - Who is affected by this AI system?
   - Which groups are at highest risk of disparate impact?
   - What intersectional groups should be considered?

2. Fairness metric selection
   - What does fairness mean for this specific use case?
   - Equal accuracy / Equal opportunity / Equal treatment / All three?
   - Define what each means concretely for my AI task

3. Test dataset design
   - What test cases would reveal bias if present?
   - How do I create demographically varied test inputs that are otherwise identical?
   - What sample size do I need for statistical significance?

4. Disparity thresholds
   - What % performance gap triggers an alert vs blocks launch?
   - How do I handle trade-offs between fairness metrics (improving one may worsen another)?

5. Production fairness monitoring
   - How do I monitor for bias in production on an ongoing basis?
   - What new bias could emerge as the user base or model evolves?

6. Remediation approach
   - If bias is detected: what are the options for addressing it?
   - How do I validate that the remediation worked without introducing new bias?

My AI feature: [describe the AI task]
Protected groups most relevant to my context: [list]
Data available for testing: [describe]
Regulatory context: [any fairness requirements from law or regulation]
```

---

### Prompt 3 — Implement Privacy by Design

> **Best for:** Applying Principle 4 in depth — designing privacy protections into an AI feature before any engineering begins.

```
You are a privacy engineer helping me implement privacy by design for my AI feature.

Design the complete privacy architecture across five dimensions:

1. Data minimisation
   - What is the minimum data required for this AI feature to work?
   - What data is being collected that goes beyond the minimum?
   - How can I achieve the same outcome with less data?

2. Purpose limitation
   - What is the stated purpose for data collection?
   - Is user data being used for any additional purpose (including model training)?
   - What controls ensure data is not used beyond its stated purpose?

3. Retention limits
   - For each data type: what is the minimum retention period needed?
   - What automated deletion mechanism enforces these limits?
   - What happens to user data if the user deletes their account?

4. User control
   - How does a user access all data held about them?
   - How does a user correct inaccurate data?
   - How does a user delete their data — and how complete is the deletion?
   - How does a user opt out of AI data use without losing core functionality?

5. Third-party data sharing
   - What user data is sent to model providers?
   - Is a Data Processing Agreement in place?
   - Does the provider train on user data?
   - How is the provider evaluated for their own privacy practices?

After all five dimensions:
- Write the user-facing privacy disclosure for this feature
- Identify the highest privacy risk and its mitigation
- Write the privacy checklist for the pre-launch review

My AI feature: [describe]
Data collected: [list all data types]
Model provider: [name]
User geography: [EU / US / global]
```

---

### Prompt 4 — Handle an Ethical Incident

> **Best for:** When an AI feature has caused or may have caused harm — designing the response to protect users, restore trust, and prevent recurrence.

```
You are an AI ethics crisis advisor helping me respond to an ethical incident involving my AI product.

Guide me through a structured ethical incident response:

1. Incident classification
   - Level 1 (minor harm, contained) / Level 2 (significant harm, systemic) / Level 3 (crisis)
   - Based on: severity of harm, number of users affected, reversibility, media attention risk

2. Immediate containment (first 2 hours)
   - What must be done immediately to stop harm from continuing?
   - Should the feature be suspended? Rate-limited? Restricted to certain users?
   - Who must be notified internally, and in what order?

3. User notification (first 24 hours for Level 2+)
   - Which users need to be notified?
   - What must the notification include? (what happened, who was affected, what we are doing)
   - What is the communication channel and timeline?

4. Investigation (first 72 hours)
   - What happened, and why?
   - Which responsible AI principle was violated?
   - Was this a design failure, a monitoring failure, or both?

5. Remediation and accountability
   - What changes prevent this from happening again?
   - Who is accountable for the incident and for the remediation?
   - Is a public statement needed? What should it say?

6. Systemic review
   - Does this incident suggest similar risks in other AI features?
   - What changes to the responsible AI review process would have caught this earlier?

The incident: [describe what happened]
Users affected: [how many and how]
Current state: [is it ongoing or contained?]
```

---

### Prompt 5 — Write the Responsible AI Policy for Your Organisation

> **Best for:** Creating the foundational responsible AI policy document that governs how your organisation builds and operates AI products.

```
You are an AI policy writer helping me create the responsible AI policy for my organisation.

Write a complete, operational responsible AI policy that:
- Is specific to my organisation's context — not a generic template
- Is written for practitioners (PMs, engineers, designers) — not just for legal
- Specifies what must be done at each stage of the product lifecycle
- Is enforced through process gates, not just aspirational language

Policy sections:
1. Policy statement (1 paragraph — what we commit to and why)
2. Scope (who this applies to and what it covers)
3. The seven principles — for each: what it means, what it requires, and who is responsible
4. The responsible AI review process — when it is triggered, who runs it, what it produces
5. Roles and responsibilities — the named accountabilities for responsible AI across the org
6. Incident response — how we respond to ethical incidents at each severity level
7. Monitoring and governance — how we maintain responsible AI practice over time
8. Updates and exceptions — how the policy evolves and how exceptions are handled

After writing the policy:
- Identify the top 3 implementation risks (where teams will cut corners)
- Write the training module summary for onboarding all employees to this policy
- Write the quarterly governance report template for leadership review

My organisation: [describe — size, industry, current AI products]
Regulatory environment: [key regulations that apply]
Known risks: [any existing ethical concerns or near-misses]
Team to govern this: [who owns responsible AI in the org]
```
