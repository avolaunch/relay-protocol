# EA-05-03 — Record Requirements Catalogue

## Part 14 — Canonical Record Creation and Repository Acceptance

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the conditions under which a record creation operation produces a canonical Relay Record and preserves the boundary between an application-local object and repository-accepted canonical state.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 17 and REM-03 requirements `REM-03-185` through `REM-03-192`.

It defines normative requirements governing:

- the complete set of conditions required to create a canonical Relay Record; and
- the inability of application-local generation alone to establish canonical state.

Source Section 18 and later sections are intentionally deferred to subsequent catalogue parts. No validation layer, detailed validation check or validation example from Section 18 is imported.

`REM-03-185` through `REM-03-190` are consolidated because the source presents their six conditions as one conjunctive record-creation rule. Every condition remains explicit and individually traceable.

`REM-03-192` restates the repository-acceptance boundary already catalogued by `REL-REC-003` and is accounted for through cross-part consolidation rather than a duplicate Part 14 requirement.

---

# 3. Requirements

---

## REL-REC-095

### Title

Canonical Record Creation Conditions

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Creating a canonical Relay Record **MUST** require all of the following:

- a valid schema;
- a Record Key that is unique within the applicable repository and collection scope;
- content that passes validation against the declared schema;
- a valid visibility classification;
- valid repository authority for the creation operation; and
- inclusion of the creation operation in an accepted repository commit.

### Rationale

Canonical creation depends on the complete conjunction of validity, authority and repository-acceptance conditions without prescribing the detailed validation or implementation mechanisms defined elsewhere.

### Source

- REM-03-185
- REM-03-186
- REM-03-187
- REM-03-188
- REM-03-189
- REM-03-190
- `design-notes/03-record-model.md`, Section 17

### Related Invariants

- CI-07
- CI-08
- AI-01

---

## REL-REC-096

### Title

Local Application Generation Does Not Establish Canonical State

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A locally generated application object **MUST NOT** be treated as a canonical Relay Record solely because an application created it.

### Rationale

Application-local generation can create an object for submission or proposal, but it does not itself provide repository authority, an accepted commit or canonical repository state.

### Source

- REM-03-191
- `design-notes/03-record-model.md`, Section 17

### Related Invariants

- CI-04
- CI-07
- AI-01

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-185` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-186` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-187` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-188` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-189` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-190` | Consolidated canonical-creation condition | `REL-REC-095` |
| `REM-03-191` | Direct | `REL-REC-096` |
| `REM-03-192` | Cross-part consolidation | Existing `REL-REC-003` already preserves repository acceptance as the boundary for canonical Relay Record status. |

Every normative REM entry in scope maps to a catalogue requirement. No REM entry in this part is excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 17 of `design-notes/03-record-model.md`.
- Source Sections 18–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-185` through `REM-03-192`.
- No Section 18 validation layer, detailed check or example is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-094`.
- First identifier in this part: `REL-REC-095`.
- Final identifier in this part: `REL-REC-096`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers are continuous and unique across Parts 1–14.

## Traceability verification

- Every normative REM entry in scope maps to a new or existing catalogue requirement.
- Every new catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-185` through `REM-03-190` retain individual traceability through the Source list and coverage table for `REL-REC-095`.
- `REM-03-192` is explicitly accounted for through cross-part consolidation into existing `REL-REC-003`.

## Canonical-creation verification

- All six canonical-record creation conditions remain explicit and independently traceable.
- Record Key uniqueness remains limited to the applicable repository and collection scope; no global uniqueness requirement is introduced.
- Application-local generation is not treated as canonical creation.
- Application generation does not itself supply repository authority or an accepted repository commit.
- Existing `REL-REC-003` preserves repository acceptance as the transition to canonical state without duplicating that rule in Part 14.

## Implementation-neutrality verification

- No schema-resolution rule, Record Key generation method, validation procedure, authority mechanism, commit format or repository workflow is invented.
- No Section 18 validation level, check or illustrative criterion is flattened into a Part 14 requirement.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 14 establishes the complete source-defined conditions for canonical record creation and preserves repository acceptance as the transition from an application-local object to canonical Relay state.

The next catalogue part should address Section 18 and the layered record-validation model while retaining its illustrative validation checks as explicitly non-normative examples.
