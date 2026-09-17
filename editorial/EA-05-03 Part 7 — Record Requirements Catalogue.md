# EA-05-03 — Record Requirements Catalogue

## Part 7 — Subject, Authority and Submission Role Separation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the distinct roles of the record subject, authorising identity and submitting application or agent, including when those roles may coincide or refer to different entities and how a record should represent them without conflation.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 10 and REM-03 requirements `REM-03-092` through `REM-03-098`.

It defines normative requirements governing:

- conceptual distinction among the subject, authorising identity and submitter;
- permission for those roles to coincide where factually appropriate;
- support for records in which the roles refer to different entities;
- the meaning of each role; and
- independent representation of the roles without conflation.

Source Section 11 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-095` through `REM-03-097` are consolidated into one role-semantics requirement because the source defines the three roles together as part of one conceptual model. Each definition remains explicit and individually traceable.

The prose and JSON examples in Section 10 are illustrative. They do not establish mandatory physical field names, identity values, schema content or final wire syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-054

### Title

Record Role Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** distinguish the record subject, authorising identity and submitting application or agent as separate concepts.

### Rationale

Separating the three roles preserves the distinction between who or what a record concerns, whose repository authority accepted it and which application or agent transmitted the operation.

### Source

- REM-03-092
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-055

### Title

Coinciding Record Roles

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The record subject, authorising identity and submitter **MAY** refer to the same entity where factually appropriate.

### Rationale

The model must accommodate direct interactions in which one entity fulfils multiple roles without erasing the distinct meaning of each role.

### Source

- REM-03-093
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-056

### Title

Differing Record Roles

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support records in which the subject, authorising identity and submitter refer to different entities.

### Rationale

Supporting different entities in these roles allows the model to represent records concerning another identity or object, records accepted under a particular identity's repository authority and operations transmitted by an application or agent.

### Source

- REM-03-094
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06
- CI-12

---

## REL-REC-057

### Title

Record Role Semantics

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Record **MUST** identify, through fields or equivalent representations:

- as its subject, the identity or object that the record concerns;
- as its authorising identity, the identity under whose repository authority the record was accepted; and
- as its submitter, the application or agent that transmitted the record operation.

### Rationale

Explicit role semantics allow implementations to determine subject matter, repository authority and submission provenance without treating any one role as a substitute for another.

### Source

- REM-03-095
- REM-03-096
- REM-03-097
- `design-notes/03-record-model.md`, Sections 10.1–10.3

### Related Invariants

- CI-02
- CI-06
- CI-08
- AI-01

---

## REL-REC-058

### Title

Independent Record Role Representation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A Relay Record **SHOULD** be capable of representing its subject, authorising identity and submitter independently without conflating one role with another.

### Rationale

Independent representation preserves accurate subject, authority and submission provenance even when the same entity happens to fulfil more than one role. The source frames this capability as a recommendation rather than an unconditional requirement.

### Source

- REM-03-098
- `design-notes/03-record-model.md`, Section 10.3

### Related Invariants

- CI-02
- CI-06
- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-092` | Direct | `REL-REC-054` |
| `REM-03-093` | Direct | `REL-REC-055` |
| `REM-03-094` | Direct | `REL-REC-056` |
| `REM-03-095` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-096` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-097` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-098` | Direct | `REL-REC-058` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-095` through `REM-03-097` retains all three role definitions in the Statement, Source list and coverage table for `REL-REC-057`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 10 of `design-notes/03-record-model.md`.
- Source Sections 11–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-092` through `REM-03-098`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-053`.
- First identifier in this part: `REL-REC-054`.
- Final identifier in this part: `REL-REC-058`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers are continuous and unique across Parts 1–7.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-095` through `REM-03-097` retain individual traceability through the Source list and coverage table for `REL-REC-057`.

## Role-separation verification

- The subject, authorising identity and submitter remain conceptually distinct.
- The roles may refer to the same entity where factually appropriate without losing their distinct meanings.
- The model supports records in which the three roles refer to different entities.
- Submission is not treated as authorisation, ownership or repository authority.

## Role-semantics verification

- The subject remains the identity or object the record concerns.
- The authorising identity remains the identity under whose repository authority the record was accepted.
- The submitter remains the application or agent that transmitted the operation.
- Fields or equivalent representations are permitted; no particular physical layout is required.

## Independent-representation verification

- Independent role representation retains the source-level `SHOULD` strength.
- The recommendation is not strengthened to `MUST` by the separate mandatory conceptual-distinction rule.
- Coinciding role values do not imply conflated role semantics.

## Illustrative-example verification

- Section 10 prose and JSON examples generate no separate normative catalogue requirements.
- `subject`, `authorisedBy` and `submittedBy` are not made mandatory physical field names.
- The example identities, employment credential, portfolio application and JSON object are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No role field, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 7 defines the distinction, permitted coincidence, possible separation, semantics and independent representation of the subject, authorising identity and submitter roles. It generates `REL-REC-054` through `REL-REC-058` from `REM-03-092` through `REM-03-098`.

The next catalogue part should begin with source Section 11 and `REM-03-099`.
