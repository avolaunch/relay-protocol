# EA-05-02 — Repository Requirements Catalogue
## Part 9 — Repository Deletion, Provider Obligations, Application Obligations & Required Operations

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing repository deletion, provider obligations, application obligations and the minimum required repository operations.

It establishes the responsibilities of protocol participants while preserving the constitutional distinction between protocol rules and implementation choices.

---

# 2. Scope

This part defines normative requirements governing:

- Repository deletion
- Provider obligations
- Application obligations
- Required repository operations
- Compliance responsibilities

---

# 3. Requirements

## REL-REP-101

### Title
Repository Deletion

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Repository deletion **MUST** follow protocol-defined lifecycle rules and **MUST** preserve historical auditability where required by the protocol.

### Rationale
Deletion is a protocol-governed lifecycle event rather than an implementation detail.

### Source
REM-02 — RREM-0193, RREM-0194

### Related Invariants
- CI-08

---

## REL-REP-102

### Title
Deletion Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository deletion **MUST** remain distinguishable from temporary unavailability, and **MUST NOT** alter historical Repository identifiers.

### Rationale
Deletion, outage and identity are separate protocol concepts.

### Source
REM-02 — RREM-0195, RREM-0196

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-103

### Title
Deletion Verification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository deletion events **MUST** remain independently verifiable.

### Rationale
Lifecycle transitions require objective verification.

### Source
REM-02 — RREM-0197

### Related Invariants
- CI-08

---

## REL-REP-104

### Title
Provider Obligations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Compliant Repository Providers **MUST** implement all mandatory Repository behaviours defined by the Relay Protocol.

### Rationale
Defines the baseline responsibilities of Repository Providers.

### Source
REM-02 — RREM-0198

### Related Invariants
- CI-03

---

## REL-REP-105

### Title
Repository Preservation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Repository Providers **MUST** preserve canonical Repository content, Repository integrity, protocol-defined export capability and protocol-defined migration capability.

### Rationale
Hosting responsibilities include preservation of protocol guarantees.

### Source
REM-02 — RREM-0199 to RREM-0202

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-106

### Title
Provider Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Hosting a Repository **MUST NOT** confer ownership of that Repository upon the hosting Provider.

### Rationale
Hosting and ownership are constitutionally distinct.

### Source
REM-02 — RREM-0203

### Related Invariants
- CI-03

---

## REL-REP-107

### Title
Application Obligations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Applications interacting with Repositories **MUST** use protocol-defined behaviours and preserve protocol identifiers.

### Rationale
Applications participate in, but do not redefine, protocol behaviour.

### Source
REM-02 — RREM-0204, RREM-0206

### Related Invariants
- CI-03
- CI-05

---

## REL-REP-108

### Title
Canonical Repository Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Applications **MUST** distinguish canonical Repository content from locally derived data and **MUST NOT** redefine Repository semantics.

### Rationale
Preserves canonical protocol authority.

### Source
REM-02 — RREM-0205, RREM-0207

### Related Invariants
- CI-08

---

## REL-REP-109

### Title
Required Repository Operations

**Level:** Compliance

**Normative Keyword:** **MUST**

### Statement
Every compliant Repository implementation **MUST** support the protocol-defined minimum operation set.

### Rationale
Defines the baseline operational capability for conformance.

### Source
REM-02 — RREM-0208, RREM-0209

### Related Invariants
- CI-03

---

## REL-REP-110

### Title
Operation Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Required Repository operations **MUST** preserve Repository integrity, Repository history and Repository portability.

### Rationale
Operational behaviour must preserve constitutional guarantees.

### Source
REM-02 — RREM-0210, RREM-0212

### Related Invariants
- CI-03
- CI-08

---

## REL-REP-111

### Title
Operation Neutrality

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Required Repository operations **MUST** remain provider-neutral and support future protocol evolution.

### Rationale
Ensures long-term interoperability and extensibility.

### Source
REM-02 — RREM-0213, RREM-0214

### Related Invariants
- CI-03

---

# Editorial Review Notes

This part defines the operational responsibilities of the Repository subsystem. It separates constitutional protocol guarantees from provider and application responsibilities, ensuring that hosting, software and operational choices cannot undermine repository ownership, portability, integrity or long-term interoperability.
