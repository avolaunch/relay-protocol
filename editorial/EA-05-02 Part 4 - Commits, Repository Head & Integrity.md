# EA-05-02 — Repository Requirements Catalogue
## Part 4 — Commits, Repository Head & Integrity

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
