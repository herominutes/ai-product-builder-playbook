# ⚙️ AI Orchestration — AI Product Builder Playbook

> **A framework for designing, building, and managing multi-step AI workflows that coordinate models, tools, and data sources**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Orchestration Model](#the-orchestration-model)
- [Pattern 1: Sequential Orchestration](#pattern-1-sequential-orchestration)
- [Pattern 2: Parallel Orchestration](#pattern-2-parallel-orchestration)
- [Pattern 3: Conditional Orchestration](#pattern-3-conditional-orchestration)
- [Pattern 4: Loop Orchestration](#pattern-4-loop-orchestration)
- [Tool Integration Architecture](#tool-integration-architecture)
- [Orchestration Reliability](#orchestration-reliability)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A single LLM call is a feature. A coordinated sequence of LLM calls, tool invocations, and decision points is a product. AI orchestration is the architecture that turns individual model capabilities into end-to-end workflows that solve real user problems.

> **Core Principle:** The power of AI is not in any single model call — it is in the composition of calls, tools, and decisions into a workflow that automates what would otherwise take a human hours. Orchestration is the discipline of designing that composition.

AI orchestration introduces challenges that single-call architectures do not have: error propagation across steps, latency compounding, state management between calls, and the difficulty of debugging a failure that occurred three steps back. This framework addresses each.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Building a workflow that requires more than one AI call | 🔴 Critical — single-call thinking will fail |
| Users need the AI to complete multi-step tasks autonomously | 🔴 Critical — agent architecture required |
| AI needs to access external data, APIs, or tools to complete a task | 🔴 Critical — tool integration design required |
| A single AI call produces insufficient quality for a complex task | 🟠 High — decompose into orchestrated steps |
| Latency is a problem in a multi-step workflow | 🟠 High — parallelisation design required |
| AI workflow is failing unpredictably | 🟠 High — reliability architecture needed |
| Evaluating whether to use an orchestration framework (LangChain, LlamaIndex, etc.) | 🟡 Medium |

---

## The Orchestration Model

AI orchestration patterns range from simple linear chains to complex dynamic graphs. The right pattern depends on the task structure, quality requirements, and latency constraints.

```
SEQUENTIAL
  Step 1 → Step 2 → Step 3 → Output
  (each step depends on the previous)

PARALLEL
  Step 1A ──┐
  Step 1B ──┤ → Merge → Output
  Step 1C ──┘
  (steps are independent; run concurrently)

CONDITIONAL
  Input → Router → Step A (if condition X)
                 → Step B (if condition Y)
  (different paths based on content or quality)

LOOP
  Input → Step → Evaluate → [pass] → Output
                           → [fail] → Step (retry or refine)
  (iterate until quality threshold met)
```

| Pattern | Use Case | Latency | Complexity | Reliability Risk |
|---|---|---|---|---|
| **Sequential** | Document processing, structured analysis | Additive | Low | Error propagation |
| **Parallel** | Research aggregation, multi-source synthesis | Parallel (fastest) | Medium | Merge complexity |
| **Conditional** | Query routing, quality-gated workflows | Variable | Medium | Routing accuracy |
| **Loop** | Quality refinement, self-correction | Highest | High | Infinite loop risk |

---

## Pattern 1: Sequential Orchestration

### 1.1 When to Use Sequential

Sequential orchestration is the right choice when each step genuinely depends on the output of the previous step — not just because it is the simplest pattern to implement.

| Good Sequential Use Case | Poor Sequential Use Case |
|---|---|
| Extract → Analyse → Summarise (each step uses previous output) | Research A + Research B (independent — should be parallel) |
| Draft → Review → Refine (quality depends on prior output) | Multiple independent document transformations |
| Classify → Route → Process (routing depends on classification) | Parallel analyses that are merged at the end |

### 1.2 Sequential Pipeline Design

```
SEQUENTIAL PIPELINE TEMPLATE

Pipeline name: _______________________________________________
Total steps: ___
Estimated latency: ___ seconds (sum of step latencies + overhead)

Step 1: _______________________________________________
  Input: [what enters this step]
  Process: [what the model or tool does]
  Output: [what leaves this step]
  Latency target: ___ ms
  Error handling: [what happens if this step fails]

Step 2: _______________________________________________
  Input: [output from Step 1 + any additional context]
  Process: _______________________________________________
  Output: _______________________________________________
  Latency target: ___ ms
  Error handling: _______________________________________________

[Continue for all steps]

State management: [how is intermediate state passed between steps?]
Failure mode: [what does the user see if the pipeline fails at Step N?]
```

### 1.3 Prompt Chaining

In sequential orchestration, the output of one prompt becomes the input to the next. Design the handoff explicitly:

```
PROMPT CHAINING DESIGN

Step N output format:
[Define the exact format the Step N prompt should produce]

Step N+1 input injection:
[Define exactly how Step N output is injected into the Step N+1 prompt]

Context carried forward:
[What context from earlier steps should be retained throughout?]

Example:
Step 1 prompt: "Extract the 5 key claims from this document. Format as a numbered list."
Step 1 output: "1. [claim] 2. [claim] 3. [claim]..."
Step 2 prompt: "For each of the following claims, assess the evidence provided in the source document: [Step 1 output]"
```

---

## Pattern 2: Parallel Orchestration

### 2.1 When to Use Parallel

Parallel orchestration runs independent steps concurrently, then merges results. It dramatically reduces latency for workflows with multiple independent subtasks.

```
PARALLELISATION DECISION TEST

Ask: "Does Step B need Step A's output to begin?"
  Yes → Sequential (Step A must complete before Step B starts)
  No  → Parallel (Steps A and B can run concurrently)

Example — Research workflow:
  "Search source 1" — independent of source 2 → PARALLEL
  "Search source 2" — independent of source 1 → PARALLEL
  "Synthesise findings from source 1 and 2" — depends on both → SEQUENTIAL (after both complete)
```

### 2.2 Parallel Pipeline Design

```
PARALLEL PIPELINE TEMPLATE

Pipeline name: _______________________________________________
Parallel branches: ___
Sequential post-merge steps: ___
Estimated latency: max(branch latencies) + post-merge latency

Branch A: _______________________________________________
  Input: _______________________________________________
  Process: _______________________________________________
  Output format: _______________________________________________
  Latency target: ___ ms

Branch B: _______________________________________________
  [Same structure as Branch A]

Branch C: _______________________________________________
  [Same structure as Branch A]

Merge step: _______________________________________________
  Input: [outputs from Branches A, B, C]
  Merge strategy: [concatenate / synthesise / select best / vote]
  Merge prompt: _______________________________________________
  Output: _______________________________________________
```

### 2.3 Merge Strategies

| Merge Strategy | When to Use | Implementation |
|---|---|---|
| **Concatenate** | Independent analyses that should all be presented | Join outputs with structure |
| **Synthesise** | Multiple sources that should be unified into one answer | LLM synthesis prompt |
| **Select best** | Multiple attempts at the same task — pick the highest quality | Quality classifier selects winner |
| **Vote / majority** | Factual claims — confirm across multiple sources | Agreement detection |
| **Weighted merge** | Sources have different reliability levels | Apply confidence weights before synthesis |

---

## Pattern 3: Conditional Orchestration

### 3.1 Router Design

A router classifies the input and directs it to the appropriate processing path.

```
ROUTER DESIGN TEMPLATE

Router name: _______________________________________________
Input: [what the router receives]
Decision criteria: [what the router uses to decide]

Route A: _______________________________________________
  Trigger condition: _______________________________________________
  Processing path: _______________________________________________
  Example inputs: _______________________________________________

Route B: _______________________________________________
  Trigger condition: _______________________________________________
  Processing path: _______________________________________________
  Example inputs: _______________________________________________

Route C (fallback): _______________________________________________
  Trigger condition: [anything not matching A or B]
  Processing path: _______________________________________________

Router implementation:
  [ ] LLM classifier (use for nuanced classification)
  [ ] Rules-based classifier (use for clear-cut criteria)
  [ ] Embedding similarity (use for intent matching)
  [ ] Hybrid (rules first; LLM for edge cases)
```

### 3.2 Quality Gate Design

A quality gate evaluates whether a step's output meets the threshold required to proceed. If not, it routes to a refinement path.

```
QUALITY GATE TEMPLATE

Gate name: _______________________________________________
Input: [output from the preceding step]
Evaluation criteria:
  [ ] Factual accuracy: [how measured?]
  [ ] Completeness: [minimum elements required?]
  [ ] Format compliance: [required structure?]
  [ ] Length: [min/max token count?]
  [ ] Custom criteria: _______________________________________________

Pass threshold: _______________________________________________
  → Route to: [next step]

Fail — refine path: _______________________________________________
  → Route to: [refinement step with specific correction instructions]

Fail — hard stop (after N attempts): _______________________________________________
  → Return: [graceful failure response]
  → Log: [failure details for review]

Max retry attempts: ___  (recommended: 2–3; more creates latency and cost risk)
```

---

## Pattern 4: Loop Orchestration

### 4.1 Self-Refinement Loop

The most common loop pattern: generate → critique → refine → evaluate → repeat.

```
SELF-REFINEMENT LOOP DESIGN

Task: _______________________________________________
Quality threshold: _______________________________________________

Iteration 1:
  Generate: [initial generation prompt]
  Evaluate: [evaluation prompt — what criteria?]
  Score: [how is quality scored? 1–10? Pass/fail? Rubric?]

Iteration 2 (if score < threshold):
  Critique: [critique prompt — what specifically needs improvement?]
  Refine: [refinement prompt — apply critique to improve output]
  Re-evaluate: [same evaluation prompt]

Max iterations: ___  (MUST have a hard limit — recommended: 3)
Cost per iteration: $___  (understand the cost ceiling before setting max iterations)

Exit conditions:
  [ ] Score meets threshold → proceed
  [ ] Max iterations reached → return best output so far
  [ ] Consecutive scores declining → stop (model cannot self-improve further)

Output: [best output across all iterations, not just the last]
```

### 4.2 Loop Risk Controls

| Risk | Prevention |
|---|---|
| **Infinite loop** | Hard iteration limit — always |
| **Cost spiral** | Calculate max cost = max_iterations × cost_per_call; set budget limit |
| **Latency spiral** | Set max total loop time; exit if exceeded |
| **Quality regression** | Track score across iterations; exit if score drops two consecutive times |
| **Prompt amplification** | Each iteration's prompt grows with history — set max context per iteration |

---

## Tool Integration Architecture

### 5.1 Tool Types

| Tool Type | Examples | Integration Complexity |
|---|---|---|
| **Search tools** | Web search, vector search, SQL query | Low — query in, results out |
| **API tools** | CRM, calendar, Slack, external services | Medium — auth, rate limits, error handling |
| **Computation tools** | Code execution, calculation, data processing | Medium — sandboxing required |
| **File tools** | Read, write, transform documents | Medium — format handling |
| **Human-in-the-loop** | Approval step, human review | High — async handling required |
| **Agent tools** | Spawning sub-agents for subtasks | High — recursive orchestration |

### 5.2 Tool Call Design

```
TOOL DEFINITION TEMPLATE

Tool name: _______________________________________________
Description (what the model sees): [Write this to be unambiguous — the model decides when to call this tool based solely on this description]

Parameters:
  Required:
    [param_name]: [type] — [description]
  Optional:
    [param_name]: [type] — [description] — default: [value]

Returns:
  Success: [describe the return structure]
  Error: [describe the error return]

Rate limits: _______________
Authentication: _______________
Latency: ___ ms typical, ___ ms P99
Retry policy: _______________

Example call:
{
  "tool": "[tool_name]",
  "parameters": {
    "[param]": "[example value]"
  }
}

Example return:
{
  "result": "[example result]"
}
```

### 5.3 Tool Selection Prompt Design

When giving the model multiple tools, design the tool descriptions to minimise ambiguity about which tool to call:

```
TOOL SELECTION DESIGN PRINCIPLES

1. Each tool description must describe WHEN to use it, not just WHAT it does
   ✅ "Use this to search the web for current events or recent information not in your training data"
   ❌ "Searches the web"

2. Tools with overlapping capability need explicit disambiguation
   "Use search_internal for company documents. Use search_web for external sources."

3. Describe the expected input format in the tool description
   "Accepts a search query string of 5–15 words. Do not pass a question — pass keywords."

4. Describe limitations explicitly
   "Does not have access to documents uploaded in this session. Only searches the knowledge base."
```

---

## Orchestration Reliability

### 6.1 Error Handling Strategy

```
ERROR HANDLING MATRIX

Error Type | Detection | Response | Retry?
─────────────────────────────────────────────────────────────
Model timeout | Latency > threshold | Log + fallback | Yes (1×)
Model error | API error code | Log + retry | Yes (2×)
Output format failure | Schema validation fails | Correction prompt | Yes (1×)
Quality threshold failure | Evaluation score < min | Refinement loop | Yes (max N)
Tool call failure | Tool returns error | Alternative tool / graceful degrade | Depends
Budget exceeded | Cost counter > limit | Return best so far + alert | No
Context overflow | Token count > window | Compression + retry | Yes (1×)
Total pipeline failure | All retries exhausted | Graceful failure message | No
```

### 6.2 Observability

```
ORCHESTRATION OBSERVABILITY CHECKLIST

[ ] Every step emits a structured log entry (step_id, timestamp, input_tokens, output_tokens, latency_ms, success)
[ ] Total pipeline cost is tracked per run
[ ] Total pipeline latency is tracked per run
[ ] Step-level failure rates are monitored
[ ] Tool call success rates are monitored
[ ] Retry rates by step are monitored (high retry rate = step quality problem)
[ ] Alert on: total cost per run exceeds threshold
[ ] Alert on: step failure rate exceeds 5% in rolling window
[ ] Alert on: total pipeline p99 latency exceeds SLA
```

---

## Templates

### Template A: Orchestration Design Document

```
# Orchestration Design — [Workflow Name]
Date: ___  |  Author: ___  |  Version: ___

## Workflow Overview
[One paragraph: what this workflow does and why it is orchestrated rather than a single call]

## Pattern
[ ] Sequential  [ ] Parallel  [ ] Conditional  [ ] Loop  [ ] Hybrid

## Step Map
[Draw or describe the full step sequence with inputs, outputs, and routing]

## Tools Required
| Tool | Purpose | Auth | Rate Limit | Latency |
|------|---------|------|------------|---------|
|      |         |      |            |         |

## Cost Model
Estimated calls per run: ___
Average tokens per call: ___
Estimated cost per run: $___
Estimated monthly cost at [N] runs/day: $___

## Latency Model
Critical path length: ___ steps
Estimated total latency: ___ seconds
Latency SLA: ___ seconds

## Reliability Design
Retry policy: _______________________________________________
Circuit breaker: _______________________________________________
Graceful failure response: _______________________________________________

## Observability
Logging: _______________________________________________
Alerting: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Chaining steps without checking output quality between them | Add quality gates between critical steps |
| No hard limit on loop iterations | Always set max_iterations before deployment |
| Running sequential steps that could be parallel | Analyse dependencies; parallelise independent steps |
| Tool descriptions that are ambiguous or overlap | Write explicit disambiguation into every tool description |
| No error handling — pipeline fails silently | Define error response for every step and every error type |
| Not tracking cost per pipeline run | Instrument cost from day one — orchestration cost compounds |
| Passing full conversation history to every step | Pass only the context each step needs |
| No observability on intermediate steps | Emit structured logs at every step — not just the final output |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Step-level quality review | Weekly | Ongoing — monitor retry rates by step |
| Cost per run review | Monthly | Budget management |
| Latency SLA review | Monthly | User experience monitoring |
| Tool health check | Weekly | Tool failure rate monitoring |
| Full orchestration architecture review | Quarterly | Or on major feature change |
| Red team on loop workflows | Before each loop deployment | Test for runaway cost and latency |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Multi-Step AI Orchestration Pipeline

> **Best for:** Designing the complete workflow architecture for a task that requires multiple AI calls, tools, or decision points.

```
You are an AI systems architect helping me design a multi-step orchestration pipeline.

Given the task I describe, design the complete pipeline:

1. Decompose the task into atomic steps — identify what each step does and what it outputs
2. Identify dependencies — which steps require the output of a previous step (sequential) vs which are independent (parallel)
3. Select the orchestration pattern for each section: Sequential / Parallel / Conditional / Loop
4. Design the full pipeline with:
   - Input and output specification for each step
   - Error handling for each step
   - Quality gates where output quality determines the next action
5. Model the cost: estimated calls per run × average tokens × token price
6. Model the latency: critical path length in sequential steps + tool call overhead
7. Identify the top 3 reliability risks and how to mitigate each

After the design:
- Draw the pipeline as a text-based flow diagram
- Identify the single step most likely to cause pipeline failure
- Recommend whether to use a framework (LangChain / LlamaIndex / custom) for this pipeline

Task to orchestrate: [describe the end-to-end task]
Tools available: [list any APIs, databases, or tools the pipeline can call]
Latency SLA: [maximum acceptable response time]
Cost constraint: [maximum cost per pipeline run]
```

---

### Prompt 2 — Design Tool Definitions for an AI Agent

> **Best for:** Writing tool definitions that an LLM agent will use to decide when and how to call external tools.

```
You are a prompt engineer specialising in AI agent tool design. Help me write tool definitions that an LLM will use to call external tools accurately.

For each tool I describe, write:
1. Tool name (snake_case)
2. Description — written for the model, not for humans. Must include: when to use this tool, what it returns, and its limitations
3. Parameter schema — all parameters with type, description, required vs optional
4. Return schema — what success and error returns look like
5. Example call and return
6. Disambiguation notes — if this tool could be confused with another, explicitly state when to use this one vs the other

After writing all tools:
- Identify any tools with overlapping use cases and write disambiguation instructions
- Write a system prompt section that introduces the tools and instructs the model on tool selection behaviour
- Design the fallback behaviour when no tool is appropriate

Tools to define:
1. [Tool name — description of what it does]
2. [Tool name — description of what it does]
3. [Tool name — description of what it does]

Agent purpose: [what the agent is trying to accomplish]
User segment: [who the agent serves]
```

---

### Prompt 3 — Design a Self-Refinement Loop

> **Best for:** Any task where a single generation pass is insufficient and quality must be improved through iteration.

```
You are an AI quality engineer helping me design a self-refinement loop for an AI task.

Design a complete refinement loop with:

1. Generation step — write the initial generation prompt for this task
2. Evaluation step — write the evaluation prompt that scores the output (1–10 scale with explicit rubric)
3. Critique step — write the critique prompt that identifies specifically what needs improvement
4. Refinement step — write the refinement prompt that applies the critique to improve the output
5. Exit conditions — define: pass threshold, max iterations, regression detection logic

Also design:
- The quality rubric (what does a 10/10 look like? What does a 6/10 look like?)
- The cost ceiling: max_iterations × cost_per_call — confirm this is within budget
- The latency ceiling: max_iterations × avg_latency — confirm this meets the SLA
- How to select the best output across all iterations (not necessarily the last)

After the design:
- Identify the most common failure mode in refinement loops and how you've mitigated it
- Write 3 test cases with expected iteration counts and final quality scores

Task: [describe what the AI needs to produce]
Quality bar: [describe what excellent output looks like for this task]
Budget per run: $[number]
Latency SLA: [seconds]
```

---

### Prompt 4 — Diagnose and Fix an Orchestration Pipeline

> **Best for:** When a multi-step AI pipeline is failing, producing poor quality, or running over cost or latency budgets.

```
You are an AI systems diagnostician helping me debug and fix a failing orchestration pipeline.

I will describe the symptoms. For each symptom, diagnose the root cause and write a specific fix.

Diagnose across these failure categories:

1. Quality failures — output is technically produced but not good enough
   - Which step is introducing the quality degradation?
   - Is the step prompt underspecified? Is the output format ambiguous?

2. Reliability failures — the pipeline fails intermittently
   - Which step has the highest failure rate?
   - Is it a model error, tool error, or format validation failure?

3. Cost failures — the pipeline costs more than expected
   - Which step consumes the most tokens?
   - Are context sizes growing unexpectedly?

4. Latency failures — the pipeline is too slow
   - Which step is the bottleneck?
   - Are there sequential steps that could be parallelised?

5. Compounding failures — a failure at step N causes cascading failures downstream
   - Where is the error propagation happening?
   - What quality gates or fallbacks are missing?

For each root cause identified:
- Write the specific fix
- Estimate the improvement in quality / cost / latency
- Write a test case to validate the fix

Symptoms I am experiencing: [describe what is going wrong]
Current pipeline design: [describe the steps and their sequence]
Monitoring data available: [any error rates, latency data, cost data]
```

---

### Prompt 5 — Design Orchestration Observability

> **Best for:** Making a multi-step AI pipeline fully observable — knowing exactly what happened at every step of every run.

```
You are a platform engineer helping me design a complete observability system for an AI orchestration pipeline.

Design the observability system across four layers:

1. Step-level logging
   - What structured fields should every step log? (Write the exact schema)
   - What is the log storage strategy?
   - How are logs correlated across steps in the same pipeline run?

2. Pipeline-level metrics
   - List every metric I should track at the pipeline level
   - Define the dashboard layout: what are the top 5 metrics to show on the main view?

3. Alerting rules
   - Write 8 specific alert conditions with threshold, severity, and response action
   - Distinguish: investigate (non-urgent) vs degrade (reduce traffic) vs shut down (immediate action)

4. Debugging tooling
   - Design the step replay capability: how can I re-run a single step with its original inputs?
   - Design the trace view: how can I see the full execution path of a specific pipeline run?
   - Design the cost breakdown view: cost per step, per run, per user, per day

After designing all four layers:
- Write the first 5 queries I should run to debug a pipeline failure
- Recommend a specific observability stack for my scale and budget

My pipeline: [describe the workflow]
Expected daily run volume: [number]
Team size managing this pipeline: [number]
Budget for observability tooling: $[monthly]
```
