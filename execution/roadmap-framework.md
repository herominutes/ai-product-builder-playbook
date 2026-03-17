# 🗺️ Roadmap Framework — AI Product Builder Playbook

> **A framework for building, communicating, and maintaining a product roadmap that reflects strategy, builds stakeholder trust, and guides team execution**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Roadmap Model](#the-roadmap-model)
- [Roadmap Type 1: Now-Next-Later](#roadmap-type-1-now-next-later)
- [Roadmap Type 2: Outcome-Based Roadmap](#roadmap-type-2-outcome-based-roadmap)
- [Roadmap Type 3: Theme-Based Roadmap](#roadmap-type-3-theme-based-roadmap)
- [Roadmap Communication](#roadmap-communication)
- [Roadmap Maintenance](#roadmap-maintenance)
- [Roadmap for AI Products](#roadmap-for-ai-products)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A product roadmap is the most visible document a product manager owns — and the most frequently misunderstood. Stakeholders treat it as a contract. Executives treat it as a commitment. Customers treat it as a promise. Engineers treat it as a specification. Used well, a roadmap is none of these things. It is a communication tool that conveys strategic direction, builds alignment, and sets appropriate expectations for what the team will work on and why.

> **Core Principle:** A roadmap communicates direction and priorities — not dates and features. The moment a roadmap becomes a list of features with delivery dates, it stops being a strategic tool and becomes a project plan. Project plans are useful, but they are not roadmaps. A roadmap answers "where are we going and why?" A project plan answers "what are we building and when?"

For AI products, roadmaps require additional nuance. AI capabilities evolve rapidly, AI features carry higher uncertainty than traditional software, and the dependencies between AI capabilities, data readiness, and evaluation infrastructure create sequencing constraints that do not appear on traditional roadmaps.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Quarterly planning — defining what to build next quarter | 🔴 Critical — roadmap must be updated before planning concludes |
| Stakeholders are confused about product direction | 🔴 Critical — roadmap misalignment is a leadership failure |
| Engineering is building without clear strategic context | 🔴 Critical — teams without roadmaps drift |
| New executive or board member joining — needs product context | 🟠 High |
| Customer is asking "what's coming next?" | 🟠 High |
| Annual planning — setting the 12-month direction | 🟡 Medium |

---

## The Roadmap Model

No single roadmap format works for all audiences and contexts. This framework provides three types, each suited to a different use case.

```
NOW-NEXT-LATER
  ↓ direction without dates — maximum flexibility, minimum commitment
OUTCOME-BASED
  ↓ metrics before features — what we will move, not what we will build
THEME-BASED
  ↓ strategic bets — categories of investment, not individual features
```

| Type | Best For | Audience | Commitment Level |
|---|---|---|---|
| **Now-Next-Later** | Internal teams, fast-moving startups | Engineering, Design, PM | Low |
| **Outcome-based** | Executive and board communication | Leadership, investors | Medium |
| **Theme-based** | Customer and partner communication | Customers, sales, marketing | Low |

---

## Roadmap Type 1: Now-Next-Later

### 1.1 What It Is

The Now-Next-Later roadmap organises work into three horizons without committing to specific dates. It communicates direction and priority without creating false precision.

| Horizon | Definition | Commitment Level | Detail Level |
|---|---|---|---|
| **Now** | Current quarter — actively being built | High — sprint-level planning | Feature-level |
| **Next** | Following 1–2 quarters — directionally committed | Medium — may shift | Initiative-level |
| **Later** | Beyond next quarter — strategic intent | Low — subject to change | Theme-level |

### 1.2 Horizon Definitions

```
NOW (current quarter):
  Definition: Work that is either in progress or about to start within the current sprint cycle
  What goes here: Specific features or initiatives that engineering has capacity for
  Level of detail: Initiative name + 1-sentence description + owner
  Commitment: High — changing "Now" items requires explicit priority decision

NEXT (1–2 quarters out):
  Definition: Work that is directionally committed but not yet fully scoped
  What goes here: Initiatives that have been prioritised and have a defined hypothesis
  Level of detail: Initiative name + outcome goal + approximate effort
  Commitment: Medium — can shift based on "Now" learnings or new evidence

LATER (beyond next quarter):
  Definition: Strategic bets and future investments — not commitments
  What goes here: Areas of exploration, moonshots, requests under consideration
  Level of detail: Theme or problem area — no specific features
  Commitment: Low — explicitly communicated as direction, not promise
```

### 1.3 Now-Next-Later Template

```
NOW-NEXT-LATER ROADMAP — [Product Name]
Last updated: ___  |  Owner: ___

NOW (Q[X] [Year])
  [ ] [Initiative name] — [1 sentence: what and why] — Owner: ___ — Status: ___
  [ ] [Initiative name] — [1 sentence: what and why] — Owner: ___ — Status: ___
  [ ] [Initiative name] — [1 sentence: what and why] — Owner: ___ — Status: ___

NEXT (Q[X+1] – Q[X+2])
  [ ] [Initiative name] — [outcome goal: what metric does this move?]
  [ ] [Initiative name] — [outcome goal]
  [ ] [Initiative name] — [outcome goal]

LATER (beyond Q[X+2])
  • [Theme / problem area] — [1 sentence on why this matters]
  • [Theme / problem area]
  • [Theme / problem area]

NOT DOING (explicit rejections — important for clarity)
  • [Item] — [1 sentence: why not now]
  • [Item] — [1 sentence: why not now]
```

---

## Roadmap Type 2: Outcome-Based Roadmap

### 2.1 What It Is

The outcome-based roadmap replaces features with metric targets. Instead of "we will build X," it says "we will move metric Y by Z amount." This forces the team to think in outcomes before jumping to solutions.

```
OUTCOME-BASED ROADMAP STRUCTURE

Quarter: Q[X] [Year]

NORTH STAR
  Current: ___  |  Target: ___  |  Target date: ___

QUARTERLY OUTCOMES
  Outcome 1: Improve [metric] from [current] to [target]
    Initiatives: [1–3 specific things we will do to achieve this outcome]
    Owner: ___

  Outcome 2: Improve [metric] from [current] to [target]
    Initiatives: _______________________________________________
    Owner: ___

  Outcome 3: Reduce [metric] from [current] to [target]
    Initiatives: _______________________________________________
    Owner: ___

WHAT WE ARE EXPLICITLY NOT OPTIMISING FOR THIS QUARTER
  [Metric or outcome] — deferred because [reason]
```

### 2.2 Outcome to Initiative Mapping

```
OUTCOME-TO-INITIATIVE MAPPING

Outcome: [Metric target]
  ↓
Hypotheses (what could move this metric?):
  H1: If we [change], [metric] will improve by [estimate] because [reasoning]
  H2: If we [change], [metric] will improve by [estimate] because [reasoning]
  ↓
Selected initiative(s): [highest-confidence + highest-impact hypothesis]
  ↓
Experiment design: [how will we validate this is working?]
  ↓
Success criteria: [metric improvement threshold that confirms success]
```

---

## Roadmap Type 3: Theme-Based Roadmap

### 3.1 What It Is

The theme-based roadmap organises future work around strategic bets rather than specific features. It is most useful for customer and partner communication where feature-level specificity creates false expectations.

```
THEME-BASED ROADMAP

[Product Name] — Strategic Themes [Year]

THEME 1: [Name] — [Tagline: what this theme is about]
  Why this matters: [1–2 sentences]
  What we are working on: [areas of investment — not specific features]
  Expected outcome: [what gets better for users]
  Horizon: Now / Soon / Exploring

THEME 2: [Name] — [Tagline]
  Why this matters: _______________________________________________
  What we are working on: _______________________________________________
  Expected outcome: _______________________________________________
  Horizon: Now / Soon / Exploring

THEME 3: [Name] — [Tagline]
  [Same structure]
```

### 3.2 Theme Selection Criteria

```
THEME SELECTION CRITERIA

A theme belongs on the roadmap when:
[ ] It addresses a validated user problem or strategic opportunity
[ ] It aligns with at least one strategic pillar
[ ] There is at least one initiative ready to be scoped within it
[ ] Leadership and the product team are committed to investment

A theme should be removed when:
[ ] No initiative has shipped under it in 2 consecutive quarters
[ ] The underlying user problem has been validated as not significant
[ ] Strategic priorities have shifted away from it

Recommended: 3–5 themes maximum. More themes = no themes.
```

---

## Roadmap Communication

### 4.1 Audience-Specific Roadmap Views

The same roadmap serves different audiences with different filters:

| Audience | What They Care About | Roadmap View | Format |
|---|---|---|---|
| **Engineering** | What to build next; technical dependencies | Now-Next-Later + detail | Jira / Linear / Notion |
| **Executive team** | Strategic direction; resource allocation | Outcome-based | Slide deck or dashboard |
| **Board / investors** | Competitive positioning; growth drivers | Theme-based + outcomes | One-page summary |
| **Customers** | What's coming that helps them | Theme-based (curated) | Public roadmap or email |
| **Sales / CS** | What to promise; when to expect features | Now-Next-Later (filtered) | Slack / internal wiki |

### 4.2 Roadmap Presentation Guide

```
ROADMAP PRESENTATION STRUCTURE

Opening (2 minutes):
"Here is the strategic context: [our North Star + our 3 strategic pillars].
The roadmap you're about to see reflects our bets on how to move these metrics."

Now section (5 minutes):
Walk through current quarter items.
For each: what we're building → what outcome we expect → how we'll know it worked.

Next section (5 minutes):
Walk through next quarter direction.
Emphasise: these are directional commitments, not dates or feature specs.

Later section (3 minutes):
Walk through strategic themes.
Emphasise: these are areas of exploration — not promises.

Not doing (2 minutes):
Explicitly name 2–3 things we are not doing and why.
This builds more trust than anything else on the roadmap.

Questions (10 minutes):
Lead with: "What's missing? What are we getting wrong?"

Closing:
"Here's how to stay updated: [link to living roadmap]
Next review: [date]"
```

### 4.3 Managing Roadmap Expectations

```
EXPECTATION MANAGEMENT PRINCIPLES

1. Always communicate the confidence level
   Now = high confidence  |  Next = medium  |  Later = low
   Never let an audience assume all items have equal certainty.

2. Lead with the "not doing" list
   Explicitly naming what you are not building builds more credibility
   than any feature announcement.

3. Connect every item to an outcome
   "We are building X because we expect it to move Y by Z."
   No item should appear without a business rationale.

4. Never give dates to Later items
   As soon as a date is attached, it becomes a commitment in the audience's mind.
   "Later" items should never have a target date until they move to Next.

5. Set a review cadence and stick to it
   Monthly for executives. Quarterly for customers.
   A roadmap that is never revisited is not a roadmap — it is a wish list.
```

---

## Roadmap Maintenance

### 5.1 Roadmap Review Cadence

```
ROADMAP REVIEW CADENCE

Weekly:
  [ ] Update status of Now items (in progress / at risk / complete)
  [ ] Any new evidence that should change Next priorities?

Monthly:
  [ ] Review completion rate of Now items
  [ ] Assess whether Next items are still correctly prioritised
  [ ] Identify any Later items ready to promote to Next
  [ ] Share updated roadmap with executive team

Quarterly:
  [ ] Full roadmap refresh — coincides with quarterly planning
  [ ] Review all pillars and themes for continued relevance
  [ ] Update confidence levels based on learnings from current quarter
  [ ] Communicate changes to all audiences with clear rationale
```

### 5.2 Roadmap Change Management

```
ROADMAP CHANGE PROTOCOL

When a roadmap item needs to change:

Step 1 — Document the reason
  What new information caused this change?
  Is this a priority change, a scope change, or an estimate change?

Step 2 — Assess the impact
  Which stakeholders committed to this item? (customers, sales, execs)
  What commitments need to be unwound?

Step 3 — Communicate proactively
  Never let stakeholders discover a change on their own.
  Communication must precede discovery.

Step 4 — Explain with evidence
  "We are changing [item] because [specific new information / decision].
  Instead, we are prioritising [replacement] because [rationale]."

Step 5 — Update the roadmap and version it
  Date-stamp every roadmap version.
  Keep a changelog of significant changes.

Change communication timing:
  Impact on Now items: Communicate within 24 hours
  Impact on Next items: Communicate within 1 week
  Impact on Later items: Address at next quarterly review
```

---

## Roadmap for AI Products

### 6.1 AI-Specific Roadmap Considerations

```
AI ROADMAP CONSIDERATIONS

1. Capability dependencies must be explicit
   AI features often depend on infrastructure (vector store, evaluation pipeline)
   that must be built before the feature can be delivered.
   Show these dependencies on the roadmap — do not bury them in engineering backlog.

2. Data readiness is a first-class roadmap item
   If an AI feature requires data that is not yet available, data preparation
   belongs on the roadmap as a prerequisite.

3. Evaluation milestones belong on the roadmap
   "Build AI feature" and "validate AI feature meets quality bar" are two separate
   roadmap items with different owners and effort estimates.

4. Research spikes for unproven AI capabilities
   If the AI capability has not been proven, put a research spike on the roadmap
   before committing to the feature delivery.

5. Model dependency risks must be documented
   If a roadmap item depends on a specific model capability,
   document what happens if that model capability is not available or not sufficient.
```

### 6.2 AI Roadmap Template

```
AI PRODUCT ROADMAP — [Product Name]
Last updated: ___  |  Owner: ___

AI INFRASTRUCTURE (prerequisite for features)
  [ ] [Infrastructure item] — Status: ___  — Blocks: [feature names]

AI RESEARCH AND VALIDATION (uncertainty reduction)
  [ ] [Research spike] — Question: [what are we trying to prove?]  — Timeline: ___

AI FEATURES — NOW
  [ ] [Feature] — AI approach: ___  — Data ready: Yes/No  — Eval framework: Yes/No

AI FEATURES — NEXT
  [ ] [Feature] — AI approach: ___  — Dependencies: ___  — Risk: H/M/L

AI CAPABILITIES — LATER
  • [Capability theme] — Dependency: [data / model / infrastructure]
  • [Capability theme]

AI QUALITY IMPROVEMENTS (ongoing)
  [ ] [Improvement area] — Current score: ___  — Target: ___

EXPLICITLY NOT BUILDING (with reason)
  • [Item] — Reason: [data not available / model not reliable / not the right time]
```

---

## Templates

### Template A: Executive Roadmap Summary

```
# Product Roadmap Summary — Q[X] [Year]
Date: ___  |  PM: ___

## Where We Are Going
North Star: [current → target]
Driving strategy: [1–2 sentences on why these priorities]

## This Quarter (High Confidence)
| Initiative | Expected Outcome | Metric Target |
|-----------|-----------------|--------------|
| | | |
| | | |

## Next Quarter (Directional)
| Initiative | Expected Outcome |
|-----------|-----------------|
| | |
| | |

## Strategic Themes (Exploring)
• [Theme] — [why it matters]
• [Theme]

## What We Are Not Doing
• [Item] — [why]
• [Item] — [why]

## Questions This Roadmap Cannot Yet Answer
• [Open question 1]
• [Open question 2]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Roadmap with specific dates for Next and Later items | Now = this quarter with dates; Next and Later = no dates |
| Feature-level detail in Later horizon | Later should be themes or outcomes — not features |
| Roadmap updated only once a year | Monthly for execs, quarterly full refresh |
| Roadmap that never changes | Change is expected — the process for communicating change matters |
| Same roadmap for all audiences | Executive view / team view / customer view are different documents |
| Roadmap with no "Not Doing" list | The Not Doing list builds more trust than any feature announcement |
| AI feature on roadmap without infrastructure dependencies shown | Infrastructure and data readiness must be visible on the AI roadmap |
| Research spikes missing from the AI roadmap | Unproven AI capabilities must have a research spike before the feature commitment |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Now item status update | Weekly | PM |
| Executive roadmap share | Monthly | PM |
| Stakeholder roadmap review | Monthly | PM |
| Full quarterly refresh | Quarterly | PM + leadership |
| Customer roadmap communication | Quarterly | PM + Marketing |
| Roadmap changelog update | On any significant change | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Build a Now-Next-Later Roadmap

> **Best for:** Creating a clean, strategy-aligned roadmap for the next three quarters without over-committing to dates or feature specs.

```
You are a product strategy advisor helping me build a Now-Next-Later roadmap.

Guide me through constructing each horizon:

1. Now (current quarter)
   - What should be in the Now horizon given my current sprint commitments?
   - Are there any items currently in Now that should be moved to Next (deprioritised)?
   - For each Now item: write the 1-sentence description of what it is and why it matters

2. Next (1–2 quarters)
   - What are the highest-priority initiatives for Next, given my strategic pillars?
   - Frame each as an outcome: "improve [metric] from [X] to [Y]" not "build feature Z"
   - Identify any dependencies that must be resolved before Next items can start

3. Later (strategic intent)
   - What themes or areas of exploration belong in Later?
   - What items currently in Next should be moved to Later (too far away or too uncertain)?

4. Not Doing
   - What should explicitly be on the Not Doing list?
   - For each: write the 1-sentence rationale (builds stakeholder trust)

After all horizons:
- Check: is the Now horizon achievable with my stated team capacity?
- Check: does the roadmap trace clearly to my North Star and strategic pillars?
- Write the 2-minute verbal summary for presenting this roadmap to the executive team

My product: [describe]
Strategic pillars: [list 2–4]
North Star metric: [define]
Current team capacity: [engineering weeks per quarter]
Items I know are in Now: [list current sprint commitments]
Items under consideration for Next and Later: [list everything you're thinking about]
```

---

### Prompt 2 — Convert Features to Outcomes

> **Best for:** Transforming a feature-based backlog into an outcome-based roadmap that communicates strategy instead of specifications.

```
You are a product strategy coach helping me convert my feature-based roadmap into an outcome-based roadmap.

For each feature or initiative I describe, help me:
1. Identify the user outcome it is trying to achieve
2. Identify the metric that would measure that outcome
3. Set a realistic improvement target for that metric
4. Rewrite the roadmap item as "[improve metric] from [current] to [target]"
5. Confirm whether the feature is still the best way to achieve that outcome — or suggest an alternative

After converting all items:
- Group them into 3–5 quarterly outcome themes
- Identify any features that serve the same underlying outcome (consolidation opportunity)
- Identify any features that do not map to a clear outcome (remove or reframe)
- Write the outcome-based roadmap in the standard format

My feature list:
1. [Feature name — describe what it does]
2. [Feature name — describe]
3. [Feature name — describe]
[continue for all items]

Context:
North Star: _______________________________________________
Primary metrics I care about: _______________________________________________
Current baseline values: _______________________________________________
```

---

### Prompt 3 — Communicate a Roadmap Change

> **Best for:** When a roadmap item needs to change — writing the communication that maintains stakeholder trust.

```
You are a product communication specialist helping me communicate a roadmap change without damaging stakeholder trust.

Design the communication for each audience:

1. Assess the change
   - What type of change is this: priority / scope / estimate / full removal?
   - Which audiences are most affected and why?
   - What was the commitment made to each audience?

2. Engineering team communication
   - What they need to know and how quickly
   - How to frame the change in terms of strategic context, not just "plans changed"

3. Executive team communication
   - Lead with the new direction, not the change
   - Explain the evidence that prompted the change
   - What is the impact on outcomes and metrics?

4. Customer / sales communication (if applicable)
   - What do customers who were expecting this feature need to hear?
   - How do you maintain credibility while delivering disappointing news?

5. The standard for communicating roadmap changes
   - Write the template your team should use for all future roadmap changes

Roadmap change:
What was on the roadmap: [describe the original item and commitment]
What is changing: [describe the new plan]
Reason for the change: [what new information or decision prompted this?]
Who was affected by the original commitment: [list stakeholders]
```

---

### Prompt 4 — Build an AI Product Roadmap

> **Best for:** Building a roadmap specifically for an AI product — including infrastructure dependencies, research spikes, and evaluation milestones.

```
You are an AI product strategy advisor helping me build a roadmap that accurately reflects the dependencies and uncertainties unique to AI products.

Design the AI product roadmap across five layers:

1. AI infrastructure layer
   - What infrastructure must be built before AI features can be delivered?
   - Which features are blocked by which infrastructure items?
   - Show these dependencies clearly on the roadmap

2. Research and validation layer
   - Which planned AI capabilities have not yet been proven reliable enough to commit to?
   - Design a research spike for each unproven capability
   - What question must the spike answer before the feature can be committed?

3. AI feature layer (Now / Next / Later)
   - For each AI feature: specify the AI approach, data dependencies, and evaluation requirements
   - Flag any feature where data readiness is uncertain
   - Flag any feature where model reliability is unproven

4. Quality improvement layer
   - What ongoing AI quality improvements belong on the roadmap?
   - Current vs target quality scores for each production AI feature

5. Explicitly not building
   - What AI capabilities are explicitly out of scope and why?

After the full roadmap:
- Identify the critical path: what must be delivered in what sequence for the roadmap to work?
- Identify the highest-risk dependency
- Write the AI roadmap presentation for the executive team

My AI product: [describe]
Current AI features in production: [list]
Planned AI features: [list with descriptions]
Known infrastructure gaps: [describe]
Data available vs data needed: [describe]
```

---

### Prompt 5 — Create Audience-Specific Roadmap Views

> **Best for:** Adapting a single internal roadmap into multiple audience-appropriate versions for executives, customers, and sales.

```
You are a product communication strategist helping me create audience-specific views of my product roadmap.

Using the internal roadmap I describe, create three distinct views:

1. Executive view (for CPO, CEO, board)
   - Focus: outcomes, metrics, and strategic pillars — not features
   - Format: outcome-based roadmap with metric targets
   - What to include: Now outcomes, Next direction, strategic themes, key risks
   - What to exclude: feature-level detail, technical implementation, engineering estimates

2. Customer / partner view (for external stakeholders)
   - Focus: what gets better for them — not what we're building
   - Format: theme-based, with no dates on Next or Later
   - What to include: themes that affect them, approximate horizon (now/soon/exploring)
   - What to exclude: internal initiatives, competitive intelligence, unproven capabilities

3. Sales and CS view (for internal revenue teams)
   - Focus: what they can promise and when, what to use as competitive differentiation
   - Format: Now-Next-Later with honest confidence levels
   - What to include: customer-facing features with realistic timelines
   - What to exclude: internal tooling, infrastructure, research spikes

For each view:
- Write the actual roadmap content (not just the structure)
- Write the 1-paragraph verbal summary for presenting this view
- Identify the 2–3 questions each audience is most likely to ask

My internal roadmap: [describe what is in Now, Next, and Later]
My strategic pillars: [list]
Customer segments: [describe who the customer view is for]
Key sales situations: [describe what the sales team most needs to communicate]
```
