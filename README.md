# NEMO

> An open model, specification, and interoperability protocol for preserving the evolution of collective knowledge.

NEMO addresses a problem shared by technical, creative, scientific, analytical, and operational teams: knowledge is generated continuously, but its reasoning, provenance, alternatives, and evolution are usually scattered across tools and eventually lost.

NEMO is designed to preserve not only what a team knows, but how that knowledge appeared, changed, was challenged, gained evidence, became a decision, and influenced action.

## What NEMO is

NEMO combines four complementary elements:

1. **A conceptual model** for knowledge objects and their relationships.
2. **An open specification** defining minimum semantics and conformance.
3. **An interoperability protocol** for exchanging knowledge between tools, agents, repositories, and workspaces.
4. **A NEMO-Ready model** for declaring and testing implementation support.

NEMO is not tied to software development. It is applicable to any team involved in design, investigation, analysis, implementation, experimentation, decision-making, or long-lived complex work.

## Foundational principle

> NEMO preserves the evolution of collective knowledge.

Documents, code, conversations, tickets, experiments, diagrams, and reports are artifacts or sources. NEMO connects them into a traceable knowledge history.

## Relationship with NATIA

NATIA is intended to become the first official support platform and reference implementation of NEMO.

In other words:

> NATIA is NEMO-Ready.

NATIA does not define the standard. NEMO remains independent so that other products, repositories, agents, and platforms can implement it.

## Draft specification

- [`docs/00-VISION.md`](docs/00-VISION.md) — purpose, scope, principles, and non-goals.
- [`docs/01-CORE-MODEL.md`](docs/01-CORE-MODEL.md) — core knowledge objects and relationships.
- [`docs/02-SPECIFICATION.md`](docs/02-SPECIFICATION.md) — initial normative requirements and portable representation.
- [`docs/03-PROTOCOL.md`](docs/03-PROTOCOL.md) — protocol capabilities and operations.
- [`docs/04-NEMO-READY.md`](docs/04-NEMO-READY.md) — proposed implementation conformance levels.

## Existing material

- [`WORKFLOW.md`](WORKFLOW.md) — original working conventions and semantic marks.
- `architecture/` — transversal architecture notes.
- `projects/` — project and research-line notes.

These materials preserve NEMO's origin as a practical technical-memory repository. They will be progressively aligned with the broader specification without erasing their history.

## Status

NEMO is currently at **0.1-draft**.

The immediate objective is to stabilize vocabulary, core semantics, object representation, and the first transport binding before claiming formal interoperability.

## Guiding principles

- Continuity over accumulation.
- Provenance by default.
- Evidence and belief are different.
- Conversations are sources, not final truth.
- Knowledge must remain portable.
- Human and artificial contributors coexist.
- Evolution must remain visible.
- Implementations may differ; semantics must survive.
