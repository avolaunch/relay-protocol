# EA-05-03 — Record Requirements Catalogue

## Part 6 — Singleton and Repeatable Record Cardinality

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines singleton and repeatable collection cardinality, the active-record constraint that gives singleton its meaning, the multiplicity permitted for repeatable records and the preferred versioning behaviour for singleton updates.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 9 and REM-03 requirements `REM-03-088` through `REM-03-091`.

It defines normative requirements governing:

- schema definition of a collection as singleton or repeatable;
- the maximum number of active logical records for a singleton schema or role;
- the permission for multiple logical records in a repeatable schema or collection; and
- the preferred treatment of singleton updates as new versions of the same logical record.

Source Section 10 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-088` complements rather than duplicates `REL-REC-042`. The earlier requirement mandates that a record schema state whether a record is singleton or repeatable; this part preserves Section 9's permission to define an applicable collection using either model and defines what each model means.

The listed singleton and repeatable examples are illustrative. They do not establish mandatory schema names, collection names, roles or a closed vocabulary and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-050

### Title

Schema-Defined Collection Cardinality

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record schema **MAY** define an applicable collection as singleton or repeatable.

### Rationale

Schema-defined collection cardinality allows the model appropriate to the record type to be selected while the mandatory declaration of singleton or repeatable status remains governed by `REL-REC-042`.

### Source

- REM-03-088
- `design-notes/03-record-model.md`, Section 9

### Related Invariants

- CI-08
- CI-12
- AI-09

---

## REL-REC-051

### Title

Singleton Active-Record Constraint

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

For a singleton schema or role, no more than one active logical record of that schema or role **MAY** exist per repository.

### Rationale

Limiting singleton cardinality to one active logical record prevents competing current records while allowing that logical record to retain historical versions.

### Source

- REM-03-089
- `design-notes/03-record-model.md`, Section 9, Singleton

### Related Invariants

- CI-07
- CI-10
- AI-01

---

## REL-REC-052

### Title

Repeatable Record Multiplicity

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

For a repeatable schema or collection, multiple logical records **MAY** exist in the repository.

### Rationale

Repeatable cardinality permits more than one logical record without implying that other applicable schema or validation rules no longer apply.

### Source

- REM-03-090
- `design-notes/03-record-model.md`, Section 9, Repeatable

### Related Invariants

- CI-07
- CI-12

---

## REL-REC-053

### Title

Preferred Singleton Update Behaviour

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An update to a singleton record **SHOULD** normally create a new version of the same logical record rather than a second competing current logical record.

### Rationale

Versioning the existing singleton preserves its continuing logical identity and its one-current-record semantics. The qualification “normally” retains the source's recommendation rather than creating an unconditional prohibition.

### Source

- REM-03-091
- `design-notes/03-record-model.md`, Section 9

### Related Invariants

- CI-05
- CI-10
- AI-02

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-088` | Direct; complementary to existing schema-declaration requirement | `REL-REC-050`; does not duplicate or weaken `REL-REC-042` |
| `REM-03-089` | Direct | `REL-REC-051` |
| `REM-03-090` | Direct | `REL-REC-052` |
| `REM-03-091` | Direct | `REL-REC-053` |

No REM entry in scope is consolidated into another requirement or excluded from normative catalogue generation. The relationship between `REM-03-088` and `REL-REC-042` is recorded explicitly without replacing either Section 9's collection-level permission or Section 7's mandatory schema-declaration rule.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 9 of `design-notes/03-record-model.md`.
- Source Sections 10–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-088` through `REM-03-091`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-049`.
- First identifier in this part: `REL-REC-050`.
- Final identifier in this part: `REL-REC-053`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–6.

## Traceability verification

- Every REM entry in scope maps directly to one catalogue requirement.
- Every catalogue requirement cites one in-scope REM identifier and the authoritative design-note section or subsection.
- No REM entry in scope is consolidated, excluded or left unaccounted for.

## Cross-part continuity verification

- `REL-REC-042` continues to require a schema to define whether a record is singleton or repeatable.
- `REL-REC-050` preserves the Section 9 permission to define an applicable collection using either model.
- The Section 9 permission does not duplicate, replace or weaken the earlier mandatory schema declaration.

## Cardinality verification

- The singleton constraint applies to active logical records of the applicable schema or role within a repository.
- Historical versions of the same singleton logical record are not treated as competing active logical records.
- Repeatable schemas or collections retain the permission for multiple logical records.
- Repeatable status does not displace other applicable schema or validation rules.

## Singleton-update verification

- The preferred update behaviour retains the source-level `SHOULD` strength.
- The qualification “normally” remains explicit.
- The recommendation favours a new version of the same logical record over a second competing current logical record.
- The recommendation is not converted into an unconditional prohibition.

## Illustrative-example verification

- Singleton and repeatable examples generate no separate normative catalogue requirements.
- Primary profile, Current repository preferences, Primary public contact settings, Posts, Projects, Photographs, Credentials and Relationships are not made mandatory schemas, collections, roles or vocabulary values.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No requirement, exception rule, schema name or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 6 defines collection-cardinality selection, singleton and repeatable semantics and preferred singleton-update behaviour. It generates `REL-REC-050` through `REL-REC-053` from `REM-03-088` through `REM-03-091`.

The next catalogue part should begin with source Section 10 and `REM-03-092`.
