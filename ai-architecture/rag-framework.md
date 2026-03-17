# 📚 RAG Framework — AI Product Builder Playbook

> **A framework for designing Retrieval-Augmented Generation systems that ground AI outputs in your own data**

---

## Table of Contents

- [Overview](#overview)
- [When to Use This Framework](#when-to-use-this-framework)
- [The RAG Architecture Model](#the-rag-architecture-model)
- [Layer 1: Data Ingestion](#layer-1-data-ingestion)
- [Layer 2: Indexing and Embedding](#layer-2-indexing-and-embedding)
- [Layer 3: Retrieval](#layer-3-retrieval)
- [Layer 4: Generation](#layer-4-generation)
- [Advanced RAG Patterns](#advanced-rag-patterns)
- [RAG Evaluation](#rag-evaluation)
- [Templates](#templates)
- [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
- [LLM Prompts](#-llm-prompts)

---

## Overview

Large language models are trained on the world's knowledge up to a cutoff date. They know nothing about your company, your documents, your customers, or anything that has happened since their training. Retrieval-Augmented Generation (RAG) bridges this gap — it retrieves relevant information from your own data sources and provides it to the model as context, enabling accurate, grounded, and up-to-date responses.

> **Core Principle:** RAG does not make a model smarter. It makes a model informed. The model's reasoning capability is unchanged — but instead of reasoning from parametric memory (which may be wrong, outdated, or absent), it reasons from retrieved evidence that you control.

RAG is the single most impactful architectural pattern available to AI product builders. It reduces hallucination, improves factual accuracy, enables auditability, and allows AI products to be built on proprietary data without fine-tuning.

---

## When to Use This Framework

| Trigger | Priority |
|---|---|
| AI needs to answer questions about your company's documents, data, or knowledge | 🔴 Critical — RAG is the standard solution |
| AI is hallucinating facts that exist in your own data | 🔴 Critical — RAG grounds the model |
| AI needs access to information more recent than its training cutoff | 🔴 Critical |
| Users need to see the source of an AI response (auditability) | 🔴 Critical — RAG enables citation |
| AI needs to reason over a large corpus that won't fit in the context window | 🟠 High |
| Building a knowledge base, internal search, or documentation assistant | 🟠 High |
| Evaluating whether fine-tuning vs RAG is the right approach | 🟠 High — RAG first, always |

---

## The RAG Architecture Model

RAG has four layers, each of which must be designed carefully. Failures in retrieval cannot be fixed by the generation layer — garbage in, garbage out.

```
DATA INGESTION
  ↓ load, clean, and chunk source documents
INDEXING AND EMBEDDING
  ↓ convert chunks into vector representations for search
RETRIEVAL
  ↓ find the most relevant chunks for a given query
GENERATION
  ↓ generate a response grounded in retrieved context
```

| Layer | Core Function | Key Decisions |
|---|---|---|
| **Ingestion** | Get the right data into the system | Source selection, cleaning, chunking strategy |
| **Indexing** | Make data searchable by meaning | Embedding model, vector store, metadata schema |
| **Retrieval** | Find the most relevant content | Search strategy, ranking, re-ranking |
| **Generation** | Produce grounded, accurate output | Prompt design, citation handling, fallback |

> **Rule of thumb:** 80% of RAG quality problems are retrieval problems, not generation problems. Before blaming the model, audit the retrieval layer.

---

## Layer 1: Data Ingestion

### 1.1 Source Selection

Not all data belongs in a RAG system. Include data that is:

| Include | Exclude |
|---|---|
| Authoritative and trusted | Outdated or superseded versions |
| Relevant to user queries | Tangentially related filler content |
| Appropriately licensed or owned | Proprietary data without clearance |
| Maintained and updated | Stale data with no refresh cadence |
| Structured enough to chunk | Deeply nested or code-heavy content that loses context when split |

### 1.2 Document Cleaning Pipeline

Raw documents are rarely ready to index. Clean before ingesting:

```
DOCUMENT CLEANING PIPELINE

Step 1 — Format normalisation
Convert all sources to plain text or structured markdown.
Remove: headers/footers, page numbers, navigation elements, boilerplate.

Step 2 — Deduplication
Identify and remove duplicate documents or near-duplicate content.
Method: hash-based (exact) + embedding similarity (near-duplicate).

Step 3 — Quality filtering
Remove: documents below minimum length threshold.
Remove: documents with encoding errors or garbled text.
Flag: documents with contradictory information for human review.

Step 4 — Metadata extraction
Extract and tag: document title, author, date, source URL, document type, topic tags.
This metadata enables filtered retrieval and citation generation.

Step 5 — Version management
For updated documents: determine update strategy.
  [ ] Overwrite (replace old chunks with new)
  [ ] Append (add new chunks; mark old as superseded)
  [ ] Version (keep all versions; tag with version number)
```

### 1.3 Chunking Strategy

Chunking is one of the highest-leverage decisions in RAG architecture. The wrong chunk size destroys retrieval quality.

| Chunking Strategy | Chunk Size | Best For | Risk |
|---|---|---|---|
| **Fixed-size** | 256–512 tokens | Uniform documents, speed | May cut sentences mid-thought |
| **Sentence-based** | 1–3 sentences | Short factual documents | Loses context for long arguments |
| **Paragraph-based** | 100–300 tokens | Well-structured documents | Paragraphs vary wildly in length |
| **Semantic chunking** | Variable | Documents with logical sections | Requires more processing |
| **Hierarchical** | Parent + child chunks | Long documents with structure | Higher index complexity |
| **Sliding window** | Overlap of 20–30% | Dense technical content | Higher storage cost |

```
CHUNKING DECISION GUIDE

Document type: [what are you indexing?]
Average document length: _____ words

If documents are short and atomic (FAQs, facts, definitions):
  → Small chunks (128–256 tokens), sentence or paragraph-based

If documents are long and structured (reports, manuals, policies):
  → Hierarchical chunking (index document summary + paragraph chunks)
  → Sliding window with overlap to preserve context at boundaries

If documents are dense and technical:
  → Larger chunks (512–1024 tokens) + sliding window overlap

Recommended chunk size for my data: _____ tokens
Overlap: _____% of chunk size
```

---

## Layer 2: Indexing and Embedding

### 2.1 Embedding Model Selection

| Embedding Model Class | Examples | Dimensions | Best For |
|---|---|---|---|
| **General purpose** | OpenAI text-embedding-3-small | 1536 | Most use cases — good starting point |
| **High performance** | OpenAI text-embedding-3-large | 3072 | When retrieval quality is critical |
| **Multilingual** | multilingual-e5-large | 1024 | Multi-language corpora |
| **Domain-specific** | Fine-tuned models | Variable | When domain language is highly specialised |
| **Open source** | BAAI/bge-large-en | 1024 | Cost-sensitive, privacy-required |

### 2.2 Vector Store Selection

| Vector Store | Deployment | Best For | Scale |
|---|---|---|---|
| **Pinecone** | Managed cloud | Production — minimal ops overhead | Very large |
| **Weaviate** | Self-hosted or cloud | Hybrid search (vector + keyword) | Large |
| **Chroma** | Local or self-hosted | Development and small production | Small-medium |
| **pgvector** | PostgreSQL extension | Existing PostgreSQL infrastructure | Medium |
| **Qdrant** | Self-hosted or cloud | High performance, low latency | Large |
| **Azure AI Search** | Managed cloud | Azure-native stacks | Large |

### 2.3 Metadata Schema Design

Metadata enables filtered retrieval — retrieving only chunks from relevant documents, date ranges, or categories:

```
CHUNK METADATA SCHEMA

{
  chunk_id: "uuid",
  document_id: "uuid",
  document_title: "string",
  document_url: "string",
  document_type: "policy | report | FAQ | manual | email | other",
  author: "string",
  created_date: "ISO-8601",
  last_updated: "ISO-8601",
  topic_tags: ["tag1", "tag2"],
  language: "en",
  chunk_index: 0,  // position in source document
  total_chunks: 12,  // total chunks from this document
  chunk_text: "raw text of this chunk",
  token_count: 256,
  embedding_model: "text-embedding-3-small",
  embedding_version: "1"
}
```

---

## Layer 3: Retrieval

### 3.1 Retrieval Strategy Selection

| Strategy | Description | When to Use |
|---|---|---|
| **Dense retrieval** | Embedding similarity search | Default — most use cases |
| **Sparse retrieval** | BM25 keyword search | When exact keyword match matters |
| **Hybrid retrieval** | Dense + sparse, merged | Best overall quality — recommended |
| **Multi-query retrieval** | Generate multiple queries; retrieve for each | Complex or ambiguous questions |
| **HyDE (Hypothetical Document Embeddings)** | Generate hypothetical answer; retrieve similar | When query and document language differ significantly |
| **Recursive retrieval** | Retrieve summaries, then retrieve from relevant documents | Hierarchical document structures |

### 3.2 Retrieval Parameters

```
RETRIEVAL CONFIGURATION

Embedding model: _______________________________________________
Top-K results: ___  (recommended starting point: 5–10)
Similarity threshold: ___  (filter out chunks below this score; start at 0.7)
Metadata filters: _______________________________________________

Hybrid search weights (if using hybrid):
  Dense weight: ___  (typically 0.7)
  Sparse weight: ___  (typically 0.3)

Re-ranking: Yes / No
  If yes, re-ranker model: _______________________________________________
  Re-ranking top-K: ___  (re-rank top 20, return top 5)

Context window budget for retrieved chunks: _____ tokens
```

### 3.3 Query Optimisation

The query sent to the retrieval system is rarely the user's raw input. Optimise it:

| Optimisation | Description | Impact |
|---|---|---|
| **Query rewriting** | LLM rewrites the query for better retrieval | +15–25% retrieval accuracy |
| **Query expansion** | Add synonyms and related terms | +10–15% recall |
| **Sub-question decomposition** | Break complex questions into sub-queries | +20–30% for multi-hop questions |
| **Conversation history injection** | Include prior context in the query | +10–20% for follow-up questions |
| **HyDE** | Generate hypothetical answer to embed | +10–20% when query and corpus language differ |

```
QUERY OPTIMISATION PROMPT

Original user query: [raw user input]

Step 1 — Conversation-aware rewrite:
"Given the conversation history below and the user's current query,
rewrite the query as a standalone, self-contained search query
that captures the full intent including implied context from the conversation.
Return only the rewritten query, nothing else."

Step 2 — Sub-question decomposition (for complex queries):
"Break this query into 2–4 specific sub-questions that, when answered together,
fully address the original query. Return as a numbered list."

Step 3 — Retrieve for each sub-question in parallel
Step 4 — Merge retrieved chunks (deduplicate by document_id + chunk_index)
Step 5 — Re-rank merged results against original query
```

### 3.4 Re-ranking

Re-ranking takes the top-K retrieved chunks and re-orders them by relevance to the query. It significantly improves precision:

```
RE-RANKING PIPELINE

Input: Top 20 chunks from retrieval + original query
Method:
  Option A — Cross-encoder re-ranker (highest quality): cohere-rerank, bge-reranker
  Option B — LLM-based re-ranking (flexible): prompt LLM to score each chunk's relevance
  Option C — Reciprocal Rank Fusion (RRF): combine multiple retrieval signals

Output: Top 5 re-ranked chunks for generation context

Re-ranking adds 100–500ms latency but can improve answer quality by 20–40%.
Use when: answer quality is critical and latency budget allows.
```

---

## Layer 4: Generation

### 4.1 RAG Generation Prompt Design

```
RAG GENERATION PROMPT STRUCTURE

System instruction:
"You are [role]. Answer questions based solely on the provided context.
If the context does not contain sufficient information to answer the question,
say so explicitly — do not answer from general knowledge.
Always cite the source document for any claim you make."

Context injection:
"Context:
[CHUNK 1]
Source: [document_title] | [document_url] | Updated: [last_updated]

[CHUNK 2]
Source: [document_title] | [document_url] | Updated: [last_updated]

[Continue for all retrieved chunks]"

User query:
"Question: [user's question]"

Answer format instruction:
"Provide a direct answer to the question.
For each claim, cite the source using [Source: document_title].
If different sources contradict each other, note the contradiction.
If the context is insufficient, respond with:
'The available documents do not contain sufficient information to answer this question.
You may want to check [suggested alternative source].'"
```

### 4.2 Citation Design

Citations are a product feature, not just a technical nicety. Design them for the user experience:

| Citation Format | Best For | Implementation |
|---|---|---|
| **Inline footnote** `[1]` | Dense technical content | Tag claims with numbered references |
| **Source card** | Document-heavy products | Rich source card with title, date, URL |
| **Highlighted source** | Search-style products | Show source chunk alongside answer |
| **Confidence indicator** | High-stakes domains | Show retrieval confidence score |

### 4.3 Fallback Handling

```
FALLBACK DECISION TREE

Step 1 — Check retrieval result quality
  If top retrieved chunk similarity < threshold:
    → "I couldn't find relevant information in the available documents for this question."
    → Offer: "Would you like to rephrase your question or search more broadly?"

Step 2 — Check answer grounding
  After generation, check: does the answer contain claims not supported by retrieved context?
  If yes:
    → Flag as potentially hallucinated
    → Add caveat: "Note: parts of this answer may go beyond the provided documents. Please verify."

Step 3 — Complete knowledge gap
  If context genuinely insufficient:
    → "The documents available don't cover this topic."
    → Offer: suggest where the user might find this information
    → Log: knowledge gap for content team to address
```

---

## Advanced RAG Patterns

### 5.1 Corrective RAG (CRAG)

CRAG adds a self-evaluation step: after retrieval, the system evaluates whether the retrieved chunks are sufficient to answer the question. If not, it searches for better sources before generating.

```
CRAG PIPELINE

Retrieve → Evaluate retrieval quality → [Sufficient] → Generate
                                      → [Insufficient] → Expand search → Re-retrieve → Generate
                                      → [Contradictory] → Flag contradiction → Generate with caveat
```

### 5.2 Self-RAG

Self-RAG trains the model to decide when retrieval is needed and to critique its own outputs:

```
SELF-RAG DECISION POINTS

Before retrieval: "Does this query require retrieval? Or can I answer from knowledge?"
After retrieval: "Are these retrieved chunks relevant to the query?"
After generation: "Is my answer fully supported by the retrieved context?"
After generation: "Does my answer directly address the user's question?"
```

### 5.3 Agentic RAG

The retrieval system itself becomes an agent that can query multiple sources, follow links, and iteratively search:

```
AGENTIC RAG PATTERN

Query received
  ↓
Agent plans search strategy
  ↓
Search source 1 → Evaluate relevance → [Relevant] → Add to context
                                     → [Insufficient] → Follow links / expand query
  ↓
Search source 2 (if needed)
  ↓
Agent evaluates: "Do I have enough context to answer?"
  → Yes → Generate
  → No → Search more (up to max_iterations)
```

---

## RAG Evaluation

### 6.1 RAG Evaluation Metrics

| Metric | What It Measures | Target |
|---|---|---|
| **Context relevance** | Are retrieved chunks relevant to the query? | > 80% of retrieved chunks are relevant |
| **Answer faithfulness** | Is the answer grounded in the retrieved context? | > 95% of claims are supported by context |
| **Answer relevance** | Does the answer actually address the query? | > 90% of answers are on-topic |
| **Context recall** | Were all relevant chunks retrieved? | > 80% of relevant information was found |
| **Groundedness** | How much of the answer can be traced to a source? | > 95% for factual domains |

### 6.2 RAG Evaluation Framework

```
RAG EVALUATION PIPELINE

Dataset: 50–100 representative queries with known correct answers

For each query:
1. Run retrieval → score context relevance (human or LLM judge)
2. Run generation → score answer faithfulness (LLM judge: "Is this claim supported by the context?")
3. Score answer relevance (LLM judge: "Does this answer address the question?")
4. Compare to ground truth → accuracy score

Aggregate across dataset:
Context relevance: ____%
Answer faithfulness: ____%
Answer relevance: ____%
Groundedness: ____%

Action if metric below target:
Context relevance < 80% → Review chunking strategy and retrieval parameters
Answer faithfulness < 95% → Tighten generation prompt; add "only use context" instruction
Answer relevance < 90% → Improve query rewriting step
```

---

## Templates

### Template A: RAG System Design Document

```
# RAG System Design — [System Name]
Date: ___  |  Author: ___  |  Version: ___

## Data Sources
| Source | Type | Volume | Update Frequency | Sensitivity |
|--------|------|--------|-----------------|-------------|
|        |      |        |                 |             |

## Ingestion Design
Cleaning pipeline: _______________________________________________
Chunking strategy: ___  tokens  |  Overlap: ___%
Metadata fields: _______________________________________________

## Indexing Design
Embedding model: _______________________________________________
Vector store: _______________________________________________
Index type: _______________________________________________

## Retrieval Design
Strategy: Dense / Sparse / Hybrid
Top-K: ___
Similarity threshold: ___
Query optimisation: _______________________________________________
Re-ranking: Yes / No — Model: _______________________________________________

## Generation Design
Citation format: _______________________________________________
Fallback handling: _______________________________________________
Grounding instruction: _______________________________________________

## Evaluation Plan
Evaluation dataset size: ___ queries
Target metrics: Context relevance > ___% | Faithfulness > ___% | Relevance > ___%
Evaluation cadence: _______________________________________________

## Cost Model
Ingestion cost (one-time): $___
Embedding cost per document: $___
Retrieval cost per query: $___
Generation cost per query: $___
Estimated monthly cost at ___ queries/day: $___
```

---

## Anti-Patterns to Avoid

| ❌ Anti-Pattern | ✅ Better Approach |
|---|---|
| Indexing raw unclean documents | Clean and normalise all documents before indexing |
| One chunk size for all document types | Design chunking strategy per document type |
| Top-K = 1 (only retrieve one chunk) | Retrieve 5–10; re-rank to select the best 3–5 |
| No similarity threshold | Filter out low-relevance chunks — they hurt generation quality |
| No query rewriting | Raw user queries are rarely optimal retrieval queries |
| Allowing model to answer from parametric knowledge when RAG fails | Implement explicit fallback — "I don't know" is better than hallucination |
| No citation in generation | Always show the source — auditability is a product feature |
| Never evaluating retrieval quality | Measure context relevance monthly — retrieval quality decays as documents change |

---

## Cadence

| Activity | Frequency | Trigger |
|---|---|---|
| Retrieval quality evaluation | Monthly | Run against evaluation dataset |
| Knowledge gap audit | Monthly | Review unanswered or poorly answered queries |
| Document freshness audit | Monthly | Are indexed documents still current? |
| Embedding model review | Quarterly | Better models become available regularly |
| Index rebuild | On major corpus change | New document types or significant content update |
| Full RAG architecture review | Annually | Or when quality metrics trend downward |

---

*Part of the [AI Product Builder Playbook](../README.md)*

---

## 🤖 LLM Prompts

Use these prompts to apply this framework directly inside ChatGPT or Claude. Copy the prompt, paste it into the chat, and fill in the bracketed fields before sending.

---

### Prompt 1 — Design a Complete RAG Architecture

> **Best for:** Designing a RAG system from scratch for a new AI product or feature.

```
You are an AI systems architect helping me design a complete RAG system.

Design the system across all four layers:

1. Data ingestion — cleaning pipeline, chunking strategy, metadata schema
2. Indexing — embedding model selection (with justification), vector store recommendation, index configuration
3. Retrieval — strategy (dense / sparse / hybrid), parameters (top-K, threshold), query optimisation, re-ranking
4. Generation — RAG prompt structure, citation format, fallback handling

For each layer, give me:
- The specific technical recommendation (not "it depends" — give me a starting point)
- The rationale for the recommendation given my use case
- The top risk at this layer and how to mitigate it

After all four layers:
- Draw the complete system as a text-based architecture diagram
- Model the cost: ingestion, embedding, retrieval, and generation per 1,000 queries
- Identify the top 3 failure modes and specific mitigations

My use case: [describe what the RAG system needs to do]
Data sources: [describe what documents / data will be indexed]
Query volume: [estimated queries per day]
Latency requirement: [maximum acceptable response time]
Budget: $[monthly maximum]
```

---

### Prompt 2 — Design a Chunking Strategy

> **Best for:** Deciding how to split documents into chunks for indexing — one of the highest-leverage RAG decisions.

```
You are a RAG specialist helping me design the optimal chunking strategy for my document corpus.

For each document type I describe, recommend:
1. Chunking method: Fixed-size / Sentence / Paragraph / Semantic / Hierarchical / Sliding window
2. Chunk size in tokens
3. Overlap size (if applicable)
4. How to handle special elements: tables, code blocks, lists, headers

After recommending for each type:
- Write the chunking logic pseudocode or Python outline
- Design the metadata schema for each chunk
- Identify where chunking will struggle and how to handle those edge cases

Then design the quality test for chunking:
- How do I verify that my chunks are retaining the right context?
- What are the 5 most important queries to test retrieval with?
- What retrieval quality score would tell me the chunking is working?

My document types:
1. [Document type — describe format, typical length, structure]
2. [Document type — describe format, typical length, structure]
3. [Document type — describe format, typical length, structure]

Retrieval use case: [what questions will users ask?]
```

---

### Prompt 3 — Improve Retrieval Quality

> **Best for:** When retrieval is working but quality is below target — answers are missing relevant information or retrieving irrelevant chunks.

```
You are a RAG quality engineer helping me improve retrieval quality in my RAG system.

I will describe my current setup and the problems I am seeing. Diagnose the root cause and recommend specific fixes.

Diagnose across these areas:

1. Chunking quality — are chunks too large/small? Losing context at boundaries?
2. Embedding model fit — is the model trained on language similar to my corpus?
3. Query-document language gap — do user queries use different terminology than the documents?
4. Retrieval parameters — is top-K too low? Similarity threshold too aggressive?
5. Missing metadata filters — is irrelevant content being retrieved because filtering isn't applied?
6. Query optimisation — is the raw user query a poor retrieval query?

For each root cause:
- Rate the likelihood this is the problem: High / Medium / Low
- Write the specific fix
- Estimate the improvement in retrieval quality
- Write a test to confirm the fix works

Current setup:
Chunking: [strategy and size]
Embedding model: [name]
Vector store: [name]
Top-K: ___  |  Similarity threshold: ___
Query optimisation: Yes / No

Problems observed:
[describe what's going wrong — missing information, irrelevant results, etc.]
```

---

### Prompt 4 — Design the RAG Generation Prompt

> **Best for:** Writing the prompt that takes retrieved chunks and generates a grounded, cited, useful response.

```
You are a prompt engineer specialising in RAG systems. Help me write the optimal generation prompt for my RAG system.

Write a complete generation prompt that:
1. Instructs the model to answer only from the provided context
2. Specifies exactly how to handle knowledge gaps (not enough information in context)
3. Specifies exactly how to handle contradictions between retrieved chunks
4. Specifies the citation format for all claims
5. Specifies the output format and length

Then write:
- The context injection format: how retrieved chunks are presented to the model
- The fallback response template: what the model returns when context is insufficient
- The contradiction handling template: what the model returns when sources disagree

Test the prompt design by showing me how it handles:
- A query with a clear, well-sourced answer in the context
- A query where only partial information is available
- A query where two retrieved chunks contradict each other
- A query that is completely outside the indexed knowledge base

My use case: [describe what the RAG system does]
Domain: [what topic area]
User segment: [who the users are]
Citation preference: [inline footnote / source card / highlighted source]
Answer length preference: [concise / detailed / variable]
```

---

### Prompt 5 — Build a RAG Evaluation Framework

> **Best for:** Systematically measuring and improving RAG quality with a repeatable evaluation process.

```
You are a RAG evaluation specialist helping me build a systematic evaluation framework for my RAG system.

Design the complete evaluation framework:

1. Evaluation dataset construction
   - How many queries do I need for a statistically meaningful evaluation?
   - How should I select queries? (representative sample / edge cases / adversarial)
   - What ground truth data do I need for each query?
   - Write 10 example evaluation queries for my use case

2. Metric definition
   For each of the four key metrics, write the exact evaluation method:
   - Context relevance: how is "relevant" defined and scored?
   - Answer faithfulness: how is "grounded in context" measured?
   - Answer relevance: how is "addresses the question" measured?
   - Groundedness: how is source traceability measured?

3. Evaluation pipeline
   - Write the LLM-as-judge prompt for each metric
   - Design the scoring rubric (1–5 scale with explicit criteria at each level)
   - How are scores aggregated across the evaluation dataset?

4. Action thresholds
   - At what score does each metric trigger an investigation?
   - What action is taken for each metric when below threshold?

5. Continuous evaluation
   - How do I run this evaluation monthly without it becoming a manual burden?
   - How do I detect retrieval quality decay as the document corpus changes?

My RAG system: [describe what it does]
Domain: [topic area]
My current quality concerns: [what problems am I seeing?]
Evaluation budget: [time and cost available for evaluation]
```
