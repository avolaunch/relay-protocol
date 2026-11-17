# EA-05-03 — Record Requirements Catalogue

## Part 30 — Record translation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 33, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 33 and REM-03 entries `REM-03-339` through `REM-03-347`.

Source Section 34 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-187

### Title

Schema translation capability

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** translate a record from one schema into another schema.

### Rationale

Translation may be lossy or reversible, but those characteristics must be disclosed through provenance.

### Source

- REM-03-339
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-188

### Title

Source Record URI provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** preserve the source Record URI in its provenance.

### Rationale

The source URI links the translated result to the logical record from which it was derived.

### Source

- REM-03-340
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-189

### Title

Source schema provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** preserve the identifier of the source schema in its provenance.

### Rationale

The source schema is necessary to understand the original semantics and assess the transformation.

### Source

- REM-03-341
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-10

---

## REL-REC-190

### Title

Transformation-application provenance

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** identify the application or agent that performed the transformation.

### Rationale

This identifies the party responsible for applying the translation logic.

### Source

- REM-03-342
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-191

### Title

Transformation-time provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** record when the transformation occurred.

### Rationale

Transformation time is distinct from the source record’s creation or update time.

### Source

- REM-03-343
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-192

### Title

Reversibility disclosure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** state whether the translation is reversible.

### Rationale

A translation is reversible only where the source representation can be reconstructed without unrecorded loss.

### Source

- REM-03-344
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-193

### Title

Omitted-information disclosure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** disclose any source information omitted during translation.

### Rationale

This prevents a lossy translation from being mistaken for a complete representation of the source.

### Source

- REM-03-345
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-194

### Title

No silent replacement of source records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A translation operation **MUST NOT** silently replace the source record.

### Rationale

By default, the translated record is a derived object rather than an implicit overwrite of the source.

### Source

- REM-03-346
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-195

### Title

Explicit authority for source replacement

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

A translated record **MAY** replace its source record only where the controller explicitly authorises the replacement.

### Rationale

The authorisation should be explicit and recorded through the repository operation accepting the change.

### Source

- REM-03-347
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-02
- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-339` | Direct | `REL-REC-187` |
| `REM-03-340` | Direct | `REL-REC-188` |
| `REM-03-341` | Direct | `REL-REC-189` |
| `REM-03-342` | Direct | `REL-REC-190` |
| `REM-03-343` | Direct | `REL-REC-191` |
| `REM-03-344` | Direct | `REL-REC-192` |
| `REM-03-345` | Direct | `REL-REC-193` |
| `REM-03-346` | Direct | `REL-REC-194` |
| `REM-03-347` | Direct | `REL-REC-195` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 33 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-339` through `REM-03-347`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-186`.
- First identifier in this part: `REL-REC-187`.
- Final identifier in this part: `REL-REC-195`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers remain continuous and unique across Parts 1–30.

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

Part 30 catalogues the settled normative content of Record Model Section 33.

The next catalogue part should address Section 34.
