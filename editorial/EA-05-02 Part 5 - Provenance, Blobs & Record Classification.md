# EA-05-02 — Repository Requirements Catalogue
## Part 5 — Provenance, Blobs & Record Classification

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
