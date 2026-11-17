# EA-05-03 — Record Requirements Catalogue

## Part 29 — Schema extension

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 32, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 32 and REM-03 entries `REM-03-331` through `REM-03-338`.

Source Section 33 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-179

### Title

Controlled schema extension

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay **SHOULD** support controlled extension of existing schemas.

### Rationale

“Controlled” indicates that extensions must remain identifiable and must not undermine required core semantics.

### Source

- REM-03-331
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

## REL-REC-180

### Title

Optional extension fields

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support optional extension fields.

### Rationale

Applications that do not understand an optional extension should still be able to preserve the underlying record.

### Source

- REM-03-332
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-181

### Title

Referenced extension records

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** represent additional information through separately referenced extension records.

### Rationale

Separate records can reduce mutation of the base record and allow independent authority or lifecycle rules.

### Source

- REM-03-333
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-182

### Title

Schema inheritance

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support schema inheritance.

### Rationale

Inheritance must not change the established meaning of inherited required core fields.

### Source

- REM-03-334
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-183

### Title

Namespaced metadata

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support namespaced metadata.

### Rationale

Namespacing allows independently defined extensions to coexist without redefining or colliding with core fields.

### Source

- REM-03-335
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-184

### Title

Core-field semantic immutability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A schema extension **MUST NOT** redefine, contradict or replace the established meaning of any required core field.

### Rationale

Extensions may add information but cannot silently change the semantics on which other implementations rely.

### Source

- REM-03-336
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-185

### Title

Ignoring unsupported extensions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** ignore an extension it does not understand.

### Rationale

Ignoring means declining to interpret or use the extension, not deleting it.

### Source

- REM-03-337
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

## REL-REC-186

### Title

Preservation of unsupported extensions

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An application that ignores an unsupported extension **SHOULD** preserve that extension when reading, storing or rewriting the record.

### Rationale

Preservation prevents applications with partial schema support from causing silent information loss.

### Source

- REM-03-338
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-331` | Direct | `REL-REC-179` |
| `REM-03-332` | Direct | `REL-REC-180` |
| `REM-03-333` | Direct | `REL-REC-181` |
| `REM-03-334` | Direct | `REL-REC-182` |
| `REM-03-335` | Direct | `REL-REC-183` |
| `REM-03-336` | Direct | `REL-REC-184` |
| `REM-03-337` | Direct | `REL-REC-185` |
| `REM-03-338` | Direct | `REL-REC-186` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 32 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-331` through `REM-03-338`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-178`.
- First identifier in this part: `REL-REC-179`.
- Final identifier in this part: `REL-REC-186`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–29.

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

Part 29 catalogues the settled normative content of Record Model Section 32.

The next catalogue part should address Section 33.
