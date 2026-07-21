# NEMO-Ready

**Status:** Draft v0.1

`NEMO-Ready` identifies an implementation that preserves defined NEMO semantics and interoperability guarantees.

It is not a marketing label without evidence. A product must declare its supported NEMO version, level, capabilities, limitations, and tested conformance.

## Level 0 — NEMO-Aware

The implementation understands NEMO concepts and can reference NEMO identifiers, but does not guarantee portable representation.

Typical examples:

- a documentation template;
- a repository convention;
- a read-only visualization.

## Level 1 — NEMO-Structured

The implementation can represent the mandatory core objects and metadata.

Requirements:

- stable identifiers;
- actor, workspace, time, and provenance;
- semantic object type;
- lifecycle state;
- typed relationships;
- distinction between observation, hypothesis, evidence, conclusion, and decision.

## Level 2 — NEMO-Portable

The implementation satisfies Level 1 and can export and import portable NEMO objects without losing mandatory semantics.

Requirements:

- versioned serialization;
- round-trip preservation of identifiers and provenance;
- extension namespace support;
- validation report for unsupported fields or profiles.

## Level 3 — NEMO-Interoperable

The implementation satisfies Level 2 and exposes protocol operations for discovery, query, creation, relationships, events, and synchronization.

Requirements:

- capability discovery;
- idempotent exchange;
- explicit conflict handling;
- protocol conformance tests;
- preservation of knowledge evolution across systems.

## Level 4 — NEMO-Continuity

The implementation satisfies Level 3 and can reconstruct and explain the evolution of a body of knowledge.

Requirements:

- immutable event history;
- traceable supersession and invalidation;
- competing hypotheses and disagreements;
- decision lineage;
- linkage from source conversation or evidence to resulting action or artifact;
- human-readable continuity views.

## Declaring conformance

A declaration should use this form:

```text
Implementation: NATIA
NEMO version: 0.1
NEMO-Ready level: 2
Profiles: none
Capabilities: objects, relationships, events, import, export
Known limitations: no distributed synchronization
Conformance report: <reference>
```

## Reference implementation

NATIA is planned as the first official NEMO-Ready support platform and reference implementation.

NATIA does not define NEMO. It implements and exercises the specification. Feedback from NATIA may evolve NEMO through the same explicit, traceable process that NEMO requires from other knowledge systems.
