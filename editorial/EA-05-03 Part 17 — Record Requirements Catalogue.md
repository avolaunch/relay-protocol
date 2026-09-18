# EA-05-03 — Record Requirements Catalogue

## Part 17 — Schema-Defined Immutability and Historical Integrity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines schema-selected record immutability, the explicit lifecycle treatments available to immutable records and the prohibition against concealed rewriting of their historical assertions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 20 and REM-03 requirements `REM-03-235` through `REM-03-244`.

It defines normative requirements governing:

- a schema's permission to define records as immutable after creation;
- revocation, supersession, annotation and legally necessary deletion of immutable records; and
- protection against concealed rewriting of an immutable record's original assertion.

Source Section 21 and later sections are intentionally deferred to subsequent catalogue parts. No deletion or tombstone requirement from Section 21 is imported.

`REM-03-236` through `REM-03-239` derive from the source's illustrative examples of record types that may be immutable. Signed credentials, historical attestations, issued receipts and completed audit events do not establish mandatory, exhaustive or separate immutable-record categories and therefore generate no catalogue requirements.

`REM-03-240` through `REM-03-243` are consolidated because the source applies one permission to four explicit lifecycle treatments for immutable records. Each treatment and the legal-necessity qualification on deletion remain explicit and individually traceable.

---

# 3. Requirements

---

## REL-REC-110

### Title

Schema-Defined Record Immutability

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define conforming records as immutable after creation.

### Rationale

Immutability is an optional schema-defined behaviour rather than a property imposed universally on every Relay Record or schema.

### Source

- REM-03-235
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-08

---

## REL-REC-111

### Title

Explicit Immutable-Record Lifecycle Treatments

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Without rewriting its original immutable content, an immutable record **MAY** be:

- revoked;
- superseded;
- annotated; or
- deleted where legally necessary.

### Rationale

Immutability protects original content from concealed alteration while allowing explicit lifecycle events and legally necessary deletion. The requirement does not prescribe how any treatment is represented or implemented.

### Source

- REM-03-240
- REM-03-241
- REM-03-242
- REM-03-243
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-112

### Title

No Concealed Rewriting of Immutable Records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An immutable record **MUST NOT** be silently rewritten in a manner that presents its original assertion as though it had always contained different content.

### Rationale

Historical integrity requires corrections or lifecycle changes to remain explicit rather than retrospectively replacing the original assertion without disclosure.

### Source

- REM-03-244
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-235` | Direct | `REL-REC-110` |
| `REM-03-236` | Excluded from separate catalogue generation | Illustrative signed-credential example; does not establish a mandatory or separate immutable-record category |
| `REM-03-237` | Excluded from separate catalogue generation | Illustrative historical-attestation example; does not establish a mandatory or separate immutable-record category |
| `REM-03-238` | Excluded from separate catalogue generation | Illustrative issued-receipt example; does not establish a mandatory or separate immutable-record category |
| `REM-03-239` | Excluded from separate catalogue generation | Illustrative completed-audit-event example; does not establish a mandatory or separate immutable-record category |
| `REM-03-240` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-241` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-242` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-243` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-244` | Direct | `REL-REC-112` |

Every REM entry in scope is represented directly, accounted for through justified consolidation or explicitly excluded from separate catalogue generation because its authoritative source content is illustrative.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 20 of `design-notes/03-record-model.md`.
- Source Sections 21–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-235` through `REM-03-244`.
- No Section 21 deletion or tombstone requirement is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-109`.
- First identifier in this part: `REL-REC-110`.
- Final identifier in this part: `REL-REC-112`.
- Total catalogue requirements in this part: 3.
- Catalogue identifiers are continuous and unique across Parts 1–17.

## Traceability verification

- Every normative source rule in scope maps directly or through justified consolidation to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- All four lifecycle treatments retain individual traceability through the Source list and coverage table for `REL-REC-111`.
- All four illustrative record types remain individually accounted for without generating separate catalogue requirements.

## Schema-defined immutability verification

- Schema-defined immutability retains `MAY` strength.
- Immutability is not imposed on every Relay Record or every schema.
- Signed credentials, historical attestations, issued receipts and completed audit events remain illustrative rather than mandatory, exhaustive or closed immutable-record categories.
- No listed example type is required to use immutable lifecycle behaviour.

## Immutable-record lifecycle verification

- Revocation, supersession, annotation and legally necessary deletion remain explicit, optional and independently traceable.
- The deletion permission retains the qualification that deletion is legally necessary.
- Revocation, supersession and annotation preserve the original immutable content.
- No lifecycle treatment mechanism, field name or schema structure is selected or invented.

## Historical-integrity verification

- Concealed rewriting remains prohibited with `MUST NOT` strength.
- The prohibition remains distinct from the permitted explicit lifecycle treatments.
- Immutability is not interpreted as prohibiting revocation, supersession, annotation or legally necessary deletion.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No deletion rule, tombstone rule, terminology, qualification or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 17 establishes schema-defined immutability, permits explicit immutable-record lifecycle treatments and prohibits concealed rewriting of original assertions.

The next catalogue part should address Section 21 and record deletion.
