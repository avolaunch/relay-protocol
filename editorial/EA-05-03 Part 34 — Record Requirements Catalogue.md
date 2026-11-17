# EA-05-03 — Record Requirements Catalogue

## Part 34 — Reposts and references

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 37, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 37 and REM-03 entries `REM-03-368` through `REM-03-372`.

Source Section 38 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-370` is explicitly non-normative and does not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-213

### Title

Repost must not imply copied authorship

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A repost **SHOULD NOT** require the original record to be copied into the reposter’s repository in a form that represents the reposter as the original author.

### Rationale

A cached or embedded representation may still exist, but it must preserve source provenance and must not misstate authorship.

### Source

- REM-03-368
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

None identified.

---

## REL-REC-214

### Title

Repost represented through source reference

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A repost record **SHOULD** reference the original source record using its stable protocol identifier.

### Rationale

The repost is a distinct logical record whose meaning depends on its reference to the source.

### Source

- REM-03-369
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

None identified.

---

## REL-REC-215

### Title

Repost belongs to reposter

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The repost record **MUST** remain controlled by the repository and authorising identity of the reposter.

### Rationale

The reposter may control the repost without gaining control of the referenced original.

### Source

- REM-03-371
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-216

### Title

Original remains under original-author control

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Creation of a repost **MUST NOT** transfer control of the original record away from its original authoritative repository and authorising identity.

### Rationale

The original author may update or delete the source according to its own schema and repository rules, independently of the repost.

### Source

- REM-03-372
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-368` | Direct | `REL-REC-213` |
| `REM-03-369` | Direct | `REL-REC-214` |
| `REM-03-370` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-371` | Direct | `REL-REC-215` |
| `REM-03-372` | Direct | `REL-REC-216` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 37 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-368` through `REM-03-372`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-212`.
- First identifier in this part: `REL-REC-213`.
- Final identifier in this part: `REL-REC-216`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–34.

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

Part 34 catalogues the settled normative content of Record Model Section 37 and excludes 1 explicitly non-normative entry.

The next catalogue part should address Section 38.
