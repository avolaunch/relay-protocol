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
