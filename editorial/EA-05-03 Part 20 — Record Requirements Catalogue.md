# EA-05-03 — Record Requirements Catalogue

## Part 20 — Record Restoration and Preservation of Deletion History

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the conditions for restoring a deleted record, creation of a new current version and preservation of the prior deletion event in repository history.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 23 and REM-03 requirements `REM-03-262` through `REM-03-267`.

It defines normative requirements governing schema permission, continued content availability, controller authorisation, repository recording, version creation and historical integrity during restoration.

Source Section 24 and later sections are intentionally deferred to subsequent catalogue parts. No expiration requirement from Section 24 is imported.

`REM-03-262` through `REM-03-265` are consolidated because the source states one restoration permission conditioned on four cumulative criteria. Each criterion remains explicit and individually traceable.

---

# 3. Requirements

---

## REL-REC-126

### Title

Conditions for Record Restoration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A deleted record **MAY** be restored only if:

- the applicable schema permits restoration;
- the deleted content remains available;
- the controller authorises restoration; and
- a new commit records the restoration operation.

### Rationale

Restoration is optional and requires all four source-defined conditions. This requirement does not prescribe storage, recovery, authorisation or commit mechanisms.

### Source

- REM-03-262
- REM-03-263
- REM-03-264
- REM-03-265
- `design-notes/03-record-model.md`, Section 23

### Related Invariants

- CI-06
- CI-07
- CI-08
- AI-01

---

## REL-REC-127

### Title

Restoration Creates a New Current Version

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Successful restoration **MUST** create a new current Record Version.

### Rationale

A restored record re-enters current state through a new version rather than silently reverting the current pointer to an earlier version.

### Source

- REM-03-266
- `design-notes/03-record-model.md`, Section 23

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-128

### Title

Preservation of Deletion History

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Restoration **MUST NOT** erase or conceal the prior deletion event from repository history.

### Rationale

Deletion and restoration remain distinct historical events, preserving repository integrity and auditability.

### Source

- REM-03-267
- `design-notes/03-record-model.md`, Section 23

### Related Invariants

- CI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-262` | Consolidated restoration condition | `REL-REC-126` |
| `REM-03-263` | Consolidated restoration condition | `REL-REC-126` |
| `REM-03-264` | Consolidated restoration condition | `REL-REC-126` |
| `REM-03-265` | Consolidated restoration condition | `REL-REC-126` |
| `REM-03-266` | Direct | `REL-REC-127` |
| `REM-03-267` | Direct | `REL-REC-128` |

Every REM entry in scope maps directly or through justified consolidation to a catalogue requirement. No REM entry is excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 23 of `design-notes/03-record-model.md`.
- Source Sections 24–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-262` through `REM-03-267`.
- No expiration requirement from Section 24 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-125`.
- First identifier in this part: `REL-REC-126`.
- Final identifier in this part: `REL-REC-128`.
- Total catalogue requirements in this part: 3.
- Catalogue identifiers are continuous and unique across Parts 1–20.

## Traceability verification

- Every in-scope normative REM entry is represented directly or through justified consolidation.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- All four restoration conditions retain individual traceability through the Source list and coverage table for `REL-REC-126`.

## Restoration-condition verification

- Restoration remains permitted rather than universally required.
- Schema permission, deleted-content availability, controller authorisation and recording in a new commit remain explicit and cumulative.
- No storage, backup, recovery, authorisation or commit mechanism is invented.

## Version and history verification

- Restoration creates a new current Record Version.
- Restoration does not silently revert the current pointer to an earlier version.
- The prior deletion event remains visible in repository history and is neither erased nor concealed.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 20 defines conditional restoration, requires a new current version and preserves the prior deletion event in repository history.

The next catalogue part should address Section 24.
