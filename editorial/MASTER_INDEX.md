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

Its purpose is to provide a single reference point linking the design corpus, editorial audits, requirement extraction, extraction review, requirements catalogues, editorial decisions, invariants, terminology and future specification work.

---

# Editorial Workspace

## Design Phase

The v0.1 design corpus contains 16 design documents:

| ID | Design Note | Status |
|---|---|---|
| 00 | `design-notes/00-relay-at-a-glance.md` | Present |
| 01 | `design-notes/01-identity-model.md` | Present |
| 02 | `design-notes/02-repository-model.md` | Present |
| 03 | `design-notes/03-record-model.md` | Present |
| 04 | `design-notes/04-application-and-permission-model.md` | Present |
| 05 | `design-notes/05-relationship-model.md` | Present |
| 06 | `design-notes/06-migration-and-portability-model.md` | Present |
| 07 | `design-notes/07-commit-and-verification-model.md` | Present |
| 08 | `design-notes/08-discovery-and-resolution-model.md` | Present |
| 09 | `design-notes/09-schema-and-interoperability-model.md` | Present |
| 10 | `design-notes/10-event-and-synchronisation-model.md` | Present |
| 11 | `design-notes/11-ecosystem-roles.md` | Present |
| 12 | `design-notes/12-provider-compliance-model.md` | Present |
| 13 | `design-notes/13-application-and-client-compliance-model.md` | Present |
| 14 | `design-notes/14-conformance-testing-model.md` | Present |
| 15 | `design-notes/15-governance-and-evolution-model.md` | Present |

The design corpus remains the authoritative source for requirement extraction.

## Editorial Phase

| ID | Deliverable | Status |
|---|---|---|
| EA-01 | Structural Audit | Complete |
| EA-02 | Duplicate Definition Analysis | Complete |
| EA-03 | Protocol Invariants | Complete |
| EA-04 | Canonical Terminology Map | Complete |
| EA-05 | Requirements Audit | In progress |
| EA-06 | Consistency Audit | Planned |
| EA-07 | Consolidation Blueprint | Planned |

### Completed foundational editorial audits

- `editorial/EA-01 Structural Audit.md`
- `editorial/EA-02 Duplicate Definition Analysis.md`
- `editorial/EA-03 Protocol Invariants.md`
- `editorial/EA-04 Canonical Terminology Map.md`

---

# EA-05 — Requirements Audit

EA-05 is being executed subsystem by subsystem. Requirement Extraction Matrices (`REM`) preserve source traceability; extraction review verifies those matrices before canonical catalogue generation; catalogue parts consolidate verified requirements without losing source mapping.

## Requirement Extraction

| REM | Source Model | Repository State | Status |
|---|---|---|---|
| REM-01 | `01-identity-model.md` | No standalone REM-01 extraction files present | **Legacy – regeneration pending** |
| REM-02 | `02-repository-model.md` | No standalone REM-02 extraction files present | **Legacy – regeneration pending** |
| REM-03 | `03-record-model.md` | Parts 1–10 present; Sections 1–48 | Extraction complete; review pending |
| REM-04 | `04-application-and-permission-model.md` | Parts 1–14 present; Sections 1–67 | Extraction complete; review pending |
| REM-05 | `05-relationship-model.md` | Parts 1–12 present; `REM-05-001`–`REM-05-673` | **Complete and verified** |
| REM-06 | `06-migration-and-portability-model.md` | No REM-06 files present | Not started |
| REM-07 | `07-commit-and-verification-model.md` | No REM-07 files present | Not started |
| REM-08 | `08-discovery-and-resolution-model.md` | No REM-08 files present | Not started |
| REM-09 | `09-schema-and-interoperability-model.md` | No REM-09 files present | Not started |
| REM-10 | `10-event-and-synchronisation-model.md` | No REM-10 files present | Not started |
| REM-11 | `11-ecosystem-roles.md` | No REM-11 files present | Not started |
| REM-12 | `12-provider-compliance-model.md` | No REM-12 files present | Not started |
| REM-13 | `13-application-and-client-compliance-model.md` | No REM-13 files present | Not started |
| REM-14 | `14-conformance-testing-model.md` | No REM-14 files present | Not started |
| REM-15 | `15-governance-and-evolution-model.md` | No REM-15 files present | Not started |

### REM-03 — Record extraction files

- `rem/REM-03 Part 1 — Record Requirement Extraction Matrix (Sections 1–5).md`
- `rem/REM-03 Part 2 — Record Requirement Extraction Matrix (Sections 6–10).md`
- `rem/REM-03 Part 3 — Record Requirement Extraction Matrix (Sections 11–15).md`
- `rem/REM-03 Part 4 — Record Requirement Extraction Matrix (Sections 16–20).md`
- `rem/REM-03 Part 5 — Record Requirement Extraction Matrix (Sections 21–25).md`
- `rem/REM-03 Part 6 — Record Requirement Extraction Matrix (Sections 26–30).md`
- `rem/REM-03 Part 7 — Record Requirement Extraction Matrix (Sections 31–35).md`
- `rem/REM-03 Part 8 — Record Requirement Extraction Matrix (Sections 36–40).md`
- `rem/REM-03 Part 9 — Record Requirement Extraction Matrix (Sections 41–45).md`
- `rem/REM-03 Part 10 — Record Requirement Extraction Matrix (Sections 46–48).md`

### REM-04 — Application and Permission extraction files

REM-04 consists of 14 committed parts covering source Sections 1–67:

- Parts 1–13 cover five-section blocks from Sections 1–65;
- Part 14 covers Sections 66–67.

All 14 files are present under `rem/` and the extraction sequence is complete. No REM-04 extraction-review document is presently committed.

### REM-05 — Relationship extraction files

REM-05 consists of 12 committed parts covering source Sections 1–60 and the continuous extraction range `REM-05-001` through `REM-05-673`.

The extraction was subsequently reviewed and remediated. Its special-status accounting is authoritative for catalogue treatment:

- `REM-05-291`–`REM-05-295`: non-normative model examples;
- `REM-05-636`–`REM-05-645`: non-normative unresolved Open Design Issues;
- `REM-05-646`–`REM-05-671`: explicitly **PROVISIONAL v0.1**;
- `REM-05-673`: non-normative model-boundary hand-off.

---

# Extraction Review / Verification

| Extraction | Review / Verification | Status |
|---|---|---|
| REM-01 | No standalone review present | Legacy – regeneration pending |
| REM-02 | No standalone review present | Legacy – regeneration pending |
| REM-03 | No `REM-03R` review present | **Pending** |
| REM-04 | No `REM-04R` review present | **Pending** |
| REM-05 | `REM-05R-01` review + `REM-05R-02` remediation verification | **Verified** |

Committed REM-05 review artefacts:

- `rem/REM-05R-01 — Relationship Requirement Extraction Review.md`
- `rem/REM-05R-02 — Relationship Requirement Extraction Remediation Verification.md`

`REM-05R-01` identified targeted extraction defects, including normative promotion of examples, descriptive possibilities, open questions, provisional assumptions and the final model-boundary hand-off. The REM-05 extraction was remediated and `REM-05R-02` verified it as ready for Requirements Catalogue generation.

---

# Requirements Catalogue

## EA-05-01 — Identity

Committed catalogue artefacts include:

- `editorial/EA-05-01 Part 1 - Identity Foundations v2.md`
- `editorial/EA-05-01 Part 2 - Relay Identifier v2.md`
- `editorial/EA-05-01 Part 3 - Handles v2.md`
- `editorial/EA-05-01 Part 4 - Identity Documents.md`
- `editorial/EA-05-01 Part 5 - Controller & Authority.md`
- `editorial/EA-05-01 Part 6 - Keys & Authority Model.md`
- `editorial/EA-05-01 Part 7 - Provider Independence Migration.md`
- `editorial/EA-05-01 Part 8 - Recovery.md`
- `editorial/EA-05-01 Part 9 - Lifecycle & Identity States.md`
- `editorial/EA-05-01 Part 10 - Compliance Requirements.md`
- `editorial/EA-05-01 Part 11 - Final Consolidation.md`
- `editorial/EA-05-01 - Identity Requirements Catalogue v1.0.md`

**Catalogue status:** consolidated v1.0 catalogue present. The earlier extraction stage remains historically classified as **Legacy – regeneration pending** because no standalone REM-01 series is present.

## EA-05-02 — Repository

Committed catalogue artefacts include Parts 1–10 and:

- `editorial/EA-05-02 - Repository Requirements Catalogue v1.0.md`

**Catalogue status:** consolidated v1.0 catalogue present. The earlier extraction stage remains historically classified as **Legacy – regeneration pending** because no standalone REM-02 series is present.

## EA-05-03 — Record

No EA-05-03 Requirements Catalogue files are presently committed.

**Catalogue status:** pending extraction review. REM-03 extraction Parts 1–10 are present, but no REM-03R review has yet been committed.

## EA-05-04 — Application and Permission

No EA-05-04 Requirements Catalogue files are presently committed.

**Catalogue status:** pending extraction review. REM-04 extraction Parts 1–14 are present, but no REM-04R review has yet been committed.

## EA-05-05 — Relationship

Committed catalogue artefacts:

- `editorial/EA-05-05 Part 1 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 2 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 3 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 4 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 5 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 6 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 7 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 8 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 9 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 10 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 11 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 12 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 13 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 14 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 15 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 16 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 17 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 18 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 19 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 20 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 21 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 22 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 23 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 24 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 25 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 26 — Relationship Requirements Catalogue.md`
- `editorial/EA-05-05 Part 27 — Relationship Requirements Catalogue.md`

**Catalogue status:** **Parts 1–27 complete.** The canonical Relationship requirement range is `REL-REL-001` through `REL-REL-432`.

Special-status catalogue accounting is preserved:

- `REM-05-291`–`REM-05-295` generated no normative `REL-REL` identifiers;
- `REM-05-636`–`REM-05-645` generated no normative `REL-REL` identifiers;
- `REM-05-646`–`REM-05-671` remain explicitly **PROVISIONAL v0.1** and are represented by `REL-REL-416`–`REL-REL-431`;
- `REM-05-673` generated no normative `REL-REL` identifier;
- `REL-REL-432` is the final canonical Relationship requirement.

No separate consolidated `EA-05-05 ... v1.0` file is presently committed; Parts 1–27 are the completed canonical Relationship catalogue series currently present in the repository.

---

# Editorial Progress

## Design Notes

**Complete as a design corpus:** Design Notes 00–15 are present.

## Requirement Extraction

- REM-01 — **Legacy – regeneration pending**; no standalone extraction files present.
- REM-02 — **Legacy – regeneration pending**; no standalone extraction files present.
- REM-03 — extraction complete; Parts 1–10 present.
- REM-04 — extraction complete; Parts 1–14 present.
- REM-05 — extraction complete; Parts 1–12 present and verified after remediation.
- REM-06 through REM-15 — not started.

## Extraction Review / Verification

- REM-03 — pending.
- REM-04 — pending.
- REM-05 — complete and verified through REM-05R-01 and REM-05R-02.

## Requirements Catalogue

- EA-05-01 Identity — catalogue parts and consolidated v1.0 present; legacy extraction regeneration remains pending.
- EA-05-02 Repository — catalogue parts and consolidated v1.0 present; legacy extraction regeneration remains pending.
- EA-05-03 Record — not started; blocked on REM-03 extraction review.
- EA-05-04 Application and Permission — not started; blocked on REM-04 extraction review.
- EA-05-05 Relationship — **complete through Part 27 / `REL-REL-432`**.
- EA-05-06 through EA-05-15 — not started because corresponding REM extraction has not yet been completed.

## Catalogue Status

EA-05 is **in progress**, not planned and not complete.

Completed catalogue work exists for Identity, Repository and Relationship. Record and Application/Permission have completed extraction but have not yet passed the review stage required by the current editorial method. Models 06–15 have not yet entered requirement extraction.

## Remaining Editorial Work

The next unfinished workstream in dependency/order terms is **REM-03 extraction review** against `design-notes/03-record-model.md`. After any required remediation and verification, EA-05-03 Record Requirements Catalogue generation can begin. REM-04 should then receive the same review treatment before EA-05-04 catalogue generation.

The later REM-06 through REM-15 extraction programme remains outstanding. EA-06 and EA-07 remain planned downstream audits and should not begin until the requirements-audit state is sufficiently complete.

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
| Normative Requirements | EA-05 / REM and catalogue series |
| Cross-document Consistency | EA-06 (planned) |
| Specification Assembly | EA-07 (planned) |

---

# Current State

The design corpus has completed architectural design and all 16 design notes are present.

The editorial programme has established structural integrity, canonical terminology, constitutional and architectural invariants, and editorial decisions. EA-05 has progressed materially beyond its original planned state: Identity and Repository have committed catalogue series and consolidated v1.0 documents; Record and Application/Permission have completed extraction series awaiting review; and Relationship has completed extraction, review, remediation verification and canonical catalogue generation through `REL-REL-432`.

The requirements audit remains incomplete across the full design corpus because REM-06 through REM-15 have not yet been generated and the REM-03 / REM-04 review-to-catalogue path remains unfinished.

---

# Recommended Next Step

Proceed to:

**REM-03R-01 — Record Requirement Extraction Review**

Objective:

Review all ten REM-03 extraction parts against `design-notes/03-record-model.md`, verify complete section and numbering coverage, preserve normative strength and qualifications, identify unsupported promotion or omission, and determine whether targeted remediation is required before EA-05-03 Record Requirements Catalogue generation.

This is the earliest completed extraction series that has not yet passed the review stage now established by REM-05.

---

## Document Status

**MASTER_INDEX.md — Current**

This document is intended to evolve alongside the editorial workspace. It is a navigation aid rather than a completed audit.
