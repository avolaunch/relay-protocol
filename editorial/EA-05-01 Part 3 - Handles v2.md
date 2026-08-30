# EA-05-01 — Identity Requirements Catalogue
## Part 3 — Handles (v2)

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Handles within the Relay Protocol.

Handles are human-readable identifiers that improve usability and discovery. They are intentionally distinct from the constitutional Relay Identifier and may evolve throughout the lifetime of a Relay Identity without changing the underlying identity.

---

# 2. Scope

This part defines normative requirements governing:

- Handle association
- Handle lifecycle
- Handle resolution
- Handle verification
- Historical continuity

---

# 3. Requirements

## REL-ID-019

### Title
Handle Association

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
A Relay Identity **MAY** be associated with one or more Handles.

### Rationale
Multiple human-readable identifiers may coexist while referring to the same constitutional identity.

### Source
REM-01 — IREM-0010

### Related Invariants
- CI-01

---

## REL-ID-020

### Title
Handle Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Handle **MUST NOT** be treated as the Relay Identity.

### Rationale
Handles support presentation and discovery but do not constitute constitutional identity.

### Source
REM-01 — IREM-0010

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-021

### Title
Handle Renaming

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
A Controller **MAY** rename an existing Handle.

### Source
REM-01 — IREM-0011

### Related Invariants
- CI-01

---

## REL-ID-022

### Title
Handle Addition

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
A Controller **MAY** associate additional Handles with an existing Relay Identity.

### Source
REM-01 — IREM-0011

### Related Invariants
- CI-01

---

## REL-ID-023

### Title
Handle Removal

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
A Controller **MAY** remove an existing Handle from a Relay Identity.

### Source
REM-01 — IREM-0011

### Related Invariants
- CI-01

---

## REL-ID-024

### Title
Handle Migration

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
A Controller **MAY** migrate a Handle in accordance with the protocol rules governing Handle ownership and verification.

### Rationale
Handle mobility supports operational flexibility while preserving identity continuity.

### Source
REM-01 — IREM-0011

### Related Invariants
- CI-01

---

## REL-ID-025

### Title
Identity Continuity During Handle Change

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Changing, adding, removing or migrating a Handle **MUST NOT** create a new Relay Identity.

### Rationale
Handle lifecycle events are independent of constitutional identity.

### Source
REM-01 — IREM-0011

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-026

### Title
Handle Resolution

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
A valid Handle **MUST** resolve to its associated Relay Identifier.

### Source
REM-01 — IREM-0012

### Related Invariants
- CI-05

---

## REL-ID-027

### Title
Identity Document Resolution

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
A valid Handle **MUST** enable compatible implementations to determine the current Identity Document.

### Source
REM-01 — IREM-0012

### Related Invariants
- CI-08

---

## REL-ID-028

### Title
Service Location Resolution

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
A valid Handle **MUST** enable compatible implementations to determine the current service location or Relay Provider.

### Source
REM-01 — IREM-0012

### Related Invariants
- CI-03

---

## REL-ID-029

### Title
Verification States

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
The protocol **SHOULD** distinguish between asserted, verified and formerly verified Handles.

### Rationale
Verification status is a property of the Handle rather than the underlying identity.

### Source
REM-01 — IREM-0013

### Related Invariants
- CI-08

---

## REL-ID-030

### Title
Verification Methods

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
A Handle **MAY** be verified using any protocol-recognised verification method.

### Source
REM-01 — IREM-0013

### Related Invariants
- CI-08

---

## REL-ID-031

### Title
Historical Identity Preservation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A reassigned Handle **MUST NOT** inherit the historical identity of a previous holder.

### Rationale
Historical continuity belongs to the Relay Identifier rather than reusable Handles.

### Source
REM-01 — IREM-0014

### Related Invariants
- CI-10

---

## REL-ID-032

### Title
Historical Record Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Historical records associated with a reassigned Handle **MUST** remain linked to the permanent Relay Identifier of the original identity.

### Source
REM-01 — IREM-0014

### Related Invariants
- CI-10

---

# Editorial Review Notes

This part establishes Handles as mutable, human-readable identifiers that improve usability without redefining constitutional identity. Handle creation, renaming, migration, verification and reassignment are all designed to preserve identity continuity while allowing operational flexibility.
