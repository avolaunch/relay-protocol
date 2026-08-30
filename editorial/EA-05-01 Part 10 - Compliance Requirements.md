# EA-05-01 — Identity Requirements Catalogue
## Part 10 — Compliance Requirements

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements that determine whether an implementation conforms to the Identity requirements of the Relay Protocol.

It is derived from the compliance section of the Identity Model and the approved REM-01.

---

# 2. Scope

This part covers:

- Minimum implementation obligations
- Compliance evaluation
- Traceability to normative requirements
- Treatment of provisional features

---

# 3. Requirements

## REL-ID-101

### Title
Identity Conformance

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
An implementation claiming conformance to the Relay Identity specification **MUST** satisfy all applicable constitutional, architectural and behavioural requirements defined in Parts 1–9.

### Rationale
Conformance is measured against the approved normative catalogue rather than selected features.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-01
- CI-02
- CI-03

---

## REL-ID-102

### Title
Identity Continuity Verification

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
A conforming implementation **MUST** demonstrate preservation of identity continuity across supported identity operations.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-01

---

## REL-ID-103

### Title
Identifier Stability Verification

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
A conforming implementation **MUST** demonstrate that Relay Identifiers remain stable throughout supported lifecycle operations.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-05

---

## REL-ID-104

### Title
Authority Verification

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
A conforming implementation **MUST** demonstrate correct enforcement of Controller authority for protected operations.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-02

---

## REL-ID-105

### Title
Recovery Verification

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
A conforming implementation **MUST** demonstrate recovery of an existing Relay Identity without creating a replacement identity.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-106

### Title
Migration Verification

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
A conforming implementation **MUST** demonstrate provider migration while preserving identity continuity.

### Source
REM-01 — IREM-0069

### Related Invariants
- CI-03

---

## REL-ID-107

### Title
Deferred Features

**Level:** Compliance

**Normative Keyword:** **MAY**

### Statement
Features explicitly identified as provisional for Relay v0.1 **MAY** remain unimplemented without preventing conformance, provided they are clearly identified as unsupported.

### Rationale
Provisional capabilities are intentionally excluded from mandatory v0.1 conformance.

### Source
REM-01 — IREM-0070

### Related Invariants
- CI-01

---

# Editorial Review Notes

The purpose of this part is not to redefine protocol behaviour but to establish the minimum evidence required for an implementation to claim conformance with the Identity specification. It separates mandatory requirements from provisional functionality and provides the bridge between the normative catalogue and the future conformance test suite.
