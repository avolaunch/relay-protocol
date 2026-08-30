# Relay Editorial Workspace

# MASTER_INDEX

**Document:** MASTER_INDEX.md  
**Status:** Current (Living Document)

---

# Purpose

The Master Index is the primary navigation document for the Relay editorial workspace.

It is not normative.

It introduces no new protocol behaviour.

It is not part of the numbered Editorial Audit series and should evolve as the workspace evolves.

Its purpose is to provide a single reference point linking the design corpus, editorial audits, editorial decisions, invariants, terminology and future specification work.

---

# Editorial Workspace

## Design Phase

- Design Corpus (16 documents)
- Public GitHub Repository
- v0.1 Design Baseline

## Editorial Phase

| ID | Deliverable | Status |
|---|---|---|
| EA-01 | Structural Audit | Complete |
| EA-02 | Duplicate Definition Analysis | Complete |
| EA-03 | Protocol Invariants | Complete |
| EA-04 | Canonical Terminology Map | Complete |
| EA-05 | Requirements Audit | Planned |
| EA-06 | Consistency Audit | Planned |
| EA-07 | Consolidation Blueprint | Planned |

## Specification Phase

- GLOSSARY.md
- SPECIFICATION.md
- Reference Schemas
- Reference Implementation
- Conformance Suite
- SDKs

---

# Editorial Decisions Index

## EA-01

ED-001 One canonical definition per protocol term

ED-002 Specification organised by dependency order

ED-003 Preserve responsibility boundaries

ED-004 Separate trust, authority and verification

ED-005 Major interactions occur through explicit protocol mechanisms

## EA-02

ED-008 Single Definition Rule

ED-009 Concept Before Obligation

ED-010 Canonical Controller Term

ED-011 Canonical Commit Term

ED-012 Role and Status Separation

ED-013 Generic Word Protection

## EA-03

ED-014 Two-Level Invariant Model

ED-015 Stable Invariant Identifiers

ED-016 Traceability Required

ED-017 No Silent Promotion

ED-018 No Silent Weakening

ED-019 Protocol Validity Is Limited

## EA-04

ED-020 Canonical terminology established by the terminology map

ED-021 Future glossary generated from the terminology map

ED-022 Ambiguous synonyms are not defined protocol terms

---

# Constitutional Invariants

CI-01 Persistent Identity

CI-02 Controller Authority

CI-03 Provider Replaceability

CI-04 Application Replaceability

CI-05 Stable Canonical Identifiers

CI-06 Explicit and Limited Authority

CI-07 Canonical State Through Authorised Acceptance

CI-08 Independent Verifiability

CI-09 Preservation Without Understanding

CI-10 Provenance and Historical Integrity

CI-11 Role Separation and Purpose Limitation

CI-12 Constitutional Continuity and Open Evolution

---

# Architectural Invariants

AI-01 One Canonical Repository State

AI-02 Commit-Backed Change

AI-03 Atomic Acceptance

AI-04 Safe Migration Boundary

AI-05 Event Non-Authority

AI-06 Detectable Synchronisation Gaps

AI-07 Visibility, Rights and Ownership Are Distinct

AI-08 Mutuality Requires Independent Acts

AI-09 Schema Evolution Preserves History

AI-10 Exact Compliance Claims

---

# Canonical Terminology

## Constitutional

- Relay Identity
- Controller
- Relay Repository
- Relay Record
- Relay Relationship
- Relay Application
- Relay Provider

## Behavioural

- Permission Grant
- Commit
- Event
- Synchronisation
- Migration
- Discovery
- Resolution

## Structural

- Identity Document
- Repository Head
- Schema
- Namespace
- Blob
- Handle
- Witness
- Client

## Governance

- Conformance
- Compliance
- Certification
- Stewardship
- Constitutional Principle

---

# Traceability Map

| Topic | Primary Editorial Source |
|---|---|
| Architecture | EA-01 |
| Duplicate Definitions | EA-02 |
| Constitutional Guarantees | EA-03 |
| Canonical Vocabulary | EA-04 |
| Normative Requirements | EA-05 (planned) |
| Cross-document Consistency | EA-06 (planned) |
| Specification Assembly | EA-07 (planned) |

---

# Current State

The design corpus has completed architectural design.

The editorial programme has established:

- structural integrity;
- canonical terminology;
- constitutional invariants;
- editorial decisions.

The remaining work focuses on extracting, validating and organising normative requirements before drafting the formal Relay Specification.

---

# Recommended Next Step

Proceed to:

**EA-05 — Requirements Audit**

Objective:

Extract every normative requirement from the design corpus, classify it by level (constitutional, architectural, subsystem, implementation), identify duplication, and prepare the requirement set that will drive both the future specification and conformance testing.

---

## Document Status

**MASTER_INDEX.md — Current**

This document is intended to evolve alongside the editorial workspace. It is a navigation aid rather than a completed audit.
