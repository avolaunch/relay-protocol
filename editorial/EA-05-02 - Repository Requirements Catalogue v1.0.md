# EA-05-02 — Repository Requirements Catalogue v1.0

**Relay Protocol Editorial Programme**

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Document Status:** Canonical v1.0  
**Specification Type:** Normative Requirements Catalogue

---

## Abstract

This document is the canonical Repository Requirements Catalogue for the Relay Protocol. It consolidates the approved Repository subsystem requirements into a single normative specification.

## Table of Contents

1. Repository Foundations
2. Records, Record URIs, Collections & Record Keys
3. Record Lifecycle & Immutable History
4. Commits, Repository Head & Integrity
5. Provenance, Blobs & Record Classification
6. Schemas, Derived Records & External References
7. Export & Migration
8. Forks, Caching, Indexes & Availability
9. Repository Deletion, Provider Obligations, Application Obligations & Required Operations
10. Repository Invariants, Compliance & Final Consolidation

---


<!-- Part 1 -->
## Part 1 — Repository Foundations

**Editorial Programme:** EA-05 — Normative Requirements Audit
**Subsystem:** Repository
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the constitutional foundations of the Relay Repository.

It establishes the immutable principles governing Repository existence, authority, independence and continuity. All subsequent Repository requirements shall be interpreted consistently with these constitutional principles.

---

# 2. Scope

This part defines normative requirements governing:

- Repository existence
- Repository authority
- Repository independence
- Repository continuity
- Repository identity
- Repository purpose
- Repository constitutional boundaries

---

# 3. Requirements

---

## REL-REP-001

### Title

Repository Existence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Relay Identity **MUST** possess exactly one canonical Relay Repository.

### Rationale

The Repository is the constitutional home of a Relay Identity's protocol state.

### Source

REM-02 — RREM-0001

### Related Invariants

- CI-01
- CI-03

---

## REL-REP-002

### Title

Canonical Repository Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Repository **MUST** be recognised as the canonical source of protocol records for its associated Relay Identity.

### Rationale

All compliant implementations require a single authoritative repository.

### Source

REM-02 — RREM-0018

### Related Invariants

- CI-08

---

## REL-REP-003

### Title

Repository Independence from Applications

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Repository **MUST NOT** permanently depend upon any individual application.

### Rationale

Applications consume Repository data but do not define Repository existence.

### Source

REM-02 — RREM-0002, RREM-0004

### Related Invariants

- CI-03

---

## REL-REP-004

### Title

Repository Independence from Providers

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Repository **MUST NOT** permanently depend upon a specific Relay Provider.

### Rationale

Changing providers must never redefine the Repository.

### Source

REM-02 — RREM-0003

### Related Invariants

- CI-03

---

## REL-REP-005

### Title

Repository Independence from Devices

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

Replacing devices **MUST NOT** alter the existence or identity of the Relay Repository.

### Rationale

Repositories outlive client devices.

### Source

REM-02 — RREM-0005

### Related Invariants

- CI-01

---

## REL-REP-006

### Title

Repository Independence from Handles

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

Changes to Handles **MUST NOT** alter the Repository.

### Rationale

Handles are presentation-layer identifiers rather than repository identifiers.

### Source

REM-02 — RREM-0006

### Related Invariants

- CI-01

---

## REL-REP-007

### Title

Repository Independence from Key Rotation

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

Rotation of cryptographic keys **MUST NOT** create a new Repository.

### Rationale

Repository continuity is independent of authentication lifecycle.

### Source

REM-02 — RREM-0007

### Related Invariants

- CI-05

---

## REL-REP-008

### Title

Repository Continuity During Service Interruption

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Temporary interruption of Repository services **MUST NOT** affect Repository identity or continuity.

### Rationale

Operational availability and constitutional existence are distinct concepts.

### Source

REM-02 — RREM-0008

### Related Invariants

- CI-03

---

## REL-REP-009

### Title

Repository Continuity During Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Migration between compliant implementations **MUST** preserve the Repository as the same constitutional Repository.

### Rationale

Migration transfers operational responsibility rather than constitutional identity.

### Source

REM-02 — RREM-0009

### Related Invariants

- CI-03

---

## REL-REP-010

### Title

Repository Operational Purpose

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Repository **MUST** function as the operational record system for a Relay Identity rather than as a provider account, storage service or archive.

### Rationale

The Repository is a protocol construct independent of implementation technologies.

### Source

REM-02 — RREM-0010

### Related Invariants

- CI-08

---

## REL-REP-011

### Title

Cross-Application Repository Operation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Repository **MUST** support authorised creation and use of Repository Records across multiple compatible applications.

### Rationale

Repositories enable interoperability rather than application lock-in.

### Source

REM-02 — RREM-0012

### Related Invariants

- CI-03

---

## REL-REP-012

### Title

Repository Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The Repository **MUST** support independent verification of authorised Repository changes.

### Rationale

Independent verification is fundamental to Repository trust.

### Source

REM-02 — RREM-0013

### Related Invariants

- CI-08

---

## REL-REP-013

### Title

Repository History Inspection

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The Repository **MUST** permit inspection of its recorded history.

### Rationale

Repository history forms part of the protocol's audit model.

### Source

REM-02 — RREM-0014

### Related Invariants

- CI-08

---

## REL-REP-014

### Title

Repository Export

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Every Relay Repository **MUST** support protocol-defined export.

### Rationale

Export is essential for Repository portability.

### Source

REM-02 — RREM-0015

### Related Invariants

- CI-03

---

## REL-REP-015

### Title

Repository Migration Support

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Every Relay Repository **MUST** support migration between compliant implementations.

### Rationale

Migration is a constitutional capability of the Repository.

### Source

REM-02 — RREM-0016

### Related Invariants

- CI-03

---

## REL-REP-016

### Title

Repository Continuity After Migration

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Following migration, the Repository **MUST** remain fully usable as the same Repository.

### Rationale

Migration changes implementation, not Repository identity.

### Source

REM-02 — RREM-0017

### Related Invariants

- CI-03

---

## REL-REP-017

### Title

Repository and Relay Identity Separation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Repository **MUST** remain conceptually distinct from the Relay Identity with which it is associated.

### Rationale

Identity defines constitutional ownership; the Repository stores constitutional state.

### Source

REM-02 — RREM-0020, RREM-0021

### Related Invariants

- CI-01

---

## REL-REP-018

### Title

Repository Structural Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Repository **MUST** define the canonical organisation, history and authorisation of Repository Records.

### Rationale

Repository authority extends beyond storage to protocol governance of repository state.

### Source

REM-02 — RREM-0022, RREM-0023, RREM-0024

### Related Invariants

- CI-08

---

## REL-REP-019

### Title

Repository Component Model

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Repository **MUST** consist of the protocol-defined Repository components.

### Rationale

A common component model enables interoperability between implementations.

### Source

REM-02 — RREM-0025

### Related Invariants

- CI-08

---

## REL-REP-020

### Title

Repository Component Portability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Repository components **MUST** remain portable between compliant Relay Providers.

### Rationale

Component portability prevents provider-specific repository implementations.

### Source

REM-02 — RREM-0026

### Related Invariants

- CI-03

---

## REL-REP-021

### Title

Repository Identifier

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Relay Repository **MUST** possess exactly one permanent Repository Identifier.

### Rationale

The Repository Identifier provides stable protocol identity for the Repository itself.

### Source

REM-02 — RREM-0027

### Related Invariants

- CI-05

---

## REL-REP-022

### Title

Repository Identifier Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Repository Identifier **MUST NOT** depend upon provider-specific identifiers, namespaces or implementation details.

### Rationale

Repository identity must remain independent of hosting providers.

### Source

REM-02 — RREM-0028, RREM-0030

### Related Invariants

- CI-03
- CI-05

---

## REL-REP-023

### Title

Repository Identifier Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

Migration between compliant providers **MUST NOT** create a new Repository Identifier.

### Rationale

Repository migration preserves constitutional identity.

### Source

REM-02 — RREM-0029

### Related Invariants

- CI-05

---

# Editorial Review Notes

This part establishes the constitutional foundations of the Repository subsystem. It defines the Repository as the canonical, provider-independent operational home of a Relay Identity's protocol state and separates Repository identity from applications, providers, devices, Handles and authentication mechanisms. It also introduces the Repository Identifier and establishes portability, migration and canonical authority as constitutional properties rather than implementation features.

---

This follows the same editorial pattern that we settled on for the Identity Requirements Catalogue: each requirement maps directly back to one or more entries in **REM-02**, contains a single independently testable behaviour, and is presented as a standalone normative requirement ready for inclusion in the eventual assembled **EA-05-02 — Repository Requirements Catalogue v1.0**.

<!-- Part 2 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Repository Records, Record URIs, Collections and Record Keys.

It establishes how Repository content is identified, organised and addressed independently of providers and applications while preserving stable protocol identity.

---

# 2. Scope

This part defines normative requirements governing:

- Repository Records
- Record metadata
- Record URIs
- Collections
- Collection ownership
- Core and external collections
- Record Keys

---

# 3. Requirements

## REL-REP-024

### Title
Repository Record

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** represent the smallest independently addressable structured protocol object within a Relay Repository.

### Rationale
Defines the fundamental protocol unit of repository content.

### Source
REM-02 — RREM-0031

### Related Invariants
- CI-08

---

## REL-REP-025

### Title
Repository Record Metadata

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** contain sufficient metadata to identify its type, logical identity, authorising identity, creation time, version and governing schema.

### Rationale
Supports interoperability and independent verification.

### Source
REM-02 — RREM-0032 to RREM-0037

### Related Invariants
- CI-08

---

## REL-REP-026

### Title
Repository Record Content

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** contain its structured content together with the protocol-defined integrity information and, where required, a valid signature.

### Rationale
Ensures complete, verifiable repository records.

### Source
REM-02 — RREM-0038 to RREM-0040

### Related Invariants
- CI-08

---

## REL-REP-027

### Title
Record URI

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** possess a stable protocol-level Record URI.

### Rationale
Provides permanent logical addressing.

### Source
REM-02 — RREM-0041

### Related Invariants
- CI-05

---

## REL-REP-028

### Title
Record URI Stability

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
A Record URI **MUST NOT** change because of provider migration, application changes, Handle changes or Record revisions.

### Rationale
Logical identity is independent of operational change.

### Source
REM-02 — RREM-0042 to RREM-0045

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-029

### Title
Logical Record Identity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
A Record URI **MUST** identify the logical Record rather than an individual historical version.

### Rationale
Separates identity from version history.

### Source
REM-02 — RREM-0046, RREM-0047

### Related Invariants
- CI-08

---

## REL-REP-030

### Title
Collections

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Repository Records **MUST** be organised into Collections according to protocol-defined schema families.

### Rationale
Provides consistent repository organisation.

### Source
REM-02 — RREM-0048 to RREM-0050

### Related Invariants
- CI-08

---

## REL-REP-031

### Title
Collection Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Schema publishers **MUST NOT** acquire ownership of Repository Records solely because those Records use schemas published by them.

### Rationale
Schema publication and record ownership are independent.

### Source
REM-02 — RREM-0051, RREM-0052

### Related Invariants
- CI-01

---

## REL-REP-032

### Title
Collection Extensibility

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
Relay **MAY** define core Collections, and third parties **MAY** define additional protocol-compatible Collections.

### Rationale
Supports ecosystem extensibility.

### Source
REM-02 — RREM-0053 to RREM-0056

### Related Invariants
- CI-03

---

## REL-REP-033

### Title
Record Key

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** possess a unique, stable Record Key within its Collection.

### Rationale
Provides stable logical identity within collections.

### Source
REM-02 — RREM-0057, RREM-0058

### Related Invariants
- CI-05

---

## REL-REP-034

### Title
Non-semantic Record Keys

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
Record Keys **SHOULD** be non-semantic and **MUST** remain independent of titles, filenames and presentation labels.

### Rationale
Avoids semantic coupling and preserves identifier stability.

### Source
REM-02 — RREM-0059, RREM-0060

### Related Invariants
- CI-05

---

# Editorial Review Notes

This part establishes the Repository addressing model. Repository Records, Record URIs, Collections and Record Keys together provide stable, provider-independent identification and organisation of repository content. These requirements separate logical identity from presentation, schema ownership and implementation details, ensuring that repository content remains portable and interoperable across compliant implementations.

<!-- Part 3 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing the lifecycle of Repository Records and the preservation of immutable Repository History.

It establishes how Repository Records evolve while ensuring that historical evidence remains permanently verifiable and independent of subsequent changes.

---

# 2. Scope

This part defines normative requirements governing:

- Record lifecycle
- Record creation
- Record modification
- Record deletion
- Record restoration
- Immutable history
- Historical verification

---

# 3. Requirements

## REL-REP-035

### Title
Record Lifecycle

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** participate in a protocol-defined lifecycle.

### Rationale
Lifecycle behaviour is a constitutional property of Repository Records.

### Source
REM-02 — RREM-0061

### Related Invariants
- CI-08

---

## REL-REP-036

### Title
Record Creation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Creating a Repository Record **MUST** establish a new logical Repository Record.

### Rationale
Creation is the initial lifecycle event.

### Source
REM-02 — RREM-0062

### Related Invariants
- CI-08

---

## REL-REP-037

### Title
Record Modification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Modification of a Repository Record **MUST** create a new version while preserving the logical identity of the Record.

### Rationale
Supports historical continuity without changing logical identity.

### Source
REM-02 — RREM-0063, RREM-0064

### Related Invariants
- CI-05
- CI-08

---

## REL-REP-038

### Title
Record Deletion

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Deletion of a Repository Record **MUST** be represented as a lifecycle event rather than silent removal.

### Rationale
Maintains an auditable repository history.

### Source
REM-02 — RREM-0065

### Related Invariants
- CI-08

---

## REL-REP-039

### Title
Record Restoration

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Restoring a Repository Record **MUST** preserve the original logical Record identity.

### Rationale
Restoration resumes an existing lifecycle rather than creating a new identity.

### Source
REM-02 — RREM-0066

### Related Invariants
- CI-05

---

## REL-REP-040

### Title
Lifecycle Traceability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
All lifecycle transitions **MUST** be recorded and independently verifiable within Repository History.

### Rationale
Provides complete lifecycle auditability.

### Source
REM-02 — RREM-0067, RREM-0068

### Related Invariants
- CI-08

---

## REL-REP-041

### Title
Current and Historical State

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** distinguish the current state of a Repository Record from its historical states.

### Rationale
Separates operational state from historical evidence.

### Source
REM-02 — RREM-0069

### Related Invariants
- CI-08

---

## REL-REP-042

### Title
Lifecycle Consistency

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Repository lifecycle behaviour **MUST** remain consistent across compliant implementations.

### Rationale
Ensures interoperable lifecycle semantics.

### Source
REM-02 — RREM-0070

### Related Invariants
- CI-03

---

## REL-REP-043

### Title
Immutable Repository History

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository History **MUST** be append-only.

### Rationale
Immutable history underpins repository trust.

### Source
REM-02 — RREM-0071

### Related Invariants
- CI-08

---

## REL-REP-044

### Title
Historical Preservation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Historical Repository entries **MUST** be preserved following Record modification, deletion or restoration.

### Rationale
Historical evidence survives lifecycle changes.

### Source
REM-02 — RREM-0072, RREM-0073

### Related Invariants
- CI-08

---

## REL-REP-045

### Title
Historical Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Historical Repository entries **MUST** remain independently verifiable and individually addressable.

### Rationale
Supports long-term verification and auditing.

### Source
REM-02 — RREM-0074, RREM-0078

### Related Invariants
- CI-08

---

## REL-REP-046

### Title
Historical State Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Repository History **MUST** distinguish historical Repository states from the current Repository state.

### Rationale
Ensures clear navigation between current and historical information.

### Source
REM-02 — RREM-0075

### Related Invariants
- CI-08

---

## REL-REP-047

### Title
History Portability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository History **MUST** preserve its integrity during Repository migration and export.

### Rationale
Audit history is portable protocol state.

### Source
REM-02 — RREM-0076, RREM-0077

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-048

### Title
Protocol History

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Immutable Repository History **MUST** remain distinct from provider backup, archival or operational storage mechanisms.

### Rationale
Protocol history is a constitutional concept independent of infrastructure.

### Source
REM-02 — RREM-0079

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-049

### Title
Canonical Audit Record

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository History **MUST** constitute the canonical audit record of Repository evolution.

### Rationale
Defines the authoritative historical record for the Repository.

### Source
REM-02 — RREM-0080

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part establishes the distinction between mutable Repository state and immutable Repository History. Records may evolve throughout their lifecycle, but the evidence of those changes becomes part of a permanent, append-only audit history. This separation ensures that compliant implementations preserve both operational flexibility and long-term verifiability.

<!-- Part 4 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Commits, the Repository Head and Repository Integrity.

It establishes how repository state changes are represented, how the current canonical state is identified, and how integrity is independently verified across compliant implementations.

---

# 2. Scope

This part defines normative requirements governing:

- Commits
- Repository Head
- Repository Integrity
- Cryptographic integrity
- Independent verification

---

# 3. Requirements

## REL-REP-050

### Title
Repository Commits

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
All Repository state changes **MUST** be represented by protocol-defined Commits.

### Rationale
Commits are the exclusive mechanism for repository state transitions.

### Source
REM-02 — RREM-0081, RREM-0082

### Related Invariants
- CI-08

---

## REL-REP-051

### Title
Commit Metadata

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Commit **MUST** record sufficient metadata to support independent verification, including its authorising authority, creation time and relationship to the previous repository state.

### Rationale
Provides traceability and verification.

### Source
REM-02 — RREM-0083 to RREM-0086

### Related Invariants
- CI-08

---

## REL-REP-052

### Title
Immutable Commits

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Accepted Commits **MUST** be immutable and permanently preserved within Repository History.

### Rationale
Maintains the integrity of repository evolution.

### Source
REM-02 — RREM-0087, RREM-0088

### Related Invariants
- CI-08

---

## REL-REP-053

### Title
Repository Head

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Repository **MUST** expose a single canonical Repository Head representing the current repository state.

### Rationale
Provides a unique reference to the current state.

### Source
REM-02 — RREM-0089

### Related Invariants
- CI-08

---

## REL-REP-054

### Title
Repository Head Advancement

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
The Repository Head **MUST** advance only through valid Commit processing and **MUST** always reference the latest accepted repository state.

### Rationale
Prevents arbitrary mutation of repository state.

### Source
REM-02 — RREM-0090, RREM-0091

### Related Invariants
- CI-08

---

## REL-REP-055

### Title
Historical Commit Accessibility

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Historical Commits **MUST** remain accessible after the Repository Head advances.

### Rationale
Current state must not replace historical evidence.

### Source
REM-02 — RREM-0092

### Related Invariants
- CI-08

---

## REL-REP-056

### Title
Repository Head Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
The Repository Head **MUST** remain distinguishable from historical repository states.

### Rationale
Separates current operational state from historical history.

### Source
REM-02 — RREM-0093

### Related Invariants
- CI-08

---

## REL-REP-057

### Title
Repository Integrity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository integrity **MUST** be independently verifiable.

### Rationale
Independent verification is fundamental to repository trust.

### Source
REM-02 — RREM-0094

### Related Invariants
- CI-08

---

## REL-REP-058

### Title
Integrity Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Integrity verification **MUST** detect unauthorised modification and remain valid following repository migration and export.

### Rationale
Integrity guarantees persist throughout repository portability.

### Source
REM-02 — RREM-0095 to RREM-0097

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-059

### Title
Implementation-independent Integrity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Repository integrity verification **MUST** remain independent of storage mechanisms and implementation-specific technologies.

### Rationale
Ensures provider-neutral verification.

### Source
REM-02 — RREM-0098

### Related Invariants
- CI-03

---

## REL-REP-060

### Title
Protocol Cryptographic Integrity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository cryptographic integrity **MUST** rely upon protocol-defined mechanisms rather than provider-specific implementations.

### Rationale
Preserves protocol independence.

### Source
REM-02 — RREM-0099

### Related Invariants
- CI-03

---

## REL-REP-061

### Title
Long-term Cryptographic Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository cryptographic mechanisms **MUST** support long-term independent verification and remain valid across compliant implementations, migration and export.

### Rationale
Cryptographic trust must survive operational change.

### Source
REM-02 — RREM-0100 to RREM-0102

### Related Invariants
- CI-03
- CI-08

---

# Editorial Review Notes

This part defines the Repository trust model. Commits provide the exclusive mechanism for repository evolution, the Repository Head identifies the current canonical state, and protocol-defined integrity mechanisms ensure that repository content can be independently verified regardless of provider, storage technology or migration history.

<!-- Part 5 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing provenance, binary objects (Blobs), content addressing and record classification within a Relay Repository.

It establishes how repositories preserve evidence of origin, support non-structured content and classify records without compromising portability, integrity or constitutional authority.

---

# 2. Scope

This part defines normative requirements governing:

- Provenance
- Blob objects
- Content addressing
- Record classification

---

# 3. Requirements

## REL-REP-062

### Title
Repository Provenance

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Relay Repository **MUST** preserve protocol-defined provenance for repository content.

### Rationale
Provenance provides verifiable evidence of origin.

### Source
REM-02 — RREM-0103

### Related Invariants
- CI-08

---

## REL-REP-063

### Title
Provenance Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Provenance information **MUST** remain associated with repository content throughout its lifecycle and distinguish original creation from subsequent modification.

### Rationale
Supports long-term traceability.

### Source
REM-02 — RREM-0104, RREM-0105

### Related Invariants
- CI-08

---

## REL-REP-064

### Title
Portable Provenance

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository provenance **MUST** be preserved during repository migration and export independently of application-specific metadata.

### Rationale
Preserves origin across implementations.

### Source
REM-02 — RREM-0106 to RREM-0108

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-065

### Title
Blob Objects

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Binary repository content **MUST** be represented through protocol-defined Blob objects where appropriate.

### Rationale
Provides a consistent binary object model.

### Source
REM-02 — RREM-0109

### Related Invariants
- CI-08

---

## REL-REP-066

### Title
Blob Identity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Every Blob **MUST** possess a stable protocol identity independent of its storage location.

### Rationale
Separates object identity from implementation.

### Source
REM-02 — RREM-0110, RREM-0111

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-067

### Title
Blob Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Blob integrity **MUST** be independently verifiable and preserved during migration and export.

### Rationale
Binary content must remain trustworthy and portable.

### Source
REM-02 — RREM-0112 to RREM-0115

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-068

### Title
Content Addressing

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Content-addressed repository objects **MUST** use deterministic, content-derived identities that support independent integrity verification.

### Rationale
Enables repeatable verification.

### Source
REM-02 — RREM-0116 to RREM-0119

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-069

### Title
Record Classification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Repository Records **MUST** be classified according to protocol-defined record classifications.

### Rationale
Provides stable semantic organisation.

### Source
REM-02 — RREM-0120, RREM-0121

### Related Invariants
- CI-08

---

## REL-REP-070

### Title
Classification Portability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Unknown record classifications **MUST** be preserved during repository export and migration.

### Rationale
Supports forward compatibility.

### Source
REM-02 — RREM-0122, RREM-0123

### Related Invariants
- CI-03

---

## REL-REP-071

### Title
Classification Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Record classification **MUST NOT** alter repository ownership, authority or constitutional semantics.

### Rationale
Classification describes content but does not redefine authority.

### Source
REM-02 — RREM-0124

### Related Invariants
- CI-02

---

## REL-REP-072

### Title
Classification Extensibility

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
Protocol-compatible record classifications **MAY** be extended without altering existing protocol semantics.

### Rationale
Supports future protocol evolution.

### Source
REM-02 — RREM-0125

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part establishes the Repository's content semantics. Provenance preserves evidence of origin, Blobs provide a protocol abstraction for binary content, content addressing enables deterministic verification, and record classification supplies an extensible semantic framework while preserving constitutional ownership, authority and interoperability.

<!-- Part 6 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing repository schemas, derived records and external references.

It establishes how repositories achieve interoperability through schemas, distinguish canonical records from derived representations, and reference external resources without compromising repository integrity, portability or constitutional authority.

---

# 2. Scope

This part defines normative requirements governing:

- Schemas
- Schema evolution
- Derived Records
- External References

---

# 3. Requirements

## REL-REP-073

### Title
Schema Conformance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Every Repository Record **MUST** conform to an associated protocol schema.

### Rationale
Schemas provide consistent interpretation across implementations.

### Source
REM-02 — RREM-0126, RREM-0127

### Related Invariants
- CI-08

---

## REL-REP-074

### Title
Schema Identity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every protocol schema **MUST** possess a stable identity independent of providers and implementations.

### Rationale
Schema identity must remain portable.

### Source
REM-02 — RREM-0128, RREM-0129

### Related Invariants
- CI-03

---

## REL-REP-075

### Title
Schema Portability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Unknown schemas **MUST** be preserved during Repository export and migration.

### Rationale
Supports forward compatibility.

### Source
REM-02 — RREM-0130, RREM-0131

### Related Invariants
- CI-03

---

## REL-REP-076

### Title
Schema Evolution

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
Schema evolution **SHOULD** preserve compatibility in accordance with protocol-defined evolution rules.

### Rationale
Allows controlled evolution without unnecessary breakage.

### Source
REM-02 — RREM-0132, RREM-0133

### Related Invariants
- CI-08

---

## REL-REP-077

### Title
Derived Record Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Derived Records **MUST** remain distinguishable from canonical Repository Records.

### Rationale
Maintains constitutional authority of canonical data.

### Source
REM-02 — RREM-0134

### Related Invariants
- CI-08

---

## REL-REP-078

### Title
Derived Record Traceability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Derived Records **MUST** reference their originating canonical Records and remain independently identifiable.

### Rationale
Supports provenance and auditing.

### Source
REM-02 — RREM-0135, RREM-0137, RREM-0139

### Related Invariants
- CI-08

---

## REL-REP-079

### Title
Canonical Record Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Derived Records **MUST NOT** replace or redefine canonical Repository Records.

### Rationale
Derived representations do not become protocol authority.

### Source
REM-02 — RREM-0136

### Related Invariants
- CI-08

---

## REL-REP-080

### Title
Derived Record Regeneration

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
Derived Records **MAY** be regenerated provided that canonical Repository Records remain unchanged.

### Rationale
Supports deterministic regeneration.

### Source
REM-02 — RREM-0138

### Related Invariants
- CI-08

---

## REL-REP-081

### Title
External References

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
Repository Records **MAY** reference external resources while maintaining a clear distinction between protocol-managed content and external content.

### Rationale
Supports integration without compromising repository semantics.

### Source
REM-02 — RREM-0140, RREM-0141

### Related Invariants
- CI-03

---

## REL-REP-082

### Title
External Reference Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Repository integrity **MUST NOT** depend upon the continued availability of externally referenced resources.

### Rationale
Repository validity is independent of external systems.

### Source
REM-02 — RREM-0142, RREM-0144

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-083

### Title
External Reference Metadata

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
External references **MUST** remain explicitly identifiable, and associated metadata **MUST** be preserved during Repository export and migration. Integrity metadata **MAY** be included where supported.

### Rationale
Preserves portability while enabling optional verification.

### Source
REM-02 — RREM-0143, RREM-0145, RREM-0146, RREM-0147

### Related Invariants
- CI-03
- CI-08

---

# Editorial Review Notes

This part defines the interoperability boundary of the Repository subsystem. Schemas provide common semantic structure, Derived Records preserve the authority of canonical records while supporting computed representations, and External References enable integration with resources beyond the Repository without compromising portability, integrity or constitutional ownership.

<!-- Part 7 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Repository export and migration.

It establishes the constitutional guarantee that a Relay Repository can be exported and migrated between compliant implementations without loss of identity, integrity, history, provenance or interoperability.

---

# 2. Scope

This part defines normative requirements governing:

- Repository export
- Export format
- Repository migration
- Cross-provider portability
- Migration integrity
- Interoperability

---

# 3. Requirements

## REL-REP-084

### Title
Repository Export

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Relay Repository **MUST** support protocol-defined export.

### Rationale
Export is a constitutional portability guarantee.

### Source
REM-02 — RREM-0148

### Related Invariants
- CI-03

---

## REL-REP-085

### Title
Complete Repository Export

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository export **MUST** preserve the complete canonical Repository state, including Repository history, provenance, identifiers, schemas and associated metadata.

### Rationale
Ensures complete semantic portability.

### Source
REM-02 — RREM-0149 to RREM-0153

### Related Invariants
- CI-08

---

## REL-REP-086

### Title
Verifiable Repository Export

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
An exported Repository **MUST** remain independently verifiable and **MUST NOT** require provider-specific information beyond protocol-defined requirements.

### Rationale
Prevents vendor lock-in while preserving trust.

### Source
REM-02 — RREM-0154 to RREM-0156

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-087

### Title
Repository Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Migration between compliant implementations **MUST** preserve Repository identity.

### Rationale
Migration transfers operational responsibility rather than constitutional identity.

### Source
REM-02 — RREM-0157

### Related Invariants
- CI-03

---

## REL-REP-088

### Title
Migration Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository migration **MUST** preserve Repository history, integrity, provenance, schemas, Blob references, external reference metadata, Commit history and the Repository Head.

### Rationale
Migration preserves the Repository as a complete protocol object.

### Source
REM-02 — RREM-0158 to RREM-0166

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-089

### Title
Verifiable Migration

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository migration **MUST** remain independently verifiable and implementation-neutral.

### Rationale
Ensures objective verification across providers.

### Source
REM-02 — RREM-0167, RREM-0168

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-090

### Title
Cross-provider Interoperability

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Compliant implementations **MUST** accept valid protocol exports produced by other compliant implementations.

### Rationale
Supports ecosystem interoperability.

### Source
REM-02 — RREM-0169

### Related Invariants
- CI-03

---

## REL-REP-091

### Title
Migration Safety

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Migration failure **MUST NOT** invalidate or corrupt the source Repository.

### Rationale
Migration must be non-destructive.

### Source
REM-02 — RREM-0170

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part defines one of the Relay Protocol's most important constitutional guarantees: Repository portability. Export and migration are protocol capabilities rather than implementation conveniences, ensuring that a Repository remains the same constitutional object regardless of where it is hosted or which compliant implementation manages it.

<!-- Part 8 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Repository forks, caching, indexes and availability.

It establishes how compliant implementations may improve collaboration, performance and resilience while preserving the constitutional authority of the canonical Repository.

---

# 2. Scope

This part defines normative requirements governing:

- Repository Forks
- Repository Caching
- Repository Indexes
- Repository Availability
- Canonical Repository Authority

---

# 3. Requirements

## REL-REP-092

### Title
Repository Forks

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Repository **MAY** be forked in accordance with protocol-defined rules.

### Rationale

Forks support collaboration and experimentation without altering the original Repository.

### Source

REM-02 — RREM-0171

### Related Invariants

- CI-03

---

## REL-REP-093

### Title
Fork Independence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Fork **MUST** remain a distinct Repository possessing its own Repository identity while preserving provenance linking it to the originating Repository.

### Rationale

Forks create independent repositories rather than alternate views of the original.

### Source

REM-02 — RREM-0172 to RREM-0176

### Related Invariants

- CI-01
- CI-08

---

## REL-REP-094

### Title
Repository Caching

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Implementations **MAY** maintain Repository caches to improve performance.

### Rationale

Caching is an implementation optimisation rather than a protocol requirement.

### Source

REM-02 — RREM-0177

### Related Invariants

- CI-03

---

## REL-REP-095

### Title
Cache Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Cached Repository data **MUST NOT** replace or redefine the canonical Repository.

### Rationale

Caches are operational conveniences and never become protocol authority.

### Source

REM-02 — RREM-0178 to RREM-0180

### Related Invariants

- CI-08

---

## REL-REP-096

### Title
Repository Indexes

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Implementations **MAY** maintain Repository indexes to improve discovery and query performance.

### Rationale

Indexes support efficient access without affecting protocol semantics.

### Source

REM-02 — RREM-0181

### Related Invariants

- CI-03

---

## REL-REP-097

### Title
Index Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Repository indexes **MUST** be derived from canonical Repository content, remain regenerable from canonical Repository state, and **MUST NOT** redefine or replace canonical Repository authority.

### Rationale

Indexes are derived operational structures.

### Source

REM-02 — RREM-0182 to RREM-0185

### Related Invariants

- CI-08

---

## REL-REP-098

### Title
Repository Availability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository availability **MUST** remain independent of any individual provider instance or service endpoint.

### Rationale

Repository existence is independent of operational infrastructure.

### Source

REM-02 — RREM-0186

### Related Invariants

- CI-03

---

## REL-REP-099

### Title
Availability Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Temporary service interruption **MUST NOT** alter Repository identity, integrity or history, and loss of an individual endpoint **MUST NOT** constitute Repository loss.

### Rationale

Operational outages do not affect constitutional Repository existence.

### Source

REM-02 — RREM-0187 to RREM-0191

### Related Invariants

- CI-03
- CI-08

---

## REL-REP-100

### Title
Availability Neutrality

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Availability mechanisms **MUST** remain transparent to Repository semantics and preserve canonical Repository behaviour.

### Rationale

Availability strategies must not change protocol behaviour.

### Source

REM-02 — RREM-0192

### Related Invariants

- CI-03

---

# Editorial Review Notes

This part reinforces the constitutional distinction between the canonical Repository and auxiliary operational structures. Forks, caches, indexes and availability mechanisms improve collaboration, resilience and performance, but they never redefine Repository identity, authority or integrity. The Repository remains the sole canonical source of protocol truth.

<!-- Part 9 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing repository deletion, provider obligations, application obligations and the minimum required repository operations.

It establishes the responsibilities of protocol participants while preserving the constitutional distinction between protocol rules and implementation choices.

---

# 2. Scope

This part defines normative requirements governing:

- Repository deletion
- Provider obligations
- Application obligations
- Required repository operations
- Compliance responsibilities

---

# 3. Requirements

## REL-REP-101

### Title
Repository Deletion

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository deletion **MUST** follow protocol-defined lifecycle rules and **MUST** preserve historical auditability where required by the protocol.

### Rationale
Deletion is a protocol-governed lifecycle event rather than an implementation detail.

### Source
REM-02 — RREM-0193, RREM-0194

### Related Invariants
- CI-08

---

## REL-REP-102

### Title
Deletion Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository deletion **MUST** remain distinguishable from temporary unavailability, and **MUST NOT** alter historical Repository identifiers.

### Rationale
Deletion, outage and identity are separate protocol concepts.

### Source
REM-02 — RREM-0195, RREM-0196

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-103

### Title
Deletion Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository deletion events **MUST** remain independently verifiable.

### Rationale
Lifecycle transitions require objective verification.

### Source
REM-02 — RREM-0197

### Related Invariants
- CI-08

---

## REL-REP-104

### Title
Provider Obligations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Compliant Repository Providers **MUST** implement all mandatory Repository behaviours defined by the Relay Protocol.

### Rationale
Defines the baseline responsibilities of Repository Providers.

### Source
REM-02 — RREM-0198

### Related Invariants
- CI-03

---

## REL-REP-105

### Title
Repository Preservation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository Providers **MUST** preserve canonical Repository content, Repository integrity, protocol-defined export capability and protocol-defined migration capability.

### Rationale
Hosting responsibilities include preservation of protocol guarantees.

### Source
REM-02 — RREM-0199 to RREM-0202

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-106

### Title
Provider Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Hosting a Repository **MUST NOT** confer ownership of that Repository upon the hosting Provider.

### Rationale
Hosting and ownership are constitutionally distinct.

### Source
REM-02 — RREM-0203

### Related Invariants
- CI-03

---

## REL-REP-107

### Title
Application Obligations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Applications interacting with Repositories **MUST** use protocol-defined behaviours and preserve protocol identifiers.

### Rationale
Applications participate in, but do not redefine, protocol behaviour.

### Source
REM-02 — RREM-0204, RREM-0206

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-108

### Title
Canonical Repository Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Applications **MUST** distinguish canonical Repository content from locally derived data and **MUST NOT** redefine Repository semantics.

### Rationale
Preserves canonical protocol authority.

### Source
REM-02 — RREM-0205, RREM-0207

### Related Invariants
- CI-08

---

## REL-REP-109

### Title
Required Repository Operations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Every compliant Repository implementation **MUST** support the protocol-defined minimum operation set.

### Rationale
Defines the baseline operational capability for conformance.

### Source
REM-02 — RREM-0208, RREM-0209

### Related Invariants
- CI-03

---

## REL-REP-110

### Title
Operation Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Required Repository operations **MUST** preserve Repository integrity, Repository history and Repository portability.

### Rationale
Operational behaviour must preserve constitutional guarantees.

### Source
REM-02 — RREM-0210, RREM-0212

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-111

### Title
Operation Neutrality

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Required Repository operations **MUST** remain provider-neutral and support future protocol evolution.

### Rationale
Ensures long-term interoperability and extensibility.

### Source
REM-02 — RREM-0213, RREM-0214

### Related Invariants
- CI-03

---

# Editorial Review Notes

This part defines the operational responsibilities of the Repository subsystem. It separates constitutional protocol guarantees from provider and application responsibilities, ensuring that hosting, software and operational choices cannot undermine repository ownership, portability, integrity or long-term interoperability.

<!-- Part 10 -->
**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the constitutional invariants governing every Relay Repository, the criteria for Repository compliance, and the final consolidation of the Repository Requirements Catalogue.

It establishes the immutable properties that every compliant implementation must preserve and concludes the Repository subsystem as a complete normative specification.

---

# 2. Scope

This part defines normative requirements governing:

- Repository invariants
- Repository compliance
- Mandatory versus optional behaviour
- Editorial consolidation

---

# 3. Requirements

## REL-REP-112

### Title
Repository Constitutional Invariants

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every compliant Repository implementation **MUST** preserve the constitutional invariants defined by the Relay Protocol.

### Rationale

Constitutional invariants define the immutable characteristics of every Relay Repository.

### Source

REM-02 — RREM-0215

### Related Invariants

- CI-01
- CI-03
- CI-08

---

## REL-REP-113

### Title
Repository Identity Independence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository identity **MUST** remain independent of providers, applications and implementation technologies.

### Rationale

Repository identity is a protocol concept rather than an implementation artifact.

### Source

REM-02 — RREM-0216

### Related Invariants

- CI-01
- CI-03

---

## REL-REP-114

### Title
Immutable Repository History

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository History **MUST** remain immutable once valid Commits have been accepted.

### Rationale

Immutable history is essential for long-term auditability and trust.

### Source

REM-02 — RREM-0217

### Related Invariants

- CI-08

---

## REL-REP-115

### Title
Independent Repository Verification

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository integrity and authenticity **MUST** remain independently verifiable.

### Rationale

Trust in the Repository must not depend upon any individual implementation or provider.

### Source

REM-02 — RREM-0218

### Related Invariants

- CI-08

---

## REL-REP-116

### Title
Repository Constitutional Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository authority **MUST** derive from the Relay Protocol rather than implementation-specific behaviour.

### Rationale

Protocol rules are authoritative; implementations realise them.

### Source

REM-02 — RREM-0219

### Related Invariants

- CI-02

---

## REL-REP-117

### Title
Repository Compliance

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement

An implementation claiming Repository compliance **MUST** satisfy every mandatory Repository requirement defined by this catalogue.

### Rationale

Compliance requires complete implementation of mandatory behaviour.

### Source

REM-02 — RREM-0220

### Related Invariants

- CI-03

---

## REL-REP-118

### Title
Behaviour-based Compliance

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement

Repository compliance **MUST** be assessed according to observable protocol behaviour rather than implementation architecture.

### Rationale

Preserves technology neutrality.

### Source

REM-02 — RREM-0221, RREM-0222

### Related Invariants

- CI-03

---

## REL-REP-119

### Title
Neutral Compliance Assessment

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement

Compliance assessment **MUST** preserve provider neutrality and clearly distinguish mandatory requirements from optional protocol features.

### Rationale

Ensures fair and interoperable conformance testing.

### Source

REM-02 — RREM-0223, RREM-0224

### Related Invariants

- CI-03

---

# 4. Final Consolidation

This document completes the Repository Requirements Catalogue.

Together, Parts 1–10 define the complete normative Repository specification for the Relay Protocol, covering:

- Repository foundations
- Records and addressing
- Lifecycle and immutable history
- Commits and integrity
- Provenance and classification
- Schemas and interoperability
- Export and migration
- Forks, caching, indexes and availability
- Operational responsibilities
- Constitutional invariants and compliance

Future revisions SHALL amend this catalogue through the Relay editorial programme while preserving constitutional continuity and full traceability to the underlying Repository Model.

---

# Editorial Review Notes

This part concludes the Repository subsystem by separating immutable constitutional principles from implementation-specific behaviour and formalising the criteria for Repository conformance. With this document, the Repository Requirements Catalogue is complete and ready for subsystem-level editorial review (EA-05R-03) and assembly into the canonical **EA-05-02 — Repository Requirements Catalogue v1.0**.

---

# Publication Note

This canonical document is assembled from the reviewed Repository Requirements Catalogue parts. Future amendments should be made to the source part documents and reassembled through the Relay editorial process to preserve traceability and editorial integrity.
