# ⚖️ Product Decision Framework — AI Product Builder Playbook

> **A structured approach for making high-quality product decisions consistently, quickly, and in a way that the whole team can align behind**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Decision Model](#the-decision-model)
- [Decision Type 1: Strategic Decisions](#decision-type-1-strategic-decisions)
- [Decision Type 2: Product Decisions](#decision-type-2-product-decisions)
- [Decision Type 3: Execution Decisions](#decision-type-3-execution-decisions)
- [Decision-Making Tools](#decision-making-tools)
- [Decision Quality Standards](#decision-quality-standards)
- [AI Product Decision Considerations](#ai-product-decision-considerations)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Most product decisions are made badly — not because the people making them are bad at their jobs, but because there is no shared framework for what a good decision looks like. Some decisions happen too slowly, paralysed by the search for perfect information. Others happen too quickly, driven by the loudest voice in the room. Most happen without a clear record of what was decided, by whom, and why.

> **Core Principle:** A decision is only as good as the clarity it produces. A great product decision specifies what will be done, what will not be done, who is responsible, and what would cause us to revisit it. Without these four elements, a decision is not a decision — it is a conversation that has temporarily stopped.

For AI products, decision quality has an additional dimension: AI introduces uncertainty that traditional products do not have. Decisions about which model to use, what quality threshold to accept, or whether to launch a feature with imperfect AI behaviour require explicit reasoning about uncertainty and risk that most product decision frameworks are not designed for.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| High-stakes decision with significant resource or strategic implications | 🔴 Critical — apply full framework |
| Team is debating without converging on a decision | 🔴 Critical — facilitate using decision tools |
| A decision needs to be revisited and there is no record of the original rationale | 🟠 High — build the decision log |
| Onboarding a new team member who needs to understand prior decisions | 🟡 Medium |
| Retrospective — why did this decision not produce the expected outcome? | 🟡 Medium |

---

## The Decision Model

Product decisions fall into three types, each requiring a different level of process rigour.

```
STRATEGIC DECISIONS
  ↓ high stakes, long-term consequences, hard to reverse
  → Full decision framework + executive sign-off

PRODUCT DECISIONS
  ↓ medium stakes, affect user experience or roadmap
  → Structured decision document + PM ownership

EXECUTION DECISIONS
  ↓ low stakes, reversible, sprint-level
  → Lightweight decision log + team autonomy
```

| Decision Type | Stakes | Reversibility | Process | Who Decides |
|---|---|---|---|---|
| **Strategic** | Very high | Low | Full framework + sign-off | CPO / CEO |
| **Product** | Medium-high | Medium | Decision doc + review | PM + stakeholders |
| **Execution** | Low-medium | High | Decision log | PM or team |

> **Rule of thumb:** Spend decision-making effort proportional to the cost of reversing the decision. A decision that takes a week to reverse deserves 10 minutes of process. A decision that takes a year to reverse deserves a structured process and written rationale.

---

## Decision Type 1: Strategic Decisions

### 1.1 What Makes a Decision Strategic

A decision is strategic if it meets two or more of these criteria:

```
STRATEGIC DECISION CRITERIA

[ ] Requires > $100K in investment (or equivalent team time)
[ ] Affects the product direction for > 6 months
[ ] Is difficult or expensive to reverse
[ ] Affects multiple teams or stakeholders
[ ] Has significant customer-facing implications
[ ] Has regulatory or legal implications
[ ] Sets a precedent for future decisions

If 2+ criteria are checked: apply the full strategic decision framework.
```

### 1.2 Strategic Decision Framework

```
STRATEGIC DECISION DOCUMENT

Decision: _______________________________________________
Date: _______________  |  Deadline: _______________
Decision owner: _______________  |  Approver: _______________

CONTEXT
What situation requires this decision?
_______________________________________________

Why must a decision be made now?
_______________________________________________

PROBLEM STATEMENT
What problem are we solving? For whom?
_______________________________________________

What happens if we do not make this decision?
_______________________________________________

OPTIONS CONSIDERED
Option A: _______________________________________________
  Pros: _______________________________________________
  Cons: _______________________________________________
  Risk: _______________________________________________
  Cost: _______________________________________________

Option B: _______________________________________________
  Pros: _______________________________________________
  Cons: _______________________________________________
  Risk: _______________________________________________
  Cost: _______________________________________________

Option C (if applicable): _______________________________________________

DECISION CRITERIA
What principles or constraints should guide this decision?
1. _______________________________________________
2. _______________________________________________
3. _______________________________________________

RECOMMENDATION
Option selected: _______________________________________________
Rationale: _______________________________________________
Trade-offs accepted: _______________________________________________

WHAT WE ARE NOT DOING
_______________________________________________

REVIEW CONDITIONS
What would cause us to revisit this decision?
_______________________________________________
Review date: _______________________________________________

SIGN-OFF
[ ] Decision owner  [ ] Approver  [ ] Stakeholders notified
```

---

## Decision Type 2: Product Decisions

### 2.1 Product Decision Template

Product decisions cover the bulk of PM work — feature scope, design direction, metric targets, launch timing. These require structure but not the full strategic framework.

```
PRODUCT DECISION RECORD

Decision: _______________________________________________
Date: _______________  |  Owner: _______________
Status: Decided / Under review / Pending input from ___

THE DECISION
[1–2 sentences: what was decided]

WHY
[2–3 sentences: the reasoning, grounded in evidence or principle]

WHAT WAS NOT DECIDED (if relevant)
[1 sentence: what is explicitly out of scope or deferred]

EVIDENCE USED
[ ] User research: _______________________________________________
[ ] Analytics data: _______________________________________________
[ ] Experiment result: _______________________________________________
[ ] Expert input: _______________________________________________
[ ] First principles reasoning: _______________________________________________

STAKEHOLDERS CONSULTED
_______________________________________________

STAKEHOLDERS INFORMED
_______________________________________________

OPEN ISSUES (unresolved related questions)
_______________________________________________

REVIEW DATE (when to check if this decision is still correct)
_______________________________________________
```

### 2.2 Decision Speed Framework

Not all product decisions should take the same amount of time. Match the decision process to the stakes:

| Decision Stakes | Process | Time Budget |
|---|---|---|
| **High** (affects many users, hard to reverse) | Full decision doc + stakeholder review | 3–5 days |
| **Medium** (affects some users, reversible in one sprint) | Lightweight decision record | 1 day |
| **Low** (affects a single component, instantly reversible) | Team agreement + log entry | Same day |
| **Urgent** (customer or business crisis) | Fast decision with documented rationale; review within 48 hours | Same hour |

---

## Decision Type 3: Execution Decisions

### 3.1 Lightweight Decision Log

Execution decisions do not require a formal document — but they do require a record. A decision that is not logged will be re-litigated.

```
EXECUTION DECISION LOG ENTRY

Date: ___  |  Decision maker: ___  |  Context: ___

Decision: [1 sentence — what was decided]
Rationale: [1 sentence — why]
Implications: [1 sentence — what this means for the sprint / design / implementation]
Reversible by: [date or condition when we check if this is still right]
```

### 3.2 Decision Authority Matrix

Clarity on who decides what is the single most effective way to accelerate decision-making:

```
DECISION AUTHORITY MATRIX (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Product vision | CPO | CEO | PM leads | All teams |
| Roadmap priorities | PM lead | CPO | Eng lead, Design | All teams |
| Feature scope | PM | PM lead | Engineering | Design |
| UI/UX design | Design | PM | Users | Engineering |
| Technical architecture | Eng lead | CTO | PM | Design |
| AI model selection | AI lead + PM | CTO | Engineering | PM lead |
| Launch timing | PM | PM lead | Eng lead, CS | All |
| Pricing | PM + Finance | CPO + CFO | Sales, CS | All |
```

---

## Decision-Making Tools

### 4.1 Pre-mortem

A pre-mortem imagines that the decision has failed and works backwards to identify why. It surfaces risks that optimism bias suppresses.

```
PRE-MORTEM PROTOCOL

Setup: "It is 12 months from now. This decision has turned out to be a serious mistake.
Tell me what went wrong."

Step 1 — Silent writing (5 minutes)
Each participant independently writes everything that could have gone wrong.

Step 2 — Share and cluster (10 minutes)
Each participant reads their list. Cluster by theme.

Step 3 — Assess likelihood
For each failure mode: how likely is this? What would it take to prevent it?

Step 4 — Update the decision
Does any failure mode change the decision? Or add a mitigation to the plan?

Common pre-mortem findings for AI decisions:
- "The model was not reliable enough for this use case and users lost trust"
- "We didn't have the evaluation infrastructure to detect quality degradation"
- "The cost at scale was 5× our model — we had to pull the feature"
- "The data we needed for this AI feature turned out to be unavailable"
```

### 4.2 Reversibility Assessment

Before finalising any decision, assess how reversible it is:

```
REVERSIBILITY ASSESSMENT

If this decision turns out to be wrong:
  What is the cost to reverse it? $___  |  Time: ___
  Can users be migrated back to the prior experience? Yes / Partially / No
  Are there contractual or regulatory commitments that make reversal difficult? Yes / No

Reversibility tier:
  High: Reversible in one sprint with no user impact → Decide quickly; accept more uncertainty
  Medium: Reversible in one quarter with moderate impact → Standard decision process
  Low: Reversible in > 6 months or with significant user impact → Apply full framework; reduce uncertainty first

For low reversibility decisions: invest more time upfront to reduce regret.
```

### 4.3 The Disagree and Commit Protocol

```
DISAGREE AND COMMIT PROTOCOL

When a team member disagrees with a decision:

Step 1 — Express the disagreement
"I disagree with this decision because [specific reason, grounded in evidence or principle]."

Step 2 — Ensure it is heard
The decision owner must demonstrate they have understood the objection:
"I hear that you believe [restate concern]. Is that right?"

Step 3 — Decide
Decision owner either:
  a) Changes the decision based on the input, or
  b) Confirms the decision despite the objection, explaining why

Step 4 — Commit
The disagreeing team member commits to the decision:
"I disagree with this decision, but I will support it fully."

Step 5 — Review trigger
"If [specific condition] happens, we revisit this decision. Agreed?"

Disagree and commit is not:
  - Suppressing dissent (the objection must be heard and documented)
  - Requiring enthusiasm (commitment, not agreement)
  - Permanent (commit for a defined period or until a review condition is met)
```

---

## Decision Quality Standards

### 5.1 The Four Elements of a Quality Decision

A decision is complete when it answers all four questions:

| Question | Why It Matters | Signs It's Missing |
|---|---|---|
| **What is decided?** | Without clarity, the team executes different things | Ongoing debate about what was agreed |
| **What is not decided?** | Scope creep and adjacent decisions consume resources | Scope expands without explicit approval |
| **Who is responsible?** | Without ownership, nothing happens | Decisions made in meetings that nobody acts on |
| **What would change it?** | Without a review trigger, decisions become permanent by default | Old decisions never revisited; situation changes but decision doesn't |

### 5.2 Decision Audit

Run a quarterly decision audit to identify patterns in decision quality:

```
QUARTERLY DECISION AUDIT

Review all decisions made in the last quarter.

For each decision, check:
[ ] Was the decision documented at the time? (Yes / No)
[ ] Was the rationale recorded? (Yes / No)
[ ] Was a review date set? (Yes / No)
[ ] Has the decision been revisited as needed? (Yes / No)

Patterns to look for:
  High % undocumented decisions: Process discipline problem
  High % decisions without review dates: No accountability mechanism
  High % decisions being re-litigated: Poor initial decision quality or stakeholder alignment
  High % decisions that should have been revisited but weren't: Review triggers not working

Action for each pattern: _______________________________________________
```

---

## AI Product Decision Considerations

### 6.1 AI-Specific Decision Dimensions

Every AI product decision should explicitly address two additional questions:

```
AI DECISION CHECKLIST

1. Uncertainty acknowledgement
   "What do we not know that could change this decision?"
   AI decisions are more uncertain than traditional product decisions.
   Acknowledging uncertainty prevents overconfident commitments.

2. Quality threshold decision
   "What AI quality is acceptable for this use case?"
   This must be explicitly decided, not assumed.
   A decision to launch with 80% accuracy is fundamentally different from
   a decision to launch only at 95% accuracy.

3. Failure mode decision
   "What happens when the AI is wrong — and is this acceptable?"
   Every AI decision is also a decision about the failure experience.

4. Reversibility in the AI context
   "If the model degrades or fails, how quickly can we revert?"
   AI decisions often have lower reversibility than they appear.

5. Data dependency decision
   "Does this decision depend on data we currently have or data we need to acquire?"
   Decisions that depend on future data are actually decisions about two things.
```

### 6.2 Common AI Product Decisions and How to Make Them

| Decision | Key Considerations | Decision Owner |
|---|---|---|
| Which AI model to use | Quality benchmark + cost at scale + latency SLA + provider risk | PM + CTO |
| What quality threshold to launch at | User tolerance for errors + stakes of failure + monitoring capability | PM |
| RAG vs fine-tuning vs prompt engineering | Data availability + quality delta + cost + build complexity | PM + AI lead |
| When to add human-in-the-loop | Stakes of AI error + user trust level + cost of human review | PM + Design |
| How to handle AI hallucinations | Frequency + severity + user ability to detect | PM + Design |
| AI pricing model | Value creation type + AI cost structure + competitive landscape | PM + Finance |

---

## Templates

### Template A: Decision Log (ongoing)

```
# Product Decision Log — [Product Name]

| Date | Decision | Owner | Rationale | Evidence | Review Date |
|------|---------|-------|-----------|----------|-------------|
| | | | | | |
| | | | | | |

Review cadence: Monthly — flag any decision whose review date has passed.
```

### Template B: Decision Retrospective

```
# Decision Retrospective — [Decision Name]
Original decision date: ___  |  Retrospective date: ___

## What was decided
[Restate the original decision]

## What actually happened
[What was the outcome?]

## Was the decision correct?
[ ] Yes — outcome matched expectation
[ ] Partially — outcome was close but not exactly as predicted
[ ] No — outcome did not match; decision should have been different

## What we would do differently
[Specific changes to the decision or the decision process]

## What this means for future decisions
[Principle or rule that should guide similar decisions going forward]
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Decision by consensus (everyone must agree) | Decision by consent (one owner decides; others can disagree and commit) |
| Undocumented decisions | Every decision, even small ones, gets a log entry |
| No review dates on decisions | Every decision has a condition or date when it is revisited |
| HiPPO (Highest Paid Person's Opinion) decides | Framework and evidence decide; seniority does not override |
| Decision by committee (no clear owner) | One named decision owner; others are consulted or informed |
| Reversible decisions treated as permanent | Fast, reversible decisions should be made quickly and reviewed soon |
| AI decisions without quality threshold | Always specify the minimum acceptable AI quality as part of the decision |
| Re-litigating decided issues without new evidence | Disagree and commit; only re-open with new evidence |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Decision log review | Monthly | PM |
| Decision authority matrix review | Quarterly | PM + CPO |
| Decision retrospective on major decisions | At 3-month mark | PM |
| Pre-mortem on high-stakes decisions | Before finalising | PM + stakeholders |
| Decision audit | Quarterly | PM |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Structure a Complex Product Decision

> **Best for:** Any high-stakes decision where the options are unclear, the stakes are high, or stakeholder alignment is needed.

```
You are a product strategy advisor helping me structure and document a complex product decision.

Guide me through the full strategic decision framework:

1. Context setting
   - Why does this decision need to be made now?
   - What happens if we delay or avoid the decision?
   - Is this a strategic, product, or execution decision? (helps set the right process level)

2. Problem framing
   - What is the actual problem we are solving? (not the solution we are choosing between)
   - Who is affected by this decision and how?

3. Options generation
   - Generate 3–4 distinct options, including the status quo
   - For each: what are the pros, cons, risks, and costs?
   - Is there an option we haven't considered?

4. Decision criteria
   - What principles should guide this decision?
   - What constraints cannot be violated?
   - How do we weight competing considerations?

5. Recommendation
   - Given the above, which option do you recommend?
   - What trade-offs are we explicitly accepting?
   - What are we explicitly not doing?
   - Under what conditions should we revisit this decision?

6. Pre-mortem
   - If this decision turns out to be wrong in 12 months, what most likely went wrong?
   - Does any failure mode change the recommendation?

Decision I need to make: [describe the situation and the options you are aware of]
Key constraints: [budget, timeline, team, regulatory]
Stakeholders who must be aligned: [list roles]
```

---

### Prompt 2 — Run a Pre-Mortem on a Decision

> **Best for:** Before finalising any significant decision — imagining failure to surface risks that optimism is hiding.

```
You are a risk analyst helping me run a pre-mortem on a product decision I am about to make.

Imagine it is 12 months from now and this decision has turned out to be a serious mistake. Walk me through the most likely failure scenarios.

For each failure scenario:
1. Describe specifically what went wrong
2. Rate the likelihood: High / Medium / Low
3. Identify the early warning signal — what would I see in the first 30–90 days that predicted this failure?
4. Recommend a specific mitigation I can build into the decision or implementation

Categories to explore:
- User adoption failure: users don't use what we built, or use it differently than expected
- Technical failure: the solution doesn't work as reliably as expected
- AI quality failure (if applicable): the AI produces outputs that damage user trust
- Resource failure: the project takes longer or costs more than planned
- Market failure: the competitive or market context changes, making the decision wrong
- Organisational failure: the team can't execute or align behind the decision

After all scenarios:
- Identify the top 2 risks that should change the decision or add a mitigation plan
- Identify what evidence in the next 30 days would signal we are on the right track

My decision: [describe what you are about to decide]
Options I am choosing between: [describe]
My current leaning: [which option and why]
```

---

### Prompt 3 — Resolve a Team Decision Deadlock

> **Best for:** When a team has been debating a decision without converging — needing a structured process to reach a conclusion.

```
You are a facilitation expert helping me resolve a team decision deadlock.

I will describe the decision, the competing positions, and the arguments made by each side. Your job is to:

1. Diagnose the deadlock
   - Is this a values disagreement (different things matter to each person)?
   - Is this an information disagreement (people have different facts)?
   - Is this a prediction disagreement (people believe different things will happen)?
   - Or is this a process disagreement (people want different levels of certainty before deciding)?

2. Find the common ground
   - What do all parties actually agree on?
   - What is the shared goal beneath the competing positions?

3. Reframe the decision
   - Is there a way to reframe the decision that gives both positions something they care about?
   - Is there an option that hasn't been considered that addresses both perspectives?

4. Design the decision process
   - Given the type of deadlock: what process would help the team converge?
   - What evidence, if gathered, would break the deadlock?
   - If evidence cannot break it: who should be the named decision owner?

5. Facilitate disagree and commit
   - Write the disagree and commit statement for the losing position
   - Write the review trigger that gives the losing position a fair hearing in the future

The decision: [describe what is being decided]
Position A: [describe the argument and who holds it]
Position B: [describe the argument and who holds it]
What has been tried: [what process has the team already gone through?]
```

---

### Prompt 4 — Make an AI Product Decision

> **Best for:** Any decision specific to AI products — model selection, quality thresholds, launch criteria, human-in-the-loop design.

```
You are an AI product advisor helping me make a well-reasoned decision about my AI product.

Guide me through the decision using the AI product decision checklist:

1. Decision framing
   - What exactly is being decided? (Be specific — "which AI approach to use" is too broad)
   - What are the 2–3 genuine options?

2. AI-specific considerations
   - What uncertainty exists that could change this decision?
   - What AI quality threshold is acceptable for this use case?
   - What failure mode does this decision create, and is that acceptable?
   - How reversible is this decision if the AI doesn't perform as expected?
   - Does this decision depend on data we have or data we need to acquire?

3. Trade-off analysis
   For the AI context specifically:
   - Quality vs cost: where do we draw the line?
   - Speed to market vs certainty of quality: which matters more here?
   - User autonomy vs AI automation: how much should users control?

4. Decision recommendation
   - Given all of the above, what is the recommended decision?
   - What are the specific conditions under which we would revisit it?
   - What monitoring would tell us within 30 days whether this was the right call?

My AI decision: [describe what you need to decide]
Context: [describe the feature, user, and business context]
Options I am considering: [describe each option]
Primary constraint: [budget / timeline / quality / user trust / other]
```

---

### Prompt 5 — Write a Decision Retrospective

> **Best for:** 3–6 months after a major decision — reflecting on whether it was right and extracting principles for future decisions.

```
You are a product retrospective facilitator helping me conduct a decision retrospective.

I will describe a decision made previously and what happened since. Your job is to:

1. Assess the decision quality
   - Was the decision process sound? (Was the right information considered? Were the right people involved?)
   - Was the decision outcome positive, neutral, or negative?
   - Was the outcome predictable from the information available at the time? (Good process can produce bad outcomes, and vice versa)

2. Identify what the decision got right
   - What assumptions proved correct?
   - What risks were correctly anticipated and mitigated?

3. Identify what the decision got wrong
   - What assumptions proved incorrect?
   - What risks were not anticipated?
   - What information was available but not used?

4. Extract the learning principle
   - What rule or principle would have led to a better decision?
   - Is this learning specific to this situation, or does it generalise?

5. Apply the learning
   - Are there any current decisions that this learning should influence?
   - Should any current assumptions be revisited based on this retrospective?

The original decision: [describe what was decided and why]
What happened: [describe the outcome — what went well, what didn't]
Time since decision: ___
What surprised you most: _______________________________________________
```
