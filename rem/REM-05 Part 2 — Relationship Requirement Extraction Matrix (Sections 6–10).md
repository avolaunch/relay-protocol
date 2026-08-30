# REM-05 Part 2 — Relationship Requirement Extraction Matrix (Sections 6–10)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 6–10 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

6. Target
7. Relationship type
8. Direction
9. Unilateral relationships
10. Reciprocal relationships

Requirement identifiers continue sequentially from Part 1, beginning with `REM-05-054`.

---

# 6. Target

## REM-05-054 — Target semantics

**Source**  
Section 6: “The Target is the identity, record or recognised external entity to which the relationship points.”

**Requirement**  
A relationship record MUST identify the identity, record or recognised external entity to which the relationship declaration points as its Target.

**Classification**  
Relationship structure; target identification; semantic modelling.

**Notes**  
The Target is distinct from the Source making the declaration and from any application that submits the record.

---

## REM-05-055 — Relay Identity target support

**Source**  
Section 6, target types: “a Relay Identity”.

**Requirement**  
The Relationship Model MUST support a Relay Identity as a valid Target.

**Classification**  
Target type; identity relationship; interoperability.

**Notes**  
This supports relationships such as following, blocking, trusting or representing another Relay Identity.

---

## REM-05-056 — Relay Record target support

**Source**  
Section 6, target types: “a Relay Record”.

**Requirement**  
The Relationship Model MUST support a Relay Record as a valid Target.

**Classification**  
Target type; record relationship; referential modelling.

**Notes**  
This supports relationships such as authorship, ownership, endorsement or attachment to a specific record.

---

## REM-05-057 — Defined-group target support

**Source**  
Section 6, target types: “a defined group”.

**Requirement**  
The Relationship Model MUST support a defined group as a valid Target where the group is represented by a resolvable or schema-recognised identifier.

**Classification**  
Target type; group modelling; interoperability.

**Notes**  
The source permits groups as targets but does not define the complete group model in this section.

---

## REM-05-058 — Organisation target support

**Source**  
Section 6, target types: “an organisation”.

**Requirement**  
The Relationship Model MUST support an organisation as a valid Target.

**Classification**  
Target type; organisational relationship.

**Notes**  
An organisation may itself be represented by a Relay Identity or another recognised stable identifier.

---

## REM-05-059 — Credential target support

**Source**  
Section 6, target types: “a credential”.

**Requirement**  
The Relationship Model MUST support a credential as a valid Target.

**Classification**  
Target type; credential relationship; assertion modelling.

**Notes**  
This permits relationships such as holding, endorsing, revoking or relying upon a credential where the applicable schema allows them.

---

## REM-05-060 — Application target support

**Source**  
Section 6, target types: “an application”.

**Requirement**  
The Relationship Model MUST support a Relay Application as a valid Target.

**Classification**  
Target type; application relationship; trust modelling.

**Notes**  
An application target should be identified through its stable Application Identity rather than only by a visible product name or domain.

---

## REM-05-061 — External-identifier target support

**Source**  
Section 6, target types: “an external identifier where no Relay Identity exists.”

**Requirement**  
The Relationship Model MAY represent a recognised external identifier as the Target where no suitable Relay Identity exists.

**Classification**  
External interoperability; provisional identity reference; target type.

**Notes**  
The external identifier should be sufficiently qualified to avoid ambiguity and should not be mistaken for a Relay-native identity.

---

## REM-05-062 — Stable Relay target identifiers preferred

**Source**  
Section 6: “The target should use a stable Relay identifier wherever possible.”

**Requirement**  
A relationship Target SHOULD use a stable Relay identifier wherever one is available.

**Classification**  
Identifier stability; portability; recommendation.

**Notes**  
Stable Relay identifiers improve portability, resolution and continuity across applications and providers.

---

## REM-05-063 — Temporary provider URLs not sufficient as sole permanent references

**Source**  
Section 6: “Temporary provider URLs and visible handles should not be used as the sole permanent target reference.”

**Requirement**  
A relationship record SHOULD NOT use a temporary provider URL as its sole permanent Target reference.

**Classification**  
Provider independence; identifier stability; portability.

**Notes**  
A temporary URL may be included as auxiliary resolution information, but it should not define the enduring identity of the Target.

---

## REM-05-064 — Visible handles not sufficient as sole permanent references

**Source**  
Section 6: “Temporary provider URLs and visible handles should not be used as the sole permanent target reference.”

**Requirement**  
A relationship record SHOULD NOT use a mutable visible handle as its sole permanent Target reference.

**Classification**  
Handle independence; identifier stability; portability.

**Notes**  
Handles may change, collide or be reassigned. A stable protocol identifier should anchor the Target where possible.

---

# 7. Relationship type

## REM-05-065 — Relationship Type semantics

**Source**  
Section 7: “The Relationship Type defines the meaning of the connection.”

**Requirement**  
Every relationship record MUST identify a Relationship Type that defines the semantic meaning of the connection.

**Classification**  
Relationship semantics; schema identification; interoperability.

**Notes**  
The Relationship Type is not merely a user-interface label. It determines the schema-defined behaviour and interpretation of the relationship.

---

## REM-05-066 — Schema definition required for each relationship type

**Source**  
Section 7: “Each relationship type must be defined by a schema.”

**Requirement**  
Each Relationship Type MUST be defined by an identifiable schema.

**Classification**  
Schema governance; relationship typing; validation.

**Notes**  
Applications must not invent private relationship semantics that cannot be identified or validated outside the originating application.

---

## REM-05-067 — Schema direction specification

**Source**  
Section 7, schema guidance: “direction”.

**Requirement**  
A relationship schema SHOULD specify the direction semantics of the Relationship Type.

**Classification**  
Schema definition; directionality; recommendation.

**Notes**  
Direction semantics may identify the relationship as directed, reciprocal, mutually interpreted or authority-bearing.

---

## REM-05-068 — Schema reciprocity specification

**Source**  
Section 7, schema guidance: “whether reciprocity is required”.

**Requirement**  
A relationship schema SHOULD specify whether independent reciprocal authorisation is required.

**Classification**  
Schema definition; reciprocity; consent.

**Notes**  
This prevents a unilateral record from being incorrectly interpreted as a mutually confirmed relationship.

---

## REM-05-069 — Schema approval specification

**Source**  
Section 7, schema guidance: “whether approval is required”.

**Requirement**  
A relationship schema SHOULD specify whether approval by the Target or another authority is required before the relationship becomes active.

**Classification**  
Schema definition; approval workflow; lifecycle.

**Notes**  
Approval requirements may differ from reciprocity. A schema may require acceptance, verification or another form of authorisation.

---

## REM-05-070 — Schema public-visibility specification

**Source**  
Section 7, schema guidance: “whether the relationship may be public”.

**Requirement**  
A relationship schema SHOULD specify whether conforming relationships may be publicly visible.

**Classification**  
Schema definition; visibility; privacy.

**Notes**  
Applications and repositories should not expose a relationship publicly where its schema prohibits public visibility.

---

## REM-05-071 — Schema expiration specification

**Source**  
Section 7, schema guidance: “whether it may expire”.

**Requirement**  
A relationship schema SHOULD specify whether conforming relationships may expire.

**Classification**  
Schema definition; lifecycle; temporal validity.

**Notes**  
Where expiration is supported, the schema should define how the validity period and expired state are represented.

---

## REM-05-072 — Schema authority-conveyance specification

**Source**  
Section 7, schema guidance: “whether it conveys authority”.

**Requirement**  
A relationship schema SHOULD specify whether the Relationship Type conveys any authority.

**Classification**  
Schema definition; delegated authority; security.

**Notes**  
Authority-bearing relationships require stronger validation and must not be inferred from ordinary social relationships.

---

## REM-05-073 — Schema evidence-requirement specification

**Source**  
Section 7, schema guidance: “whether evidence or credentials are required”.

**Requirement**  
A relationship schema SHOULD specify whether evidence or credentials are required to establish or validate the relationship.

**Classification**  
Schema definition; evidence; verification.

**Notes**  
Evidence requirements may apply to employment, representation, guardianship, ownership or other higher-assurance relationships.

---

## REM-05-074 — Schema revocation specification

**Source**  
Section 7, schema guidance: “how it may be revoked.”

**Requirement**  
A relationship schema SHOULD specify how a conforming relationship may be revoked or ended.

**Classification**  
Schema definition; revocation; lifecycle.

**Notes**  
The schema should identify which party may revoke, what resulting status applies and whether reciprocal records are affected independently.

---

# 8. Direction

## REM-05-075 — Direction classification support

**Source**  
Section 8: “A relationship may be” directed, reciprocal, undirected by interpretation or authority-bearing.

**Requirement**  
The Relationship Model MUST support explicit representation or schema-defined interpretation of relationship direction.

**Classification**  
Directionality; relationship structure; interoperability.

**Notes**  
Different direction models have different authorisation, presentation and validation consequences.

---

## REM-05-076 — Directed relationship semantics

**Source**  
Section 8, Directed: “One identity makes a declaration about another.”

**Requirement**  
A directed relationship MUST represent a declaration made by one Source concerning a Target.

**Classification**  
Directionality; unilateral declaration; semantic modelling.

**Notes**  
The Target does not become a co-author of the declaration merely because it is named by it.

---

## REM-05-077 — Directed relationships do not require matching declarations

**Source**  
Section 8, Directed: “Bob does not need to make a matching declaration.”

**Requirement**  
A directed relationship MUST NOT require a matching declaration from the Target unless the applicable schema separately requires approval or reciprocity.

**Classification**  
Directionality; authorisation; unilateral relationship.

**Notes**  
Examples include follow, subscribe and block relationships.

---

## REM-05-078 — Reciprocal relationship independent confirmation

**Source**  
Section 8, Reciprocal: “Both identities separately confirm a relationship.”

**Requirement**  
A reciprocal relationship MUST be based on separate confirmation by each participating identity.

**Classification**  
Reciprocity; independent authority; consent.

**Notes**  
A single record controlled by one identity is insufficient to establish mutual confirmation.

---

## REM-05-079 — Matching directed declarations may be presented mutually

**Source**  
Section 8, Undirected by interpretation: “Two matching directed declarations may be presented as one mutual relationship.”

**Requirement**  
An application MAY present two compatible matching directed declarations as one mutual relationship.

**Classification**  
Presentation; relationship interpretation; application behaviour.

**Notes**  
The mutual presentation is a derived interpretation and must not erase or replace the underlying independently authorised records.

---

## REM-05-080 — Independent authority retained beneath mutual presentation

**Source**  
Section 8: “The underlying records should still identify each identity’s independent authority.”

**Requirement**  
Where matching declarations are presented as a mutual relationship, the underlying records SHOULD continue to identify each identity’s independent authorisation.

**Classification**  
Authority provenance; derived presentation; recommendation.

**Notes**  
Applications should be able to determine which party authorised each side and whether either side has ended or changed its declaration.

---

## REM-05-081 — Authority-bearing relationship support

**Source**  
Section 8, Authority-bearing: “A relationship may convey limited authority.”

**Requirement**  
The Relationship Model MAY support Relationship Types that convey limited authority.

**Classification**  
Authority relationship; delegation; extensibility.

**Notes**  
Examples include representation of an organisation or administration of a team.

---

## REM-05-082 — Authority-bearing scope must remain limited

**Source**  
Section 8: “A relationship may convey limited authority.”

**Requirement**  
Any authority conveyed by a relationship MUST be limited to the scope defined by the applicable schema, record and supporting authorisation.

**Classification**  
Least privilege; delegated authority; security.

**Notes**  
The existence of an authority-bearing relationship must not be interpreted as unrestricted identity, repository or administrative authority.

---

## REM-05-083 — Stricter validation for authority-bearing relationships

**Source**  
Section 8: “Authority-bearing relationships require stricter validation than ordinary social connections.”

**Requirement**  
Authority-bearing relationships MUST undergo stricter validation than ordinary social relationship declarations.

**Classification**  
Security; authority validation; assurance.

**Notes**  
Stricter validation may include approval, credential evidence, stronger authentication, validity checks or verification of the granting authority.

---

# 9. Unilateral relationships

## REM-05-084 — Source-only authorisation for unilateral relationships

**Source**  
Section 9: “A unilateral relationship requires only the source identity’s authorisation.”

**Requirement**  
A unilateral relationship MUST require authorisation from the Source identity and MUST NOT require Target approval unless the schema explicitly adds such a condition.

**Classification**  
Unilateral relationship; authorisation; consent boundary.

**Notes**  
The source model identifies follow, subscribe, block, mute, endorse, trust, bookmark and watch as examples.

---

## REM-05-085 — Target notification permitted

**Source**  
Section 9: “The target may be notified...”

**Requirement**  
An implementation MAY notify the Target that a unilateral relationship declaration has been made, subject to applicable visibility and privacy rules.

**Classification**  
Notification; application behaviour; privacy.

**Notes**  
Notification does not convert the relationship into a reciprocal or approved relationship.

---

## REM-05-086 — Target approval not required for unilateral relationships

**Source**  
Section 9: “...but does not need to approve the relationship.”

**Requirement**  
The Target MUST NOT be required to approve a unilateral relationship for the Source’s declaration to exist.

**Classification**  
Unilateral relationship; lifecycle; authority.

**Notes**  
The Target may still exercise separate rights defined by the schema or protocol, such as blocking visibility or disputing a misleading presentation.

---

## REM-05-087 — No false representation of Target agreement

**Source**  
Section 9: “A unilateral relationship must not be presented as though the target agreed to it.”

**Requirement**  
An application or provider MUST NOT present a unilateral relationship as though the Target authorised, accepted, confirmed or endorsed it.

**Classification**  
Presentation integrity; consent; anti-misrepresentation.

**Notes**  
The distinction must remain clear in user interfaces, derived views, exports and APIs.

---

## REM-05-088 — Source judgement does not imply Target verification

**Source**  
Section 9 example: “Alice considers Bob a trusted source” does not mean “Bob has accepted or verified Alice’s judgement.”

**Requirement**  
A Source’s unilateral judgement about a Target MUST NOT be interpreted as verification, acceptance or endorsement by the Target.

**Classification**  
Semantic integrity; unilateral assertion; verification boundary.

**Notes**  
This is particularly important for trust, endorsement and reputation-related Relationship Types.

---

# 10. Reciprocal relationships

## REM-05-089 — Independent authorisation required from each participant

**Source**  
Section 10: “A reciprocal relationship requires independent authorisation from each participating identity.”

**Requirement**  
A reciprocal relationship MUST require independent authorisation from every participating identity whose agreement is represented.

**Classification**  
Reciprocity; consent; independent authority.

**Notes**  
One participant cannot authorise or fabricate the other participant’s side of the relationship.

---

## REM-05-090 — Proposal and acceptance workflow support

**Source**  
Section 10 example: “Alice proposes collaboration with Bob. Bob accepts.”

**Requirement**  
The Relationship Model SHOULD support proposal and acceptance workflows for reciprocal Relationship Types that require staged confirmation.

**Classification**  
Lifecycle; reciprocal relationship; recommendation.

**Notes**  
The exact statuses and transitions are schema-defined.

---

## REM-05-091 — Linked-record representation permitted

**Source**  
Section 10: “This may produce two linked records.”

**Requirement**  
A reciprocal relationship MAY be represented through separate linked relationship records controlled by the participating identities.

**Classification**  
Record structure; reciprocity; distributed authority.

**Notes**  
Each record represents one identity’s independently authorised declaration.

---

## REM-05-092 — Each reciprocal record identifies its own Source

**Source**  
Section 10, Alice’s and Bob’s record examples.

**Requirement**  
Each record participating in a reciprocal relationship MUST identify the identity authorising that record as its own Source.

**Classification**  
Source integrity; reciprocal record structure; authority provenance.

**Notes**  
The two records reverse Source and Target according to the identity controlling each declaration.

---

## REM-05-093 — Reciprocal record references permitted

**Source**  
Section 10 examples include `reciprocalRecord` references.

**Requirement**  
A reciprocal relationship record MAY include a stable reference to the corresponding record authorised by the other participant.

**Classification**  
Referential integrity; reciprocal linkage; interoperability.

**Notes**  
The example field name and serialisation are illustrative rather than final syntax.

---

## REM-05-094 — Reciprocal references must not replace independent authorisation

**Source**  
Section 10, linked-record model and independent authorisation requirement.

**Requirement**  
A reciprocal-record reference MUST NOT be treated as a substitute for validating the independent authorisation and current state of the referenced record.

**Classification**  
Validation; reciprocal authority; integrity.

**Notes**  
A stale, missing or revoked reciprocal record may change how the relationship is presented without invalidating the other identity’s historical declaration.

---

## REM-05-095 — No control over another participant’s declaration

**Source**  
Section 10: “Neither identity controls the other’s declaration.”

**Requirement**  
No participant in a reciprocal relationship MUST be able to modify, revoke or otherwise control another participant’s relationship declaration solely by controlling its own record.

**Classification**  
Independent control; reciprocity; repository authority.

**Notes**  
Each participant may change or end its own side. Applications may then derive that the mutual relationship is no longer active.

---

## REM-05-096 — Independent repository authority for reciprocal records

**Source**  
Section 10, separate Alice and Bob records and statement that neither controls the other’s declaration.

**Requirement**  
Each reciprocal relationship record MUST remain under the authority of the repository and identity that authorised that record.

**Classification**  
Repository authority; distributed relationship state; portability.

**Notes**  
Linking records does not merge repository control or create shared ownership of either record.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 6–10 of `design-notes/05-relationship-model.md`.
- Section 11 and later content was excluded from independent extraction.
- Examples were used to clarify semantics without promoting illustrative field names or serialisation into final syntax.

## Numbering verification

- First requirement: `REM-05-054`.
- Final requirement: `REM-05-096`.
- Requirement numbering continues directly from Part 1.
- Requirement identifiers are continuous, unique and ordered by source section.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each requirement is traceable to an explicit definition, statement, list item, example consequence or necessary decomposition of a compound source rule.
- Schema guidance expressed as “should” remains `SHOULD` rather than being strengthened into an unconditional mandate.
- Permitted target types and representational options remain `MAY` where the source permits rather than requires them.

## Editorial verification

- Stable protocol identifiers remain preferred over provider URLs and visible handles.
- Relationship Type semantics remain schema-defined and application-independent.
- Directed, reciprocal, mutually interpreted and authority-bearing relationships remain distinct.
- Unilateral relationships are not misrepresented as Target consent.
- Reciprocal relationships preserve independent authorisation, record control and repository authority for every participant.
- Authority-bearing relationships are not treated as ordinary social links and require stronger validation.
