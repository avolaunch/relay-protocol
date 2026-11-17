# EA-05-03 — Record Requirements Catalogue

## Part 25 — Lists and ordering

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 28, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 28 and REM-03 entries `REM-03-300` through `REM-03-305`.

Source Section 29 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-152

### Title

Ordered-item support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support schemas for records containing ordered items.

### Rationale

Examples include portfolio ordering, image galleries, playlists and article sections.

### Source

- REM-03-300
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-153

### Title

Schema-defined ordering model

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema governing ordered items **MUST** define how ordering is represented or derived.

### Rationale

The source identifies three permitted models: ordering as record content, ordering derived by an application, or ordering maintained through separate relationship records.

### Source

- REM-03-301
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-154

### Title

Ordering as record content

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define ordering as part of the record content.

### Rationale

Under this model, changes to order may constitute changes to the record content and may create a new version.

### Source

- REM-03-302
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-155

### Title

Application-derived ordering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define that ordering is derived by an application rather than stored canonically in the record.

### Rationale

Applications must not imply that an application-derived order is repository-wide canonical order unless the schema establishes that meaning.

### Source

- REM-03-303
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

- CI-07

---

## REL-REC-156

### Title

Relationship-record ordering

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define that ordering is maintained through separate relationship records.

### Rationale

This allows order to be changed independently of the primary items being ordered.

### Source

- REM-03-304
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-157

### Title

No assumed repository-wide order

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

Applications **SHOULD NOT** assume a repository-wide universal order where the applicable schema does not define one.

### Rationale

Display order may be local, contextual or application-derived unless the schema establishes canonical ordering semantics.

### Source

- REM-03-305
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-300` | Direct | `REL-REC-152` |
| `REM-03-301` | Direct | `REL-REC-153` |
| `REM-03-302` | Direct | `REL-REC-154` |
| `REM-03-303` | Direct | `REL-REC-155` |
| `REM-03-304` | Direct | `REL-REC-156` |
| `REM-03-305` | Direct | `REL-REC-157` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 28 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-300` through `REM-03-305`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-151`.
- First identifier in this part: `REL-REC-152`.
- Final identifier in this part: `REL-REC-157`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers remain continuous and unique across Parts 1–25.

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

Part 25 catalogues the settled normative content of Record Model Section 28.

The next catalogue part should address Section 29.
