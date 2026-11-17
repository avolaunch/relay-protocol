# EA-05-03 — Record Requirements Catalogue

## Part 21 — Schema-Defined Record Expiration

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines optional schema-level and record-level expiration, the permitted meanings of expiration and the schema obligation to identify which consequences apply.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 24 and REM-03 requirements `REM-03-268` through `REM-03-274`.

It defines normative requirements governing expiration definition, the four source-defined expiration interpretations and explicit schema selection of applicable consequences.

Source Section 25 and later sections are intentionally deferred to subsequent catalogue parts. No inter-record reference requirement from Section 25 is imported.

`REM-03-270` through `REM-03-273` are consolidated because they are four compatible schema-selectable interpretations of expiration. Each interpretation remains explicit and individually traceable. The illustrative record types and JSON generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-129

### Title

Schema-Defined Expiration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define expiration behaviour and an expiration time for conforming records.

### Rationale

Expiration is optional schema-defined lifecycle behaviour and is not imposed on every schema or record.

### Source

- REM-03-268
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-130

### Title

Record-Defined Expiration Time

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record **MAY** define an expiration time where the applicable schema permits or supports it.

### Rationale

A record-level expiration value is optional and remains governed by the applicable schema rather than establishing independent expiration semantics.

### Source

- REM-03-269
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-131

### Title

Permitted Expiration Interpretations

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define expiration to mean one or more of the following:

- the record is no longer publicly displayed;
- the record is no longer valid as an assertion;
- the record is no longer accessible; or
- the record is eligible for deletion.

### Rationale

The source permits distinct expiration consequences without making any one consequence universal or treating deletion eligibility as completed deletion.

### Source

- REM-03-270
- REM-03-271
- REM-03-272
- REM-03-273
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-132

### Title

Explicit Schema Interpretation of Expiration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema supporting expiration **MUST** specify which semantic consequence or consequences of expiration apply.

### Rationale

Explicit schema semantics prevent applications from inferring public-display, assertion-validity, accessibility or deletion consequences from one another.

### Source

- REM-03-274
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-268` | Direct | `REL-REC-129` |
| `REM-03-269` | Direct | `REL-REC-130` |
| `REM-03-270` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-271` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-272` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-273` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-274` | Direct | `REL-REC-132` |

Every REM entry in scope maps directly or through justified consolidation to a catalogue requirement. No illustrative example generates a catalogue requirement.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 24 of `design-notes/03-record-model.md`.
- Source Sections 25–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-268` through `REM-03-274`.
- No inter-record reference requirement from Section 25 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-128`.
- First identifier in this part: `REL-REC-129`.
- Final identifier in this part: `REL-REC-132`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–21.

## Traceability verification

- Every in-scope normative REM entry is represented directly or through justified consolidation.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- All four expiration interpretations retain individual traceability through the Source list and coverage table for `REL-REC-131`.

## Expiration-definition verification

- Schema-level and record-level expiration retain `MAY` strength.
- No schema or record is universally required to expire.
- A record-level expiration time remains subject to applicable schema support.

## Expiration-semantics verification

- End of public display, assertion invalidity, loss of access and deletion eligibility remain distinct schema-selectable meanings.
- Deletion eligibility is not treated as deletion having occurred.
- A supporting schema must identify the applicable consequence or consequences.
- Temporary announcements, access invitations, credentials, statuses and the illustrative `expiresAt` JSON generate no normative requirements or mandatory vocabulary.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 21 defines optional record expiration and requires schemas that support it to state its applicable semantic consequences.

The next catalogue part should address Section 25.
