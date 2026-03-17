# 🧠 AI Memory System — AI Product Builder Playbook

> **A framework for designing persistent context and memory architectures in AI-powered products**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Memory Architecture Model](#the-memory-architecture-model)
- [Memory Type 1: Working Memory](#memory-type-1-working-memory)
- [Memory Type 2: Episodic Memory](#memory-type-2-episodic-memory)
- [Memory Type 3: Semantic Memory](#memory-type-3-semantic-memory)
- [Memory Type 4: Procedural Memory](#memory-type-4-procedural-memory)
- [Memory Retrieval Architecture](#memory-retrieval-architecture)
- [Memory Privacy and Control](#memory-privacy-and-control)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Every LLM has a fundamental limitation: it forgets everything between sessions. Each conversation starts from zero. For consumer applications, this may be acceptable. For professional AI products — where users expect the system to know their preferences, history, and context — it is a product-ending limitation.

> **Core Principle:** Memory is what transforms an AI tool into an AI colleague. A tool you have to re-explain yourself to every session is exhausting. A system that remembers who you are, what you care about, and how you work creates compounding value with every interaction.

AI memory systems are not simply storing conversation history. They are architectures for selecting, organising, retrieving, and applying the right context at the right moment — without overwhelming the model's context window or violating user trust.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Building a conversational AI product with repeat users | 🔴 Critical — stateless AI cannot build user trust |
| Users are re-explaining context every session | 🔴 Critical — memory failure is a churn driver |
| Designing a personalised AI assistant or copilot | 🔴 Critical — personalisation requires memory |
| AI outputs are inconsistent with prior decisions the user shared | 🟠 High |
| Building an AI agent that operates over multiple sessions | 🟠 High |
| Designing for enterprise users who need institutional memory | 🟠 High |
| Evaluating whether to build or buy a memory layer | 🟡 Medium |

---

## The Memory Architecture Model

AI memory systems mirror human memory — four distinct types, each serving a different role. A complete AI memory architecture implements all four.

```
WORKING MEMORY
  ↓ what the AI knows right now (current context window)
EPISODIC MEMORY
  ↓ what happened in past interactions (conversation history)
SEMANTIC MEMORY
  ↓ what the AI knows about the user and domain (facts, preferences, entities)
PROCEDURAL MEMORY
  ↓ how the AI should behave for this user (learned patterns and preferences)
```

| Memory Type | Human Analogy | AI Implementation | Persistence |
|---|---|---|---|
| **Working** | What you're thinking about right now | Context window / active prompt | Session only |
| **Episodic** | "Last time we spoke, you mentioned..." | Conversation history store | Cross-session |
| **Semantic** | Facts you know about someone | Entity and preference store | Long-term |
| **Procedural** | "She likes bullet points, hates jargon" | Behaviour preference store | Long-term |

> **Rule of thumb:** Working memory is cheap but ephemeral. Semantic and procedural memory are expensive to build but create the compounding value that makes users say "this AI actually knows me."

---

## Memory Type 1: Working Memory

### 1.1 Context Window Management

Working memory is bounded by the model's context window. Exceeding it causes the model to "forget" earlier parts of the conversation — a jarring and trust-damaging experience.

| Model Class | Typical Context Window | Practical Working Memory |
|---|---|---|
| Standard (GPT-3.5 class) | 4K–16K tokens | 3,000–12,000 tokens after system prompt |
| Large (GPT-4 / Claude class) | 32K–200K tokens | 25K–180K tokens after system prompt |
| Extended (Gemini 1.5 class) | 1M+ tokens | Theoretical — practical limits apply |

### 1.2 Context Window Strategy

```
CONTEXT WINDOW ALLOCATION PLAN — [Feature Name]

Total context window:          _____ tokens
System prompt allocation:      _____ tokens  (___%)
Retrieved memory allocation:   _____ tokens  (___%)
Current conversation:          _____ tokens  (___%)
User input buffer:             _____ tokens  (___%)
Output buffer:                 _____ tokens  (___%)

Total allocated:               _____ tokens  (should be < 90% of window)
```

### 1.3 Context Compression

When conversations exceed working memory capacity, compress older content:

| Compression Technique | Approach | Token Reduction |
|---|---|---|
| **Summarisation** | Periodically summarise older turns | 60–80% |
| **Key fact extraction** | Extract key facts from earlier turns; discard raw dialogue | 70–90% |
| **Selective retention** | Keep only the most recent N turns in full | Variable |
| **Hierarchical compression** | Summarise then summarise the summary | 85–95% |
| **Entity-centric retention** | Keep all mentions of key entities; compress the rest | 50–70% |

---

## Memory Type 2: Episodic Memory

### 2.1 What Episodic Memory Stores

Episodic memory is the record of specific past interactions — the "when, what, and what happened" of prior sessions.

```
EPISODIC MEMORY SCHEMA

{
  session_id: "uuid",
  timestamp: "ISO-8601",
  user_id: "uuid",
  session_summary: "2–3 sentence summary of what was discussed",
  key_outcomes: ["outcome 1", "outcome 2"],
  decisions_made: ["decision 1", "decision 2"],
  open_questions: ["question the user left unresolved"],
  entities_mentioned: ["entity 1", "entity 2"],
  sentiment: "positive / neutral / negative",
  follow_up_needed: true / false,
  follow_up_topic: "if true, what to follow up on"
}
```

### 2.2 Episodic Memory Retrieval

Not all past sessions are equally relevant. Retrieve based on relevance, not recency alone:

```
EPISODIC RETRIEVAL STRATEGY

For each new session:

Step 1 — Recency retrieval: Pull last N sessions verbatim (N = 3–5)
Step 2 — Semantic retrieval: Embed current query; retrieve most similar past sessions
Step 3 — Entity retrieval: Extract entities from current query; pull sessions mentioning same entities
Step 4 — Merge and deduplicate retrieved sessions
Step 5 — Compress to fit context window allocation
Step 6 — Inject into system prompt as "conversation history"

Priority order: Semantic similarity > Entity match > Recency
```

### 2.3 Session Summarisation Pipeline

```
SESSION SUMMARISATION PIPELINE

Trigger: Session ends (user closes / inactivity timeout / explicit end signal)

Step 1 — Extract raw conversation
Step 2 — Generate summary (LLM call):
  "Summarise this conversation in 2–3 sentences. Include:
   - The main topic or task
   - Key decisions or conclusions reached
   - Any open questions or follow-ups needed
   - Important entities mentioned (people, projects, products)"

Step 3 — Extract structured entities (NLP pipeline or LLM):
  - People mentioned
  - Projects / products mentioned
  - Decisions made
  - Actions committed to

Step 4 — Store to episodic memory store with session metadata
Step 5 — Update semantic memory with new entity information extracted
```

---

## Memory Type 3: Semantic Memory

### 3.1 What Semantic Memory Stores

Semantic memory is a structured knowledge base about the user, their domain, and the entities they work with.

```
SEMANTIC MEMORY SCHEMA — USER PROFILE

{
  user_id: "uuid",
  role: "Senior Product Manager",
  organisation: "Acme Corp",
  domain: "B2B SaaS",
  expertise_areas: ["product strategy", "AI products", "growth"],
  current_projects: [
    {name: "Project X", context: "Launching Q3, main challenge is..."}
  ],
  key_stakeholders: [
    {name: "Alex", role: "CTO", relationship: "reports to"}
  ],
  preferences: {
    output_format: "bullet points",
    communication_style: "direct and concise",
    detail_level: "executive summary first"
  },
  constraints: {
    tools: ["Jira", "Figma", "Notion"],
    team_size: 4,
    budget_cycle: "quarterly"
  },
  last_updated: "ISO-8601"
}
```

### 3.2 Semantic Memory Extraction

Extract semantic facts from conversations continuously:

```
SEMANTIC EXTRACTION PROMPT

After each conversation turn, check:
"Did the user reveal any of the following?
- New facts about their role, organisation, or domain
- New projects or priorities
- New constraints or requirements
- New preferences about how I should communicate
- Corrections to information I held previously

If yes, extract and structure as:
{
  fact_type: [role / project / preference / constraint / correction],
  content: [extracted fact],
  confidence: [high / medium / low],
  source: [direct statement / implied / inferred]
}"

High confidence: user stated it directly ("I need this for a board presentation")
Medium confidence: user implied it ("given our budget constraints...")
Low confidence: inferred from behaviour ("user always asks for bullet points")
```

### 3.3 Entity Graph

For complex domains, build an entity graph that maps relationships between the people, projects, and concepts the user works with:

```
ENTITY GRAPH STRUCTURE

Nodes: User, Person, Project, Product, Organisation, Concept
Edges: works_with, manages, reports_to, owns, stakeholder_of, depends_on

Example:
User → manages → [Project Alpha, Project Beta]
Project Alpha → stakeholder_of → [Alex (CTO), Finance team]
Project Alpha → depends_on → [Data infrastructure, Q3 budget approval]
Alex (CTO) → manages → [User, Engineering team]
```

---

## Memory Type 4: Procedural Memory

### 4.1 What Procedural Memory Stores

Procedural memory captures how the AI should behave specifically for this user — learned from explicit statements and observed patterns.

```
PROCEDURAL MEMORY SCHEMA

{
  user_id: "uuid",
  communication_preferences: {
    format: "bullet points over prose",
    length: "concise — max 200 words per response",
    tone: "direct, no pleasantries",
    technical_level: "expert — no need to explain basics"
  },
  task_preferences: {
    first_draft_approach: "give me a rough structure to react to",
    feedback_style: "tell me what's wrong, not what's good",
    decision_support: "present options with trade-offs, not recommendations"
  },
  workflow_patterns: {
    typical_session_start: "catching up on context from last time",
    typical_session_end: "list of actions or next steps",
    preferred_working_time: "mornings — prefers quick exchanges"
  },
  explicit_instructions: [
    "Always start responses with the direct answer",
    "Never use corporate jargon",
    "Flag uncertainty explicitly"
  ],
  learned_corrections: [
    "User corrected bullet format to numbered list on 3 occasions — update default"
  ]
}
```

### 4.2 Preference Learning Pipeline

```
PREFERENCE LEARNING PIPELINE

Explicit learning (highest confidence):
User says: "Can you always give me bullet points?"
→ Update procedural memory: format = "bullet points"
→ Confirm: "Got it — I'll use bullet points going forward."

Implicit learning (medium confidence):
User consistently reformats AI output from prose to bullets
→ Detect pattern after 3 occurrences
→ Update procedural memory: format = "bullet points" (implicit)
→ Confirm: "I noticed you prefer bullet points — I'll default to that."

Correction learning:
User says: "That's not how I meant it — I wanted X not Y"
→ Record correction to procedural memory
→ Update semantic memory if factual correction
→ Adjust for future responses immediately
```

---

## Memory Retrieval Architecture

### 4.3 Retrieval-Augmented Memory (RAM)

The standard retrieval pattern for injecting the right memory into each session:

```
RETRIEVAL-AUGMENTED MEMORY PIPELINE

Input: New user query
          ↓
Step 1 — Query embedding
Embed the user's query into a vector representation.
          ↓
Step 2 — Multi-source retrieval
Retrieve in parallel from:
  a) Episodic store (semantic similarity search)
  b) Semantic memory (entity match)
  c) Procedural memory (always included in full — small and critical)
          ↓
Step 3 — Relevance scoring
Score each retrieved item by relevance to current query.
Discard items below relevance threshold.
          ↓
Step 4 — Context assembly
Assemble retrieved items into a context block:
  [Procedural preferences] + [Semantic user profile] + [Relevant episodic summaries]
          ↓
Step 5 — Context compression
If assembled context exceeds allocation, compress least-relevant items.
          ↓
Step 6 — Inject into system prompt
Pass assembled context to model as part of the system prompt or early conversation turns.
```

### 4.4 Memory Store Technology Options

| Store Type | Technology Options | Best For |
|---|---|---|
| **Vector store** (episodic retrieval) | Pinecone, Weaviate, Chroma, pgvector | Semantic similarity search across sessions |
| **Document store** (episodic raw) | PostgreSQL, MongoDB, DynamoDB | Storing and retrieving conversation records |
| **Graph database** (entity graph) | Neo4j, Amazon Neptune | Complex entity relationship mapping |
| **Key-value store** (procedural) | Redis, DynamoDB | Fast lookup of user preferences |
| **Relational database** (semantic) | PostgreSQL | Structured user profile data |

---

## Memory Privacy and Control

### User Rights Over Their Memory

| Right | Implementation |
|---|---|
| **View** | User can see all stored memory — export as readable format |
| **Edit** | User can correct inaccurate stored facts |
| **Delete** | User can delete specific memories or all memory |
| **Pause** | User can pause memory collection without deleting existing |
| **Export** | User can export full memory as JSON or readable format |

### Memory Privacy Checklist

```
MEMORY PRIVACY CHECKLIST

Data minimisation:
[ ] Only store memory that directly improves product value
[ ] Do not store sensitive personal or financial data in memory
[ ] Apply retention limits — delete episodic memory older than [N months]

Transparency:
[ ] Users know memory is being collected (explicit disclosure)
[ ] Users can view exactly what is stored about them
[ ] AI clearly signals when it is using memory ("Based on what you told me last week...")

Security:
[ ] Memory stores are encrypted at rest and in transit
[ ] Memory is user-scoped — no cross-user memory leakage
[ ] Memory access requires user authentication

Compliance:
[ ] GDPR right to erasure implemented
[ ] Data retention policies defined and enforced
[ ] Third-party model providers cannot train on user memory data
```

---

## Templates

### Template A: Memory Architecture Design Document

```
# Memory Architecture Design — [Product / Feature Name]
Date: ___  |  Author: ___  |  Version: ___

## Memory Requirements
What does the user expect the AI to remember?
_______________________________________________

What memory failure would cause the user to churn?
_______________________________________________

## Memory Type Implementation

Working memory:
Context window: ___ tokens
Allocation plan: System prompt ___% / Retrieved memory ___% / Conversation ____%
Compression strategy: _______________________________________________

Episodic memory:
Store: _______________________________________________
Retrieval method: _______________________________________________
Retention period: ___ months
Summarisation cadence: Per session / Daily / Weekly

Semantic memory:
Schema: [attach or describe]
Extraction method: _______________________________________________
Update frequency: Real-time / End of session / Daily

Procedural memory:
Storage: _______________________________________________
Learning method: Explicit / Implicit / Both
Confirmation UX: _______________________________________________

## Retrieval Architecture
RAM pipeline implemented: Yes / No / Planned
Vector store: _______________________________________________
Retrieval latency target: < ___ ms

## Privacy and Control
User view implemented: Yes / No
User edit implemented: Yes / No
User delete implemented: Yes / No
Retention policy: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Storing entire conversation history without summarisation | Summarise sessions; store structured facts, not raw transcripts |
| No memory at all — stateless AI for repeat-use products | Implement at minimum episodic and procedural memory |
| Injecting all memory into every session regardless of relevance | Retrieve selectively based on current query context |
| No user control over stored memory | Users must be able to view, edit, and delete their memory |
| Storing sensitive data (financial, health, credentials) in memory | Never store sensitive data — memory stores are not secure vaults |
| Memory that contradicts itself without reconciliation | Implement conflict detection and resolution in semantic memory |
| Never confirming what the AI has learned | When updating procedural memory, explicitly confirm with the user |
| Memory that never expires | Apply retention limits — stale memory can be worse than no memory |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Memory quality audit | Monthly | Sample 50 user memory profiles — are facts accurate? |
| Retrieval performance review | Monthly | Measure: is retrieved memory actually being used by the model? |
| Preference learning accuracy | Quarterly | Survey: does the AI's behaviour match user expectations? |
| Privacy compliance review | Quarterly | Retention policy enforcement; user rights audit |
| Memory store capacity planning | Quarterly | Storage growth rate vs budget |
| Full architecture review | Annually | Or on major model upgrade |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Complete Memory Architecture

> **Best for:** Designing the full memory system for a new AI product or feature from scratch.

```
You are an AI systems architect helping me design a complete memory architecture for my AI product.

Design the memory system across all four types:

1. Working memory — context window allocation plan, compression strategy
2. Episodic memory — storage schema, retrieval strategy, summarisation pipeline, retention policy
3. Semantic memory — user profile schema, entity extraction approach, update frequency
4. Procedural memory — preference schema, explicit and implicit learning pipeline, confirmation UX

For each memory type:
- Specify the data schema (what fields are stored)
- Specify the retrieval logic (when and how this memory is retrieved)
- Specify the update logic (when and how this memory is updated)
- Identify the technology stack you recommend

After all four types, design the Retrieval-Augmented Memory (RAM) pipeline that assembles context for each new session.

End with:
- A privacy and control checklist for this specific product
- The top 3 technical risks in this memory design and how to mitigate them

My product: [describe what the AI does]
Typical session frequency: [how often does a user interact?]
Typical session length: [how long is a conversation?]
Key information the user expects the AI to remember: [describe]
Sensitivity of stored data: [low / medium / high]
```

---

### Prompt 2 — Design the Session Summarisation Pipeline

> **Best for:** Implementing the process that converts raw conversation history into structured episodic memory.

```
You are an AI engineer helping me build a session summarisation pipeline for episodic memory.

Design the complete pipeline for converting a raw conversation into structured episodic memory:

1. Summarisation prompt — write the exact LLM prompt to generate a 2–3 sentence session summary
2. Entity extraction — write the prompt or NLP logic to extract structured entities (people, projects, decisions, actions)
3. Sentiment and outcome classification — design the classifier for session sentiment and outcome type
4. Schema population — map extracted elements to the episodic memory schema
5. Deduplication logic — how do we avoid storing the same fact twice across sessions?
6. Conflict detection — what happens when a new session contradicts a stored fact?

After designing the pipeline:
- Estimate the token cost per session summarisation
- Recommend whether to run this synchronously (end of session) or asynchronously (background)
- Write 3 test cases I can use to validate the pipeline quality

My AI product: [describe]
Typical conversation length: [turns / tokens]
Key information types I need to extract: [list]
Memory store technology: [what am I storing to?]
```

---

### Prompt 3 — Design Preference Learning for Procedural Memory

> **Best for:** Building the system that learns how individual users want to be communicated with and adapts over time.

```
You are a product AI specialist helping me design a preference learning system for procedural memory.

Design the preference learning system across three learning modes:

1. Explicit learning — user directly states a preference
   - How do we detect explicit preference statements in conversation?
   - What is the confirmation UX? (confirm immediately / confirm at session end / silent update)
   - How do we handle conflicts with existing preferences?

2. Implicit learning — user behaviour implies a preference
   - List 10 behavioural signals that reveal user preferences (e.g. always reformatting output)
   - How many occurrences before we update the preference store?
   - How do we avoid over-fitting to a temporary behaviour?

3. Correction learning — user corrects the AI's behaviour
   - How do we detect a correction vs a new request?
   - How quickly should the correction be applied (immediate / next session)?
   - How do we prevent one correction from over-generalising?

After designing all three modes:
- Write the procedural memory schema for storing these preferences
- Design the injection prompt that activates these preferences in the system prompt
- Write 5 test scenarios I can use to validate the preference learning system

My AI product: [describe]
Typical user interaction style: [describe what you know about how users communicate]
Most important preferences to capture: [list 3–5]
```

---

### Prompt 4 — Build the User Memory Control UX

> **Best for:** Designing the interface through which users can view, edit, and control their AI memory.

```
You are a UX designer helping me design the user-facing memory control experience for my AI product.

Design the complete memory control system:

1. Memory transparency view
   - What should the user be able to see about their stored memory?
   - How should it be presented? (structured list / timeline / natural language summary)
   - What level of detail is appropriate (full schema vs simplified view)?

2. Memory editing
   - Which memory types should users be able to edit?
   - What is the edit flow? (inline / modal / dedicated settings page)
   - How do we prevent users from editing in ways that break the system?

3. Memory deletion
   - Individual fact deletion — how does a user remove one stored item?
   - Session deletion — how does a user remove a specific past conversation?
   - Full reset — how does a user clear all memory?

4. Memory pause
   - How does a user pause memory collection without deleting existing memory?
   - How is the paused state clearly communicated in the product?

5. Memory disclosure
   - How and when do we inform users that memory is being collected?
   - How do we signal in-conversation when the AI is using memory?
   - What is the onboarding disclosure flow?

After designing the full system:
- Write the copy for 5 key UX moments (memory disclosure, first memory stored, edit confirmation, deletion warning, reset confirmation)
- Identify the top 3 privacy risks in this design and how to mitigate them

My product: [describe]
User segment: [who are they and how tech-savvy are they?]
Regulatory environment: [GDPR / CCPA / other / none]
```

---

### Prompt 5 — Diagnose and Fix Memory Quality Issues

> **Best for:** When the memory system is in production but users are experiencing inconsistencies, outdated facts, or irrelevant retrieval.

```
You are an AI systems diagnostician helping me identify and fix memory quality problems in my AI product.

I will describe the memory issues users are experiencing. For each issue, diagnose the root cause and recommend a specific fix.

Diagnose across these potential failure points:

1. Extraction failures — are we failing to capture important facts from conversations?
2. Storage failures — are facts being stored incorrectly or with wrong confidence levels?
3. Retrieval failures — is the wrong memory being retrieved for the current context?
4. Injection failures — is memory being injected into the model in a way that it ignores or misinterprets?
5. Staleness failures — is the AI using outdated memory that contradicts current reality?
6. Conflict failures — is the AI holding contradictory facts without resolving them?

For each root cause identified:
- Describe the specific failure mechanism
- Write the fix (prompt change / schema change / retrieval logic change / pipeline change)
- Write a test case to confirm the fix works

Memory issues I am experiencing:
[describe what users are complaining about or what you have observed]

Current memory architecture:
[describe your current implementation]
```
