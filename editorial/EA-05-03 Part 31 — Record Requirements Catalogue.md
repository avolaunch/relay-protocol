# EA-05-03 — Record Requirements Catalogue

## Part 31 — Canonical records and projections

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 34, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 34 and REM-03 entries `REM-03-348` through `REM-03-351`.

Source Section 35 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-196

### Title

Projection definition

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Projection **MUST** be treated as an application-specific representation derived from one or more source records.

### Rationale

Examples include feed cards, profile pages, search results, résumés and recommendation scores.

### Source

- REM-03-348
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-04

---

## REL-REC-197

### Title

Projection not automatically canonical

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application-generated Projection **MUST NOT** be treated as a canonical Relay Record merely because it was derived or displayed.

### Rationale

Derived application views remain outside canonical repository history unless deliberately saved.

### Source

- REM-03-349
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-07

---

## REL-REC-198

### Title

Deliberate saving requirement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Projection **MUST** become a repository record only when the controller deliberately saves it through an authorised repository operation.

### Rationale

Automatic generation, caching or display does not satisfy the deliberate-saving requirement.

### Source

- REM-03-350
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-199

### Title

Prevention of projection pollution

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Applications **SHOULD** preserve the distinction between Projections and repository records so that transient or application-generated views do not pollute the controller’s canonical history.

### Rationale

The requirement supports meaningful canonical history rather than indiscriminate persistence of every derived presentation.

### Source

- REM-03-351
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-02
- CI-07
- CI-10

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-348` | Direct | `REL-REC-196` |
| `REM-03-349` | Direct | `REL-REC-197` |
| `REM-03-350` | Direct | `REL-REC-198` |
| `REM-03-351` | Direct | `REL-REC-199` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 34 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-348` through `REM-03-351`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-195`.
- First identifier in this part: `REL-REC-196`.
- Final identifier in this part: `REL-REC-199`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–31.

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

Part 31 catalogues the settled normative content of Record Model Section 34.

The next catalogue part should address Section 35.
