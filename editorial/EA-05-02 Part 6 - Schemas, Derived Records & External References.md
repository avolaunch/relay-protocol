# EA-05-02 — Repository Requirements Catalogue
## Part 6 — Schemas, Derived Records & External References

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
