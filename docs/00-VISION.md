# NEMO Vision

**Status:** Draft v0.1

## Purpose

NEMO is an open model, specification, and interoperability protocol for preserving and evolving the collective knowledge of a team.

Its scope is not limited to software development. NEMO is intended for any team that designs, investigates, analyses, decides, experiments, implements, or maintains complex work over time.

Examples include engineering, product design, scientific research, industrial projects, architecture, operations, consulting, and multidisciplinary innovation.

## The problem

Teams generate knowledge continuously, but most of it is fragmented across conversations, documents, tickets, source code, experiments, meetings, personal notes, and implicit experience.

Traditional systems preserve outputs. They rarely preserve the path that produced those outputs.

As a result, teams lose:

- the reasoning behind decisions;
- discarded alternatives and why they were rejected;
- the relationship between evidence, hypotheses, and conclusions;
- the context that makes an artifact understandable;
- continuity when people, tools, or project phases change.

## The NEMO proposition

NEMO treats collective knowledge as an evolving system rather than a static archive.

It provides:

1. **A conceptual model** for representing knowledge, evidence, decisions, conversations, hypotheses, artifacts, and their relationships.
2. **A specification** that defines the minimum semantics required for compatible implementations.
3. **A protocol** for exchanging and synchronizing NEMO knowledge objects between tools, agents, repositories, and workspaces.
4. **A readiness model** that allows a product or service to declare itself `NEMO-Ready` at a defined level of compliance.

## Foundational idea

> NEMO preserves the evolution of collective knowledge.

NEMO does not merely store what a team knows. It records how that knowledge appeared, changed, was challenged, gained evidence, became a decision, and eventually influenced action.

## NEMO and implementations

NEMO is independent of any single application.

NATIA is intended to become the first official NEMO-Ready support platform and reference implementation, but NEMO must remain usable by other systems.

A NEMO-compatible ecosystem may include:

- collaborative workspaces;
- AI assistants and autonomous agents;
- source-code repositories;
- issue trackers;
- laboratory notebooks;
- document systems;
- engineering tools;
- business and research platforms.

## Design principles

1. **Continuity over accumulation**  
   The objective is not to collect more information, but to maintain an understandable thread through time.

2. **Provenance by default**  
   Every relevant knowledge object should identify its origin, authorship, time, and supporting context.

3. **Evidence and belief are different**  
   Observations, hypotheses, decisions, assumptions, and conclusions must not be treated as equivalent.

4. **Conversations are sources, not final truth**  
   A conversation may create knowledge, but its claims require structure, status, and traceability.

5. **Knowledge must remain portable**  
   Teams should not lose their intellectual history because they change tools or vendors.

6. **Human and artificial contributors coexist**  
   NEMO must represent contributions from people, teams, software agents, and models without erasing authorship or responsibility.

7. **Evolution must be visible**  
   Superseded ideas should remain traceable instead of being silently overwritten.

8. **Implementations may differ; semantics must survive**  
   A lightweight Markdown repository and a graph-based platform may both be NEMO-Ready if they preserve the required meaning.

## Non-goals

NEMO is not:

- a note-taking application;
- a document management product;
- a replacement for Git, issue trackers, or chat systems;
- a universal ontology for all human knowledge;
- an AI model or agent framework;
- a requirement that every event be recorded forever.

NEMO connects and gives continuity to existing systems. It does not need to replace them.

## Initial success criterion

NEMO v0.1 succeeds when two independent implementations can:

1. represent the same core knowledge objects;
2. preserve provenance and status;
3. exchange those objects without losing essential semantics;
4. reconstruct a meaningful sequence of how a decision or conclusion evolved.
