# EA-05-03 — Record Requirements Catalogue

## Part 32 — Comments and replies

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 35, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 35 and REM-03 entries `REM-03-352` through `REM-03-360`.

Source Section 36 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-353` is explicitly non-normative and does not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-200

### Title

Reply stored in replying identity’s repository

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A reply **SHOULD** normally be represented as a record in the repository of the identity that created the reply.

### Rationale

The source allows exceptional arrangements but establishes the replying identity’s repository as the normal canonical location.

### Source

- REM-03-352
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

None identified.

---

## REL-REC-201

### Title

Indexing and display by target-side services

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The provider or application serving the target record **MAY** index and display a reply stored in another identity’s repository.

### Rationale

Indexing or display does not transfer canonical authority over the reply.

### Source

- REM-03-354
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-03

---

## REL-REC-202

### Title

Reply repository remains canonical source

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The replying identity’s repository **MUST** remain the canonical source of the reply unless an explicitly authorised protocol operation changes that authority.

### Rationale

Copies, indexes and cached renderings are secondary representations.

### Source

- REM-03-355
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06
- CI-07

---

## REL-REC-203

### Title

Cross-client reply editing

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** be able to edit the reply through an authorised client other than the application that originally created it.

### Rationale

Editing remains subject to the reply schema, repository permissions and versioning rules.

### Source

- REM-03-356
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-204

### Title

Cross-client reply deletion

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** be able to delete the reply through an authorised client other than the application that originally created it.

### Rationale

Deletion remains subject to the repository’s deletion and tombstone requirements.

### Source

- REM-03-357
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-205

### Title

Target author does not own reply

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The identity controlling the target record **MUST NOT** be treated as the owner or controller of another identity’s reply merely because the reply references that target.

### Rationale

The target-side application may moderate display without acquiring canonical control of the reply record.

### Source

- REM-03-358
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02

---

## REL-REC-206

### Title

Application-specific moderation policies

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Different applications **MAY** apply different moderation or display policies to the same reply.

### Rationale

Application-level moderation affects presentation or availability within that application and does not automatically alter the canonical reply.

### Source

- REM-03-359
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

None identified.

---

## REL-REC-207

### Title

Reply survival beyond originating application

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A canonical reply **SHOULD** remain available through its repository independently of the continued existence of the application that created it.

### Rationale

This outcome depends on repository continuity and reinforces why the application is not the canonical owner of the reply.

### Source

- REM-03-360
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-352` | Direct | `REL-REC-200` |
| `REM-03-353` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-354` | Direct | `REL-REC-201` |
| `REM-03-355` | Direct | `REL-REC-202` |
| `REM-03-356` | Direct | `REL-REC-203` |
| `REM-03-357` | Direct | `REL-REC-204` |
| `REM-03-358` | Direct | `REL-REC-205` |
| `REM-03-359` | Direct | `REL-REC-206` |
| `REM-03-360` | Direct | `REL-REC-207` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 35 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-352` through `REM-03-360`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-199`.
- First identifier in this part: `REL-REC-200`.
- Final identifier in this part: `REL-REC-207`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–32.

## Traceability verification

- Every settled normative rule in scope maps directly or through justified decomposition to a catalogue requirement.
- Every generated requirement cites its in-scope REM identifier and authoritative design-note section.
- Every excluded entry remains individually accounted for in the coverage table.

## Source-status and implementation-neutrality verification

- Normative strength and material qualifications are preserved.
- Illustrative examples and open design questions do not become protocol requirements.
- No example vocabulary, physical field, syntax, mechanism or implementation detail is made mandatory unless the source establishes that obligation.
- Extraction Notes are used as rationale only and do not broaden the authoritative source rule.

## Normative-language verification

- Each generated catalogue requirement carries one explicit normative keyword.
- No later-section requirement is imported.

---

# 6. Part conclusion

Part 32 catalogues the settled normative content of Record Model Section 35 and excludes 1 explicitly non-normative entry.

The next catalogue part should address Section 36.
