# EA-05-03 — Record Requirements Catalogue

## Part 18 — Record Deletion Modes and Distinct State Semantics

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines canonical record deletion as an authorised repository operation, the information required to identify a deletion and the distinct semantics of the five source-defined deletion states.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 21 and REM-03 requirements `REM-03-245` through `REM-03-257`.

It defines normative requirements governing:

- repository authority for record deletion;
- deletion identification and acceptance information;
- soft deletion, content erasure, expiring deletion, legal restriction and provider removal; and
- distinct presentation of those deletion states.

Source Section 22 and later sections are intentionally deferred to subsequent catalogue parts. The applicable tombstone requirements must be identified, but their detailed content is not defined in this part.

`REM-03-246` through `REM-03-251` are consolidated because the source presents their six items as the required identifying information for a deletion operation. Each item remains explicit and individually traceable.

`REM-03-256` contains two independently testable effects with different normative keywords and is decomposed into separate requirements for provider refusal and the absence of a necessary canonical-history implication.

---

# 3. Requirements

---

## REL-REC-113

### Title

Deletion as an Authorised Repository Operation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Deleting a Relay Record **MUST** be performed as an authorised operation of the authoritative Relay Repository.

### Rationale

Canonical deletion changes repository-governed record state; hiding or removing an application's local representation does not itself perform that operation.

### Source

- REM-03-245
- `design-notes/03-record-model.md`, Section 21

### Related Invariants

- CI-06
- AI-01

---

## REL-REC-114

### Title

Deletion Identification and Acceptance Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A deletion operation **MUST** identify:

- the Record URI of the logical record being deleted;
- the Record Version to which deletion applies;
- the time at which deletion became accepted repository state;
- the authority authorising the deletion;
- the deletion mode being applied; and
- the tombstone requirements applicable to the deleted record.

### Rationale

These elements identify the logical record, affected version, accepted deletion event, authority, state semantics and applicable persistence obligations without prescribing the detailed tombstone contents defined elsewhere.

### Source

- REM-03-246
- REM-03-247
- REM-03-248
- REM-03-249
- REM-03-250
- REM-03-251
- `design-notes/03-record-model.md`, Section 21

### Related Invariants

- CI-06
- CI-07
- CI-08
- AI-01

---

## REL-REC-115

### Title

Soft-Deletion Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A soft-deletion state **MUST** mean that the active record is hidden while the provider retains its prior content.

### Rationale

Soft deletion changes active visibility without representing the retained content as erased.

### Source

- REM-03-252
- `design-notes/03-record-model.md`, Section 21, **Soft deletion**

### Related Invariants

- CI-08

---

## REL-REC-116

### Title

Content-Erasure Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A content-erasure state **MUST** remove the prior record content while retaining minimum verification metadata.

### Rationale

Content erasure removes prior content but preserves the minimum metadata needed to maintain verifiability. This section does not define the complete minimum metadata set.

### Source

- REM-03-253
- `design-notes/03-record-model.md`, Section 21, **Content erasure**

### Related Invariants

- CI-08

---

## REL-REC-117

### Title

Expiring-Deletion Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An expiring-deletion state **MUST** specify a date after which the record becomes unavailable.

### Rationale

The stated date distinguishes scheduled unavailability from immediate deletion or another access state.

### Source

- REM-03-254
- `design-notes/03-record-model.md`, Section 21, **Expiring deletion**

### Related Invariants

- CI-08

---

## REL-REC-118

### Title

Legal-Restriction Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A legal-restriction state **MUST** indicate that record content is being withheld because of a legal or regulatory requirement.

### Rationale

Legal restriction communicates the basis for withholding content without representing that state as necessarily equivalent to erasure or canonical deletion.

### Source

- REM-03-255
- `design-notes/03-record-model.md`, Section 21, **Legal restriction**

### Related Invariants

- CI-08

---

## REL-REC-119

### Title

Provider-Removal Service Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A provider-removal state **MUST** indicate that the current provider refuses to serve the record.

### Rationale

Provider removal describes the current provider's service behaviour rather than, by itself, a protocol-level deletion of the record.

### Source

- REM-03-256
- `design-notes/03-record-model.md`, Section 21, **Provider removal**

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-120

### Title

Provider Removal Does Not Necessarily Change Canonical History

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A provider-removal state **MUST NOT** imply that canonical repository history has necessarily changed.

### Rationale

A provider's refusal to serve a record is distinct from an authorised operation that changes canonical repository history.

### Source

- REM-03-256
- `design-notes/03-record-model.md`, Section 21, **Provider removal**

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-121

### Title

Distinct Presentation of Deletion States

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Implementations **MUST NOT** present soft deletion, content erasure, expiring deletion, legal restriction and provider removal as equivalent states.

### Rationale

The five states have materially different consequences for content retention, availability, verification and canonical repository history and must remain distinguishable.

### Source

- REM-03-257
- `design-notes/03-record-model.md`, Section 21

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-245` | Direct | `REL-REC-113` |
| `REM-03-246` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-247` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-248` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-249` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-250` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-251` | Consolidated deletion-information element | `REL-REC-114` |
| `REM-03-252` | Direct | `REL-REC-115` |
| `REM-03-253` | Direct | `REL-REC-116` |
| `REM-03-254` | Direct | `REL-REC-117` |
| `REM-03-255` | Direct | `REL-REC-118` |
| `REM-03-256` | Decomposed to preserve distinct normative effects | `REL-REC-119` and `REL-REC-120` |
| `REM-03-257` | Direct | `REL-REC-121` |

Every REM entry in scope maps directly, through justified consolidation or through justified decomposition to a catalogue requirement. No REM entry in this part is excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 21 of `design-notes/03-record-model.md`.
- Source Sections 22–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-245` through `REM-03-257`.
- No detailed tombstone-content requirement from Section 22 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-112`.
- First identifier in this part: `REL-REC-113`.
- Final identifier in this part: `REL-REC-121`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers are continuous and unique across Parts 1–18.

## Traceability verification

- Every REM entry in scope maps directly, through justified consolidation or through justified decomposition to a catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- All six deletion-information items retain individual traceability through the Source list and coverage table for `REL-REC-114`.
- Both normative effects extracted in `REM-03-256` remain traceable through `REL-REC-119` and `REL-REC-120`.

## Deletion-authority and information verification

- Canonical record deletion remains an authorised operation of the authoritative Relay Repository.
- Application-local hiding or removal is not treated as canonical deletion.
- Record URI, affected Record Version, accepted deletion time, authorising authority, deletion mode and applicable tombstone requirements remain explicit and independently traceable.
- Deletion time remains tied to accepted repository state rather than local request creation.
- The logical Record URI remains distinct from the Record Version to which deletion applies.

## Deletion-mode verification

- Soft deletion, content erasure, expiring deletion, legal restriction and provider removal remain distinct and independently traceable.
- Soft deletion hides the active record while retaining prior content and is not treated as content erasure.
- Content erasure removes prior content while retaining minimum verification metadata without inventing the complete metadata set.
- Expiring deletion specifies the date after which the record becomes unavailable.
- Legal restriction remains tied to a legal or regulatory requirement and is not treated as necessarily equivalent to erasure or canonical deletion.
- Provider removal describes current-provider refusal without necessarily changing canonical repository history.

## State-distinction verification

- The five deletion states are not presented as equivalent or collapsed into one undifferentiated deleted state.
- Provider refusal remains distinct from protocol-level deletion.
- No mode is represented as having consequences that belong only to another mode.

## Implementation-neutrality verification

- No deletion mechanism, authorisation mechanism, tombstone content, physical field, state-transition procedure or provider behaviour beyond the source is invented.
- No detailed Section 22 tombstone requirement is imported.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 18 defines authorised record deletion, preserves the required deletion information and keeps all five deletion states semantically distinct.

The next catalogue part should address Section 22 and tombstones.
