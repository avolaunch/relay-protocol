# EA-05-01 — Identity Requirements Catalogue
## Part 4 — Identity Documents

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing the Relay Identity Document.

It is derived from the approved REM-01 and the Identity Model sections relating to the Identity Document, versioning, authorisation, verification, discovery and history.

---

# 2. Scope

This part covers:

- Identity Document
- Document versioning
- Authorisation
- Verification
- Discovery
- Historical continuity

---

# 3. Requirements

## REL-ID-033

### Title
Identity Document Existence

### Level
Constitutional

### Normative Keyword
**MUST**

### Statement
Every Relay Identity **MUST** have an Identity Document representing its current operational state.

### Rationale
The Identity Document is the canonical protocol representation of an identity.

### Source
REM-01 — IREM-0015

### Related Invariants
- CI-08

---

## REL-ID-034

### Title
Identity Document Versioning

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Every material change to an Identity Document **MUST** create a new document version.

### Rationale
Material changes require a verifiable history.

### Source
REM-01 — IREM-0016

### Related Invariants
- CI-08

---

## REL-ID-035

### Title
Document Authorisation

### Level
Constitutional

### Normative Keyword
**MUST**

### Statement
Every new Identity Document version **MUST** be authorised by a currently valid authority.

### Rationale
Identity state changes must be attributable to recognised authority.

### Source
REM-01 — IREM-0017

### Related Invariants
- CI-02
- CI-08

---

## REL-ID-036

### Title
Ownership Verification

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Implementations **MUST** verify that an Identity Document belongs to the stated Relay Identifier.

### Source
REM-01 — IREM-0018

### Related Invariants
- CI-08

---

## REL-ID-037

### Title
Integrity Verification

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Implementations **MUST** verify that an Identity Document has not been altered.

### Source
REM-01 — IREM-0018

### Related Invariants
- CI-08

---

## REL-ID-038

### Title
Authority Verification

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Implementations **MUST** verify that the signer of an Identity Document possessed valid authority at the time of signing.

### Source
REM-01 — IREM-0018

### Related Invariants
- CI-02
- CI-08

---

## REL-ID-039

### Title
Document Succession

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Implementations **MUST** verify that an Identity Document correctly supersedes the previous valid version.

### Source
REM-01 — IREM-0018

### Related Invariants
- CI-08

---

## REL-ID-040

### Title
Discovery Support

### Level
Behavioural

### Normative Keyword
**MUST**

### Statement
Implementations **MUST** provide a defined mechanism for discovering the current Identity Document.

### Source
REM-01 — IREM-0019

### Related Invariants
- CI-03
- CI-08

---

## REL-ID-041

### Title
Provider-Independent Discovery

### Level
Architectural

### Normative Keyword
**MUST NOT**

### Statement
Identity Document discovery **MUST NOT** permanently depend upon the current Relay Provider.

### Source
REM-01 — IREM-0019

### Related Invariants
- CI-03

---

## REL-ID-042

### Title
Historical Verification

### Level
Architectural

### Normative Keyword
**SHOULD**

### Statement
The protocol **SHOULD** retain sufficient document history to enable verification of authorised Identity Document updates.

### Rationale
Historical continuity strengthens auditability and trust.

### Source
REM-01 — IREM-0020

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part establishes the Identity Document as the authoritative representation of a Relay Identity's current operational state while ensuring every material change is authorised, versioned and independently verifiable. Together these requirements provide the basis for future migration, recovery and conformance behaviour.
