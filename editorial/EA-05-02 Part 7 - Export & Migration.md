# EA-05-02 — Repository Requirements Catalogue
## Part 7 — Export & Migration

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
