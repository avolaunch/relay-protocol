# EA-05-01 — Identity Requirements Catalogue
## Part 1 — Identity Foundations (v2)

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the constitutional foundations of Relay Identity.

It establishes the immutable principles upon which all subsequent Identity requirements are based. Every requirement in later parts of the Identity Requirements Catalogue shall be interpreted consistently with these constitutional foundations.

---

# 2. Scope

This part defines normative requirements governing:

- Relay Identity
- Identity persistence
- Identity independence
- Identity continuity
- Constitutional separation between identity and mutable operational attributes

---

# 3. Requirements

## REL-ID-001

### Title
Relay Identity Persistence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
A Relay Identity **MUST** remain the same identity throughout its lifetime unless explicitly replaced through a protocol-defined identity transfer mechanism.

### Rationale
Persistent identity is the constitutional basis for long-term ownership, authority and continuity.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-01
- CI-03

---

## REL-ID-002

### Title
Provider Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a single Relay Provider.

### Rationale
Changing providers must not redefine constitutional identity.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-03

---

## REL-ID-003

### Title
Application Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a single Relay Application.

### Rationale
Applications consume Relay Identity but do not define it.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-03

---

## REL-ID-004

### Title
Username Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a username.

### Rationale
Usernames are mutable presentation identifiers rather than constitutional identity.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-01

---

## REL-ID-005

### Title
Domain Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a domain name.

### Rationale
Domain ownership may change independently of identity ownership.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-03

---

## REL-ID-006

### Title
Device Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a specific device.

### Rationale
Devices are replaceable implementation artefacts and do not constitute identity.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-01

---

## REL-ID-007

### Title
Authentication Independence

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** permanently depend upon a specific authentication mechanism.

### Rationale
Authentication mechanisms may evolve throughout an identity's lifetime without altering the identity itself.

### Source
REM-01 — IREM-0002

### Related Invariants
- CI-01

---

# Editorial Review Notes

This part establishes the constitutional principles that underpin the Identity subsystem. Every subsequent requirement concerning identifiers, handles, documents, controllers, keys, migration, recovery and lifecycle derives from these foundational requirements. These requirements intentionally separate constitutional identity from providers, applications, usernames, domains, devices and authentication methods, ensuring that operational change never redefines the identity itself.
