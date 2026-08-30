# EA-05-01 — Identity Requirements Catalogue
## Part 5 — Controller & Authority

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Controllers, authority and high-authority operations within Relay Identity.

It is derived from the approved REM-01 and the Controller & Authority sections of the Identity Model.

---

# 2. Scope

This part covers:

- Controller authority
- Multi-controller identities
- Authentication versus authority
- High-authority operations
- Authority separation

---

# 3. Requirements

## REL-ID-043

### Title
Controller Requirement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Every Relay Identity **MUST** have at least one Controller possessing authority over that identity.

### Rationale
Identity authority must always be attributable to a recognised Controller.

### Source
REM-01 — IREM-0021

### Related Invariants
- CI-02

---

## REL-ID-044

### Title
Controller Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Authority to modify a Relay Identity **MUST** derive from a valid Controller.

### Rationale
Authority is an explicit protocol concept rather than an implementation detail.

### Source
REM-01 — IREM-0021

### Related Invariants
- CI-02

---

## REL-ID-045

### Title
Multiple Controllers

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
A Relay Identity **MAY** define multiple Controllers.

### Source
REM-01 — IREM-0022

### Related Invariants
- CI-02

---

## REL-ID-046

### Title
Single-Controller Assumption

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement
Implementations **MUST NOT** assume that every Relay Identity has only one permanent Controller.

### Source
REM-01 — IREM-0022

### Related Invariants
- CI-02

---

## REL-ID-047

### Title
Authentication Separation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** distinguish authentication from identity authority.

### Rationale
Authentication establishes who is interacting; authority determines what protocol actions are permitted.

### Source
REM-01 — IREM-0023

### Related Invariants
- CI-02

---

## REL-ID-048

### Title
Migration Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication alone **MUST NOT** grant authority to migrate a Relay Identity.

### Source
REM-01 — IREM-0024

### Related Invariants
- CI-02

---

## REL-ID-049

### Title
Root Key Rotation Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication alone **MUST NOT** grant authority to rotate root keys.

### Source
REM-01 — IREM-0025

### Related Invariants
- CI-02

---

## REL-ID-050

### Title
Recovery Configuration Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication alone **MUST NOT** grant authority to modify recovery configuration.

### Source
REM-01 — IREM-0026

### Related Invariants
- CI-02

---

## REL-ID-051

### Title
Identity Transfer Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication alone **MUST NOT** grant authority to transfer control of a Relay Identity.

### Source
REM-01 — IREM-0027

### Related Invariants
- CI-02

---

## REL-ID-052

### Title
Repository Deletion Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication alone **MUST NOT** grant authority to delete the associated Repository.

### Source
REM-01 — IREM-0028

### Related Invariants
- CI-02

---

## REL-ID-053

### Title
High-Authority Verification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
High-authority operations **SHOULD** require stronger verification than ordinary authenticated actions.

### Rationale
Operations capable of permanently affecting identity require proportionally stronger assurance.

### Source
REM-01 — IREM-0029

### Related Invariants
- CI-02

---

# Editorial Review Notes

This part formalises one of the constitutional principles of Relay: authentication and authority are distinct concepts. A user may be successfully authenticated without possessing authority to perform high-impact protocol operations. The requirements in this part therefore establish the authority model upon which migration, recovery, delegation and governance are built.
