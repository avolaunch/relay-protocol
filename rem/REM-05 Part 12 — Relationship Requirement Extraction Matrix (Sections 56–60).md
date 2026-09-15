# REM-05 Part 12 — Relationship Requirement Extraction Matrix (Sections 56–60)

## Document status

**Canonical editorial extraction — remediated following REM-05R-01**

This document extracts protocol requirements and explicitly identified non-normative editorial items from Sections 56–60 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source. Open questions and model-boundary statements are retained for traceability but are explicitly non-normative. Section 59 items retain their provisional v0.1 status.

---

## Extraction scope

This part covers:

56. Relationship invariants
57. Compliance scenario
58. Open design questions
59. Provisional decisions for v0.1
60. Core relationship principle

Requirement identifiers continue sequentially from Part 11, beginning with `REM-05-601`.

---

# 56. Relationship invariants

Section 56 states that the following rules “must always remain true.” Each invariant is therefore extracted as a mandatory protocol requirement.

## REM-05-601 — Relationship declarations belong to their authorising identities

**Source**  
Section 56, Invariant 1: “A relationship declaration belongs to the identity that authorised it.”

**Requirement**  
A relationship declaration MUST remain under the canonical authority of the identity that authorised that declaration.

**Classification**  
Invariant; ownership; relationship authority.

**Notes**  
Participation by another identity, application, provider or index does not transfer ownership of the declaration.

---

## REM-05-602 — Application changes must not change source Relay Identifiers

**Source**  
Section 56, Invariant 2: “Changing applications does not change the source or target Relay Identifier.”

**Requirement**  
Changing applications MUST NOT change the source Relay Identifier referenced by an existing relationship.

**Classification**  
Invariant; application portability; identity continuity.

---

## REM-05-603 — Application changes must not change target Relay Identifiers

**Source**  
Section 56, Invariant 2: “Changing applications does not change the source or target Relay Identifier.”

**Requirement**  
Changing applications MUST NOT change the target Relay Identifier referenced by an existing relationship.

**Classification**  
Invariant; application portability; identity continuity.

---

## REM-05-604 — Provider changes must not require relationship recreation

**Source**  
Section 56, Invariant 3: “Changing Relay Provider does not require recreating the relationship.”

**Requirement**  
Changing Relay Provider MUST NOT require an existing relationship to be recreated solely because of the provider change.

**Classification**  
Invariant; provider portability; relationship continuity.

---

## REM-05-605 — Unilateral relationships must not be presented as mutual consent

**Source**  
Section 56, Invariant 4: “A unilateral relationship must not be presented as mutual consent.”

**Requirement**  
A unilateral relationship MUST NOT be represented, displayed or interpreted as evidence of mutual consent.

**Classification**  
Invariant; consent; unilateral relationship.

---

## REM-05-606 — Reciprocal relationships require independent authority from each participant

**Source**  
Section 56, Invariant 5: “A reciprocal relationship requires independent authority from each participating identity.”

**Requirement**  
A reciprocal relationship MUST require independently authorised participation from each identity whose declaration is necessary to establish reciprocity.

**Classification**  
Invariant; reciprocity; independent authority.

---

## REM-05-607 — Identities must not rewrite another identity’s relationship record

**Source**  
Section 56, Invariant 6: “One identity cannot rewrite another identity’s relationship record.”

**Requirement**  
One identity MUST NOT be permitted to rewrite a relationship record canonically controlled by another identity.

**Classification**  
Invariant; record authority; integrity.

---

## REM-05-608 — Relationship labels must not imply undeclared technical authority

**Source**  
Section 56, Invariant 7: “A relationship label does not imply technical authority unless authority is explicitly defined.”

**Requirement**  
A relationship label MUST NOT be interpreted as granting technical authority unless that authority is explicitly defined by the applicable authority-bearing relationship or Permission Grant.

**Classification**  
Invariant; permissions; explicit authority.

---

## REM-05-609 — Graph indexing must not make private relationships public

**Source**  
Section 56, Invariant 8: “Private relationships must not become public merely because an application indexes the graph.”

**Requirement**  
Indexing or graph processing by an application MUST NOT cause a private relationship to become publicly discoverable solely because the relationship was indexed.

**Classification**  
Invariant; privacy; indexing.

---

## REM-05-610 — Derived follower counts are not the canonical relationship graph

**Source**  
Section 56, Invariant 9: “A derived follower count is not the canonical relationship graph.”

**Requirement**  
A derived follower count MUST NOT be treated as the canonical relationship graph or as a substitute for the underlying canonical relationship records.

**Classification**  
Invariant; derived data; graph authority.

---

## REM-05-611 — Applications do not own relationships they introduced

**Source**  
Section 56, Invariant 10: “An application does not own a relationship merely because it introduced the participants.”

**Requirement**  
An application MUST NOT acquire ownership or canonical authority over a relationship merely because the relationship was initiated, discovered or introduced through that application.

**Classification**  
Invariant; application independence; ownership.

---

## REM-05-612 — Released handles must not redirect historical relationships

**Source**  
Section 56, Invariant 11: “A released handle must not redirect historical relationships to a new identity.”

**Requirement**  
Reassignment or reuse of a released handle MUST NOT redirect historical relationship references from the original identity to a new identity.

**Classification**  
Invariant; identity continuity; handle reuse.

**Notes**  
Historical relationships must remain bound to persistent identity, not mutable human-readable handles.

---

## REM-05-613 — Self-declared relationships must not be represented as externally verified

**Source**  
Section 56, Invariant 12: “A self-declared relationship must not be represented as externally verified.”

**Requirement**  
A self-declared relationship MUST NOT be represented as externally verified unless independent verification satisfying the applicable verification model has actually occurred.

**Classification**  
Invariant; verification; evidentiary status.

---

## REM-05-614 — Relationship termination must not falsify historical existence

**Source**  
Section 56, Invariant 13: “Ending a relationship does not permit falsification of its historical existence.”

**Requirement**  
Ending a relationship MUST NOT permit its historical existence to be falsely represented as never having occurred where the protocol retains historical evidence of that relationship.

**Classification**  
Invariant; history; termination; integrity.

---

## REM-05-615 — Blocks are not protocol-level deletion or identity suspension

**Source**  
Section 56, Invariant 14: “Blocks and mutes are not protocol-level deletion or identity suspension.”

**Requirement**  
A block MUST NOT be interpreted as protocol-level deletion or suspension of the blocked identity.

**Classification**  
Invariant; block; identity status.

---

## REM-05-616 — Mutes are not protocol-level deletion or identity suspension

**Source**  
Section 56, Invariant 14: “Blocks and mutes are not protocol-level deletion or identity suspension.”

**Requirement**  
A mute MUST NOT be interpreted as protocol-level deletion or suspension of the muted identity.

**Classification**  
Invariant; mute; identity status.

---

# 57. Compliance scenario

Section 57 defines a basic relationship implementation test with overall `SHOULD` strength. Scenario-specific entries therefore remain `SHOULD`; mandatory principles are supplied independently by the invariant and substantive sections of the model.

## REM-05-617 — Basic implementations should pass the relationship compliance scenario

**Source**  
Section 57: “A basic relationship implementation should pass the following test.”

**Requirement**  
A basic Relay Relationship implementation SHOULD demonstrate the application replacement, provider migration, reciprocal collaboration, termination and private-block behaviours described by the Section 57 compliance scenario.

**Classification**  
Compliance; reference scenario; interoperability.

---

## REM-05-618 — A follow created by an application is stored in the follower’s repository

**Source**  
Section 57, Initial follow: “Application A creates a follow record in Alice’s repository.”

**Requirement**  
In the basic compliance scenario, a follow created on behalf of a source identity SHOULD be stored as that source identity’s relationship record rather than as an application-owned record.

**Classification**  
Compliance; follow; repository ownership.

---

## REM-05-619 — Follow records identify their targets by Relay Identifier

**Source**  
Section 57, Initial follow: “Bob’s Relay Identifier is the target.”

**Requirement**  
In the basic compliance scenario, the follow record SHOULD identify the followed identity using its stable Relay Identifier.

**Classification**  
Compliance; follow; target identity.

---

## REM-05-620 — Replacement applications receive permission before reading follow records

**Source**  
Section 57, Application replacement: “Application B receives permission to read Alice’s follow records.”

**Requirement**  
A replacement application SHOULD obtain appropriate permission before reading the user’s existing follow records.

**Classification**  
Compliance; application replacement; permissions.

---

## REM-05-621 — Existing follows should appear without being recreated after application replacement

**Source**  
Section 57, Application replacement: “Bob appears in Alice’s following list without Alice following him again.”

**Requirement**  
A compatible replacement application SHOULD be able to present an existing supported follow relationship without requiring the user to recreate that follow.

**Classification**  
Compliance; application portability; relationship continuity.

---

## REM-05-622 — Provider migration preserves the follow Record URI

**Source**  
Section 57, Provider migration: “The follow Record URI and Bob’s target identifier remain unchanged.”

**Requirement**  
In the basic provider-migration compliance scenario, the existing follow Record URI SHOULD remain unchanged after the source identity moves providers.

**Classification**  
Compliance; provider migration; record continuity.

---

## REM-05-623 — Provider migration preserves the target identifier

**Source**  
Section 57, Provider migration: “The follow Record URI and Bob’s target identifier remain unchanged.”

**Requirement**  
In the basic provider-migration compliance scenario, the target Relay Identifier of an existing relationship SHOULD remain unchanged after the source identity moves providers.

**Classification**  
Compliance; provider migration; identity continuity.

---

## REM-05-624 — Applications should resolve the migrated repository

**Source**  
Section 57, Provider migration: “Application B resolves Alice’s new repository and continues displaying the relationship.”

**Requirement**  
A compatible application SHOULD resolve the identity’s new repository location following provider migration and continue using the existing relationship record.

**Classification**  
Compliance; provider migration; resolution.

---

## REM-05-625 — Reciprocal collaboration proposals may cross applications

**Source**  
Section 57, Reciprocal collaboration: “Alice proposes a collaboration with Bob. Bob accepts through a different application.”

**Requirement**  
A reciprocal relationship workflow SHOULD permit a relationship proposal created through one compatible application to be accepted through another compatible application.

**Classification**  
Compliance; reciprocity; cross-application interoperability.

---

## REM-05-626 — Reciprocal collaborators create independently authorised linked records

**Source**  
Section 57, Reciprocal collaboration: “Alice and Bob each create independently authorised linked records.”

**Requirement**  
The basic reciprocal-collaboration scenario SHOULD result in independently authorised relationship records for each participant, linked according to the reciprocal relationship schema.

**Classification**  
Compliance; reciprocity; independent authority.

---

## REM-05-627 — Applications should not own cross-application collaborations

**Source**  
Section 57, Reciprocal collaboration: “Neither application owns the collaboration.”

**Requirement**  
In the basic compliance scenario, neither participating application SHOULD acquire canonical ownership of the collaboration merely by facilitating proposal or acceptance.

**Classification**  
Compliance; application independence; ownership; recommendation.

**Notes**  
The corresponding mandatory principle is independently established by Section 56, Invariant 10.

---

## REM-05-628 — A participant should be able to end its own side of a collaboration

**Source**  
Section 57, Relationship termination: “Bob ends his side of the collaboration.”

**Requirement**  
In the basic compliance scenario, a participant SHOULD be able to end its own authorised side of the collaboration in accordance with the relationship schema.

**Classification**  
Compliance; termination; participant authority; recommendation.

---

## REM-05-629 — Ending one required side should make the mutual relationship inactive

**Source**  
Section 57, Relationship termination: “The mutual relationship becomes inactive.”

**Requirement**  
In the basic compliance scenario, where mutual activation requires both participants’ active declarations, termination of one required declaration SHOULD cause the mutual relationship to cease being represented as active.

**Classification**  
Compliance; reciprocal lifecycle; activation state; recommendation.

---

## REM-05-630 — One participant should not falsify another participant’s ended record

**Source**  
Section 57, Relationship termination: “Alice cannot rewrite Bob’s record to make it appear active.”

**Requirement**  
In the basic compliance scenario, a participant SHOULD NOT be able to rewrite another participant’s terminated relationship record to falsely represent that declaration as active.

**Classification**  
Compliance; record authority; integrity; recommendation.

**Notes**  
The corresponding mandatory principle is independently established by Section 56, Invariant 6.

---

## REM-05-631 — Private blocks should affect authorised applications

**Source**  
Section 57, Private block: “The block affects authorised applications.”

**Requirement**  
In the basic compliance scenario, a private block SHOULD be enforceable by applications authorised to access and apply the blocking identity’s block state.

**Classification**  
Compliance; block; authorised application behaviour.

---

## REM-05-632 — Private blocks should not be exposed publicly in the compliance scenario

**Source**  
Section 57, Private block: “The block … is not exposed publicly or to the blocked identity.”

**Requirement**  
In the basic compliance scenario, a private block SHOULD NOT be exposed publicly merely as a consequence of its protocol representation or enforcement.

**Classification**  
Compliance; block; privacy; recommendation.

---

## REM-05-633 — Private blocks should not be exposed to the blocked identity in the compliance scenario

**Source**  
Section 57, Private block: “The block … is not exposed publicly or to the blocked identity.”

**Requirement**  
In the basic compliance scenario, a private block SHOULD NOT disclose the private block record to the blocked identity merely as a consequence of enforcement.

**Classification**  
Compliance; block; privacy; recommendation.

---

## REM-05-634 — Basic compliance requires relationships not to be bound to one application

**Source**  
Section 57: “If these actions occur without binding the relationships to one application or provider, the implementation satisfies the basic Relay Relationship objective.”

**Requirement**  
A basic compliant implementation SHOULD demonstrate that the tested relationships are not bound to a single application.

**Classification**  
Compliance; application portability; core objective.

---

## REM-05-635 — Basic compliance requires relationships not to be bound to one provider

**Source**  
Section 57: “If these actions occur without binding the relationships to one application or provider, the implementation satisfies the basic Relay Relationship objective.”

**Requirement**  
A basic compliant implementation SHOULD demonstrate that the tested relationships are not bound to a single Relay Provider.

**Classification**  
Compliance; provider portability; core objective.

---

# 58. Open design questions

Section 58 deliberately records unresolved questions. The entries below are retained for traceability as **non-normative Open Design Issues**. They are not settled protocol requirements and MUST NOT be carried into a Requirements Catalogue as normative requirements unless resolved by an authoritative design decision.

## REM-05-636 — Public reverse indexing design question

**Source**  
Section 58.1: “How should public reverse relationships be indexed efficiently without creating one indispensable global graph owner?”

**Requirement**  
**Non-normative Open Design Issue:** determine how public reverse relationships can be indexed efficiently without creating one indispensable global graph owner.

**Classification**  
Non-normative; open design issue; indexing; decentralisation.

**Notes**  
No final indexing architecture is selected by the Relationship Model.

---

## REM-05-637 — Reciprocal activation mechanism design question

**Source**  
Section 58.2: “Should reciprocal relationships become active through linked records, a shared transaction or an external coordination service?”

**Requirement**  
**Non-normative Open Design Issue:** determine the activation mechanism for reciprocal relationships.

**Classification**  
Non-normative; open design issue; reciprocity; activation.

**Notes**  
Linked records, a shared transaction and an external coordination service remain candidate approaches rather than settled requirements.

---

## REM-05-638 — Private graph portability and secrecy design question

**Source**  
Section 58.3: “How should private relationship records remain portable while preventing providers and indexers from learning the graph?”

**Requirement**  
**Non-normative Open Design Issue:** determine how private relationship records can remain portable while preventing unauthorised providers and indexers from learning protected graph information.

**Classification**  
Non-normative; open design issue; privacy; encryption; portability.

---

## REM-05-639 — Dynamic audience evaluation and revocation design question

**Source**  
Section 58.4: “How should relationship-based access be evaluated efficiently and revoked promptly?”

**Requirement**  
**Non-normative Open Design Issue:** determine how relationship-based access can be evaluated efficiently and revoked promptly.

**Classification**  
Non-normative; open design issue; access control; dynamic audiences.

---

## REM-05-640 — Relationship request transport design question

**Source**  
Section 58.5: “Should requests be repository records, direct protocol messages or both?”

**Requirement**  
**Non-normative Open Design Issue:** determine whether relationship requests should be repository records, direct protocol messages, both, or another defined mechanism.

**Classification**  
Non-normative; open design issue; requests; protocol messaging.

---

## REM-05-641 — Authority-model boundary design question

**Source**  
Section 58.6: “Which authority-bearing relationships belong in the Relationship Model, and which should instead use Permission Grants or credentials?”

**Requirement**  
**Non-normative Open Design Issue:** determine the boundary between authority represented by relationship schemas and authority represented through Permission Grants or credentials.

**Classification**  
Non-normative; open design issue; authority; model boundaries.

---

## REM-05-642 — Identity recovery and trusted relationships design question

**Source**  
Section 58.7: “What happens to trusted-contact and guardian relationships when an identity recovery occurs?”

**Requirement**  
**Non-normative Open Design Issue:** determine the lifecycle and authority effects of identity recovery on trusted-contact and guardian relationships.

**Classification**  
Non-normative; open design issue; identity recovery; authority relationships.

---

## REM-05-643 — Historical mutuality representation design question

**Source**  
Section 58.8: “How should applications represent a relationship that was once reciprocal but is now active on only one side?”

**Requirement**  
**Non-normative Open Design Issue:** determine how applications should represent a relationship that was historically reciprocal but is currently active on only one side.

**Classification**  
Non-normative; open design issue; history; reciprocity; lifecycle.

---

## REM-05-644 — External identity matching evidence design question

**Source**  
Section 58.9: “What evidence is sufficient to connect an imported external account with a Relay Identity?”

**Requirement**  
**Non-normative Open Design Issue:** determine the evidence or verification threshold sufficient to connect an imported external account to a Relay Identity.

**Classification**  
Non-normative; open design issue; external identity; verification.

---

## REM-05-645 — Conflicting relationship schema design question

**Source**  
Section 58.10: “How should applications handle two schemas that use similar labels but define materially different relationship meanings?”

**Requirement**  
**Non-normative Open Design Issue:** determine interoperability guidance for relationship schemas that use similar labels but define materially different semantics.

**Classification**  
Non-normative; open design issue; schema conflict; interoperability.

**Notes**  
No semantic-equivalence rule is established by this open question.

---

# 59. Provisional decisions for v0.1

Section 59 states that Relay v0.1 “will provisionally assume” the following decisions. Every entry below is therefore explicitly a **PROVISIONAL v0.1 requirement or decision**. These entries describe the current working baseline but MUST NOT be treated as final, immutable protocol commitments without later confirmation.

## REM-05-646 — v0.1 provisionally represents relationships as Relay Records

**Source**  
Section 59: “relationships are Relay Records.”

**Requirement**  
**PROVISIONAL v0.1:** relationships are to be represented as Relay Records under the current v0.1 working assumption.

**Classification**  
Provisional v0.1 decision; record model; relationship representation.

---

## REM-05-647 — Declaring identities provisionally store their own canonical relationship records

**Source**  
Section 59: “the declaring identity stores its own canonical relationship record.”

**Requirement**  
**PROVISIONAL v0.1:** the declaring identity’s repository is to store that identity’s canonical relationship declaration under the current working assumption.

**Classification**  
Provisional v0.1 decision; canonical authority; repository ownership.

---

## REM-05-648 — v0.1 provisionally distinguishes unilateral and reciprocal relationships

**Source**  
Section 59: “unilateral and reciprocal relationships are distinct.”

**Requirement**  
**PROVISIONAL v0.1:** unilateral and reciprocal relationships are distinct under the current v0.1 working assumption.

**Classification**  
Provisional v0.1 decision; relationship type; reciprocity.

---

## REM-05-649 — v0.1 provisionally uses independently authorised linked records for reciprocal relationships

**Source**  
Section 59: “reciprocal relationships use independently authorised linked records.”

**Requirement**  
**PROVISIONAL v0.1:** reciprocal relationships use independently authorised linked relationship records under the current working assumption.

**Classification**  
Provisional v0.1 decision; reciprocity; linked records.

---

## REM-05-650 — v0.1 provisionally uses stable Relay Identifiers as relationship sources

**Source**  
Section 59: “stable Relay Identifiers are used as source and target.”

**Requirement**  
**PROVISIONAL v0.1:** stable Relay Identifiers are used to identify relationship sources under the current working assumption.

**Classification**  
Provisional v0.1 decision; identity; source reference.

---

## REM-05-651 — v0.1 provisionally uses stable Relay Identifiers as relationship targets

**Source**  
Section 59: “stable Relay Identifiers are used as source and target.”

**Requirement**  
**PROVISIONAL v0.1:** stable Relay Identifiers are used to identify Relay relationship targets under the current working assumption, subject to the model’s explicit allowance for external references.

**Classification**  
Provisional v0.1 decision; identity; target reference.

---

## REM-05-652 — Follows provisionally survive application changes

**Source**  
Section 59: “follows and subscriptions survive application and provider changes.”

**Requirement**  
**PROVISIONAL v0.1:** follow relationships survive compatible application changes under the current working assumption.

**Classification**  
Provisional v0.1 decision; follow; application portability.

---

## REM-05-653 — Follows provisionally survive provider changes

**Source**  
Section 59: “follows and subscriptions survive application and provider changes.”

**Requirement**  
**PROVISIONAL v0.1:** follow relationships survive Relay Provider changes under the current working assumption.

**Classification**  
Provisional v0.1 decision; follow; provider portability.

---

## REM-05-654 — Subscriptions provisionally survive application changes

**Source**  
Section 59: “follows and subscriptions survive application and provider changes.”

**Requirement**  
**PROVISIONAL v0.1:** subscription relationships survive compatible application changes under the current working assumption.

**Classification**  
Provisional v0.1 decision; subscription; application portability.

---

## REM-05-655 — Subscriptions provisionally survive provider changes

**Source**  
Section 59: “follows and subscriptions survive application and provider changes.”

**Requirement**  
**PROVISIONAL v0.1:** subscription relationships survive Relay Provider changes under the current working assumption.

**Classification**  
Provisional v0.1 decision; subscription; provider portability.

---

## REM-05-656 — Public reverse graph queries provisionally use optional indexes

**Source**  
Section 59: “public reverse graph queries are provided by optional indexes.”

**Requirement**  
**PROVISIONAL v0.1:** public reverse graph querying is provided by optional indexes rather than by a mandatory global reverse-query capability of every repository under the current working assumption.

**Classification**  
Provisional v0.1 decision; indexing; reverse relationships.

---

## REM-05-657 — Public is a provisional v0.1 relationship visibility classification

**Source**  
Section 59: “visibility may be public, unlisted, restricted or private.”

**Requirement**  
**PROVISIONAL v0.1:** `public` is an available relationship visibility classification under the current working assumption.

**Classification**  
Provisional v0.1 decision; visibility; privacy.

---

## REM-05-658 — Unlisted is a provisional v0.1 relationship visibility classification

**Source**  
Section 59: “visibility may be public, unlisted, restricted or private.”

**Requirement**  
**PROVISIONAL v0.1:** `unlisted` is an available relationship visibility classification under the current working assumption.

**Classification**  
Provisional v0.1 decision; visibility; privacy.

---

## REM-05-659 — Restricted is a provisional v0.1 relationship visibility classification

**Source**  
Section 59: “visibility may be public, unlisted, restricted or private.”

**Requirement**  
**PROVISIONAL v0.1:** `restricted` is an available relationship visibility classification under the current working assumption.

**Classification**  
Provisional v0.1 decision; visibility; access control.

---

## REM-05-660 — Private is a provisional v0.1 relationship visibility classification

**Source**  
Section 59: “visibility may be public, unlisted, restricted or private.”

**Requirement**  
**PROVISIONAL v0.1:** `private` is an available relationship visibility classification under the current working assumption.

**Classification**  
Provisional v0.1 decision; visibility; privacy.

---

## REM-05-661 — Private relationships provisionally require explicit access controls

**Source**  
Section 59: “private relationships require explicit access controls.”

**Requirement**  
**PROVISIONAL v0.1:** private relationships require explicit access controls under the current working assumption.

**Classification**  
Provisional v0.1 decision; privacy; access control.

---

## REM-05-662 — Authority-bearing relationships provisionally define exact capabilities

**Source**  
Section 59: “authority-bearing relationships must define exact capabilities.”

**Requirement**  
**PROVISIONAL v0.1:** authority-bearing relationships define exact technical capabilities under the current working assumption.

**Classification**  
Provisional v0.1 decision; authority; capabilities.

---

## REM-05-663 — Self-declared relationships remain provisionally distinguishable

**Source**  
Section 59: “self-declared, reciprocally confirmed and externally verified relationships are distinguishable.”

**Requirement**  
**PROVISIONAL v0.1:** self-declared relationships remain distinguishable as an evidentiary state under the current working assumption.

**Classification**  
Provisional v0.1 decision; evidence; verification status.

---

## REM-05-664 — Reciprocally confirmed relationships remain provisionally distinguishable

**Source**  
Section 59: “self-declared, reciprocally confirmed and externally verified relationships are distinguishable.”

**Requirement**  
**PROVISIONAL v0.1:** reciprocally confirmed relationships remain distinguishable as an evidentiary state under the current working assumption.

**Classification**  
Provisional v0.1 decision; evidence; reciprocal confirmation.

---

## REM-05-665 — Externally verified relationships remain provisionally distinguishable

**Source**  
Section 59: “self-declared, reciprocally confirmed and externally verified relationships are distinguishable.”

**Requirement**  
**PROVISIONAL v0.1:** externally verified relationships remain distinguishable as an evidentiary state under the current working assumption.

**Classification**  
Provisional v0.1 decision; evidence; external verification.

---

## REM-05-666 — Follower counts are provisionally treated as derived values

**Source**  
Section 59: “follower counts and reputation are derived values.”

**Requirement**  
**PROVISIONAL v0.1:** follower counts are treated as derived values rather than canonical relationship declarations under the current working assumption.

**Classification**  
Provisional v0.1 decision; derived data; follower count.

---

## REM-05-667 — Reputation is provisionally treated as a derived value

**Source**  
Section 59: “follower counts and reputation are derived values.”

**Requirement**  
**PROVISIONAL v0.1:** reputation results are treated as derived values rather than canonical relationship declarations under the current working assumption.

**Classification**  
Provisional v0.1 decision; derived data; reputation.

---

## REM-05-668 — Blocks are provisionally normally private

**Source**  
Section 59: “blocks and mutes are normally private.”

**Requirement**  
**PROVISIONAL v0.1:** blocks are normally private under the current working assumption.

**Classification**  
Provisional v0.1 decision; block; privacy.

---

## REM-05-669 — Mutes are provisionally normally private

**Source**  
Section 59: “blocks and mutes are normally private.”

**Requirement**  
**PROVISIONAL v0.1:** mutes are normally private under the current working assumption.

**Classification**  
Provisional v0.1 decision; mute; privacy.

---

## REM-05-670 — Unknown relationship schemas provisionally survive migration

**Source**  
Section 59: “unknown relationship schemas must survive migration.”

**Requirement**  
**PROVISIONAL v0.1:** unknown relationship schemas survive migration under the current working assumption.

**Classification**  
Provisional v0.1 decision; migration; forward compatibility.

---

## REM-05-671 — Advanced end-to-end encrypted graph privacy may provisionally be deferred

**Source**  
Section 59: “advanced end-to-end encrypted graph privacy may be deferred beyond the first reference implementation.”

**Requirement**  
**PROVISIONAL v0.1:** advanced end-to-end encrypted graph-privacy mechanisms MAY be deferred beyond the first reference implementation.

**Classification**  
Provisional v0.1 decision; encryption; implementation scope.

**Notes**  
Deferral does not remove the explicit privacy, visibility and access-control requirements applicable to relationship data that the implementation supports.

---

# 60. Core relationship principle

## REM-05-672 — Relationships exist between persistent identities rather than applications

**Source**  
Section 60: “A relationship exists between persistent identities, not inside the application that happened to introduce them.”

**Requirement**  
The Relay Relationship Model MUST treat a relationship as existing between persistent identities rather than as an object owned by or inherently contained within the application that introduced or facilitated the relationship.

**Classification**  
Core principle; identity persistence; application independence.

**Notes**  
This principle summarises the portability objective underlying the Relationship Model: applications may create, display and act upon authorised relationship records, but the relationship remains anchored to persistent identities and their canonical records.

---

## REM-05-673 — Migration and Portability Model hand-off

**Source**  
Section 60: “The next core object is the Relay Migration and Portability Model: how identities, repositories, records, blobs, grants and relationships move between providers without breaking continuity.”

**Requirement**  
**Non-normative model-boundary note:** Section 60 identifies the Relay Migration and Portability Model as the next core object and describes continuity across provider movement as its subject matter.

**Classification**  
Non-normative; model boundary; migration; portability.

**Notes**  
This statement is retained only for traceability. It is not a normative Relationship Model requirement and MUST NOT be carried into the Relationship Requirements Catalogue as such. Requirements for the Migration and Portability Model must be extracted from that model’s own authoritative source.

---

## Editorial QA

The remediated extraction for Sections 56–60 has been reviewed for numbering, traceability, normative strength and status semantics.

- Requirement identifiers remain continuous from `REM-05-601` through `REM-05-673` with no gaps or duplicates.
- Section 56 invariants remain mandatory because the source explicitly states that they “must always remain true.”
- Section 57 scenario entries preserve the overall `SHOULD` strength of the compliance test; independently mandatory principles remain represented elsewhere in the model.
- Section 58 entries are explicitly non-normative Open Design Issues and are excluded from settled catalogue requirements unless later resolved authoritatively.
- Section 59 entries are explicitly marked `PROVISIONAL v0.1` in both requirement wording and classification; they must not silently become ordinary final requirements downstream.
- REM-05-673 is retained only as a non-normative model-boundary note and is excluded from the Relationship Requirements Catalogue.
- All numbered entries remain traceable to Sections 56–60.
- No source section was removed and no unresolved design question was answered by the remediation.
