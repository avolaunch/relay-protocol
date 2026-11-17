# EA-05-03 — Record Requirements Catalogue

## Part 36 — Record conflict

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 39, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 39 and REM-03 entries `REM-03-382` through `REM-03-389`.

Source Section 40 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-222

### Title

Conflict definition

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An implementation **MUST** recognise a record conflict when two or more update operations attempt to replace the same current Record Version.

### Rationale

The requirement applies regardless of whether the updates originate from the same or different applications.

### Source

- REM-03-382
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

- CI-07

---

## REL-REC-223

### Title

No silent dual linear acceptance

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The repository **MUST NOT** silently accept conflicting updates as though both formed one unambiguous linear continuation of the record history.

### Rationale

The repository must expose or resolve the conflict through an explicit outcome.

### Source

- REM-03-383
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

- CI-10
- AI-01

---

## REL-REC-224

### Title

Conflict outcome: reject later submission

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A repository **MAY** resolve a record conflict by rejecting the later conflicting submission.

### Rationale

Rejection should provide sufficient information for the application or user to understand that the expected version was no longer current.

### Source

- REM-03-384
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

None identified.

---

## REL-REC-225

### Title

Conflict outcome: request user review

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

A repository or application **MAY** require user review before resolving a record conflict.

### Rationale

User review is particularly appropriate where neither update can safely be discarded automatically.

### Source

- REM-03-385
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

None identified.

---

## REL-REC-226

### Title

Conflict outcome: reconciled version

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A conflict-resolution process **MAY** create a new reconciled Record Version.

### Rationale

The reconciled version is a new accepted state and must not retroactively rewrite the conflicting proposals as though no conflict occurred.

### Source

- REM-03-386
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

None identified.

---

## REL-REC-227

### Title

Conflict outcome: preserve candidates

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A repository **MAY** preserve conflicting proposed versions as separately identifiable conflict candidates.

### Rationale

Candidate preservation allows later review without presenting both candidates as the single current version.

### Source

- REM-03-387
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

None identified.

---

## REL-REC-228

### Title

Application-assisted merge

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

For text or other mergeable record formats, an application **MAY** offer a merge of conflicting proposals.

### Rationale

The ability to merge is format- and schema-dependent.

### Source

- REM-03-388
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

None identified.

---

## REL-REC-229

### Title

Explicit authorisation of merged record

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A merged record produced during conflict resolution **MUST** receive explicit valid authorisation before it becomes an accepted current Record Version.

### Rationale

Technical merge success does not substitute for repository authority or controller approval.

### Source

- REM-03-389
- `design-notes/03-record-model.md`, Section 39

### Related Invariants

- CI-02
- CI-06
- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-382` | Direct | `REL-REC-222` |
| `REM-03-383` | Direct | `REL-REC-223` |
| `REM-03-384` | Direct | `REL-REC-224` |
| `REM-03-385` | Direct | `REL-REC-225` |
| `REM-03-386` | Direct | `REL-REC-226` |
| `REM-03-387` | Direct | `REL-REC-227` |
| `REM-03-388` | Direct | `REL-REC-228` |
| `REM-03-389` | Direct | `REL-REC-229` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 39 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-382` through `REM-03-389`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-221`.
- First identifier in this part: `REL-REC-222`.
- Final identifier in this part: `REL-REC-229`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–36.

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

Part 36 catalogues the settled normative content of Record Model Section 39.

The next catalogue part should address Section 40.
