# EA-05-05 — Relationship Requirements Catalogue

## Part 1 — Relationship Foundations, Portability and Canonical Representation

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the foundational requirements of the Relay Relationship subsystem.

It establishes what a Relay Relationship is, the continuity and portability properties that distinguish it from application-local social state, and the canonical record model through which a relationship declaration exists independently of the application or provider that facilitated it.

This catalogue part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 1–3 and REM-05 requirements `REM-05-001` through `REM-05-030`.

It defines normative requirements governing:

- relationship representation;
- relationship portability and continuity;
- supported relationship domains;
- application independence and application participation;
- cross-application operation;
- provider independence;
- visibility and lifecycle control;
- authorisation traceability;
- operational portability;
- canonical relationship-record placement;
- unilateral declaration independence.

Sections 4 and later are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-001

### Title

Relationship Record Representation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every canonical Relay Relationship **MUST** be represented as a structured Relay Record.

### Rationale

A relationship must exist as protocol-governed state rather than only as unstructured or application-local social data. Representation as a Relay Record gives the relationship a portable, independently interpretable canonical form.

### Source

- REM-05-001
- REM-05-026
- `design-notes/05-relationship-model.md`, Sections 1 and 3

### Related Invariants

- CI-08
- AI-01

---

## REL-REL-002

### Title

Relationship Portability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Relationship **MUST** remain portable across compatible Relay implementations.

### Rationale

A relationship that cannot leave the implementation in which it was created cannot satisfy Relay's relationship-continuity objective.

### Source

- REM-05-002
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-03
- CI-04

---

## REL-REL-003

### Title

Identity-to-Identity Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationships connecting one Relay Identity to another Relay Identity.

### Rationale

Identity-to-identity connections are a primary relationship domain and underpin social, collaborative, organisational and authority-bearing relationship types.

### Source

- REM-05-003
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-01

---

## REL-REL-004

### Title

Record-Related Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationships involving Relay Records as a source or target where permitted by the governing relationship schema.

### Rationale

Relationships may describe connections involving protocol records as well as identities, while schema governance determines which source-target combinations are valid.

### Source

- REM-05-004
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-08

---

## REL-REL-005

### Title

External-Entity Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationships involving recognised external entities where no suitable Relay-native entity exists.

### Rationale

External-entity support permits staged interoperability and import without requiring every relationship target to possess a Relay Identity at the time the relationship is represented.

### Source

- REM-05-005
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-12

---

## REL-REL-006

### Title

Relationship Semantic Extensibility

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support multiple schema-defined categories of connection rather than restricting Relay Relationships to a single social or organisational relationship type.

### Rationale

The source model identifies social, subscription, collaboration, employment, membership, endorsement, trust, blocking, representation, authorship, ownership, management and general association semantics as illustrative relationship categories.

### Source

- REM-05-006
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-12

---

## REL-REL-007

### Title

Relationship Independence from Originating Applications

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The continued validity, resolution, access to portable state and protocol interpretation of a Relay Relationship **MUST NOT** depend solely on continued use, availability or existence of the application through which the relationship was created.

### Rationale

Relationships exist between protocol entities rather than inside the client that introduced or displayed them. Application replacement must therefore not convert relationship continuity into platform lock-in.

### Source

- REM-05-007
- REM-05-022
- `design-notes/05-relationship-model.md`, Sections 1 and 2

### Related Invariants

- CI-04

---

## REL-REL-008

### Title

Application-Assisted Relationship Establishment

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An authorised Relay Application **MAY** assist a person or Relay Identity in establishing a Relay Relationship subject to applicable repository authority, permissions and relationship-schema rules.

### Rationale

Applications are valid interfaces for relationship establishment without becoming the constitutional owners of the resulting relationship state.

### Source

- REM-05-008
- REM-05-014
- `design-notes/05-relationship-model.md`, Sections 1 and 2

### Related Invariants

- CI-04
- CI-06

---

## REL-REL-009

### Title

Application Relationship Display

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** display a Relay Relationship that it is authorised to access.

### Rationale

Presentation is an application capability and does not transfer ownership or canonical authority over the relationship.

### Source

- REM-05-009
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- AI-07

---

## REL-REL-010

### Title

Application Relationship Filtering

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** filter authorised Relay Relationships for presentation or application-specific use without altering their canonical protocol meaning or state.

### Rationale

Application-specific views may differ while the underlying portable relationship remains unchanged.

### Source

- REM-05-010
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- AI-01
- AI-07

---

## REL-REL-011

### Title

Application Relationship Interpretation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** provide an application-specific interpretation or presentation of a Relay Relationship provided that it does not falsely represent the relationship's schema-defined meaning or authority.

### Rationale

Relay permits application diversity without permitting applications to rewrite protocol semantics through presentation.

### Source

- REM-05-011
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-012

### Title

Application Participation Does Not Confer Relationship Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** acquire ownership or controlling authority over a Relay Relationship solely because it established, submitted, displayed, filtered or interpreted that relationship.

### Rationale

Application participation is operational. Canonical authority remains with the identities, records and repositories authorised by the protocol model.

### Source

- REM-05-012
- `design-notes/05-relationship-model.md`, Section 1

### Related Invariants

- CI-04
- AI-07

---

## REL-REL-013

### Title

Relationship Continuity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** preserve relationship continuity across changes in applications, Relay Providers and compatible service environments.

### Rationale

Relationship continuity is the explicit purpose of the Relationship Model and ensures that a connection remains independently resolvable and interpretable as operational surroundings change.

### Source

- REM-05-013
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-03
- CI-04

---

## REL-REL-014

### Title

Cross-Application Relationship Viewing

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** allow a relationship established through one application to be viewed through another compatible application when that application is authorised to access it.

### Rationale

Portable relationship state must remain usable when a user changes compatible applications.

### Source

- REM-05-015
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-04

---

## REL-REL-015

### Title

Cross-Application Relationship Operation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** allow a compatible application to perform authorised operations on or in relation to an existing relationship subject to the governing schema, relationship state and applicable Permission Grant.

### Rationale

Application replaceability requires more than passive export or display; authorised relationship functionality must remain available through compatible clients.

### Source

- REM-05-016
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-04
- CI-06

---

## REL-REL-016

### Title

Relationship Continuity Across Provider Change

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing Relay Provider **MUST NOT**, by itself, terminate or invalidate a portable Relay Relationship.

### Rationale

Provider replacement changes operational hosting rather than the persistent identities or portable relationship between them.

### Source

- REM-05-017
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-03

---

## REL-REL-017

### Title

Public and Private Relationship Distinction

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** distinguish public relationships from private relationships through protocol-understandable visibility or access semantics.

### Rationale

Relationship privacy cannot depend solely on an application's visual presentation of otherwise indistinguishable protocol state.

### Source

- REM-05-018
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- AI-07

---

## REL-REL-018

### Title

Relationship-Side Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Identity **MUST** be able to revoke its own relationship declaration or its own independently authorised side of a relationship, subject to the governing schema and repository rules.

### Rationale

A participant must retain control over the relationship claim that it independently authorised without gaining authority to erase another participant's independent declaration.

### Source

- REM-05-019
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-019

### Title

Relationship-Side Modification

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A Relay Identity **MUST** be able to change its own relationship declaration or relationship-side state where the governing schema permits modification.

### Rationale

Relationship state must remain controllable by its authorising identity while respecting schema-defined lifecycle and history rules.

### Source

- REM-05-020
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-02
- AI-09

---

## REL-REL-020

### Title

Relationship Authorisation Traceability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** provide sufficient information to verify which Relay Identity authorised each relationship claim.

### Rationale

Relationship meaning, consent and authority depend on independently identifying the identity responsible for each declaration rather than merely the application that transmitted it.

### Source

- REM-05-021
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-06
- CI-08
- AI-08

---

## REL-REL-021

### Title

Username Export Is Not Operational Relationship Portability

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** claim operational relationship portability solely because it can export usernames or display handles.

### Rationale

Mutable or provider-specific names do not provide the stable identity resolution and relationship semantics required for continued operation by another compatible service.

### Source

- REM-05-023
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-05
- AI-10

---

## REL-REL-022

### Title

Identity Resolution Required for Operational Portability

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A relationship **MUST NOT** be considered operationally portable unless another compatible service can resolve the identities involved.

### Rationale

A relationship cannot continue operationally when its participants cannot be resolved independently of the originating service.

### Source

- REM-05-024
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- CI-05
- AI-10

---

## REL-REL-023

### Title

Semantic Interpretation Required for Operational Portability

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A relationship **MUST NOT** be considered operationally portable unless another compatible service can continue interpreting the relationship's type and meaning.

### Rationale

Stable participant identifiers alone are insufficient if the receiving implementation cannot understand the connection represented between them.

### Source

- REM-05-025
- `design-notes/05-relationship-model.md`, Section 2

### Related Invariants

- AI-10

---

## REL-REL-024

### Title

Declarant Repository Placement

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship declaration **SHOULD** normally be stored in the repository controlled by the Relay Identity making that declaration.

### Rationale

Declarant-controlled placement aligns relationship state with the identity that authorised it while preserving the source model's allowance for authorised exceptions.

### Source

- REM-05-027
- `design-notes/05-relationship-model.md`, Section 3

### Related Invariants

- CI-02
- AI-01

---

## REL-REL-025

### Title

Declarant Repository Canonical Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The repository of the identity making a relationship declaration **MUST** serve as the canonical source of that identity's declaration unless the protocol defines an authorised equivalent repository arrangement.

### Rationale

Canonical authority over one identity's declaration must not be inferred from the target identity, an application or a derived graph service.

### Source

- REM-05-028
- `design-notes/05-relationship-model.md`, Section 3

### Related Invariants

- CI-02
- AI-01

---

## REL-REL-026

### Title

Unilateral Declaration Independence

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A unilateral relationship declaration **MUST** be capable of existing as a valid declaration without requiring duplication of that declaration as a matching record in the target identity's repository.

### Rationale

A directed declaration belongs to its declarant. Requiring target-side duplication would incorrectly turn unilateral relationship existence into reciprocal repository state.

### Source

- REM-05-029
- REM-05-030
- `design-notes/05-relationship-model.md`, Section 3

### Related Invariants

- AI-01
- AI-08

---

# 4. Consolidation Record

Part 1 performs only consolidations where the contributing REM entries express the same catalogue-level obligation or a necessary inseparable formulation of that obligation.

| Catalogue requirement | Consolidated REM-05 entries | Basis |
|---|---|---|
| REL-REL-001 | REM-05-001, REM-05-026 | The general structured-record definition and the explicit Relay Record representation describe one canonical representation requirement. |
| REL-REL-007 | REM-05-007, REM-05-022 | Both prohibit application dependence as the basis of relationship continuity; the latter states the anti-lock-in consequence of the former. |
| REL-REL-008 | REM-05-008, REM-05-014 | Both establish that an authorised application may be the interface through which a relationship is established. |
| REL-REL-026 | REM-05-029, REM-05-030 | Both establish that a unilateral declaration does not require a matching target-repository copy for validity. |

No other REM-05 entries in the covered range were merged merely because they concern the same topic. In particular, viewing and acting across applications remain separate; revocation and modification remain separate; identity resolution and semantic interpretation remain separate operational-portability conditions.

---

# 5. Traceability and Editorial QA

### Source-range verification

- Authoritative design source: `design-notes/05-relationship-model.md`, Sections 1–3.
- Verified extraction input: `REM-05-001` through `REM-05-030`.
- Section 4 begins a distinct structural-component topic and is intentionally reserved for the next catalogue part.

### Catalogue numbering verification

- First catalogue requirement: `REL-REL-001`.
- Final catalogue requirement: `REL-REL-026`.
- Catalogue identifiers are continuous and unique within Part 1.
- Part 2 must continue from `REL-REL-027`.

### Normative-strength verification

- `MUST`, `MUST NOT`, `SHOULD` and `MAY` strengths are inherited from the verified REM-05 requirements and their authoritative source.
- Consolidation does not strengthen a weaker source statement.
- The `SHOULD` qualification governing normal declarant-repository placement remains intact.
- Permitted application behaviour remains `MAY` and is not promoted into implementation obligations.

### Status verification

- The non-normative exclusions identified by `REM-05R-02` occur outside this part's covered range and therefore do not enter Part 1.
- Section 58 remains untouched and unresolved.
- Section 59 provisional decisions remain untouched and will retain explicit `PROVISIONAL v0.1` status when their range is reached.

### Traceability verification

Every catalogue requirement maps to one or more verified REM-05 identifiers and to the corresponding authoritative source section. Consolidated requirements retain all contributing REM identifiers rather than discarding duplicate source traces.

---

# Editorial Review Notes

Part 1 establishes the constitutional and architectural basis of the Relationship subsystem: relationships are structured Relay Records whose existence and meaning survive application and provider change; applications may facilitate and present relationships without owning them; identities retain control of their own declarations; and operational portability requires both stable participant resolution and continued semantic interpretation.

The bounded range of Sections 1–3 was selected because it forms a coherent foundational unit comparable in scale to established EA-05 catalogue parts while ending before Section 4 begins the detailed relationship-component model.

This part is ready for founder review and subsequent assembly into the eventual `EA-05-05 — Relationship Requirements Catalogue v1.0`.