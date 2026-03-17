# 🧭 Product Principles — AI Product Builder Playbook

> **The foundational principles that define how great products are conceived, built, and evolved — applicable across all product types and stages**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [Principle 1: Users Over Stakeholders](#principle-1-users-over-stakeholders)
- [Principle 2: Outcomes Over Outputs](#principle-2-outcomes-over-outputs)
- [Principle 3: Evidence Over Opinion](#principle-3-evidence-over-opinion)
- [Principle 4: Simple Over Clever](#principle-4-simple-over-clever)
- [Principle 5: Now Over Perfect](#principle-5-now-over-perfect)
- [Principle 6: Focus Over Breadth](#principle-6-focus-over-breadth)
- [Principle 7: Systems Over Features](#principle-7-systems-over-features)
- [Principle 8: Honesty Over Comfort](#principle-8-honesty-over-comfort)
- [Applying the Principles](#applying-the-principles)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Product principles are not values. Values describe what you believe. Principles describe how you act. A value says "we care about users." A principle says "when user needs conflict with stakeholder requests, user needs win." Principles are operational — they produce different decisions than the absence of principles would.

> **Core Principle (meta-principle):** Principles earn their place by being tested. The measure of a principle is not how much the team agrees with it when things are easy — it is whether the team honours it when it is inconvenient, costly, or unpopular. A principle that is never tested is a preference, not a principle.

These eight principles are distilled from the practice of building products that users choose, return to, and recommend — across industries, team sizes, and technological contexts. They are deliberately uncomfortable in places, because the comfortable version of each principle is already how most teams think. These are the harder, more honest versions.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Starting a new product or team — establishing shared philosophy | 🔴 Critical — principles before roadmap |
| Team disagreement about a product decision | 🔴 Critical — principles resolve disputes |
| A product is struggling despite strong execution | 🟠 High — principle violation is often the cause |
| Onboarding new team members — what does good look like here? | 🟠 High |
| Retrospective on a shipped feature that underperformed | 🟡 Medium |
| Annual team alignment — are we still building the right way? | 🟡 Medium |

---

## Principle 1: Users Over Stakeholders

### The Principle

When user needs conflict with stakeholder preferences, user needs win. This does not mean stakeholders are ignored — it means their requests are evaluated through the lens of what they produce for users, not what they produce for stakeholders. A stakeholder request that cannot be connected to a user benefit is not a product requirement. It is a business request that deserves a different answer.

> **In practice:** Before implementing any stakeholder request, the PM must be able to answer: "How does this create value for the user?" If the answer is "it doesn't — it creates value for the business," the product team's job is to find a version that does both, or to push back on the request.

### What This Looks Like

| Applies Principle | Violates Principle |
|---|---|
| CEO requests a dashboard feature; PM asks who the user is and what they need, then designs a version that serves both | PM implements the dashboard exactly as the CEO described without validating user need |
| Enterprise customer requests a feature; PM investigates whether it reflects a broader user need before building | PM adds the feature to the roadmap because the customer is large |
| Sales team wants a feature to close a deal; PM validates whether the feature would serve other users and prioritises accordingly | PM fast-tracks the feature because it affects a revenue target |

### The Test

```
PRINCIPLE 1 TEST — USERS OVER STAKEHOLDERS

For any stakeholder-originated request:

1. Who is the user this serves? (Be specific — not "the customer")
   _______________________________________________

2. What user problem does it solve? (Not "what does the stakeholder want?")
   _______________________________________________

3. How many users experience this problem?
   _______________________________________________

4. Is there evidence the user has this problem? (Not just that the stakeholder believes they do)
   _______________________________________________

5. If we build this, does it make the product meaningfully better for users?
   Yes → Proceed  |  Unclear → Research first  |  No → Push back with evidence
```

---

## Principle 2: Outcomes Over Outputs

### The Principle

The product team's job is not to ship features. It is to improve user lives and advance business outcomes. Features are the means — outcomes are the end. A team that ships every feature on time but moves no metric is failing at product management, not succeeding at it.

> **In practice:** Every item on the roadmap must have an associated outcome — a specific metric it is expected to move. If the outcome cannot be specified before building, the item is not ready for the roadmap. If the outcome is not measured after shipping, the learning opportunity is wasted.

### Outcomes Framework

```
OUTCOMES FRAMEWORK

For every roadmap item, complete before building:

Feature: _______________________________________________
User outcome: "After this ships, users will be able to [do something they couldn't before / do something faster / do something better]."
Business outcome: "This will move [metric] from [X] to [Y]."
Evidence this will work: _______________________________________________
How we will know it worked: _______________________________________________

If you cannot complete this framework: the item is not ready for the roadmap.

Shipped features without measured outcomes represent lost learning.
The minimum standard is: measure the primary outcome 30 days after launch.
```

---

## Principle 3: Evidence Over Opinion

### The Principle

In a product debate, evidence outranks opinion — regardless of who holds the opinion. The most junior PM with a user interview is epistemically superior to the most senior executive with a hunch. This is not disrespectful; it is how good products are built. The team's job is to seek evidence before forming opinions, and to update opinions when evidence contradicts them.

> **In practice:** "I think" and "I believe" are acceptable starting points for a hypothesis. They are not acceptable as endpoints for a product decision. Every claim made in a product context should be followed by the question: "What evidence do we have for this?"

### Evidence Quality Hierarchy

| Evidence Type | Quality | Weight |
|---|---|---|
| **Controlled experiment** (A/B test) | Highest — proves causation | Decisive |
| **Cohort analysis** | High — shows correlation | Strong |
| **User interviews** (8+) | High — reveals motivation | Strong for qualitative |
| **Analytics + quantitative data** | Medium — shows behaviour | Corroborating |
| **Observational research** | Medium — shows context | Corroborating |
| **Single customer feedback** | Low — one data point | Hypothesis-generating |
| **Expert opinion** | Low-medium — expertise without user data | Hypothesis-generating |
| **Team intuition** | Lowest — may be right, but unchecked | Starting point only |

### The Test

```
PRINCIPLE 3 TEST — EVIDENCE OVER OPINION

For any product claim that is influencing a decision:

1. What type of evidence supports this claim?
   [Use the hierarchy above]

2. What is the sample size? (For user research)
   _______________________________________________

3. Is the evidence representative of the target user? (Not just early adopters or vocal customers)
   _______________________________________________

4. What evidence would change this conclusion?
   _______________________________________________

5. Has anyone looked for contradicting evidence?
   _______________________________________________

A claim with no evidence above "team intuition" is a hypothesis — not a conclusion.
Label it as such and design a way to validate it before committing resources.
```

---

## Principle 4: Simple Over Clever

### The Principle

The best product solution is the simplest one that solves the problem. Complexity is not sophistication — it is risk. Complex features are harder to build, harder to maintain, harder to explain, and harder for users to adopt. Every layer of complexity added to a product is a layer of friction added to the user experience.

> **In practice:** When evaluating solutions, always ask: "What is the simplest version of this that still solves the problem?" Then ask it again. And once more. The first answer is almost never the simplest viable solution.

### Simplicity Principles

```
SIMPLICITY CHECKLIST

Before finalising any feature design:

[ ] Could the user accomplish the same outcome with fewer steps?
[ ] Is every element in the design doing meaningful work? (Remove anything that isn't)
[ ] Is the default state the right state for most users? (Do not make users configure)
[ ] Could this feature be explained to the user in one sentence?
[ ] Is the cognitive load appropriate for the user's context?
[ ] Have we considered whether this feature should exist at all?

For AI features specifically:
[ ] Is the AI interaction the simplest possible way to achieve the outcome?
[ ] Is the AI output presented in a way that requires no interpretation?
[ ] Does the AI response get to the point without unnecessary preamble?

The most powerful simplicity question: "What if we removed this entirely?"
If the honest answer is "most users would not notice," remove it.
```

---

## Principle 5: Now Over Perfect

### The Principle

A good product shipped and learned from is worth more than a perfect product that never ships. The purpose of shipping is not to declare the feature finished — it is to gain access to real-world signal that staging environments cannot provide. Perfectionism before launch is not quality control; it is fear management at the cost of learning.

> **In practice:** This principle does not mean shipping broken products or ignoring quality. It means identifying the minimum quality threshold that creates genuine value — and shipping at that threshold, not at perfection. The remaining quality gap is a product backlog item, not a launch blocker.

### Quality Threshold Framework

```
QUALITY THRESHOLD FRAMEWORK

Before launch, define the minimum quality threshold explicitly:

Core experience quality (non-negotiable):
[ ] The core user flow works end-to-end without errors
[ ] The primary value proposition is deliverable at launch quality
[ ] Critical failure modes are handled gracefully

Known gaps at launch (acceptable):
[ ] [Gap 1] — Impact: [low / medium / high] — Plan: _______________________________________________
[ ] [Gap 2] — Impact: ___  — Plan: _______________________________________________

Launch gate:
[ ] Core quality threshold is met
[ ] All known gaps are documented with a post-launch plan
[ ] The learning we will gain from shipping exceeds the cost of the known gaps

Post-launch iteration plan:
[ ] Week 1 learning: _______________________________________________
[ ] Gap 1 addressed by: _______________________________________________
[ ] Gap 2 addressed by: _______________________________________________
```

---

## Principle 6: Focus Over Breadth

### The Principle

A product that does one thing brilliantly beats a product that does ten things adequately. Focus is the discipline of saying no to things that are good so you can say yes to things that are great. The hardest product decisions are not between a good idea and a bad idea — they are between a good idea and a better idea.

> **In practice:** The North Star metric is the tool for enforcing focus. Every feature should be evaluated against a single question: does this move our North Star? If it doesn't, it needs extraordinary justification to make the roadmap. Most of the time, it should not.

### Focus Test

```
FOCUS TEST

For any proposed roadmap addition:

1. Does this directly move our North Star metric?
   Yes → Strong case for inclusion
   Indirectly → Needs explicit connection to a strategic pillar
   No → Requires extraordinary justification

2. What are we NOT building in order to build this?
   [Name the specific item(s) being displaced from the roadmap]

3. Is the proposed addition higher leverage than what it displaces?
   Yes → Proceed with tradeoff explicit
   Unclear → Do not add until the comparison is resolved
   No → Reject the addition; maintain current priority

4. Does this serve our primary persona — or a different one?
   Primary persona → Proceed (subject to other criteria)
   Different persona → Requires explicit decision to expand scope

The question that enforces focus: "What is the one thing, if we did it brilliantly,
that would move our North Star more than anything else?"
Do that. Do it completely. Then consider what's next.
```

---

## Principle 7: Systems Over Features

### The Principle

Features solve problems. Systems prevent them. The highest-leverage product work creates infrastructure that makes future features easier, faster, and better — not just the next feature. A team that only ships features is on a treadmill. A team that also invests in systems is building compounding advantage.

> **In practice:** Every quarter, some portion of the roadmap should be explicitly dedicated to system investments — not features, but the architecture, infrastructure, and foundations that make everything else better. For AI products, this includes evaluation infrastructure, monitoring systems, and the data pipelines that power future AI capabilities.

### System vs Feature Investment

```
SYSTEM vs FEATURE DECISION FRAMEWORK

System investment is justified when:
[ ] Multiple future features depend on this foundation
[ ] The current approach has a ceiling that prevents product improvement
[ ] Technical debt is actively slowing feature delivery
[ ] AI quality improvements are limited by evaluation infrastructure gaps

System investment targets:
  Early stage: 10–15% of engineering capacity
  Growth stage: 15–25% of engineering capacity
  Scale stage: 20–30% of engineering capacity

Example system investments:
  Data pipeline that enables all future AI features
  Evaluation infrastructure that enables AI quality measurement
  Component library that accelerates design consistency
  Analytics foundation that enables faster learning
  Permission system that enables enterprise expansion
```

---

## Principle 8: Honesty Over Comfort

### The Principle

Product teams that tell each other and their stakeholders what they want to hear — instead of what is true — build the wrong things confidently. Honesty in product requires courage: the courage to say that a metric is not moving, that a hypothesis was wrong, that a beloved feature is not being used, that the AI quality is not good enough to ship. Comfortable dishonesty is the most common root cause of product failure.

> **In practice:** Honesty over comfort means: data is shared even when it's bad. Experiments are reported even when they fail. Roadmap items are acknowledged as not working. Users are told the truth about what a product can and cannot do. The standard is not brutal honesty — it is caring honesty, delivered with respect and a plan.

### Honesty Standards

```
HONESTY STANDARDS CHECKLIST

Data reporting:
[ ] Negative results from experiments are shared as widely as positive ones
[ ] Metrics that are not moving are reported alongside metrics that are
[ ] Root cause analysis is honest, even when the cause is a product decision we made

Stakeholder communication:
[ ] Launch timelines are communicated with honest confidence levels (not just what people want to hear)
[ ] When a feature is not working, this is said clearly — not softened into "early days"
[ ] When a hypothesis is invalidated, the team says "we were wrong" — not "we learned something"

User honesty:
[ ] The product does not imply capabilities it does not have
[ ] AI limitations are communicated proactively, not discovered by users
[ ] Pricing and terms are presented without ambiguity

Internal honesty:
[ ] The PM says "I don't know" when they don't know
[ ] "This feature is not performing" is said out loud in team reviews
[ ] Decisions are owned even when they turn out to be wrong
```

---

## Applying the Principles

### Principles Priority Hierarchy

When principles conflict, apply this hierarchy:

```
PRINCIPLES CONFLICT RESOLUTION

1. Users Over Stakeholders — always
2. Evidence Over Opinion — always
3. Outcomes Over Outputs — always

When the above three agree, the other principles guide execution:
4. Simple Over Clever
5. Focus Over Breadth
6. Now Over Perfect
7. Systems Over Features
8. Honesty Over Comfort

Example conflicts:
P5 (Now) vs P4 (Simple): If simplification would meaningfully delay the launch,
ship the slightly less simple version and simplify post-launch. Now wins.

P6 (Focus) vs P7 (Systems): If a system investment would enable the North Star
metric more than a feature would, the system is the focused choice. Systems win.

P8 (Honesty) vs comfort: Honesty always wins. The question is delivery, not truth.
```

---

## Templates

### Template A: Product Principles Review

```
# Product Principles Review
Decision / Feature: _______________________________________________
Date: ___  |  Reviewer: ___

P1 Users Over Stakeholders: Applying / Tension / Violation
  Evidence: _______________________________________________

P2 Outcomes Over Outputs: Outcome defined / Undefined
  Outcome: _______________________________________________

P3 Evidence Over Opinion: Evidence type: ___ / Opinion only
  Evidence: _______________________________________________

P4 Simple Over Clever: Simplest viable / Unnecessary complexity
  Simplification opportunity: _______________________________________________

P5 Now Over Perfect: At quality threshold / Perfectionism risk
  Known gaps: _______________________________________________

P6 Focus Over Breadth: Serves North Star / Scope creep
  North Star connection: _______________________________________________

P7 Systems Over Features: Feature / System / Balanced
  System component (if any): _______________________________________________

P8 Honesty Over Comfort: Honest / Softened truth
  What is being understated: _______________________________________________

Overall: Principles strong / Gaps to address
Top priority: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Principles as inspiration quotes, not decision tools | Apply the test for each principle to every significant decision |
| Treating all eight principles as equally important in every situation | Know the hierarchy — some principles always outrank others |
| "Evidence" that is one customer's opinion | Evidence requires multiple data points; label single points as hypotheses |
| Shipping prematurely under the guise of "Now Over Perfect" | "Now" means at minimum quality threshold — not broken |
| "Simple" used to justify under-investing in important capabilities | Simplicity is about cognitive load for users, not engineering shortcuts |
| Outcomes defined after features are built | Define the outcome before building — the feature may be wrong |
| Softening bad data in stakeholder presentations | Honest data with a plan is always more credible than comfortable data without one |
| Principles reviewed only when things go wrong | Apply principles proactively — before decisions, not just in retrospectives |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Principles review on new features | Per feature | PM |
| Team principles discussion | Quarterly | PM + full team |
| Principles document refresh | Annually | CPO + PM leads |
| Onboarding — principles introduction | Each new hire | PM |
| Retrospective — which principles applied? | After major launches | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Apply Product Principles to a Decision

> **Best for:** Stress-testing any product decision against all eight principles before committing.

```
You are a product strategy advisor helping me apply the eight Product Principles to a decision.

For each principle, evaluate my decision:

1. Users Over Stakeholders — whose interests is this primarily serving?
2. Outcomes Over Outputs — what metric will this move, and how do I know?
3. Evidence Over Opinion — what evidence supports this, and what is the evidence quality?
4. Simple Over Clever — is this the simplest solution that solves the problem?
5. Now Over Perfect — am I at the right quality threshold to ship, or am I holding back for perfection?
6. Focus Over Breadth — does this move my North Star, or does it scatter focus?
7. Systems Over Features — is there a system investment that would be higher leverage?
8. Honesty Over Comfort — am I being fully honest about the risks and limitations?

For each principle:
- Rate: Applying strongly / Some tension / Clear violation
- Identify the specific gap or conflict
- Recommend the change that would bring this decision into alignment

After all eight:
- Identify the top 2 principles being violated
- Write the revised decision that better honours all eight principles
- Identify any principle I should explicitly override for this decision (and justify why)

My decision: [describe what you are considering]
Context: [product stage, user segment, strategic priority]
Stakeholder pressures: [any external pressures influencing the decision]
```

---

### Prompt 2 — Define Product Principles for a New Team

> **Best for:** Establishing the product philosophy for a new team or product — making principles specific enough to actually guide decisions.

```
You are a product leadership coach helping me define working product principles for my team.

The principles I need are not aspirational values — they are operational guidelines that produce different decisions than their absence would.

For each of the eight core product principles, help me:
1. Make it specific to my product context (not generic)
2. Write a concrete "what this looks like" example from our specific domain
3. Write a concrete "what this violates" example
4. Write the test — a question my team can ask to verify we are applying this principle
5. Identify the most likely way this principle will be violated on our team

After defining all eight:
- Identify the 2–3 principles most at risk given our team's culture and pressures
- Write the team principles card (1 page, plain language, operational)
- Design the onboarding exercise that makes these principles real for new team members

My product: [describe]
Team culture: [describe — how decisions are currently made, what pressures exist]
Known weaknesses: [where does the team currently struggle?]
Stakeholder environment: [what pressures come from outside the product team?]
```

---

### Prompt 3 — Resolve a Principles Conflict

> **Best for:** When two principles seem to point in opposite directions on a specific decision.

```
You are a product philosophy advisor helping me resolve a conflict between product principles.

I will describe a situation where two principles seem to conflict. Your job is to:

1. Diagnose the conflict
   - Is this a genuine conflict between principles, or a false conflict caused by framing?
   - Which principle is at stake on each side of the tension?

2. Apply the priority hierarchy
   - Some principles always outrank others (Users > Stakeholders; Evidence > Opinion)
   - Does the hierarchy resolve this conflict? If yes, which principle wins?

3. Find the synthesis
   - Is there a version of the decision that honours both principles?
   - What would need to change about the options for both principles to be satisfied?

4. Make the call
   - If synthesis is not possible: which principle takes precedence in this specific context and why?
   - What is the explicit trade-off being accepted?
   - How do we mitigate the downside of the principle we are overriding?

5. Document the decision
   - Write the decision record including which principles applied and how the conflict was resolved
   - What precedent does this set for future similar conflicts?

The conflict: [describe the situation and which two principles seem to conflict]
Options I am considering: [describe each option]
Stakes: [what is the cost of getting this wrong?]
```

---

### Prompt 4 — Run a Principles Retrospective

> **Best for:** After a feature launch or product failure — identifying which principles were violated and what to change.

```
You are a product retrospective facilitator helping me run a principles retrospective on a product outcome.

For the outcome I describe, assess each principle:

1. Users Over Stakeholders — did we prioritise the right people's interests?
2. Outcomes Over Outputs — did we define and measure the outcome before and after?
3. Evidence Over Opinion — what quality of evidence drove the key decisions?
4. Simple Over Clever — was the solution appropriately simple?
5. Now Over Perfect — did we ship at the right quality threshold?
6. Focus Over Breadth — did this serve our North Star, or did it scatter focus?
7. Systems Over Features — was the right balance struck between features and foundations?
8. Honesty Over Comfort — were we honest with ourselves and stakeholders throughout?

For each principle:
- Rate: Upheld / Partially upheld / Violated
- For violations: was the violation a decision, a process, or a pressure failure?
- For violations: what specifically should change going forward?

After all eight:
- Identify the root principle violation (the one that most caused the poor outcome)
- Write the one change that would have the highest impact on preventing a similar outcome
- Write the retrospective summary for the team

The outcome: [describe what happened — a feature that underperformed, a missed metric, a launch that didn't go as planned]
Context: [describe the decisions made and the pressures that influenced them]
```

---

### Prompt 5 — Write a Product Principles Document for a New Product

> **Best for:** Creating the foundational product philosophy document for a new product or team — something that will guide decisions for years.

```
You are a product philosophy writer helping me create the product principles document for my product.

Write a complete product principles document that is:
- Specific to my product context — not generic platitudes
- Operational — each principle produces different decisions than its absence
- Tested — each principle includes a question the team can use to apply it
- Honest — includes the difficult implications of each principle

Document structure:
1. Why these principles (1 paragraph — what problem they solve)
2. The eight principles — for each:
   - The principle (one sentence — uncomfortable version, not the comfortable version)
   - What this means in practice for our product specifically
   - A concrete example of applying it (from our domain)
   - A concrete example of violating it (from our domain)
   - The test question the team asks to apply it
3. How to resolve principle conflicts
4. How to onboard new team members to these principles
5. How to update these principles as the product evolves

My product: [describe]
Our users: [describe]
Our current challenges: [what decisions are hardest for us?]
Our team culture: [how do we currently make decisions?]
Stage: [early / growth / scale]
```
