# EA-05-03 — Record Requirements Catalogue

## Part 2 — Required Envelope Information and Stable Record Identity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the common information required for every active Relay Record and the stability rules governing its Record URI.

It establishes the baseline information that an active record must include or inherit, permits schemas and operations to impose additional requirements, and ensures that a logical record retains one stable Record URI across editing, provider changes, handle changes, application display contexts and media-storage changes.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Sections 4–5 and REM-03 requirements `REM-03-026` through `REM-03-045`.

It defines normative requirements governing:

- the common information every active Relay Record must include or inherit;
- schema- and operation-specific additional fields;
- enforcement of applicable additional requirements;
- the Record URI as the stable identifier of a logical record;
- Record URI stability across record edits;
- Record URI stability across repository-provider changes;
- Record URI stability across identity-handle changes;
- Record URI stability across application display contexts;
- Record URI stability across media-storage changes; and
- the distinction between logical record identity and one particular content version.

Source Section 6 and later sections are intentionally deferred to subsequent catalogue parts.

The common envelope-information list is consolidated into one catalogue requirement because the source states one aggregate `include or inherit` obligation and then enumerates the information governed by that obligation. The consolidation preserves every list item and its REM traceability without implying separate physical fields or repeating the same normative rule twelve times.

---

# 3. Requirements

---

## REL-REC-025

### Title

Required Active-Record Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every active Relay Record **MUST** include or inherit all of the following information:

- its Record URI;
- its Repository Identifier;
- its collection;
- its Record Key;
- its schema identifier;
- its creation time;
- its current update time;
- its authorising Relay Identity;
- its visibility classification;
- its schema-defined content; and
- its integrity reference.

### Rationale

This information is the common baseline required to identify, organise, interpret and verify an active record. Allowing information to be inherited avoids unnecessary duplication while requiring the complete record context to remain unambiguous and available.

### Source

- REM-03-026
- REM-03-027
- REM-03-028
- REM-03-029
- REM-03-030
- REM-03-031
- REM-03-032
- REM-03-033
- REM-03-034
- REM-03-035
- REM-03-036
- REM-03-037
- `design-notes/03-record-model.md`, Section 4

### Related Invariants

- CI-05
- CI-07
- CI-08
- CI-10
- AI-01

---

## REL-REC-026

### Title

Additional Schema- or Operation-Specific Fields

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record schema or record operation **MAY** require additional fields beyond the common active-record information defined by the Record Model.

### Rationale

The common information is a protocol baseline rather than an exhaustive definition of every valid record type or operation. Schemas and operations therefore remain free to define additional information needed for their own semantics and validation.

### Source

- REM-03-038
- `design-notes/03-record-model.md`, Section 4

### Related Invariants

- CI-12
- AI-09

---

## REL-REC-027

### Title

Enforcement of Additional Field Requirements

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An implementation **MUST** enforce any additional field requirement imposed by the applicable record schema or record operation.

### Rationale

Permitting schema- and operation-specific requirements has no interoperable effect unless implementations enforce those requirements when determining whether the applicable record or operation is valid.

### Source

- REM-03-038
- `design-notes/03-record-model.md`, Section 4

### Related Invariants

- CI-08
- AI-09

---

## REL-REC-028

### Title

Stable Logical Record Identifier

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Record URI **MUST** serve as the stable identifier of a logical Relay Record.

### Rationale

A stable protocol identifier allows references to continue identifying the same logical record independently of changes to content, infrastructure, presentation or associated media storage.

### Source

- REM-03-039
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-05

---

## REL-REC-029

### Title

Record URI Stability Across Edits

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Editing a Relay Record **MUST NOT** change the Record URI of the logical record.

### Rationale

An edit changes record state rather than creating a new logical identity. References to the logical record must therefore continue to resolve through the same Record URI.

### Source

- REM-03-040
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-05

---

## REL-REC-030

### Title

Record URI Stability Across Provider Changes

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing the provider of the Relay Repository containing a record **MUST NOT** change the Record URI of the logical record.

### Rationale

Provider migration changes operational hosting, not record identity. Embedding provider dependence into Record URIs would break portable references and repository continuity.

### Source

- REM-03-041
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-03
- CI-05
- AI-04

---

## REL-REC-031

### Title

Record URI Stability Across Handle Changes

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing the handle of the Relay Identity associated with a record **MUST NOT** change the Record URI of the logical record.

### Rationale

Handles are mutable human-readable references. Record identity must remain anchored in stable protocol identity rather than changing when a handle changes.

### Source

- REM-03-042
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-01
- CI-05

---

## REL-REC-032

### Title

Record URI Stability Across Application Display

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Record URI **MUST** remain unchanged when another application displays the record.

### Rationale

An application may present a record through its own interface, but presentation by a different client does not create a new logical record or redefine its canonical identifier.

### Source

- REM-03-043
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-04
- CI-05

---

## REL-REC-033

### Title

Record URI Stability Across Media-Storage Changes

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing the storage location of media associated with a Relay Record **MUST NOT** change the Record URI of the logical record.

### Rationale

Media location is an operational detail that may change independently of the continuing record. The Record URI must therefore remain separate from mutable media-storage locators.

### Source

- REM-03-044
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-05

---

## REL-REC-034

### Title

Logical Record Identity Distinct from Version Identity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Record URI **MUST** identify the continuing logical record rather than only one particular version of its content.

### Rationale

Logical identity must remain stable as record content changes. Identifying a particular historical state is a separate version-reference concern and must not redefine the base Record URI.

### Source

- REM-03-045
- `design-notes/03-record-model.md`, Section 5

### Related Invariants

- CI-05
- CI-10

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-026` | Consolidated aggregate obligation | `REL-REC-025` |
| `REM-03-027` | Consolidated required information | `REL-REC-025` |
| `REM-03-028` | Consolidated required information | `REL-REC-025` |
| `REM-03-029` | Consolidated required information | `REL-REC-025` |
| `REM-03-030` | Consolidated required information | `REL-REC-025` |
| `REM-03-031` | Consolidated required information | `REL-REC-025` |
| `REM-03-032` | Consolidated required information | `REL-REC-025` |
| `REM-03-033` | Consolidated required information | `REL-REC-025` |
| `REM-03-034` | Consolidated required information | `REL-REC-025` |
| `REM-03-035` | Consolidated required information | `REL-REC-025` |
| `REM-03-036` | Consolidated required information | `REL-REC-025` |
| `REM-03-037` | Consolidated required information | `REL-REC-025` |
| `REM-03-038` | Split to preserve independent normative effects | `REL-REC-026`, `REL-REC-027` |
| `REM-03-039` | Direct | `REL-REC-028` |
| `REM-03-040` | Direct | `REL-REC-029` |
| `REM-03-041` | Direct | `REL-REC-030` |
| `REM-03-042` | Direct | `REL-REC-031` |
| `REM-03-043` | Direct | `REL-REC-032` |
| `REM-03-044` | Direct | `REL-REC-033` |
| `REM-03-045` | Direct | `REL-REC-034` |

No REM entry in scope is excluded from normative catalogue generation. `REM-03-026` through `REM-03-037` are consolidated into one complete active-record information requirement. `REM-03-038` is split because its permission for additional fields and its enforcement obligation carry different normative keywords and are independently testable.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Sections 4–5 of `design-notes/03-record-model.md`.
- Source Sections 6–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-026` through `REM-03-045`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-024`.
- First identifier in this part: `REL-REC-025`.
- Final identifier in this part: `REL-REC-034`.
- Total catalogue requirements in this part: 10.
- Catalogue identifiers are continuous and unique across Parts 1–2.

## Traceability verification

- Every REM entry in scope maps to at least one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-026` through `REM-03-037` retain individual traceability through the Source list and coverage table for `REL-REC-025`.
- `REM-03-038` maps to two catalogue requirements to preserve its independently testable `MAY` and `MUST` effects.
- `REM-03-039` through `REM-03-045` remain independently traceable.

## Envelope-information verification

- Every item enumerated by Section 4 is retained in `REL-REC-025`.
- The source qualification that required information may be included or inherited is preserved.
- Consolidation does not require one physical field per information item.
- No example JSON key or final serialisation field name has been inferred.
- The common information remains a baseline rather than an exhaustive schema or operation definition.

## Record-identity verification

- The Record URI remains the stable identifier of the logical record.
- Editing, repository-provider changes, identity-handle changes, display by another application and media-storage changes are all independently accounted for.
- The distinction between the logical record and one particular content version is preserved.
- No example Record URI syntax is promoted into a final wire-format requirement.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- The two normative effects in `REM-03-038` are separated rather than compressed under one keyword.
- No requirement, qualification, exception, schema field or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 2 defines the complete common-information baseline for active Relay Records and the stability of logical record identity. It generates `REL-REC-025` through `REL-REC-034` from `REM-03-026` through `REM-03-045`.

The next catalogue part should begin with source Section 6 and `REM-03-046`.
