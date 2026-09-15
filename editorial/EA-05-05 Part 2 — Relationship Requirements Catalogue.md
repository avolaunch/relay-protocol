# EA-05-05 — Relationship Requirements Catalogue

## Part 2 — Relationship Structure, Source and Target

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the structural components of a Relay Relationship and the protocol semantics governing relationship Source and Target.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-027`, following Part 1's coverage of relationship foundations, portability and canonical representation. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 4–6 and REM-05 requirements `REM-05-031` through `REM-05-064`.

It defines normative requirements governing:

- relationship component representation;
- schema-dependent component requirements;
- Source identification and semantics;
- correspondence between Source and repository authority;
- delegated application submission;
- separation of submitter and Source roles;
- Target identification and supported Target categories;
- stable Target references;
- avoidance of provider-local URLs and mutable Handles as sole permanent Target references.

Section 7 and later Relationship Type and direction semantics are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-027

### Title

Relationship Source Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Source component identifying the identity or record making the relationship declaration.

### Rationale

Every relationship claim requires an identifiable declarant. Combining the structural Source capability with its semantic definition ensures that Source is not treated as an uninterpreted field.

### Source

- REM-05-031
- REM-05-045
- `design-notes/05-relationship-model.md`, Sections 4 and 5

### Related Invariants

- CI-08

---

## REL-REL-028

### Title

Relationship Target Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Target component identifying the identity, record or recognised external entity to which the relationship declaration points.

### Rationale

A portable relationship requires a protocol-understandable object of the declaration rather than an application-local display value.

### Source

- REM-05-032
- REM-05-054
- `design-notes/05-relationship-model.md`, Sections 4 and 6

### Related Invariants

- CI-05
- CI-08

---

## REL-REL-029

### Title

Relationship Type Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of the Relationship Type defining the semantic meaning of a connection.

### Rationale

Relationship Type allows compatible implementations to distinguish the meaning of different connections. Detailed Relationship Type schema requirements are defined in the next catalogue part.

### Source

- REM-05-033
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-12

---

## REL-REL-030

### Title

Relationship Direction Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of relationship Direction where relevant to the governing schema.

### Rationale

Direction permits schemas to distinguish directed, reciprocal and other direction-sensitive relationship semantics without requiring every relationship to use the component identically.

### Source

- REM-05-034
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-08

---

## REL-REL-031

### Title

Relationship Status Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of relationship Status where required by the governing schema.

### Rationale

Schema-defined lifecycle state must be representable for relationship types that distinguish pending, active, revoked, expired or other statuses.

### Source

- REM-05-035
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-09

---

## REL-REL-032

### Title

Relationship Visibility Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of relationship Visibility.

### Rationale

Relationship visibility is protocol state and must be distinguishable from application presentation or ownership.

### Source

- REM-05-036
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-07

---

## REL-REL-033

### Title

Relationship Audience Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of an Audience where relationship access requires audience-specific restriction.

### Rationale

Audience restrictions allow relationship access to be narrower than a broad visibility classification when the applicable schema or policy requires it.

### Source

- REM-05-037
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-07

---

## REL-REL-034

### Title

Relationship Context Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of Context where context is necessary to interpret a relationship accurately.

### Rationale

The same participants and Relationship Type may have materially different meanings in different projects, organisations or other contexts.

### Source

- REM-05-038
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-08

---

## REL-REL-035

### Title

Relationship Provenance Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of relationship Provenance.

### Rationale

Relationship claims must be attributable to their authorising and submission context so that authority and origin can be independently evaluated.

### Source

- REM-05-039
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-08
- CI-10

---

## REL-REL-036

### Title

Relationship Validity Period Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of a Validity Period where a relationship is time-bound.

### Rationale

Some relationship types are temporary or expire and therefore require protocol-level temporal validity without imposing a validity period on every relationship.

### Source

- REM-05-040
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-09

---

## REL-REL-037

### Title

Relationship Reciprocal Reference Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of a Reciprocal Reference where a relationship depends upon or is associated with another participant's independently authorised declaration.

### Rationale

Reciprocal references allow independently controlled relationship records to be associated without collapsing their separate authority or ownership.

### Source

- REM-05-041
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- AI-08

---

## REL-REL-038

### Title

Relationship Authority Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of the Authority under which a relationship declaration or relationship-conveyed power exists.

### Rationale

Authority-bearing relationships require explicit protocol state distinguishing social meaning from delegated or otherwise consequential authority.

### Source

- REM-05-042
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-06

---

## REL-REL-039

### Title

Relationship Conditions Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support representation of Conditions that limit or qualify a relationship where required by the governing schema.

### Rationale

Relationship semantics may be constrained by duration, context, evidence, permitted actions or other schema-defined conditions and must be able to express those constraints explicitly.

### Source

- REM-05-043
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-06

---

## REL-REL-040

### Title

Schema-Dependent Relationship Components

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement

An implementation **MUST NOT** require every Relationship Model component for every Relationship Type unless the governing schema requires that component.

### Rationale

The component model defines representational capability rather than a universal mandatory field set. Individual schemas determine which components are required, optional or inapplicable.

### Source

- REM-05-044
- `design-notes/05-relationship-model.md`, Section 4

### Related Invariants

- CI-12

---

## REL-REL-041

### Title

Relay Identity as Relationship Source

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Relay Identity as the Source of a relationship declaration.

### Rationale

Identity-authored declarations are the normal basis for social, organisational and authority-bearing relationship records.

### Source

- REM-05-046
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-02

---

## REL-REL-042

### Title

Relay Record as Relationship Source

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Relay Record as the Source of a relationship declaration where the governing schema permits record-originated semantics.

### Rationale

The source model permits relationships to originate semantically from records while preserving the independently verifiable identity and repository authority behind those records.

### Source

- REM-05-047
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-08

---

## REL-REL-043

### Title

Relationship Source Semantic Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The Source **MUST** correspond to the declarant of the relationship statement defined by the governing schema.

### Rationale

Reversing Source and Target changes the meaning of a relationship claim and would therefore create a semantically different relationship.

### Source

- REM-05-048
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-08

---

## REL-REL-044

### Title

Source and Repository Controller Correspondence

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The Source **SHOULD** normally correspond to the Relay Identity controlling the repository in which the relationship record is stored.

### Rationale

Normal Source-to-controller correspondence makes declaration authority directly attributable while retaining the source model's allowance for authorised exceptions.

### Source

- REM-05-049
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-02
- AI-01

---

## REL-REL-045

### Title

Validation of Source-Controller Exceptions

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where a relationship Source does not directly correspond to the repository-controlling Relay Identity, the implementation **MUST** be able to validate the authority and schema basis permitting that exception.

### Rationale

An exception to normal Source placement cannot be accepted merely because software submitted the record; it must remain grounded in valid protocol authority and semantics.

### Source

- REM-05-050
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-06
- AI-01

---

## REL-REL-046

### Title

Delegated Relationship Submission

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** submit a relationship declaration on behalf of its Source only under valid delegated authority.

### Rationale

Applications may act as authorised submitters without thereby becoming the declarant or gaining independent authority over the relationship.

### Source

- REM-05-051
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-06

---

## REL-REL-047

### Title

Relationship Submitter and Source Separation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application submitting a relationship declaration under delegated authority **MUST NOT** be treated as the relationship Source solely because it transmitted or submitted the operation.

### Rationale

Submission is an operational role. Relationship Source identifies the entity making the declaration and must remain distinct from the software acting on that entity's behalf.

### Source

- REM-05-052
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-048

### Title

Application Acting as Relationship Source

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** be the Source of a relationship only where it is intentionally represented and authorised as a Relay Identity rather than merely acting as software for another identity.

### Rationale

The exception preserves the distinction between an application as software and an entity that intentionally participates in Relay as an identity in its own right.

### Source

- REM-05-053
- `design-notes/05-relationship-model.md`, Section 5

### Related Invariants

- CI-06

---

## REL-REL-049

### Title

Relay Identity as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Relay Identity as a valid Target.

### Rationale

Identity targets underpin direct social, trust, blocking, representation and other identity-to-identity relationships.

### Source

- REM-05-055
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-01

---

## REL-REL-050

### Title

Relay Record as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Relay Record as a valid Target.

### Rationale

Record targets allow relationships such as authorship, ownership or endorsement to refer to a stable protocol record rather than only to an identity.

### Source

- REM-05-056
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-08

---

## REL-REL-051

### Title

Defined Group as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a defined group as a valid Target where that group is represented by a resolvable or schema-recognised identifier.

### Rationale

Group-target relationships require enough stable identity or schema recognition to remain interoperable beyond an application's local grouping model.

### Source

- REM-05-057
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-05

---

## REL-REL-052

### Title

Organisation as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support an organisation as a valid Target.

### Rationale

Organisational relationships such as membership, employment, collaboration and representation require organisations to be addressable as relationship targets.

### Source

- REM-05-058
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-05

---

## REL-REL-053

### Title

Credential as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a credential as a valid Target.

### Rationale

Credential-target relationships allow schemas to represent connections involving a specific credential while retaining its independent identity and verification semantics.

### Source

- REM-05-059
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-08

---

## REL-REL-054

### Title

Relay Application as Relationship Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support a Relay Application as a valid Target.

### Rationale

Applications may themselves be the objects of relationship claims such as trust, subject to stable application identification and the governing schema.

### Source

- REM-05-060
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-05

---

## REL-REL-055

### Title

External Identifier as Relationship Target

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The Relationship Model **MAY** represent a recognised external identifier as the Target where no suitable Relay Identity exists.

### Rationale

External identifiers permit staged interoperability without falsely treating an external reference as a Relay-native identity.

### Source

- REM-05-061
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-12

---

## REL-REL-056

### Title

Stable Relay Target Identifier Preference

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship Target **SHOULD** use a stable Relay identifier wherever one is available.

### Rationale

Stable identifiers improve portability, resolution and continuity across applications and Relay Providers.

### Source

- REM-05-062
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-05

---

## REL-REL-057

### Title

Provider URL Is Not a Sole Permanent Target Reference

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

A relationship record **SHOULD NOT** use a temporary provider URL as its sole permanent Target reference.

### Rationale

Provider-local routing information may change during migration and therefore cannot reliably define the enduring Target of a portable relationship.

### Source

- REM-05-063
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-03
- CI-05

---

## REL-REL-058

### Title

Visible Handle Is Not a Sole Permanent Target Reference

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

A relationship record **SHOULD NOT** use a mutable visible Handle as its sole permanent Target reference.

### Rationale

Handles may change, collide or be reassigned and therefore should not independently anchor the enduring identity of a relationship Target.

### Source

- REM-05-064
- `design-notes/05-relationship-model.md`, Section 6

### Related Invariants

- CI-05

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express the same independently testable protocol behaviour:

- `REM-05-031` and `REM-05-045` are consolidated into `REL-REL-027`, combining support for the Source component with the definition of what that component identifies.
- `REM-05-032` and `REM-05-054` are consolidated into `REL-REL-028`, combining support for the Target component with the definition of what that component identifies.

No other REM-05 entries in the covered range are consolidated. In particular, individual relationship components remain separate because support for each is independently testable; Source authority and delegation requirements remain separate because they govern distinct behaviours; and each Target category remains separate because support for one category does not demonstrate support for another.

All REM-05 requirements from `REM-05-031` through `REM-05-064` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 2 begins at `REM-05-031`, immediately after Part 1's final covered requirement `REM-05-030`.
- Coverage ends at `REM-05-064`, the end of source Section 6.
- Section 7 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 4–6.

## Numbering verification

- First catalogue requirement: `REL-REL-027`.
- Final catalogue requirement: `REL-REL-058`.
- Catalogue numbering continues directly from Part 1's `REL-REL-026`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- `SHOULD`, `SHOULD NOT` and `MAY` requirements have not been silently promoted to `MUST`.
- Illustrative examples have not been promoted into additional catalogue requirements.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes the common structural vocabulary needed by all later Relationship requirements. It preserves the distinction between declarant, submitter and repository authority; defines the Target categories the model must be capable of addressing; and anchors portable Target references in stable protocol identifiers rather than provider-local URLs or mutable Handles.

The next catalogue part should begin with `REM-05-065` / source Section 7 and continue catalogue numbering from `REL-REL-059`.