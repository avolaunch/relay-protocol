# EA-05-01 — Identity Requirements Catalogue
## Part 2 — Relay Identifier (v2)

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing the Relay Identifier.

The Relay Identifier is the permanent protocol identifier associated with a Relay Identity. It provides stable identification throughout the identity lifecycle irrespective of changes to providers, applications, handles, authentication mechanisms or hosting.

---

# 2. Scope

This part defines normative requirements governing:

- Relay Identifier assignment
- Identifier permanence
- Identifier uniqueness
- Independence from operational changes
- Provider-neutral identifiers

---

# 3. Requirements

## REL-ID-008

### Title
Relay Identifier Assignment

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Relay Identity **MUST** possess exactly one permanent Relay Identifier.

### Rationale
A stable protocol identifier is required to preserve constitutional identity.

### Source
REM-01 — IREM-0005

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-009

### Title
Identifier Permanence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
A Relay Identifier **MUST** remain unchanged throughout the lifetime of its associated Relay Identity.

### Rationale
The identifier represents constitutional identity rather than mutable operational state.

### Source
REM-01 — IREM-0006

### Related Invariants
- CI-01
- CI-05

---

## REL-ID-010

### Title
Username Changes

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Changing a username **MUST NOT** alter the associated Relay Identifier.

### Rationale
Usernames are presentation-layer identifiers and are not constitutional identity.

### Source
REM-01 — IREM-0006

### Related Invariants
- CI-05

---

## REL-ID-011

### Title
Domain Changes

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Changing a domain name **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0006

### Related Invariants
- CI-05

---

## REL-ID-012

### Title
Provider Changes

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Changing a Relay Provider **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0006, IREM-0009

### Related Invariants
- CI-03
- CI-05

---

## REL-ID-013

### Title
Device Replacement

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Replacing a device **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0006

### Related Invariants
- CI-05

---

## REL-ID-014

### Title
Cryptographic Key Rotation

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Rotating cryptographic keys **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0006, IREM-0038

### Related Invariants
- CI-05

---

## REL-ID-015

### Title
Application Changes

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Changing Relay Applications **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0006

### Related Invariants
- CI-05

---

## REL-ID-016

### Title
Identifier Uniqueness

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Two independently created Relay Identities **MUST NOT** share the same Relay Identifier.

### Rationale
Each Relay Identifier uniquely identifies one constitutional identity.

### Source
REM-01 — IREM-0007

### Related Invariants
- CI-05

---

## REL-ID-017

### Title
Non-semantic Structure

**Level:** Architectural

**Normative Keyword:** **SHOULD NOT**

### Statement
A Relay Identifier **SHOULD NOT** encode descriptive information about the associated identity.

### Rationale
Identifiers exist to identify rather than describe.

### Source
REM-01 — IREM-0008

### Related Invariants
- CI-05

---

## REL-ID-018

### Title
Provider-specific Identifiers

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identifier **MUST NOT** depend upon a provider-specific domain, address or namespace.

### Rationale
Provider independence is a constitutional property of Relay.

### Source
REM-01 — IREM-0009

### Related Invariants
- CI-03
- CI-05

---

# Editorial Review Notes

This part establishes the Relay Identifier as the permanent constitutional identifier for every Relay Identity. All operational changes—including provider migration, handle changes, key rotation, application changes and device replacement—are explicitly separated from identifier continuity. This separation allows implementations to evolve operationally while preserving a stable constitutional identity.
