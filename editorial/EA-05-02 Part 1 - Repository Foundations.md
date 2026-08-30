# EA-05-02 — Repository Requirements Catalogue

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