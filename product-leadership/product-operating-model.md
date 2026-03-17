# ⚙️ Product Operating Model — AI Product Builder Playbook

> **A framework for designing how a product team organises, plans, executes, and improves its work — the system that makes the strategy real**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Operating Model Components](#the-operating-model-components)
- [Component 1: Team Structure](#component-1-team-structure)
- [Component 2: Planning Rhythm](#component-2-planning-rhythm)
- [Component 3: Execution System](#component-3-execution-system)
- [Component 4: Review and Improvement](#component-4-review-and-improvement)
- [AI Product Operating Model Specifics](#ai-product-operating-model-specifics)
- [Scaling the Operating Model](#scaling-the-operating-model)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Strategy without an operating model is aspiration without execution. The operating model is the system that converts strategy into work — how the team is structured, how it plans, how it executes, and how it learns. A strong operating model makes a good strategy great. A weak operating model makes a great strategy irrelevant.

> **Core Principle:** The operating model must be designed — not inherited. Most product teams inherit their operating model from past practices, adjacent teams, or industry defaults. The result is an operating model that serves no one's strategy well and everyone's inertia perfectly. Intentional design of the operating model is one of the highest-leverage investments a product leader can make.

For AI products, the operating model requires modifications that most standard agile frameworks do not anticipate. AI features require evaluation infrastructure, monitoring systems, and quality review cycles that do not exist in traditional sprint workflows. Ignoring these creates invisible debt — features that ship but are not monitored, quality that degrades without detection, and incidents that are discovered by users rather than teams.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting a new product team | 🔴 Critical — design before the first sprint |
| Team is scaling and the current model is breaking | 🔴 Critical — the model that worked at 5 won't work at 20 |
| Execution quality has declined despite good people | 🟠 High — operating model failure, not talent failure |
| Cross-functional friction is slowing delivery | 🟠 High |
| Launching a significant AI product capability | 🟠 High — AI requires operating model modifications |
| Annual planning — how does the team work next year? | 🟡 Medium |

---

## The Operating Model Components

A product operating model has four components. All four must be designed; none can be borrowed wholesale from a methodology without customisation.

```
TEAM STRUCTURE
  ↓ who does what, and how they relate to each other
PLANNING RHYTHM
  ↓ how the team decides what to work on, at what horizon
EXECUTION SYSTEM
  ↓ how the team builds, ships, and learns within a cycle
REVIEW AND IMPROVEMENT
  ↓ how the team gets better over time
```

| Component | Core Question | Common Failure |
|---|---|---|
| **Team structure** | Is the team organised for the work? | Structure inherited rather than designed |
| **Planning rhythm** | Does planning serve execution? | Planning disconnected from delivery |
| **Execution system** | Can the team ship reliably? | Inconsistent process; undefined quality standards |
| **Review** | Is the team getting better? | Retrospectives without action; learnings not applied |

---

## Component 1: Team Structure

### 1.1 Team Design Principles

```
TEAM DESIGN PRINCIPLES

1. Organise around outcomes, not functions
   A team that owns a metric is more effective than a team that owns a feature.
   Structure teams around the user journey or business outcome they are responsible for.

2. Minimise cross-team dependencies
   Every dependency is a coordination cost and a delivery risk.
   The ideal team can design, build, and ship their area without waiting for another team.

3. Match team size to the work
   Small teams move faster. Large teams have more capability.
   The right team size is the smallest that can own the outcome end-to-end.
   Recommended: 5–9 people per product team (includes PM, Design, Engineering).

4. Collocate the decision-making
   The PM, design lead, and engineering lead should form the decision core.
   Decisions that require three-team meetings are decisions that should be restructured.

5. Stable teams over project teams
   Long-lived teams build domain knowledge, trust, and shared context.
   Project-based team assembly loses this investment after every project.
```

### 1.2 Core Roles in an AI Product Team

```
AI PRODUCT TEAM ROLES

Product Manager (PM)
  Owns: product strategy, prioritisation, stakeholder communication, launch decisions
  AI-specific: AI PRD, quality requirements, evaluation strategy, AI governance

Design Lead
  Owns: user experience, interaction design, design system contribution
  AI-specific: AI interaction design, trust UX, failure state design, confidence UI

Engineering Lead
  Owns: technical architecture, engineering execution, quality, deployment
  AI-specific: AI infrastructure, model integration, cost management, prompt deployment

AI/ML Engineer (if dedicated)
  Owns: model selection, prompt engineering, evaluation implementation, monitoring
  Consults: PM on quality requirements, Engineering on integration

Data Analyst
  Owns: product analytics, experimentation, performance reporting
  AI-specific: AI quality metrics, cohort analysis, retention impact measurement

QA Engineer
  Owns: test coverage, quality gates, regression testing
  AI-specific: AI-specific test cases, failure mode testing, adversarial testing

Optional / Shared Roles:
  Research (UX / User research): Shared across teams; embedded for key projects
  Legal / Privacy: Consulted on AI PRD, governance; not embedded
  AI Safety specialist: Consulted for high-risk features; not embedded
```

### 1.3 Team Topology for AI Products

```
TEAM TOPOLOGY OPTIONS

Option A — Embedded AI capability (recommended for early/growth stage)
  Structure: Each product squad has an AI engineer and/or data analyst embedded
  Pros: AI integrated into product thinking; fast iteration
  Cons: AI capability is distributed; harder to maintain standards

Option B — AI platform team + product squads (recommended for scale)
  Structure: Dedicated AI platform team provides shared infrastructure, models, and tooling.
              Product squads consume AI platform and focus on features.
  Pros: Standards maintained; infrastructure investment scales; expertise concentrated
  Cons: More coordination required; platform must serve squad needs proactively

Option C — Centralised AI team (not recommended beyond early stage)
  Structure: All AI work done by a central team; product squads are consumers
  Pros: Maximum expertise concentration
  Cons: Bottleneck; product squads lack AI context; slow
```

---

## Component 2: Planning Rhythm

### 2.1 The Three-Horizon Planning Rhythm

```
THREE-HORIZON PLANNING RHYTHM

Annual planning (1–2 days, November/December):
  Output: Strategic priorities, annual goals, resource allocation
  Who: CPO + PM leads + Engineering leads
  Produces: The annual roadmap themes and North Star targets

Quarterly planning (1 day per quarter):
  Output: Quarterly OKRs, prioritised backlog, team capacity allocation
  Who: Full product team + key stakeholders
  Produces: Committed quarterly roadmap + deferred items list

Sprint planning (2–4 hours per sprint):
  Output: Sprint goal, committed backlog items, team agreement
  Who: PM + Engineering + Design (full squad)
  Produces: Sprint commitment + owner for each item

This rhythm connects strategy to execution:
  Annual → sets the direction
  Quarterly → commits the priorities
  Sprint → executes the commitments
```

### 2.2 Quarterly Planning Process

```
QUARTERLY PLANNING PROCESS — 4–6 WEEKS BEFORE QUARTER START

Week -6: Data gathering
  [ ] Review current quarter performance vs targets
  [ ] Compile user research insights from the quarter
  [ ] Review experiment results and learnings
  [ ] Gather stakeholder input (what should next quarter prioritise?)

Week -4: Strategy review
  [ ] Confirm North Star and strategic pillars are still correct
  [ ] Review competitive landscape — any new threats or opportunities?
  [ ] Align on the 2–3 most important outcomes for next quarter

Week -3: Prioritisation
  [ ] Score the backlog using the chosen prioritisation framework
  [ ] Model capacity — how many sprints, what team composition?
  [ ] Stack rank the top initiatives against available capacity
  [ ] Draft the quarterly roadmap

Week -2: Stakeholder alignment
  [ ] Present draft roadmap to executive team
  [ ] Incorporate feedback — adjust priorities where evidence supports
  [ ] Confirm the "Not Doing" list with stakeholders

Week -1: Team alignment
  [ ] Present final roadmap to full product team
  [ ] Break roadmap items into sprint-sized chunks
  [ ] Confirm: does the team understand what they are building and why?
  [ ] Identify risks that could disrupt the plan

Quarter start: Execute
```

### 2.3 Sprint Rhythm

```
SPRINT RHYTHM (2-week sprint)

Day 1 (Monday): Sprint planning
  Duration: 2–3 hours
  Output: Sprint goal + committed backlog + owner for each item

Daily: Async standup
  Format: [DONE] [DOING] [BLOCKED] — in Slack or equivalent
  No daily meeting unless explicitly needed

Day 7 (Monday): Mid-sprint check
  Duration: 30 minutes
  Purpose: Are we on track? Anything to deprioritise or add?

Day 10 (Thursday): Demo prep
  Engineers ensure demos are ready for Friday

Day 11 (Friday): Sprint review + retrospective
  Sprint review (45 min): Demo what was built; PM accepts or rejects
  Retrospective (45 min): What went well, what to improve, specific actions

Day 14 (next Monday): Sprint planning begins the next cycle
```

---

## Component 3: Execution System

### 3.1 Definition of Ready (DoR)

A backlog item is ready to be pulled into a sprint when it meets the Definition of Ready. Items that do not meet DoR are not brought into sprint planning.

```
DEFINITION OF READY (DoR)

For all items:
[ ] User story written: "As [user], I want [capability] so that [outcome]"
[ ] Acceptance criteria defined (at least 3 specific, testable criteria)
[ ] Design is complete and approved (for UX-facing items)
[ ] Dependencies identified and resolved (or explicitly accepted)
[ ] Effort estimated by the team
[ ] PM has answered all engineering questions

For AI items (additional requirements):
[ ] AI approach specified (model, prompt pattern, data sources)
[ ] Quality threshold defined (minimum acceptable score)
[ ] Evaluation approach designed (how quality will be tested)
[ ] Failure modes and designed responses documented
[ ] Cost estimate per interaction validated
[ ] Privacy requirements specified (PII handling, data retention)
```

### 3.2 Definition of Done (DoD)

An item is done when it meets the Definition of Done. "Done" means ready for production — not "code complete."

```
DEFINITION OF DONE (DoD)

For all items:
[ ] Code reviewed and merged
[ ] Unit tests written and passing
[ ] Acceptance criteria all met and verified
[ ] QA sign-off received
[ ] Documentation updated (user-facing and internal)
[ ] Deployed to staging — PM has accepted the implementation

For AI items (additional requirements):
[ ] Evaluation dataset tested — quality score meets threshold
[ ] Safety evaluation passed — adversarial test pass rate meets threshold
[ ] Monitoring dashboard live — alerts configured
[ ] Prompt version controlled — change log entry written
[ ] Output sampling active
[ ] Rollback procedure documented and tested
[ ] Privacy checklist complete
[ ] Cost per interaction within budget model
```

### 3.3 Quality Gates in Execution

```
EXECUTION QUALITY GATES

Gate 1 — Ready for engineering (end of sprint planning)
  Item has passed Definition of Ready
  All unknowns resolved or risk-accepted

Gate 2 — Ready for QA (end of engineering)
  Code reviewed and unit tests passing
  Feature flag deployed — staging environment verified

Gate 3 — Ready for PM acceptance (end of QA)
  QA sign-off received
  All acceptance criteria verified
  Known issues documented with resolution plan

Gate 4 — Ready for production (end of PM acceptance)
  PM has accepted the implementation
  Definition of Done complete
  Rollout plan confirmed
```

---

## Component 4: Review and Improvement

### 4.1 Retrospective Structure

```
EFFECTIVE RETROSPECTIVE FORMAT (45–60 minutes)

Opening (5 min):
  Set the tone: blameless, improvement-focused, psychological safety
  Confirm: all voices count equally

Data gathering (10 min):
  Silent — each person writes their own notes
  Prompts: What went well? What slowed us down? What one thing would make next sprint better?

Discussion (20 min):
  Share one item each (round robin — prevents dominant voices)
  Cluster similar themes
  Identify the top 2–3 themes with team consensus

Action items (15 min):
  For each theme: one specific action, one owner, one deadline
  Maximum 3 action items — more is not implemented
  Review last sprint's action items: did we do them?

Closing (5 min):
  Rate the retrospective itself (1–5)
  What would make the retrospective more valuable?

Retrospective outputs:
  3 action items max — specific, owned, time-bound
  Action items tracked in the next sprint as first-class items
  No action item survives two sprints without resolution
```

### 4.2 Operating Model Health Check

```
OPERATING MODEL HEALTH CHECK (quarterly)

Team structure:
  Is the team organised around the outcomes it is responsible for? Y / Partially / N
  Are cross-team dependencies creating delays? Y / No / Occasionally
  Is the team size appropriate for the scope of work? Y / Too small / Too large

Planning rhythm:
  Is quarterly planning producing a clear, committed roadmap? Y / Partially / N
  Is sprint planning starting with clear requirements? Y / Partially / N
  Is the team consistently hitting sprint commitments? ___% hit rate

Execution system:
  Is the Definition of Ready preventing unclear items from entering sprints? Y / Partially / N
  Is the Definition of Done preventing undone items from being called done? Y / Partially / N
  Are AI-specific DoR and DoD items being applied? Y / Partially / N

Review and improvement:
  Are retrospective action items being implemented? ___% completion
  Is the team improving measurably sprint over sprint? Y / Plateau / Declining
  Are learnings being shared across teams? Y / Partially / N

Top improvement priority: _______________________________________________
```

---

## AI Product Operating Model Specifics

### 5.1 AI-Specific Operating Rituals

```
AI-SPECIFIC RITUALS

AI Quality Weekly (30 minutes — PM + AI lead):
  Review AI quality scores for all production features
  Identify any features trending below target
  Review content filter trigger rates and anomalies
  Assign action items for quality improvements

AI Prompt Review (per change — PM + AI lead + Engineering):
  Run regression tests on the updated prompt
  Review test results against the existing quality baseline
  Sign off before deployment
  Update prompt change log

AI Evaluation Sprint (quarterly — 1 sprint dedicated):
  Refresh evaluation datasets with new examples from production failures
  Re-run all production features against updated evaluation dataset
  Update quality baselines
  Identify features that need prompt or architecture improvements

AI Red Team (quarterly — Engineering + PM):
  Attempt to break production AI features with adversarial inputs
  Document all successful attacks and near-misses
  Update guardrails and evaluation datasets based on findings
```

### 5.2 AI Integration into Standard Rituals

```
AI INTEGRATION INTO STANDARD RITUALS

Sprint planning additions for AI items:
  "Is the AI approach specified in the DoR?" (blocker if no)
  "Is the evaluation approach designed?" (blocker if no)
  "Is the cost estimate validated?" (blocker if no)

Sprint review additions for AI items:
  PM demos the AI feature including edge cases and failure states
  QA confirms adversarial test cases were run
  Monitoring dashboard shown as part of acceptance

Retrospective additions for AI teams:
  Standing item: "Any AI quality issues this sprint?"
  Standing item: "Did any AI failure modes reach users?"
  Standing item: "Is our AI evaluation keeping pace with what we're shipping?"
```

---

## Scaling the Operating Model

### 6.1 Operating Model at Different Scales

```
OPERATING MODEL BY SCALE

1–5 people (founding team):
  Structure: Everyone does everything; PM is often also the AI engineer
  Planning: Weekly priorities — no formal quarterly cycle
  Execution: Ship fast; quality checked by founders
  Review: Weekly team discussion — no formal retrospective
  AI specifics: Evaluation is manual; monitoring is minimal

5–20 people (early product team):
  Structure: Dedicated PM + Design + Engineering; shared AI capability
  Planning: Quarterly planning begins; sprints formalised
  Execution: DoR and DoD introduced; basic AI-specific gates
  Review: Bi-weekly retrospectives; monthly operating model check
  AI specifics: Evaluation datasets introduced; basic monitoring dashboards

20–100 people (growth):
  Structure: Multiple squads with shared platform; embedded AI capability
  Planning: Full quarterly cycle; OKRs introduced
  Execution: Full DoR/DoD; AI-specific rituals; governance gates
  Review: Weekly retrospectives; quarterly operating model review
  AI specifics: AI platform team formed; automated quality monitoring

100+ people (scale):
  Structure: Product areas with multiple squads; dedicated AI platform
  Planning: Annual + quarterly + sprint; full OKR cascade
  Execution: Standardised across squads; governance integrated
  Review: Squad-level + leadership-level reviews; operating model evolution team
  AI specifics: Full AI governance; ethics committee; regulatory compliance programme
```

---

## Templates

### Template A: Operating Model Canvas

```
# Operating Model Canvas — [Team / Product Name]
Date: ___  |  Owner: ___  |  Review date: ___

## Team Structure
Composition: _______________________________________________
Organisation: _______________________________________________
Key dependencies: _______________________________________________

## Planning Rhythm
Annual planning: _______________________________________________
Quarterly planning: _______________________________________________
Sprint length: ___  |  Sprint rituals: _______________________________________________

## Execution System
Definition of Ready: [link]
Definition of Done: [link]
Quality gates: _______________________________________________
AI-specific requirements: _______________________________________________

## Review and Improvement
Retrospective format: _______________________________________________
Operating model review: _______________________________________________
Learning mechanisms: _______________________________________________

## Operating Model Health
Last review date: ___
Top improvement priority: _______________________________________________
Next review date: ___
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Copying a methodology wholesale without adaptation | Design the operating model for your specific team, product, and stage |
| No Definition of Ready — items enter sprints unclear | DoR enforced in sprint planning; unclear items are not pulled |
| AI features shipped without evaluation and monitoring | AI-specific DoD requires evaluation and monitoring before "done" |
| Retrospectives without action items | Maximum 3 specific, owned actions per retrospective |
| Quarterly planning that produces no clear priorities | Quarterly planning must produce a committed roadmap AND a Not Doing list |
| Operating model never reviewed | Quarterly health check + annual design review |
| AI rituals added to an already-overloaded calendar | Remove a ritual before adding one; respect the team's attention budget |
| Structure organised around functions not outcomes | Organise squads around metrics or user journeys, not engineering disciplines |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Daily async standup | Daily | Each team member |
| Sprint planning | Every 2 weeks | PM |
| Sprint review + retrospective | Every 2 weeks | PM |
| AI quality weekly | Weekly | PM + AI lead |
| Monthly stakeholder review | Monthly | PM |
| Quarterly planning | Quarterly | PM + CPO |
| Operating model health check | Quarterly | PM |
| AI evaluation sprint | Quarterly | PM + AI team |
| Annual operating model design | Annually | CPO + PM leads |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Product Operating Model

> **Best for:** Designing the operating model for a new team or redesigning one that is not working.

```
You are an organisational design expert helping me design a product operating model.

Design the complete operating model across all four components:

1. Team structure
   - Recommend the team composition for my product and stage
   - Recommend the team topology (embedded AI / platform + squads / centralised)
   - Identify the key roles and their AI-specific responsibilities

2. Planning rhythm
   - Design the annual, quarterly, and sprint planning process
   - For each horizon: what is the output, who attends, how long, what decisions are made?

3. Execution system
   - Write the Definition of Ready for my team (including AI-specific requirements)
   - Write the Definition of Done for my team (including AI-specific requirements)
   - Design the quality gates between phases

4. Review and improvement
   - Design the retrospective format appropriate for my team
   - Design the operating model health check for quarterly review
   - Design the AI-specific rituals that should be added to the calendar

After all four components:
- Identify the top 3 operating model anti-patterns my team is currently exhibiting
- Write the 30-day implementation plan for transitioning to this model
- Identify what to stop doing in order to create space for new rituals

My team: [size, composition, remote/hybrid]
Product stage: [early / growth / scale]
Current operating model: [describe how the team currently works]
Known problems: [what is not working?]
Is this an AI product: [yes/no]
```

---

### Prompt 2 — Write Definitions of Ready and Done

> **Best for:** Creating the quality gates that prevent unclear work from entering sprints and undone work from being called done.

```
You are a product process designer helping me write the Definition of Ready and Definition of Done for my team.

Write both definitions for my specific context:

1. Definition of Ready (DoR)
   - What must be true before an item can enter sprint planning?
   - For each criterion: why does this criterion matter? What goes wrong without it?
   - Include: user story format, acceptance criteria standard, design requirements, dependency check
   - Include AI-specific DoR criteria if applicable

2. Definition of Done (DoD)
   - What must be true before an item can be called done?
   - For each criterion: who verifies it and how?
   - Include: code review, testing, documentation, deployment, PM acceptance
   - Include AI-specific DoD criteria if applicable

After writing both definitions:
- Identify the criterion most likely to be skipped under time pressure
- Write the conversation for enforcing DoR when a stakeholder wants to pull an unclear item
- Write the conversation for enforcing DoD when a developer wants to call undone work done
- Design the sprint planning gate where DoR is checked

My team: [composition and roles]
Product type: [what we build — AI / traditional / mixed]
Current quality problems: [what slips through that shouldn't?]
Current process: [how do items currently enter and exit sprints?]
```

---

### Prompt 3 — Design the Quarterly Planning Process

> **Best for:** Creating a quarterly planning rhythm that connects strategy to execution reliably.

```
You are a product planning expert helping me design my quarterly planning process.

Design the complete process for the 6 weeks before each quarter:

1. Week-by-week preparation
   - What happens each week in the 6 weeks before quarter start?
   - Who is responsible for each step?
   - What is the output of each step?

2. Data inputs to planning
   - What data must be gathered before the planning session?
   - How is user research synthesised for planning?
   - How are experiment results and learnings incorporated?

3. The planning session itself
   - Who attends? (Full team vs leadership team?)
   - What is the agenda and how long does it take?
   - What decisions are made in the session vs prepared in advance?
   - What does the team leave with?

4. Stakeholder alignment
   - How and when is the draft roadmap shared with executives?
   - How is feedback incorporated without the roadmap becoming a wish list?
   - How is the "Not Doing" list communicated?

5. Team alignment
   - How is the final plan communicated to the full team?
   - How does quarterly planning connect to sprint planning?
   - How does the team know if they are on track mid-quarter?

My team: [size and structure]
Stakeholder environment: [who needs to be aligned]
Current planning problems: [what is not working in current planning]
Product stage: [early / growth / scale]
```

---

### Prompt 4 — Design AI-Specific Operating Rituals

> **Best for:** Adding AI-specific rituals to a standard product operating model without overwhelming the team's calendar.

```
You are an AI product operations specialist helping me design the AI-specific rituals my team needs.

Design the complete AI ritual set for my team:

1. AI quality weekly (30 minutes)
   - What is reviewed?
   - Who attends?
   - What is the output?
   - What action triggers an escalation?

2. AI prompt review (per change)
   - What process does a prompt change go through before deployment?
   - Who reviews and signs off?
   - What constitutes a pass vs a hold?

3. AI evaluation sprint (quarterly)
   - What does the team do during a dedicated AI evaluation sprint?
   - What is the output?
   - How does it feed back into the product roadmap?

4. AI red team (quarterly)
   - How is a red team exercise structured?
   - Who participates?
   - What are the outputs and how are they actioned?

5. Integration into existing rituals
   - What AI-specific items should be added to sprint planning?
   - What should be added to sprint review?
   - What should be added to retrospectives?

After designing all rituals:
- Estimate the total additional time per sprint these rituals add
- Identify which ritual adds the most value
- Recommend what existing ritual could be shortened to create space
- Write the 60-day adoption plan for introducing these rituals

My team: [size and current ritual set]
Current AI quality problems: [what quality issues are we experiencing?]
Current sprint velocity: [how many sprints per quarter]
Available team time for new rituals: [realistically, what can be added?]
```

---

### Prompt 5 — Run an Operating Model Health Check

> **Best for:** Quarterly review of whether the current operating model is serving the team — identifying what to fix before it becomes a crisis.

```
You are an organisational effectiveness advisor helping me run a quarterly operating model health check.

Guide me through a structured assessment of my operating model:

1. Team structure health
   - Is the team organised around outcomes or around functions?
   - Are cross-team dependencies creating delays? If so, which ones?
   - Is the team composition appropriate for the current scope of work?

2. Planning rhythm health
   - Is quarterly planning producing a clear, committed roadmap?
   - Are sprint commitments being hit? (What % of sprint items complete?)
   - Is there alignment between what the team plans and what stakeholders expect?

3. Execution system health
   - Is DoR being enforced? (Are unclear items entering sprints?)
   - Is DoD being enforced? (Are items being called done before they are?)
   - Are AI-specific quality gates being applied consistently?

4. Review and improvement health
   - Are retrospective action items being completed?
   - Is the team improving measurably over time?
   - Are learnings being captured and applied?

5. AI operating model health
   - Are AI rituals running and producing value?
   - Is AI quality being monitored systematically?
   - Is the team catching AI issues before users do?

After the assessment:
- Identify the top 3 operating model issues to address next quarter
- Write the specific changes needed for each issue
- Estimate the impact of each change on team velocity and quality

My team's current state:
[Describe what is working and what is not — be honest about the pain points]
Last quarter's performance: [sprint completion %, quality metrics, incidents]
Current rituals: [list what the team currently does regularly]
```
