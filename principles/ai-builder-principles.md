# 🔨 AI Builder Principles — AI Product Builder Playbook

> **The core principles that guide how responsible, effective AI products are designed, built, and operated**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [Principle 1: Start With the Human Problem](#principle-1-start-with-the-human-problem)
- [Principle 2: Design for Trust, Not Just Utility](#principle-2-design-for-trust-not-just-utility)
- [Principle 3: Fail Gracefully](#principle-3-fail-gracefully)
- [Principle 4: Measure What Matters](#principle-4-measure-what-matters)
- [Principle 5: Build in the Open](#principle-5-build-in-the-open)
- [Principle 6: Earn Autonomy Incrementally](#principle-6-earn-autonomy-incrementally)
- [Principle 7: Protect the Human in the Loop](#principle-7-protect-the-human-in-the-loop)
- [Principle 8: Ship to Learn, Not to Finish](#principle-8-ship-to-learn-not-to-finish)
- [Applying the Principles](#applying-the-principles)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Principles are not rules. Rules tell you what to do. Principles tell you how to think — so that you can make good decisions in situations no rule anticipated. The AI builder's landscape changes faster than any rulebook can keep pace with. New models, new capabilities, new failure modes, and new user expectations emerge constantly. Principles are what allow a team to navigate that change with consistency and integrity.

> **Core Principle (meta-principle):** The principles in this document are not aspirational values posted on a wall. They are working constraints that apply to every product decision, every architecture choice, and every launch gate. If a principle is not influencing decisions, it is not a principle — it is decoration.

These eight principles were developed from the practice of building AI products — not from theory. They reflect the lessons of teams that got things right and teams that got things wrong. They are specific enough to produce real constraints and flexible enough to apply across different product types, industries, and stages.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting a new AI product or team — establishing shared values | 🔴 Critical — principles before architecture |
| A product decision is creating internal disagreement | 🔴 Critical — use principles to resolve |
| An AI feature failed and the team is conducting a retrospective | 🟠 High — which principle was violated? |
| Onboarding a new team member to AI product practices | 🟠 High |
| Preparing to enter a new domain or user segment | 🟠 High — apply principles to new context |
| Quarterly team review | 🟡 Medium |

---

## Principle 1: Start With the Human Problem

### The Principle

No AI feature should be built because the technology is available. Every AI feature should be built because there is a specific human problem — validated with evidence — that AI is the best solution for. Technology without a problem is a prototype. A problem without validation is an assumption.

> **In practice:** Before any AI development begins, the product team must be able to answer: "What specific human problem are we solving? How do we know this problem is real? Why is AI the right solution rather than a simpler alternative?"

### What This Looks Like

| Applies Principle | Violates Principle |
|---|---|
| PM interviews 12 users, identifies that manual synthesis takes 4 hours/week, validates AI can reduce this to 20 minutes | PM reads a competitor announcement and proposes matching their AI feature |
| Team runs a research spike to confirm model can reliably extract the required information before committing to build | Team commits to building an AI feature without testing whether a model can do the task |
| Product brief starts with problem statement and evidence before describing the AI solution | Product brief starts with "we will use GPT to..." |

### The Test

```
PRINCIPLE 1 TEST — START WITH THE HUMAN PROBLEM

Before any AI development commitment, answer all three:

1. What is the specific human problem this AI feature solves?
   [1–2 sentences — must describe a user struggle, not a product capability]

2. What evidence confirms this problem is real and significant?
   [ ] User interviews (minimum 8)
   [ ] Support ticket analysis
   [ ] Analytics data
   [ ] Validated by: ___

3. Why is AI the right solution (not a simpler alternative)?
   [ ] AI is necessary because: ___
   [ ] Simpler alternative considered and rejected because: ___

If any question cannot be answered: do not begin AI development.
```

---

## Principle 2: Design for Trust, Not Just Utility

### The Principle

A useful AI feature that users do not trust will not be used. Trust is not a byproduct of quality — it is a design outcome that must be explicitly engineered. Users need to understand what the AI is doing, why it did it, and what to do when it is wrong. These are design requirements, not afterthoughts.

> **In practice:** For every AI interaction, the design team must answer: "Does the user understand what the AI is doing? Do they know how to verify it? Do they know what to do if it's wrong?" If the answer to any of these is no, the trust design is incomplete.

### Trust Design Components

| Component | Description | Implementation |
|---|---|---|
| **Transparency** | User understands what the AI is doing and why | Show reasoning, not just output |
| **Calibrated confidence** | AI communicates uncertainty honestly | Confidence signals, caveats, explicit uncertainty |
| **Controllability** | User can modify, correct, or override the AI | Edit, reject, regenerate controls on all outputs |
| **Explainability** | User can understand why the AI produced this output | "Based on [source]..." / "Because you said..." |
| **Consistency** | AI behaves predictably across similar inputs | Same quality and format for similar queries |
| **Recovery** | User knows exactly what to do when the AI fails | Clear error states and recovery paths |

### The Test

```
PRINCIPLE 2 TEST — DESIGN FOR TRUST

For every AI feature, verify:

[ ] The user knows they are interacting with AI (not a human or a lookup)
[ ] The user can see where the AI output came from (citation / source)
[ ] The user can correct or override the AI output with one action
[ ] When the AI is uncertain, it says so explicitly
[ ] The user knows what to do if the AI is wrong
[ ] The AI does not present uncertain information as confirmed fact

Trust gap identified: _______________________________________________
Design change required: _______________________________________________
```

---

## Principle 3: Fail Gracefully

### The Principle

Every AI system will fail. The question is not whether but when, how often, and how badly. The teams that build excellent AI products design their failure states with the same care as their success states — because how a product behaves when the AI is wrong is what users remember longest and trust most strongly.

> **In practice:** For every AI feature, there must be a designed response for every failure mode before the feature launches. "Graceful" means the user is never stranded, never confused about what happened, and always has a path forward.

### Failure Mode Taxonomy

| Failure Type | User Experience Without Design | Designed Response |
|---|---|---|
| **Hallucination** | User acts on false information | Confidence signal + easy correction + source requirement |
| **Out of scope** | Confusing or irrelevant output | Clear "I can't help with that" + redirect to alternative |
| **Timeout / unavailability** | Blank screen or spinner forever | Async option / manual fallback / "try again" with context |
| **Low confidence** | False certainty presented to user | Explicit caveat + recommendation to verify |
| **Format failure** | Structured output breaks downstream system | Schema validation + retry with correction prompt |
| **Trust-breaking failure** | Single bad output destroys accumulated trust | Acknowledge + explain + offer correction |

### The Test

```
PRINCIPLE 3 TEST — FAIL GRACEFULLY

For every AI feature, confirm each failure mode has a designed response:

[ ] Hallucination — User sees: ___ / Can do: ___
[ ] Out of scope — User sees: ___ / Can do: ___
[ ] Timeout — User sees: ___ / Can do: ___
[ ] Low confidence — User sees: ___ / Can do: ___
[ ] Format failure — User sees: ___ / System does: ___
[ ] Persistent quality degradation — User sees: ___ / System does: ___

Launch gate: All failure modes must have designed responses before launch.
Any failure mode without a designed response is a launch blocker.
```

---

## Principle 4: Measure What Matters

### The Principle

AI products are easy to measure in ways that do not matter — clicks, sessions, time in product. They are hard to measure in ways that do — value delivered to the user, trust earned over time, quality of AI outputs in production. The AI builder's obligation is to measure what actually indicates user value, not what is easiest to instrument.

> **In practice:** The primary metric for any AI feature must capture genuine user value — not AI activity. A user who accepts an AI output without modification and acts on it has received value. A user who generates ten AI outputs and discards nine has not.

### Metric Hierarchy for AI Products

```
METRIC HIERARCHY

Tier 1 — Outcome metrics (hardest to game, highest signal)
  Did the user achieve their goal?
  Did the user act on the AI output?
  Did the AI save the user meaningful time?

Tier 2 — Quality metrics (leading indicator of outcomes)
  Was the AI output accepted without modification?
  Did the user rate the output positively?
  Was the AI output grounded in evidence?

Tier 3 — Adoption metrics (necessary but not sufficient)
  Did users use the AI feature?
  Did users return to use the AI feature again?

Tier 4 — Activity metrics (weakest signal — do not use as primary)
  How many AI interactions were generated?
  How long did users spend with the AI?
  How many times did users open the AI feature?

Rule: Primary success metric must be Tier 1 or Tier 2.
Tier 3 and Tier 4 metrics are inputs, not success criteria.
```

### The Test

```
PRINCIPLE 4 TEST — MEASURE WHAT MATTERS

For every AI feature, before launch:

[ ] Primary success metric defined: _______________________________________________
[ ] Metric tier: 1 / 2 / 3 / 4
[ ] If Tier 3 or 4: justify or change to Tier 1 or 2
[ ] Counter metric defined (prevents gaming): _______________________________________________
[ ] Measurement instrumented and validated (event firing correctly)
[ ] Baseline established before launch
[ ] Target set: _______________________________________________

If no Tier 1 or Tier 2 metric can be identified: the feature's value proposition
needs to be reconsidered. You cannot succeed at something you cannot measure.
```

---

## Principle 5: Build in the Open

### The Principle

AI products that operate as black boxes — where users cannot understand what the AI is doing or why — accumulate distrust invisibly. Transparency is not just an ethical obligation; it is a strategic advantage. Users who understand how an AI works are more likely to use it correctly, trust it appropriately, and advocate for it to others.

> **In practice:** "Build in the open" does not mean exposing system prompts or model details. It means designing the product so that users always know: that they are interacting with AI, what the AI is using to generate its response, and what the AI's confidence in that response is.

### Transparency Design Checklist

```
PRINCIPLE 5 CHECKLIST — BUILD IN THE OPEN

Disclosure:
[ ] The AI involvement is clearly disclosed in the product
[ ] AI-generated content is labelled as AI-generated
[ ] The user knows what data the AI has access to

Source transparency:
[ ] AI outputs cite their sources when grounded in documents or data
[ ] When AI uses the user's prior context, this is communicated
[ ] When AI is operating from general knowledge (no retrieval), this is stated

Limitation transparency:
[ ] The AI's topic and task limitations are communicated proactively
[ ] When the AI cannot help, it explains why and suggests an alternative
[ ] Known quality limitations are communicated before users encounter them

Feedback transparency:
[ ] The user knows how their feedback affects AI behaviour
[ ] The user knows whether and how their data is used to improve the AI
[ ] Privacy choices regarding AI data usage are clear and accessible
```

---

## Principle 6: Earn Autonomy Incrementally

### The Principle

Autonomy is the end state of an AI product that has earned user trust. It cannot be granted at launch — it must be earned through demonstrated reliability, consistent quality, and a track record of getting things right. Launching a fully autonomous AI feature on day one is not ambition; it is impatience, and it transfers risk from the product to the user.

> **In practice:** Every AI feature should launch at the minimum autonomy level required to demonstrate value, then earn increased autonomy through demonstrated performance. The autonomy ladder moves from "AI suggests, human decides" through "AI does, human reviews" to "AI does, human spots-checks."

### The Autonomy Ladder

```
AUTONOMY LADDER

Level 1 — Suggestion
  AI surfaces an option. Human makes the decision and takes the action.
  User risk: Low. AI error: Easily caught.
  Example: AI suggests a reply; user sends it manually.

Level 2 — Draft
  AI produces a draft. Human reviews and can modify before action.
  User risk: Low-Medium. AI error: Caught in review.
  Example: AI drafts a meeting summary; user edits and shares.

Level 3 — Assisted action
  AI takes an action with user confirmation step.
  User risk: Medium. AI error: Caught at confirmation.
  Example: AI proposes a calendar event; user approves with one click.

Level 4 — Supervised autonomy
  AI takes action without confirmation; human receives notification and can undo.
  User risk: Medium-High. AI error: Caught in notification review.
  Example: AI sends a draft email; user has 5 minutes to cancel.

Level 5 — Full autonomy
  AI takes action without human review. Human sees the outcome.
  User risk: High. AI error: Discovered after the fact.
  Example: AI autonomously manages a workflow end-to-end.

RULE: Start at the lowest viable autonomy level.
Advance only when: quality metrics are stable + user acceptance rate is high
+ no critical errors have occurred at the current level for [N weeks].
```

### The Test

```
PRINCIPLE 6 TEST — EARN AUTONOMY INCREMENTALLY

Current autonomy level: ___
Target autonomy level: ___

Gate criteria for advancing one level:
[ ] Quality score > ___ for ___ consecutive weeks
[ ] User acceptance rate > ___%
[ ] Zero critical errors in the past ___ weeks
[ ] User feedback sentiment > ___

Current status: Ready to advance / Not yet ready
Evidence: _______________________________________________
```

---

## Principle 7: Protect the Human in the Loop

### The Principle

As AI systems become more capable and more autonomous, the temptation is to remove humans from the loop entirely. This is wrong — not because AI cannot be accurate, but because the consequences of AI errors are borne by humans, not by the AI. Wherever the stakes of an AI error are significant, a human must be able to understand, verify, and override what the AI has done.

> **In practice:** "Human in the loop" does not mean every AI output requires human approval. It means: for every category of consequential AI action, there is a defined checkpoint where a human can review, correct, or override before the action becomes irreversible.

### Human-in-the-Loop Design

```
HITL DESIGN FRAMEWORK

Step 1 — Identify consequential AI actions
  What AI actions in this product have significant consequences if wrong?
  Examples: sending a communication, changing a record, making a financial decision,
  providing medical or legal information, taking an autonomous action on behalf of the user.

Step 2 — Rate consequence severity
  High: Irreversible, significant impact on user or third parties
  Medium: Reversible with effort, moderate impact
  Low: Easily reversible, minor impact

Step 3 — Assign HITL requirement
  High consequence → Human approval before action
  Medium consequence → Human notification with undo window
  Low consequence → Human can review in audit log

Step 4 — Design the HITL experience
  What does the human see at the checkpoint?
  What decision are they making?
  How long do they have to decide?
  What is the default if they do not respond?

Step 5 — Test the HITL experience
  Does the human understand what they are approving?
  Is the information presented sufficient to make an informed decision?
  Is the decision presented at the right level of abstraction?
```

---

## Principle 8: Ship to Learn, Not to Finish

### The Principle

An AI product is never finished. The model will change. The user base will evolve. The competitive landscape will shift. New capabilities will emerge. The teams that build the best AI products are the ones that treat every launch as the beginning of a learning cycle — not the end of a build cycle.

> **In practice:** Every AI launch includes a learning plan: what hypotheses will this launch test? What will we measure? How will we incorporate findings into the next iteration? A launch without a learning plan is a deployment, not a product decision.

### The Learning Launch Protocol

```
LEARNING LAUNCH PROTOCOL

Before launch, define:

Hypotheses this launch will test:
  H1: We believe [user] will [behaviour] because [insight]. We will know if we're right when [metric].
  H2: _______________________________________________

What we will measure:
  Primary: _______________________________________________
  Quality: _______________________________________________
  Trust indicators: _______________________________________________

What we will do with the findings:
  If H1 is confirmed: _______________________________________________
  If H1 is invalidated: _______________________________________________
  Review date: _______________________________________________

Learning cadence:
  Week 1: Intensive monitoring — daily metric review
  Week 2–4: Standard monitoring — weekly metric review
  Day 30: 30-day review — full learning synthesis
  Day 90: 90-day review — strategic implications
```

---

## Applying the Principles

### Principles in Practice — Decision Checklist

```
AI DECISION PRINCIPLES CHECKLIST

Apply this to every significant AI product decision:

[ ] Principle 1: Is this solving a validated human problem (not just using available technology)?
[ ] Principle 2: Does the design build trust — transparency, control, and recovery?
[ ] Principle 3: Are all failure modes designed? Is the failure path as good as the success path?
[ ] Principle 4: Is the primary metric capturing genuine user value (Tier 1 or 2)?
[ ] Principle 5: Does the user know what the AI is doing, why, and how confident it is?
[ ] Principle 6: Is the autonomy level appropriate for the current maturity of the AI?
[ ] Principle 7: Are high-consequence AI actions protected by human review?
[ ] Principle 8: Does this launch have a learning plan — hypotheses, metrics, and review dates?

Any unchecked box is a gap that must be addressed before launch.
```

### Principles Conflict Resolution

Sometimes principles create tension with each other. Use this framework:

| Conflict | Resolution |
|---|---|
| Principle 1 (human problem) vs speed to market | Human problem always wins. Building without validation creates waste, not speed. |
| Principle 2 (trust) vs simplicity of UX | Trust is a product feature. Transparency that increases cognitive load must be redesigned, not removed. |
| Principle 6 (earn autonomy) vs competitive pressure | Autonomy without trust track record destroys the moat. Build trust before building autonomy. |
| Principle 7 (human in loop) vs efficiency | Efficiency is not served by AI errors. HITL cost is a fraction of the cost of a trust failure. |
| Principle 8 (ship to learn) vs perfectionism | Ship at the minimum quality threshold. Learning requires real user signal — staging cannot provide it. |

---

## Templates

### Template A: Principles Review Card

```
# AI Builder Principles Review
Feature: _______________________________________________  |  Date: ___

P1 Human problem: Validated / Not yet validated
  Evidence: _______________________________________________

P2 Trust design: Complete / Gaps identified
  Gaps: _______________________________________________

P3 Graceful failure: All modes designed / Gaps
  Undesigned modes: _______________________________________________

P4 Meaningful metrics: Tier 1–2 metric / Tier 3–4 only
  Primary metric: _______________________________________________

P5 Transparent: Yes / Partially / No
  Gap: _______________________________________________

P6 Appropriate autonomy: Level ___ / Justified
  Justification: _______________________________________________

P7 Human protected: Yes / Not needed / Gap
  High-consequence action unprotected: _______________________________________________

P8 Learning plan: Yes / No
  Hypotheses: _______________________________________________

OVERALL: Ready to launch / Gaps must be addressed
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| "AI for AI's sake" — building AI features because the technology exists | Validate the human problem before any development begins |
| Measuring AI success with activity metrics (interactions, sessions) | Measure with outcome metrics (value delivered, trust earned) |
| Launching at full autonomy from day one | Start at suggestion level; earn autonomy through demonstrated quality |
| Treating failure states as an afterthought | Design failure states before building success states |
| Black-box AI that users cannot understand or control | Every AI output must be explainable, correctable, and overrideable |
| Launching without a learning plan | Every launch is a hypothesis — define what you expect to learn before shipping |
| Removing human oversight to increase efficiency | Maintain HITL for consequential actions; efficiency at the cost of trust is a trap |
| Principles as wall art — aspirational but not operational | Apply principles to every product decision; track violations and learn from them |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Principles review on new features | Per feature, before launch | PM |
| Principles retrospective on incidents | After every P1/P2 AI incident | PM + team |
| Team principles alignment session | Quarterly | PM + full team |
| Principles document refresh | Annually | CPO + PM leads |
| New team member principles onboarding | On each new hire | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Apply the AI Builder Principles to a Feature Decision

> **Best for:** Evaluating any AI product decision against all eight principles before committing to build.

```
You are an AI product ethics and quality advisor. Help me apply the eight AI Builder Principles to a product decision I am about to make.

For each principle, evaluate my decision:

1. Start With the Human Problem — Is there a validated human problem? Is AI the right solution?
2. Design for Trust — Does the design include transparency, control, and recovery paths?
3. Fail Gracefully — Are all failure modes identified and designed?
4. Measure What Matters — Is the primary metric a genuine value indicator (Tier 1 or 2)?
5. Build in the Open — Does the user understand what the AI is doing and why?
6. Earn Autonomy Incrementally — Is the autonomy level appropriate for current trust level?
7. Protect the Human in the Loop — Are high-consequence actions protected by human review?
8. Ship to Learn — Is there a learning plan with hypotheses and measurement?

For each principle:
- Rate compliance: Strong / Partial / Weak / Not addressed
- Identify the specific gap (if any)
- Recommend the specific change that would address the gap

After all eight principles:
- Identify the top 2 gaps that must be resolved before launch
- Identify any gap that should block launch entirely
- Write the principles review card for this feature

My feature decision: [describe what you are planning to build or change]
Current design state: [describe what has been designed so far]
Launch timeline: [when are you planning to launch?]
```

---

### Prompt 2 — Design the Trust Layer for an AI Feature

> **Best for:** Applying Principle 2 in depth — systematically designing transparency, control, and confidence communication into an AI feature.

```
You are a trust-centred AI designer helping me build the trust layer for my AI feature.

Design the trust components across six dimensions:

1. Transparency — what does the user need to know about what the AI is doing?
   - Write the disclosure text that should appear when the AI feature is first encountered
   - Design the ongoing transparency signals (what does the user see with each AI output?)

2. Calibrated confidence — how does the AI communicate uncertainty?
   - Design the confidence signal for high / medium / low confidence outputs
   - Write the uncertainty caveat text for each confidence level
   - Identify the threshold below which the AI must explicitly caveat its output

3. Controllability — how does the user modify, correct, or override the AI?
   - Design the edit / override / reject control for AI outputs
   - How does the user regenerate an output they are unhappy with?
   - How does the user signal that an output is wrong (for quality improvement)?

4. Explainability — how does the user understand why the AI produced this output?
   - Design the "why" explanation experience (one click? always visible? on request?)
   - Write the explanation format template

5. Consistency — how do we ensure the AI behaves predictably?
   - What quality monitoring confirms consistent behaviour?
   - How do we handle inconsistency when detected?

6. Recovery — what does the user do when the AI is wrong?
   - Design the correction flow
   - Design the "start over" flow
   - Write the recovery path copy

After all six dimensions:
- Identify the trust element most likely to determine adoption for my specific user
- Write the trust design requirements for the AI PRD section

My AI feature: [describe what the AI does]
Target user's AI literacy: [naive / curious / confident / expert]
Stakes of AI errors for this user: [low / medium / high — describe]
```

---

### Prompt 3 — Design the Autonomy Roadmap

> **Best for:** Applying Principle 6 — planning how an AI feature will earn increasing autonomy over time through demonstrated quality.

```
You are an AI product strategy advisor helping me design the autonomy roadmap for my AI feature.

Map the autonomy progression from launch through full autonomy:

1. Current appropriate autonomy level
   Given my feature's quality maturity and user trust level, which autonomy level is appropriate at launch?
   Level 1 (suggest) / Level 2 (draft) / Level 3 (assisted action) / Level 4 (supervised) / Level 5 (full)
   Justify the recommendation.

2. Advancement criteria for each level transition
   For each level from my launch level through the target level:
   - What quality metrics must be sustained for how long?
   - What user acceptance rate must be maintained?
   - What incident-free period is required?
   - Who makes the decision to advance?

3. User experience at each level
   - What does the user see and do at Level [X]?
   - How does the interface change when advancing from Level [X] to Level [X+1]?
   - How is the autonomy increase communicated to the user?

4. Rollback criteria
   - Under what circumstances would we reduce autonomy (move back a level)?
   - What metric threshold triggers a rollback to lower autonomy?

5. Timeline projection
   Given my current quality metrics, when might I realistically advance to each level?

My AI feature: [describe]
Current quality score: ___
User acceptance rate: ___% 
Time since launch: ___
Any incidents at current level: [describe]
Target autonomy level (12 months): Level ___
```

---

### Prompt 4 — Run a Principles Retrospective on an AI Incident

> **Best for:** After any AI product failure — using the principles framework to identify which principle was violated and what to change.

```
You are an AI product quality analyst helping me run a principles retrospective on an AI incident.

For the incident I describe, identify which principles were violated and what changes are required:

1. Principle audit
   For each of the eight principles, assess:
   - Was this principle upheld in the design and operation of the feature?
   - Did a violation of this principle contribute to the incident?
   - Rate: Upheld / Partially upheld / Violated / Not applicable

2. Root cause identification
   - Which principle violation was the primary root cause?
   - Which violations were contributing factors?
   - Was the violation in design, build, or operation?

3. Systemic pattern identification
   - Is this the first time this principle has been violated, or a pattern?
   - Is the violation limited to this feature or systemic across the product?

4. Remediation design
   For the primary principle violation:
   - What specific design change prevents this violation?
   - What process change prevents this violation?
   - What monitoring would detect this violation early in future?

5. Principle reinforcement
   - Does this incident suggest any principle should be strengthened or made more specific?
   - What addition to the principles checklist would prevent this incident from recurring?

The incident: [describe what happened — what the AI did, who was affected, what the impact was]
Feature context: [describe the AI feature and its design]
What was designed: [what failure states, guardrails, and monitoring were in place]
Timeline: [when was it discovered and how?]
```

---

### Prompt 5 — Create a Team Principles Alignment Session

> **Best for:** Aligning a new or existing team on the AI Builder Principles — making them real, operational, and shared.

```
You are a product team facilitator helping me design and run a principles alignment session for my AI product team.

Design the complete 2-hour session:

1. Opening exercise (20 minutes)
   Design an exercise that helps the team experience why each principle matters — not just read it.
   Make it concrete: use a real or realistic AI product scenario.

2. Principles in our context (40 minutes)
   For our specific product, what does each principle look like in practice?
   Design a group exercise where the team translates each abstract principle into:
   - A specific "do this" example from our product
   - A specific "don't do this" example from our product

3. Conflict and tradeoff discussion (20 minutes)
   Present 2–3 scenarios where principles conflict.
   Facilitate the team discussion on how to resolve them.
   Document the agreed resolution approach.

4. Principles checklist review (20 minutes)
   Walk through the principles checklist and adapt it to our product and team context.
   What additions make it more specific to us?
   What items are not relevant and should be removed?

5. Commitment and accountability (20 minutes)
   How does the team hold itself accountable to these principles?
   Who reviews the principles checklist on new features?
   What happens when a principle is violated?

After the session design:
- Write the facilitator notes for each exercise
- Write the pre-reading material to send 48 hours before the session
- Write the post-session summary template

My team: [describe — size, roles, AI experience level]
Product context: [what AI product or feature are we building?]
Known tensions or disagreements in the team: [any existing conflicts on approach]
Session goals: [what do you want the team to leave with?]
```
