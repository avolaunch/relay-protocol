# EA-05-01 — Identity Requirements Catalogue
## Part 8 — Recovery

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing recovery of Relay Identities.

It covers recovery authority, recovery events, recovery records and preservation of identity continuity during recovery.

---

# 2. Scope

This part covers:

- Recovery authority
- Recovery events
- Recovery metadata
- Recovery distinctions
- Identity continuity during recovery

---

# 3. Requirements

## REL-ID-079

### Title
Recovery Requirement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
The Relay Protocol **MUST** provide a recovery mechanism capable of restoring authority over an existing Relay Identity.

### Rationale
Recovery is essential to long-term identity persistence.

### Source
REM-01 — IREM-0046

### Related Invariants
- CI-01
- CI-02

---

## REL-ID-080

### Title
Recovery Continuity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Recovery **MUST** restore authority over the existing Relay Identifier rather than creating a replacement identity.

### Rationale
Recovery preserves identity continuity rather than replacing constitutional identity.

### Source
REM-01 — IREM-0047

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-081

### Title
Replacement Identity Prohibition

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A recovery process **MUST NOT** create a new Relay Identity to replace the recovered identity.

### Source
REM-01 — IREM-0047

### Related Invariants
- CI-01

---

## REL-ID-082

### Title
Recovery Event

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Recovery operations **SHOULD** generate a signed or otherwise verifiable recovery event.

### Source
REM-01 — IREM-0048

### Related Invariants
- CI-08

---

## REL-ID-083

### Title
Recovery Metadata

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Recovery events **SHOULD** contain sufficient metadata to support independent verification.

### Rationale
Recovery must be auditable after completion.

### Source
REM-01 — IREM-0048

### Related Invariants
- CI-08

---

## REL-ID-084

### Title
Recovery Classification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** distinguish between authentication recovery, identity-authority recovery and provider-account recovery.

### Source
REM-01 — IREM-0049

### Related Invariants
- CI-02

---

## REL-ID-085

### Title
Authentication Recovery

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication recovery **MUST NOT** be treated as equivalent to identity-authority recovery.

### Source
REM-01 — IREM-0049

### Related Invariants
- CI-02

---

## REL-ID-086

### Title
Provider Account Recovery

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement
Recovery of a provider account **MUST NOT** by itself constitute recovery of the underlying Relay Identity.

### Source
REM-01 — IREM-0049

### Related Invariants
- CI-03

---

## REL-ID-087

### Title
Recovery Auditability

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Recovery operations **SHOULD** leave a verifiable audit trail sufficient to demonstrate authorised restoration of identity control.

### Rationale
Auditable recovery strengthens trust and accountability.

### Source
REM-01 — Derived from IREM-0048 and IREM-0049

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part establishes recovery as a constitutional capability of Relay rather than an implementation convenience. Recovery restores authority over an existing identity, preserves continuity, distinguishes between different recovery contexts, and supports verification through auditable recovery events.
