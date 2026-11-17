# EA-05-03 — Record Requirements Catalogue

## Part 37 — Batch operations

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 40, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 40 and REM-03 entries `REM-03-390` through `REM-03-393`.

Source Section 41 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-230

### Title

Multiple record changes in one commit

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** submit multiple record changes together as one repository commit.

### Rationale

The changes may include heterogeneous operations affecting different records and collections.

### Source

- REM-03-390
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

## REL-REC-231

### Title

Atomic batch success or failure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A batch commit **MUST** be atomic: all included record changes MUST be accepted together, or none of them MUST be accepted.

### Rationale

Partial acceptance would leave repository state inconsistent with the submitted commit boundary.

### Source

- REM-03-391
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

- AI-03

---

## REL-REC-232

### Title

Independent addressability after batch acceptance

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Each record affected or created by an accepted batch commit **MUST** remain independently addressable after acceptance.

### Rationale

Batching changes for atomic acceptance must not collapse the participating records into one inseparable logical object.

### Source

- REM-03-392
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

## REL-REC-233

### Title

Batch commit does not replace record identity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The identity of the batch commit **MUST** remain distinct from the stable logical identity of each record included in that commit.

### Rationale

The commit identifies the accepted state transition, while each Record URI continues to identify its own logical record.

### Source

- REM-03-393
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-390` | Direct | `REL-REC-230` |
| `REM-03-391` | Direct | `REL-REC-231` |
| `REM-03-392` | Direct | `REL-REC-232` |
| `REM-03-393` | Direct | `REL-REC-233` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 40 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-390` through `REM-03-393`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-229`.
- First identifier in this part: `REL-REC-230`.
- Final identifier in this part: `REL-REC-233`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–37.

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

Part 37 catalogues the settled normative content of Record Model Section 40.

The next catalogue part should address Section 41.
