# EA-05-03 — Record Requirements Catalogue

## Part 5 — Core Record Categories and Schema Diversity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the recommended broad categories used to distinguish the principal semantic roles of Relay Records and permits records in different categories to share common fields while using different schemas.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 8 and REM-03 requirements `REM-03-079` through `REM-03-087`.

It defines normative requirements governing:

- the recommended distinction of broad record categories;
- the meanings of Entity, Activity, Relationship, Authority, Assertion and Tombstone Records; and
- optional sharing of common fields across categories that use different schemas.

Source Section 9 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-079` through `REM-03-085` are consolidated because the source introduces one recommended broad-category model and then defines the six categories it contains. `REM-03-086` and `REM-03-087` are consolidated because they express the two compatible permissions contained in one source sentence. Every category meaning and both schema-diversity permissions remain explicit and individually traceable.

The examples listed beneath the category definitions illustrate possible records or actions. They do not define mandatory category members, schema names, operations or a closed vocabulary and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-048

### Title

Broad Record Category Distinction

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** distinguish broad record categories sufficient to describe the principal semantic role of a record, including support for:

- Entity Records, which describe a persistent entity or object;
- Activity Records, which describe an action or event;
- Relationship Records, which describe a directed or mutual relationship between identities or records;
- Authority Records, which describe permission or control;
- Assertion Records, which describe a claim; and
- Tombstone Records, which record the deletion or retirement of another record without retaining its full active content.

### Rationale

Broad semantic categories provide a common way to distinguish the principal roles of records while allowing specific schemas to define their detailed structure and behaviour. The categories are recommendations for Relay v0.1 rather than unconditional validity requirements or a closed schema vocabulary.

### Source

- REM-03-079
- REM-03-080
- REM-03-081
- REM-03-082
- REM-03-083
- REM-03-084
- REM-03-085
- `design-notes/03-record-model.md`, Section 8

### Related Invariants

- CI-09
- CI-12

---

## REL-REC-049

### Title

Shared Fields with Schema Diversity

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Different record categories **MAY** share common fields while using different schemas.

### Rationale

Field reuse can support common semantics across categories without replacing specific schemas with one universal content schema or treating a broad category as a specific record type.

### Source

- REM-03-086
- REM-03-087
- `design-notes/03-record-model.md`, Section 8.6

### Related Invariants

- CI-08
- CI-12

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-079` | Consolidated category-model recommendation | `REL-REC-048` |
| `REM-03-080` | Consolidated category definition | `REL-REC-048` |
| `REM-03-081` | Consolidated category definition | `REL-REC-048` |
| `REM-03-082` | Consolidated category definition | `REL-REC-048` |
| `REM-03-083` | Consolidated category definition | `REL-REC-048` |
| `REM-03-084` | Consolidated category definition | `REL-REC-048` |
| `REM-03-085` | Consolidated category definition | `REL-REC-048` |
| `REM-03-086` | Consolidated schema-diversity permission | `REL-REC-049` |
| `REM-03-087` | Consolidated schema-diversity permission | `REL-REC-049` |

No REM entry in scope is excluded from normative catalogue generation. The illustrative examples beneath the category definitions have no separate REM identifiers and generate no normative catalogue requirements.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 8 of `design-notes/03-record-model.md`.
- Source Sections 9–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-079` through `REM-03-087`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-047`.
- First identifier in this part: `REL-REC-048`.
- Final identifier in this part: `REL-REC-049`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers are continuous and unique across Parts 1–5.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites its in-scope REM identifiers and the authoritative design-note section or subsection.
- `REM-03-079` through `REM-03-085` retain individual traceability through the Source list and coverage table for `REL-REC-048`.
- `REM-03-086` and `REM-03-087` retain individual traceability through the Source list and coverage table for `REL-REC-049`.

## Category-model verification

- The broad category model retains the source-level `SHOULD` strength.
- Entity, Activity, Relationship, Authority, Assertion and Tombstone Record meanings remain explicit.
- The six categories are not represented as an exhaustive, mutually exclusive or final schema vocabulary.
- A broad semantic category is not treated as a substitute for a specific record schema.

## Illustrative-example verification

- Category examples generate no separate normative catalogue requirements.
- Profiles, projects, publications, organisations, media items, publish, react, follow, endorse, revoke, announce and the other example terms are not made mandatory category members, schema names or operations.
- No final field name, category identifier, schema identifier or serialisation syntax is inferred from an example.

## Schema-diversity verification

- Different categories remain permitted to share common fields.
- Different categories remain permitted to use different schemas even where fields are shared.
- No universal content schema is required.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- Consolidation does not remove any category meaning or schema-diversity permission.
- No requirement, qualification or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 5 defines the recommended broad Record categories and permits shared fields alongside schema diversity. It generates `REL-REC-048` through `REL-REC-049` from `REM-03-079` through `REM-03-087`.

The next catalogue part should begin with source Section 9 and `REM-03-088`.
