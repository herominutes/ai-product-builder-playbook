# 🎯 AI Product Strategy Playbook — AI Product Builder Playbook

> **A comprehensive playbook for defining, validating, and executing an AI product strategy that creates durable competitive advantage**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Playbook](#when-to-use-this-playbook)
- [The AI Product Strategy Model](#the-ai-product-strategy-model)
- [Phase 1: Market and Opportunity Analysis](#phase-1-market-and-opportunity-analysis)
- [Phase 2: AI Value Proposition Design](#phase-2-ai-value-proposition-design)
- [Phase 3: Competitive Positioning](#phase-3-competitive-positioning)
- [Phase 4: Build vs Buy vs Partner](#phase-4-build-vs-buy-vs-partner)
- [Phase 5: Go-to-Market Strategy](#phase-5-go-to-market-strategy)
- [Phase 6: Moat and Defensibility](#phase-6-moat-and-defensibility)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Most AI product strategies are not strategies — they are feature lists with the word "AI" added. A real AI product strategy answers the questions that feature lists cannot: why will users trust us with this? Why will we be better than competitors in 12 months, not just today? What prevents a well-resourced competitor from copying what we build next quarter?

> **Core Principle:** AI is not a strategy. It is a capability. The strategy defines how that capability creates value that compounds over time — through data network effects, user trust, proprietary training, or workflow integration depth. Without this, AI features are temporary advantages that competitors can replicate at the cost of an API subscription.

This playbook guides the full arc of AI product strategy development: from identifying the right market opportunity through to building the defensibility moat that sustains competitive advantage. It is designed for product leaders who are either launching a new AI product or repositioning an existing product with AI.

---

## When to Use This Playbook

| Trigger | Priority |
|---|---|
| Launching a new AI product or major AI initiative | 🔴 Critical — strategy before build |
| Repositioning existing product with AI capabilities | 🔴 Critical — strategy before repositioning |
| Competitors have launched AI features and the team is reacting | 🔴 Critical — reactive strategy is worse than no strategy |
| Leadership is asking "what is our AI strategy?" | 🟠 High |
| AI features are shipping but not creating differentiation | 🟠 High — strategy gap, not execution gap |
| Annual planning — setting AI investment direction | 🟡 Medium |
| New funding raised for AI product development | 🟡 Medium |

---

## The AI Product Strategy Model

AI product strategy develops across six phases. Each phase builds the foundation for the next.

```
MARKET AND OPPORTUNITY ANALYSIS
  ↓ where is the real AI opportunity?
AI VALUE PROPOSITION DESIGN
  ↓ what specific value does AI create for which user?
COMPETITIVE POSITIONING
  ↓ how do we win against alternatives — including other AI products?
BUILD VS BUY VS PARTNER
  ↓ what is the right make-or-buy decision for each AI capability?
GO-TO-MARKET STRATEGY
  ↓ how do we reach, convert, and retain our target user?
MOAT AND DEFENSIBILITY
  ↓ how do we sustain advantage as competitors respond?
```

| Phase | Core Question | Key Output | Who Leads |
|---|---|---|---|
| **Market analysis** | Where is the real opportunity? | Market map + opportunity sizing | CPO + PM |
| **Value proposition** | What value does AI create? | AI value proposition canvas | PM + Design |
| **Competitive positioning** | How do we win? | Positioning statement + battle cards | PM + Marketing |
| **Build vs buy** | What do we build vs buy? | Make-or-buy decision framework | CPO + CTO |
| **GTM strategy** | How do we reach users? | GTM plan + launch strategy | PM + Marketing |
| **Moat design** | How do we sustain advantage? | Defensibility roadmap | CPO + CTO |

---

## Phase 1: Market and Opportunity Analysis

### 1.1 AI Market Segmentation

Not all markets benefit equally from AI. Segment before committing:

| Market Characteristic | AI Opportunity Level | Rationale |
|---|---|---|
| High-volume, repetitive knowledge work | Very high | AI scales what humans cannot |
| Complex, expert-dependent tasks | High | AI democratises expert access |
| Time-sensitive decision-making | High | AI accelerates human judgment |
| Creative and generative work | High | AI amplifies creative output |
| Relationship-dependent services | Medium | AI supports but cannot replace trust |
| Regulatory, high-liability decisions | Medium | AI assists with human accountability |
| Physical, hands-on work | Low | AI has limited direct value |

### 1.2 Opportunity Sizing for AI Products

```
AI OPPORTUNITY SIZING FRAMEWORK

Total Addressable Market (TAM):
Total spending on [problem category] globally = $___
Of this, the portion that could be addressed by AI = $___

Time-to-value compression opportunity:
Current time to complete [core task] manually: ___ hours
AI-assisted time: ___ hours
Value of time saved per user per year: $___
× Total addressable users: ___
= Time value TAM: $___

Quality improvement opportunity:
Current average output quality / error rate: ___%
AI-improved quality / error rate: ___%
Value of quality improvement per user: $___
× Total addressable users = Quality value TAM: $___

Cost reduction opportunity:
Current cost to deliver [outcome] without AI: $___
AI-assisted cost: $___
Cost reduction per customer: $___
× Total addressable customers = Cost reduction TAM: $___
```

### 1.3 AI Market Timing Assessment

```
MARKET TIMING ASSESSMENT

Technology readiness:
[ ] Foundation models capable enough for this task: Yes / Not yet / Marginal
[ ] Latency acceptable for real-time use: Yes / Not yet
[ ] Cost per inference sustainable at target pricing: Yes / Not yet
[ ] Reliability / accuracy threshold met: Yes / Not yet

Market readiness:
[ ] Target users are aware that AI can solve this: Yes / Emerging / No
[ ] Trust threshold for AI in this domain has been crossed: Yes / Emerging / No
[ ] Regulatory environment is clear: Yes / Ambiguous / Prohibitive
[ ] Enterprise procurement has AI-specific processes: Yes / Emerging / No

Competitive window:
[ ] How many funded competitors are in this space? ___
[ ] What is the estimated lead time of the most advanced competitor? ___ months
[ ] Is there a first-mover advantage in this market? Yes / Limited / No

Timing verdict:
Now: All technology and market readiness boxes checked + competitive window open
Wait: Technology not ready — build infrastructure while waiting
Pivot: Market timing unfavourable — reassess in 12 months
```

---

## Phase 2: AI Value Proposition Design

### 2.1 The AI Value Proposition Canvas

```
AI VALUE PROPOSITION CANVAS

USER PROFILE
  Jobs to be done: [what is the user trying to accomplish?]
  Pains: [what frustrates them about doing this today?]
  Gains: [what would make this significantly better?]

AI VALUE MAP
  AI gain creators: [how does AI specifically create the gains above?]
  AI pain relievers: [how does AI specifically relieve the pains above?]
  AI products and features: [what AI capabilities create the value?]

FIT ASSESSMENT
  Which gains does AI create better than any alternative? _______________________________________________
  Which pains does AI relieve better than any alternative? _______________________________________________
  Where does AI fall short vs the current workaround? _______________________________________________
```

### 2.2 AI Value Types

Identify which type of AI value your product primarily creates:

| AI Value Type | Description | User Signal | Example |
|---|---|---|---|
| **Speed value** | AI does in seconds what takes humans minutes/hours | "This saves me so much time" | Meeting summarisation |
| **Scale value** | AI does at scale what humans can only do at small scale | "I could never have done this for all 10,000 customers" | Personalisation at scale |
| **Quality value** | AI produces better output than the average human | "The AI version is better than what I'd write myself" | First draft generation |
| **Discovery value** | AI surfaces insights or connections humans would miss | "I never would have noticed this pattern" | Anomaly detection |
| **Consistency value** | AI produces consistent output regardless of time, mood, or volume | "It never has a bad day" | Quality assurance |
| **Access value** | AI democratises expertise previously available only to some | "I couldn't afford a consultant for this" | Expert-level guidance |

### 2.3 Value Proposition Statement

```
VALUE PROPOSITION FORMULA

For [specific user]
Who [specific struggle or unmet need],
[Product name] is the [category]
That [specific AI value — speed / scale / quality / discovery / consistency / access]
By [specific mechanism that creates the value],
Unlike [current alternative],
Our product [specific differentiator].

Example:
For senior analysts at consulting firms
Who spend 4+ hours per week manually synthesising research across 20+ sources,
Luminary is the AI research platform
That reduces that 4 hours to 20 minutes
By automatically retrieving, synthesising, and citing from your approved source library,
Unlike general AI tools that require you to provide the sources,
Our platform learns your firm's trusted sources and applies your methodology automatically.
```

---

## Phase 3: Competitive Positioning

### 3.1 AI Competitive Landscape Mapping

```
COMPETITIVE LANDSCAPE MAP

Direct AI competitors (same problem, AI solution):
| Competitor | AI approach | Strengths | Weaknesses | Pricing |
|------------|------------|-----------|------------|---------|
| | | | | |

Indirect AI competitors (different problem, same user):
| Competitor | What they offer | Why users might choose them | Our response |
|------------|----------------|---------------------------|-------------|
| | | | |

Status quo (current non-AI alternative):
What users do today: _______________________________________________
Cost of status quo (time + money): _______________________________________________
Switching cost from status quo to our product: _______________________________________________

Future competitors (likely entrants in 12–24 months):
Who could enter: _______________________________________________
What would they bring: _______________________________________________
Our defensive strategy: _______________________________________________
```

### 3.2 Positioning Strategy Selection

| Positioning Strategy | Description | When It Works |
|---|---|---|
| **AI quality leader** | Best AI outputs in the category | When model quality is genuinely superior and verifiable |
| **AI workflow integrator** | Deepest integration with existing tools | When users are locked into an ecosystem |
| **AI domain specialist** | AI tuned for a specific domain or use case | When domain data creates a quality advantage |
| **AI trust leader** | Most transparent, explainable, reliable AI | When users are risk-averse or in regulated industries |
| **AI speed leader** | Fastest AI in the category | When latency is the critical user constraint |
| **AI price leader** | Best value AI | When the market is price-sensitive and quality is commoditising |

### 3.3 Competitive Battle Cards

```
COMPETITIVE BATTLE CARD — [Competitor Name]

Overview:
Their AI approach: _______________________________________________
Their core strength: _______________________________________________
Their core weakness: _______________________________________________

When we win:
We beat them when: _______________________________________________
Our proof point: _______________________________________________
Customer quote supporting this: _______________________________________________

When they win:
They beat us when: _______________________________________________
Our response: _______________________________________________
What to avoid in this conversation: _______________________________________________

Their likely counter to our positioning:
They will say: _______________________________________________
We respond with: _______________________________________________

One thing that would fundamentally change this dynamic:
_______________________________________________
```

---

## Phase 4: Build vs Buy vs Partner

### 4.1 Decision Framework

```
BUILD VS BUY VS PARTNER DECISION TREE

For each AI capability required, answer:

1. Is this a differentiating capability?
   Yes (core to our value proposition) → Consider Build or Train
   No (commodity capability) → Consider Buy

2. Do we have the data advantage?
   Yes (we have proprietary data that improves this capability) → Build or Fine-tune
   No → Buy (commoditised capability) or Partner (access the data)

3. Is the capability available from a reliable provider?
   Yes + meets our quality bar → Buy
   No → Build

4. Is deep customisation required?
   Yes (must behave in proprietary ways specific to our domain) → Build or Fine-tune
   No → Buy

5. Do we have the talent to build and maintain this?
   Yes → Build
   No → Buy or Partner until talent is available

Decision:
[ ] Build — core capability, proprietary data advantage, talent available
[ ] Fine-tune — commodity base model, proprietary data advantage
[ ] Buy (API) — non-differentiating, available, meets quality bar
[ ] Partner — strategic capability, joint development advantage
[ ] Do not build — out of scope
```

### 4.2 AI Capability Map

```
AI CAPABILITY MAP — [Product Name]

| Capability | Strategic importance | Data advantage | Build/Buy/Partner | Timeline |
|-----------|---------------------|----------------|-------------------|----------|
| [Core AI feature] | Differentiating | Yes — proprietary | Build | Q1 |
| [Supporting AI feature] | Supporting | No | Buy (API) | Q1 |
| [Future AI capability] | Differentiating | Building | Fine-tune | Q3 |
| [Commodity AI task] | Commodity | No | Buy (API) | Q1 |
```

---

## Phase 5: Go-to-Market Strategy

### 5.1 AI Product GTM Specifics

AI products require GTM considerations that traditional SaaS does not:

| GTM Consideration | AI-Specific Challenge | Strategy |
|---|---|---|
| **Trust building** | Users are skeptical of AI quality and reliability | Demo-first → free trial → conversion; lead with proof, not promises |
| **AI literacy** | Target users may not understand what AI can do | Education-led GTM; webinars, case studies, ROI calculators |
| **First output quality** | First AI output is the most important conversion moment | Invest heavily in onboarding; first session quality determines trial-to-paid |
| **Privacy concerns** | Enterprise buyers worry about data security | Lead with security certifications; offer private deployment for enterprise |
| **Expectation setting** | Users often expect AI to be either magic or useless | Be specific about what AI does and does not do; show the error cases honestly |

### 5.2 AI Product Positioning Statement for GTM

```
EXTERNAL POSITIONING STATEMENT

For: [target user in specific role]
Who: [specific pain — time-based, quality-based, or scale-based]
[Product] is: [category framing]
That: [specific AI value — concrete, measurable]
Unlike: [current alternative — status quo or competitor]
We: [specific differentiator — why AI from us, not anyone else]

Proof points (required for each positioning claim):
Claim 1: [___] — Proof: [customer quote / case study / benchmark]
Claim 2: [___] — Proof: [___]
Claim 3: [___] — Proof: [___]
```

### 5.3 Pricing Strategy for AI Products

| Pricing Model | Description | Best For |
|---|---|---|
| **Seat-based** | Per user per month | When value is proportional to users |
| **Usage-based** | Per AI interaction, output, or task | When value is proportional to usage |
| **Outcome-based** | Per successful outcome | When outcomes are measurable and high-value |
| **Tiered** | Feature differentiation across tiers | When different segments have different value needs |
| **Value-capture** | % of value created | When AI value is directly measurable (e.g. revenue generated) |

---

## Phase 6: Moat and Defensibility

### 6.1 AI Moat Types

| Moat Type | Description | How to Build | Time to Establish |
|---|---|---|---|
| **Data moat** | Proprietary data that improves AI quality | Collect data competitors cannot; build data flywheels | 12–24 months |
| **Workflow integration moat** | Deep integration into user workflows creates switching cost | Build into daily workflows; become the system of record | 6–18 months |
| **Trust moat** | Users trust your AI more than competitors' | Consistent quality + transparency + safety track record | 12–24 months |
| **Network effects moat** | Each new user makes the AI better for others | Shared learning; collaborative features; community data | 18–36 months |
| **Expert knowledge moat** | Domain expertise embedded in training and prompting | Partner with domain experts; fine-tune on expert-labelled data | 6–12 months |
| **Distribution moat** | User relationships and channel access that competitors lack | Enterprise relationships; platform integration; ecosystem position | 12–36 months |

### 6.2 Moat Assessment

```
MOAT ASSESSMENT — [Product Name]

For each moat type, rate current strength (1–5) and 12-month trajectory:

| Moat Type | Current Strength | 12-Month Target | Key Action Required |
|-----------|-----------------|-----------------|---------------------|
| Data moat | ___ / 5 | ___ / 5 | |
| Workflow integration | ___ / 5 | ___ / 5 | |
| Trust moat | ___ / 5 | ___ / 5 | |
| Network effects | ___ / 5 | ___ / 5 | |
| Expert knowledge | ___ / 5 | ___ / 5 | |
| Distribution | ___ / 5 | ___ / 5 | |

Primary moat (where we will invest most): _______________________________________________
Secondary moat (supporting the primary): _______________________________________________

Moat vulnerability: What would a well-resourced competitor need to neutralise our moat?
_______________________________________________

Moat investment required: $_______________________________________________
```

### 6.3 Defensibility Roadmap

```
DEFENSIBILITY ROADMAP — 24 MONTHS

Month 1–6: Establish product-market fit with superior first experience
  Primary moat investment: [workflow integration — get into the daily workflow]
  Key milestones: [define what integration depth looks like]

Month 6–12: Begin data flywheel
  Primary moat investment: [data moat — collect proprietary usage data]
  Key milestones: [first fine-tuning run on proprietary data]

Month 12–18: Deepen integration; begin network effects
  Primary moat investment: [workflow integration + network effects]
  Key milestones: [collaboration features; shared learning across users]

Month 18–24: Compound advantage
  Primary moat investment: [all moats reinforce each other]
  Key milestones: [measurable quality gap vs competitors; switching cost established]
```

---

## Templates

### Template A: AI Product Strategy One-Pager

```
# AI Product Strategy — [Product Name]
Date: ___  |  Author: ___  |  Horizon: 12 months

## The Opportunity
Market: _______________________________________________
AI-specific opportunity: _______________________________________________
Why now: _______________________________________________

## Target User
Persona: _______________________________________________
Core job to be done: _______________________________________________
AI value type: Speed / Scale / Quality / Discovery / Consistency / Access

## Value Proposition
[One paragraph using the value proposition formula]

## Competitive Position
We win when: _______________________________________________
We lose when: _______________________________________________
Primary moat: _______________________________________________

## Build vs Buy Decisions
Build: _______________________________________________
Buy: _______________________________________________
Partner: _______________________________________________

## GTM Approach
Segment: _______________________________________________
Channel: _______________________________________________
Pricing model: _______________________________________________

## 12-Month Moat Milestone
_______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| "Our AI strategy is to add AI to our existing product" | Define the specific AI value type and the specific user job it serves |
| Positioning on AI quality without proof | Lead with case studies and benchmarks — claims without proof accelerate distrust |
| No moat strategy — just features | Every AI feature should contribute to at least one moat |
| Building what competitors have, not what users need | Return to the AI value proposition canvas — what gap does the market have? |
| Treating AI as a product, not a capability | AI is the engine; the strategy defines where the car goes |
| Ignoring the trust-building arc in GTM | AI GTM is education-first, proof-second, conversion-third |
| Pricing on features rather than value created | AI pricing should reflect the value delivered — time saved, outcomes achieved |
| No defensibility roadmap | Without a moat plan, first-mover advantage evaporates when competitors enter |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Competitive landscape review | Monthly | PM |
| Value proposition validation (user interviews) | Monthly | PM |
| Moat assessment | Quarterly | CPO |
| Build vs buy decision review | Quarterly | CPO + CTO |
| Full strategy review | Annually | CPO + Leadership |
| Market timing re-assessment | Quarterly | CPO |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Develop a Complete AI Product Strategy

> **Best for:** Building the full AI product strategy document from opportunity through to moat design.

```
You are an AI product strategy consultant helping me develop a complete AI product strategy.

Guide me through all six phases in sequence:

1. Market and opportunity analysis — where is the real AI opportunity in my market?
2. AI value proposition design — what specific value does AI create for which user?
3. Competitive positioning — how do I win against alternatives including other AI products?
4. Build vs buy vs partner — what AI capabilities do I build vs buy vs partner for?
5. Go-to-market strategy — how do I reach, convert, and retain my target user?
6. Moat and defensibility — how do I sustain advantage as competitors respond?

For each phase:
- Ask me the key questions needed to complete the phase
- Challenge any assumptions I make that are not grounded in evidence
- Produce the key output document for that phase
- Identify what I don't yet know and would need to validate

After all six phases:
- Produce the AI product strategy one-pager
- Identify the top 3 strategic risks in the plan
- Identify the single most important decision that will determine success

My product: [describe]
Target user: [describe]
Current stage: [idea / prototype / early product / growth]
Market context: [describe the competitive landscape you're aware of]
Team: [size, key roles, AI capability]
```

---

### Prompt 2 — Design the AI Value Proposition

> **Best for:** Articulating precisely what value AI creates for a specific user — the foundation of all product and marketing decisions.

```
You are an AI product strategist helping me design a compelling, evidence-grounded value proposition.

Using the AI Value Proposition Canvas, help me define:

1. User profile (from research, not assumption)
   - The specific job to be done
   - The specific pains (time-based, quality-based, or emotional)
   - The specific gains the user wants

2. AI value map
   - Which AI value type applies: Speed / Scale / Quality / Discovery / Consistency / Access
   - Specific AI gain creators (how does AI create each gain above?)
   - Specific AI pain relievers (how does AI address each pain above?)

3. Fit assessment
   - Where is the fit strongest? (where AI uniquely beats all alternatives)
   - Where is the fit weakest? (where AI still falls short)

4. Value proposition statement
   - Write a full value proposition using the formula
   - Then write a one-sentence version for the homepage
   - Then write a one-sentence version for a cold email subject line

5. Proof points required
   - What evidence would make each claim in the value proposition credible?
   - What case studies or benchmarks do I need to build?

My product: [describe]
Target user: [describe their role, context, and what you know about their pain]
What I currently say our value is: [your current positioning, if any]
Evidence I have from users: [interview quotes, analytics findings, or feedback]
```

---

### Prompt 3 — Map the Competitive Landscape and Define Positioning

> **Best for:** Understanding the competitive dynamics of an AI market and choosing a positioning strategy that creates a defensible advantage.

```
You are a competitive strategy analyst helping me map the AI competitive landscape and define my positioning.

Guide me through:

1. Competitive landscape mapping
   - Direct AI competitors: same problem, AI solution
   - Indirect competitors: different problem, same user budget
   - Status quo: what users do today without AI
   - Future threats: who is likely to enter in 12–24 months

2. Competitive analysis
   For each competitor I describe:
   - What AI approach do they use?
   - Where do they win? Where do they lose?
   - What is their primary moat?
   - What would I need to do to take their best customer?

3. Positioning strategy selection
   - Which positioning strategy fits my situation: quality leader / workflow integrator / domain specialist / trust leader / speed leader / price leader?
   - Why this strategy and not an alternative?
   - What makes this positioning defensible?

4. Positioning statement
   - Write the full positioning statement using the formula
   - Write the competitive battle card for my top competitor

5. Positioning risks
   - What would invalidate this positioning?
   - How quickly could a competitor match it?
   - What would change the competitive dynamics most?

My product: [describe]
Competitors I know of: [list names and what you know about them]
My perceived differentiation: [what you currently believe sets you apart]
User segment: [who you're targeting]
```

---

### Prompt 4 — Design the Moat and Defensibility Strategy

> **Best for:** Building the 24-month roadmap for creating sustainable competitive advantage that compounds over time.

```
You are an AI strategy advisor helping me design a defensibility roadmap for my AI product.

Assess and design the moat strategy across all six AI moat types:

1. Data moat
   - What proprietary data could I collect that competitors cannot?
   - How do I build a data flywheel where more usage generates better AI?
   - Timeline to meaningful data advantage: ___

2. Workflow integration moat
   - Which daily workflows should my AI be embedded in?
   - What switching cost does deep integration create?
   - What integrations with existing tools create the highest lock-in?

3. Trust moat
   - How do I build a track record of AI reliability in my domain?
   - What transparency and explainability features build trust over time?
   - How do I make trust visible and communicable to new users?

4. Network effects
   - Is there a version of this product where each new user makes it better for others?
   - How do I design shared learning across users?
   - What collaboration features create organic network effects?

5. Expert knowledge moat
   - What domain expertise can I embed in training and prompting that competitors cannot easily replicate?
   - Who are the domain experts I should partner with?

6. Distribution moat
   - What distribution channels or relationships give me access that competitors don't have?
   - What platform integrations create distribution advantages?

After all six moat types:
- Select the primary moat (where to invest most)
- Design the 24-month defensibility roadmap
- Identify the single most important moat-building action in the next 90 days

My product: [describe]
Current competitive advantages (if any): [describe]
Resources available for moat investment: [budget / team / time]
```

---

### Prompt 5 — Build the AI Product GTM Plan

> **Best for:** Designing the go-to-market strategy for an AI product launch, including trust-building, channel, and pricing.

```
You are a GTM strategist specialising in AI products helping me design my go-to-market plan.

Design the complete GTM plan addressing AI-specific challenges:

1. Target segment selection
   - Which user segment should I go to market with first? (not "everyone")
   - Why this segment first? (AI readiness, willingness to pay, reference value)
   - What does the ideal early adopter look like?

2. Trust-building GTM sequence
   - How do I lead with proof instead of promises?
   - What is the free trial / demo / proof-of-concept structure?
   - What does the first session experience need to show to convert?

3. Channel strategy
   - Which channels reach my target segment?
   - Which channels are best for an AI product (education-heavy, trust-building)?
   - What does the content strategy look like to build AI literacy?

4. Pricing strategy
   - Which pricing model fits my value creation type?
   - How do I price to capture value without creating adoption friction?
   - What is the freemium or trial structure?

5. Launch sequence
   - What is the 90-day launch plan? (Week by week)
   - How do I create early social proof from the first 10–20 customers?
   - What is the feedback loop from early users back into product?

After the full GTM plan:
- Identify the single most important success metric for the first 90 days
- Identify the top 3 risks to the GTM plan and specific mitigations

My product: [describe]
Target segment: [who you're going after first]
Current traction (if any): [existing users, beta customers, early feedback]
GTM resources: [sales team? marketing budget? founder-led?]
```

