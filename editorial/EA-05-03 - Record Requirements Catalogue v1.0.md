# EA-05-03 — Record Requirements Catalogue v1.0

**Relay Protocol Editorial Programme**

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Document Status:** Canonical v1.0

**Specification Type:** Normative Requirements Catalogue

---

## Abstract

This document is the canonical Record Requirements Catalogue for the Relay Protocol. It assembles the reviewed requirements in EA-05-03 Parts 1–45 and preserves bidirectional traceability to REM-03 and the authoritative Record Model.

The ten Section 46 open design questions remain explicitly non-normative and unresolved. The seventeen Section 47 requirements remain marked **PROVISIONAL v0.1** under the founder-approved carry-forward disposition recorded after EA-05R-03.

## Catalogue statistics

| Measure | Value |
|---|---:|
| Source sections | 48 |
| REM entries accounted for | 483 |
| Catalogue parts | 45 |
| Normative requirements | 313 |
| Requirement range | REL-REC-001 through REL-REC-313 |
| Non-normative open questions carried forward | 10 |
| Provisional v0.1 requirements | 17 |

## Table of contents

1. Record Foundations, Purpose and Conceptual Structure
2. Required Envelope Information and Stable Record Identity
3. Record Versioning, Historical References and Current State
4. Record Types, Schema Authority and Schema-Defined Behaviour
5. Core Record Categories and Schema Diversity
6. Singleton and Repeatable Record Cardinality
7. Subject, Authority and Submission Role Separation
8. Issued Assertions, Holder Storage and Signed-Claim Integrity
9. Structured Provenance and Provenance Assurance
10. Creation Modes, Authorship Declarations and Evidentiary Limits
11. Record Visibility Classifications and Access Semantics
12. Restricted Audiences, Dynamic Evaluation and Access Revocation
13. Usage-Rights Expression and Enforcement Boundaries
14. Canonical Record Creation and Repository Acceptance
15. Layered Record Validation and Protocol-Validity Boundaries
16. Record Updates, Optimistic Concurrency and Metadata Versioning
17. Schema-Defined Immutability and Historical Integrity
18. Record Deletion Modes and Distinct State Semantics
19. Tombstones, Data Minimisation and Record-Key Non-Reuse
20. Record Restoration and Preservation of Deletion History
21. Schema-Defined Record Expiration
22. Inter-Record References, Version Pinning and Unavailable Targets
23. Embedded content
24. Blob references
25. Lists and ordering
26. Local application state
27. Draft records
28. Application-specific records
29. Schema extension
30. Record translation
31. Canonical records and projections
32. Comments and replies
33. Reactions
34. Reposts and references
35. Moderation labels
36. Record conflict
37. Batch operations
38. Record portability
39. Record interoperability
40. Required v0.1 record operations
41. Record invariants
42. Compliance scenario
43. Open design questions
44. Provisional decisions for v0.1
45. Core record principle

---

<!-- Part 1 -->

# EA-05-03 — Record Requirements Catalogue

## Part 1 — Record Foundations, Purpose and Conceptual Structure

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the foundational requirements of the Relay Record subsystem.

It establishes what a Relay Record is, how its canonical status and control relate to a Relay Repository, how applications may interact with records without owning them, the interoperability capabilities the Record Model must provide and the conceptual separation between the Record Envelope and Record Content.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Sections 1–3 and REM-03 requirements `REM-03-001` through `REM-03-025`.

It defines normative requirements governing:

- structured and independently addressable records;
- repository acceptance and repository-anchored control;
- record association with a Relay Identity;
- application independence, participation and non-ownership;
- cross-application usability and interpretation flexibility;
- location, type, validation, history, authority, visibility and version information;
- migration preservation and inter-record references;
- permissionless record-type extensibility; and
- the conceptual roles of the Record Envelope and Record Content.

Source Sections 4 and later are intentionally deferred to subsequent catalogue parts.

Two REM entries within the covered range are explicitly non-normative and do not generate catalogue requirements:

- `REM-03-005` records the illustrative Section 1 list of record types; and
- `REM-03-025` records the provisional status of the Section 3 example serialisation.

---

# 3. Requirements

---

## REL-REC-001

### Title

Structured Record Representation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** be represented as a structured unit of information.

### Rationale

A common structured representation allows records to be parsed, validated and interpreted as protocol objects rather than remaining opaque application-local data.

### Source

- REM-03-001
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-08

---

## REL-REC-002

### Title

Independent Record Addressability

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** be independently addressable.

### Rationale

Independent addressability allows a record to be located and referenced as a protocol object without depending solely on its position inside another object or an application-owned data structure.

### Source

- REM-03-002
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-05
- CI-08

---

## REL-REC-003

### Title

Canonical Status Through Repository Acceptance

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement

An information object **MUST NOT** be treated as a canonical Relay Record until it has been accepted into a Relay Repository.

### Rationale

Repository acceptance distinguishes canonical protocol state from an object generated or retained only within an application or other local environment.

### Source

- REM-03-003
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-07
- AI-01

---

## REL-REC-004

### Title

Identity-Associated Record Subject Matter

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Record **MUST** represent a specific object, statement, action or relationship associated with a Relay Identity.

### Rationale

The requirement defines the semantic scope of a record while leaving schemas free to represent different kinds of identity-associated objects and activity.

### Source

- REM-03-004
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-01
- CI-12

---

## REL-REC-005

### Title

Record Independence from Originating Applications

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Record **MUST** be defined independently of the application that created it.

### Rationale

Record identity and meaning must survive application replacement and cannot depend on the continued existence or proprietary interpretation of the originating client.

### Source

- REM-03-006
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-04

---

## REL-REC-006

### Title

Application Record Interaction

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** create, edit or display a Relay Record.

### Rationale

Applications are permitted to provide record-creation, editing and presentation experiences while the protocol separately defines record authority and control.

### Source

- REM-03-007
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-04
- CI-06

---

## REL-REC-007

### Title

Application Interaction Does Not Establish Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Creating, editing or displaying a Relay Record **MUST NOT** establish ownership or control of that record by the participating application.

### Rationale

Application participation is operational. It does not transfer repository authority or make the record dependent on the client through which the interaction occurred.

### Source

- REM-03-007
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-02
- CI-04

---

## REL-REC-008

### Title

Repository-Anchored Record Control

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Control of a Relay Record **MUST** remain anchored in the Relay Repository in which the record was authorised.

### Rationale

Repository-anchored control separates canonical authority from the applications that submit operations or display the resulting record.

### Source

- REM-03-008
- `design-notes/03-record-model.md`, Section 1

### Related Invariants

- CI-07
- AI-01

---

## REL-REC-009

### Title

Cross-Application Record Usability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** enable digital objects to be used across multiple applications.

### Rationale

Records provide portable protocol state only when compatible applications can use them without depending on the application that created them.

### Source

- REM-03-009
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-04

---

## REL-REC-010

### Title

Application Interpretation Flexibility

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay Record Model **MUST NOT** require every application to interpret all record information identically.

### Rationale

Protocol interoperability requires shared structure and meaning where defined, but does not require applications to provide identical interpretation or presentation experiences.

### Source

- REM-03-010
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-09
- CI-12

---

## REL-REC-011

### Title

Record Location Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to locate a record.

### Rationale

Applications cannot interoperate with records that lack sufficient protocol information to be located independently of application-private storage.

### Source

- REM-03-011
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-05
- CI-08

---

## REL-REC-012

### Title

Record-Type Determination

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to determine a record's type.

### Rationale

Type determination allows applications to identify the applicable schema and decide whether and how they can process a record.

### Source

- REM-03-012
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-08
- CI-09

---

## REL-REC-013

### Title

Structural Validation Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to validate a record's structure.

### Rationale

Structural validation requires common protocol and schema information that can be evaluated independently of the originating application's private implementation.

### Source

- REM-03-013
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-08

---

## REL-REC-014

### Title

Repository-History Verification Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to verify a record's repository history.

### Rationale

Repository-history verification allows an implementation to establish that record state is supported by the repository's accepted history rather than relying on an application's assertion alone.

### Source

- REM-03-014
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-015

### Title

Authorising-Identity Determination

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to determine which Relay Identity authorised a record.

### Rationale

Authorisation must be attributable to an identity and remain distinguishable from the application or agent that submitted or displayed the record.

### Source

- REM-03-015
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-016

### Title

Visibility Determination

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to determine a record's visibility.

### Rationale

Applications require explicit visibility information to interpret and serve a record according to its access classification rather than inferring access from presentation context.

### Source

- REM-03-016
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-017

### Title

Current-Version Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** provide sufficient consistent information for an application to identify the current version of a logical record.

### Rationale

Current-version identification prevents an application from confusing historical or cached state with the repository's current authoritative record state.

### Source

- REM-03-017
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-08
- AI-01

---

## REL-REC-018

### Title

Record Preservation During Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support preservation of a record during migration.

### Rationale

Migration cannot preserve continuity if a record loses its protocol identity or required information when its repository changes operational location.

### Source

- REM-03-018
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-03
- AI-04

---

## REL-REC-019

### Title

Inter-Record Reference Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** allow one record to refer to another record.

### Rationale

Inter-record references allow independently addressable records to express associations without collapsing separate logical objects into application-local structures.

### Source

- REM-03-019
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-05

---

## REL-REC-020

### Title

Permissionless Record-Type Extension

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** allow third parties to introduce new record types without obtaining permission from a central platform.

### Rationale

Permissionless extension allows the Record Model to evolve without making a central platform the mandatory gatekeeper for new record semantics.

### Source

- REM-03-020
- `design-notes/03-record-model.md`, Section 2

### Related Invariants

- CI-12

---

## REL-REC-021

### Title

Record Envelope and Content Layers

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** consist conceptually of a Record Envelope and Record Content.

### Rationale

The two-layer model distinguishes common protocol metadata from the information governed by an individual record schema without requiring a particular physical storage layout.

### Source

- REM-03-021
- `design-notes/03-record-model.md`, Section 3

### Related Invariants

- CI-08

---

## REL-REC-022

### Title

Record Envelope Responsibility

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Record Envelope **MUST** contain the protocol-level metadata required for record identification, verification, access and interoperability.

### Rationale

Common envelope metadata allows protocol operations to identify and evaluate a record without depending solely on schema-specific content or application-private knowledge.

### Source

- REM-03-022
- `design-notes/03-record-model.md`, Section 3

### Related Invariants

- CI-08

---

## REL-REC-023

### Title

Record Content Responsibility

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Record Content **MUST** contain the information defined by the record's schema.

### Rationale

Schema-governed content allows different record types to define their own information while remaining inside the common Record Model.

### Source

- REM-03-023
- `design-notes/03-record-model.md`, Section 3

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-024

### Title

Envelope and Content Semantic Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Implementations **MUST** preserve a clear semantic separation between protocol-level Record Envelope metadata and schema-defined Record Content.

### Rationale

Semantic separation ensures that the common protocol layer and schema-specific information retain distinct roles even when an implementation serialises or stores them together.

### Source

- REM-03-024
- `design-notes/03-record-model.md`, Section 3

### Related Invariants

- CI-08
- AI-09

---

# 4. REM coverage and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-001` | Direct | `REL-REC-001` |
| `REM-03-002` | Direct | `REL-REC-002` |
| `REM-03-003` | Direct | `REL-REC-003` |
| `REM-03-004` | Direct | `REL-REC-004` |
| `REM-03-005` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative record-type list |
| `REM-03-006` | Direct | `REL-REC-005` |
| `REM-03-007` | Split to preserve independent normative effects | `REL-REC-006`, `REL-REC-007` |
| `REM-03-008` | Direct | `REL-REC-008` |
| `REM-03-009` | Direct | `REL-REC-009` |
| `REM-03-010` | Direct | `REL-REC-010` |
| `REM-03-011` | Direct | `REL-REC-011` |
| `REM-03-012` | Direct | `REL-REC-012` |
| `REM-03-013` | Direct | `REL-REC-013` |
| `REM-03-014` | Direct | `REL-REC-014` |
| `REM-03-015` | Direct | `REL-REC-015` |
| `REM-03-016` | Direct | `REL-REC-016` |
| `REM-03-017` | Direct | `REL-REC-017` |
| `REM-03-018` | Direct | `REL-REC-018` |
| `REM-03-019` | Direct | `REL-REC-019` |
| `REM-03-020` | Direct | `REL-REC-020` |
| `REM-03-021` | Direct | `REL-REC-021` |
| `REM-03-022` | Direct | `REL-REC-022` |
| `REM-03-023` | Direct | `REL-REC-023` |
| `REM-03-024` | Direct | `REL-REC-024` |
| `REM-03-025` | Excluded from normative catalogue generation | Explicit Non-normative specification-status note; example serialisation remains provisional |

No normative REM entry within the covered range is omitted or consolidated into another catalogue requirement. `REM-03-007` is split because its application permission and non-ownership prohibition carry different normative keywords and are independently testable.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Sections 1–3 of `design-notes/03-record-model.md`.
- Source Sections 4–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-001` through `REM-03-025`.

## Identifier verification

- First catalogue identifier: `REL-REC-001`.
- Final catalogue identifier: `REL-REC-024`.
- Total catalogue requirements: 24.
- Catalogue identifiers are continuous and unique.

## Traceability verification

- Every normative REM entry in scope maps to at least one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-007` maps to two catalogue requirements to preserve its independently testable `MAY` and `MUST NOT` effects.
- No other REM entry is consolidated or split.

## Non-normative exclusion verification

- `REM-03-005` generates no normative catalogue requirement.
- `REM-03-025` generates no normative catalogue requirement.
- The illustrative Section 1 record-type list is not treated as a mandatory closed capability set.
- The Section 3 example JSON is not treated as final or exhaustive wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- Application interaction is separated from application ownership without adding a repository-authorisation condition to display.
- No requirement, qualification, exception, schema field or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 1 establishes the Record Model's foundations, interoperability purpose and two-layer conceptual structure. It generates `REL-REC-001` through `REL-REC-024` from normative material in `REM-03-001` through `REM-03-025`, while explicitly excluding the non-normative example and provisional serialisation entries.

The next catalogue part should begin with source Section 4 and `REM-03-026`.

---

<!-- Part 2 -->

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

---

<!-- Part 3 -->

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

---

<!-- Part 4 -->

# EA-05-03 — Record Requirements Catalogue

## Part 4 — Record Types, Schema Authority and Schema-Defined Behaviour

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how a schema identifier establishes a Relay Record's type and structure, what every record schema must define, how schema authority remains separate from record ownership and control, and which record behaviours a schema may define.

It also preserves the boundary between protocol-level validation and application-specific presentation.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 7 and REM-03 requirements `REM-03-057` through `REM-03-078`.

It defines normative requirements governing:

- schema identification of record type and structure;
- the information and behaviour every record schema must define;
- separation of schema namespaces from application or organisation ownership;
- identification of schema authority;
- continued repository and authorising-identity control when a third-party schema is used;
- optional schema-defined record behaviours; and
- separation of protocol-level validation from application-specific presentation.

Source Section 8 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-057` and `REM-03-058` are consolidated because they express the two effects of the same schema-identifier rule. `REM-03-059` through `REM-03-067` are consolidated because the source introduces one mandatory schema-definition obligation and enumerates the matters governed by that obligation. `REM-03-071` through `REM-03-077` are consolidated as the expressly optional behaviours listed under one schema-level permission. Each consolidated item remains explicit and individually traceable.

---

# 3. Requirements

---

## REL-REC-041

### Title

Schema Identification of Record Type and Structure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The schema identifier **MUST** define the Relay Record's type and structure.

### Rationale

Using the schema identifier for both type and structure gives implementations a common basis for determining what a record represents and which structural rules apply to it.

### Source

- REM-03-057
- REM-03-058
- `design-notes/03-record-model.md`, Section 7

### Related Invariants

- CI-08
- CI-09

---

## REL-REC-042

### Title

Mandatory Record Schema Definition

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A record schema **MUST** define:

- its required fields;
- its optional fields;
- its field types;
- its validation constraints;
- the meaning of each field;
- its supported operations;
- its compatibility rules;
- whether the record is singleton or repeatable; and
- whether updates are allowed or only superseding records are allowed.

### Rationale

A schema must state the structural, semantic, operational, compatibility and lifecycle rules needed for interoperable validation and handling of conforming records.

### Source

- REM-03-059
- REM-03-060
- REM-03-061
- REM-03-062
- REM-03-063
- REM-03-064
- REM-03-065
- REM-03-066
- REM-03-067
- `design-notes/03-record-model.md`, Section 7

### Related Invariants

- CI-08
- CI-12
- AI-09

---

## REL-REC-043

### Title

Schema Namespace Does Not Establish Record Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Use of an application-associated or organisation-associated schema namespace **MUST NOT** establish ownership of a conforming record by that application or organisation.

### Rationale

A namespace identifies who defines a schema, not who owns each record that uses it. Keeping those concepts separate preserves record independence from applications and organisations.

### Source

- REM-03-068
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-02
- CI-04

---

## REL-REC-044

### Title

Schema Namespace Authority Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema namespace **MUST** identify the schema authority.

### Rationale

Identifying the schema authority makes responsibility for the schema distinguishable from ownership or control of records that conform to it.

### Source

- REM-03-069
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-12

---

## REL-REC-045

### Title

Record Control When Using a Third-Party Schema

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Record that uses a third-party schema **MUST** remain controlled by its Relay Repository and authorising Relay Identity.

### Rationale

Schema authorship does not displace repository authority or the authorising identity's control of an individual record.

### Source

- REM-03-070
- `design-notes/03-record-model.md`, Section 7.1

### Related Invariants

- CI-02
- CI-07
- AI-01

---

## REL-REC-046

### Title

Optional Schema-Defined Record Behaviour

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record schema **MAY** define:

- whether comments may reference the record;
- whether the record supports revisions;
- whether the record can expire;
- whether the record may be public;
- whether a field contains another Record URI;
- whether a blob is required; and
- whether multiple instances are allowed.

### Rationale

Schemas may govern behaviours specific to their record types without making any listed behaviour mandatory for every schema or record.

### Source

- REM-03-071
- REM-03-072
- REM-03-073
- REM-03-074
- REM-03-075
- REM-03-076
- REM-03-077
- `design-notes/03-record-model.md`, Section 7.2

### Related Invariants

- CI-12
- AI-09

---

## REL-REC-047

### Title

Protocol Validation and Application Presentation Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Protocol-level validation **MUST** remain separate from application-specific presentation.

### Rationale

Protocol validity must be determined by protocol and schema rules rather than by how a particular application chooses or is able to present a record.

### Source

- REM-03-078
- `design-notes/03-record-model.md`, Section 7.2

### Related Invariants

- CI-04
- CI-09

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-057` | Consolidated schema-identifier obligation | `REL-REC-041` |
| `REM-03-058` | Consolidated schema-identifier obligation | `REL-REC-041` |
| `REM-03-059` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-060` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-061` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-062` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-063` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-064` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-065` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-066` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-067` | Consolidated mandatory schema definition | `REL-REC-042` |
| `REM-03-068` | Direct | `REL-REC-043` |
| `REM-03-069` | Direct | `REL-REC-044` |
| `REM-03-070` | Direct | `REL-REC-045` |
| `REM-03-071` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-072` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-073` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-074` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-075` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-076` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-077` | Consolidated optional schema-defined behaviour | `REL-REC-046` |
| `REM-03-078` | Direct | `REL-REC-047` |

No REM entry in scope is excluded from normative catalogue generation. The three consolidations follow the source's own aggregate rules and lists while retaining every item in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 7 of `design-notes/03-record-model.md`.
- Source Sections 8–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-057` through `REM-03-078`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-040`.
- First identifier in this part: `REL-REC-041`.
- Final identifier in this part: `REL-REC-047`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–4.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-057` and `REM-03-058` retain individual traceability through the Source list and coverage table for `REL-REC-041`.
- `REM-03-059` through `REM-03-067` retain individual traceability through the Source list and coverage table for `REL-REC-042`.
- `REM-03-071` through `REM-03-077` retain individual traceability through the Source list and coverage table for `REL-REC-046`.

## Schema-definition verification

- The schema identifier defines both record type and record structure.
- Every mandatory schema-definition concern listed in Section 7 remains explicit.
- No example namespace, final field name, schema syntax or implementation detail has been made normative.

## Authority and control verification

- A schema namespace does not establish record ownership by its associated application or organisation.
- The namespace identifies the schema authority.
- A record using a third-party schema remains controlled by its repository and authorising identity.
- Schema authority is not treated as authority over each conforming record.

## Optional-behaviour verification

- All seven schema-defined behaviours retain the source-level `MAY` framing.
- No listed behaviour is required to be defined or enabled by every schema.
- The source example namespace is not treated as a selected or mandatory namespace vocabulary.

## Validation-boundary verification

- Protocol-level validation remains separate from application-specific presentation.
- Presentation capability or choice does not determine protocol validity.
- No requirement or qualification has been imported from later Record Model sections.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- Consolidation does not remove any independently traceable obligation or optional behaviour.

---

# 6. Part conclusion

Part 4 defines schema identification, mandatory schema content, schema authority, record-control separation, optional schema-defined behaviour and the protocol-validation boundary. It generates `REL-REC-041` through `REL-REC-047` from `REM-03-057` through `REM-03-078`.

The next catalogue part should begin with source Section 8 and `REM-03-079`.

---

<!-- Part 5 -->

# EA-05-03 — Record Requirements Catalogue

## Part 5 — Core Record Categories and Schema Diversity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the recommended broad categories used to distinguish the principal semantic roles of Relay Records and permits records in different categories to share common fields while using different schemas.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 8 and REM-03 requirements `REM-03-079` through `REM-03-087`.

It defines normative requirements governing:

- the recommended distinction of broad record categories;
- the meanings of Entity, Activity, Relationship, Authority, Assertion and Tombstone Records; and
- optional sharing of common fields across categories that use different schemas.

Source Section 9 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-079` through `REM-03-085` are consolidated because the source introduces one recommended broad-category model and then defines the six categories it contains. `REM-03-086` and `REM-03-087` are consolidated because they express the two compatible permissions contained in one source sentence. Every category meaning and both schema-diversity permissions remain explicit and individually traceable.

The examples listed beneath the category definitions illustrate possible records or actions. They do not define mandatory category members, schema names, operations or a closed vocabulary and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-048

### Title

Broad Record Category Distinction

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** distinguish broad record categories sufficient to describe the principal semantic role of a record, including support for:

- Entity Records, which describe a persistent entity or object;
- Activity Records, which describe an action or event;
- Relationship Records, which describe a directed or mutual relationship between identities or records;
- Authority Records, which describe permission or control;
- Assertion Records, which describe a claim; and
- Tombstone Records, which record the deletion or retirement of another record without retaining its full active content.

### Rationale

Broad semantic categories provide a common way to distinguish the principal roles of records while allowing specific schemas to define their detailed structure and behaviour. The categories are recommendations for Relay v0.1 rather than unconditional validity requirements or a closed schema vocabulary.

### Source

- REM-03-079
- REM-03-080
- REM-03-081
- REM-03-082
- REM-03-083
- REM-03-084
- REM-03-085
- `design-notes/03-record-model.md`, Section 8

### Related Invariants

- CI-09
- CI-12

---

## REL-REC-049

### Title

Shared Fields with Schema Diversity

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Different record categories **MAY** share common fields while using different schemas.

### Rationale

Field reuse can support common semantics across categories without replacing specific schemas with one universal content schema or treating a broad category as a specific record type.

### Source

- REM-03-086
- REM-03-087
- `design-notes/03-record-model.md`, Section 8.6

### Related Invariants

- CI-08
- CI-12

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-079` | Consolidated category-model recommendation | `REL-REC-048` |
| `REM-03-080` | Consolidated category definition | `REL-REC-048` |
| `REM-03-081` | Consolidated category definition | `REL-REC-048` |
| `REM-03-082` | Consolidated category definition | `REL-REC-048` |
| `REM-03-083` | Consolidated category definition | `REL-REC-048` |
| `REM-03-084` | Consolidated category definition | `REL-REC-048` |
| `REM-03-085` | Consolidated category definition | `REL-REC-048` |
| `REM-03-086` | Consolidated schema-diversity permission | `REL-REC-049` |
| `REM-03-087` | Consolidated schema-diversity permission | `REL-REC-049` |

No REM entry in scope is excluded from normative catalogue generation. The illustrative examples beneath the category definitions have no separate REM identifiers and generate no normative catalogue requirements.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 8 of `design-notes/03-record-model.md`.
- Source Sections 9–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-079` through `REM-03-087`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-047`.
- First identifier in this part: `REL-REC-048`.
- Final identifier in this part: `REL-REC-049`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers are continuous and unique across Parts 1–5.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites its in-scope REM identifiers and the authoritative design-note section or subsection.
- `REM-03-079` through `REM-03-085` retain individual traceability through the Source list and coverage table for `REL-REC-048`.
- `REM-03-086` and `REM-03-087` retain individual traceability through the Source list and coverage table for `REL-REC-049`.

## Category-model verification

- The broad category model retains the source-level `SHOULD` strength.
- Entity, Activity, Relationship, Authority, Assertion and Tombstone Record meanings remain explicit.
- The six categories are not represented as an exhaustive, mutually exclusive or final schema vocabulary.
- A broad semantic category is not treated as a substitute for a specific record schema.

## Illustrative-example verification

- Category examples generate no separate normative catalogue requirements.
- Profiles, projects, publications, organisations, media items, publish, react, follow, endorse, revoke, announce and the other example terms are not made mandatory category members, schema names or operations.
- No final field name, category identifier, schema identifier or serialisation syntax is inferred from an example.

## Schema-diversity verification

- Different categories remain permitted to share common fields.
- Different categories remain permitted to use different schemas even where fields are shared.
- No universal content schema is required.

## Normative-language verification

- Catalogue statements preserve the normative strength of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- Consolidation does not remove any category meaning or schema-diversity permission.
- No requirement, qualification or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 5 defines the recommended broad Record categories and permits shared fields alongside schema diversity. It generates `REL-REC-048` through `REL-REC-049` from `REM-03-079` through `REM-03-087`.

The next catalogue part should begin with source Section 9 and `REM-03-088`.

---

<!-- Part 6 -->

# EA-05-03 — Record Requirements Catalogue

## Part 6 — Singleton and Repeatable Record Cardinality

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines singleton and repeatable collection cardinality, the active-record constraint that gives singleton its meaning, the multiplicity permitted for repeatable records and the preferred versioning behaviour for singleton updates.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 9 and REM-03 requirements `REM-03-088` through `REM-03-091`.

It defines normative requirements governing:

- schema definition of a collection as singleton or repeatable;
- the maximum number of active logical records for a singleton schema or role;
- the permission for multiple logical records in a repeatable schema or collection; and
- the preferred treatment of singleton updates as new versions of the same logical record.

Source Section 10 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-088` complements rather than duplicates `REL-REC-042`. The earlier requirement mandates that a record schema state whether a record is singleton or repeatable; this part preserves Section 9's permission to define an applicable collection using either model and defines what each model means.

The listed singleton and repeatable examples are illustrative. They do not establish mandatory schema names, collection names, roles or a closed vocabulary and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-050

### Title

Schema-Defined Collection Cardinality

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record schema **MAY** define an applicable collection as singleton or repeatable.

### Rationale

Schema-defined collection cardinality allows the model appropriate to the record type to be selected while the mandatory declaration of singleton or repeatable status remains governed by `REL-REC-042`.

### Source

- REM-03-088
- `design-notes/03-record-model.md`, Section 9

### Related Invariants

- CI-08
- CI-12
- AI-09

---

## REL-REC-051

### Title

Singleton Active-Record Constraint

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

For a singleton schema or role, no more than one active logical record of that schema or role **MAY** exist per repository.

### Rationale

Limiting singleton cardinality to one active logical record prevents competing current records while allowing that logical record to retain historical versions.

### Source

- REM-03-089
- `design-notes/03-record-model.md`, Section 9, Singleton

### Related Invariants

- CI-07
- CI-10
- AI-01

---

## REL-REC-052

### Title

Repeatable Record Multiplicity

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

For a repeatable schema or collection, multiple logical records **MAY** exist in the repository.

### Rationale

Repeatable cardinality permits more than one logical record without implying that other applicable schema or validation rules no longer apply.

### Source

- REM-03-090
- `design-notes/03-record-model.md`, Section 9, Repeatable

### Related Invariants

- CI-07
- CI-12

---

## REL-REC-053

### Title

Preferred Singleton Update Behaviour

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An update to a singleton record **SHOULD** normally create a new version of the same logical record rather than a second competing current logical record.

### Rationale

Versioning the existing singleton preserves its continuing logical identity and its one-current-record semantics. The qualification “normally” retains the source's recommendation rather than creating an unconditional prohibition.

### Source

- REM-03-091
- `design-notes/03-record-model.md`, Section 9

### Related Invariants

- CI-05
- CI-10
- AI-02

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-088` | Direct; complementary to existing schema-declaration requirement | `REL-REC-050`; does not duplicate or weaken `REL-REC-042` |
| `REM-03-089` | Direct | `REL-REC-051` |
| `REM-03-090` | Direct | `REL-REC-052` |
| `REM-03-091` | Direct | `REL-REC-053` |

No REM entry in scope is consolidated into another requirement or excluded from normative catalogue generation. The relationship between `REM-03-088` and `REL-REC-042` is recorded explicitly without replacing either Section 9's collection-level permission or Section 7's mandatory schema-declaration rule.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 9 of `design-notes/03-record-model.md`.
- Source Sections 10–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-088` through `REM-03-091`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-049`.
- First identifier in this part: `REL-REC-050`.
- Final identifier in this part: `REL-REC-053`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–6.

## Traceability verification

- Every REM entry in scope maps directly to one catalogue requirement.
- Every catalogue requirement cites one in-scope REM identifier and the authoritative design-note section or subsection.
- No REM entry in scope is consolidated, excluded or left unaccounted for.

## Cross-part continuity verification

- `REL-REC-042` continues to require a schema to define whether a record is singleton or repeatable.
- `REL-REC-050` preserves the Section 9 permission to define an applicable collection using either model.
- The Section 9 permission does not duplicate, replace or weaken the earlier mandatory schema declaration.

## Cardinality verification

- The singleton constraint applies to active logical records of the applicable schema or role within a repository.
- Historical versions of the same singleton logical record are not treated as competing active logical records.
- Repeatable schemas or collections retain the permission for multiple logical records.
- Repeatable status does not displace other applicable schema or validation rules.

## Singleton-update verification

- The preferred update behaviour retains the source-level `SHOULD` strength.
- The qualification “normally” remains explicit.
- The recommendation favours a new version of the same logical record over a second competing current logical record.
- The recommendation is not converted into an unconditional prohibition.

## Illustrative-example verification

- Singleton and repeatable examples generate no separate normative catalogue requirements.
- Primary profile, Current repository preferences, Primary public contact settings, Posts, Projects, Photographs, Credentials and Relationships are not made mandatory schemas, collections, roles or vocabulary values.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No requirement, exception rule, schema name or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 6 defines collection-cardinality selection, singleton and repeatable semantics and preferred singleton-update behaviour. It generates `REL-REC-050` through `REL-REC-053` from `REM-03-088` through `REM-03-091`.

The next catalogue part should begin with source Section 10 and `REM-03-092`.

---

<!-- Part 7 -->

# EA-05-03 — Record Requirements Catalogue

## Part 7 — Subject, Authority and Submission Role Separation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the distinct roles of the record subject, authorising identity and submitting application or agent, including when those roles may coincide or refer to different entities and how a record should represent them without conflation.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 10 and REM-03 requirements `REM-03-092` through `REM-03-098`.

It defines normative requirements governing:

- conceptual distinction among the subject, authorising identity and submitter;
- permission for those roles to coincide where factually appropriate;
- support for records in which the roles refer to different entities;
- the meaning of each role; and
- independent representation of the roles without conflation.

Source Section 11 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-095` through `REM-03-097` are consolidated into one role-semantics requirement because the source defines the three roles together as part of one conceptual model. Each definition remains explicit and individually traceable.

The prose and JSON examples in Section 10 are illustrative. They do not establish mandatory physical field names, identity values, schema content or final wire syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-054

### Title

Record Role Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** distinguish the record subject, authorising identity and submitting application or agent as separate concepts.

### Rationale

Separating the three roles preserves the distinction between who or what a record concerns, whose repository authority accepted it and which application or agent transmitted the operation.

### Source

- REM-03-092
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-055

### Title

Coinciding Record Roles

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The record subject, authorising identity and submitter **MAY** refer to the same entity where factually appropriate.

### Rationale

The model must accommodate direct interactions in which one entity fulfils multiple roles without erasing the distinct meaning of each role.

### Source

- REM-03-093
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-056

### Title

Differing Record Roles

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support records in which the subject, authorising identity and submitter refer to different entities.

### Rationale

Supporting different entities in these roles allows the model to represent records concerning another identity or object, records accepted under a particular identity's repository authority and operations transmitted by an application or agent.

### Source

- REM-03-094
- `design-notes/03-record-model.md`, Section 10

### Related Invariants

- CI-02
- CI-06
- CI-12

---

## REL-REC-057

### Title

Record Role Semantics

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Record **MUST** identify, through fields or equivalent representations:

- as its subject, the identity or object that the record concerns;
- as its authorising identity, the identity under whose repository authority the record was accepted; and
- as its submitter, the application or agent that transmitted the record operation.

### Rationale

Explicit role semantics allow implementations to determine subject matter, repository authority and submission provenance without treating any one role as a substitute for another.

### Source

- REM-03-095
- REM-03-096
- REM-03-097
- `design-notes/03-record-model.md`, Sections 10.1–10.3

### Related Invariants

- CI-02
- CI-06
- CI-08
- AI-01

---

## REL-REC-058

### Title

Independent Record Role Representation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A Relay Record **SHOULD** be capable of representing its subject, authorising identity and submitter independently without conflating one role with another.

### Rationale

Independent representation preserves accurate subject, authority and submission provenance even when the same entity happens to fulfil more than one role. The source frames this capability as a recommendation rather than an unconditional requirement.

### Source

- REM-03-098
- `design-notes/03-record-model.md`, Section 10.3

### Related Invariants

- CI-02
- CI-06
- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-092` | Direct | `REL-REC-054` |
| `REM-03-093` | Direct | `REL-REC-055` |
| `REM-03-094` | Direct | `REL-REC-056` |
| `REM-03-095` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-096` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-097` | Consolidated role semantics | `REL-REC-057` |
| `REM-03-098` | Direct | `REL-REC-058` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-095` through `REM-03-097` retains all three role definitions in the Statement, Source list and coverage table for `REL-REC-057`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 10 of `design-notes/03-record-model.md`.
- Source Sections 11–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-092` through `REM-03-098`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-053`.
- First identifier in this part: `REL-REC-054`.
- Final identifier in this part: `REL-REC-058`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers are continuous and unique across Parts 1–7.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-095` through `REM-03-097` retain individual traceability through the Source list and coverage table for `REL-REC-057`.

## Role-separation verification

- The subject, authorising identity and submitter remain conceptually distinct.
- The roles may refer to the same entity where factually appropriate without losing their distinct meanings.
- The model supports records in which the three roles refer to different entities.
- Submission is not treated as authorisation, ownership or repository authority.

## Role-semantics verification

- The subject remains the identity or object the record concerns.
- The authorising identity remains the identity under whose repository authority the record was accepted.
- The submitter remains the application or agent that transmitted the operation.
- Fields or equivalent representations are permitted; no particular physical layout is required.

## Independent-representation verification

- Independent role representation retains the source-level `SHOULD` strength.
- The recommendation is not strengthened to `MUST` by the separate mandatory conceptual-distinction rule.
- Coinciding role values do not imply conflated role semantics.

## Illustrative-example verification

- Section 10 prose and JSON examples generate no separate normative catalogue requirements.
- `subject`, `authorisedBy` and `submittedBy` are not made mandatory physical field names.
- The example identities, employment credential, portfolio application and JSON object are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No role field, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 7 defines the distinction, permitted coincidence, possible separation, semantics and independent representation of the subject, authorising identity and submitter roles. It generates `REL-REC-054` through `REL-REC-058` from `REM-03-092` through `REM-03-098`.

The next catalogue part should begin with source Section 11 and `REM-03-099`.

---

<!-- Part 8 -->

# EA-05-03 — Record Requirements Catalogue

## Part 8 — Issued Assertions, Holder Storage and Signed-Claim Integrity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines support for assertions issued by an identity other than the record subject, the information an issued assertion must distinguish, the holder's permission to store an assertion and the integrity rule governing alteration of an issuer's signed claim.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 11 and REM-03 requirements `REM-03-099` through `REM-03-108`.

It defines normative requirements governing:

- support for assertions made by an identity other than the record subject;
- identification of the issuer, subject and holder repository;
- representation of issuance time, expiration and revocation status;
- inclusion or reference of an issuer signature;
- holder storage of an issued assertion or credential; and
- validity of the issuer signature when the signed claim is altered.

Source Section 12 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-100` through `REM-03-106` are consolidated because the source imposes one mandatory distinction rule and then enumerates the seven items governed by it. Every item remains explicit and individually traceable.

The prose and JSON examples in Section 11 are illustrative. They do not establish an exhaustive set of assertion issuers or types, mandatory physical field names, final schema content, cryptographic mechanisms or wire syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-059

### Title

Externally Issued Assertion Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support records containing assertions made by an identity other than the record subject.

### Rationale

Externally issued assertions allow records to represent claims whose authority comes from an issuer distinct from the identity or object to which the claim applies.

### Source

- REM-03-099
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-08
- CI-12

---

## REL-REC-060

### Title

Required Issued-Assertion Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An issued assertion record **MUST** distinguish:

- the issuer of the assertion;
- the subject to whom or to which the assertion applies;
- the repository holding the assertion record;
- the time at which the assertion was issued;
- whether the assertion expires and, where applicable, its expiration time or condition;
- the assertion's revocation status; and
- an issuer signature, contained or referenced, that is capable of binding the issuer to the signed assertion.

### Rationale

These distinctions allow implementations to determine who made the claim, what it concerns, where it is held, its lifecycle status and whether its signed content remains attributable to the issuer.

### Source

- REM-03-100
- REM-03-101
- REM-03-102
- REM-03-103
- REM-03-104
- REM-03-105
- REM-03-106
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-07
- CI-08
- CI-10

---

## REL-REC-061

### Title

Holder Storage of Issued Assertions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A holder **MAY** store an issued assertion or credential in the holder's Relay Repository.

### Rationale

Holder storage supports portability and repository-based custody without transferring issuer authority or granting permission to alter the issuer's signed claim.

### Source

- REM-03-107
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-03
- CI-07

---

## REL-REC-062

### Title

Signed-Claim Integrity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A holder or other non-issuer **MUST NOT** alter the issuer's signed claim while continuing to represent the issuer signature as valid.

### Rationale

An issuer signature can attest only to the claim content the issuer signed. Altering that content invalidates the original signature unless the issuer signs the altered content as a new assertion.

### Source

- REM-03-108
- `design-notes/03-record-model.md`, Section 11

### Related Invariants

- CI-02
- CI-08
- CI-10

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-099` | Direct | `REL-REC-059` |
| `REM-03-100` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-101` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-102` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-103` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-104` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-105` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-106` | Consolidated required issued-assertion information | `REL-REC-060` |
| `REM-03-107` | Direct | `REL-REC-061` |
| `REM-03-108` | Direct | `REL-REC-062` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-100` through `REM-03-106` retains all seven mandatory distinctions in the Statement, Source list and coverage table for `REL-REC-060`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 11 of `design-notes/03-record-model.md`.
- Source Sections 12–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-099` through `REM-03-108`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-058`.
- First identifier in this part: `REL-REC-059`.
- Final identifier in this part: `REL-REC-062`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–8.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-100` through `REM-03-106` retain individual traceability through the Source list and coverage table for `REL-REC-060`.

## Issued-assertion verification

- The Record Model supports assertions made by an identity other than the record subject.
- Issuer, subject and holder repository remain distinct concepts.
- Issuance time is not conflated with repository acceptance or import time.
- Expiration and revocation status remain represented as separate lifecycle concerns.
- No revocation-resolution mechanism is invented.
- The issuer signature may be contained or referenced and must bind the issuer to the signed assertion.
- No signature algorithm, encoding or key-resolution mechanism is selected.

## Holder-storage verification

- Holder storage retains the source-level `MAY` strength.
- Storage does not transfer issuer authority.
- Storage does not permit alteration of the issuer's signed claim while preserving the signature's represented validity.

## Signed-claim verification

- The prohibition applies when a holder or other non-issuer alters the signed claim while continuing to represent the issuer signature as valid.
- The rule does not prohibit storage of the assertion or management of information outside the signed claim.
- Altered claim content requires invalidation of the original signature unless the issuer signs the altered content as a new assertion.

## Illustrative-example verification

- Section 11 prose and JSON examples generate no separate normative catalogue requirements.
- Universities, employers, professional bodies and communities are not treated as an exhaustive issuer or assertion-type set.
- `schema`, `issuer`, `subject`, `issuedAt`, `expiresAt`, `credential` and `issuerSignature` are not made mandatory physical field names.
- The example schema identifier, identities, qualification, timestamp, null value and signature placeholder are not treated as final schema content or wire syntax.
- Omission of holder-repository and revocation-status representations from the example JSON does not weaken the source's mandatory distinction list.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No physical field, cryptographic mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 8 defines externally issued assertions, their required distinguishing information, holder storage permission and signed-claim integrity. It generates `REL-REC-059` through `REL-REC-062` from `REM-03-099` through `REM-03-108`.

The next catalogue part should begin with source Section 12 and `REM-03-109`.

---

<!-- Part 9 -->

# EA-05-03 — Record Requirements Catalogue

## Part 9 — Structured Provenance and Provenance Assurance

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines support for structured record provenance, the origin and processing information provenance may identify, the boundary between source declaration and verification, the assurance forms provenance may represent and the recommended indication of the applicable assurance level.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 12 and REM-03 requirements `REM-03-109` through `REM-03-123`.

It defines normative requirements governing:

- support for structured provenance information;
- optional identification of record origin, source, processing and migration information;
- separation of declared provenance from authentication or verification;
- optional provenance assurance representations; and
- indication of the applicable provenance assurance level.

Source Section 13 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-110` through `REM-03-117` are consolidated because the source introduces one permission for provenance to identify information and then enumerates eight optional matters. `REM-03-119` through `REM-03-122` are consolidated because the source introduces one permission for provenance to use four assurance representations. Every optional matter and assurance form remains explicit and individually traceable.

The JSON in Section 12 is illustrative. It does not establish mandatory physical field names, provenance-method vocabulary, schema content or final wire syntax and therefore generates no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-063

### Title

Structured Provenance Support

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Every Relay Record **SHOULD** support structured provenance information.

### Rationale

Structured provenance allows a record to carry interoperable information about its origin and processing history. The source recommends support for that information without requiring every record to contain provenance.

### Source

- REM-03-109
- `design-notes/03-record-model.md`, Section 12

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-064

### Title

Optional Provenance Information

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Record provenance **MAY** identify:

- whether the record was created directly;
- whether the record was imported;
- the service from which the record or its source material originated;
- a source record from which the record was imported, copied, derived or transformed;
- a source file used to create, import or transform the record;
- an AI system involved in creating, editing, transforming or processing the record;
- a process through which source material was transformed into the current record; and
- a migration event affecting the record.

### Rationale

These optional provenance elements allow implementations to describe different origins and processing histories without requiring every provenance representation to contain every element or prescribing how sources are stored or referenced.

### Source

- REM-03-110
- REM-03-111
- REM-03-112
- REM-03-113
- REM-03-114
- REM-03-115
- REM-03-116
- REM-03-117
- `design-notes/03-record-model.md`, Section 12

### Related Invariants

- CI-03
- CI-05
- CI-08
- CI-10

---

## REL-REC-065

### Title

Provenance Declaration Is Not Automatic Verification

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** treat a declared provenance source as automatically authenticated or verified solely because it appears in the record.

### Rationale

A source declaration states provenance but does not itself supply proof of source authenticity. Keeping declaration and verification separate prevents unverified metadata from being treated as established evidence.

### Source

- REM-03-118
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-08
- CI-10

---

## REL-REC-066

### Title

Provenance Assurance Representations

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The provenance model **MAY** represent provenance information as:

- self-declared;
- application-attested;
- cryptographically verified; or
- externally issued by another identity or authority.

### Rationale

The four representations allow provenance to communicate different assurance bases without imposing a universal ranking, trust value or implementation mechanism.

### Source

- REM-03-119
- REM-03-120
- REM-03-121
- REM-03-122
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-067

### Title

Applicable Provenance Assurance Indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A record containing provenance information **SHOULD** indicate the applicable provenance assurance level.

### Rationale

Indicating the applicable assurance level helps consumers distinguish the basis on which provenance is presented while retaining the source's recommended rather than mandatory strength.

### Source

- REM-03-123
- `design-notes/03-record-model.md`, Section 12.1

### Related Invariants

- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-109` | Direct | `REL-REC-063` |
| `REM-03-110` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-111` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-112` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-113` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-114` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-115` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-116` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-117` | Consolidated optional provenance information | `REL-REC-064` |
| `REM-03-118` | Direct | `REL-REC-065` |
| `REM-03-119` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-120` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-121` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-122` | Consolidated provenance assurance representation | `REL-REC-066` |
| `REM-03-123` | Direct | `REL-REC-067` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated permission in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 12 of `design-notes/03-record-model.md`.
- Source Sections 13–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-109` through `REM-03-123`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-062`.
- First identifier in this part: `REL-REC-063`.
- Final identifier in this part: `REL-REC-067`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers are continuous and unique across Parts 1–9.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-110` through `REM-03-117` retain individual traceability through the Source list and coverage table for `REL-REC-064`.
- `REM-03-119` through `REM-03-122` retain individual traceability through the Source list and coverage table for `REL-REC-066`.

## Structured-provenance verification

- Structured provenance support retains the source-level `SHOULD` strength.
- Support for structured provenance is not converted into a requirement that every record contain provenance information.
- All eight provenance matters remain explicit and optional.
- No provenance representation is required to contain all eight matters.
- No source-reference format, embedding model, integrity-hash mechanism or storage arrangement is prescribed.
- AI-system identification does not assert the extent, nature or significance of the system's involvement.

## Declaration and verification boundary

- A declared source is not treated as automatically authenticated or verified.
- Provenance declaration and provenance verification remain separate concepts.

## Assurance-representation verification

- Self-declared, application-attested, cryptographically verified and externally issued provenance remain explicit optional representations.
- No universal ranking, trust value or equivalence is imposed among the four representations.
- No application-attestation mechanism, cryptographic algorithm, key model or external-issuance mechanism is selected.
- Indication of the applicable assurance level retains the source-level `SHOULD` strength.

## Illustrative-example verification

- The Section 12 JSON generates no separate normative catalogue requirements.
- `provenance`, `method`, `sourceService`, `sourceIdentifier`, `importedAt` and `importedBy` are not made mandatory physical field names.
- `imported`, the example service, source identifier, timestamp and application identity are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No assurance ranking, field name, cryptographic mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 9 defines structured provenance support, optional provenance information, the source-declaration verification boundary, provenance assurance representations and applicable-level indication. It generates `REL-REC-063` through `REL-REC-067` from `REM-03-109` through `REM-03-123`.

The next catalogue part should begin with source Section 13 and `REM-03-124`.

---

<!-- Part 10 -->

# EA-05-03 — Record Requirements Catalogue

## Part 10 — Creation Modes, Authorship Declarations and Evidentiary Limits

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines representation of creation modes, limits on inferring those modes from record style or content, recommended sources of creation-mode declarations, optional tool information, preservation of declarations and the evidentiary limit on claims of human authorship.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 13 and REM-03 requirements `REM-03-124` through `REM-03-139`.

It defines normative requirements governing:

- optional representation of different creation modes;
- prohibition of creation-mode assignment solely from style or content;
- recommended declaration or attestation sources;
- optional structured information about creation tools and their roles;
- preservation of authorised creation-mode declarations and associated metadata; and
- the limit on claims that Relay proves human authorship.

Source Section 14 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-124` through `REM-03-131` are consolidated because the source introduces one permission for multiple creation forms and then provides seven possible declarations. `REM-03-133` through `REM-03-136` are consolidated because the source applies one recommendation to four declaration or attestation sources. Every mode and source remains explicit and individually traceable.

The declaration list and JSON in Section 13 are illustrative and non-exclusive. They do not establish a closed creation-mode vocabulary, mandatory physical field names, mandatory tool roles, final schema content or wire syntax and therefore generate no additional catalogue requirements.

---

# 3. Requirements

---

## REL-REC-068

### Title

Creation-Mode Representation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Relay Record Model **MAY** represent multiple forms of human, assisted, automated, imported or unknown creation, including the following non-exclusive declarations:

- `human-created`;
- `human-assisted`;
- `AI-assisted`;
- `AI-generated`;
- `automated`;
- `imported`; and
- `unknown`, where the creation mode cannot be determined or responsibly asserted.

### Rationale

Creation-mode declarations allow records to communicate different forms of authorship and automation while retaining uncertainty where the mode cannot be responsibly established. The listed declarations are permitted options rather than a mandatory or closed vocabulary.

### Source

- REM-03-124
- REM-03-125
- REM-03-126
- REM-03-127
- REM-03-128
- REM-03-129
- REM-03-130
- REM-03-131
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-069

### Title

No Style-Only Creation-Mode Inference

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** assign a human, assisted, AI-generated, automated, imported or equivalent creation label solely by analysing the style or content of the record.

### Rationale

Style or content alone does not establish a record's creation mode. Preventing such analysis from being represented as a declared mode preserves the distinction between an authorised declaration or attestation and an unsupported inference.

### Source

- REM-03-132
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

## REL-REC-070

### Title

Creation-Mode Declaration Sources

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A creation-mode declaration **SHOULD** be capable of being:

- made by the record controller;
- made or attested by the submitting application;
- made or attested by a trusted creation system; or
- issued or attested by an external verification service.

### Rationale

Supporting multiple declaration sources allows creation mode to be represented in different operational contexts while leaving the applicable identity, trust, attestation and verification mechanisms to their governing specifications.

### Source

- REM-03-133
- REM-03-134
- REM-03-135
- REM-03-136
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-REC-071

### Title

Structured Creation-Tool Information

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** include structured details about tools involved in its creation and the role performed by each tool.

### Rationale

Optional tool details can provide richer creation provenance without requiring them for every record or creation-mode declaration.

### Source

- REM-03-137
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

## REL-REC-072

### Title

Preservation of Creation Declarations

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** preserve authorised creation-mode declarations and associated creation metadata across record handling and migration.

### Rationale

Preservation prevents creation declarations and their supporting context from being lost as records are handled or moved, while making no claim that preservation proves the declarations true.

### Source

- REM-03-138
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-03
- CI-08
- CI-10

---

## REL-REC-073

### Title

No Universal Human-Authorship Claim

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay v0.1 **MUST NOT** claim that creation-mode declarations or provenance metadata provide universal proof of human authorship.

### Rationale

Relay can preserve declarations and attestations, but their existence does not solve the broader evidentiary problem of proving human authorship in every context.

### Source

- REM-03-139
- `design-notes/03-record-model.md`, Section 13

### Related Invariants

- CI-08

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-124` | Consolidated creation-mode representation | `REL-REC-068` |
| `REM-03-125` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-126` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-127` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-128` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-129` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-130` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-131` | Consolidated permitted creation-mode declaration | `REL-REC-068` |
| `REM-03-132` | Direct | `REL-REC-069` |
| `REM-03-133` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-134` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-135` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-136` | Consolidated declaration source | `REL-REC-070` |
| `REM-03-137` | Direct | `REL-REC-071` |
| `REM-03-138` | Direct | `REL-REC-072` |
| `REM-03-139` | Direct | `REL-REC-073` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated mode or declaration source in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 13 of `design-notes/03-record-model.md`.
- Source Sections 14–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-124` through `REM-03-139`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-067`.
- First identifier in this part: `REL-REC-068`.
- Final identifier in this part: `REL-REC-073`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–10.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-124` through `REM-03-131` retain individual traceability through the Source list and coverage table for `REL-REC-068`.
- `REM-03-133` through `REM-03-136` retain individual traceability through the Source list and coverage table for `REL-REC-070`.

## Creation-mode verification

- All seven listed creation-mode declarations remain explicit and optional.
- The declaration list remains non-exclusive and is not treated as a closed or final protocol vocabulary.
- No declaration is required for every record.
- `unknown` remains available where the creation mode cannot be determined or responsibly asserted.

## Inference-boundary verification

- A creation label must not be assigned solely from record style or content.
- The word “solely” remains explicit and is not broadened into a prohibition against every possible evidence-based assessment.
- An unsupported inference is not presented as an authorised creation-mode declaration or attestation.

## Declaration-source verification

- The controller, submitting application, trusted creation system and external verification service remain explicit supported sources.
- The declaration-source capability retains the source-level `SHOULD` strength.
- No identity, trust, attestation or verification mechanism is invented.

## Creation-information and preservation verification

- Structured tool and role information remains optional.
- Richer tool information is not required for every creation declaration.
- Preservation of authorised creation-mode declarations and associated creation metadata retains the source-level `SHOULD` strength.
- Declaration preservation remains distinct from proof that the declaration is true.

## Evidentiary-limit verification

- Relay v0.1 does not claim that creation-mode declarations or provenance metadata solve universal proof of human authorship.

## Illustrative-example verification

- The Section 13 declaration list and JSON generate no additional normative catalogue requirements.
- `creation`, `mode`, `tools`, `name` and `role` are not made mandatory physical field names.
- The example assistant name, `editing` role and `human-assisted` value are not treated as final schema content or wire syntax.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No closed vocabulary, field name, verification mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 10 defines creation-mode representation, inference limits, declaration sources, creation-tool information, declaration preservation and the universal-human-authorship evidentiary boundary. It generates `REL-REC-068` through `REL-REC-073` from `REM-03-124` through `REM-03-139`.

The next catalogue part should begin with source Section 14 and `REM-03-140`.

---

<!-- Part 11 -->

# EA-05-03 — Record Requirements Catalogue

## Part 11 — Record Visibility Classifications and Access Semantics

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the access-classification requirement for Relay Records, the recommended Relay v0.1 visibility classifications and the access and discovery semantics of public, unlisted, restricted and private records.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 14 and REM-03 requirements `REM-03-140` through `REM-03-151`.

It defines normative requirements governing:

- declaration or inheritance of record access classification;
- Relay v0.1 support for public, unlisted, restricted and private classifications;
- public-record readability;
- unlisted-record readability, discovery intent and ecosystem handling;
- restricted-record access authority; and
- controller and explicitly authorised service access to private records.

Source Section 15 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-141` through `REM-03-144` are consolidated because the source applies one recommendation to four access classifications. Every classification remains explicit and individually traceable. The remaining requirements are kept separate because they define independently testable access or discovery effects and, in several cases, carry different normative keywords.

The JSON in Section 14 is illustrative. It does not establish mandatory physical field names, final audience syntax or the audience rules defined in Section 15 and therefore generates no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-074

### Title

Record Access Classification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** declare or inherit an access classification.

### Rationale

An explicit or inherited classification provides the visibility context required to determine how a record may be accessed without requiring a particular physical field layout.

### Source

- REM-03-140
- `design-notes/03-record-model.md`, Section 14

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-075

### Title

Relay v0.1 Visibility Classifications

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay v0.1 **SHOULD** support the following access classifications:

- `public`;
- `unlisted`;
- `restricted`; and
- `private`.

### Rationale

The four recommended classifications provide distinct visibility modes for open access, URI-based access with reduced discovery, authority-limited access and controller-centred private access.

### Source

- REM-03-141
- REM-03-142
- REM-03-143
- REM-03-144
- `design-notes/03-record-model.md`, Section 14

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-076

### Title

Public Record Readability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A public record **MUST** be readable by any observer capable of resolving and accessing the repository through the protocol.

### Rationale

Public classification establishes open protocol readability for observers that can reach the repository. Readability does not itself grant separate reproduction, modification or usage rights.

### Source

- REM-03-145
- `design-notes/03-record-model.md`, Section 14.1

### Related Invariants

- CI-05
- AI-07

---

## REL-REC-077

### Title

Unlisted Record URI-Based Readability

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An unlisted record **MUST** be readable by an observer possessing its stable Record URI, subject to the repository being resolvable and available.

### Rationale

Unlisted access relies on possession of the stable Record URI rather than identity-based authorisation, while remaining dependent on the repository being reachable.

### Source

- REM-03-146
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- CI-05
- AI-07

---

## REL-REC-078

### Title

Unlisted Non-Indexing Intent

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An unlisted classification **MUST** signal that the record is not intended for public indexing or general discovery.

### Rationale

The signal distinguishes reduced discoverability from restricted access: an unlisted record remains readable to a holder of its URI but is not intended for general indexing or discovery.

### Source

- REM-03-147
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- AI-07

---

## REL-REC-079

### Title

Honouring Unlisted Status

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Applications and indexers **SHOULD** honour an unlisted record's non-indexing and non-discovery intent.

### Rationale

Ecosystem observance gives practical effect to unlisted status while remaining a recommendation rather than a technical guarantee against indexing or disclosure by third parties.

### Source

- REM-03-148
- `design-notes/03-record-model.md`, Section 14.2

### Related Invariants

- CI-04
- AI-07

---

## REL-REC-080

### Title

Restricted Record Access Authority

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A restricted record **MUST** be readable only by identities, applications or groups holding valid access authority for that record.

### Rationale

Restricted classification conditions readability on valid access authority rather than on possession of the Record URI alone.

### Source

- REM-03-149
- `design-notes/03-record-model.md`, Section 14.3

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-081

### Title

Private Record Controller Access

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A private record **MUST** be readable by the controller.

### Rationale

Private classification retains the controller as the primary party authorised to read the record.

### Source

- REM-03-150
- `design-notes/03-record-model.md`, Section 14.4

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-082

### Title

Private Service Explicit Authorisation

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A private service **MUST NOT** read a private record unless it has been explicitly authorised to do so.

### Rationale

Private-record access by a service requires explicit authority; general application access or repository connectivity does not establish that authority.

### Source

- REM-03-151
- `design-notes/03-record-model.md`, Section 14.4

### Related Invariants

- CI-02
- CI-06
- AI-07

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-140` | Direct | `REL-REC-074` |
| `REM-03-141` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-142` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-143` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-144` | Consolidated visibility-classification support | `REL-REC-075` |
| `REM-03-145` | Direct | `REL-REC-076` |
| `REM-03-146` | Direct | `REL-REC-077` |
| `REM-03-147` | Direct | `REL-REC-078` |
| `REM-03-148` | Direct | `REL-REC-079` |
| `REM-03-149` | Direct | `REL-REC-080` |
| `REM-03-150` | Direct | `REL-REC-081` |
| `REM-03-151` | Direct | `REL-REC-082` |

No REM entry in scope is excluded from normative catalogue generation. The consolidation of `REM-03-141` through `REM-03-144` preserves all four recommended classifications in the Statement, Source list and coverage table for `REL-REC-075`.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 14 of `design-notes/03-record-model.md`.
- Source Sections 15–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-140` through `REM-03-151`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-073`.
- First identifier in this part: `REL-REC-074`.
- Final identifier in this part: `REL-REC-082`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers are continuous and unique across Parts 1–11.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-141` through `REM-03-144` retain individual traceability through the Source list and coverage table for `REL-REC-075`.

## Classification verification

- Every Relay Record must declare or inherit an access classification.
- Declaration and inheritance remain distinct permitted means of supplying the classification.
- Public, unlisted, restricted and private support retains the source-level `SHOULD` strength.
- The four classifications retain distinct access semantics.
- No physical access-classification field layout is required.

## Public and unlisted verification

- Public records are readable by observers capable of resolving and accessing the repository through the protocol.
- Public readability does not create separate reproduction, modification or usage rights.
- An unlisted record is readable by a holder of its stable Record URI where the repository is resolvable and available.
- Unlisted access does not add an identity-authorisation requirement.
- Unlisted classification signals non-indexing and non-discovery intent.
- Applications and indexers retain the source-level `SHOULD` obligation to honour that intent.
- Unlisted status is not represented as secrecy, restricted access or a technical guarantee against third-party indexing or disclosure.

## Restricted and private verification

- Restricted readability requires valid access authority held by an identity, application or group.
- Possession of a restricted record's URI alone is not treated as sufficient authority.
- A private record remains readable by the controller.
- A private service requires explicit authorisation to read a private record.
- Controller access and private-service authorisation remain separate requirements with their respective `MUST` and `MUST NOT` keywords.

## Illustrative-example verification

- The Section 14 JSON generates no separate normative catalogue requirements.
- `visibility`, `classification` and `audience` are not made mandatory physical field names.
- The example identity, group, audience array and JSON structure are not treated as final access-control syntax.
- Section 15 audience or dynamic-audience rules are not imported from the example.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No access mechanism, field name, audience rule, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 11 defines access classification, recommended visibility modes and the access and discovery semantics of public, unlisted, restricted and private records. It generates `REL-REC-074` through `REL-REC-082` from `REM-03-140` through `REM-03-151`.

The next catalogue part should begin with source Section 15 and `REM-03-152`.

---

<!-- Part 12 -->

# EA-05-03 — Record Requirements Catalogue

## Part 12 — Restricted Audiences, Dynamic Evaluation and Access Revocation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines how restricted records may identify intended audiences, how changing relationship-based audiences determine access, how later audience membership may affect earlier records and what audience removal can and cannot revoke.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 15 and REM-03 requirements `REM-03-152` through `REM-03-165`.

It defines normative requirements governing:

- optional structured audience rules for restricted records;
- permitted identity-, application-, relationship-, group-, grant- and other rule-based audiences;
- required evaluation semantics for audiences based on changing relationships;
- permitted publication-time, access-time and alternative evaluation rules;
- schema- or record-defined treatment of later audience membership;
- revocation of future authorised access after audience removal; and
- the inability of revocation to guarantee deletion of copies already received.

Source Section 16 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-152` through `REM-03-158` are consolidated because the source introduces one permission to identify an intended audience and then enumerates six permitted audience bases. `REM-03-160` through `REM-03-162` are consolidated because the source permits three alternative dynamic-audience evaluation approaches. Every audience basis and evaluation approach remains explicit and individually traceable.

The audience examples in Section 15 are illustrative. They do not establish mandatory rules, default audience semantics, physical field names, schema vocabulary or final access-control syntax and therefore generate no separate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-083

### Title

Restricted Record Audience Declaration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A restricted record **MAY** identify its intended audience through structured audience rules using:

- specific Relay Identities;
- approved applications;
- relationship-based groups;
- named access groups;
- valid permission grants; or
- another explicitly defined access rule supported by the applicable schema or protocol.

### Rationale

Multiple optional audience bases allow restricted access to be expressed for different identity, application, relationship, group and permission contexts without requiring every record to use every basis or prescribing their resolution mechanisms.

### Source

- REM-03-152
- REM-03-153
- REM-03-154
- REM-03-155
- REM-03-156
- REM-03-157
- REM-03-158
- `design-notes/03-record-model.md`, Section 15

### Related Invariants

- CI-02
- CI-06
- CI-12
- AI-07

---

## REL-REC-084

### Title

Dynamic Audience Evaluation Rule

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An audience based on a changing relationship **MUST** define the point or rule by which audience membership and access are evaluated.

### Rationale

An explicit evaluation point or rule prevents ambiguity over whether later relationship changes affect access to records created earlier.

### Source

- REM-03-159
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-085

### Title

Dynamic Audience Evaluation Options

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A dynamic audience **MAY** define access using:

- audience membership as it existed at publication time;
- audience membership as it exists at the time of each access attempt; or
- another explicitly defined temporal or membership-evaluation rule.

### Rationale

These alternatives support snapshot, live and other defined audience semantics without selecting a universal evaluation default.

### Source

- REM-03-160
- REM-03-161
- REM-03-162
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-086

### Title

Later Audience Membership and Earlier Records

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema or individual record **MAY** define whether later audience membership grants access to records created before that membership began.

### Rationale

Schema- or record-level definition prevents a changing relationship from automatically implying either retroactive access or permanent exclusion from earlier records.

### Source

- REM-03-163
- `design-notes/03-record-model.md`, Section 15.1

### Related Invariants

- CI-12
- AI-07

---

## REL-REC-087

### Title

Future Access Revocation on Audience Removal

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Removing an identity from a record's audience **MUST** revoke that identity's future authorised access under the removed audience rule.

### Rationale

Audience removal must end future access that depended on the removed rule, while remaining distinct from deletion of information the identity previously received.

### Source

- REM-03-164
- `design-notes/03-record-model.md`, Section 15.2

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-088

### Title

No Received-Copy Deletion Guarantee

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay protocol **MUST NOT** represent audience removal or access revocation as guaranteeing deletion of copies already received by a former audience member.

### Rationale

Revocation can terminate future protocol-authorised access but cannot ensure that a recipient deletes information already obtained.

### Source

- REM-03-165
- `design-notes/03-record-model.md`, Section 15.2

### Related Invariants

- AI-07

---

# 4. REM coverage and consolidation

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-152` | Consolidated restricted-audience permission | `REL-REC-083` |
| `REM-03-153` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-154` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-155` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-156` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-157` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-158` | Consolidated permitted audience basis | `REL-REC-083` |
| `REM-03-159` | Direct | `REL-REC-084` |
| `REM-03-160` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-161` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-162` | Consolidated dynamic-audience evaluation option | `REL-REC-085` |
| `REM-03-163` | Direct | `REL-REC-086` |
| `REM-03-164` | Direct | `REL-REC-087` |
| `REM-03-165` | Direct | `REL-REC-088` |

No REM entry in scope is excluded from normative catalogue generation. Both consolidations preserve every enumerated audience basis or evaluation option in the relevant Statement, Source list and coverage row.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 15 of `design-notes/03-record-model.md`.
- Source Sections 16–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-152` through `REM-03-165`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-082`.
- First identifier in this part: `REL-REC-083`.
- Final identifier in this part: `REL-REC-088`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–12.

## Traceability verification

- Every REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- `REM-03-152` through `REM-03-158` retain individual traceability through the Source list and coverage table for `REL-REC-083`.
- `REM-03-160` through `REM-03-162` retain individual traceability through the Source list and coverage table for `REL-REC-085`.

## Restricted-audience verification

- All six restricted-audience bases remain explicit and optional.
- No restricted record is required to use every audience basis.
- No identity, application-approval, group-membership, permission-grant or access-rule resolution mechanism is invented.

## Dynamic-audience verification

- An audience based on a changing relationship must define its access-evaluation point or rule.
- Publication-time, access-time and alternative evaluation remain permitted options.
- No universal evaluation default is selected.
- A schema or individual record may define whether later audience membership grants access to earlier records.
- Later followers or group members are not assumed always to receive access to earlier records.

## Audience-removal verification

- Removing an identity from an audience revokes future authorised access under the removed audience rule.
- Future access revocation remains distinct from deletion of information already received.
- Audience removal and access revocation are not represented as guaranteeing deletion of received copies.
- No mechanism for deleting external copies is invented.

## Illustrative-example verification

- Section 15 audience examples generate no separate normative catalogue requirements.
- “Only Bob”, “Only current collaborators”, “Only Application X”, membership-credential holders and “Visible to current followers” are not made mandatory rules, schema vocabulary or default access semantics.
- No physical audience-field name or final access-control syntax is inferred from an example.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No usage-rights requirement, access mechanism, audience default, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 12 defines restricted-audience declarations, dynamic-audience evaluation, later-membership treatment and the effects and limits of audience removal. It generates `REL-REC-083` through `REL-REC-088` from `REM-03-152` through `REM-03-165`.

The next catalogue part should begin with source Section 16 and `REM-03-166`.

---

<!-- Part 13 -->

# EA-05-03 — Record Requirements Catalogue

## Part 13 — Usage-Rights Expression and Enforcement Boundaries

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the separation between record visibility and usage rights, the limits of rights implied by public visibility, structured usage-rights expression and the boundary between protocol expression and external enforcement.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 16 and REM-03 requirements `REM-03-166` through `REM-03-184`.

It defines normative requirements governing:

- separation of record visibility from usage rights;
- limitations on rights implied by public visibility;
- optional structured rights declarations;
- protocol capability to represent structured usage-rights terms;
- the absence of guaranteed external compliance; and
- permitted external enforcement dependencies.

Source Section 17 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-167` through `REM-03-171` are consolidated because the source applies one public-visibility qualification to five usage categories. `REM-03-180` through `REM-03-184` are consolidated because the source permits reliance on five external enforcement mechanisms. Every limitation and enforcement dependency remains explicit and individually traceable.

`REM-03-173` through `REM-03-177` are explicit Non-normative model examples. They illustrate possible rights terms but do not establish final rights fields, term names, vocabulary values or enforceability rules and therefore generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-089

### Title

Visibility and Usage-Rights Separation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** represent record visibility separately from record usage rights.

### Rationale

Permission to view a record does not itself establish permission to reproduce, modify, commercially exploit, syndicate or use that record for model training.

### Source

- REM-03-166
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- AI-07

---

## REL-REC-090

### Title

Public Visibility Does Not Grant Unlimited Usage Rights

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Public visibility **MUST NOT** be interpreted as an unlimited grant to:

- reproduce the record;
- commercially exploit the record;
- use the record for model training;
- modify the record or create derivatives; or
- syndicate or redistribute the record.

### Rationale

Public readability determines access, not the separate terms governing downstream use of the record.

### Source

- REM-03-167
- REM-03-168
- REM-03-169
- REM-03-170
- REM-03-171
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- AI-07

---

## REL-REC-091

### Title

Structured Rights Declaration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** include a structured rights declaration.

### Rationale

A structured declaration allows usage terms to accompany a record without requiring every record to contain one or fixing a final rights vocabulary in this section.

### Source

- REM-03-172
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-092

### Title

Protocol Usage-Rights Expression Capability

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Protocol **MUST** be capable of representing structured usage-rights terms associated with a record.

### Rationale

Protocol-level expression enables interoperable communication of usage terms while remaining distinct from enforcement or guaranteed compliance.

### Source

- REM-03-178
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08
- CI-12

---

## REL-REC-093

### Title

No Guarantee of External Rights Compliance

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay Protocol **MUST NOT** represent structured usage-rights terms as a guarantee that every external observer will obey them.

### Rationale

The protocol can express usage terms, but metadata alone cannot ensure the behaviour of every observer after information has been disclosed.

### Source

- REM-03-179
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-08

---

## REL-REC-094

### Title

External Usage-Rights Enforcement Dependencies

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Enforcement of declared usage rights **MAY** depend on:

- contractual mechanisms outside the Relay Protocol;
- application policies;
- technical controls;
- licensing systems; or
- applicable law.

### Rationale

Usage-rights enforcement may rely on mechanisms beyond protocol expression without requiring every declaration to use every mechanism or selecting how any mechanism operates.

### Source

- REM-03-180
- REM-03-181
- REM-03-182
- REM-03-183
- REM-03-184
- `design-notes/03-record-model.md`, Section 16

### Related Invariants

- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-166` | Direct | `REL-REC-089` |
| `REM-03-167` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-168` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-169` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-170` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-171` | Consolidated public-visibility limitation | `REL-REC-090` |
| `REM-03-172` | Direct | `REL-REC-091` |
| `REM-03-173` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative view term |
| `REM-03-174` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative redistribution term |
| `REM-03-175` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative commercial-use term |
| `REM-03-176` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative model-training term |
| `REM-03-177` | Excluded from normative catalogue generation | Explicit Non-normative model example; illustrative derivative-work term |
| `REM-03-178` | Direct | `REL-REC-092` |
| `REM-03-179` | Direct | `REL-REC-093` |
| `REM-03-180` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-181` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-182` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-183` | Consolidated external enforcement dependency | `REL-REC-094` |
| `REM-03-184` | Consolidated external enforcement dependency | `REL-REC-094` |

Every normative REM entry in scope maps to one catalogue requirement. `REM-03-173` through `REM-03-177` remain explicitly accounted for but generate no normative requirements because their source material is illustrative example JSON.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 16 of `design-notes/03-record-model.md`.
- Source Sections 17–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-166` through `REM-03-184`.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-088`.
- First identifier in this part: `REL-REC-089`.
- Final identifier in this part: `REL-REC-094`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers are continuous and unique across Parts 1–13.

## Traceability verification

- Every normative REM entry in scope maps to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- `REM-03-167` through `REM-03-171` retain individual traceability through the Source list and coverage table for `REL-REC-090`.
- `REM-03-180` through `REM-03-184` retain individual traceability through the Source list and coverage table for `REL-REC-094`.
- `REM-03-173` through `REM-03-177` remain explicitly accounted for as non-normative exclusions.

## Visibility and usage-rights verification

- Record visibility remains separate from record usage rights.
- Public visibility does not imply unlimited reproduction, commercial-exploitation, model-training, modification, derivative-work, syndication or redistribution rights.
- All five public-visibility limitations remain explicit and independently traceable.

## Rights-expression verification

- Record inclusion of a structured rights declaration retains the source-level `MAY` strength.
- Protocol capability to represent structured usage-rights terms retains the source-level `MUST` strength.
- The record-level permission and protocol-level capability remain separate requirements.
- Rights expression is not treated as enforcement or guaranteed compliance.

## External-enforcement verification

- The protocol does not represent rights terms as a guarantee of external-observer compliance.
- Contracts, application policies, technical controls, licensing systems and applicable law remain explicit optional enforcement dependencies.
- No declaration is required to use every enforcement dependency.
- No contractual term, application policy, technical control, licensing system, legal remedy or jurisdictional rule is selected or invented.

## Non-normative and illustrative-example verification

- `REM-03-173` through `REM-03-177` generate no normative catalogue requirements.
- The Section 16 JSON generates no normative catalogue requirements.
- `rights`, `view`, `redistribution`, `commercialUse`, `modelTraining` and `derivatives` are not made mandatory physical field names.
- `public`, `attribution-required`, `prohibited` and `permission-required` are not treated as final or mandatory vocabulary values.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each new catalogue requirement carries one explicit normative keyword.
- No rights vocabulary, enforcement mechanism, schema content, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 13 defines visibility and usage-rights separation, public-visibility limitations, structured rights expression and external-enforcement boundaries. It generates `REL-REC-089` through `REL-REC-094` from normative material in `REM-03-166` through `REM-03-184`, while explicitly excluding five non-normative example entries.

The next catalogue part should begin with source Section 17 and `REM-03-185`.

---

<!-- Part 14 -->

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

---

<!-- Part 15 -->

# EA-05-03 — Record Requirements Catalogue

## Part 15 — Layered Record Validation and Protocol-Validity Boundaries

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the layered Relay record-validation model, the distinct purpose of each substantive validation layer and the boundary between application-specific semantic checks and protocol validity.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 18 and REM-03 requirements `REM-03-193` through `REM-03-219`.

It defines normative requirements governing:

- separation of record validation into multiple levels;
- envelope, schema, authority and repository-state validation;
- optional application semantic validation; and
- separation of application-specific semantic validation from protocol validity.

Source Section 19 and later sections are intentionally deferred to subsequent catalogue parts. Section 17 canonical-creation conditions are not duplicated.

`REM-03-195` through `REM-03-199`, `REM-03-201` through `REM-03-204`, `REM-03-206` through `REM-03-209`, `REM-03-211` through `REM-03-214`, and `REM-03-216` through `REM-03-218` are explicit Non-normative validation examples. They illustrate possible checks within the five validation layers but do not establish mandatory algorithms, exhaustive checklists or final protocol rules and therefore generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-097

### Title

Multi-Level Record Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Relay record validation **MUST** distinguish multiple validation levels rather than treating all validity questions as one undifferentiated check.

### Rationale

Separating envelope, schema, authority, repository-state and semantic validation preserves the different questions each layer answers and prevents success at one layer from being interpreted as success at every other layer.

### Source

- REM-03-193
- `design-notes/03-record-model.md`, Section 18

### Related Invariants

- CI-08

---

## REL-REC-098

### Title

Envelope Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Envelope validation **MUST** check the record's protocol-level structure.

### Rationale

Envelope validation establishes structural protocol conformance while remaining distinct from schema-defined content, operation authority, repository state and application-specific meaning.

### Source

- REM-03-194
- `design-notes/03-record-model.md`, Section 18.1

### Related Invariants

- CI-08

---

## REL-REC-099

### Title

Schema Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Schema validation **MUST** check record content against the record's declared schema.

### Rationale

The declared schema supplies the applicable content constraints without allowing private application assumptions to substitute for schema conformance.

### Source

- REM-03-200
- `design-notes/03-record-model.md`, Section 18.2

### Related Invariants

- CI-08

---

## REL-REC-100

### Title

Authority Validation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Authority validation **MUST** determine whether the record operation was authorised.

### Rationale

Structural or schema validity does not establish that an operation was performed under valid authority.

### Source

- REM-03-205
- `design-notes/03-record-model.md`, Section 18.3

### Related Invariants

- CI-06
- CI-08

---

## REL-REC-101

### Title

Repository-State Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Repository-state validation **MUST** check the proposed operation against the repository's current state.

### Rationale

An operation can be structurally and schema-valid yet remain inconsistent with the repository state against which it is proposed.

### Source

- REM-03-210
- `design-notes/03-record-model.md`, Section 18.4

### Related Invariants

- AI-01
- CI-08

---

## REL-REC-102

### Title

Optional Application Semantic Validation

**Level:** Application

**Normative Keyword:** **MAY**

### Statement

An application **MAY** perform additional semantic or meaning-based validation checks.

### Rationale

Applications may evaluate meaning or suitability for their own contexts without making those checks universal protocol-validity conditions.

### Source

- REM-03-215
- `design-notes/03-record-model.md`, Section 18.5

### Related Invariants

- AI-07

---

## REL-REC-103

### Title

Semantic Validation Separate from Protocol Validity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Application-specific semantic validation **MUST** remain distinct from protocol validity.

### Rationale

An application may reject or hide a protocol-valid record under its own meaning-based or policy checks without making that record protocol-invalid.

### Source

- REM-03-219
- `design-notes/03-record-model.md`, Section 18.5

### Related Invariants

- AI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-193` | Direct | `REL-REC-097` |
| `REM-03-194` | Direct | `REL-REC-098` |
| `REM-03-195` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative URI check |
| `REM-03-196` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative identifier check |
| `REM-03-197` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative required-metadata check |
| `REM-03-198` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative encoding check |
| `REM-03-199` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative timestamp check |
| `REM-03-200` | Direct | `REL-REC-099` |
| `REM-03-201` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative required-field check |
| `REM-03-202` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative value-type check |
| `REM-03-203` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative length-constraint check |
| `REM-03-204` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative reference-constraint check |
| `REM-03-205` | Direct | `REL-REC-100` |
| `REM-03-206` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative controller-signature check |
| `REM-03-207` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative delegated-grant check |
| `REM-03-208` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative key-revocation check |
| `REM-03-209` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative authorisation-scope check |
| `REM-03-210` | Direct | `REL-REC-101` |
| `REM-03-211` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative Record Key uniqueness check |
| `REM-03-212` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative current-version check |
| `REM-03-213` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative referenced-commit check |
| `REM-03-214` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative singleton-constraint check |
| `REM-03-215` | Direct | `REL-REC-102` |
| `REM-03-216` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative URL-reachability check |
| `REM-03-217` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative media-suitability check |
| `REM-03-218` | Excluded from normative catalogue generation | Explicit Non-normative validation example; illustrative community-policy check |
| `REM-03-219` | Direct | `REL-REC-103` |

Every normative REM entry in scope maps directly to one catalogue requirement. All twenty non-normative validation examples remain explicitly accounted for but generate no normative catalogue requirements.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 18 of `design-notes/03-record-model.md`.
- Source Sections 19–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-193` through `REM-03-219`.
- Section 17 canonical-creation conditions are not duplicated.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-096`.
- First identifier in this part: `REL-REC-097`.
- Final identifier in this part: `REL-REC-103`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–15.

## Traceability verification

- Every normative REM entry in scope maps directly to one catalogue requirement.
- Every catalogue requirement cites one in-scope REM identifier and the authoritative design-note subsection.
- Every non-normative example REM entry is individually identified in the coverage table.
- No normative REM entries are consolidated or accounted for through an existing catalogue requirement in this part.

## Validation-layer verification

- Envelope, schema, authority, repository-state and semantic validation remain distinct and traceable.
- Success at one validation layer is not represented as automatically establishing success at another layer.
- Envelope validation remains limited to protocol-level structure.
- Schema validation remains tied to content and the declared schema.
- Authority validation remains tied to whether the operation was authorised.
- Repository-state validation remains tied to checking the operation against current repository state.
- Application semantic validation retains the source-level `MAY` strength.

## Protocol-validity boundary verification

- Application-specific semantic validation remains distinct from protocol validity.
- Application rejection or hiding under a meaning-based or policy check is not represented as making an otherwise protocol-valid record protocol-invalid.
- No application-specific semantic criterion is promoted into a universal protocol-validity condition.

## Non-normative validation-example verification

- `REM-03-195` through `REM-03-199`, `REM-03-201` through `REM-03-204`, `REM-03-206` through `REM-03-209`, `REM-03-211` through `REM-03-214`, and `REM-03-216` through `REM-03-218` generate no normative catalogue requirements.
- The example lists are not treated as exhaustive validation algorithms, mandatory checklists or final protocol rules.
- No example-derived URI, identifier, metadata, encoding, timestamp, field, type, length, reference, signature, grant, key, scope, state, version, commit, singleton, reachability, suitability or policy mechanism is invented or selected.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their source REM entries.
- Each catalogue requirement carries one explicit normative keyword.
- No validation rule, algorithm, field name, schema detail, authority mechanism, repository-state procedure, application policy, implementation detail or requirement has been imported from another Record Model section.

---

# 6. Part conclusion

Part 15 establishes a layered record-validation model and preserves the boundary between optional application-specific semantic checks and protocol validity.

The next catalogue part should address Section 19 and record-update semantics.

---

<!-- Part 16 -->

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

---

<!-- Part 17 -->

# EA-05-03 — Record Requirements Catalogue

## Part 17 — Schema-Defined Immutability and Historical Integrity

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines schema-selected record immutability, the explicit lifecycle treatments available to immutable records and the prohibition against concealed rewriting of their historical assertions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 20 and REM-03 requirements `REM-03-235` through `REM-03-244`.

It defines normative requirements governing:

- a schema's permission to define records as immutable after creation;
- revocation, supersession, annotation and legally necessary deletion of immutable records; and
- protection against concealed rewriting of an immutable record's original assertion.

Source Section 21 and later sections are intentionally deferred to subsequent catalogue parts. No deletion or tombstone requirement from Section 21 is imported.

`REM-03-236` through `REM-03-239` derive from the source's illustrative examples of record types that may be immutable. Signed credentials, historical attestations, issued receipts and completed audit events do not establish mandatory, exhaustive or separate immutable-record categories and therefore generate no catalogue requirements.

`REM-03-240` through `REM-03-243` are consolidated because the source applies one permission to four explicit lifecycle treatments for immutable records. Each treatment and the legal-necessity qualification on deletion remain explicit and individually traceable.

---

# 3. Requirements

---

## REL-REC-110

### Title

Schema-Defined Record Immutability

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define conforming records as immutable after creation.

### Rationale

Immutability is an optional schema-defined behaviour rather than a property imposed universally on every Relay Record or schema.

### Source

- REM-03-235
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-08

---

## REL-REC-111

### Title

Explicit Immutable-Record Lifecycle Treatments

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Without rewriting its original immutable content, an immutable record **MAY** be:

- revoked;
- superseded;
- annotated; or
- deleted where legally necessary.

### Rationale

Immutability protects original content from concealed alteration while allowing explicit lifecycle events and legally necessary deletion. The requirement does not prescribe how any treatment is represented or implemented.

### Source

- REM-03-240
- REM-03-241
- REM-03-242
- REM-03-243
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-112

### Title

No Concealed Rewriting of Immutable Records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An immutable record **MUST NOT** be silently rewritten in a manner that presents its original assertion as though it had always contained different content.

### Rationale

Historical integrity requires corrections or lifecycle changes to remain explicit rather than retrospectively replacing the original assertion without disclosure.

### Source

- REM-03-244
- `design-notes/03-record-model.md`, Section 20

### Related Invariants

- CI-07
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-235` | Direct | `REL-REC-110` |
| `REM-03-236` | Excluded from separate catalogue generation | Illustrative signed-credential example; does not establish a mandatory or separate immutable-record category |
| `REM-03-237` | Excluded from separate catalogue generation | Illustrative historical-attestation example; does not establish a mandatory or separate immutable-record category |
| `REM-03-238` | Excluded from separate catalogue generation | Illustrative issued-receipt example; does not establish a mandatory or separate immutable-record category |
| `REM-03-239` | Excluded from separate catalogue generation | Illustrative completed-audit-event example; does not establish a mandatory or separate immutable-record category |
| `REM-03-240` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-241` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-242` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-243` | Consolidated immutable-record lifecycle treatment | `REL-REC-111` |
| `REM-03-244` | Direct | `REL-REC-112` |

Every REM entry in scope is represented directly, accounted for through justified consolidation or explicitly excluded from separate catalogue generation because its authoritative source content is illustrative.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 20 of `design-notes/03-record-model.md`.
- Source Sections 21–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-235` through `REM-03-244`.
- No Section 21 deletion or tombstone requirement is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-109`.
- First identifier in this part: `REL-REC-110`.
- Final identifier in this part: `REL-REC-112`.
- Total catalogue requirements in this part: 3.
- Catalogue identifiers are continuous and unique across Parts 1–17.

## Traceability verification

- Every normative source rule in scope maps directly or through justified consolidation to one catalogue requirement.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section.
- All four lifecycle treatments retain individual traceability through the Source list and coverage table for `REL-REC-111`.
- All four illustrative record types remain individually accounted for without generating separate catalogue requirements.

## Schema-defined immutability verification

- Schema-defined immutability retains `MAY` strength.
- Immutability is not imposed on every Relay Record or every schema.
- Signed credentials, historical attestations, issued receipts and completed audit events remain illustrative rather than mandatory, exhaustive or closed immutable-record categories.
- No listed example type is required to use immutable lifecycle behaviour.

## Immutable-record lifecycle verification

- Revocation, supersession, annotation and legally necessary deletion remain explicit, optional and independently traceable.
- The deletion permission retains the qualification that deletion is legally necessary.
- Revocation, supersession and annotation preserve the original immutable content.
- No lifecycle treatment mechanism, field name or schema structure is selected or invented.

## Historical-integrity verification

- Concealed rewriting remains prohibited with `MUST NOT` strength.
- The prohibition remains distinct from the permitted explicit lifecycle treatments.
- Immutability is not interpreted as prohibiting revocation, supersession, annotation or legally necessary deletion.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No deletion rule, tombstone rule, terminology, qualification or implementation detail has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 17 establishes schema-defined immutability, permits explicit immutable-record lifecycle treatments and prohibits concealed rewriting of original assertions.

The next catalogue part should address Section 21 and record deletion.

---

<!-- Part 18 -->

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

---

<!-- Part 19 -->

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

---

<!-- Part 20 -->

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

---

<!-- Part 21 -->

# EA-05-03 — Record Requirements Catalogue

## Part 21 — Schema-Defined Record Expiration

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines optional schema-level and record-level expiration, the permitted meanings of expiration and the schema obligation to identify which consequences apply.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 24 and REM-03 requirements `REM-03-268` through `REM-03-274`.

It defines normative requirements governing expiration definition, the four source-defined expiration interpretations and explicit schema selection of applicable consequences.

Source Section 25 and later sections are intentionally deferred to subsequent catalogue parts. No inter-record reference requirement from Section 25 is imported.

`REM-03-270` through `REM-03-273` are consolidated because they are four compatible schema-selectable interpretations of expiration. Each interpretation remains explicit and individually traceable. The illustrative record types and JSON generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-129

### Title

Schema-Defined Expiration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define expiration behaviour and an expiration time for conforming records.

### Rationale

Expiration is optional schema-defined lifecycle behaviour and is not imposed on every schema or record.

### Source

- REM-03-268
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-130

### Title

Record-Defined Expiration Time

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A record **MAY** define an expiration time where the applicable schema permits or supports it.

### Rationale

A record-level expiration value is optional and remains governed by the applicable schema rather than establishing independent expiration semantics.

### Source

- REM-03-269
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-131

### Title

Permitted Expiration Interpretations

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define expiration to mean one or more of the following:

- the record is no longer publicly displayed;
- the record is no longer valid as an assertion;
- the record is no longer accessible; or
- the record is eligible for deletion.

### Rationale

The source permits distinct expiration consequences without making any one consequence universal or treating deletion eligibility as completed deletion.

### Source

- REM-03-270
- REM-03-271
- REM-03-272
- REM-03-273
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

## REL-REC-132

### Title

Explicit Schema Interpretation of Expiration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema supporting expiration **MUST** specify which semantic consequence or consequences of expiration apply.

### Rationale

Explicit schema semantics prevent applications from inferring public-display, assertion-validity, accessibility or deletion consequences from one another.

### Source

- REM-03-274
- `design-notes/03-record-model.md`, Section 24

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-268` | Direct | `REL-REC-129` |
| `REM-03-269` | Direct | `REL-REC-130` |
| `REM-03-270` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-271` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-272` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-273` | Consolidated expiration interpretation | `REL-REC-131` |
| `REM-03-274` | Direct | `REL-REC-132` |

Every REM entry in scope maps directly or through justified consolidation to a catalogue requirement. No illustrative example generates a catalogue requirement.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 24 of `design-notes/03-record-model.md`.
- Source Sections 25–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-268` through `REM-03-274`.
- No inter-record reference requirement from Section 25 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-128`.
- First identifier in this part: `REL-REC-129`.
- Final identifier in this part: `REL-REC-132`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers are continuous and unique across Parts 1–21.

## Traceability verification

- Every in-scope normative REM entry is represented directly or through justified consolidation.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- All four expiration interpretations retain individual traceability through the Source list and coverage table for `REL-REC-131`.

## Expiration-definition verification

- Schema-level and record-level expiration retain `MAY` strength.
- No schema or record is universally required to expire.
- A record-level expiration time remains subject to applicable schema support.

## Expiration-semantics verification

- End of public display, assertion invalidity, loss of access and deletion eligibility remain distinct schema-selectable meanings.
- Deletion eligibility is not treated as deletion having occurred.
- A supporting schema must identify the applicable consequence or consequences.
- Temporary announcements, access invitations, credentials, statuses and the illustrative `expiresAt` JSON generate no normative requirements or mandatory vocabulary.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 21 defines optional record expiration and requires schemas that support it to state its applicable semantic consequences.

The next catalogue part should address Section 25.

---

<!-- Part 22 -->

# EA-05-03 — Record Requirements Catalogue

## Part 22 — Inter-Record References, Version Pinning and Unavailable Targets

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part defines stable inter-record references, semantic relationship identification, logical and version-pinned targets and accurate handling when referenced targets become unavailable.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 25 and REM-03 requirements `REM-03-275` through `REM-03-281`.

It defines normative requirements governing reference addressing, reference semantics, target version selection, exact-version integrity and unavailable-target behaviour.

Source Section 26 and later sections are intentionally deferred to subsequent catalogue parts. No embedding or provenance requirement from Section 26 is imported.

The seven in-scope REM entries remain separate because each establishes an independently testable permission, recommendation, validity rule or application obligation. The example relationship names and JSON generate no catalogue requirements.

---

# 3. Requirements

---

## REL-REC-133

### Title

Stable Record URI References

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** refer to another Relay Record using the target's stable Record URI.

### Rationale

Stable Record URI references allow relationships to survive changes of application, provider or storage location.

### Source

- REM-03-275
- `design-notes/03-record-model.md`, Section 25

### Related Invariants

- CI-02
- CI-08

---

## REL-REC-134

### Title

Semantic Relationship Identification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An inter-record reference **SHOULD** identify the semantic relationship between the referring record and its target.

### Rationale

Identifying reference semantics allows applications to interpret the relationship without selecting the illustrative relationship names as a mandatory vocabulary.

### Source

- REM-03-276
- `design-notes/03-record-model.md`, Section 25

### Related Invariants

- CI-08

---

## REL-REC-135

### Title

Logical-Record Reference

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reference **MAY** point to the continuing logical record without identifying a specific historical Record Version.

### Rationale

Logical-record references follow the continuing record identity and may resolve to its current version at access time.

### Source

- REM-03-277
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-136

### Title

Version-Pinned Reference

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reference **MAY** identify a specific historical Record Version.

### Rationale

Version pinning preserves the exact historical state selected by the referring record.

### Source

- REM-03-278
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-137

### Title

Exact-Version References for Verifiable Observations

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A quotation or signed assertion **SHOULD** use a version-pinned reference where verification depends on the exact record state observed at the time.

### Rationale

Pinning the observed version prevents later changes to the current logical record from altering the state on which verification depends.

### Source

- REM-03-279
- `design-notes/03-record-model.md`, Section 25.1

### Related Invariants

- CI-07
- CI-08

---

## REL-REC-138

### Title

Referring-Record Validity After Target Unavailability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A referring record **MUST NOT** become invalid solely because its referenced target later becomes deleted, restricted, unavailable, migrated or blocked by an application.

### Rationale

Target availability can change without changing the validity of the referring record itself.

### Source

- REM-03-280
- `design-notes/03-record-model.md`, Section 25.2

### Related Invariants

- CI-08

---

## REL-REC-139

### Title

Accurate Handling of Unavailable Reference Targets

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An application **MUST** accurately represent and handle a referenced target that is deleted, restricted, unavailable, migrated or blocked.

### Rationale

Accurate handling preserves the distinction between an unavailable target and an invalid referring record without prescribing a particular user interface or recovery mechanism.

### Source

- REM-03-281
- `design-notes/03-record-model.md`, Section 25.2

### Related Invariants

- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-275` | Direct | `REL-REC-133` |
| `REM-03-276` | Direct | `REL-REC-134` |
| `REM-03-277` | Direct | `REL-REC-135` |
| `REM-03-278` | Direct | `REL-REC-136` |
| `REM-03-279` | Direct | `REL-REC-137` |
| `REM-03-280` | Direct | `REL-REC-138` |
| `REM-03-281` | Direct | `REL-REC-139` |

Every REM entry in scope maps directly to one catalogue requirement. No REM entry is consolidated or excluded because of non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 25 of `design-notes/03-record-model.md`.
- Source Sections 26–48 are outside this part and have not been used to create requirements.
- The verified extraction range is limited to `REM-03-275` through `REM-03-281`.
- No embedding or provenance requirement from Section 26 is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-132`.
- First identifier in this part: `REL-REC-133`.
- Final identifier in this part: `REL-REC-139`.
- Total catalogue requirements in this part: 7.
- Catalogue identifiers are continuous and unique across Parts 1–22.

## Traceability verification

- Every in-scope normative REM entry is represented directly or through justified consolidation.
- Every catalogue requirement cites at least one in-scope REM identifier and the authoritative design-note section or subsection.
- Logical-record and version-pinned references remain separately traceable.
- Referring-record validity and application handling remain separate obligations.

## Reference-target verification

- Stable Record URI addressing retains `MAY` strength.
- Semantic relationship identification retains `SHOULD` strength.
- Logical-record and specific-version references remain distinct permissions.
- Exact-version referencing remains a `SHOULD` recommendation limited to cases where verification depends on the observed state.

## Unavailable-target verification

- Later target deletion, restriction, unavailability, migration or application blocking does not by itself invalidate the referring record.
- Applications remain responsible for accurate representation and handling of unavailable targets.
- No target content, substitute record, user-interface behaviour or recovery mechanism is invented.

## Illustrative-example verification

- The example relationship names and JSON generate no normative catalogue requirements.
- No example field name, relationship term, URI or structure becomes mandatory.

## Normative-language verification

- Catalogue statements preserve the normative strength and qualifications of their authoritative source.
- Each catalogue requirement carries one explicit normative keyword.
- No terminology, qualification, implementation detail or requirement has been imported from later Record Model sections.

---

# 6. Part conclusion

Part 22 defines resilient inter-record references, preserves logical and historical target choices and requires accurate handling of unavailable targets.

The next catalogue part should address Section 26.

---

<!-- Part 23 -->

# EA-05-03 — Record Requirements Catalogue

## Part 23 — Embedded content

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 26, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 26 and REM-03 entries `REM-03-282` through `REM-03-291`.

Source Section 27 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-283`, `REM-03-284`, `REM-03-285`, `REM-03-286`, `REM-03-288`, `REM-03-289`, `REM-03-290` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-140

### Title

Limited embedded representation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** contain a limited embedded representation of another object.

### Rationale

The source permits limited representations such as quoted text, thumbnails, preview titles or an author handle observed at publication time. An embed is not a complete replacement for the referenced source object.

### Source

- REM-03-282
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

## REL-REC-141

### Title

Provenance for embedded content

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Embedded content **SHOULD** include provenance sufficient to identify its source and observation context.

### Rationale

Useful provenance may include the source Record URI, observed version and observation time, as illustrated by the source example.

### Source

- REM-03-287
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

- CI-10

---

## REL-REC-142

### Title

Embed Treatment as Historical Observation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An application **MUST** treat an embed as a historical observation.

### Rationale

Applications may separately resolve the source Record URI to obtain current state, but must not silently overwrite the historical meaning of the embed.

### Source

- REM-03-291
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

- CI-10

---

## REL-REC-143

### Title

No Assumption That an Embed Is Current

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** assume that an embed necessarily represents the current state of the source record.

### Rationale

Applications may separately resolve the source Record URI to obtain current state, but must not silently overwrite the historical meaning of the embed.

### Source

- REM-03-291
- `design-notes/03-record-model.md`, Section 26

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-282` | Direct | `REL-REC-140` |
| `REM-03-283` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-284` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-285` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-286` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-287` | Direct | `REL-REC-141` |
| `REM-03-288` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-289` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-290` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-291` | Decomposed to preserve distinct normative effects | `REL-REC-142` and `REL-REC-143` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 26 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-282` through `REM-03-291`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-139`.
- First identifier in this part: `REL-REC-140`.
- Final identifier in this part: `REL-REC-143`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–23.

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

Part 23 catalogues the settled normative content of Record Model Section 26 and excludes 7 explicitly non-normative entries.

The next catalogue part should address Section 27.

---

<!-- Part 24 -->

# EA-05-03 — Record Requirements Catalogue

## Part 24 — Blob references

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 27, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 27 and REM-03 entries `REM-03-292` through `REM-03-299`.

Source Section 28 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-144

### Title

Blob-reference support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Record **MAY** refer to one or more blobs.

### Rationale

Blobs may hold binary or large content while the record retains protocol metadata and references.

### Source

- REM-03-292
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-145

### Title

Blob identifier

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A blob reference **SHOULD** include a blob identifier.

### Rationale

The blob identifier should provide stable identity independent of a temporary delivery URL.

### Source

- REM-03-293
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-146

### Title

Blob media type

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference **SHOULD** include the blob’s media type.

### Rationale

Media type enables applications to determine whether and how they can process or present the referenced content.

### Source

- REM-03-294
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-147

### Title

Blob intended role

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference **SHOULD** identify the intended role or purpose of the blob within the record.

### Rationale

Examples may include primary image, attachment, thumbnail or another schema-defined purpose.

### Source

- REM-03-295
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-148

### Title

Blob accessibility metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference **SHOULD** include accessibility metadata where applicable.

### Rationale

The example uses alternative text for an image. Other media may require captions, transcripts or schema-specific accessibility information.

### Source

- REM-03-296
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-149

### Title

Optional blob dimensions or duration

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A blob reference **MAY** include dimensions or duration where relevant to the referenced media.

### Rationale

Dimensions are relevant to visual media, while duration is relevant to audio, video or time-based media.

### Source

- REM-03-297
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

None identified.

---

## REL-REC-150

### Title

Blob integrity hash

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A blob reference **SHOULD** include an integrity hash.

### Rationale

The hash enables applications or repositories to verify that retrieved blob content matches the referenced object.

### Source

- REM-03-298
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

- CI-10
- CI-08

---

## REL-REC-151

### Title

Temporary URL not permanent blob identity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Record **MUST NOT** treat a temporary storage or delivery URL as the permanent identity of a blob.

### Rationale

Temporary URLs may expire, rotate or change providers. Stable blob identity must remain independent of the current retrieval location.

### Source

- REM-03-299
- `design-notes/03-record-model.md`, Section 27

### Related Invariants

- CI-05

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-292` | Direct | `REL-REC-144` |
| `REM-03-293` | Direct | `REL-REC-145` |
| `REM-03-294` | Direct | `REL-REC-146` |
| `REM-03-295` | Direct | `REL-REC-147` |
| `REM-03-296` | Direct | `REL-REC-148` |
| `REM-03-297` | Direct | `REL-REC-149` |
| `REM-03-298` | Direct | `REL-REC-150` |
| `REM-03-299` | Direct | `REL-REC-151` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 27 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-292` through `REM-03-299`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-143`.
- First identifier in this part: `REL-REC-144`.
- Final identifier in this part: `REL-REC-151`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–24.

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

Part 24 catalogues the settled normative content of Record Model Section 27.

The next catalogue part should address Section 28.

---

<!-- Part 25 -->

# EA-05-03 — Record Requirements Catalogue

## Part 25 — Lists and ordering

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 28, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 28 and REM-03 entries `REM-03-300` through `REM-03-305`.

Source Section 29 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-152

### Title

Ordered-item support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support schemas for records containing ordered items.

### Rationale

Examples include portfolio ordering, image galleries, playlists and article sections.

### Source

- REM-03-300
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-153

### Title

Schema-defined ordering model

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A schema governing ordered items **MUST** define how ordering is represented or derived.

### Rationale

The source identifies three permitted models: ordering as record content, ordering derived by an application, or ordering maintained through separate relationship records.

### Source

- REM-03-301
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-154

### Title

Ordering as record content

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define ordering as part of the record content.

### Rationale

Under this model, changes to order may constitute changes to the record content and may create a new version.

### Source

- REM-03-302
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-155

### Title

Application-derived ordering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define that ordering is derived by an application rather than stored canonically in the record.

### Rationale

Applications must not imply that an application-derived order is repository-wide canonical order unless the schema establishes that meaning.

### Source

- REM-03-303
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

- CI-07

---

## REL-REC-156

### Title

Relationship-record ordering

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema **MAY** define that ordering is maintained through separate relationship records.

### Rationale

This allows order to be changed independently of the primary items being ordered.

### Source

- REM-03-304
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

## REL-REC-157

### Title

No assumed repository-wide order

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

Applications **SHOULD NOT** assume a repository-wide universal order where the applicable schema does not define one.

### Rationale

Display order may be local, contextual or application-derived unless the schema establishes canonical ordering semantics.

### Source

- REM-03-305
- `design-notes/03-record-model.md`, Section 28

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-300` | Direct | `REL-REC-152` |
| `REM-03-301` | Direct | `REL-REC-153` |
| `REM-03-302` | Direct | `REL-REC-154` |
| `REM-03-303` | Direct | `REL-REC-155` |
| `REM-03-304` | Direct | `REL-REC-156` |
| `REM-03-305` | Direct | `REL-REC-157` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 28 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-300` through `REM-03-305`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-151`.
- First identifier in this part: `REL-REC-152`.
- Final identifier in this part: `REL-REC-157`.
- Total catalogue requirements in this part: 6.
- Catalogue identifiers remain continuous and unique across Parts 1–25.

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

Part 25 catalogues the settled normative content of Record Model Section 28.

The next catalogue part should address Section 29.

---

<!-- Part 26 -->

# EA-05-03 — Record Requirements Catalogue

## Part 26 — Local application state

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 29, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 29 and REM-03 entries `REM-03-306` through `REM-03-314`.

Source Section 30 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-307`, `REM-03-308`, `REM-03-309`, `REM-03-310` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-158

### Title

Canonical repository exclusion for some preferences

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Applications **MUST NOT** assume that every application preference or implementation detail belongs in the canonical Relay Repository.

### Rationale

Examples that may remain local include window size, dismissed-tooltip state, temporary draft position and client-specific cache configuration.

### Source

- REM-03-306
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-159

### Title

Portability-value test for canonical inclusion

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Information or state **SHOULD** be stored in the canonical Relay Repository when preserving it across applications provides meaningful portability or continuity value to the user.

### Rationale

The criterion focuses on user value rather than technical possibility.

### Source

- REM-03-311
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07
- CI-03

---

## REL-REC-160

### Title

Discouragement of irrelevant implementation details

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The protocol **SHOULD** discourage applications from storing irrelevant implementation details in the canonical Relay Repository.

### Rationale

Excess local-state records can reduce clarity, portability and long-term repository usefulness.

### Source

- REM-03-312
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-161

### Title

Reasonable survival expectation test

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Applications **SHOULD** evaluate canonical inclusion by asking whether the person would reasonably expect the information or state to survive a change of application.

### Rationale

The test is editorial guidance for deciding whether state has meaningful portability or continuity value.

### Source

- REM-03-313
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

- CI-07

---

## REL-REC-162

### Title

Local retention where survival is not expected

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Information or state **MAY** remain local where a person would not reasonably expect it to survive a change of application.

### Rationale

This is permission, not a prohibition on portability. A schema or user choice may still justify canonical storage in a particular case.

### Source

- REM-03-314
- `design-notes/03-record-model.md`, Section 29

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-306` | Direct | `REL-REC-158` |
| `REM-03-307` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-308` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-309` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-310` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-311` | Direct | `REL-REC-159` |
| `REM-03-312` | Direct | `REL-REC-160` |
| `REM-03-313` | Direct | `REL-REC-161` |
| `REM-03-314` | Direct | `REL-REC-162` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 29 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-306` through `REM-03-314`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-157`.
- First identifier in this part: `REL-REC-158`.
- Final identifier in this part: `REL-REC-162`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–26.

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

Part 26 catalogues the settled normative content of Record Model Section 29 and excludes 4 explicitly non-normative entries.

The next catalogue part should address Section 30.

---

<!-- Part 27 -->

# EA-05-03 — Record Requirements Catalogue

## Part 27 — Draft records

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 30, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 30 and REM-03 entries `REM-03-315` through `REM-03-322`.

Source Section 31 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-163

### Title

Local draft creation before acceptance

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** create local draft records before repository acceptance.

### Rationale

Local drafting allows incomplete work to exist before it becomes a canonical repository record.

### Source

- REM-03-315
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-164

### Title

Draft non-canonicity before commit

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A draft **MUST NOT** be treated as canonical until it has been included in an accepted repository commit.

### Rationale

Local persistence or application synchronisation alone does not establish canonical repository acceptance.

### Source

- REM-03-316
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

- CI-07
- AI-02

---

## REL-REC-165

### Title

Optional private repository drafts

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Repository **MAY** support private draft records.

### Rationale

This capability is optional. A private repository-supported draft remains distinct from a fully canonical published or active record where the schema or workflow makes that distinction.

### Source

- REM-03-317
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-166

### Title

Draft incompleteness indication

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate that it is incomplete.

### Rationale

Applications should not present draft content as final or complete where that status is material to the user.

### Source

- REM-03-318
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-167

### Title

Draft synchronisation indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate whether it has been synchronised.

### Rationale

Synchronisation status is distinct from canonical repository acceptance.

### Source

- REM-03-319
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-168

### Title

Draft creating-application indication

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** identify the application that created it.

### Rationale

This helps users and other applications understand draft origin and compatibility expectations.

### Source

- REM-03-320
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-169

### Title

Cross-application draft-editability indication

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A draft **SHOULD** clearly indicate whether another application is permitted to edit it.

### Rationale

Editability may depend on schema support, repository authority, application grants and draft format compatibility.

### Source

- REM-03-321
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

None identified.

---

## REL-REC-170

### Title

No false canonical-storage representation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Applications **MUST NOT** present unsynchronised local drafts as safely stored canonical Relay Records.

### Rationale

Applications must accurately distinguish local-only state from repository-accepted canonical state so that users are not misled about durability, portability or recoverability.

### Source

- REM-03-322
- `design-notes/03-record-model.md`, Section 30

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-315` | Direct | `REL-REC-163` |
| `REM-03-316` | Direct | `REL-REC-164` |
| `REM-03-317` | Direct | `REL-REC-165` |
| `REM-03-318` | Direct | `REL-REC-166` |
| `REM-03-319` | Direct | `REL-REC-167` |
| `REM-03-320` | Direct | `REL-REC-168` |
| `REM-03-321` | Direct | `REL-REC-169` |
| `REM-03-322` | Direct | `REL-REC-170` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 30 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-315` through `REM-03-322`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-162`.
- First identifier in this part: `REL-REC-163`.
- Final identifier in this part: `REL-REC-170`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–27.

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

Part 27 catalogues the settled normative content of Record Model Section 30.

The next catalogue part should address Section 31.

---

<!-- Part 28 -->

# EA-05-03 — Record Requirements Catalogue

## Part 28 — Application-specific records

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 31, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 31 and REM-03 entries `REM-03-323` through `REM-03-330`.

Source Section 32 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-171

### Title

Custom record-type definition

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** define a custom Relay record type.

### Rationale

A custom type remains subject to the wider Relay requirements for schema definition, repository acceptance and record portability.

### Source

- REM-03-323
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-172

### Title

Portable custom records

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A custom record **SHOULD** remain portable even where only one application currently implements or understands its schema.

### Rationale

Limited ecosystem support does not justify binding the record permanently to the originating application.

### Source

- REM-03-324
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

- CI-03

---

## REL-REC-173

### Title

Preservation without rendering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** preserve an unsupported custom record without rendering its schema-defined content.

### Rationale

Preservation allows records to survive transitions through applications that do not yet understand their schema.

### Source

- REM-03-325
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-174

### Title

Limited metadata rendering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** render only the protocol-level or otherwise understood metadata of a custom record whose full schema it does not implement.

### Rationale

Limited rendering must not imply that the application has fully interpreted or validated unsupported schema content.

### Source

- REM-03-326
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-175

### Title

Interpretation after schema implementation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** interpret a custom record after implementing the applicable schema.

### Rationale

Interpretation should follow the schema’s declared structure, semantics and compatibility rules.

### Source

- REM-03-327
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-176

### Title

Permissioned transformation of custom records

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

An application **MAY** transform a custom record into another schema only where the required permission has been obtained.

### Rationale

Section 33 provides additional provenance and source-preservation requirements for translated records.

### Source

- REM-03-328
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

## REL-REC-177

### Title

Prohibition on anti-competitive obscurity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The originating application **MUST NOT** encrypt, encode or otherwise obscure a record solely to prevent competing clients from using, preserving or interpreting it.

### Rationale

This prohibition targets deliberate competitive exclusion rather than legitimate confidentiality or security controls.

### Source

- REM-03-329
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

- CI-04

---

## REL-REC-178

### Title

Security-based encryption exception

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An originating application **MAY** encrypt or obscure record content where that protection is genuinely required for user security.

### Rationale

The security purpose must be genuine and must not be used as a pretext for application lock-in.

### Source

- REM-03-330
- `design-notes/03-record-model.md`, Section 31

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-323` | Direct | `REL-REC-171` |
| `REM-03-324` | Direct | `REL-REC-172` |
| `REM-03-325` | Direct | `REL-REC-173` |
| `REM-03-326` | Direct | `REL-REC-174` |
| `REM-03-327` | Direct | `REL-REC-175` |
| `REM-03-328` | Direct | `REL-REC-176` |
| `REM-03-329` | Direct | `REL-REC-177` |
| `REM-03-330` | Direct | `REL-REC-178` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 31 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-323` through `REM-03-330`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-170`.
- First identifier in this part: `REL-REC-171`.
- Final identifier in this part: `REL-REC-178`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–28.

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

Part 28 catalogues the settled normative content of Record Model Section 31.

The next catalogue part should address Section 32.

---

<!-- Part 29 -->

# EA-05-03 — Record Requirements Catalogue

## Part 29 — Schema extension

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 32, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 32 and REM-03 entries `REM-03-331` through `REM-03-338`.

Source Section 33 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-179

### Title

Controlled schema extension

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay **SHOULD** support controlled extension of existing schemas.

### Rationale

“Controlled” indicates that extensions must remain identifiable and must not undermine required core semantics.

### Source

- REM-03-331
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

## REL-REC-180

### Title

Optional extension fields

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support optional extension fields.

### Rationale

Applications that do not understand an optional extension should still be able to preserve the underlying record.

### Source

- REM-03-332
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-181

### Title

Referenced extension records

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** represent additional information through separately referenced extension records.

### Rationale

Separate records can reduce mutation of the base record and allow independent authority or lifecycle rules.

### Source

- REM-03-333
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-182

### Title

Schema inheritance

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support schema inheritance.

### Rationale

Inheritance must not change the established meaning of inherited required core fields.

### Source

- REM-03-334
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-183

### Title

Namespaced metadata

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A schema extension mechanism **MAY** support namespaced metadata.

### Rationale

Namespacing allows independently defined extensions to coexist without redefining or colliding with core fields.

### Source

- REM-03-335
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-184

### Title

Core-field semantic immutability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A schema extension **MUST NOT** redefine, contradict or replace the established meaning of any required core field.

### Rationale

Extensions may add information but cannot silently change the semantics on which other implementations rely.

### Source

- REM-03-336
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

- CI-09

---

## REL-REC-185

### Title

Ignoring unsupported extensions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** ignore an extension it does not understand.

### Rationale

Ignoring means declining to interpret or use the extension, not deleting it.

### Source

- REM-03-337
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

## REL-REC-186

### Title

Preservation of unsupported extensions

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An application that ignores an unsupported extension **SHOULD** preserve that extension when reading, storing or rewriting the record.

### Rationale

Preservation prevents applications with partial schema support from causing silent information loss.

### Source

- REM-03-338
- `design-notes/03-record-model.md`, Section 32

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-331` | Direct | `REL-REC-179` |
| `REM-03-332` | Direct | `REL-REC-180` |
| `REM-03-333` | Direct | `REL-REC-181` |
| `REM-03-334` | Direct | `REL-REC-182` |
| `REM-03-335` | Direct | `REL-REC-183` |
| `REM-03-336` | Direct | `REL-REC-184` |
| `REM-03-337` | Direct | `REL-REC-185` |
| `REM-03-338` | Direct | `REL-REC-186` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 32 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-331` through `REM-03-338`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-178`.
- First identifier in this part: `REL-REC-179`.
- Final identifier in this part: `REL-REC-186`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–29.

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

Part 29 catalogues the settled normative content of Record Model Section 32.

The next catalogue part should address Section 33.

---

<!-- Part 30 -->

# EA-05-03 — Record Requirements Catalogue

## Part 30 — Record translation

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 33, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 33 and REM-03 entries `REM-03-339` through `REM-03-347`.

Source Section 34 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-187

### Title

Schema translation capability

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** translate a record from one schema into another schema.

### Rationale

Translation may be lossy or reversible, but those characteristics must be disclosed through provenance.

### Source

- REM-03-339
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-188

### Title

Source Record URI provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** preserve the source Record URI in its provenance.

### Rationale

The source URI links the translated result to the logical record from which it was derived.

### Source

- REM-03-340
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-189

### Title

Source schema provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** preserve the identifier of the source schema in its provenance.

### Rationale

The source schema is necessary to understand the original semantics and assess the transformation.

### Source

- REM-03-341
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-10

---

## REL-REC-190

### Title

Transformation-application provenance

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** identify the application or agent that performed the transformation.

### Rationale

This identifies the party responsible for applying the translation logic.

### Source

- REM-03-342
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-191

### Title

Transformation-time provenance

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** record when the transformation occurred.

### Rationale

Transformation time is distinct from the source record’s creation or update time.

### Source

- REM-03-343
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-192

### Title

Reversibility disclosure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** state whether the translation is reversible.

### Rationale

A translation is reversible only where the source representation can be reconstructed without unrecorded loss.

### Source

- REM-03-344
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-193

### Title

Omitted-information disclosure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A translated record **MUST** disclose any source information omitted during translation.

### Rationale

This prevents a lossy translation from being mistaken for a complete representation of the source.

### Source

- REM-03-345
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-194

### Title

No silent replacement of source records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A translation operation **MUST NOT** silently replace the source record.

### Rationale

By default, the translated record is a derived object rather than an implicit overwrite of the source.

### Source

- REM-03-346
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

None identified.

---

## REL-REC-195

### Title

Explicit authority for source replacement

**Level:** Constitutional

**Normative Keyword:** **MAY**

### Statement

A translated record **MAY** replace its source record only where the controller explicitly authorises the replacement.

### Rationale

The authorisation should be explicit and recorded through the repository operation accepting the change.

### Source

- REM-03-347
- `design-notes/03-record-model.md`, Section 33

### Related Invariants

- CI-02
- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-339` | Direct | `REL-REC-187` |
| `REM-03-340` | Direct | `REL-REC-188` |
| `REM-03-341` | Direct | `REL-REC-189` |
| `REM-03-342` | Direct | `REL-REC-190` |
| `REM-03-343` | Direct | `REL-REC-191` |
| `REM-03-344` | Direct | `REL-REC-192` |
| `REM-03-345` | Direct | `REL-REC-193` |
| `REM-03-346` | Direct | `REL-REC-194` |
| `REM-03-347` | Direct | `REL-REC-195` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 33 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-339` through `REM-03-347`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-186`.
- First identifier in this part: `REL-REC-187`.
- Final identifier in this part: `REL-REC-195`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers remain continuous and unique across Parts 1–30.

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

Part 30 catalogues the settled normative content of Record Model Section 33.

The next catalogue part should address Section 34.

---

<!-- Part 31 -->

# EA-05-03 — Record Requirements Catalogue

## Part 31 — Canonical records and projections

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 34, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 34 and REM-03 entries `REM-03-348` through `REM-03-351`.

Source Section 35 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-196

### Title

Projection definition

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Projection **MUST** be treated as an application-specific representation derived from one or more source records.

### Rationale

Examples include feed cards, profile pages, search results, résumés and recommendation scores.

### Source

- REM-03-348
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-04

---

## REL-REC-197

### Title

Projection not automatically canonical

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application-generated Projection **MUST NOT** be treated as a canonical Relay Record merely because it was derived or displayed.

### Rationale

Derived application views remain outside canonical repository history unless deliberately saved.

### Source

- REM-03-349
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-07

---

## REL-REC-198

### Title

Deliberate saving requirement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Projection **MUST** become a repository record only when the controller deliberately saves it through an authorised repository operation.

### Rationale

Automatic generation, caching or display does not satisfy the deliberate-saving requirement.

### Source

- REM-03-350
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-199

### Title

Prevention of projection pollution

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Applications **SHOULD** preserve the distinction between Projections and repository records so that transient or application-generated views do not pollute the controller’s canonical history.

### Rationale

The requirement supports meaningful canonical history rather than indiscriminate persistence of every derived presentation.

### Source

- REM-03-351
- `design-notes/03-record-model.md`, Section 34

### Related Invariants

- CI-02
- CI-07
- CI-10

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-348` | Direct | `REL-REC-196` |
| `REM-03-349` | Direct | `REL-REC-197` |
| `REM-03-350` | Direct | `REL-REC-198` |
| `REM-03-351` | Direct | `REL-REC-199` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 34 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-348` through `REM-03-351`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-195`.
- First identifier in this part: `REL-REC-196`.
- Final identifier in this part: `REL-REC-199`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–31.

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

Part 31 catalogues the settled normative content of Record Model Section 34.

The next catalogue part should address Section 35.

---

<!-- Part 32 -->

# EA-05-03 — Record Requirements Catalogue

## Part 32 — Comments and replies

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 35, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 35 and REM-03 entries `REM-03-352` through `REM-03-360`.

Source Section 36 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-353` is explicitly non-normative and does not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-200

### Title

Reply stored in replying identity’s repository

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A reply **SHOULD** normally be represented as a record in the repository of the identity that created the reply.

### Rationale

The source allows exceptional arrangements but establishes the replying identity’s repository as the normal canonical location.

### Source

- REM-03-352
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

None identified.

---

## REL-REC-201

### Title

Indexing and display by target-side services

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The provider or application serving the target record **MAY** index and display a reply stored in another identity’s repository.

### Rationale

Indexing or display does not transfer canonical authority over the reply.

### Source

- REM-03-354
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-03

---

## REL-REC-202

### Title

Reply repository remains canonical source

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The replying identity’s repository **MUST** remain the canonical source of the reply unless an explicitly authorised protocol operation changes that authority.

### Rationale

Copies, indexes and cached renderings are secondary representations.

### Source

- REM-03-355
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06
- CI-07

---

## REL-REC-203

### Title

Cross-client reply editing

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** be able to edit the reply through an authorised client other than the application that originally created it.

### Rationale

Editing remains subject to the reply schema, repository permissions and versioning rules.

### Source

- REM-03-356
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-204

### Title

Cross-client reply deletion

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** be able to delete the reply through an authorised client other than the application that originally created it.

### Rationale

Deletion remains subject to the repository’s deletion and tombstone requirements.

### Source

- REM-03-357
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-205

### Title

Target author does not own reply

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The identity controlling the target record **MUST NOT** be treated as the owner or controller of another identity’s reply merely because the reply references that target.

### Rationale

The target-side application may moderate display without acquiring canonical control of the reply record.

### Source

- REM-03-358
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-02

---

## REL-REC-206

### Title

Application-specific moderation policies

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Different applications **MAY** apply different moderation or display policies to the same reply.

### Rationale

Application-level moderation affects presentation or availability within that application and does not automatically alter the canonical reply.

### Source

- REM-03-359
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

None identified.

---

## REL-REC-207

### Title

Reply survival beyond originating application

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A canonical reply **SHOULD** remain available through its repository independently of the continued existence of the application that created it.

### Rationale

This outcome depends on repository continuity and reinforces why the application is not the canonical owner of the reply.

### Source

- REM-03-360
- `design-notes/03-record-model.md`, Section 35

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-352` | Direct | `REL-REC-200` |
| `REM-03-353` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-354` | Direct | `REL-REC-201` |
| `REM-03-355` | Direct | `REL-REC-202` |
| `REM-03-356` | Direct | `REL-REC-203` |
| `REM-03-357` | Direct | `REL-REC-204` |
| `REM-03-358` | Direct | `REL-REC-205` |
| `REM-03-359` | Direct | `REL-REC-206` |
| `REM-03-360` | Direct | `REL-REC-207` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 35 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-352` through `REM-03-360`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-199`.
- First identifier in this part: `REL-REC-200`.
- Final identifier in this part: `REL-REC-207`.
- Total catalogue requirements in this part: 8.
- Catalogue identifiers remain continuous and unique across Parts 1–32.

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

Part 32 catalogues the settled normative content of Record Model Section 35 and excludes 1 explicitly non-normative entry.

The next catalogue part should address Section 36.

---

<!-- Part 33 -->

# EA-05-03 — Record Requirements Catalogue

## Part 33 — Reactions

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 36, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 36 and REM-03 entries `REM-03-361` through `REM-03-367`.

Source Section 37 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-363`, `REM-03-364` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-208

### Title

Reaction represented as a record

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A reaction **SHOULD** normally be represented as an independently addressable Relay Record.

### Rationale

The source establishes record representation as the normal model while leaving room for exceptional schema-specific approaches.

### Source

- REM-03-361
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

None identified.

---

## REL-REC-209

### Title

Reaction ownership by reacting identity

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

A reaction record **SHOULD** normally be controlled by the Relay Repository and authority of the identity that performed the reaction.

### Rationale

The identity controlling the target content does not thereby own reactions made by other identities.

### Source

- REM-03-362
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-02

---

## REL-REC-210

### Title

Reaction aggregation permitted

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** aggregate individual reaction records into counts or equivalent derived summaries.

### Rationale

Aggregation does not replace the underlying canonical reaction records.

### Source

- REM-03-365
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

None identified.

---

## REL-REC-211

### Title

Reaction count is derived

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An aggregate reaction count **MUST** be treated as a derived value rather than as the underlying canonical reaction objects.

### Rationale

A count may change as reaction records are created, deleted, restricted or become unavailable.

### Source

- REM-03-366
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-07

---

## REL-REC-212

### Title

Individual reactions remain canonical

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Individual accepted reaction records **MUST** remain the underlying canonical objects from which aggregate reaction values are derived.

### Rationale

Applications must not substitute an untraceable count for the canonical reaction records where record-level verification or ownership matters.

### Source

- REM-03-367
- `design-notes/03-record-model.md`, Section 36

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-361` | Direct | `REL-REC-208` |
| `REM-03-362` | Direct | `REL-REC-209` |
| `REM-03-363` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-364` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-365` | Direct | `REL-REC-210` |
| `REM-03-366` | Direct | `REL-REC-211` |
| `REM-03-367` | Direct | `REL-REC-212` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 36 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-361` through `REM-03-367`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-207`.
- First identifier in this part: `REL-REC-208`.
- Final identifier in this part: `REL-REC-212`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–33.

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

Part 33 catalogues the settled normative content of Record Model Section 36 and excludes 2 explicitly non-normative entries.

The next catalogue part should address Section 37.

---

<!-- Part 34 -->

# EA-05-03 — Record Requirements Catalogue

## Part 34 — Reposts and references

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 37, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 37 and REM-03 entries `REM-03-368` through `REM-03-372`.

Source Section 38 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-370` is explicitly non-normative and does not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-213

### Title

Repost must not imply copied authorship

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A repost **SHOULD NOT** require the original record to be copied into the reposter’s repository in a form that represents the reposter as the original author.

### Rationale

A cached or embedded representation may still exist, but it must preserve source provenance and must not misstate authorship.

### Source

- REM-03-368
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

None identified.

---

## REL-REC-214

### Title

Repost represented through source reference

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A repost record **SHOULD** reference the original source record using its stable protocol identifier.

### Rationale

The repost is a distinct logical record whose meaning depends on its reference to the source.

### Source

- REM-03-369
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

None identified.

---

## REL-REC-215

### Title

Repost belongs to reposter

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The repost record **MUST** remain controlled by the repository and authorising identity of the reposter.

### Rationale

The reposter may control the repost without gaining control of the referenced original.

### Source

- REM-03-371
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-216

### Title

Original remains under original-author control

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Creation of a repost **MUST NOT** transfer control of the original record away from its original authoritative repository and authorising identity.

### Rationale

The original author may update or delete the source according to its own schema and repository rules, independently of the repost.

### Source

- REM-03-372
- `design-notes/03-record-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-368` | Direct | `REL-REC-213` |
| `REM-03-369` | Direct | `REL-REC-214` |
| `REM-03-370` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-371` | Direct | `REL-REC-215` |
| `REM-03-372` | Direct | `REL-REC-216` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 37 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-368` through `REM-03-372`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-212`.
- First identifier in this part: `REL-REC-213`.
- Final identifier in this part: `REL-REC-216`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–34.

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

Part 34 catalogues the settled normative content of Record Model Section 37 and excludes 1 explicitly non-normative entry.

The next catalogue part should address Section 38.

---

<!-- Part 35 -->

# EA-05-03 — Record Requirements Catalogue

## Part 35 — Moderation labels

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 38, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 38 and REM-03 entries `REM-03-373` through `REM-03-381`.

Source Section 39 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-374`, `REM-03-375`, `REM-03-376`, `REM-03-377` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-217

### Title

Moderation decision represented separately

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A moderation decision **SHOULD** be represented as a separate record rather than as an in-place rewrite of the target record.

### Rationale

Separate representation preserves the distinction between original content and a third-party judgement about that content.

### Source

- REM-03-373
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-218

### Title

Label does not alter original record

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Issuing or applying a moderation label **MUST NOT** alter the canonical content or history of the original target record.

### Rationale

An application may change how it displays or serves the target based on the label without rewriting the target itself.

### Source

- REM-03-378
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

- CI-07
- CI-10

---

## REL-REC-219

### Title

Application choice of trusted label providers

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** choose which moderation-label issuers and moderation policies they trust or enforce.

### Rationale

Different applications may therefore produce different moderation outcomes from the same underlying records and labels.

### Source

- REM-03-379
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-220

### Title

No universal moderation policy in Relay v0.1

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay v0.1 **MUST NOT** be interpreted as defining one universal moderation policy that all applications must apply.

### Rationale

The protocol supplies interoperable moderation records, not a universal content-policy authority.

### Source

- REM-03-380
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

## REL-REC-221

### Title

Support for independently issued labels

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Record Model **MUST** support moderation labels issued independently of the repository or identity controlling the target record.

### Rationale

Independent issuance requires clear issuer, subject and provenance information.

### Source

- REM-03-381
- `design-notes/03-record-model.md`, Section 38

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-373` | Direct | `REL-REC-217` |
| `REM-03-374` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-375` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-376` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-377` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-378` | Direct | `REL-REC-218` |
| `REM-03-379` | Direct | `REL-REC-219` |
| `REM-03-380` | Direct | `REL-REC-220` |
| `REM-03-381` | Direct | `REL-REC-221` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 38 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-373` through `REM-03-381`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-216`.
- First identifier in this part: `REL-REC-217`.
- Final identifier in this part: `REL-REC-221`.
- Total catalogue requirements in this part: 5.
- Catalogue identifiers remain continuous and unique across Parts 1–35.

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

Part 35 catalogues the settled normative content of Record Model Section 38 and excludes 4 explicitly non-normative entries.

The next catalogue part should address Section 39.

---

<!-- Part 36 -->

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

---

<!-- Part 37 -->

# EA-05-03 — Record Requirements Catalogue

## Part 37 — Batch operations

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 40, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 40 and REM-03 entries `REM-03-390` through `REM-03-393`.

Source Section 41 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-230

### Title

Multiple record changes in one commit

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** submit multiple record changes together as one repository commit.

### Rationale

The changes may include heterogeneous operations affecting different records and collections.

### Source

- REM-03-390
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

## REL-REC-231

### Title

Atomic batch success or failure

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A batch commit **MUST** be atomic: all included record changes MUST be accepted together, or none of them MUST be accepted.

### Rationale

Partial acceptance would leave repository state inconsistent with the submitted commit boundary.

### Source

- REM-03-391
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

- AI-03

---

## REL-REC-232

### Title

Independent addressability after batch acceptance

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Each record affected or created by an accepted batch commit **MUST** remain independently addressable after acceptance.

### Rationale

Batching changes for atomic acceptance must not collapse the participating records into one inseparable logical object.

### Source

- REM-03-392
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

## REL-REC-233

### Title

Batch commit does not replace record identity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The identity of the batch commit **MUST** remain distinct from the stable logical identity of each record included in that commit.

### Rationale

The commit identifies the accepted state transition, while each Record URI continues to identify its own logical record.

### Source

- REM-03-393
- `design-notes/03-record-model.md`, Section 40

### Related Invariants

None identified.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-390` | Direct | `REL-REC-230` |
| `REM-03-391` | Direct | `REL-REC-231` |
| `REM-03-392` | Direct | `REL-REC-232` |
| `REM-03-393` | Direct | `REL-REC-233` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 40 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-390` through `REM-03-393`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-229`.
- First identifier in this part: `REL-REC-230`.
- Final identifier in this part: `REL-REC-233`.
- Total catalogue requirements in this part: 4.
- Catalogue identifiers remain continuous and unique across Parts 1–37.

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

Part 37 catalogues the settled normative content of Record Model Section 40.

The next catalogue part should address Section 41.

---

<!-- Part 38 -->

# EA-05-03 — Record Requirements Catalogue

## Part 38 — Record portability

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 41, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 41 and REM-03 entries `REM-03-394` through `REM-03-402`.

Source Section 42 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-234

### Title

Preservation of Record URI during portability

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve the Record URI of a portable record.

### Rationale

Migration must not assign a new logical identity merely because the serving provider changes.

### Source

- REM-03-394
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-05
- CI-03

---

## REL-REC-235

### Title

Preservation of collection and schema

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve the record’s collection association and schema identifier during migration.

### Rationale

Preserving content without its collection and schema context would remove operational meaning required for validation and interoperability.

### Source

- REM-03-395
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-04

---

## REL-REC-236

### Title

Envelope validation after migration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A portable record **MUST** remain capable of passing applicable Record Envelope validation at the receiving compliant provider.

### Rationale

Migration must preserve the protocol-level metadata and context necessary for validation.

### Source

- REM-03-396
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03

---

## REL-REC-237

### Title

Preservation of record content

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve the record’s schema-defined content during migration.

### Rationale

Any deliberate transformation belongs to a separately authorised translation or migration process and must not be confused with faithful preservation.

### Source

- REM-03-397
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-04

---

## REL-REC-238

### Title

Preservation of blob references

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve the record’s blob references during migration.

### Rationale

The storage location may change, but the stable blob identity and relationship to the record must remain intact.

### Source

- REM-03-398
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-04

---

## REL-REC-239

### Title

Preservation of version history

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve the record’s version history during migration.

### Rationale

Portability is not satisfied by retaining only the latest visible payload where the protocol history is required to verify record state.

### Source

- REM-03-399
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-04
- CI-10

---

## REL-REC-240

### Title

Preservation of unknown extensions

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** preserve valid extensions that it does not understand.

### Rationale

Lack of local interpretation is not permission to strip unknown but valid extension data.

### Source

- REM-03-400
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03

---

## REL-REC-241

### Title

Continued visibility-rule enforcement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant receiving provider **MUST** continue serving a migrated record in accordance with its applicable visibility rules.

### Rationale

Migration must not silently make restricted or private content public, or make public content unavailable without a separately valid reason.

### Source

- REM-03-401
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-07

---

## REL-REC-242

### Title

Operational meaning required for portability

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A migration **MUST NOT** be considered Relay-portable if it merely converts records into flat files while losing the protocol metadata, relationships, validation context or operational meaning required by the Record Model.

### Rationale

Exportability alone is not sufficient. The receiving environment must be able to continue treating the information as operational Relay records.

### Source

- REM-03-402
- `design-notes/03-record-model.md`, Section 41

### Related Invariants

- CI-03
- AI-04

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-394` | Direct | `REL-REC-234` |
| `REM-03-395` | Direct | `REL-REC-235` |
| `REM-03-396` | Direct | `REL-REC-236` |
| `REM-03-397` | Direct | `REL-REC-237` |
| `REM-03-398` | Direct | `REL-REC-238` |
| `REM-03-399` | Direct | `REL-REC-239` |
| `REM-03-400` | Direct | `REL-REC-240` |
| `REM-03-401` | Direct | `REL-REC-241` |
| `REM-03-402` | Direct | `REL-REC-242` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 41 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-394` through `REM-03-402`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-233`.
- First identifier in this part: `REL-REC-234`.
- Final identifier in this part: `REL-REC-242`.
- Total catalogue requirements in this part: 9.
- Catalogue identifiers remain continuous and unique across Parts 1–38.

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

Part 38 catalogues the settled normative content of Record Model Section 41.

The next catalogue part should address Section 42.

---

<!-- Part 39 -->

# EA-05-03 — Record Requirements Catalogue

## Part 39 — Record interoperability

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 42, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 42 and REM-03 entries `REM-03-403` through `REM-03-407`.

Source Section 43 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-404`, `REM-03-405`, `REM-03-406` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

---

## REL-REC-243

### Title

Universal type support not required

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A compliant Relay application **MUST NOT** be required to fully interpret or render every valid Relay record type.

### Rationale

Interoperability is achieved through safe handling and preservation, not mandatory universal feature support.

### Source

- REM-03-403
- `design-notes/03-record-model.md`, Section 42

### Related Invariants

None identified.

---

## REL-REC-244

### Title

Minimum handling of unsupported records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A compliant application **MUST NOT** damage, misrepresent or discard a valid record solely because the application does not support its record type.

### Rationale

The application may decline to display or operate on the record, but must preserve it accurately where it assumes custody or participates in migration.

### Source

- REM-03-407
- `design-notes/03-record-model.md`, Section 42

### Related Invariants

- AI-10

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-403` | Direct | `REL-REC-243` |
| `REM-03-404` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-405` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-406` | Excluded from normative catalogue generation | Explicit non-normative example or specification-status entry |
| `REM-03-407` | Direct | `REL-REC-244` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 42 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-403` through `REM-03-407`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-242`.
- First identifier in this part: `REL-REC-243`.
- Final identifier in this part: `REL-REC-244`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers remain continuous and unique across Parts 1–39.

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

Part 39 catalogues the settled normative content of Record Model Section 42 and excludes 3 explicitly non-normative entries.

The next catalogue part should address Section 43.

---

<!-- Part 40 -->

# EA-05-03 — Record Requirements Catalogue

## Part 40 — Required v0.1 record operations

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 43, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 43 and REM-03 entries `REM-03-408` through `REM-03-425`.

Source Section 44 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-245

### Title

Create-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support creation of a record through an authorised repository operation.

### Rationale

Creation remains subject to schema, authority, validation and accepted-commit requirements.

### Source

- REM-03-408
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-246

### Title

Read-current-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support reading the current accepted version of a logical record.

### Rationale

Access remains subject to the record’s visibility and audience rules.

### Source

- REM-03-409
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-247

### Title

Read-specific-version operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support reading a specific historical Record Version where that version remains retrievable and access is authorised.

### Rationale

This operation is distinct from resolving the current version through the base Record URI.

### Source

- REM-03-410
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06
- CI-10

---

## REL-REC-248

### Title

List-records-by-collection operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support listing records by collection.

### Rationale

The results must respect visibility, audience and other access controls.

### Source

- REM-03-411
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-249

### Title

Validate-record-envelope operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support validation of a Record Envelope against protocol-level structural requirements.

### Rationale

Envelope validation is separate from schema-content and semantic validation.

### Source

- REM-03-412
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-250

### Title

Validate-record-schema operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support validation of record content against its declared schema where that schema is supported.

### Rationale

Unknown valid schemas must still be preserved even where local schema validation is unavailable.

### Source

- REM-03-413
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-251

### Title

Update-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support authorised updates to records whose schemas permit updating.

### Rationale

An accepted update creates a new Record Version and must satisfy concurrency and authority rules.

### Source

- REM-03-414
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-252

### Title

Delete-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support authorised record deletion.

### Rationale

Deletion must preserve the distinctions among deletion modes and apply applicable tombstone requirements.

### Source

- REM-03-415
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-253

### Title

Restore-record operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support restoration of a deleted record where the schema and retained state permit restoration and the controller authorises it.

### Rationale

Restoration is conditional and creates a new current version without erasing the historical deletion event.

### Source

- REM-03-416
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-254

### Title

Read-tombstone operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support reading an accessible tombstone for a deleted or retired logical record.

### Rationale

The tombstone must expose only the minimum information allowed by protocol and policy.

### Source

- REM-03-417
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-10

---

## REL-REC-255

### Title

Verify-record-integrity operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support verification of record integrity against the applicable integrity reference and accepted repository history.

### Rationale

The exact proof mechanism may depend on commits, hashes, signatures or other protocol-defined structures.

### Source

- REM-03-418
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-10
- CI-08

---

## REL-REC-256

### Title

Resolve-record-references operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support resolution of references to other Relay Records or specific Record Versions where accessible.

### Rationale

Unavailable targets must be handled accurately rather than causing the referring record to be misrepresented.

### Source

- REM-03-419
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-257

### Title

Upload-and-attach-blob operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support uploading a blob and attaching its stable reference to a record where permitted by the schema.

### Rationale

Temporary storage URLs must not become the blob’s permanent identity.

### Source

- REM-03-420
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-258

### Title

Change-visibility operation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support authorised changes to a record’s visibility classification where permitted.

### Rationale

A visibility change may create a new version even where the primary content does not change.

### Source

- REM-03-421
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06
- AI-07

---

## REL-REC-259

### Title

Change-audience operation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support authorised changes to a restricted record’s audience rules where permitted.

### Rationale

Audience removal revokes future authorised access but cannot guarantee deletion of copies already received.

### Source

- REM-03-422
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-260

### Title

Inspect-provenance operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support inspection of the structured provenance associated with a record.

### Rationale

Inspection must preserve the distinction between declared provenance and verified provenance.

### Source

- REM-03-423
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-10

---

## REL-REC-261

### Title

Preserve-unknown-record-types operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** preserve valid record types that it does not understand.

### Rationale

Unknown records may be preserved without being rendered or fully validated against their schema locally.

### Source

- REM-03-424
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

None identified.

---

## REL-REC-262

### Title

Detect-update-conflict operation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** detect when competing updates attempt to replace the same current version.

### Rationale

Detected conflicts must not be silently collapsed into one linear continuation.

### Source

- REM-03-425
- `design-notes/03-record-model.md`, Section 43

### Related Invariants

- CI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-408` | Direct | `REL-REC-245` |
| `REM-03-409` | Direct | `REL-REC-246` |
| `REM-03-410` | Direct | `REL-REC-247` |
| `REM-03-411` | Direct | `REL-REC-248` |
| `REM-03-412` | Direct | `REL-REC-249` |
| `REM-03-413` | Direct | `REL-REC-250` |
| `REM-03-414` | Direct | `REL-REC-251` |
| `REM-03-415` | Direct | `REL-REC-252` |
| `REM-03-416` | Direct | `REL-REC-253` |
| `REM-03-417` | Direct | `REL-REC-254` |
| `REM-03-418` | Direct | `REL-REC-255` |
| `REM-03-419` | Direct | `REL-REC-256` |
| `REM-03-420` | Direct | `REL-REC-257` |
| `REM-03-421` | Direct | `REL-REC-258` |
| `REM-03-422` | Direct | `REL-REC-259` |
| `REM-03-423` | Direct | `REL-REC-260` |
| `REM-03-424` | Direct | `REL-REC-261` |
| `REM-03-425` | Direct | `REL-REC-262` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 43 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-408` through `REM-03-425`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-244`.
- First identifier in this part: `REL-REC-245`.
- Final identifier in this part: `REL-REC-262`.
- Total catalogue requirements in this part: 18.
- Catalogue identifiers remain continuous and unique across Parts 1–40.

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

Part 40 catalogues the settled normative content of Record Model Section 43.

The next catalogue part should address Section 44.

---

<!-- Part 41 -->

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

- CI-05

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

- CI-05

---

## REL-REC-265

### Title

URI stability under editing invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Editing a record **MUST NOT** change the Record URI of the logical record.

### Rationale

The edit creates a new version rather than a new logical identity.

### Source

- REM-03-427
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-05

---

## REL-REC-266

### Title

Accepted-commit membership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every current Record Version **MUST** belong to an accepted repository commit.

### Rationale

A locally generated or pending version cannot be represented as canonical current state.

### Source

- REM-03-428
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-07
- AI-02

---

## REL-REC-267

### Title

Submitter-authority distinction invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Record Model **MUST NOT** assume that the submitting application or agent is the authorising identity.

### Rationale

The two roles may coincide but must remain independently representable.

### Source

- REM-03-429
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-02
- CI-06
- CI-11

---

## REL-REC-268

### Title

Schema-use ownership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Use of a schema **MUST NOT** confer ownership or repository control of the record on the schema publisher.

### Rationale

Schema authority governs the schema definition, not individual conforming records.

### Source

- REM-03-430
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-12
- CI-11

---

## REL-REC-269

### Title

Visibility-rights distinction invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A record’s visibility classification **MUST NOT** be treated as determining its legal ownership or usage rights.

### Rationale

A public record may remain subject to licensing, attribution, commercial-use or model-training restrictions.

### Source

- REM-03-431
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- AI-07

---

## REL-REC-270

### Title

Deletion-history integrity invariant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Record deletion **MUST** preserve sufficient repository history to avoid falsely representing that the logical record never existed.

### Rationale

The retained history may be reduced to minimum verification metadata or a tombstone according to policy.

### Source

- REM-03-432
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-10

---

## REL-REC-271

### Title

Unknown-field migration invariant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Unknown but valid fields and extensions **MUST** survive migration without being stripped or altered solely because the receiving implementation does not understand them.

### Rationale

This rule applies to valid unknown data, not malformed or prohibited fields.

### Source

- REM-03-433
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-03
- AI-04
- CI-09

---

## REL-REC-272

### Title

Projection canonicality invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application projection **MUST NOT** be treated as a canonical Relay Record unless the controller deliberately causes it to be accepted into the repository.

### Rationale

Derived views, scores and presentation objects remain application state until deliberately saved.

### Source

- REM-03-434
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-02
- CI-07
- CI-04
- AI-02

---

## REL-REC-273

### Title

Cached-copy identity and provenance invariant

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A cached copy of a Relay Record **MUST** retain the canonical Record URI and source provenance.

### Rationale

A cache must not relabel itself as the canonical source or detach the copy from its source identity.

### Source

- REM-03-435
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-05
- CI-07
- CI-10

---

## REL-REC-274

### Title

Index non-ownership invariant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Indexing a public record **MUST NOT** make the index the canonical owner or authoritative repository of that record.

### Rationale

An index is a discovery or projection layer and remains subordinate to the canonical repository source.

### Source

- REM-03-436
- `design-notes/03-record-model.md`, Section 44

### Related Invariants

- CI-07
- CI-11

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

- CI-02
- CI-06
- CI-11

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

- CI-02
- CI-11

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

---

<!-- Part 42 -->

# EA-05-03 — Record Requirements Catalogue

## Part 42 — Compliance scenario

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 45, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 45 and REM-03 entries `REM-03-438` through `REM-03-455`.

Source Section 46 and later sections are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REC-277

### Title

Basic compliance-scenario expectation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A basic Relay Record implementation **SHOULD** pass the complete compliance scenario defined in Section 45.

### Rationale

The source uses “should”, so the scenario is an expected baseline test rather than language redefining every conformance tier.

### Source

- REM-03-438
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- AI-10

---

## REL-REC-278

### Title

Initial public-record creation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** allow an authorised application to create a public record that becomes version 1 when accepted by the repository.

### Rationale

The example Record URI is illustrative rather than mandatory syntax beyond the source model’s provisional URI design.

### Source

- REM-03-439
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-279

### Title

Cross-application record reading and updating

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** allow another authorised application to read and update the same logical record.

### Rationale

The second application does not acquire ownership by performing the update.

### Source

- REM-03-440
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-280

### Title

Acceptance of the second version

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A valid cross-application update **SHOULD** be accepted as a new Record Version rather than replacing version 1 without history.

### Rationale

The new version remains part of the same logical record.

### Source

- REM-03-441
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-10

---

## REL-REC-281

### Title

URI continuity across applications and versions

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The Record URI **SHOULD** remain unchanged when another application creates a new accepted version of the record.

### Rationale

This scenario tests the general URI-stability invariant.

### Source

- REM-03-442
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05

---

## REL-REC-282

### Title

Stale-update detection

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** detect an update based on a stale expected version when a newer current version already exists.

### Rationale

The example tests optimistic concurrency behaviour.

### Source

- REM-03-443
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-07

---

## REL-REC-283

### Title

Stale-update rejection or conflict marking

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The repository **SHOULD** reject a stale update or explicitly mark and preserve it as a conflict requiring resolution.

### Rationale

The source allows either rejection or explicit conflict treatment.

### Source

- REM-03-444
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-284

### Title

No silent overwrite of current version

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

The repository **SHOULD NOT** silently overwrite the current version with an update based on stale state.

### Rationale

This retains the Section 45 scenario’s governing SHOULD framing. Independently sourced mandatory concurrency requirements remain elsewhere in the extraction.

### Source

- REM-03-445
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-07

---

## REL-REC-285

### Title

Reply stored in replying identity’s repository

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The implementation **SHOULD** support creation of a reply in the replying identity’s repository while referencing the original record in another repository.

### Rationale

The reply is a separate canonical record rather than content inserted into the original author’s record.

### Source

- REM-03-446
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-286

### Title

Cross-application display of reply

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An application displaying the original record **SHOULD** be able to resolve and display an accessible reply stored in another identity’s repository.

### Rationale

Display does not transfer canonical control of the reply.

### Source

- REM-03-447
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

None identified.

---

## REL-REC-287

### Title

Reply-controller continuity

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

The replying identity **SHOULD** remain the controller of the reply record even when another identity’s application displays it.

### Rationale

This tests the acting-identity ownership invariant.

### Source

- REM-03-448
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02

---

## REL-REC-288

### Title

Visibility change creates a version

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An authorised change from public to restricted visibility **SHOULD** create a new accepted Record Version recording that change.

### Rationale

The primary content may remain unchanged while the metadata change creates a new version.

### Source

- REM-03-449
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06
- AI-07

---

## REL-REC-289

### Title

Refusal of future unauthorised access

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

### Statement

After a valid visibility restriction, the repository **SHOULD** refuse future access attempts that do not satisfy the applicable authority or audience rule.

### Rationale

The requirement concerns future authorised service and cannot revoke copies already obtained.

### Source

- REM-03-450
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- AI-07

---

## REL-REC-290

### Title

Policy-governed removal of active content

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

When the controller deletes the record, the implementation **SHOULD** remove or withhold its active content in accordance with the applicable deletion policy.

### Rationale

The exact retained verification metadata depends on the deletion mode and tombstone requirements.

### Source

- REM-03-451
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02

---

## REL-REC-291

### Title

Tombstone prevention of Record URI reuse

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Deletion **SHOULD** leave sufficient tombstone state to prevent reuse or reassignment of the deleted Record URI.

### Rationale

This applies even when the active content has been erased.

### Source

- REM-03-452
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05
- CI-10

---

## REL-REC-292

### Title

Tombstone preservation of minimum verification history

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The tombstone **SHOULD** preserve the minimum verification history required to demonstrate the prior existence and authorised deletion of the logical record.

### Rationale

The tombstone should not retain more deleted content than necessary.

### Source

- REM-03-453
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-02
- CI-06
- CI-10
- CI-08

---

## REL-REC-293

### Title

Migration continuity for URI, versions and tombstone

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Repository migration **SHOULD** preserve the record’s Record URI, accepted versions and tombstone intact at the receiving provider.

### Rationale

This scenario tests portability after both versioning and deletion history have occurred.

### Source

- REM-03-454
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-05
- CI-03
- AI-04
- CI-10

---

## REL-REC-294

### Title

Basic Relay Record objective

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An implementation **SHOULD** be considered to satisfy the basic Relay Record objective when it completes the Section 45 operations without conflating application ownership, logical record identity, historical versions or visibility state.

### Rationale

The scenario evaluates both functional operations and preservation of the Record Model’s core conceptual boundaries.

### Source

- REM-03-455
- `design-notes/03-record-model.md`, Section 45

### Related Invariants

- CI-10
- AI-07

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-438` | Direct | `REL-REC-277` |
| `REM-03-439` | Direct | `REL-REC-278` |
| `REM-03-440` | Direct | `REL-REC-279` |
| `REM-03-441` | Direct | `REL-REC-280` |
| `REM-03-442` | Direct | `REL-REC-281` |
| `REM-03-443` | Direct | `REL-REC-282` |
| `REM-03-444` | Direct | `REL-REC-283` |
| `REM-03-445` | Direct | `REL-REC-284` |
| `REM-03-446` | Direct | `REL-REC-285` |
| `REM-03-447` | Direct | `REL-REC-286` |
| `REM-03-448` | Direct | `REL-REC-287` |
| `REM-03-449` | Direct | `REL-REC-288` |
| `REM-03-450` | Direct | `REL-REC-289` |
| `REM-03-451` | Direct | `REL-REC-290` |
| `REM-03-452` | Direct | `REL-REC-291` |
| `REM-03-453` | Direct | `REL-REC-292` |
| `REM-03-454` | Direct | `REL-REC-293` |
| `REM-03-455` | Direct | `REL-REC-294` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 45 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-438` through `REM-03-455`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-276`.
- First identifier in this part: `REL-REC-277`.
- Final identifier in this part: `REL-REC-294`.
- Total catalogue requirements in this part: 18.
- Catalogue identifiers remain continuous and unique across Parts 1–42.

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

Part 42 catalogues the settled normative content of Record Model Section 45.

The next catalogue part should address Section 46.

---

<!-- Part 43 -->

# EA-05-03 — Record Requirements Catalogue

## Part 43 — Open design questions

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 46, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 46 and REM-03 entries `REM-03-456` through `REM-03-465`.

Source Section 47 and later sections are intentionally deferred to subsequent catalogue parts.

`REM-03-456`, `REM-03-457`, `REM-03-458`, `REM-03-459`, `REM-03-460`, `REM-03-461`, `REM-03-462`, `REM-03-463`, `REM-03-464`, `REM-03-465` are explicitly non-normative and do not generate catalogue requirements.

---

# 3. Requirements

No normative catalogue requirements are generated from this section.

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-456` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-457` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-458` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-459` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-460` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-461` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-462` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-463` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-464` | Excluded from normative catalogue generation | Explicit non-normative open design issue |
| `REM-03-465` | Excluded from normative catalogue generation | Explicit non-normative open design issue |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 46 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-456` through `REM-03-465`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-294`.
- This section generates no REL-REC identifier because every in-scope entry is non-normative.
- Catalogue endpoint remains `REL-REC-294`.
- Catalogue identifiers remain continuous and unique across Parts 1–43.

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

Part 43 catalogues the settled normative content of Record Model Section 46 and excludes 10 explicitly non-normative entries.

The next catalogue part should address Section 47.

---

<!-- Part 44 -->

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

Relay v0.1 **SHOULD** provisionally represent records using a JSON-compatible structured data model.

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

Relay v0.1 **MUST** provisionally use stable Record URIs for the persistent identity of logical records.

### Rationale

This assumption is consistent with the record invariants and the core record principle.

### Source

- REM-03-467
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-05

---

## REL-REC-297

### Title

Versioned schemas

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally support explicit schema versioning.

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

Relay v0.1 **MUST** provisionally maintain exactly one authoritative current version for each active logical record.

### Rationale

Conflicting proposed versions may be preserved as candidates, but they must not both be silently treated as one linear current continuation.

### Source

- REM-03-469
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-07
- AI-01

---

## REL-REC-299

### Title

Optimistic concurrency checks

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally use optimistic concurrency checks for record updates.

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

Relay v0.1 **MUST** provisionally treat a valid signed repository commit as the minimum authority proof for an accepted record operation.

### Rationale

This does not preclude stronger or additional signatures where required by a schema or assertion type.

### Source

- REM-03-471
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-02

---

## REL-REC-301

### Title

Optional signatures for externally issued assertions

**Level:** Architectural

**Normative Keyword:** **MAY**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MAY** provisionally support individual record signatures for externally issued assertions in addition to signed repository commits.

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

Relay v0.1 **SHOULD** provisionally support public, unlisted, restricted and private record visibility classifications.

### Rationale

These classifications do not by themselves determine usage rights or legal ownership.

### Source

- REM-03-473
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- AI-07

---

## REL-REC-303

### Title

Logical deletion with tombstones

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally support logical deletion represented through tombstones or equivalent minimum persistent deletion records.

### Rationale

The retained tombstone should preserve only the information necessary for integrity, deletion history and identifier non-reuse.

### Source

- REM-03-474
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-10

---

## REL-REC-304

### Title

No reuse of deleted Record Keys

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally prohibit reuse of a deleted Record Key for a different logical record.

### Rationale

The associated tombstone preserves evidence that the identifier has already been used.

### Source

- REM-03-475
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-05

---

## REL-REC-305

### Title

Content-addressed blob references

**Level:** Constitutional

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally identify referenced blobs through content-addressed identifiers rather than treating temporary storage URLs as permanent blob identity.

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

Relay v0.1 **SHOULD** provisionally support structured record provenance.

### Rationale

Provenance declarations must continue to distinguish declared origin from independently verified authenticity.

### Source

- REM-03-477
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-10

---

## REL-REC-307

### Title

Preservation of unknown fields and schemas

**Level:** Architectural

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally preserve valid but unknown fields, extensions and record schemas during storage, migration and round-trip processing.

### Rationale

An implementation may decline to render or interpret an unknown type but must not damage or discard it solely because it is unknown.

### Source

- REM-03-478
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-03
- AI-04
- CI-09

---

## REL-REC-308

### Title

Acting-identity storage for replies, reactions and reposts

**Level:** Constitutional

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **SHOULD** provisionally store replies, reactions and reposts in the repository of the identity that authorised the respective action record.

### Rationale

The repository of the referenced content may index or display these records but does not become their canonical owner.

### Source

- REM-03-479
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-02
- CI-06

---

## REL-REC-309

### Title

Projections remain non-canonical unless explicitly saved

**Level:** Constitutional

**Normative Keyword:** **MUST**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **MUST** provisionally treat application projections as non-canonical unless the controller explicitly saves and authorises them as repository records.

### Rationale

Derived views, cards, rankings and recommendations must not automatically pollute the person’s canonical repository history.

### Source

- REM-03-480
- `design-notes/03-record-model.md`, Section 47

### Related Invariants

- CI-02
- CI-06
- CI-07
- CI-04

---

## REL-REC-310

### Title

Moderation labels as separate records

**Level:** Architectural

**Normative Keyword:** **SHOULD**

**Specification Status:** **PROVISIONAL v0.1**

### Statement

Relay v0.1 **SHOULD** provisionally represent moderation labels as records separate from the target record.

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

Relay v0.1 **MUST** provisionally apply schema-specific content and behaviour rules on top of a common protocol-level Record Envelope.

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

---

<!-- Part 45 -->

# EA-05-03 — Record Requirements Catalogue

## Part 45 — Core record principle

**Editorial Programme:** EA-05 — Normative Requirements Audit

**Subsystem:** Record

**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the settled normative Record Model rules in source Section 48, while preserving the source's qualifications and non-normative status distinctions.

This catalogue part is generated from the completed and verified REM-03 extraction series. The authoritative design source remains `design-notes/03-record-model.md`.

---

# 2. Scope

This part covers source Section 48 and REM-03 entries `REM-03-483` through `REM-03-483`.

This is the final Record Model source section.

---

# 3. Requirements

---

## REL-REC-312

### Title

Stable Portable Record Principle

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Relay Record **MUST** be treated as a stable and portable logical object governed by repository authority.

### Rationale

This principle summarises the Record Model and governs interpretation of the more detailed requirements throughout REM-03.

### Source

- REM-03-483
- `design-notes/03-record-model.md`, Section 48

### Related Invariants

- CI-02
- CI-03

---

## REL-REC-313

### Title

No Disposable Application-Owned Row Treatment

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Record **MUST NOT** be treated as a disposable application-owned database row whose identity or continued existence depends on the application that created it.

### Rationale

This principle summarises the Record Model and governs interpretation of the more detailed requirements throughout REM-03.

### Source

- REM-03-483
- `design-notes/03-record-model.md`, Section 48

### Related Invariants

- CI-04

---

# 4. REM coverage, consolidation and exclusions

| REM identifier | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-03-483` | Decomposed to preserve distinct normative effects | `REL-REC-312` and `REL-REC-313` |

Every in-scope REM entry is represented directly, decomposed where required to preserve distinct normative effects, or explicitly excluded because it is non-normative. No compatible normative entries are consolidated in this part.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Section 48 of `design-notes/03-record-model.md`.
- The verified extraction range is limited to `REM-03-483` through `REM-03-483`.
- No requirement from a later source section is imported.

## Identifier verification

- Previous catalogue endpoint: `REL-REC-311`.
- First identifier in this part: `REL-REC-312`.
- Final identifier in this part: `REL-REC-313`.
- Total catalogue requirements in this part: 2.
- Catalogue identifiers remain continuous and unique across Parts 1–45.

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

Part 45 catalogues the settled normative content of Record Model Section 48.

This completes catalogue generation for `design-notes/03-record-model.md`.
