# EA-05-03 — Record Requirements Catalogue

## Part 26 — Local application state

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 29, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 29 and REM-03 entries `REM-03-306` through `REM-03-314`.

Source Section 30 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-307`, `REM-03-308`, `REM-03-309`, `REM-03-310` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-158

### Title

Canonical repository exclusion for some preferences

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Applications **MUST NOT** assume that every application preference or implementation detail belongs in the canonical Relay Repository.

### Rationale

Examples that may remain local include window size, dismissed-tooltip state, temporary draft position and client-specific cache configuration.

### Source

- REM-03-306
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-159

### Title

Portability-value test for canonical inclusion

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Information or state **SHOULD** be stored in the canonical Relay Repository when preserving it across applications provides meaningful portability or continuity value to the user.

### Rationale

The criterion focuses on user value rather than technical possibility.

### Source

- REM-03-311
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07
- CI-03

---

## REL-REC-160

### Title

Discouragement of irrelevant implementation details

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The protocol **SHOULD** discourage applications from storing irrelevant implementation details in the canonical Relay Repository.

### Rationale

Excess local-state records can reduce clarity, portability and long-term repository usefulness.

### Source

- REM-03-312
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-161

### Title

Reasonable survival expectation test

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Applications **SHOULD** evaluate canonical inclusion by asking whether the person would reasonably expect the information or state to survive a change of application.

### Rationale

The test is editorial guidance for deciding whether state has meaningful portability or continuity value.

### Source

- REM-03-313
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-162

### Title

Local retention where survival is not expected

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Information or state **MAY** remain local where a person would not reasonably expect it to survive a change of application.

### Rationale

This is permission, not a prohibition on portability. A schema or user choice may still justify canonical storage in a particular case.

### Source

- REM-03-314
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-306` | Direct | `REL-REC-158` |
| `REM-03-307` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-308` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-309` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-310` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-311` | Direct | `REL-REC-159` |
| `REM-03-312` | Direct | `REL-REC-160` |
| `REM-03-313` | Direct | `REL-REC-161` |
| `REM-03-314` | Direct | `REL-REC-162` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 29 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-306` through `REM-03-314`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-157`.
- First identifier in this part: `REL-REC-158`.
- Final identifier in this part: `REL-REC-162`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–26.

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

Part 26 catalogues the settled normative content of Record Model Section 29 and excludes 4 explicitly non-normative entries.

The next catalogue part should address Section 30.
