# RFC-0001: NEMO Foundation

**Category:** Standards Track  
**Status:** Draft  
**Version:** 0.1  
**Date:** 2026-07-21  
**Editors:** Txema Zapater, OpenAI  
**Repository:** `txemazapater/nemo`

## Abstract

This document defines the initial foundation of NEMO: an open conceptual model, specification, and interoperability protocol for preserving the evolution of collective knowledge within a team.

NEMO is not limited to software development. It applies to teams that design, investigate, analyse, decide, experiment, implement, operate, or maintain complex work over time.

The central proposition is:

> NEMO preserves the evolution of collective knowledge.

This RFC establishes the problem statement, scope, terminology, architectural layers, core semantic objects, minimum conformance requirements, interoperability principles, governance direction, and the role of NEMO-Ready implementations.

## 1. Status of this document

This is the first NEMO standards-track RFC.

It is intentionally incomplete. Its purpose is to establish a coherent foundation from which later RFCs can define canonical schemas, transport bindings, synchronization behavior, security profiles, domain profiles, and conformance tests.

Until this RFC is promoted beyond Draft status:

- normative language expresses design intent;
- object names and field names may evolve;
- incompatible changes remain possible;
- implementations must declare the exact draft version they support.

## 2. Normative language

The keywords **MUST**, **MUST NOT**, **REQUIRED**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** are to be interpreted as requirement levels.

## 3. Problem statement

Teams continuously generate knowledge through:

- conversations;
- meetings;
- documents;
- source code;
- experiments;
- prototypes;
- measurements;
- incidents;
- tickets;
- diagrams;
- reports;
- external references;
- human experience;
- artificial agents.

Most tools preserve outputs. Few preserve the path by which those outputs became accepted, rejected, revised, or acted upon.

As a result, teams routinely lose:

- the reasoning behind decisions;
- the distinction between observation and interpretation;
- assumptions that were once implicit;
- alternatives that were considered and discarded;
- evidence that supported or contradicted a claim;
- the origin and authorship of an idea;
- the relation between conversations and resulting artifacts;
- continuity when people, tools, repositories, or project phases change.

This loss is not merely documentary. It degrades the team's ability to understand itself, revisit prior decisions, onboard new participants, reuse learning, detect repeated mistakes, and continue work coherently.

## 4. Scope

NEMO defines a common way to represent and exchange the evolution of collective knowledge.

Its scope includes four inseparable dimensions:

1. **Conceptual model**  
   The meaning of knowledge objects, actors, events, sources, artifacts, and relationships.

2. **Specification**  
   The minimum semantics that a conforming implementation must preserve.

3. **Protocol**  
   The operations and exchange principles through which NEMO-compatible systems interoperate.

4. **Conformance model**  
   The criteria by which an implementation may declare itself `NEMO-Ready`.

## 5. Non-goals

NEMO is not intended to be:

- a note-taking application;
- a document management system;
- a chat product;
- a source-control replacement;
- an issue tracker replacement;
- an AI model or agent framework;
- a universal ontology for all human knowledge;
- a requirement to record every action forever;
- a centralized service controlled by one vendor;
- a single mandatory storage engine.

NEMO connects and gives continuity to existing systems. It does not require replacing them.

## 6. Foundational principles

### 6.1 Continuity over accumulation

The purpose of NEMO is not to collect more information. It is to preserve an understandable thread through time.

### 6.2 Provenance by default

Relevant knowledge MUST retain sufficient information to identify where it came from, when it appeared, and which actor contributed or transformed it.

### 6.3 Evidence and belief are distinct

An observation, hypothesis, assumption, interpretation, conclusion, and decision MUST NOT be collapsed into an undifferentiated note.

### 6.4 Conversations are sources, not final truth

Conversations may create candidate knowledge, but their relevant content requires explicit semantic status and traceability before it becomes dependable operational knowledge.

### 6.5 Evolution must remain visible

Correction MUST NOT erase history. Rejection, refinement, invalidation, and supersession SHOULD be represented as new events and typed relationships.

### 6.6 Knowledge must remain portable

A team SHOULD NOT lose its intellectual history because it changes tools, platforms, vendors, repositories, or AI providers.

### 6.7 Human and artificial contributors coexist

NEMO MUST support people, teams, organizations, software systems, AI models, and autonomous agents as actors without erasing authorship, responsibility, or authority boundaries.

### 6.8 Semantics survive implementation differences

A Markdown repository, relational database, graph database, desktop application, cloud service, or embedded tool may all be NEMO-Ready if they preserve the required meaning.

## 7. Architectural layers

NEMO separates the following layers:

### 7.1 Semantic layer

Defines what NEMO objects mean and how they relate.

### 7.2 Representation layer

Defines portable serializations of those objects.

JSON is the initial reference representation, but it is not the only permitted form.

### 7.3 Protocol layer

Defines operations for discovery, retrieval, creation, relation, event append, query, synchronization, import, export, and validation.

### 7.4 Binding layer

Defines how the protocol maps onto a transport such as HTTP, local files, message queues, peer-to-peer exchange, or embedded IPC.

### 7.5 Implementation layer

Defines the product, service, repository convention, adapter, or agent that implements one or more NEMO capabilities.

## 8. Core terminology

### 8.1 Workspace

A bounded context in which actors pursue an objective.

A workspace may represent a project, product, investigation, department, incident, machine design, client engagement, research line, or temporary initiative.

### 8.2 Actor

An entity capable of contributing, transforming, validating, authorizing, or consuming knowledge.

Actor types may include:

- person;
- team;
- organization;
- AI model;
- autonomous agent;
- software service;
- external system.

Identity does not imply authority. Authority and validation are separate concerns.

### 8.3 Source

The origin from which information is obtained.

Examples include conversations, documents, experiments, measurements, tickets, code repositories, publications, meetings, sensors, and human recollection.

### 8.4 Knowledge Event

The smallest meaningful event that changes the state of collective knowledge.

Examples include:

- recording an observation;
- proposing a hypothesis;
- attaching evidence;
- contradicting a claim;
- adopting a decision;
- invalidating an assumption;
- creating an artifact;
- superseding a conclusion.

Knowledge events SHOULD be immutable.

### 8.5 Claim

A statement that may be evaluated, supported, contradicted, accepted, rejected, disputed, refined, or superseded.

Initial semantic classes include:

- `OBSERVATION`;
- `HYPOTHESIS`;
- `ASSUMPTION`;
- `INTERPRETATION`;
- `CONCLUSION`;
- `DECISION`;
- `RISK`;
- `QUESTION`;
- `TASK`.

### 8.6 Evidence

A traceable object used to support, weaken, or contradict a claim.

Evidence may be empirical, documentary, computational, testimonial, or derived.

Evidence does not automatically make a claim true. It changes the support available for evaluating that claim.

### 8.7 Decision

A claim adopted as a basis for action by an authorized actor or group.

A decision SHOULD identify:

- the question or problem addressed;
- alternatives considered;
- supporting and contradicting evidence;
- assumptions;
- responsible decision makers;
- effective date;
- expected consequences;
- review conditions.

### 8.8 Artifact

A durable output produced or used by the team.

Examples include documents, source files, designs, diagrams, prototypes, datasets, configurations, reports, contracts, and physical test results.

An artifact is not itself a knowledge event, but its creation, modification, validation, rejection, or replacement is.

### 8.9 Conversation

A sequence of contributions between actors.

A conversation is a source of candidate knowledge. Its significant claims, evidence, questions, decisions, risks, and actions SHOULD be extracted or linked explicitly.

### 8.10 Relationship

A typed connection between NEMO objects.

Initial relationship types include:

- `DERIVED_FROM`;
- `SUPPORTS`;
- `CONTRADICTS`;
- `REFINES`;
- `SUPERSEDES`;
- `IMPLEMENTS`;
- `VALIDATES`;
- `INVALIDATES`;
- `DEPENDS_ON`;
- `RESULTED_IN`;
- `REFERENCES`;
- `PART_OF`.

## 9. Common object requirements

A portable NEMO object MUST preserve:

- a stable identifier;
- object type;
- semantic class or status where applicable;
- creation time;
- contributing actor;
- workspace context;
- provenance;
- lifecycle state;
- representation version.

A portable object SHOULD support:

- a human-readable title;
- tags;
- confidentiality classification;
- extensions;
- relationships;
- content integrity metadata.

## 10. Lifecycle and semantic status

Semantic class and lifecycle state are distinct.

For example, a hypothesis may be:

- `DRAFT`;
- `ACTIVE`;
- `DISPUTED`;
- `VALIDATED`;
- `REJECTED`;
- `SUPERSEDED`;
- `ARCHIVED`.

Changing lifecycle state MUST NOT silently change semantic class.

## 11. Historical integrity

NEMO favors append-only historical truth.

A conforming implementation:

- MUST NOT silently rewrite provenance;
- MUST preserve supersession and invalidation history;
- SHOULD represent corrections as new events;
- SHOULD retain competing claims where disagreement exists;
- MUST NOT resolve conflicts by destructive overwrite without traceability.

Implementations MAY expose a materialized current state, but that state MUST remain explainable from its historical lineage at conformance levels that claim continuity support.

## 12. Minimal knowledge evolution chain

A valid evolution chain may be:

```text
Conversation
  -> Hypothesis
  -> Experiment
  -> Evidence
  -> Conclusion
  -> Decision
  -> Artifact
```

This sequence is illustrative, not mandatory.

Real work may branch, converge, regress, remain unresolved, contain parallel hypotheses, or include contradictory conclusions.

## 13. Canonical portable envelope

The initial reference envelope is JSON-compatible:

```json
{
  "nemo_version": "0.1",
  "id": "urn:nemo:claim:example-001",
  "type": "claim",
  "semantic_class": "HYPOTHESIS",
  "lifecycle_state": "ACTIVE",
  "title": "Example hypothesis",
  "created_at": "2026-07-21T10:00:00+02:00",
  "created_by": "urn:nemo:actor:txema",
  "workspace_id": "urn:nemo:workspace:nemo",
  "provenance": {
    "source_type": "conversation",
    "source_ref": "urn:nemo:conversation:example"
  },
  "content": {
    "text": "A team's knowledge should preserve its evolution, not only its outputs."
  },
  "relationships": []
}
```

The exact schema remains non-final in this draft.

## 14. Extension model

Extensions MUST:

- use a unique namespace;
- declare the NEMO version they extend;
- avoid redefining core fields;
- state whether they affect interoperability;
- remain ignorable unless declared required by a profile.

Example:

```json
{
  "extensions": {
    "org.example.lab": {
      "instrument_id": "scope-04"
    }
  }
}
```

## 15. Protocol capabilities

A NEMO endpoint or adapter MAY expose:

- capability discovery;
- object retrieval;
- object creation;
- relationship creation;
- event append;
- query;
- synchronization;
- validation;
- subscription;
- import;
- export.

### 15.1 Discovery

An endpoint SHOULD publish its supported NEMO version, capabilities, profiles, limitations, and conformance level.

### 15.2 Read

A system SHOULD be able to retrieve an object by stable identifier.

### 15.3 Create

Creation operations MUST preserve authorship and provenance.

### 15.4 Append event

Write operations SHOULD emit a knowledge event.

### 15.5 Relate

Systems SHOULD support explicit typed relationships between objects.

### 15.6 Query

A basic query capability SHOULD support filtering by workspace, actor, type, semantic class, lifecycle state, source, time, or relationship.

### 15.7 Import and export

Portable exchange MUST preserve mandatory semantics and MUST report unsupported fields or profiles.

### 15.8 Synchronization

Synchronization SHOULD be idempotent and MUST NOT silently discard conflicts.

## 16. Transport independence

NEMO does not mandate a single transport.

Possible bindings include:

- HTTP;
- local filesystem packages;
- Git repositories;
- message queues;
- peer-to-peer exchange;
- desktop IPC;
- embedded communication channels.

An HTTP reference binding is expected in a later RFC.

## 17. Identity, authority, and responsibility

NEMO distinguishes:

- **identity**: who or what produced a contribution;
- **authority**: who may approve, reject, validate, or decide;
- **responsibility**: who is accountable for an action or decision;
- **execution**: which actor or system performed an operation.

These concepts MUST NOT be inferred as equivalent.

## 18. Security and confidentiality

This RFC does not define a mandatory authentication technology.

However, conforming implementations MUST NOT treat portability as permission to disclose.

Implementations SHOULD support:

- access control;
- confidentiality classification;
- integrity verification;
- auditability;
- selective export;
- redaction with traceable reason;
- lawful deletion or erasure procedures.

Detailed security and privacy requirements are deferred to a later RFC.

## 19. NEMO-Ready conformance

A product, service, repository, adapter, or platform may declare itself `NEMO-Ready` only when it publishes:

- supported NEMO version;
- conformance level;
- capabilities;
- supported profiles;
- known limitations;
- conformance evidence.

Initial levels are:

### Level 0 — NEMO-Aware

Understands or references NEMO concepts without portable semantic guarantees.

### Level 1 — NEMO-Structured

Represents mandatory objects, metadata, distinctions, and typed relationships.

### Level 2 — NEMO-Portable

Supports round-trip import and export without losing mandatory semantics.

### Level 3 — NEMO-Interoperable

Exposes protocol operations, capability discovery, idempotent exchange, and explicit conflict handling.

### Level 4 — NEMO-Continuity

Can reconstruct and explain the evolution of knowledge, including supersession, disagreement, evidence lineage, and decision history.

## 20. Reference implementation

NATIA is designated as the planned first official NEMO-Ready support platform and reference implementation.

This relationship is intentionally asymmetric:

- NEMO defines the model and interoperability contract;
- NATIA implements, exercises, and validates that contract;
- feedback from NATIA may evolve NEMO through explicit RFC changes;
- NATIA does not own or redefine NEMO unilaterally.

In practical terms:

> NATIA is NEMO-Ready; NEMO is not NATIA-specific.

## 21. Governance direction

NEMO evolution SHOULD occur through numbered RFCs.

An RFC lifecycle SHOULD include:

- Draft;
- Review;
- Accepted;
- Implemented;
- Final;
- Superseded;
- Withdrawn.

Future governance SHOULD define:

- editor responsibilities;
- proposal submission rules;
- review periods;
- compatibility policy;
- versioning policy;
- conformance ownership;
- dispute resolution;
- change-control authority.

During the initial project phase, the repository `main` branch acts as the canonical working deposit for accepted editorial changes.

## 22. Success criteria for NEMO 0.1

NEMO 0.1 is successful when two independent implementations can:

1. represent the same core knowledge objects;
2. preserve provenance, authorship, semantic class, and lifecycle state;
3. exchange objects without losing mandatory semantics;
4. preserve typed relationships;
5. reconstruct a meaningful sequence of how a conclusion or decision evolved;
6. report unsupported extensions or profiles explicitly;
7. demonstrate conformance through repeatable tests.

## 23. Open questions

The following remain unresolved:

- canonical identifier strategy;
- formal object schema language;
- event ordering in distributed environments;
- replica conflict resolution;
- confidence and validation semantics;
- authentication baseline;
- authorization and delegation model;
- deletion, erasure, and redaction semantics;
- packaging format for portable workspaces;
- signature and integrity model;
- standard query language;
- minimum requirements for conversation extraction;
- formal NEMO-Ready test suite;
- governance after the founding phase.

These questions SHOULD be addressed by subsequent RFCs rather than hidden inside implementation-specific behavior.

## 24. Planned follow-up RFCs

The following sequence is proposed:

- **RFC-0002 — Core Object Model and Vocabulary**
- **RFC-0003 — Canonical JSON Representation**
- **RFC-0004 — Knowledge Event and History Model**
- **RFC-0005 — HTTP Binding and Capability Discovery**
- **RFC-0006 — NEMO Package Import and Export**
- **RFC-0007 — NEMO-Ready Conformance and Test Suite**
- **RFC-0008 — Identity, Authority, and Agent Attribution**
- **RFC-0009 — Security, Confidentiality, and Erasure**
- **RFC-0010 — NATIA Reference Implementation Profile**

## 25. Final principle

NEMO exists to ensure that a team's knowledge does not become a pile of disconnected outputs.

A NEMO-compatible system preserves enough structure, provenance, and history for another person or system to answer:

- What do we currently believe or know?
- Where did that understanding come from?
- What evidence supports or contradicts it?
- Which alternatives were considered?
- Who decided what, and under what assumptions?
- What changed over time?
- What remains unresolved?
- Which actions and artifacts resulted from that evolution?

When those questions remain answerable across time, tools, and participants, continuity has been preserved.
