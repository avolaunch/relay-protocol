# EA-05-03 — Record Requirements Catalogue

## Part 40 — Required v0.1 record operations

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 43, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 43 and REM-03 entries `REM-03-408` through `REM-03-425`.

Source Section 44 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-245

### Title

Create-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support creation of a record through an authorised repository operation.

### Rationale

Creation remains subject to schema, authority, validation and accepted-commit requirements.

### Source

- REM-03-408
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-246

### Title

Read-current-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support reading the current accepted version of a logical record.

### Rationale

Access remains subject to the record’s visibility and audience rules.

### Source

- REM-03-409
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-247

### Title

Read-specific-version operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support reading a specific historical Record Version where that version remains retrievable and access is authorised.

### Rationale

This operation is distinct from resolving the current version through the base Record URI.

### Source

- REM-03-410
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-248

### Title

List-records-by-collection operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support listing records by collection.

### Rationale

The results must respect visibility, audience and other access controls.

### Source

- REM-03-411
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-249

### Title

Validate-record-envelope operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support validation of a Record Envelope against protocol-level structural requirements.

### Rationale

Envelope validation is separate from schema-content and semantic validation.

### Source

- REM-03-412
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-250

### Title

Validate-record-schema operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support validation of record content against its declared schema where that schema is supported.

### Rationale

Unknown valid schemas must still be preserved even where local schema validation is unavailable.

### Source

- REM-03-413
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-251

### Title

Update-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support authorised updates to records whose schemas permit updating.

### Rationale

An accepted update creates a new Record Version and must satisfy concurrency and authority rules.

### Source

- REM-03-414
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-252

### Title

Delete-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support authorised record deletion.

### Rationale

Deletion must preserve the distinctions among deletion modes and apply applicable tombstone requirements.

### Source

- REM-03-415
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-253

### Title

Restore-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support restoration of a deleted record where the schema and retained state permit restoration and the controller authorises it.

### Rationale

Restoration is conditional and creates a new current version without erasing the historical deletion event.

### Source

- REM-03-416
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-254

### Title

Read-tombstone operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support reading an accessible tombstone for a deleted or retired logical record.

### Rationale

The tombstone must expose only the minimum information allowed by protocol and policy.

### Source

- REM-03-417
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-255

### Title

Verify-record-integrity operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support verification of record integrity against the applicable integrity reference and accepted repository history.

### Rationale

The exact proof mechanism may depend on commits, hashes, signatures or other protocol-defined structures.

### Source

- REM-03-418
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-256

### Title

Resolve-record-references operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support resolution of references to other Relay Records or specific Record Versions where accessible.

### Rationale

Unavailable targets must be handled accurately rather than causing the referring record to be misrepresented.

### Source

- REM-03-419
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-257

### Title

Upload-and-attach-blob operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support uploading a blob and attaching its stable reference to a record where permitted by the schema.

### Rationale

Temporary storage URLs must not become the blob’s permanent identity.

### Source

- REM-03-420
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-258

### Title

Change-visibility operation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support authorised changes to a record’s visibility classification where permitted.

### Rationale

A visibility change may create a new version even where the primary content does not change.

### Source

- REM-03-421
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-259

### Title

Change-audience operation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support authorised changes to a restricted record’s audience rules where permitted.

### Rationale

Audience removal revokes future authorised access but cannot guarantee deletion of copies already received.

### Source

- REM-03-422
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-260

### Title

Inspect-provenance operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST support inspection of the structured provenance associated with a record.

### Rationale

Inspection must preserve the distinction between declared provenance and verified provenance.

### Source

- REM-03-423
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-261

### Title

Preserve-unknown-record-types operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST preserve valid record types that it does not understand.

### Rationale

Unknown records may be preserved without being rendered or fully validated against their schema locally.

### Source

- REM-03-424
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-262

### Title

Detect-update-conflict operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation MUST detect when competing updates attempt to replace the same current version.

### Rationale

Detected conflicts must not be silently collapsed into one linear continuation.

### Source

- REM-03-425
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-408` | Direct | `REL-REC-245` |
| `REM-03-409` | Direct | `REL-REC-246` |
| `REM-03-410` | Direct | `REL-REC-247` |
| `REM-03-411` | Direct | `REL-REC-248` |
| `REM-03-412` | Direct | `REL-REC-249` |
| `REM-03-413` | Direct | `REL-REC-250` |
| `REM-03-414` | Direct | `REL-REC-251` |
| `REM-03-415` | Direct | `REL-REC-252` |
| `REM-03-416` | Direct | `REL-REC-253` |
| `REM-03-417` | Direct | `REL-REC-254` |
| `REM-03-418` | Direct | `REL-REC-255` |
| `REM-03-419` | Direct | `REL-REC-256` |
| `REM-03-420` | Direct | `REL-REC-257` |
| `REM-03-421` | Direct | `REL-REC-258` |
| `REM-03-422` | Direct | `REL-REC-259` |
| `REM-03-423` | Direct | `REL-REC-260` |
| `REM-03-424` | Direct | `REL-REC-261` |
| `REM-03-425` | Direct | `REL-REC-262` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 43 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-408` through `REM-03-425`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-244`.
- First identifier in this part: `REL-REC-245`.
- Final identifier in this part: `REL-REC-262`.
- Total catalogue requirements in this part: 18.
- Catalogue identifiers remain continuous and unique across Parts 1–40.

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

Part 40 catalogues the settled normative content of Record Model Section 43.

The next catalogue part should address Section 44.
