# EA-05-03 — Record Requirements Catalogue

## Part 38 — Record portability

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 41, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 41 and REM-03 entries `REM-03-394` through `REM-03-402`.

Source Section 42 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-234

### Title

Preservation of Record URI during portability

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve the Record URI of a portable record.

### Rationale

Migration must not assign a new logical identity merely because the serving provider changes.

### Source

- REM-03-394
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-235

### Title

Preservation of collection and schema

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve the record’s collection association and schema identifier during migration.

### Rationale

Preserving content without its collection and schema context would remove operational meaning required for validation and interoperability.

### Source

- REM-03-395
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-236

### Title

Envelope validation after migration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A portable record MUST remain capable of passing applicable Record Envelope validation at the receiving compliant provider.

### Rationale

Migration must preserve the protocol-level metadata and context necessary for validation.

### Source

- REM-03-396
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-237

### Title

Preservation of record content

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve the record’s schema-defined content during migration.

### Rationale

Any deliberate transformation belongs to a separately authorised translation or migration process and must not be confused with faithful preservation.

### Source

- REM-03-397
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-238

### Title

Preservation of blob references

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve the record’s blob references during migration.

### Rationale

The storage location may change, but the stable blob identity and relationship to the record must remain intact.

### Source

- REM-03-398
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-239

### Title

Preservation of version history

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve the record’s version history during migration.

### Rationale

Portability is not satisfied by retaining only the latest visible payload where the protocol history is required to verify record state.

### Source

- REM-03-399
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-240

### Title

Preservation of unknown extensions

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST preserve valid extensions that it does not understand.

### Rationale

Lack of local interpretation is not permission to strip unknown but valid extension data.

### Source

- REM-03-400
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-241

### Title

Continued visibility-rule enforcement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider MUST continue serving a migrated record in accordance with its applicable visibility rules.

### Rationale

Migration must not silently make restricted or private content public, or make public content unavailable without a separately valid reason.

### Source

- REM-03-401
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

## REL-REC-242

### Title

Operational meaning required for portability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A migration MUST NOT be considered Relay-portable if it merely converts records into flat files while losing the protocol metadata, relationships, validation context or operational meaning required by the Record Model.

### Rationale

Exportability alone is not sufficient. The receiving environment must be able to continue treating the information as operational Relay records.

### Source

- REM-03-402
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-394` | Direct | `REL-REC-234` |
| `REM-03-395` | Direct | `REL-REC-235` |
| `REM-03-396` | Direct | `REL-REC-236` |
| `REM-03-397` | Direct | `REL-REC-237` |
| `REM-03-398` | Direct | `REL-REC-238` |
| `REM-03-399` | Direct | `REL-REC-239` |
| `REM-03-400` | Direct | `REL-REC-240` |
| `REM-03-401` | Direct | `REL-REC-241` |
| `REM-03-402` | Direct | `REL-REC-242` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 41 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-394` through `REM-03-402`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-233`.
- First identifier in this part: `REL-REC-234`.
- Final identifier in this part: `REL-REC-242`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers remain continuous and unique across Parts 1–38.

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

Part 38 catalogues the settled normative content of Record Model Section 41.

The next catalogue part should address Section 42.
