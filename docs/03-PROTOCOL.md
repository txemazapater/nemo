# NEMO Protocol

**Status:** Draft v0.1

## 1. Purpose

The NEMO protocol defines how compatible systems exchange and operate on NEMO knowledge objects.

It is transport-agnostic. HTTP is expected to be the first reference binding, but local files, message queues, peer-to-peer transports, and embedded systems may implement the same operations.

## 2. Protocol capabilities

A NEMO protocol implementation may expose the following capabilities:

- discovery;
- object retrieval;
- object creation;
- relationship creation;
- event append;
- query;
- synchronization;
- validation;
- subscription;
- export and import.

## 3. Capability discovery

A NEMO endpoint SHOULD publish a capability document.

Example:

```json
{
  "nemo_version": "0.1",
  "implementation": "NATIA",
  "capabilities": [
    "objects.read",
    "objects.write",
    "relationships.write",
    "events.append",
    "query.basic",
    "export.json"
  ],
  "profiles": []
}
```

## 4. Core operations

### 4.1 Read object

Retrieve one object by stable identifier.

### 4.2 Create object

Create a new object with provenance and authorship.

### 4.3 Append knowledge event

Record an immutable event that changes the understood state of one or more objects.

### 4.4 Relate objects

Create a typed relationship between existing objects.

### 4.5 Query

Retrieve objects by workspace, actor, type, status, time, source, or relationship.

### 4.6 Export

Produce a portable package containing objects, relationships, events, and required metadata.

### 4.7 Import

Validate and ingest a portable NEMO package while preserving original identifiers and provenance.

## 5. Event-first behavior

Write operations SHOULD produce a knowledge event. An implementation may maintain materialized current state, but the event history remains authoritative for evolution and provenance.

## 6. Idempotency

Create, import, and synchronization operations SHOULD support idempotency so repeated delivery does not create duplicate knowledge.

## 7. Conflict handling

Conflicts MUST NOT be silently resolved by overwriting one source.

An implementation SHOULD preserve both competing states and represent their relationship as disagreement, contradiction, divergence, or unresolved conflict.

## 8. Authentication and authorization

The core protocol does not mandate one identity technology. Implementations MUST nevertheless preserve the logical actor responsible for each contribution.

Authorization policy is implementation-specific in v0.1.

## 9. HTTP reference binding

A future HTTP profile is expected to define routes similar to:

```text
GET    /.well-known/nemo
GET    /nemo/objects/{id}
POST   /nemo/objects
POST   /nemo/events
POST   /nemo/relationships
POST   /nemo/query
POST   /nemo/export
POST   /nemo/import
```

These routes are informative, not yet normative.

## 10. Interoperability principle

A protocol adapter is successful when the receiving system can understand not only the payload, but also:

- what kind of knowledge it represents;
- where it came from;
- who contributed it;
- what state it is in;
- how it relates to prior knowledge;
- whether it supports, contradicts, refines, or supersedes something else.
