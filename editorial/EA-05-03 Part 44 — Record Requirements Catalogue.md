# EA-05-03 — Record Requirements Catalogue

## Part 44 — Provisional decisions for v0.1

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 47, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 47 and REM-03 entries `REM-03-466` through `REM-03-482`.

Source Section 48 and later sections are intentionally deferred to subsequent catalogue parts.

All requirements in this part retain the source status **PROVISIONAL v0.1** and remain subject to later resolution and specification refinement.

---

# 3. Requirements

---

## REL-REC-295

### Title

JSON-compatible structured records

**Level:** Architectural

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 SHOULD provisionally represent records using a JSON-compatible structured data model.

### Rationale

This establishes data-model compatibility, not necessarily one final canonical byte-level serialisation.

### Source

- REM-03-466
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-296

### Title

Stable Record URIs

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally use stable Record URIs for the persistent identity of logical records.

### Rationale

This assumption is consistent with the record invariants and the core record principle.

### Source

- REM-03-467
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-297

### Title

Versioned schemas

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally support explicit schema versioning.

### Rationale

Schema identifiers should make the applicable schema version determinable.

### Source

- REM-03-468
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-298

### Title

One current version per logical record

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally maintain exactly one authoritative current version for each active logical record.

### Rationale

Conflicting proposed versions may be preserved as candidates, but they must not both be silently treated as one linear current continuation.

### Source

- REM-03-469
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-299

### Title

Optimistic concurrency checks

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally use optimistic concurrency checks for record updates.

### Rationale

An update should identify the version it expects to replace so stale updates can be rejected or explicitly reconciled.

### Source

- REM-03-470
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-300

### Title

Signed commits as minimum authority proof

**Level:** Constitutional

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally treat a valid signed repository commit as the minimum authority proof for an accepted record operation.

### Rationale

This does not preclude stronger or additional signatures where required by a schema or assertion type.

### Source

- REM-03-471
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-301

### Title

Optional signatures for externally issued assertions

**Level:** Architectural

**Normative Keyword:** **MAY**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MAY provisionally support individual record signatures for externally issued assertions in addition to signed repository commits.

### Rationale

The signature preserves the issuer’s claim independently of the holder repository’s authority to store the assertion.

### Source

- REM-03-472
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-302

### Title

Four visibility classifications

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 SHOULD provisionally support public, unlisted, restricted and private record visibility classifications.

### Rationale

These classifications do not by themselves determine usage rights or legal ownership.

### Source

- REM-03-473
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-303

### Title

Logical deletion with tombstones

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally support logical deletion represented through tombstones or equivalent minimum persistent deletion records.

### Rationale

The retained tombstone should preserve only the information necessary for integrity, deletion history and identifier non-reuse.

### Source

- REM-03-474
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-304

### Title

No reuse of deleted Record Keys

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally prohibit reuse of a deleted Record Key for a different logical record.

### Rationale

The associated tombstone preserves evidence that the identifier has already been used.

### Source

- REM-03-475
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-305

### Title

Content-addressed blob references

**Level:** Constitutional

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally identify referenced blobs through content-addressed identifiers rather than treating temporary storage URLs as permanent blob identity.

### Rationale

Temporary retrieval locations may change without changing the blob’s logical content identity.

### Source

- REM-03-476
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-306

### Title

Structured provenance

**Level:** Architectural

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 SHOULD provisionally support structured record provenance.

### Rationale

Provenance declarations must continue to distinguish declared origin from independently verified authenticity.

### Source

- REM-03-477
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-307

### Title

Preservation of unknown fields and schemas

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally preserve valid but unknown fields, extensions and record schemas during storage, migration and round-trip processing.

### Rationale

An implementation may decline to render or interpret an unknown type but must not damage or discard it solely because it is unknown.

### Source

- REM-03-478
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-308

### Title

Acting-identity storage for replies, reactions and reposts

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 SHOULD provisionally store replies, reactions and reposts in the repository of the identity that authorised the respective action record.

### Rationale

The repository of the referenced content may index or display these records but does not become their canonical owner.

### Source

- REM-03-479
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-309

### Title

Projections remain non-canonical unless explicitly saved

**Level:** Constitutional

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally treat application projections as non-canonical unless the controller explicitly saves and authorises them as repository records.

### Rationale

Derived views, cards, rankings and recommendations must not automatically pollute the person’s canonical repository history.

### Source

- REM-03-480
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-310

### Title

Moderation labels as separate records

**Level:** Architectural

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 SHOULD provisionally represent moderation labels as records separate from the target record.

### Rationale

A moderation label does not rewrite the target record and may be trusted or ignored according to application policy.

### Source

- REM-03-481
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

## REL-REC-311

### Title

Schema rules layered over a common envelope

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 MUST provisionally apply schema-specific content and behaviour rules on top of a common protocol-level Record Envelope.

### Rationale

This preserves common identification, authority, visibility and integrity semantics while allowing schema-specific extensibility.

### Source

- REM-03-482
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-466` | Direct | `REL-REC-295` |
| `REM-03-467` | Direct | `REL-REC-296` |
| `REM-03-468` | Direct | `REL-REC-297` |
| `REM-03-469` | Direct | `REL-REC-298` |
| `REM-03-470` | Direct | `REL-REC-299` |
| `REM-03-471` | Direct | `REL-REC-300` |
| `REM-03-472` | Direct | `REL-REC-301` |
| `REM-03-473` | Direct | `REL-REC-302` |
| `REM-03-474` | Direct | `REL-REC-303` |
| `REM-03-475` | Direct | `REL-REC-304` |
| `REM-03-476` | Direct | `REL-REC-305` |
| `REM-03-477` | Direct | `REL-REC-306` |
| `REM-03-478` | Direct | `REL-REC-307` |
| `REM-03-479` | Direct | `REL-REC-308` |
| `REM-03-480` | Direct | `REL-REC-309` |
| `REM-03-481` | Direct | `REL-REC-310` |
| `REM-03-482` | Direct | `REL-REC-311` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 47 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-466` through `REM-03-482`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-294`.
- First identifier in this part: `REL-REC-295`.
- Final identifier in this part: `REL-REC-311`.
- Total catalogue requirements in this part: 17.
- Catalogue identifiers remain continuous and unique across Parts 1–44.

## Traceability verification

- Every settled normative rule in scope maps directly or through justified decomposition to a catalogue requirement.
- Every generated requirement cites its in-scope REM identifier and authoritative design-note section.
- Every excluded entry remains individually accounted for in the coverage table.

## Source-status and implementation-neutrality verification

- Normative strength and material qualifications are preserved.
- Illustrative examples and open design questions do not become protocol requirements.
- Every generated requirement remains explicitly **PROVISIONAL v0.1**.
- No example vocabulary, physical field, syntax, mechanism or implementation detail is made mandatory unless the source establishes that obligation.
- Extraction Notes are used as rationale only and do not broaden the authoritative source rule.

## Normative-language verification

- Each generated catalogue requirement carries one explicit normative keyword.
- No later-section requirement is imported.

---

# 6. Part conclusion

Part 44 catalogues the settled normative content of Record Model Section 47.

The next catalogue part should address Section 48.
