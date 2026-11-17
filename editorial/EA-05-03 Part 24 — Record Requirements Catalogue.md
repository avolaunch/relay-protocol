# EA-05-03 — Record Requirements Catalogue

## Part 24 — Blob references

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 27, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 27 and REM-03 entries `REM-03-292` through `REM-03-299`.

Source Section 28 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-144

### Title

Blob-reference support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record MAY refer to one or more blobs.

### Rationale

Blobs may hold binary or large content while the record retains protocol metadata and references.

### Source

- REM-03-292
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-145

### Title

Blob identifier

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A blob reference SHOULD include a blob identifier.

### Rationale

The blob identifier should provide stable identity independent of a temporary delivery URL.

### Source

- REM-03-293
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-146

### Title

Blob media type

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference SHOULD include the blob’s media type.

### Rationale

Media type enables applications to determine whether and how they can process or present the referenced content.

### Source

- REM-03-294
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-147

### Title

Blob intended role

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference SHOULD identify the intended role or purpose of the blob within the record.

### Rationale

Examples may include primary image, attachment, thumbnail or another schema-defined purpose.

### Source

- REM-03-295
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-148

### Title

Blob accessibility metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference SHOULD include accessibility metadata where applicable.

### Rationale

The example uses alternative text for an image. Other media may require captions, transcripts or schema-specific accessibility information.

### Source

- REM-03-296
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-149

### Title

Optional blob dimensions or duration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A blob reference MAY include dimensions or duration where relevant to the referenced media.

### Rationale

Dimensions are relevant to visual media, while duration is relevant to audio, video or time-based media.

### Source

- REM-03-297
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-150

### Title

Blob integrity hash

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference SHOULD include an integrity hash.

### Rationale

The hash enables applications or repositories to verify that retrieved blob content matches the referenced object.

### Source

- REM-03-298
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-151

### Title

Temporary URL not permanent blob identity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Record MUST NOT treat a temporary storage or delivery URL as the permanent identity of a blob.

### Rationale

Temporary URLs may expire, rotate or change providers. Stable blob identity must remain independent of the current retrieval location.

### Source

- REM-03-299
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-292` | Direct | `REL-REC-144` |
| `REM-03-293` | Direct | `REL-REC-145` |
| `REM-03-294` | Direct | `REL-REC-146` |
| `REM-03-295` | Direct | `REL-REC-147` |
| `REM-03-296` | Direct | `REL-REC-148` |
| `REM-03-297` | Direct | `REL-REC-149` |
| `REM-03-298` | Direct | `REL-REC-150` |
| `REM-03-299` | Direct | `REL-REC-151` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 27 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-292` through `REM-03-299`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-143`.
- First identifier in this part: `REL-REC-144`.
- Final identifier in this part: `REL-REC-151`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–24.

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

Part 24 catalogues the settled normative content of Record Model Section 27.

The next catalogue part should address Section 28.
