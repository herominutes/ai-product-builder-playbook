# 📡 Communication and Handoffs — AI Product Builder Playbook

> **A framework for designing clear, consistent communication practices and seamless handoffs that keep teams aligned and context intact across the full product lifecycle**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The Communication Model](#the-communication-model)
- [Communication Type 1: Team Communication](#communication-type-1-team-communication)
- [Communication Type 2: Stakeholder Communication](#communication-type-2-stakeholder-communication)
- [Communication Type 3: Cross-Functional Handoffs](#communication-type-3-cross-functional-handoffs)
- [Communication Type 4: Incident Communication](#communication-type-4-incident-communication)
- [AI Product Communication Specifics](#ai-product-communication-specifics)
- [Building a Communication Culture](#building-a-communication-culture)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Most product failures are communication failures before they are execution failures. The engineer who builds the wrong thing because the requirement was ambiguous. The designer whose work is ignored because it arrived too late. The executive who makes a bad decision because the data was buried in a Notion page nobody reads. These are not talent failures — they are system failures, and they are preventable with deliberate communication design.

> **Core Principle:** Communication is infrastructure, not overhead. A team that invests in clear communication norms, reliable handoff protocols, and predictable stakeholder updates moves faster — not slower — than a team that treats every communication as an ad hoc event. The overhead is in the exceptions, not the system.

For AI products, communication has an additional layer of complexity. AI behaviour is probabilistic and often opaque. Communicating what an AI feature does, why it produced a particular output, and what the quality trajectory looks like requires language and formats that most organisations have not yet developed. This framework addresses both standard product communication and the AI-specific communication challenges.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| Team is building misaligned to expectations | 🔴 Critical — communication failure |
| Context is lost between discovery, design, and engineering | 🔴 Critical — handoff failure |
| Stakeholders are surprised by product decisions | 🔴 Critical — update cadence failure |
| An AI incident was communicated poorly | 🔴 Critical — incident communication failure |
| Scaling team — new members struggle to understand context | 🟠 High |
| Cross-functional friction between PM, Design, and Engineering | 🟠 High |
| Building communication norms for a new team | 🟡 Medium |

---

## The Communication Model

Effective product communication operates across four types. Each type has different audiences, different cadences, and different quality standards.

```
TEAM COMMUNICATION
  ↓ keeping the build team aligned day-to-day
STAKEHOLDER COMMUNICATION
  ↓ keeping leadership and partners informed and aligned
CROSS-FUNCTIONAL HANDOFFS
  ↓ transferring context between functions without loss
INCIDENT COMMUNICATION
  ↓ communicating clearly when things go wrong
```

| Type | Primary Audience | Failure Mode | Key Standard |
|---|---|---|---|
| **Team** | PM, Design, Engineering | Context loss, misalignment | Clarity and frequency |
| **Stakeholder** | Leadership, executives, partners | Surprise, distrust | Proactivity and brevity |
| **Handoff** | Next function in the chain | Misinterpretation, rework | Completeness and precision |
| **Incident** | All affected parties | Panic, misinformation | Speed and honesty |

---

## Communication Type 1: Team Communication

### 1.1 Team Communication Principles

```
TEAM COMMUNICATION PRINCIPLES

1. Written over verbal for decisions
   Verbal discussions generate insights. Written communication records decisions.
   Every decision made verbally must be confirmed in writing within 24 hours.

2. Async over sync where possible
   Synchronous time is the team's scarcest resource.
   Use it for things that require real-time collaboration.
   Use async for updates, status, and anything that can wait.

3. Single source of truth
   Every piece of important information lives in one place.
   Links, not copies. Updates flow to the source, not to every copy.

4. Context-rich, not verbose
   Good team communication provides the context needed to act — not every detail.
   "We changed X because Y showed us Z" is better than "we changed X" and better than
   a 500-word explanation of the entire decision history.

5. Explicit, not implicit
   "This is done" vs "I think this is done."
   "Please decide by Thursday" vs "let me know your thoughts."
   Ambiguity in team communication is a cost passed on to the reader.
```

### 1.2 Async Communication Standards

```
ASYNC COMMUNICATION STANDARDS

Update format (for status updates in Slack, Notion, etc.):
  [DONE] — [what was completed] — [link if relevant]
  [BLOCKED] — [what is blocked] — [what is needed to unblock] — [from whom]
  [DECISION NEEDED] — [the decision] — [context] — [deadline]
  [FYI] — [information, no action needed]

Decision confirmation format:
  "Decision confirmed: [what was decided]. Owner: [name]. By when: [date]. 
   This was discussed in [context]. See [link] for full background."

Request format:
  "Request: [specific ask]. Context: [why this matters]. Deadline: [when needed]. 
   If not responded to by [date], I will assume [default action]."
```

### 1.3 Meeting Communication Standards

```
MEETING STANDARDS

Every meeting must have:
[ ] A written agenda sent at least 24 hours before
[ ] A clear objective: decision / alignment / exploration (one only)
[ ] A named facilitator and a named note-taker
[ ] An end with explicit next actions (what, who, when)
[ ] Written notes distributed within 2 hours of the meeting

Meeting types and appropriate length:
  Daily standup: 15 minutes (status only — no problem-solving)
  Sprint planning: 1–2 hours (scope and commitment)
  Design critique: 60 minutes (feedback, not approval)
  Stakeholder review: 30–45 minutes (update + questions)
  Retrospective: 60 minutes (reflection + actions)
  Decision meeting: 30 minutes (focused — pre-read required)

Cancel the meeting if:
  The agenda has not been written 24 hours before
  The objective is "to discuss" without a specific question
  All participants could read an update instead
```

---

## Communication Type 2: Stakeholder Communication

### 2.1 Stakeholder Communication Principles

```
STAKEHOLDER COMMUNICATION PRINCIPLES

1. Proactive over reactive
   Stakeholders should never discover news from a source other than the PM.
   If something has changed — good or bad — the PM communicates it first.

2. Brief over comprehensive
   Executives read the first paragraph. They skim the rest.
   Lead with the conclusion. Support with evidence. Put detail in an appendix.

3. Signal over noise
   Not every data point deserves stakeholder attention.
   Curate: what is the single most important thing they need to know this week?

4. No surprises
   A stakeholder who is surprised — positively or negatively — by a product development
   is a stakeholder who was not communicated with effectively.
   The goal is zero surprises, not zero bad news.

5. Honest about uncertainty
   "We expect [X] but are not certain" is more credible than false confidence.
   Stakeholders who are given honest uncertainty are better partners than ones who are managed.
```

### 2.2 Stakeholder Update Formats

```
WEEKLY PRODUCT UPDATE (for executive team)

Format: Email or Slack — maximum 200 words in the body

Subject: Product Update — Week of [date]

[1 sentence: the most important thing that happened this week]

Wins:
• [specific accomplishment with metric if possible]
• [specific accomplishment]

Risks / flags:
• [anything leadership needs to be aware of or decide]

Next week:
• [what we are focused on]

Full details: [link to product dashboard or weekly notes]

---

MONTHLY STAKEHOLDER REVIEW (for exec team + board)

Format: 30-minute meeting with pre-read document

Pre-read covers (1 page max):
  North Star: [current value vs target]
  Key metrics: [3–5 metrics, current vs target]
  Top 3 decisions made this month
  Top 3 decisions needed next month
  Primary risk on the radar

Meeting agenda:
  5 min: metrics review
  10 min: top decisions + rationale
  10 min: upcoming decisions — input needed
  5 min: questions
```

### 2.3 Bad News Communication

```
BAD NEWS COMMUNICATION PROTOCOL

Rule: Bad news ages badly. Communicate it early, clearly, and with a plan.

Structure:
  1. What happened (factual, specific — not defensive)
  2. Why it happened (root cause — not excuse-making)
  3. What we are doing about it (concrete actions, owners, timelines)
  4. What we expect the outcome to be (honest uncertainty acknowledged)

Timing: As soon as the bad news is known — not after the fix is in place.
Channel: Direct, not buried in a weekly update.
Tone: Honest, calm, solution-oriented.

What NOT to do:
  ❌ Bury bad news in a long update
  ❌ Wait until you have a solution before communicating the problem
  ❌ Use passive voice to obscure accountability
  ❌ Minimise the severity to manage stakeholder reaction

The single rule: If you would feel uncomfortable if a stakeholder discovered
this through another channel, you should communicate it to them directly, now.
```

---

## Communication Type 3: Cross-Functional Handoffs

### 3.1 The Handoff Problem

Context loss between functions is one of the most expensive and preventable costs in product development. When discovery hands off to design, design hands off to engineering, or engineering hands off to QA, the information required to execute correctly is almost always transmitted incompletely. What follows is rework, misalignment, and delays.

### 3.2 Discovery-to-Design Handoff

```
DISCOVERY → DESIGN HANDOFF

Purpose: Transfer user research findings into design inputs without losing nuance.

Handoff document must include:
[ ] Problem statement (validated — not assumed)
[ ] Primary user persona with context and AI literacy profile (if AI product)
[ ] User journey map (current state with pain points)
[ ] Key insights from research (with direct quotes)
[ ] Constraints (technical, regulatory, business)
[ ] Success criteria (what does a successful design outcome look like?)
[ ] Open questions (what does design need to answer?)
[ ] What is explicitly out of scope

Handoff meeting (30–45 minutes):
  PM walks design through the problem — not the solution
  Design asks questions — PM answers without proposing UI solutions
  Together: agree on the design brief and success criteria
  Output: Signed-off design brief that both PM and Design can reference

Common handoff failures:
  PM hands over a wireframe sketch alongside the brief (constrains design)
  Brief is too vague ("make it delightful") or too specific ("it must have a button here")
  No agreed success criteria — design has no way to know when they are done
```

### 3.3 Design-to-Engineering Handoff

```
DESIGN → ENGINEERING HANDOFF

Purpose: Transfer design intent into engineering specifications without ambiguity.

Handoff package must include:
[ ] Final designs in the agreed tool (Figma, etc.) — all states, not just the happy path
[ ] Component specifications (sizes, spacing, typography, colours)
[ ] All interactive states (hover, focus, disabled, loading, error, empty)
[ ] All AI states (loading, output, low confidence, error, out of scope)
[ ] Mobile and responsive breakpoints
[ ] Accessibility requirements
[ ] Animation specifications (if any)
[ ] Edge cases explicitly designed (not left for engineering to decide)
[ ] What is intentionally NOT designed (deferred to V2)

Handoff meeting (45–60 minutes):
  Design walks engineering through every state — no assumptions
  Engineering raises technical concerns or constraints
  Together: agree on which edge cases can be simplified for V1
  Output: Engineering has every question answered before coding begins

Common handoff failures:
  Only the happy path is designed — error states are "to be determined"
  No mobile designs — assumed to be "like the desktop version"
  AI states not designed — "engineering will figure it out"
  Specifications are in the designer's head, not in the handoff package
```

### 3.4 Engineering-to-QA Handoff

```
ENGINEERING → QA HANDOFF

Purpose: Transfer implementation context into a test plan that catches real issues.

Handoff document must include:
[ ] What was built (feature description, not technical jargon)
[ ] What changed from the design (and why)
[ ] Known limitations or edge cases not handled in V1
[ ] Areas of highest technical risk (where bugs are most likely)
[ ] Environment and configuration requirements for testing
[ ] For AI features: test cases that specifically probe AI failure modes
[ ] Rollback procedure if critical bugs are found

For AI features, test plan must include:
[ ] Happy path: AI produces correct output
[ ] Quality edge cases: near-miss inputs that might fool the model
[ ] Out-of-scope requests: does the AI refuse appropriately?
[ ] Adversarial inputs: prompt injection attempts
[ ] Latency testing: does the UX degrade gracefully under slow AI response?
[ ] Failure state testing: what does the user see when the AI fails?
```

---

## Communication Type 4: Incident Communication

### 4.1 Incident Communication Principles

```
INCIDENT COMMUNICATION PRINCIPLES

Speed over perfection: A fast, incomplete update is better than a slow, comprehensive one.
Honesty over management: Say what you know; say what you don't know; say what you're doing.
One voice: A single named person owns all external communication.
Update cadence: Communicate on a fixed schedule — every [30 min / 1 hour / 2 hours] — even if the update is "no change."
Separate internal from external: Internal updates can be more detailed; external updates should be plain language.
```

### 4.2 Incident Communication Timeline

```
INCIDENT COMMUNICATION TIMELINE

T+0: Incident detected
  Internal: Alert on-call PM and engineering lead via [PagerDuty / Slack #incidents]
  Action: Assess severity (P1 / P2 / P3)

T+15 minutes (P1/P2): Internal status update
  Channel: #incidents Slack or equivalent
  Format: "INCIDENT — [what is happening] — [who is affected] — [what we are doing] — [next update in X minutes]"

T+30 minutes (P1): Stakeholder notification
  Who: CPO + CTO (and Legal if user data involved)
  Format: Brief (< 100 words): what happened, who is affected, what we are doing, expected resolution time

T+1 hour (if unresolved): External user communication (P1 only)
  Channel: Status page / in-product banner / email
  Format: "We are aware of an issue affecting [feature]. Our team is working to resolve it.
           We will update again by [time]. We apologise for the impact."

T+resolution: Resolution communication
  Internal: Full timeline + root cause + resolution
  External: "The issue affecting [feature] has been resolved. [Brief explanation if appropriate]. 
             We will share a full retrospective within [N] days."

T+48 hours (P1/P2): Post-incident retrospective
  Audience: Internal engineering and PM team
  Content: Timeline, root cause, what went wrong in detection/response, action items
```

---

## AI Product Communication Specifics

### 5.1 Communicating AI Quality

AI quality is difficult to communicate because it is probabilistic, not binary. These formats help:

```
AI QUALITY COMMUNICATION FORMATS

For the team (technical):
"AI quality score this week: 4.1 / 5 (target: 4.0). Up from 3.9 last week.
Top failure category: format compliance (18% of poor outputs). Root cause: system prompt 
ambiguity in structured output section. Fix deployed Monday — monitor through end of week."

For stakeholders (non-technical):
"The AI feature is performing above target. Users are accepting 67% of AI outputs 
without modification (target: 60%). The main area of improvement is how the AI 
formats structured data — we are addressing this and expect improvement next week."

For users (simple):
"We've made improvements to how the AI formats its responses. You may notice 
cleaner, more consistent output starting this week."

Standard: Always give the number AND the interpretation. Never give just the number.
```

### 5.2 Communicating AI Limitations

```
AI LIMITATION COMMUNICATION STANDARDS

Internal standard (for team):
  Document limitations in the AI PRD before launch.
  Update the limitation list as new failure modes are discovered in production.

Stakeholder standard:
  "The AI works well for [use case A] but has limitations in [use case B].
   We are monitoring and plan to address this in [timeframe]."

User standard:
  Proactive: "The AI works best on [specific use case]. For [different use case], 
              you may want to [alternative]."
  Reactive (when user encounters limitation): "The AI couldn't help with this one. 
              [Here is what you can do instead.]"

Never:
  Imply the AI can do something it cannot
  Use passive voice to avoid owning the limitation
  Promise a fix without a realistic timeline
```

---

## Building a Communication Culture

### 6.1 Communication Norms Document

```
TEAM COMMUNICATION NORMS — [Team Name]

How we make decisions:
  All significant decisions are made by a named owner.
  Decisions are documented in the decision log within 24 hours.
  We use the disagree-and-commit protocol when team members disagree.

How we share updates:
  Status updates go in [Slack channel] using the standard format.
  Weekly written update shared by PM every [day].
  No news is not the same as good news — silence is not a valid status.

How we run meetings:
  Every meeting has a written agenda 24 hours before.
  Every meeting ends with written next actions.
  We cancel meetings where a written update would suffice.

How we handle bad news:
  Bad news is communicated as soon as it is known — not after it is fixed.
  We communicate directly, not through intermediaries.
  We lead with facts, then root cause, then plan.

How we handle handoffs:
  Discovery-to-Design: [link to handoff template]
  Design-to-Engineering: [link to handoff template]
  Engineering-to-QA: [link to handoff template]

Our communication tools:
  Async updates: [Slack / Teams]
  Decisions and docs: [Notion / Confluence]
  Design: [Figma]
  Project tracking: [Jira / Linear]
  Single source of truth for: [each document type → tool mapping]
```

---

## Templates

### Template A: Handoff Brief

```
# Handoff Brief — [Discovery / Design / Engineering] to [Design / Engineering / QA]
Feature: _______________________________________________
From: ___  |  To: ___  |  Date: ___

## What Was Completed
[Summary of what the sending function delivered]

## Key Decisions Made (and why)
1. _______________________________________________
2. _______________________________________________

## Known Limitations / Out of Scope for V1
1. _______________________________________________
2. _______________________________________________

## Open Questions for the Receiving Function
1. _______________________________________________
2. _______________________________________________

## Success Criteria
[How does the receiving function know they have done their job correctly?]

## Handoff Meeting
[ ] Meeting scheduled: ___  |  Duration: ___
[ ] Questions answered before meeting ends
[ ] Handoff confirmed: Receiving function confirms they have what they need
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Verbal-only decisions with no written record | All decisions confirmed in writing within 24 hours |
| Status updates buried in long Slack threads | Standard status format with clear signal words [DONE] [BLOCKED] [DECISION] |
| Stakeholder surprises — good or bad | Proactive communication before stakeholders hear from another source |
| Handoffs without a meeting | Always run a handoff meeting — written docs are necessary but not sufficient |
| Incident communication delayed until resolution | Communicate as soon as detected; update on a fixed cadence |
| AI quality communicated as binary (working / not working) | Always communicate quality as a spectrum with number and interpretation |
| Meeting without agenda and next actions | No agenda = cancel the meeting; no next actions = the meeting failed |
| "No news is good news" communication style | Active silence signals must be replaced with explicit "no change" updates |

---

## Cadence

| Activity | Frequency | Owner |
|---|---|---|
| Team written standup | Daily | PM |
| Weekly stakeholder update | Weekly | PM |
| Monthly executive review | Monthly | PM |
| Handoff meeting | Per phase transition | PM |
| Communication norms review | Quarterly | PM + team |
| Incident retrospective | After every P1/P2 | PM + Eng |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Write a Stakeholder Update

> **Best for:** Drafting a clear, concise stakeholder update that communicates progress, risks, and decisions without overwhelming the reader.

```
You are a product communication specialist helping me write a stakeholder update.

Write a stakeholder update for the situation I describe, following these standards:
- Maximum 200 words in the body
- Lead with the most important thing — not background
- Wins: specific, with metrics where possible
- Risks / flags: honest, with an action or owner for each
- Next week: what the team is focused on
- No jargon; no passive voice; no hedging

Also write:
- The subject line (< 10 words, states the key news)
- A 1-sentence verbal summary I can use if asked in the hallway

After the update:
- Identify anything I am softening that should be stated more directly
- Identify anything I should have included that I left out

My situation: [describe what happened this week — wins, misses, decisions, risks]
Audience: [who is receiving this — CEO / CPO / board / investors]
Primary concern of this audience: [what do they care most about?]
Most important thing for them to know: [what would you lead with?]
```

---

### Prompt 2 — Design a Cross-Functional Handoff

> **Best for:** Creating the handoff document and meeting structure for a transition between discovery, design, or engineering.

```
You are a product process designer helping me design a cross-functional handoff.

Design the complete handoff for the transition I describe:

1. Handoff document
   - What must be included for the receiving function to have everything they need?
   - What are the most common gaps in this type of handoff?
   - Write the template with specific sections and guidance for each

2. Handoff meeting structure
   - What should be covered in the handoff meeting?
   - What questions should the receiving function ask?
   - What is the confirmation that the handoff is complete?

3. Quality check
   - How does the receiving function confirm they have everything they need?
   - What signal indicates the handoff was incomplete?
   - How do we close the loop when a gap is discovered mid-execution?

4. For AI product handoffs specifically
   - What AI-specific information must be included in this type of handoff?
   - How are AI failure states communicated in the handoff?
   - What does the receiving function need to know about AI quality requirements?

Handoff type: [Discovery → Design / Design → Engineering / Engineering → QA]
Feature being handed off: [describe what was completed by the sending function]
Known gaps or risks: [what do you already know is incomplete or uncertain?]
Is this an AI feature: [yes/no — if yes, describe the AI component]
```

---

### Prompt 3 — Communicate Bad News to Stakeholders

> **Best for:** Drafting the communication for a metric miss, a delayed launch, a quality failure, or any other negative development.

```
You are a product communications advisor helping me communicate bad news to stakeholders.

Draft the bad news communication following the standard structure:
1. What happened (factual, specific, no hedging)
2. Why it happened (root cause, not excuses)
3. What we are doing about it (concrete, owned, time-bound)
4. What we expect the outcome to be (honest about uncertainty)

Also advise:
- Should this be communicated now or after more investigation? (bias toward now)
- What channel is appropriate for this severity? (direct message / email / meeting)
- What questions will the stakeholder ask and what are the answers?
- What is the single most important thing to avoid saying? (the thing that would damage trust)

After drafting:
- Identify any softening language I should remove
- Identify any detail I am omitting that the stakeholder will notice is missing
- Write the verbal version for a 60-second spoken update

The bad news: [describe what happened]
Audience: [who needs to hear this and what do they care about most?]
What I know for certain: [facts]
What I don't yet know: [open questions]
What I am doing about it: [current actions]
```

---

### Prompt 4 — Run an Incident Communication

> **Best for:** During or immediately after an AI product incident — drafting all required communications for each audience.

```
You are a crisis communications specialist helping me communicate through an AI product incident.

Write all required communications for the incident I describe:

1. Internal team alert (immediate — within 15 minutes of detection)
   - Format: Slack message in #incidents
   - Content: what is happening, who is affected, what is being done, next update time

2. Executive notification (within 30 minutes — P1/P2 only)
   - Format: Direct message or email
   - Content: < 100 words — what happened, scope, action, ETA

3. External user communication (within 1 hour — P1 only)
   - Format: Status page / in-product banner
   - Content: Plain language, no jargon, empathetic, action-oriented

4. Resolution communication (when resolved)
   - Format: All channels that received an incident update
   - Content: What was resolved, brief explanation, what we are doing to prevent recurrence

5. Post-incident retrospective summary (within 48 hours)
   - Format: Internal document
   - Content: Timeline, root cause, what went wrong, action items with owners

For all communications:
- No jargon or technical language in user-facing or executive communications
- No passive voice
- Lead with the impact on the user, not the technical problem
- Never promise a timeline you are not confident in

The incident: [describe what happened, who was affected, what you know about the cause]
Current status: [ongoing / resolved]
Number of users affected: [estimate]
```

---

### Prompt 5 — Build a Team Communication Norms Document

> **Best for:** Establishing clear communication practices for a new or growing team — creating shared expectations that reduce friction.

```
You are an organisational design expert helping me create a communication norms document for my product team.

Write a complete, practical communication norms document that covers:

1. Decision communication
   - How decisions are made (who decides, who is consulted, who is informed)
   - How decisions are documented and shared
   - How disagreements are handled (disagree and commit protocol)

2. Async communication
   - What goes in which channel (Slack / email / doc / ticket)
   - Standard formats for status updates, requests, and decisions
   - Response time expectations by urgency level

3. Meeting standards
   - What types of meetings we have and their purposes
   - Agenda and note requirements
   - When to cancel a meeting

4. Handoff standards
   - Brief description of the handoff process for each transition
   - What makes a handoff complete
   - How gaps discovered mid-execution are handled

5. Stakeholder communication
   - Update cadence and format for executive team
   - How bad news is communicated
   - Zero surprises standard

For AI products, add:
- How AI quality is communicated to different audiences
- How AI limitations are disclosed
- How AI incidents are communicated

After writing the document:
- Identify the 2–3 norms most likely to be violated and why
- Write the team onboarding exercise that makes these norms real for new members

My team: [size, roles, remote/hybrid/in-person]
Current communication problems: [what is not working?]
Tools in use: [Slack / Notion / Jira / etc.]
Product type: [AI product / traditional / mixed]
```
