# EA-05-03 — Record Requirements Catalogue

## Part 23 — Embedded content

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 26, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 26 and REM-03 entries `REM-03-282` through `REM-03-291`.

Source Section 27 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-283`, `REM-03-284`, `REM-03-285`, `REM-03-286`, `REM-03-288`, `REM-03-289`, `REM-03-290` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-140

### Title

Limited embedded representation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record MAY contain a limited embedded representation of another object.

### Rationale

The source permits limited representations such as quoted text, thumbnails, preview titles or an author handle observed at publication time. An embed is not a complete replacement for the referenced source object.

### Source

- REM-03-282
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

## REL-REC-141

### Title

Provenance for embedded content

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Embedded content SHOULD include provenance sufficient to identify its source and observation context.

### Rationale

Useful provenance may include the source Record URI, observed version and observation time, as illustrated by the source example.

### Source

- REM-03-287
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

## REL-REC-142

### Title

Embed Treatment as Historical Observation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An application **MUST** treat an embed as a historical observation.

### Rationale

Applications may separately resolve the source Record URI to obtain current state, but must not silently overwrite the historical meaning of the embed.

### Source

- REM-03-291
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

## REL-REC-143

### Title

No Assumption That an Embed Is Current

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** assume that an embed necessarily represents the current state of the source record.

### Rationale

Applications may separately resolve the source Record URI to obtain current state, but must not silently overwrite the historical meaning of the embed.

### Source

- REM-03-291
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-282` | Direct | `REL-REC-140` |
| `REM-03-283` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-284` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-285` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-286` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-287` | Direct | `REL-REC-141` |
| `REM-03-288` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-289` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-290` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-291` | Decomposed to preserve distinct normative effects | `REL-REC-142` and `REL-REC-143` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 26 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-282` through `REM-03-291`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-139`.
- First identifier in this part: `REL-REC-140`.
- Final identifier in this part: `REL-REC-143`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–23.

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

Part 23 catalogues the settled normative content of Record Model Section 26 and excludes 7 explicitly non-normative entries.

The next catalogue part should address Section 27.
