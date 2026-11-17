# EA-05-03 — Record Requirements Catalogue

## Part 41 — Record invariants

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 44, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 44 and REM-03 entries `REM-03-426` through `REM-03-437`.

Source Section 45 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-263

### Title

Unique Logical Record Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Record URI **MUST** identify exactly one logical record.

### Rationale

The rule continues to apply after deletion and is supported by tombstone retention.

### Source

- REM-03-426
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-264

### Title

No Record URI Reassignment

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Record URI **MUST NOT** be reassigned to another logical record.

### Rationale

The rule continues to apply after deletion and is supported by tombstone retention.

### Source

- REM-03-426
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-265

### Title

URI stability under editing invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Editing a record MUST NOT change the Record URI of the logical record.

### Rationale

The edit creates a new version rather than a new logical identity.

### Source

- REM-03-427
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-266

### Title

Accepted-commit membership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every current Record Version MUST belong to an accepted repository commit.

### Rationale

A locally generated or pending version cannot be represented as canonical current state.

### Source

- REM-03-428
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-267

### Title

Submitter-authority distinction invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Record Model MUST NOT assume that the submitting application or agent is the authorising identity.

### Rationale

The two roles may coincide but must remain independently representable.

### Source

- REM-03-429
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-268

### Title

Schema-use ownership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Use of a schema MUST NOT confer ownership or repository control of the record on the schema publisher.

### Rationale

Schema authority governs the schema definition, not individual conforming records.

### Source

- REM-03-430
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-269

### Title

Visibility-rights distinction invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A record’s visibility classification MUST NOT be treated as determining its legal ownership or usage rights.

### Rationale

A public record may remain subject to licensing, attribution, commercial-use or model-training restrictions.

### Source

- REM-03-431
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-270

### Title

Deletion-history integrity invariant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Record deletion MUST preserve sufficient repository history to avoid falsely representing that the logical record never existed.

### Rationale

The retained history may be reduced to minimum verification metadata or a tombstone according to policy.

### Source

- REM-03-432
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-271

### Title

Unknown-field migration invariant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Unknown but valid fields and extensions MUST survive migration without being stripped or altered solely because the receiving implementation does not understand them.

### Rationale

This rule applies to valid unknown data, not malformed or prohibited fields.

### Source

- REM-03-433
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-272

### Title

Projection canonicality invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application projection MUST NOT be treated as a canonical Relay Record unless the controller deliberately causes it to be accepted into the repository.

### Rationale

Derived views, scores and presentation objects remain application state until deliberately saved.

### Source

- REM-03-434
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-273

### Title

Cached-copy identity and provenance invariant

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A cached copy of a Relay Record MUST retain the canonical Record URI and source provenance.

### Rationale

A cache must not relabel itself as the canonical source or detach the copy from its source identity.

### Source

- REM-03-435
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-274

### Title

Index non-ownership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Indexing a public record MUST NOT make the index the canonical owner or authoritative repository of that record.

### Rationale

An index is a discovery or projection layer and remains subordinate to the canonical repository source.

### Source

- REM-03-436
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-275

### Title

Control of Referencing Interaction Records

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A reply, reaction or repost **MUST** remain controlled by the identity that authorised that record.

### Rationale

The referenced-content controller may index, display or moderate the interaction within an application, but does not thereby become its canonical controller.

### Source

- REM-03-437
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

## REL-REC-276

### Title

No Ownership Transfer Through Reference

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A reply, reaction or repost **MUST NOT** become owned by the controller of referenced content merely because it points to that content.

### Rationale

The referenced-content controller may index, display or moderate the interaction within an application, but does not thereby become its canonical controller.

### Source

- REM-03-437
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-426` | Decomposed to preserve distinct normative effects | `REL-REC-263` and `REL-REC-264` |
| `REM-03-427` | Direct | `REL-REC-265` |
| `REM-03-428` | Direct | `REL-REC-266` |
| `REM-03-429` | Direct | `REL-REC-267` |
| `REM-03-430` | Direct | `REL-REC-268` |
| `REM-03-431` | Direct | `REL-REC-269` |
| `REM-03-432` | Direct | `REL-REC-270` |
| `REM-03-433` | Direct | `REL-REC-271` |
| `REM-03-434` | Direct | `REL-REC-272` |
| `REM-03-435` | Direct | `REL-REC-273` |
| `REM-03-436` | Direct | `REL-REC-274` |
| `REM-03-437` | Decomposed to preserve distinct normative effects | `REL-REC-275` and `REL-REC-276` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 44 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-426` through `REM-03-437`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-262`.
- First identifier in this part: `REL-REC-263`.
- Final identifier in this part: `REL-REC-276`.
- Total catalogue requirements in this part: 14.
- Catalogue identifiers remain continuous and unique across Parts 1–41.

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

Part 41 catalogues the settled normative content of Record Model Section 44.

The next catalogue part should address Section 45.
