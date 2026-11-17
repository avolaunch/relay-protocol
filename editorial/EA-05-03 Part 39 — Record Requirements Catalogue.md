# EA-05-03 — Record Requirements Catalogue

## Part 39 — Record interoperability

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 42, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 42 and REM-03 entries `REM-03-403` through `REM-03-407`.

Source Section 43 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-404`, `REM-03-405`, `REM-03-406` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-243

### Title

Universal type support not required

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A compliant Relay application **MUST NOT** be required to fully interpret or render every valid Relay record type.

### Rationale

Interoperability is achieved through safe handling and preservation, not mandatory universal feature support.

### Source

- REM-03-403
- `design-notes/03-record-model.md`, Section 42

### Related Invariants

None identified.

---

## REL-REC-244

### Title

Minimum handling of unsupported records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A compliant application **MUST NOT** damage, misrepresent or discard a valid record solely because the application does not support its record type.

### Rationale

The application may decline to display or operate on the record, but must preserve it accurately where it assumes custody or participates in migration.

### Source

- REM-03-407
- `design-notes/03-record-model.md`, Section 42

### Related Invariants

- AI-10

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-403` | Direct | `REL-REC-243` |
| `REM-03-404` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-405` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-406` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-407` | Direct | `REL-REC-244` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 42 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-403` through `REM-03-407`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-242`.
- First identifier in this part: `REL-REC-243`.
- Final identifier in this part: `REL-REC-244`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers remain continuous and unique across Parts 1–39.

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

Part 39 catalogues the settled normative content of Record Model Section 42 and excludes 3 explicitly non-normative entries.

The next catalogue part should address Section 43.
