# EA-05-03 — Record Requirements Catalogue

## Part 3 — Record Versioning, Historical References and Current State

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how accepted record changes create Record Versions, how versions may be identified, how historical-version references differ from the continuing logical Record URI and how repositories and applications represent current or potentially stale state.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 6 and REM-03 requirements `REM-03-046` through `REM-03-056`.

It defines normative requirements governing:

- creation of a new Record Version for each accepted change;
- permitted Record Version identification mechanisms;
- separate identification of a particular historical state;
- semantic separation between logical-record and historical-version references;
- authoritative repository indication of the current version; and
- application disclosure when an older cached version may be stale.

Source Section 7 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-051` restates the Section 5 logical-identity rule already catalogued as `REL-REC-034` and is therefore accounted for through cross-part consolidation rather than a duplicate requirement. `REM-03-054` is an explicit Non-normative open-design note and does not generate a catalogue requirement.

---

# 3. Requirements

---

## REL-REC-035

### Title

New Version for Each Accepted Change

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Each change to a Relay Record accepted by the authoritative Relay Repository **MUST** create a new Record Version.

### Rationale

Tying version creation to repository acceptance distinguishes canonical version history from local or unaccepted edits and preserves an auditable sequence of accepted record states.

### Source

- REM-03-046
- `design-notes/03-record-model.md`, Section 6

### Related Invariants

- CI-07
- CI-10
- AI-02

---

## REL-REC-036

### Title

Permitted Record Version Identification Mechanisms

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Record Version **MAY** be identified by:

- the repository commit in which the version was accepted;
- a monotonically increasing version number;
- a content hash; or
- a combination of those mechanisms.

### Rationale

The source permits multiple compatible identification approaches without requiring any one approach to be the sole or universal mechanism. Combining mechanisms may support ordering, repository traceability and content verification while leaving the final technical choices open.

### Source

- REM-03-047
- REM-03-048
- REM-03-049
- REM-03-050
- `design-notes/03-record-model.md`, Section 6

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-037

### Title

Historical Version Reference

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A version reference **MUST** identify one particular historical state of a logical Relay Record.

### Rationale

A historical reference requires a stable meaning distinct from a reference to the continuing logical record, allowing a specific accepted state to be identified even after later versions exist.

### Source

- REM-03-052
- `design-notes/03-record-model.md`, Section 6.1

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-038

### Title

Logical and Historical Reference Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Implementations **MUST** preserve a clear semantic distinction between a reference to the continuing logical record and a reference to one particular historical Record Version.

### Rationale

Conflating the two reference forms would make it unclear whether a reference follows the record's current state or remains fixed to an earlier accepted state.

### Source

- REM-03-053
- `design-notes/03-record-model.md`, Section 6.1

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-039

### Title

Authoritative Current-Version Indication

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The authoritative Relay Repository **MUST** clearly indicate which accepted Record Version is current for each logical record.

### Rationale

An unambiguous current-version indication allows applications to distinguish authoritative current state from historical or locally cached states.

### Source

- REM-03-055
- `design-notes/03-record-model.md`, Section 6.2

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-040

### Title

Stale Cached-Version Disclosure

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** treat an older cached Record Version as current unless it clearly identifies that the cached version may be stale.

### Rationale

Cached and offline use remains permitted, but an application must not represent uncertain cached state as authoritative current state without disclosing that uncertainty.

### Source

- REM-03-056
- `design-notes/03-record-model.md`, Section 6.2

### Related Invariants

- CI-08
- AI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-046` | Direct | `REL-REC-035` |
| `REM-03-047` | Consolidated permitted mechanism | `REL-REC-036` |
| `REM-03-048` | Consolidated permitted mechanism | `REL-REC-036` |
| `REM-03-049` | Consolidated permitted mechanism | `REL-REC-036` |
| `REM-03-050` | Consolidated permitted combination | `REL-REC-036` |
| `REM-03-051` | Cross-part consolidation; no duplicate requirement generated | Existing `REL-REC-034` |
| `REM-03-052` | Direct | `REL-REC-037` |
| `REM-03-053` | Direct | `REL-REC-038` |
| `REM-03-054` | Excluded from normative catalogue generation | Explicit Non-normative open-design note; exact version-reference syntax remains open |
| `REM-03-055` | Direct | `REL-REC-039` |
| `REM-03-056` | Direct | `REL-REC-040` |

`REM-03-047` through `REM-03-050` are consolidated because the source presents four alternatives under one permission to identify a version. The consolidation preserves the optional status of every mechanism. `REM-03-051` is already represented by `REL-REC-034`, which states that the Record URI identifies the continuing logical record rather than only one content version.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 6 of `design-notes/03-record-model.md`.
- Source Sections 7–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-046` through `REM-03-056`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-034`.
- First identifier in this part: `REL-REC-035`.
- Final identifier in this part: `REL-REC-040`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–3.

## Traceability verification

- Every normative REM entry in scope maps to a new requirement or the existing `REL-REC-034` requirement.
- Every new catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note subsection.
- `REM-03-047` through `REM-03-050` retain individual traceability through the Source list and coverage table for `REL-REC-036`.
- `REM-03-051` is explicitly accounted for through cross-part consolidation into `REL-REC-034`.

## Version-identification verification

- Commit identity, monotonic version number, content hash and a combination of those mechanisms remain permitted alternatives.
- No identification mechanism is made mandatory, exclusive or preferred.
- No final hash algorithm is selected.
- The example version object creates no final field-name or serialisation requirement.

## Reference-semantics verification

- The Record URI continues to identify the logical record through `REL-REC-034`.
- A version reference identifies one particular historical state through `REL-REC-037`.
- `REL-REC-038` preserves the semantic distinction between those reference forms.
- `REM-03-054` generates no normative catalogue requirement.
- The example `?version=3` form is not treated as final, exclusive or selected syntax.

## Current-state verification

- The authoritative repository must clearly identify the current accepted version.
- An application must not treat an older cached version as current without identifying that it may be stale.
- Cached and offline use is not prohibited.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No requirement, qualification, algorithm, syntax or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 3 defines Record Version creation, permitted version-identification mechanisms, historical reference semantics, current-version indication and stale-cache disclosure. It generates `REL-REC-035` through `REL-REC-040` from normative material in `REM-03-046` through `REM-03-056`, while accounting for one cross-part consolidation and excluding the non-normative open syntax note.

The next catalogue part should begin with source Section 7 and `REM-03-057`.
