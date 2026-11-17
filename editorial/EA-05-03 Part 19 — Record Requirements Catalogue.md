# EA-05-03 — Record Requirements Catalogue

## Part 19 — Tombstones, Data Minimisation and Record-Key Non-Reuse

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the minimum persistent role of a Tombstone, limits its retention of deleted content, prohibits reuse of a deleted Record Key for a different logical record and requires evidence of prior identifier use.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 22 and REM-03 requirements `REM-03-258` through `REM-03-261`.

It defines normative requirements governing:

- persistence of the fact that a logical record previously existed but is no longer active or available;
- minimisation of deleted content retained in a Tombstone;
- non-reuse of a deleted Record Key for a different logical record; and
- preservation of evidence that a deleted record's identifier was previously used.

Source Section 23 and later sections are intentionally deferred to subsequent catalogue parts. No restoration requirement from Section 23 is imported.

The Section 22 JSON is illustrative. Its field names, values, timestamp, version number, hash syntax, identity, structure and example URI do not establish normative Tombstone content or wire syntax and generate no catalogue requirements.

The four in-scope REM entries remain separate because persistence, deleted-content minimisation, Record Key non-reuse and evidence of prior identifier use are independently testable obligations.

---

# 3. Requirements

---

## REL-REC-122

### Title

Minimum Persistent Tombstone

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Tombstone **MUST** be the minimum persistent record indicating both that:

- a logical record previously existed; and
- that logical record is no longer active or available.

### Rationale

A Tombstone preserves the historical existence and current inactive or unavailable state of a logical record without implying retention of the complete deleted record or its full prior content.

### Source

- REM-03-258
- `design-notes/03-record-model.md`, Section 22

### Related Invariants

- CI-08

---

## REL-REC-123

### Title

Deleted-Content Minimisation in Tombstones

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Tombstone **SHOULD** contain no more deleted content than is necessary to preserve repository integrity and prevent identifier reuse.

### Rationale

Deleted-content retention should be minimised while allowing the limited content necessary for repository integrity and identifier history. Tombstone persistence does not itself require retention of the deleted record's full content.

### Source

- REM-03-259
- `design-notes/03-record-model.md`, Section 22

### Related Invariants

- CI-08

---

## REL-REC-124

### Title

No Record Key Reuse for a Different Logical Record

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Record Key previously used by a deleted record **MUST NOT** be reused for a different logical record.

### Rationale

Preventing reassignment of a deleted Record Key protects logical-record identity and identifier history. The prohibition does not prevent continued historical reference to the deleted logical record or preservation of that Record Key in its history.

### Source

- REM-03-260
- `design-notes/03-record-model.md`, Section 22.1

### Related Invariants

- CI-08

---

## REL-REC-125

### Title

Evidence of Prior Identifier Use

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Tombstone **MUST** preserve sufficient evidence that the deleted record's identifier was previously used.

### Rationale

Evidence of prior use supports identifier history and prevents an identifier from appearing unused after deletion. The evidence does not require retention of the deleted content itself or prescribe a particular metadata set, hash mechanism or representation.

### Source

- REM-03-261
- `design-notes/03-record-model.md`, Section 22.1

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-258` | Direct | `REL-REC-122` |
| `REM-03-259` | Direct | `REL-REC-123` |
| `REM-03-260` | Direct | `REL-REC-124` |
| `REM-03-261` | Direct | `REL-REC-125` |

Every REM entry in scope maps directly to one catalogue requirement. No REM entry is consolidated, mapped to an existing catalogue requirement or excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 22 of `design-notes/03-record-model.md`.
- Source Sections 23–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-258` through `REM-03-261`.
- No Section 23 restoration requirement is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-121`.
- First identifier in this part: `REL-REC-122`.
- Final identifier in this part: `REL-REC-125`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–19.

## Traceability verification

- Every REM entry in scope maps directly to one catalogue requirement.
- Every catalogue requirement cites one in-scope REM identifier and the authoritative design-note section or subsection.
- Persistence, deleted-content minimisation, Record Key non-reuse and evidence of prior identifier use remain independently traceable.

## Tombstone persistence verification

- A Tombstone remains the minimum persistent record.
- Prior existence of the logical record and its current inactivity or unavailability remain explicit.
- Tombstone persistence does not imply retention of the complete deleted record or its full prior content.

## Data-minimisation verification

- Deleted-content minimisation retains `SHOULD` strength.
- Preservation of repository integrity and prevention of identifier reuse remain the two explicit purposes for any necessary retained deleted content.
- The recommendation is not strengthened into an unconditional prohibition against retaining minimum necessary content.

## Identifier-history verification

- Deleted Record Key non-reuse retains `MUST NOT` strength and remains limited to reuse for a different logical record.
- Continued historical reference to the deleted logical record is not prohibited.
- The Tombstone preserves sufficient evidence of prior identifier use.
- Evidence of prior use does not require retention of the deleted content itself.

## Illustrative-example and implementation-neutrality verification

- The Section 22 JSON generates no normative catalogue requirement.
- No example field name, value, URI, timestamp, version number, hash syntax, identity or JSON structure is mandatory.
- No hash algorithm, Tombstone schema, minimum metadata set or identifier-history representation is selected or invented.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 19 defines minimum persistent Tombstones, minimises retained deleted content, prohibits cross-record reuse of deleted Record Keys and preserves evidence of prior identifier use.

The next catalogue part should address Section 23 and restoration.
