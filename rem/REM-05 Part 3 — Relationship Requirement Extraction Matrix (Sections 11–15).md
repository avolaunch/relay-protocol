# REM-05 Part 3 — Relationship Requirement Extraction Matrix (Sections 11–15)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 11–15 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

11. Relationship status
12. Relationship lifecycle
13. Relationship ownership
14. Relationship continuity
15. Follows

Requirement identifiers continue sequentially from Part 2, beginning with `REM-05-097`.

---

# 11. Relationship status

## REM-05-097 — Schema-governed relationship status

**Source**  
Section 11: “A relationship may have a status such as... The allowed states depend on the relationship schema.”

**Requirement**  
A relationship schema MUST define or constrain the statuses permitted for records of that relationship type.

**Classification**  
Schema behaviour; lifecycle state; validation.

**Notes**  
The source lists `proposed`, `pending`, `active`, `declined`, `ended`, `revoked`, `expired`, `disputed` and `suspended` as possible examples rather than a universal closed enumeration.

---

## REM-05-098 — Proposed status support

**Source**  
Section 11, example status: `proposed`.

**Requirement**  
A relationship schema MAY support a `proposed` status for a declaration that has been initiated but is not yet accepted or operational.

**Classification**  
Lifecycle state; proposal workflow.

**Notes**  
This status is most relevant to reciprocal or approval-based relationship types.

---

## REM-05-099 — Pending status support

**Source**  
Section 11, example status: `pending`.

**Requirement**  
A relationship schema MAY support a `pending` status where further approval, evidence or validation is required before activation.

**Classification**  
Lifecycle state; approval workflow.

**Notes**  
The schema should determine what event or authority moves the relationship out of the pending state.

---

## REM-05-100 — Active status support

**Source**  
Section 11, example status: `active`.

**Requirement**  
A relationship schema MAY support an `active` status to identify a relationship that is currently operational under that schema.

**Classification**  
Lifecycle state; current relationship state.

**Notes**  
Active status does not itself imply that the relationship conveys authority, access or reciprocity.

---

## REM-05-101 — Declined status support

**Source**  
Section 11, example status: `declined`.

**Requirement**  
A relationship schema MAY support a `declined` status where a required participant refuses a proposed or pending relationship.

**Classification**  
Lifecycle state; denial outcome.

**Notes**  
A declined status records the relationship workflow outcome without representing the relationship as active.

---

## REM-05-102 — Ended status support

**Source**  
Section 11, example status: `ended`.

**Requirement**  
A relationship schema MAY support an `ended` status for a relationship that was previously operational but has been terminated.

**Classification**  
Lifecycle state; termination.

**Notes**  
An ended relationship may remain historically verifiable where the schema requires preservation of relationship history.

---

## REM-05-103 — Revoked status support

**Source**  
Section 11, example status: `revoked`.

**Requirement**  
A relationship schema MAY support a `revoked` status where the authority underlying a declaration has been withdrawn.

**Classification**  
Lifecycle state; revocation.

**Notes**  
Revocation applies to the relevant declaration and must not be interpreted as control over another identity’s independent record.

---

## REM-05-104 — Expired status support

**Source**  
Section 11, example status: `expired`.

**Requirement**  
A relationship schema MAY support an `expired` status where the relationship ceases automatically at the end of a defined validity period.

**Classification**  
Lifecycle state; temporal validity.

**Notes**  
Where expiration is supported, the schema should define the applicable validity fields and transition rules.

---

## REM-05-105 — Disputed status support

**Source**  
Section 11, example status: `disputed`.

**Requirement**  
A relationship schema MAY support a `disputed` status where a participant challenges an asserted or externally supported relationship.

**Classification**  
Lifecycle state; dispute handling.

**Notes**  
Disputed status does not by itself establish that the underlying assertion is true or false.

---

## REM-05-106 — Suspended status support

**Source**  
Section 11, example status: `suspended`.

**Requirement**  
A relationship schema MAY support a `suspended` status where the relationship temporarily stops producing effects without being permanently ended.

**Classification**  
Lifecycle state; temporary interruption.

**Notes**  
The schema should define whether and how a suspended relationship can return to active status.

---

## REM-05-107 — Direct activation for simple relationships

**Source**  
Section 11: “A simple follow may move directly from nonexistent to active.”

**Requirement**  
A schema for a simple unilateral relationship MAY permit creation directly in the active state without proposal or pending stages.

**Classification**  
Lifecycle simplification; unilateral relationship behaviour.

**Notes**  
This permission does not apply automatically to relationships requiring approval, evidence or reciprocity.

---

## REM-05-108 — Multi-stage activation for collaborations

**Source**  
Section 11: “A collaboration may require: proposed → pending → active.”

**Requirement**  
A collaboration schema MAY require a staged transition from proposed to pending to active.

**Classification**  
Lifecycle workflow; reciprocal relationship behaviour.

**Notes**  
The exact transition model remains schema-defined.

---

## REM-05-109 — Credential-based relationship validation

**Source**  
Section 11: “A verified employment relationship may require an external credential rather than a simple self-declaration.”

**Requirement**  
A schema for a verified employment or similarly evidence-dependent relationship MAY require an external credential rather than accepting an unsupported self-declaration.

**Classification**  
Evidence; credential validation; relationship assurance.

**Notes**  
This distinguishes a claim of employment from a verified employment relationship.

---

# 12. Relationship lifecycle

## REM-05-110 — Schema-defined lifecycle support

**Source**  
Section 12: “A relationship lifecycle may include...”

**Requirement**  
A relationship schema MAY define a lifecycle containing one or more of the proposal, acceptance, activation, modification, suspension, termination, expiration and dispute stages.

**Classification**  
Lifecycle modelling; schema behaviour.

**Notes**  
Not every relationship type must implement every listed stage.

---

## REM-05-111 — Proposal-stage semantics

**Source**  
Section 12, Proposal: “One identity proposes a reciprocal or approval-based relationship.”

**Requirement**  
Where a proposal stage exists, it MUST represent one identity proposing a reciprocal or approval-based relationship.

**Classification**  
Lifecycle semantics; proposal.

**Notes**  
A proposal is not equivalent to acceptance or activation.

---

## REM-05-112 — Acceptance-stage semantics

**Source**  
Section 12, Acceptance: “The target authorises its side.”

**Requirement**  
Where an acceptance stage exists, it MUST represent the target independently authorising its side of the relationship.

**Classification**  
Lifecycle semantics; reciprocal authorisation.

**Notes**  
Acceptance must not allow the proposing identity to control the target’s declaration.

---

## REM-05-113 — Activation-stage semantics

**Source**  
Section 12, Activation: “The relationship becomes operational.”

**Requirement**  
Where an activation stage exists, it MUST identify the point at which the relationship becomes operational under the applicable schema.

**Classification**  
Lifecycle semantics; activation.

**Notes**  
The operational effects of activation remain relationship-type specific.

---

## REM-05-114 — Modification-stage support

**Source**  
Section 12, Modification: “Context, visibility, role or conditions change.”

**Requirement**  
A relationship lifecycle MAY support modification of context, visibility, role or conditions.

**Classification**  
Lifecycle operation; relationship update.

**Notes**  
A modification must remain subject to the authority and schema rules applicable to the declaration being changed.

---

## REM-05-115 — Context modification

**Source**  
Section 12, Modification: “Context... change.”

**Requirement**  
Where permitted by the schema, the context associated with a relationship MAY be changed through an authorised lifecycle operation.

**Classification**  
Relationship context; update semantics.

**Notes**  
Changing context must not silently change the underlying relationship type unless the schema explicitly permits that transition.

---

## REM-05-116 — Visibility modification

**Source**  
Section 12, Modification: “visibility... change.”

**Requirement**  
Where permitted by the schema and authority model, the visibility of a relationship declaration MAY be changed independently of its substantive type.

**Classification**  
Visibility; lifecycle update; access control.

**Notes**  
Changing visibility must remain a separately authorised operation where the permission model requires it.

---

## REM-05-117 — Role modification

**Source**  
Section 12, Modification: “role... change.”

**Requirement**  
A relationship schema MAY permit the role represented by an existing relationship to change through an authorised modification.

**Classification**  
Role modelling; lifecycle update.

**Notes**  
The schema should define whether a role change updates the same logical relationship or requires a superseding record.

---

## REM-05-118 — Condition modification

**Source**  
Section 12, Modification: “conditions change.”

**Requirement**  
A relationship schema MAY permit authorised changes to the conditions attached to a relationship declaration.

**Classification**  
Conditional relationship behaviour; lifecycle update.

**Notes**  
A change to conditions must not expand authority beyond what the controlling identity is entitled to grant.

---

## REM-05-119 — Suspension-stage semantics

**Source**  
Section 12, Suspension: “The relationship temporarily stops producing effects without being permanently ended.”

**Requirement**  
Where suspension is supported, a suspended relationship MUST temporarily stop producing its schema-defined effects without being represented as permanently ended.

**Classification**  
Lifecycle semantics; suspension.

**Notes**  
Historical existence and ownership of the declaration remain unaffected by temporary suspension.

---

## REM-05-120 — Termination-stage semantics

**Source**  
Section 12, Termination: “One or both parties end the relationship.”

**Requirement**  
Where termination is supported, the lifecycle MUST allow one or both authorised parties to end the relationship according to the schema’s control rules.

**Classification**  
Lifecycle semantics; termination; party authority.

**Notes**  
Each party remains limited to the authority it has over its own declaration unless the schema establishes a valid shared control mechanism.

---

## REM-05-121 — Expiration-stage semantics

**Source**  
Section 12, Expiration: “The relationship ends automatically at a defined time.”

**Requirement**  
Where expiration is supported, the relationship MUST end automatically at the defined expiration time.

**Classification**  
Lifecycle semantics; temporal enforcement.

**Notes**  
The expiry event should remain distinguishable from manual termination or revocation.

---

## REM-05-122 — Dispute-stage semantics

**Source**  
Section 12, Dispute: “One party challenges an externally issued or asserted relationship.”

**Requirement**  
Where dispute handling is supported, the lifecycle MUST allow a party to challenge an externally issued or asserted relationship.

**Classification**  
Lifecycle semantics; dispute handling; external assertions.

**Notes**  
A dispute record or status should preserve the distinction between the original assertion and the challenging party’s response.

---

## REM-05-123 — Verifiable relationship history

**Source**  
Section 12: “The relationship history should remain verifiable where the schema requires it.”

**Requirement**  
Where required by the relationship schema, the lifecycle history SHOULD remain verifiable.

**Classification**  
History; provenance; recommendation.

**Notes**  
Verifiability may include the sequence of accepted states, responsible authorities and relevant supporting records.

---

# 13. Relationship ownership

## REM-05-124 — Declarant control of relationship records

**Source**  
Section 13: “Each identity owns and controls its own relationship declaration.”

**Requirement**  
Each Relay Identity MUST retain control over its own relationship declaration.

**Classification**  
Ownership; identity authority; record control.

**Notes**  
“Owns” is treated as protocol control over the declaration, not necessarily as a statement of external legal property rights.

---

## REM-05-125 — Alice controls Alice’s mutual-relationship record

**Source**  
Section 13: “For a mutual relationship: Alice controls Alice’s record...”

**Requirement**  
In a mutual relationship, each participant MUST control the relationship record stored under that participant’s authority.

**Classification**  
Reciprocal relationship ownership; distributed control.

**Notes**  
The source’s Alice/Bob example expresses a general rule applying to every participant.

---

## REM-05-126 — Independent control of reciprocal declarations

**Source**  
Section 13: “Bob controls Bob’s record.”

**Requirement**  
A participant in a reciprocal relationship MUST NOT depend on the other participant for control of its own declaration.

**Classification**  
Distributed control; reciprocity; application independence.

**Notes**  
Linked reciprocal records may coordinate state while remaining independently controlled.

---

## REM-05-127 — No silent rewriting of another party’s declaration

**Source**  
Section 13: “Neither party may silently rewrite... the other party’s declaration.”

**Requirement**  
A relationship participant MUST NOT silently rewrite another participant’s independently controlled relationship declaration.

**Classification**  
Integrity; ownership boundary; unauthorised modification prevention.

**Notes**  
A participant may publish its own changed state or a reference indicating loss of reciprocity, but it cannot alter the other repository’s authoritative record without valid authority.

---

## REM-05-128 — No silent deletion of another party’s declaration

**Source**  
Section 13: “Neither party may silently... delete the other party’s declaration.”

**Requirement**  
A relationship participant MUST NOT silently delete another participant’s independently controlled relationship declaration.

**Classification**  
Deletion authority; ownership boundary; integrity.

**Notes**  
This prohibition does not prevent the other participant from deleting its own declaration through an authorised operation.

---

## REM-05-129 — Self-revocation of participation

**Source**  
Section 13: “If Alice ends a collaboration, Alice may revoke her own active participation.”

**Requirement**  
A participant MAY revoke or end its own active participation in a relationship where permitted by the schema.

**Classification**  
Participant autonomy; revocation; lifecycle.

**Notes**  
Self-revocation does not grant control over the other participant’s historical or current record.

---

## REM-05-130 — Reciprocal state may reflect loss of activity

**Source**  
Section 13: “Bob’s record may then reflect that the reciprocal relationship is no longer active...”

**Requirement**  
A participant’s relationship record MAY reflect that a reciprocal relationship is no longer active after the other participant ends its side.

**Classification**  
Reciprocal state; synchronisation; lifecycle reflection.

**Notes**  
The reflecting record must preserve attribution and must not falsely claim control over the other participant’s declaration.

---

## REM-05-131 — Historical-record control remains with the declarant

**Source**  
Section 13: “...but Bob retains control over Bob’s historical record.”

**Requirement**  
A participant MUST retain control over its own historical relationship record after the reciprocal relationship ceases to be active.

**Classification**  
Historical integrity; ownership; continuity.

**Notes**  
The end of reciprocity does not transfer or erase control of either party’s repository history.

---

# 14. Relationship continuity

## REM-05-132 — Stable identity requirement for portability

**Source**  
Section 14: “A relationship remains operationally portable when: both identities retain stable Relay Identifiers...”

**Requirement**  
Operational relationship portability REQUIRES each participating Relay Identity to retain a stable Relay Identifier.

**Classification**  
Portability; identity persistence; continuity.

**Notes**  
Mutable handles or provider-local usernames are insufficient as the sole enduring identity references.

---

## REM-05-133 — Stable relationship-record URI requirement

**Source**  
Section 14: “...the relationship records preserve stable Record URIs...”

**Requirement**  
Operational relationship portability REQUIRES the relevant relationship records to preserve stable Record URIs.

**Classification**  
Portability; record identity; continuity.

**Notes**  
The logical relationship declaration must remain addressable across application or provider changes.

---

## REM-05-134 — Compatible schema understanding requirement

**Source**  
Section 14: “...compatible applications understand the relationship schema...”

**Requirement**  
Operational relationship portability REQUIRES compatible applications to understand the applicable relationship schema sufficiently to interpret the connection.

**Classification**  
Interoperability; schema support; portability.

**Notes**  
An application may preserve an unsupported record without being able to present or operate on it fully.

---

## REM-05-135 — Provider migration must preserve source identity

**Source**  
Section 14: “...provider migration does not alter source or target identity...”

**Requirement**  
Provider migration MUST NOT alter the source identity of a relationship declaration.

**Classification**  
Migration; identity continuity; relationship integrity.

**Notes**  
The authoritative repository location may change while the source identity remains stable.

---

## REM-05-136 — Provider migration must preserve target identity

**Source**  
Section 14: “...provider migration does not alter source or target identity...”

**Requirement**  
Provider migration MUST NOT alter the target identity or target reference of a relationship declaration solely because the provider changed.

**Classification**  
Migration; target continuity; relationship integrity.

**Notes**  
A legitimate target update requires its own authorised and schema-valid operation.

---

## REM-05-137 — Current repository discovery requirement

**Source**  
Section 14: “...applications can discover the current repositories involved.”

**Requirement**  
Operational relationship portability REQUIRES applications to be able to discover the current repositories associated with the identities or records involved.

**Classification**  
Discovery; resolution; portability.

**Notes**  
Discovery allows stable identifiers to remain usable after repositories move between providers.

---

## REM-05-138 — Application replacement without relationship recreation

**Source**  
Section 14: “Changing from Application A to Application B must not require recreating the underlying relationship.”

**Requirement**  
Replacing one compatible application with another MUST NOT require recreation of the underlying relationship record solely because the application changed.

**Classification**  
Application replaceability; continuity; portability.

**Notes**  
The replacement application may require a new permission grant, but the relationship itself remains repository-controlled state.

---

## REM-05-139 — Provider replacement without source alteration

**Source**  
Section 14: “Changing Relay Provider must not alter the relationship’s source or target.”

**Requirement**  
Changing Relay Provider MUST NOT alter the relationship’s source.

**Classification**  
Provider portability; identity continuity.

**Notes**  
The source remains the same Relay Identity or Relay Record after migration.

---

## REM-05-140 — Provider replacement without target alteration

**Source**  
Section 14: “Changing Relay Provider must not alter the relationship’s source or target.”

**Requirement**  
Changing Relay Provider MUST NOT alter the relationship’s target.

**Classification**  
Provider portability; target continuity.

**Notes**  
A provider change is an infrastructure event, not a semantic change to the relationship.

---

# 15. Follows

## REM-05-141 — Follow as directed declaration

**Source**  
Section 15: “A follow is a directed declaration...”

**Requirement**  
A follow relationship MUST be represented as a directed declaration from a source to a target.

**Classification**  
Relationship semantics; directed relationship; follow.

**Notes**  
The target does not need to create a matching declaration for the follow to exist.

---

## REM-05-142 — Follow receipt purpose

**Source**  
Section 15: a follow indicates that “the source wishes to receive... public activity from the target.”

**Requirement**  
A follow MAY indicate that the source wishes to receive public activity from the target.

**Classification**  
Follow semantics; activity delivery.

**Notes**  
Actual delivery remains subject to application behaviour, target availability and applicable visibility rules.

---

## REM-05-143 — Follow discovery purpose

**Source**  
Section 15: a follow indicates that “the source wishes to... discover... public activity from the target.”

**Requirement**  
A follow MAY be used as a signal that the source wishes to discover public activity from the target.

**Classification**  
Follow semantics; discovery.

**Notes**  
A follow does not guarantee that all public activity will be discovered or delivered.

---

## REM-05-144 — Follow prioritisation purpose

**Source**  
Section 15: a follow indicates that “the source wishes to... prioritise public activity from the target.”

**Requirement**  
A follow MAY be used as an input for prioritising public activity from the target.

**Classification**  
Follow semantics; ranking; feed construction.

**Notes**  
The follow record is one possible signal and does not prescribe a universal ranking algorithm.

---

## REM-05-145 — Follow does not grant restricted-record access

**Source**  
Section 15: “A follow does not automatically grant: access to restricted records...”

**Requirement**  
A follow relationship MUST NOT be interpreted as granting access to restricted records.

**Classification**  
Access control; follow limitation.

**Notes**  
Restricted access requires a separate visibility rule, audience relationship or permission basis.

---

## REM-05-146 — Follow does not grant messaging rights

**Source**  
Section 15: “A follow does not automatically grant... messaging rights...”

**Requirement**  
A follow relationship MUST NOT be interpreted as granting messaging rights.

**Classification**  
Communication authority; follow limitation.

**Notes**  
Messaging permission or eligibility must be established separately.

---

## REM-05-147 — Follow does not imply endorsement

**Source**  
Section 15: “A follow does not automatically grant... endorsement...”

**Requirement**  
A follow relationship MUST NOT be represented as an endorsement by the source of the target.

**Classification**  
Semantic limitation; endorsement distinction.

**Notes**  
An endorsement requires a distinct relationship type or assertion.

---

## REM-05-148 — Follow does not imply friendship

**Source**  
Section 15: “A follow does not automatically grant... friendship...”

**Requirement**  
A follow relationship MUST NOT be represented as friendship.

**Classification**  
Semantic limitation; relationship-type distinction.

**Notes**  
Friendship may require reciprocal authorisation or other schema-specific conditions.

---

## REM-05-149 — Follow does not convey authority

**Source**  
Section 15: “A follow does not automatically grant... authority...”

**Requirement**  
A follow relationship MUST NOT be interpreted as conveying authority over the target, the target’s repository or the target’s records.

**Classification**  
Authority limitation; follow semantics.

**Notes**  
Authority-bearing relationships require stricter validation and a relationship type that explicitly conveys authority.

---

## REM-05-150 — Follow does not require reciprocity

**Source**  
Section 15: “A follow does not automatically grant... reciprocal following.”

**Requirement**  
A follow by one identity MUST NOT be interpreted as a reciprocal follow by the target.

**Classification**  
Reciprocity limitation; unilateral relationship.

**Notes**  
A reciprocal follow exists only where the target independently creates or authorises its own follow declaration.

---

## REM-05-151 — Follow records as feed input

**Source**  
Section 15: “Applications may use follow records as one input when constructing feeds.”

**Requirement**  
Applications MAY use follow records as one input when constructing feeds.

**Classification**  
Application behaviour; feed construction; permission.

**Notes**  
Applications remain free to combine follow records with other authorised signals and must not imply that the protocol defines one mandatory feed algorithm.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 11–15 of `design-notes/05-relationship-model.md`.
- Section 16 and later material was excluded.
- Examples were used to clarify lifecycle and relationship semantics but were not promoted into universal closed taxonomies.

## Numbering verification

- First requirement: `REM-05-097`.
- Final requirement: `REM-05-151`.
- Requirement numbering continues directly from Part 2.
- Identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit sentence, listed state, lifecycle definition, portability condition or necessary decomposition of a compound source statement.
- Relationship statuses and lifecycle stages were extracted individually because they represent independently testable semantics.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or schema options.
- Descriptive definitions were converted into normative language only where necessary to make the model testable.

## Editorial verification

- Relationship state remains schema-governed rather than globally fixed.
- Each participant retains independent control of its own declaration and history.
- Application replacement and provider migration do not recreate or semantically alter relationships.
- Stable Relay Identifiers and Record URIs remain the basis of portability.
- Follow relationships remain unilateral and do not imply restricted access, messaging rights, endorsement, friendship, authority or reciprocity.
