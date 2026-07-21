# NEMO Core Model

**Status:** Draft v0.1

## 1. Overview

The NEMO core model defines the minimum set of semantic objects required to represent the evolution of collective knowledge.

An implementation may store these objects in Markdown, JSON, a relational database, a graph database, or another medium. Storage is implementation-specific; meaning is not.

## 2. Core objects

### 2.1 Workspace

A bounded context in which a team pursues an objective.

A workspace may represent a product, research line, client engagement, machine design, incident, department, or temporary initiative.

Minimum properties:

- stable identifier;
- name;
- purpose;
- participants;
- creation time;
- lifecycle state.

### 2.2 Actor

A participant capable of contributing, transforming, validating, or consuming knowledge.

An actor may be:

- a person;
- a team;
- an organization;
- an AI model;
- an autonomous agent;
- an external system.

Actor identity must not imply authority. Responsibility and validation are separate concerns.

### 2.3 Source

The origin from which information is obtained.

Examples:

- conversation;
- meeting;
- document;
- experiment;
- sensor reading;
- code repository;
- ticket;
- external publication;
- human recollection.

### 2.4 Knowledge Event

The smallest meaningful event that changes the state of collective knowledge.

Examples:

- a new observation is recorded;
- a hypothesis is proposed;
- evidence supports or contradicts a claim;
- a decision is adopted;
- an assumption is invalidated;
- an artifact is created;
- a prior conclusion is superseded.

A knowledge event is immutable. Corrections create new events linked to the prior event.

### 2.5 Claim

A statement that may be evaluated, supported, contradicted, accepted, rejected, or superseded.

Claims must carry a semantic status. Initial statuses include:

- `OBSERVATION`;
- `HYPOTHESIS`;
- `ASSUMPTION`;
- `INTERPRETATION`;
- `CONCLUSION`;
- `DECISION`;
- `RISK`;
- `QUESTION`;
- `TASK`.

### 2.6 Evidence

A traceable object used to support, weaken, or contradict a claim.

Evidence may be empirical, documentary, computational, testimonial, or derived. Its type and origin must be explicit.

Evidence does not automatically make a claim true. It modifies the claim's support state.

### 2.7 Decision

A claim adopted as a basis for action by an authorized actor or group.

A decision should reference:

- the problem or question addressed;
- considered alternatives;
- supporting evidence;
- assumptions;
- decision makers;
- effective date;
- consequences;
- conditions for review.

### 2.8 Artifact

A durable output produced or used by the team.

Examples include documents, designs, diagrams, source files, prototypes, datasets, contracts, reports, configurations, and physical test results.

Artifacts are not themselves knowledge events, but their creation, modification, validation, or rejection is.

### 2.9 Conversation

A sequence of contributions between actors.

A conversation is a source of candidate knowledge. It becomes operational knowledge when relevant claims, evidence, decisions, questions, and actions are extracted or linked with explicit status.

### 2.10 Relationship

A typed connection between two NEMO objects.

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

## 3. Common metadata

Every core object should support:

- `id`;
- `type`;
- `title` or human-readable label;
- `created_at`;
- `created_by`;
- `workspace_id`;
- `provenance`;
- `status`;
- `version`;
- optional tags;
- optional confidentiality classification.

## 4. Immutability and evolution

NEMO favors append-only historical truth.

An object may expose a current representation, but prior states must remain traceable. Changes should be represented through new knowledge events and typed relationships such as `REFINES`, `INVALIDATES`, or `SUPERSEDES`.

## 5. Minimal evolution chain

A minimal meaningful chain may be:

```text
Conversation
  -> Hypothesis
  -> Experiment
  -> Evidence
  -> Conclusion
  -> Decision
  -> Artifact
```

Real work is rarely linear. NEMO therefore supports branching, disagreement, parallel hypotheses, reversals, and unresolved questions.

## 6. Required distinction

A NEMO implementation must preserve the distinction between:

- what happened;
- what was observed;
- what someone believes;
- what the team decided;
- what was produced;
- what remains uncertain.

Collapsing those categories into undifferentiated notes is not NEMO-compliant.
