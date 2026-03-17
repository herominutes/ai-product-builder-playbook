# 🤖 Multi-Agent System — AI Product Builder Playbook

> **A framework for designing, building, and managing systems of coordinated AI agents that collaborate to solve complex tasks**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Multi-Agent Architecture Model](#the-multi-agent-architecture-model)
- [Agent Design](#agent-design)
- [Coordination Patterns](#coordination-patterns)
- [Communication Architecture](#communication-architecture)
- [State and Memory Across Agents](#state-and-memory-across-agents)
- [Multi-Agent Reliability](#multi-agent-reliability)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

A single AI agent is a capable but limited system. It can reason, call tools, and complete tasks — but it operates within a single context window, with a single model, and without the ability to genuinely specialise. Multi-agent systems solve this by distributing work across specialised agents that collaborate, check each other's work, and operate in parallel.

> **Core Principle:** Multi-agent systems are not multiple chatbots. They are distributed systems where each agent has a specific role, authority, and interface — and where the coordination between agents is as important to design as the agents themselves.

Multi-agent architectures introduce system design complexity that single-agent systems avoid. The question is not "can we build this as a multi-agent system?" — almost anything can be. The question is "does the complexity of multi-agent coordination produce better outcomes than a well-designed single-agent system?" Often, the answer is no.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Task is too complex for a single context window | 🔴 Critical — parallelisation or specialisation required |
| Task requires genuinely different expertise at different stages | 🔴 Critical — specialised agents outperform generalist |
| Quality improves significantly when one agent critiques another | 🟠 High — reviewer-agent pattern |
| Task must be completed in parallel across independent subtasks | 🟠 High — parallel agent pattern |
| A single agent is consistently hallucinating on specialised subtasks | 🟠 High — specialisation reduces hallucination |
| Building an autonomous AI product that handles end-to-end workflows | 🟠 High |
| Considering multi-agent when a single well-prompted agent would suffice | ❌ Do not — start simple |

---

## The Multi-Agent Architecture Model

Multi-agent systems have three structural components: the agents themselves, the coordination layer that manages them, and the communication channels between them.

```
ORCHESTRATOR AGENT
  ↓ decomposes tasks, assigns to specialists, aggregates results
SPECIALIST AGENTS
  ↓ each focused on a specific domain, role, or capability
TOOL LAYER
  ↓ shared or agent-specific tools (search, APIs, code execution)
SHARED STATE
  ↓ memory and context accessible across agents
COMMUNICATION CHANNELS
  ↓ structured messages between agents
```

| Component | Role | Design Decisions |
|---|---|---|
| **Orchestrator** | Task decomposition, agent selection, result aggregation | How smart should it be? When does it decide vs delegate? |
| **Specialist agents** | Domain-specific execution | How narrow should each specialisation be? |
| **Tool layer** | External capability access | Shared vs agent-specific tools? |
| **Shared state** | Cross-agent context | What is shared vs agent-private? |
| **Communication** | Inter-agent messaging | Synchronous vs asynchronous? Direct vs message-passing? |

---

## Agent Design

### 2.1 Agent Anatomy

Every agent in a multi-agent system has five components:

```
AGENT ANATOMY

1. Identity and role
   "You are [role]. Your specific responsibility is [task scope]."
   Every agent must have a clear, bounded role.

2. Capability set
   The tools this agent can call.
   Agents should only have access to tools their role requires.

3. Input schema
   The exact format of tasks assigned to this agent.
   Must be machine-readable and unambiguous.

4. Output schema
   The exact format of this agent's outputs.
   The orchestrator and other agents depend on this contract.

5. Decision authority
   What can this agent decide autonomously vs what requires escalation?
   Clear authority prevents both under-action and over-reach.
```

### 2.2 Agent Specialisation Levels

| Specialisation Level | Description | When to Use |
|---|---|---|
| **Domain specialist** | Deep expertise in one domain (legal, financial, technical) | When domain knowledge reduces hallucination |
| **Task specialist** | Focused on one type of task (research, writing, analysis) | When task type requires different prompting |
| **Role specialist** | Simulates a specific professional role (critic, editor, planner) | When role perspective improves quality |
| **Tool specialist** | Optimised for using a specific tool or API | When tool complexity warrants specialisation |
| **Quality specialist** | Reviews and critiques other agents' outputs | When self-review is insufficient |

### 2.3 Agent Prompt Design

The system prompt for a specialist agent must be tighter and more specific than a general-purpose agent:

```
SPECIALIST AGENT SYSTEM PROMPT STRUCTURE

Role definition:
"You are the [role] agent in a multi-agent system. Your only responsibility is [specific task].
You do not perform any task outside this scope."

Input handling:
"You will receive tasks in the following format:
[exact input schema]
Do not proceed if the input does not match this format — return a format error."

Output requirements:
"You must always return your output in the following format:
[exact output schema]
Never return output in any other format."

Scope constraints:
"You are not responsible for [list of related tasks explicitly out of scope].
If asked to perform these tasks, return: 'This is outside my scope. Please route to [agent name].'"

Quality standards:
"[Specific quality criteria for this agent's outputs]"

Escalation policy:
"Escalate to the orchestrator if: [specific escalation conditions]"
```

### 2.4 Agent Capability Matrix

Map every agent's tools and authority before building:

```
AGENT CAPABILITY MATRIX

| Agent | Tools | Can Read | Can Write | Can Call External | Can Spawn Sub-agent | Escalation Trigger |
|-------|-------|----------|-----------|-------------------|--------------------|--------------------|
| Orchestrator | | Shared state | Shared state | No | Yes | Never |
| Research agent | Web search, DB | Own memory | Task queue | Yes (search APIs) | No | Confidence < 70% |
| Analysis agent | Code execution | Task outputs | Analysis store | No | No | Data insufficient |
| Review agent | None | All outputs | Review log | No | No | Critical finding |
| Writer agent | Document tools | Analysis + Review | Output store | No | No | Missing information |
```

---

## Coordination Patterns

### 3.1 Orchestrator-Worker Pattern

The most common and recommended starting architecture. A single orchestrator coordinates all specialist workers.

```
ORCHESTRATOR-WORKER DESIGN

Orchestrator responsibilities:
1. Receive the user task
2. Decompose into subtasks
3. Assign each subtask to the appropriate specialist
4. Track completion status
5. Handle failures and reassign
6. Aggregate and synthesise results
7. Return final output to user

Worker responsibilities:
1. Receive an assigned subtask
2. Execute within defined scope
3. Return structured output
4. Report errors or blockers to orchestrator

Communication:
Worker → Orchestrator: task_complete | task_failed | escalation_needed
Orchestrator → Worker: task_assignment | clarification | cancellation
```

### 3.2 Pipeline Pattern

Agents are arranged in a linear sequence. Each agent's output becomes the next agent's input.

```
PIPELINE PATTERN

Agent 1 (Research) → Agent 2 (Analysis) → Agent 3 (Writing) → Agent 4 (Review) → Output

Use when:
- Tasks have clear sequential dependencies
- Each stage requires different specialisation
- Quality gates between stages are valuable

Risk: A failure at Stage N blocks all subsequent stages.
Mitigation: Quality gate + retry at each stage transition.
```

### 3.3 Peer Review Pattern

Two or more agents independently complete the same task. A reviewer agent compares and adjudicates.

```
PEER REVIEW PATTERN

Agent A: Complete [task]
Agent B: Complete [task] (independently, no visibility of Agent A's output)
Reviewer Agent: Compare outputs from A and B.
  - Where they agree: high confidence — pass through
  - Where they disagree: flag for resolution
  Resolution: Reviewer synthesises or escalates to orchestrator

Use when:
- Accuracy is critical and hallucination risk is high
- Two perspectives add genuine value
- Cost of errors exceeds cost of redundant generation

Cost: 2× generation cost + reviewer cost
Latency: max(Agent A, Agent B) + reviewer latency (parallel generation recommended)
```

### 3.4 Hierarchical Pattern

Orchestrators can spawn sub-orchestrators, creating a hierarchy of coordination.

```
HIERARCHICAL PATTERN

Master Orchestrator
  ├── Sub-orchestrator A (managing research cluster)
  │     ├── Research Agent 1
  │     ├── Research Agent 2
  │     └── Research Agent 3
  └── Sub-orchestrator B (managing writing cluster)
        ├── Writer Agent
        └── Editor Agent

Use when:
- Task complexity requires nested decomposition
- Different clusters of work are genuinely independent
- Single orchestrator would exceed context window

Risk: Coordination overhead multiplies. Communication failures cascade.
Rule: Do not go beyond 2 levels of hierarchy without strong justification.
```

---

## Communication Architecture

### 4.1 Message Schema

All inter-agent communication should use a structured message format:

```
AGENT MESSAGE SCHEMA

{
  message_id: "uuid",
  timestamp: "ISO-8601",
  from_agent: "agent_id",
  to_agent: "agent_id",
  message_type: "task_assignment | task_complete | task_failed | escalation | query | response",
  task_id: "uuid",  // links to the parent task
  payload: {
    // message_type-specific content
  },
  metadata: {
    priority: "high | medium | low",
    timeout_ms: 30000,
    retry_count: 0
  }
}
```

### 4.2 Task Assignment Schema

```
TASK ASSIGNMENT PAYLOAD

{
  task_description: "Clear description of what the agent must do",
  input_data: {
    // structured input the agent needs
  },
  output_format: {
    // exact schema the agent must return
  },
  constraints: {
    max_tokens: 2000,
    timeout_ms: 15000,
    quality_threshold: 0.8
  },
  context: {
    // relevant context from prior steps or shared state
  }
}
```

### 4.3 Synchronous vs Asynchronous Communication

| Mode | When to Use | Implementation |
|---|---|---|
| **Synchronous** | Orchestrator needs result before proceeding | Direct call + await response |
| **Asynchronous** | Parallel work; orchestrator continues while agents work | Message queue + callback |
| **Event-driven** | Agent completion triggers next step automatically | Event bus subscription |

---

## State and Memory Across Agents

### 5.1 Shared State Design

```
SHARED STATE SCHEMA

{
  task_id: "uuid",
  created_at: "ISO-8601",
  status: "in_progress | complete | failed",
  user_request: "original user request",
  subtasks: [
    {
      subtask_id: "uuid",
      assigned_to: "agent_id",
      status: "pending | in_progress | complete | failed",
      output: {}, // populated when complete
      error: {}   // populated if failed
    }
  ],
  intermediate_outputs: {
    research: {},
    analysis: {},
    draft: {}
  },
  final_output: {},
  audit_trail: [
    {timestamp, agent_id, action, details}
  ]
}
```

### 5.2 Agent-Private vs Shared Memory

| Memory Type | Access | Contents |
|---|---|---|
| **Agent-private** | This agent only | Working memory, intermediate reasoning, tool call history |
| **Task-shared** | All agents on this task | Task inputs, intermediate outputs, current status |
| **System-shared** | All agents, all tasks | Domain knowledge, user profile, procedural preferences |

---

## Multi-Agent Reliability

### 6.1 Failure Modes

| Failure Mode | Description | Mitigation |
|---|---|---|
| **Agent timeout** | Agent does not respond within deadline | Timeout policy + retry + fallback |
| **Cascade failure** | One agent's failure breaks downstream agents | Quality gates + graceful degradation |
| **Coordination deadlock** | Two agents waiting for each other | Timeout on all waits; orchestrator detects and resolves |
| **Context drift** | Agent's understanding of the task diverges from original intent | Periodic re-grounding with original task |
| **Authority conflict** | Two agents both attempt to modify shared state | Mutex on shared state writes |
| **Hallucination amplification** | One agent's hallucination is accepted as fact by the next | Cross-agent verification; human-in-the-loop checkpoints |

### 6.2 Human-in-the-Loop Checkpoints

Not all multi-agent workflows should be fully autonomous. Define explicitly where human review is required:

```
HUMAN-IN-THE-LOOP CHECKPOINT DESIGN

Checkpoint: _______________________________________________
Location in workflow: After [agent/step]
Trigger condition: [Always / If confidence < threshold / If output contains [flag]]
What the human sees: _______________________________________________
Human decision: [Approve / Revise / Reject]
  Approve → workflow continues
  Revise → human provides correction; workflow continues with correction
  Reject → workflow terminates; human handles manually
Timeout (if human does not respond): [Wait indefinitely / Proceed with caveat / Terminate]
```

---

## Templates

### Template A: Multi-Agent System Design Document

```
# Multi-Agent System Design — [System Name]
Date: ___  |  Author: ___  |  Version: ___

## System Purpose
[What end-to-end task does this system complete?]

## Justification for Multi-Agent Approach
[Why is a single agent insufficient? Be specific.]

## Agent Roster
| Agent Name | Role | Specialisation | Tools | Authority Level |
|------------|------|---------------|-------|-----------------|
|            |      |               |       |                 |

## Coordination Pattern
[ ] Orchestrator-Worker  [ ] Pipeline  [ ] Peer Review  [ ] Hierarchical

## Communication Architecture
Message format: _______________________________________________
Synchronous vs async: _______________________________________________
State management: _______________________________________________

## Human-in-the-Loop Checkpoints
| Checkpoint | Trigger | Human Decision |
|------------|---------|----------------|
|            |         |                |

## Reliability Design
Timeout policy: _______________________________________________
Failure handling: _______________________________________________
Cascade protection: _______________________________________________

## Cost Model
Agents: ___  |  Avg calls per task: ___  |  Est. cost per task: $___

## Latency Model
Critical path: ___ agents × avg latency = ___ seconds
Parallelisation opportunity: _______________________________________________
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Building multi-agent before trying single-agent | Always start with a single well-prompted agent; add agents only when needed |
| Agents without bounded scope | Every agent must have explicit scope — what it does AND does not do |
| No structured message format between agents | Define a strict schema for all inter-agent communication |
| Fully autonomous agents in high-stakes domains | Always include human-in-the-loop checkpoints for consequential actions |
| No shared state — agents pass state in natural language | Use structured shared state; natural language is ambiguous at scale |
| No timeout policy | Every agent call must have a timeout; every timeout must have a handler |
| More than 2 levels of agent hierarchy | Complexity compounds exponentially; flatten before adding hierarchy |
| No observability into individual agent calls | Log every agent call with inputs, outputs, latency, and cost |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Agent quality audit | Weekly | Sample outputs from each agent |
| Coordination efficiency review | Monthly | Are agents waiting on each other unnecessarily? |
| Cost per task review | Monthly | Cost per agent, per task, per day |
| Failure rate analysis | Monthly | Which agents fail most often and why? |
| Human checkpoint utilisation | Monthly | Are checkpoints triggering appropriately? |
| Full system architecture review | Quarterly | Or on major capability change |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Multi-Agent System Architecture

> **Best for:** Designing the complete architecture for a multi-agent AI system from scratch.

```
You are an AI systems architect helping me design a multi-agent system.

First, assess whether a multi-agent approach is justified:
- What is the task? Can a single well-prompted agent with good tools complete it?
- If yes: recommend the single-agent approach instead
- If no: proceed with multi-agent design

If multi-agent is justified, design the complete system:

1. Agent roster — list every agent with: name, role, specialisation, tool access, authority level
2. Coordination pattern — select and justify: Orchestrator-Worker / Pipeline / Peer Review / Hierarchical
3. Communication architecture — message schema, synchronous vs async, state management
4. Shared state design — what is shared across agents vs agent-private
5. Human-in-the-loop checkpoints — where human review is required and how it works
6. Reliability design — timeout policy, failure handling, cascade protection

After the design:
- Model the cost per task: agents × calls × token cost
- Model the critical path latency
- Identify the top 3 reliability risks and specific mitigations

Task to be automated: [describe the end-to-end task]
Quality requirements: [what does excellent output look like?]
Stakes if agents make errors: [low / medium / high — describe consequences]
Latency SLA: [maximum acceptable time]
Budget per task run: $[number]
```

---

### Prompt 2 — Write Specialist Agent System Prompts

> **Best for:** Writing the system prompts for each specialist agent in a multi-agent system.

```
You are a prompt engineer specialising in multi-agent AI systems. Write the system prompts for each specialist agent I describe.

For each agent, write a system prompt that includes:
1. Role definition — clear, bounded, specific to this agent
2. Input handling — the exact input format expected and what to do if input doesn't match
3. Output requirements — the exact output schema this agent must return
4. Scope constraints — explicit list of what this agent does NOT do
5. Quality standards — what excellent output from this agent looks like
6. Escalation policy — when and how to escalate to the orchestrator

After writing all agent prompts:
- Write the orchestrator system prompt that coordinates all specialist agents
- Write the message schema for inter-agent communication
- Test each prompt with a sample input and show the expected output

Agents to write prompts for:
1. [Agent name — role description]
2. [Agent name — role description]
3. [Agent name — role description]

System purpose: [what the overall multi-agent system does]
Coordination pattern: [Orchestrator-Worker / Pipeline / Peer Review]
```

---

### Prompt 3 — Design the Orchestrator Logic

> **Best for:** Designing the intelligence layer that coordinates specialist agents — how it decomposes tasks, assigns work, and handles failures.

```
You are an AI systems designer helping me build the orchestrator logic for a multi-agent system.

Design the orchestrator across five functions:

1. Task decomposition
   - How does the orchestrator break a complex user request into subtasks?
   - Write the decomposition prompt the orchestrator uses
   - How does it handle tasks that don't decompose cleanly?

2. Agent selection
   - How does the orchestrator decide which agent to assign each subtask to?
   - Write the selection logic (rule-based / LLM-based / hybrid)
   - How does it handle a subtask that no agent is equipped for?

3. Dependency management
   - How does the orchestrator track which subtasks depend on others?
   - How does it schedule parallel subtasks vs sequential ones?
   - Write the dependency resolution algorithm

4. Result aggregation
   - How does the orchestrator combine outputs from multiple agents?
   - Write the aggregation prompt
   - How does it handle conflicting outputs from different agents?

5. Failure handling
   - What does the orchestrator do when an agent fails?
   - Write the retry logic, reassignment logic, and graceful degradation plan

After designing all five functions:
- Write the complete orchestrator system prompt
- Design the orchestrator's shared state schema
- Identify the 3 most likely orchestrator failures and the mitigation for each

My agent roster: [list agents and their capabilities]
Task types the system handles: [describe]
Failure tolerance: [what happens if the orchestrator cannot complete a task?]
```

---

### Prompt 4 — Design Human-in-the-Loop Checkpoints

> **Best for:** Defining where and how humans should be inserted into an autonomous multi-agent workflow for quality and safety.

```
You are an AI product safety specialist helping me design human-in-the-loop checkpoints for a multi-agent system.

For the system I describe, identify where human oversight is required and design the checkpoint experience:

1. Checkpoint identification
   - Analyse the workflow and identify every point where a human should review before proceeding
   - For each point: why is human review needed? What could go wrong without it?
   - Classify each checkpoint: Required (always) / Conditional (if risk threshold exceeded) / Optional (user preference)

2. Checkpoint design
   For each required or conditional checkpoint:
   - What does the human see? (output from agents + confidence level + what decision is being requested)
   - What are the human's options? (Approve / Revise / Reject)
   - What happens for each choice?
   - What is the timeout behaviour if the human doesn't respond?

3. Risk calibration
   - At what confidence level should conditional checkpoints trigger?
   - How do we prevent checkpoint fatigue (too many approvals = humans stop reading them)?
   - How do we ensure checkpoints are fast enough that they don't break the user experience?

4. Audit trail
   - What gets logged at each checkpoint? (human decision, time to decide, any revision made)
   - How is this used for quality improvement?

My multi-agent system: [describe the workflow]
Stakes of errors: [low / medium / high — describe consequences]
User's tolerance for interruption: [how often can we interrupt with approval requests?]
Regulatory requirements: [any compliance requirements for human oversight]
```

---

### Prompt 5 — Debug a Multi-Agent System Failure

> **Best for:** When a multi-agent system is producing poor results, failing intermittently, or running over budget.

```
You are an AI systems diagnostician helping me debug a multi-agent system that is not working correctly.

I will describe the symptoms. Diagnose across these failure categories:

1. Agent-level failures
   - Is a specific agent producing poor quality outputs?
   - Is an agent hallucinating or going out of scope?
   - Is an agent's system prompt too vague or ambiguous?

2. Coordination failures
   - Is the orchestrator decomposing tasks incorrectly?
   - Is context being lost between agent handoffs?
   - Are agents waiting for each other unnecessarily?

3. State failures
   - Is shared state being corrupted or overwritten?
   - Are agents working with stale or conflicting information?

4. Communication failures
   - Are messages between agents in the wrong format?
   - Is context being dropped or misinterpreted in transit?

5. Reliability failures
   - Are timeouts configured correctly?
   - Is cascade failure occurring when one agent fails?
   - Is the system retrying unnecessarily?

For each root cause identified:
- Describe the specific failure mechanism
- Write the specific fix
- Write a test case to confirm the fix

Symptoms: [describe what is going wrong — poor outputs, errors, timeouts, cost overruns]
System design: [describe your current agent roster and coordination pattern]
Any monitoring data: [error rates, latency, cost per agent]
```
