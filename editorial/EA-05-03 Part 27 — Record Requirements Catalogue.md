# EA-05-03 — Record Requirements Catalogue

## Part 27 — Draft records

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 30, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 30 and REM-03 entries `REM-03-315` through `REM-03-322`.

Source Section 31 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-163

### Title

Local draft creation before acceptance

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** create local draft records before repository acceptance.

### Rationale

Local drafting allows incomplete work to exist before it becomes a canonical repository record.

### Source

- REM-03-315
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-164

### Title

Draft non-canonicity before commit

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A draft **MUST NOT** be treated as canonical until it has been included in an accepted repository commit.

### Rationale

Local persistence or application synchronisation alone does not establish canonical repository acceptance.

### Source

- REM-03-316
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

- CI-07
- AI-02

---

## REL-REC-165

### Title

Optional private repository drafts

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Repository **MAY** support private draft records.

### Rationale

This capability is optional. A private repository-supported draft remains distinct from a fully canonical published or active record where the schema or workflow makes that distinction.

### Source

- REM-03-317
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-166

### Title

Draft incompleteness indication

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate that it is incomplete.

### Rationale

Applications should not present draft content as final or complete where that status is material to the user.

### Source

- REM-03-318
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-167

### Title

Draft synchronisation indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate whether it has been synchronised.

### Rationale

Synchronisation status is distinct from canonical repository acceptance.

### Source

- REM-03-319
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-168

### Title

Draft creating-application indication

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** identify the application that created it.

### Rationale

This helps users and other applications understand draft origin and compatibility expectations.

### Source

- REM-03-320
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-169

### Title

Cross-application draft-editability indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate whether another application is permitted to edit it.

### Rationale

Editability may depend on schema support, repository authority, application grants and draft format compatibility.

### Source

- REM-03-321
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-170

### Title

No false canonical-storage representation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Applications **MUST NOT** present unsynchronised local drafts as safely stored canonical Relay Records.

### Rationale

Applications must accurately distinguish local-only state from repository-accepted canonical state so that users are not misled about durability, portability or recoverability.

### Source

- REM-03-322
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-315` | Direct | `REL-REC-163` |
| `REM-03-316` | Direct | `REL-REC-164` |
| `REM-03-317` | Direct | `REL-REC-165` |
| `REM-03-318` | Direct | `REL-REC-166` |
| `REM-03-319` | Direct | `REL-REC-167` |
| `REM-03-320` | Direct | `REL-REC-168` |
| `REM-03-321` | Direct | `REL-REC-169` |
| `REM-03-322` | Direct | `REL-REC-170` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 30 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-315` through `REM-03-322`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-162`.
- First identifier in this part: `REL-REC-163`.
- Final identifier in this part: `REL-REC-170`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–27.

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

Part 27 catalogues the settled normative content of Record Model Section 30.

The next catalogue part should address Section 31.
