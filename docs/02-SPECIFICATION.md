# NEMO Specification

**Version:** 0.1-draft

## 1. Scope

This document defines the normative structure of NEMO.

The keywords **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** indicate requirement strength.

## 2. Conformance layers

NEMO separates four layers:

1. **Conceptual model** — the meaning of knowledge objects and relationships.
2. **Representation** — the serialized form used to store or exchange them.
3. **Protocol** — operations used to create, retrieve, relate, evolve, and synchronize them.
4. **Implementation** — a product, service, repository, or tool that supports one or more conformance levels.

## 3. Mandatory semantics

A conforming implementation MUST:

- represent stable identifiers for core objects;
- preserve object type and semantic status;
- preserve provenance;
- identify the actor responsible for a contribution;
- preserve creation time;
- support typed relationships;
- distinguish observations, hypotheses, evidence, conclusions, and decisions;
- preserve supersession and invalidation history;
- export its supported NEMO objects in a portable representation.

A conforming implementation MUST NOT silently rewrite historical provenance.

## 4. Optional semantics

An implementation MAY support:

- confidence scores;
- access-control policies;
- cryptographic signatures;
- semantic embeddings;
- automatic knowledge extraction;
- graph traversal;
- conflict resolution;
- federated workspaces;
- real-time synchronization;
- domain-specific extensions.

Optional features MUST NOT alter the meaning of mandatory fields.

## 5. Canonical object envelope

The first portable representation is JSON-compatible.

```json
{
  "nemo_version": "0.1",
  "id": "urn:nemo:claim:example-001",
  "type": "claim",
  "status": "HYPOTHESIS",
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

## 6. Extensions

Extensions MUST use a namespace and MUST NOT redefine core fields.

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

## 7. Lifecycle

Objects SHOULD use explicit lifecycle states such as:

- `DRAFT`;
- `ACTIVE`;
- `DISPUTED`;
- `VALIDATED`;
- `REJECTED`;
- `SUPERSEDED`;
- `ARCHIVED`.

Lifecycle state is distinct from semantic type. A hypothesis can be active, disputed, rejected, or superseded without ceasing to be a hypothesis.

## 8. Versioning

The specification follows semantic intent rather than software release cadence.

- Patch changes clarify wording without changing interoperability.
- Minor changes add backward-compatible capabilities.
- Major changes may alter required semantics.

## 9. Domain profiles

A domain profile may add constraints for a field such as engineering, research, healthcare, or industrial operations.

Profiles MUST declare:

- their namespace;
- the NEMO version they extend;
- additional required objects or fields;
- validation rules;
- interoperability impact.

## 10. Open questions for v0.1

The following remain intentionally unresolved:

- canonical identifier strategy;
- conflict resolution across replicas;
- minimum authentication requirements;
- normative schema language;
- event ordering in distributed environments;
- deletion and legal erasure semantics;
- formal definition of confidence and validation.
