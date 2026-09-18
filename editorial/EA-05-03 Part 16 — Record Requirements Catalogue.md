# EA-05-03 — Record Requirements Catalogue

## Part 16 — Record Updates, Optimistic Concurrency and Metadata Versioning

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines record-update semantics, the information required to identify an update, recommended optimistic-concurrency safeguards and the permission for metadata-only changes to create a new Record Version.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 19 and REM-03 requirements `REM-03-220` through `REM-03-234`.

It defines normative requirements governing:

- updates to existing logical records;
- identification of an update and its acceptance;
- expected-version declarations and conflict handling;
- prevention of silent overwriting; and
- creation of new Record Versions for metadata-only changes.

Source Section 20 and later sections are intentionally deferred to subsequent catalogue parts. No immutable-record rule is imported.

`REM-03-221` through `REM-03-225` are consolidated because the source presents their five items as the required identifying information for an update. Each item and its applicable qualification remain explicit and individually traceable.

`REM-03-229` through `REM-03-234` are consolidated because the source applies one metadata-versioning permission to six listed change types. Every change type remains explicit, optional and individually traceable.

---

# 3. Requirements

---

## REL-REC-104

### Title

Update of an Existing Logical Record

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A record update **MUST** operate on an existing logical record and **MUST** change that record's content, metadata or both.

### Rationale

An update produces a changed state of the continuing logical record rather than creating a different logical record merely because a new Record Version results.

### Source

- REM-03-220
- `design-notes/03-record-model.md`, Section 19

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-105

### Title

Update Identification and Acceptance Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An update operation **MUST** identify:

- the Record URI of the continuing logical record;
- the Record Version being replaced;
- the proposed new content where the update changes content;
- the authority authorising the update; and
- for an accepted update, the repository commit that accepted it.

### Rationale

These elements distinguish the continuing logical record, the prior version, the proposed changed state, the authority for the operation and the canonical repository-history event that accepts the update. The content qualification preserves metadata-only updates without requiring replacement primary content.

### Source

- REM-03-221
- REM-03-222
- REM-03-223
- REM-03-224
- REM-03-225
- `design-notes/03-record-model.md`, Section 19

### Related Invariants

- CI-06
- CI-07
- CI-08
- AI-01

---

## REL-REC-106

### Title

Expected Current Version Declaration

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An update operation **SHOULD** state which current Record Version it expects to replace.

### Rationale

Declaring the expected current version supports optimistic concurrency while preserving the source's recommended rather than unconditional treatment.

### Source

- REM-03-226
- `design-notes/03-record-model.md`, Section 19.1

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-107

### Title

Conflicting Update Handling

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where the repository's current Record Version differs from the version expected by an update, the repository **SHOULD** reject the update or require explicit conflict resolution.

### Rationale

Either permitted response exposes the version conflict instead of silently applying a stale update, without selecting one response as universally mandatory.

### Source

- REM-03-227
- `design-notes/03-record-model.md`, Section 19.1

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-108

### Title

Prevention of Silent Overwriting

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The update process **SHOULD** prevent an update from silently overwriting a newer accepted Record Version.

### Rationale

Preventing silent overwrite protects accepted repository history while retaining the source's recommendation-level strength.

### Source

- REM-03-228
- `design-notes/03-record-model.md`, Section 19.1

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-109

### Title

Metadata-Only Record Versioning

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A change to any of the following **MAY** create a new Record Version even where the primary content remains unchanged:

- record visibility;
- record audience;
- record rights;
- record title;
- record labels; or
- record blob references.

### Rationale

Material metadata changes may be preserved as versioned changes to the same logical record without requiring a change to its primary content or Record URI.

### Source

- REM-03-229
- REM-03-230
- REM-03-231
- REM-03-232
- REM-03-233
- REM-03-234
- `design-notes/03-record-model.md`, Section 19.2

### Related Invariants

- CI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-220` | Direct | `REL-REC-104` |
| `REM-03-221` | Consolidated update-identification element | `REL-REC-105` |
| `REM-03-222` | Consolidated update-identification element | `REL-REC-105` |
| `REM-03-223` | Consolidated update-identification element | `REL-REC-105` |
| `REM-03-224` | Consolidated update-identification element | `REL-REC-105` |
| `REM-03-225` | Consolidated update-identification element | `REL-REC-105` |
| `REM-03-226` | Direct | `REL-REC-106` |
| `REM-03-227` | Direct | `REL-REC-107` |
| `REM-03-228` | Direct | `REL-REC-108` |
| `REM-03-229` | Consolidated metadata-versioning permission | `REL-REC-109` |
| `REM-03-230` | Consolidated metadata-versioning permission | `REL-REC-109` |
| `REM-03-231` | Consolidated metadata-versioning permission | `REL-REC-109` |
| `REM-03-232` | Consolidated metadata-versioning permission | `REL-REC-109` |
| `REM-03-233` | Consolidated metadata-versioning permission | `REL-REC-109` |
| `REM-03-234` | Consolidated metadata-versioning permission | `REL-REC-109` |

Every REM entry in scope maps directly or through justified consolidation to one catalogue requirement. No REM entry in this part is excluded because of non-normative status. The Section 19 JSON is illustrative and generates no catalogue requirement.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 19 of `design-notes/03-record-model.md`.
- Source Sections 20–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-220` through `REM-03-234`.
- No immutable-record requirement from Section 20 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-103`.
- First identifier in this part: `REL-REC-104`.
- Final identifier in this part: `REL-REC-109`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–16.

## Traceability verification

- Every REM entry in scope maps directly or through justified consolidation to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- All five update-identification elements retain individual traceability through the Source list and coverage table for `REL-REC-105`.
- All six metadata-only change types retain individual traceability through the Source list and coverage table for `REL-REC-109`.

## Logical-record and update-identification verification

- An update operates on an existing logical record and changes its content, metadata or both.
- A new Record Version is not treated as a new logical record.
- The Record URI, replaced version, conditionally applicable new content, authorising authority and accepting repository commit remain explicit and independently traceable.
- New content is required where content changes and is not imposed on a metadata-only update.
- The continuing logical record, replaced version, proposed changed state and accepting commit remain distinct.

## Optimistic-concurrency verification

- Expected-current-version declaration retains `SHOULD` strength.
- Conflict rejection or explicit resolution retains `SHOULD` strength and both responses remain available.
- Prevention of silent overwriting retains `SHOULD` strength as an independently testable effect.
- No optimistic-concurrency recommendation is strengthened into an unconditional requirement.

## Metadata-versioning verification

- Visibility, audience, rights, title, labels and blob references remain explicit and individually traceable.
- Creation of a new Record Version for any listed metadata-only change retains `MAY` strength.
- No listed metadata change is required to create a version.
- Metadata-only versioning does not change the logical Record URI.

## Illustrative-example and implementation-neutrality verification

- The Section 19 JSON generates no normative catalogue requirement.
- `record`, `expectedVersion`, `newContent` and `text` are not made mandatory physical field names.
- The example Record URI, version numbers and content are not treated as final wire syntax.
- No conflict-resolution mechanism, field name, commit format or implementation detail is invented.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- No immutable-record rule, terminology, qualification or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 16 defines updates to continuing logical records, preserves explicit update and acceptance information, recommends optimistic-concurrency safeguards and permits metadata-only changes to create new Record Versions.

The next catalogue part should address Section 20 and immutable records.
