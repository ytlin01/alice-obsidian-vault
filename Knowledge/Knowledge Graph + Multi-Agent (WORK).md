# Knowledge Graph + Multi-Agent

## Why This Matters

This topic sits at the intersection of:

- `knowledge representation`
- `information extraction`
- `retrieval and reasoning`
- `LLM agent orchestration`
- `system design for AI products`

It is useful for job search prep because it gives me a concrete way to talk about how unstructured or semi-structured technical data can be transformed into a machine-usable graph, then queried or acted on by one or more agents.

---

## Core Problem Framing

A knowledge-graph + multi-agent system usually tries to solve one or both of these problems:

1. Convert messy source material into structured entities, relations, and evidence.
2. Use that structure to support downstream retrieval, reasoning, planning, or workflow automation.

A good interview framing:

- Raw documents, tables, or engineering artifacts are hard to search reliably with keyword matching alone.
- A knowledge graph adds explicit structure: `entity -> relation -> entity`.
- Multi-agent orchestration helps split complex tasks into smaller roles such as extraction, validation, retrieval, planning, and synthesis.

---

## Mental Model

Think of the stack in five layers:

1. `Ingestion`
2. `Normalization / extraction`
3. `Graph construction`
4. `Retrieval + reasoning`
5. `Agent orchestration`

Simple flow:

`source data -> parser / extractor -> entities + relations + evidence -> graph store -> retrieval -> agent workflow -> answer / action`

---

## Knowledge Graph Basics

### What a Knowledge Graph Stores

A knowledge graph usually contains:

- `entities`
  - examples: part, assembly, document, requirement, supplier, defect, drawing, report
- `relationships`
  - examples: `part_of`, `connected_to`, `references`, `matches`, `requires`, `owned_by`
- `attributes`
  - examples: part number, quantity, revision, confidence score, timestamp
- `evidence / provenance`
  - examples: source file, row id, page, parser version, extraction rule

### Why Provenance Matters

In production systems, provenance is critical because:

- graphs can contain noisy or uncertain facts
- multiple sources can disagree
- downstream agents need traceable evidence
- human reviewers need to audit how a relationship was created

Interview language:

- "I would store not just the edge, but also confidence, source, and extraction method so the graph remains explainable and reviewable."

---

## Good Graph Schema Thinking

When designing a graph schema, I should be able to answer:

- What are the main node types?
- What relationships are stable enough to model explicitly?
- Which properties belong on nodes versus edges?
- What is the entity resolution strategy?
- How do we version graph facts over time?

Common schema decisions:

- Use nodes for durable business objects.
- Use edges for relationships that drive traversal or reasoning.
- Use properties for scalar metadata that does not need separate traversal.
- Keep `source_id`, `confidence`, and `last_updated` close to extracted facts.

---

## Extraction Pipeline

### Typical Pipeline Stages

1. Parse source data.
2. Normalize text, identifiers, units, and encodings.
3. Extract candidate entities and relations.
4. Resolve duplicates or aliases.
5. Assign confidence scores.
6. Write graph records plus provenance.
7. Run validation and human review on ambiguous cases.

### Engineering Lessons That Transfer Well

A strong extraction pipeline needs more than just model output:

- encoding handling
- normalization rules
- fuzzy matching
- confidence thresholds
- ambiguity buckets
- review workflows

This is a strong interview point because it shows that production IE systems are not just "call an LLM and save JSON."

---

## Entity Resolution

Entity resolution is often the hardest part.

Typical issues:

- formatting variation
- aliases or abbreviations
- revision suffixes
- language / encoding differences
- partial overlaps between systems
- one-to-many or many-to-one mapping ambiguity

Useful techniques:

- exact normalized matching
- rule-based canonicalization
- fuzzy string similarity
- attribute-aware matching
- graph-context matching
- human review for borderline cases

Interview framing:

- "A high similarity score is not automatically a true match. I would separate exact matches, fuzzy candidates, quantity mismatches, and unresolved cases instead of flattening them into one metric."

---

## Retrieval: Why Graphs Help

Compared with plain vector search, graphs help when the question depends on:

- explicit relationships
- multi-hop traversal
- constraints
- lineage / provenance
- structured filtering

Example graph-friendly questions:

- Which components belong to this assembly and also appear in a discrepancy report?
- What documents reference a part that has unresolved quantity mismatches?
- Which entities are two hops away from a given requirement?

A practical hybrid pattern:

- use vector search for semantic recall
- use graph traversal for precise structure
- combine both before final synthesis

---

## Multi-Agent Layer

### Why Use Multiple Agents

Multi-agent design makes sense when a task can be decomposed into distinct roles with different prompts, tools, or constraints.

Example roles:

- `Extractor agent`
  - pulls entities / relations from source material
- `Normalizer agent`
  - standardizes names, units, and identifiers
- `Validator agent`
  - checks confidence, schema conformance, and conflicts
- `Retriever agent`
  - gathers relevant graph subgraphs and source evidence
- `Planner agent`
  - decides what subtasks are needed
- `Synthesizer agent`
  - writes the final answer or recommendation

### Benefits

- clearer separation of responsibility
- easier debugging
- more controllable prompting
- better tool specialization
- less context overload per agent

### Risks

- coordination overhead
- error propagation between agents
- latency and cost growth
- duplicate work
- inconsistent intermediate formats

Strong interview line:

- "I would use multiple agents only when decomposition improves reliability or tool use. If a single tool-using workflow is enough, multi-agent can be unnecessary complexity."

---

## Architecture Pattern

### High-Level Design

1. Sources arrive from files, docs, APIs, or engineering exports.
2. A parsing layer converts them into structured intermediate records.
3. Extraction logic proposes entities, attributes, and edges.
4. Resolution logic merges duplicates and marks uncertainty.
5. The graph store persists nodes, edges, and provenance.
6. Retrieval services expose graph queries, semantic search, and filters.
7. Agents use those retrieval tools to answer questions or run workflows.

### Important Supporting Components

- `schema registry`
- `feature / metadata store`
- `review queue`
- `observability and tracing`
- `versioned prompts or extraction rules`
- `evaluation dataset`

---

## Data Quality and Evaluation

For interview prep, it helps to think in metrics.

### Extraction Metrics

- entity precision / recall
- relation precision / recall
- schema-valid rate
- unresolved ambiguity rate
- reviewer-overturn rate

### Retrieval Metrics

- top-k recall
- evidence coverage
- subgraph relevance
- latency

### Agent Metrics

- task success rate
- groundedness to retrieved evidence
- unnecessary tool-call rate
- handoff failure rate
- end-to-end latency and cost

### Human-in-the-Loop Metrics

- review volume
- acceptance rate of auto-generated facts
- time-to-resolution for ambiguous cases

---

## Common Failure Modes

### Graph Construction Failures

- duplicate entities due to poor canonicalization
- over-merged entities that should remain separate
- missing provenance
- relation type explosion
- stale graph facts after source updates

### Agent Failures

- hallucinated edges or unsupported conclusions
- poor subtask decomposition
- circular delegation
- over-retrieval causing noisy context
- under-retrieval causing incomplete answers

### System Design Failures

- no clear source of truth
- no versioning strategy
- expensive graph updates
- weak observability
- no evaluation set for regression testing

---

## Design Tradeoffs

### Rule-Based vs LLM-Based Extraction

Rule-based:

- high precision for stable patterns
- brittle to variation
- easier to explain

LLM-based:

- better flexibility on messy text
- more expensive
- needs stronger validation

Best practical answer in interviews:

- "I would use a hybrid pipeline: deterministic parsing and normalization where structure exists, then model-based extraction on ambiguous or unstructured portions."

### Graph DB vs Relational DB

Graph DB is stronger when:

- traversal is central
- relation depth matters
- queries are highly connected

Relational storage is still useful for:

- tabular facts
- audits
- batch analytics
- downstream reporting

A hybrid architecture is often the most realistic.

### Single Agent vs Multi-Agent

Single agent:

- simpler
- cheaper
- easier to evaluate

Multi-agent:

- more modular
- better for tool specialization
- better for long workflows if interfaces are clean

---

## How I'd Explain This in an Interview

### Short Version

"A knowledge graph gives structured, explainable relationships over entities and evidence, while a multi-agent layer uses that structure to retrieve, validate, and act on information in a modular way."

### More Technical Version

"I think about it as a pipeline: ingest and normalize source data, extract entities and relationships with provenance, resolve ambiguity, persist the graph, then expose retrieval tools that agents can use for multi-step reasoning or workflow automation. The hard parts are usually entity resolution, confidence handling, provenance, and evaluation."

---

## Resume / Story Framing

Good themes to emphasize:

- converted messy technical data into structured graph-friendly records
- improved reliability through normalization and validation
- separated exact matches, fuzzy candidates, and unresolved conflicts
- designed for provenance and human review
- thought about retrieval, reasoning, and orchestration as a system rather than isolated scripts

Possible bullet style:

- Designed graph-oriented extraction and normalization workflows for technical source data, with provenance, confidence scoring, and ambiguity handling for downstream retrieval and agent workflows.
- Structured entity and relationship pipelines to distinguish exact matches, fuzzy candidates, and true discrepancies, improving explainability and reviewability.
- Framed multi-step AI workflows as modular agent responsibilities across extraction, validation, retrieval, and synthesis.

---

## Interview Questions To Practice

- When would you use a knowledge graph instead of vector search alone?
- How would you design entity resolution for noisy technical identifiers?
- What would you store on edges versus nodes?
- How would you evaluate relation extraction quality?
- When is multi-agent architecture worth the added complexity?
- How would you prevent hallucinated graph updates from LLM agents?
- How would you keep provenance and auditability in the system?
- How would you design human review for low-confidence extractions?

---

## Talking Points I Want To Remember

- Graphs are strongest when relationships and multi-hop reasoning matter.
- Provenance is not optional in production knowledge systems.
- Entity resolution is often harder than initial extraction.
- Hybrid systems usually win: deterministic parsing + model-based extraction + human review.
- Multi-agent is a design choice, not a default.
- Evaluation should cover extraction quality, retrieval quality, and end-to-end agent behavior.

---

## Related Concepts To Review

- [[System Design]]
- [[ML Concepts]]
- [[SQL Patterns]]
- [[LeetCode Patterns]]
