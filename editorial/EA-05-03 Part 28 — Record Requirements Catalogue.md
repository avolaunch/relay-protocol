# EA-05-03 — Record Requirements Catalogue

## Part 28 — Application-specific records

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 31, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 31 and REM-03 entries `REM-03-323` through `REM-03-330`.

Source Section 32 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-171

### Title

Custom record-type definition

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** define a custom Relay record type.

### Rationale

A custom type remains subject to the wider Relay requirements for schema definition, repository acceptance and record portability.

### Source

- REM-03-323
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-172

### Title

Portable custom records

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A custom record **SHOULD** remain portable even where only one application currently implements or understands its schema.

### Rationale

Limited ecosystem support does not justify binding the record permanently to the originating application.

### Source

- REM-03-324
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

- CI-03

---

## REL-REC-173

### Title

Preservation without rendering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** preserve an unsupported custom record without rendering its schema-defined content.

### Rationale

Preservation allows records to survive transitions through applications that do not yet understand their schema.

### Source

- REM-03-325
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-174

### Title

Limited metadata rendering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** render only the protocol-level or otherwise understood metadata of a custom record whose full schema it does not implement.

### Rationale

Limited rendering must not imply that the application has fully interpreted or validated unsupported schema content.

### Source

- REM-03-326
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-175

### Title

Interpretation after schema implementation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** interpret a custom record after implementing the applicable schema.

### Rationale

Interpretation should follow the schema’s declared structure, semantics and compatibility rules.

### Source

- REM-03-327
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-176

### Title

Permissioned transformation of custom records

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

An application **MAY** transform a custom record into another schema only where the required permission has been obtained.

### Rationale

Section 33 provides additional provenance and source-preservation requirements for translated records.

### Source

- REM-03-328
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-177

### Title

Prohibition on anti-competitive obscurity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The originating application **MUST NOT** encrypt, encode or otherwise obscure a record solely to prevent competing clients from using, preserving or interpreting it.

### Rationale

This prohibition targets deliberate competitive exclusion rather than legitimate confidentiality or security controls.

### Source

- REM-03-329
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

- CI-04

---

## REL-REC-178

### Title

Security-based encryption exception

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An originating application **MAY** encrypt or obscure record content where that protection is genuinely required for user security.

### Rationale

The security purpose must be genuine and must not be used as a pretext for application lock-in.

### Source

- REM-03-330
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-323` | Direct | `REL-REC-171` |
| `REM-03-324` | Direct | `REL-REC-172` |
| `REM-03-325` | Direct | `REL-REC-173` |
| `REM-03-326` | Direct | `REL-REC-174` |
| `REM-03-327` | Direct | `REL-REC-175` |
| `REM-03-328` | Direct | `REL-REC-176` |
| `REM-03-329` | Direct | `REL-REC-177` |
| `REM-03-330` | Direct | `REL-REC-178` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 31 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-323` through `REM-03-330`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-170`.
- First identifier in this part: `REL-REC-171`.
- Final identifier in this part: `REL-REC-178`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–28.

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

Part 28 catalogues the settled normative content of Record Model Section 31.

The next catalogue part should address Section 32.
