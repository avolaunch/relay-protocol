# EA-05-05 — Relationship Requirements Catalogue

## Part 3 — Relationship Types, Direction and Independent Authorisation

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the schema semantics of Relationship Types, the supported direction models, and the authorisation boundaries governing unilateral and reciprocal relationships.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-059`, following Parts 1–2's coverage of relationship foundations, canonical representation, structural components, Source and Target semantics. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 7–10 and REM-05 requirements `REM-05-065` through `REM-05-096`.

It defines normative requirements governing:

- Relationship Type identification and schema definition;
- schema declaration of direction, reciprocity, approval, visibility, expiration, authority, evidence and revocation semantics;
- directed, reciprocal, mutually interpreted and authority-bearing relationships;
- unilateral relationship authorisation and presentation;
- reciprocal relationship independent authorisation;
- linked reciprocal records and reciprocal references;
- independent record and repository authority between participants.

Section 11 and later relationship status and lifecycle semantics are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-059

### Title

Relationship Type Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every relationship record **MUST** identify a Relationship Type that defines the semantic meaning of the connection.

### Rationale

A portable relationship cannot be interpreted consistently if its semantic type is only implicit in an originating application's behaviour or presentation.

### Source

- REM-05-065
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- CI-08
- CI-12

---

## REL-REL-060

### Title

Relationship Type Schema Definition

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Each Relationship Type **MUST** be defined by an identifiable relationship schema.

### Rationale

Schema-defined semantics allow compatible implementations to validate and interpret a Relationship Type independently of the application that created or displayed it.

### Source

- REM-05-066
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- CI-12

---

## REL-REL-061

### Title

Schema Direction Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify the direction semantics of its Relationship Type.

### Rationale

Direction affects authorisation, reciprocity, validation and presentation and should therefore be interpretable from the schema rather than inferred from application behaviour.

### Source

- REM-05-067
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-08

---

## REL-REL-062

### Title

Schema Reciprocity Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether independent reciprocal authorisation is required.

### Rationale

Explicit reciprocity semantics prevent a unilateral declaration from being interpreted as mutual consent.

### Source

- REM-05-068
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-08

---

## REL-REL-063

### Title

Schema Approval Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether approval by the Target or another authority is required before the relationship becomes active.

### Rationale

Approval is a distinct lifecycle condition from reciprocity and must be expressible for relationships requiring acceptance, verification or another authorising act.

### Source

- REM-05-069
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-08
- AI-09

---

## REL-REL-064

### Title

Schema Public-Visibility Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether conforming relationships may be publicly visible.

### Rationale

Public visibility must be constrained by protocol-understandable relationship semantics rather than left entirely to application presentation.

### Source

- REM-05-070
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-07

---

## REL-REL-065

### Title

Schema Expiration Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether conforming relationships may expire.

### Rationale

Schemas for time-bound relationships need to make expiration an interoperable lifecycle property rather than an application-local assumption.

### Source

- REM-05-071
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-09

---

## REL-REL-066

### Title

Schema Authority-Conveyance Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether its Relationship Type conveys any authority.

### Rationale

Authority must not be inferred from ordinary social or organisational labels. The schema should make any authority-bearing semantics explicit.

### Source

- REM-05-072
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- CI-06

---

## REL-REL-067

### Title

Schema Evidence Requirement Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify whether evidence or credentials are required to establish or validate the relationship.

### Rationale

Higher-assurance relationships may require evidence beyond self-declaration, and compatible implementations need to know when such evidence is required.

### Source

- REM-05-073
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- CI-06
- CI-10

---

## REL-REL-068

### Title

Schema Revocation Specification

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** specify how a conforming relationship may be revoked or ended.

### Rationale

Portable lifecycle semantics require implementations to understand how a relationship ceases to be operational and which authority may produce that change.

### Source

- REM-05-074
- `design-notes/05-relationship-model.md`, Section 7

### Related Invariants

- AI-09

---

## REL-REL-069

### Title

Relationship Direction Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support explicit representation or schema-defined interpretation of relationship direction.

### Rationale

Directed, reciprocal and mutually interpreted relationships have different authorisation and presentation consequences and therefore require protocol-understandable direction semantics.

### Source

- REM-05-075
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- AI-08

---

## REL-REL-070

### Title

Directed Relationship Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A directed relationship **MUST** represent a declaration made by one Source concerning a Target.

### Rationale

Direction identifies who makes the declaration and prevents the Target from being treated as a co-author merely because it is named by the relationship.

### Source

- REM-05-076
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-08

---

## REL-REL-071

### Title

Directed Relationship Independence from Matching Declarations

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A directed relationship **MUST NOT** require a matching declaration from the Target unless the applicable schema separately requires approval or reciprocity.

### Rationale

Directed relationships such as follows and blocks must be capable of representing one identity's independently authorised declaration without manufacturing a reciprocal dependency.

### Source

- REM-05-077
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- AI-08

---

## REL-REL-072

### Title

Reciprocal Relationship Independent Confirmation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A reciprocal relationship **MUST** be based on separate confirmation by each participating identity whose agreement is represented.

### Rationale

Reciprocity represents mutual agreement and therefore cannot be established through one participant's authority alone.

### Source

- REM-05-078
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-073

### Title

Mutual Presentation of Matching Directed Declarations

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** present two compatible matching directed declarations as one mutual relationship.

### Rationale

Applications may provide a convenient mutual view without converting the underlying independently authorised declarations into a single jointly controlled record.

### Source

- REM-05-079
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- AI-07
- AI-08

---

## REL-REL-074

### Title

Independent Authority Beneath Mutual Presentation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where matching directed declarations are presented as a mutual relationship, the underlying records **SHOULD** continue to identify each identity's independent authorisation.

### Rationale

A derived mutual view must not obscure which participant authorised each side or prevent implementations from evaluating each declaration independently.

### Source

- REM-05-080
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-075

### Title

Authority-Bearing Relationship Support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Relationship Model **MAY** support Relationship Types that convey limited authority.

### Rationale

Some relationships may represent constrained authority such as representation or administration, but authority-bearing semantics are not inherent in every relationship.

### Source

- REM-05-081
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-06

---

## REL-REL-076

### Title

Authority-Bearing Relationship Scope

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Any authority conveyed by a relationship **MUST** be limited to the scope defined by the applicable schema, relationship record and supporting authorisation.

### Rationale

The existence of an authority-bearing relationship cannot safely imply unrestricted identity, repository or administrative authority.

### Source

- REM-05-082
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-06

---

## REL-REL-077

### Title

Authority-Bearing Relationship Validation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Authority-bearing relationships **MUST** undergo stricter validation than ordinary social relationship declarations.

### Rationale

Relationships capable of conveying operational authority create greater security consequences than ordinary social declarations and therefore require correspondingly stronger assurance.

### Source

- REM-05-083
- `design-notes/05-relationship-model.md`, Section 8

### Related Invariants

- CI-06
- CI-10

---

## REL-REL-078

### Title

Unilateral Relationship Source Authorisation

**Level:** Constitutional

**Normative Keyword:** **MUST / MUST NOT**

### Statement

A unilateral relationship **MUST** require authorisation from its Source identity and **MUST NOT** require Target approval for the Source's declaration to exist unless the governing schema explicitly adds an approval condition.

### Rationale

Unilateral relationships represent the Source's independently authorised declaration. Target notification or separate Target rights must not be converted into an implicit consent requirement.

### Source

- REM-05-084
- REM-05-086
- `design-notes/05-relationship-model.md`, Section 9

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-079

### Title

Unilateral Relationship Target Notification

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An implementation **MAY** notify the Target that a unilateral relationship declaration has been made, subject to applicable visibility and privacy rules.

### Rationale

Notification may be useful to an affected Target but does not transform the Source's unilateral declaration into a reciprocal or approved relationship.

### Source

- REM-05-085
- `design-notes/05-relationship-model.md`, Section 9

### Related Invariants

- AI-07

---

## REL-REL-080

### Title

No False Representation of Target Agreement

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application or provider **MUST NOT** present a unilateral relationship as though the Target authorised, accepted, confirmed or endorsed it.

### Rationale

Presentation must preserve the distinction between a Source's declaration and mutual consent.

### Source

- REM-05-087
- `design-notes/05-relationship-model.md`, Section 9

### Related Invariants

- AI-07
- AI-08

---

## REL-REL-081

### Title

Unilateral Judgement Does Not Imply Target Verification

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Source's unilateral judgement about a Target **MUST NOT** be interpreted as verification, acceptance or endorsement by that Target.

### Rationale

Trust, endorsement and similar unilateral assertions describe the Source's position and cannot manufacture a claim about the Target's own authority or agreement.

### Source

- REM-05-088
- `design-notes/05-relationship-model.md`, Section 9

### Related Invariants

- AI-08

---

## REL-REL-082

### Title

Reciprocal Relationship Participant Authorisation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A reciprocal relationship **MUST** require independent authorisation from every participating identity whose agreement is represented.

### Rationale

No participant may manufacture another participant's side of a reciprocal relationship.

### Source

- REM-05-089
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-083

### Title

Reciprocal Proposal and Acceptance Workflow

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The Relationship Model **SHOULD** support proposal and acceptance workflows for reciprocal Relationship Types that require staged confirmation.

### Rationale

Some reciprocal relationships require one participant to propose and another to accept before mutual state can be presented as active.

### Source

- REM-05-090
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- AI-09

---

## REL-REL-084

### Title

Linked Reciprocal Record Representation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reciprocal relationship **MAY** be represented through separate linked relationship records controlled by the participating identities.

### Rationale

Linked records permit reciprocal semantics while preserving each participant's independent declaration and repository authority.

### Source

- REM-05-091
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-085

### Title

Reciprocal Record Source Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Each record participating in a reciprocal relationship **MUST** identify the identity authorising that record as its own Source.

### Rationale

Each side of a reciprocal relationship remains an independently attributable declaration even where applications present the records as a mutual connection.

### Source

- REM-05-092
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-08
- AI-08

---

## REL-REL-086

### Title

Reciprocal Record Reference

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reciprocal relationship record **MAY** include a stable reference to the corresponding record authorised by another participant.

### Rationale

A stable reciprocal reference permits independently controlled records to be associated without requiring shared ownership or a single canonical mutual record.

### Source

- REM-05-093
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-05
- AI-08

---

## REL-REL-087

### Title

Reciprocal Reference Does Not Replace Authorisation Validation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A reciprocal-record reference **MUST NOT** be treated as a substitute for validating the independent authorisation and current state of the referenced record.

### Rationale

A reference identifies another record but cannot itself prove that the other participant authorised that record or that its current state still supports a mutual interpretation.

### Source

- REM-05-094
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-06
- AI-08

---

## REL-REL-088

### Title

Independent Control of Reciprocal Declarations

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A participant in a reciprocal relationship **MUST NOT** be able to modify, revoke or otherwise control another participant's relationship declaration solely by controlling its own record.

### Rationale

Reciprocity does not merge participant authority. Each participant retains independent control over the declaration it authorised.

### Source

- REM-05-095
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-089

### Title

Independent Repository Authority for Reciprocal Records

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Each reciprocal relationship record **MUST** remain under the authority of the repository and identity that authorised that record.

### Rationale

Linking reciprocal records does not merge repository control or create shared ownership of either participant's declaration.

### Source

- REM-05-096
- `design-notes/05-relationship-model.md`, Section 10

### Related Invariants

- CI-02
- AI-01
- AI-08

---

# 4. Consolidation and Traceability Record

This part performs one genuine consolidation:

- `REM-05-084` and `REM-05-086` are consolidated into `REL-REL-078`. Both extract the same Section 9 authorisation boundary: a unilateral relationship requires the Source's authorisation while Target approval is not required for the Source's declaration to exist. The schema-qualified exception is retained.

No other REM-05 entries in the covered range are consolidated. In particular:

- Relationship Type identification and schema definition remain separate because a record identifying a type does not establish that the type has an independently interpretable schema.
- The eight schema-definition recommendations remain separate because each governs a distinct independently reviewable semantic dimension.
- General direction support remains separate from the semantics of directed, reciprocal, mutually interpreted and authority-bearing relationships.
- Independent reciprocal authorisation, linked-record representation, reciprocal references, reference validation, participant control and repository authority remain separate because each imposes a distinct protocol behaviour or authority boundary.

All REM-05 requirements from `REM-05-065` through `REM-05-096` are represented exactly once in the catalogue mapping, either independently or through the explicit consolidation above.

---

# 5. Editorial QA Record

## Scope verification

- Part 3 begins at `REM-05-065`, immediately after Part 2's final covered requirement `REM-05-064`.
- Coverage ends at `REM-05-096`, the end of source Section 10.
- Section 11 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 7–10.

## Numbering verification

- First catalogue requirement: `REL-REL-059`.
- Final catalogue requirement: `REL-REL-089`.
- Catalogue numbering continues directly from Part 2's `REL-REL-058`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- The single consolidated catalogue requirement retains both contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Section 7's schema guidance remains `SHOULD` rather than being promoted to mandatory schema requirements.
- Permitted behaviours and representations remain `MAY` where the verified extraction is permissive.
- Examples clarify semantics but do not create new relationship types, fields or mandatory serialisation syntax.

## Semantic-boundary verification

- Directed relationships remain distinguishable from reciprocal relationships.
- A derived mutual presentation does not replace the independently authorised underlying records.
- Authority-bearing relationships remain limited in scope and subject to stricter validation.
- Unilateral relationships remain Source-authorised and are not represented as Target consent.
- Reciprocal relationships preserve independent participant authorisation and independent record control.
- Reciprocal references do not become substitutes for validating the referenced declaration.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes the schema and authorisation semantics necessary to distinguish different kinds of relationships without collapsing them into a single social-graph concept. Relationship Type meaning remains schema-defined; direction and reciprocity remain explicit; unilateral declarations remain independent of Target consent; and reciprocal relationships preserve separate authority for every participant.

The next catalogue part should begin with `REM-05-097` / source Section 11 and continue catalogue numbering from `REL-REL-090`.