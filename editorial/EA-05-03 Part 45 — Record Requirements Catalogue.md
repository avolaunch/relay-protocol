# EA-05-03 — Record Requirements Catalogue

## Part 45 — Core record principle

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 48, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 48 and REM-03 entries `REM-03-483` through `REM-03-483`.

This is the final Record Model source section.

---

# 3. Requirements

---

## REL-REC-312

### Title

Stable Portable Record Principle

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** be treated as a stable and portable logical object governed by repository authority.

### Rationale

This principle summarises the Record Model and governs interpretation of the more detailed requirements throughout REM-03.

### Source

- REM-03-483
- `design-notes/03-record-model.md`, Section 48

### Related Invariants

None identified.

---

## REL-REC-313

### Title

No Disposable Application-Owned Row Treatment

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Record **MUST NOT** be treated as a disposable application-owned database row whose identity or continued existence depends on the application that created it.

### Rationale

This principle summarises the Record Model and governs interpretation of the more detailed requirements throughout REM-03.

### Source

- REM-03-483
- `design-notes/03-record-model.md`, Section 48

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-483` | Decomposed to preserve distinct normative effects | `REL-REC-312` and `REL-REC-313` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 48 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-483` through `REM-03-483`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-311`.
- First identifier in this part: `REL-REC-312`.
- Final identifier in this part: `REL-REC-313`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers remain continuous and unique across Parts 1–45.

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

Part 45 catalogues the settled normative content of Record Model Section 48.

This completes catalogue generation for `design-notes/03-record-model.md`.
