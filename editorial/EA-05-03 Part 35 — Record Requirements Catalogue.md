# EA-05-03 — Record Requirements Catalogue

## Part 35 — Moderation labels

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 38, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 38 and REM-03 entries `REM-03-373` through `REM-03-381`.

Source Section 39 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-374`, `REM-03-375`, `REM-03-376`, `REM-03-377` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-217

### Title

Moderation decision represented separately

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A moderation decision SHOULD be represented as a separate record rather than as an in-place rewrite of the target record.

### Rationale

Separate representation preserves the distinction between original content and a third-party judgement about that content.

### Source

- REM-03-373
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-218

### Title

Label does not alter original record

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Issuing or applying a moderation label MUST NOT alter the canonical content or history of the original target record.

### Rationale

An application may change how it displays or serves the target based on the label without rewriting the target itself.

### Source

- REM-03-378
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-219

### Title

Application choice of trusted label providers

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications MAY choose which moderation-label issuers and moderation policies they trust or enforce.

### Rationale

Different applications may therefore produce different moderation outcomes from the same underlying records and labels.

### Source

- REM-03-379
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-220

### Title

No universal moderation policy in Relay v0.1

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay v0.1 MUST NOT be interpreted as defining one universal moderation policy that all applications must apply.

### Rationale

The protocol supplies interoperable moderation records, not a universal content-policy authority.

### Source

- REM-03-380
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-221

### Title

Support for independently issued labels

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model MUST support moderation labels issued independently of the repository or identity controlling the target record.

### Rationale

Independent issuance requires clear issuer, subject and provenance information.

### Source

- REM-03-381
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-373` | Direct | `REL-REC-217` |
| `REM-03-374` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-375` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-376` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-377` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-378` | Direct | `REL-REC-218` |
| `REM-03-379` | Direct | `REL-REC-219` |
| `REM-03-380` | Direct | `REL-REC-220` |
| `REM-03-381` | Direct | `REL-REC-221` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 38 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-373` through `REM-03-381`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-216`.
- First identifier in this part: `REL-REC-217`.
- Final identifier in this part: `REL-REC-221`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–35.

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

Part 35 catalogues the settled normative content of Record Model Section 38 and excludes 4 explicitly non-normative entries.

The next catalogue part should address Section 39.
