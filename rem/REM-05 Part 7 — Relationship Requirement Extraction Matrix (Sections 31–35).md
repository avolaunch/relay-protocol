# REM-05 Part 7 — Relationship Requirement Extraction Matrix (Sections 31–35)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 31–35 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

31. Relationship termination
32. Relationship revocation
33. Relationship disputes
34. Blocks
35. Mutes

Requirement identifiers continue sequentially from Part 6, beginning with `REM-05-343`.

---

# 31. Relationship termination

## REM-05-343 — Source-controlled termination

**Source**  
Section 31: “A source identity may end its own relationship declaration.”

**Requirement**  
A source identity MUST be able to terminate a relationship declaration that it controls.

**Classification**  
Relationship lifecycle; source authority; termination.

**Notes**  
Termination authority applies to the source identity’s own declaration and does not confer authority to rewrite or delete another identity’s records.

---

## REM-05-344 — Unilateral termination effect

**Source**  
Section 31: “For unilateral relationships, termination normally ends the relationship immediately.”

**Requirement**  
For a unilateral relationship, termination by the source SHOULD make that relationship inactive immediately unless the governing schema specifies a different valid transition.

**Classification**  
Unilateral relationship; lifecycle transition; termination semantics.

**Notes**  
Examples include follows, subscriptions, blocks, mutes and other declarations requiring only source authorisation.

---

## REM-05-345 — Reciprocal withdrawal changes mutual state

**Source**  
Section 31: “For reciprocal relationships, one party’s withdrawal should cause the mutual state to become inactive.”

**Requirement**  
When one participant withdraws from a reciprocal relationship, the shared or derived mutual state SHOULD become inactive.

**Classification**  
Reciprocal relationship; withdrawal; derived state.

**Notes**  
The withdrawal ends the operational mutual state without granting either party control over the other party’s historical declaration.

---

## REM-05-346 — Historical records may be retained

**Source**  
Section 31: “The other party may retain a historical record such as: ‘Previously collaborated with Alice.’”

**Requirement**  
A participant MAY retain a historical record of a terminated relationship where the governing schema permits historical retention.

**Classification**  
Historical continuity; relationship history; retention.

**Notes**  
The retained record represents the participant’s own historical record and does not revive the ended relationship.

---

## REM-05-347 — Historical retention must obey schema rules

**Source**  
Section 31: “provided the schema and visibility rules allow it.”

**Requirement**  
Historical relationship retention MUST comply with the applicable relationship schema.

**Classification**  
Schema compliance; historical records; retention controls.

**Notes**  
A relationship type may prohibit, limit or define the form of retained historical information.

---

## REM-05-348 — Historical retention must obey visibility rules

**Source**  
Section 31: “provided the schema and visibility rules allow it.”

**Requirement**  
Historical relationship retention and disclosure MUST comply with the applicable visibility rules.

**Classification**  
Privacy; visibility; historical relationship data.

**Notes**  
The fact that a historical record may be retained does not imply that it may be made public.

---

## REM-05-349 — Termination cannot falsify another party’s history

**Source**  
Section 31: “Termination must not allow one party to falsify the other’s historical record.”

**Requirement**  
Termination MUST NOT allow one party to alter, erase, misrepresent or otherwise falsify another party’s historical relationship record.

**Classification**  
Historical integrity; independent authority; anti-tampering.

**Notes**  
Each party remains authoritative over its own declaration and history.

---

# 32. Relationship revocation

## REM-05-350 — Revocation support for authority-bearing relationships

**Source**  
Section 32: “Revocation is particularly important for authority-bearing relationships.”

**Requirement**  
Relay implementations MUST support revocation for authority-bearing relationships.

**Classification**  
Authority governance; revocation; security.

**Notes**  
Authority-bearing relationships include relationships such as administrator, legal representative, guardian, delegated publisher or repository custodian.

---

## REM-05-351 — Revocation must identify the relationship record

**Source**  
Section 32: “Revocation should identify: relationship record.”

**Requirement**  
A relationship revocation SHOULD identify the specific relationship record being revoked.

**Classification**  
Revocation record; traceability; target identification.

**Notes**  
The identifier should be stable and sufficient to distinguish the affected declaration from similar or historical relationships.

---

## REM-05-352 — Revocation must identify the revoking authority

**Source**  
Section 32: “Revocation should identify: revoking authority.”

**Requirement**  
A relationship revocation SHOULD identify the authority that issued or authorised the revocation.

**Classification**  
Revocation provenance; authority attribution; auditability.

**Notes**  
The revoking authority must itself be authorised to revoke the affected relationship or capabilities.

---

## REM-05-353 — Revocation must identify effective time

**Source**  
Section 32: “Revocation should identify: effective time.”

**Requirement**  
A relationship revocation SHOULD identify the time from which the revocation becomes effective.

**Classification**  
Temporal validity; revocation; audit trail.

**Notes**  
The effective time is necessary to distinguish actions performed while authority was valid from actions attempted after revocation.

---

## REM-05-354 — Revocation may record a reason

**Source**  
Section 32: “Revocation should identify: reason where appropriate.”

**Requirement**  
A relationship revocation SHOULD record a reason where disclosure of that reason is appropriate.

**Classification**  
Revocation metadata; reason code; auditability.

**Notes**  
The reason may be omitted, restricted or generalised where disclosure would create privacy, safety or legal risk.

---

## REM-05-355 — Revocation must identify affected capabilities

**Source**  
Section 32: “Revocation should identify: affected capabilities.”

**Requirement**  
A revocation of an authority-bearing relationship SHOULD identify the capabilities that cease to be valid.

**Classification**  
Capability control; scope; revocation effects.

**Notes**  
This supports partial revocation and prevents ambiguity where a relationship conveys multiple distinct powers.

---

## REM-05-356 — Revocation must define treatment of existing actions

**Source**  
Section 32: “Revocation should identify: whether existing actions remain valid.”

**Requirement**  
A relationship revocation SHOULD specify whether actions validly completed before the effective revocation time remain valid.

**Classification**  
Revocation semantics; prior acts; legal and operational continuity.

**Notes**  
Revocation should not be assumed to invalidate all historical actions retroactively.

---

## REM-05-357 — New authority-based actions must be rejected

**Source**  
Section 32: “After revocation, new authority-based actions must be rejected.”

**Requirement**  
After an authority-bearing relationship has been revoked, all new actions that depend on the revoked authority MUST be rejected.

**Classification**  
Access control; enforcement; revocation.

**Notes**  
This applies from the revocation’s effective time and includes direct, delegated and automated actions relying on that authority.

---

## REM-05-358 — Historical proof of earlier authority may remain

**Source**  
Section 32: “The system may retain historical proof that the authority existed during an earlier period.”

**Requirement**  
The system MAY retain verifiable historical evidence that an authority-bearing relationship was valid during an earlier period.

**Classification**  
Historical proof; auditability; authority lifecycle.

**Notes**  
Historical proof does not provide current authority and must not be interpreted as an active grant.

---

## REM-05-359 — Historical proof must preserve temporal context

**Source**  
Section 32: “the authority existed during an earlier period.”

**Requirement**  
Retained proof of revoked authority MUST preserve sufficient temporal context to distinguish the earlier valid period from the current revoked state.

**Classification**  
Temporal integrity; historical evidence; revocation status.

**Notes**  
At minimum, this requires interpretable validity and revocation timing.

---

# 33. Relationship disputes

## REM-05-360 — Identities may dispute relationship assertions

**Source**  
Section 33: “An identity may dispute a relationship assertion.”

**Requirement**  
A Relay Identity MUST be able to issue a dispute against a relationship assertion concerning that identity or its controlled interests.

**Classification**  
Dispute mechanism; counterclaim; relationship integrity.

**Notes**  
A dispute is an attributable counterclaim and does not, by itself, erase the original assertion.

---

## REM-05-361 — Disputes must be represented separately

**Source**  
Section 33: “The dispute should be represented separately rather than deleting or altering the original assertion.”

**Requirement**  
A relationship dispute SHOULD be represented as a separate record or separately attributable protocol object.

**Classification**  
Record separation; dispute representation; provenance.

**Notes**  
Separate representation preserves both the original assertion and the counterclaim for independent evaluation.

---

## REM-05-362 — Disputes must not delete the original assertion

**Source**  
Section 33: “rather than deleting ... the original assertion.”

**Requirement**  
Creating a dispute MUST NOT automatically delete the original relationship assertion.

**Classification**  
Historical integrity; dispute handling; non-destructive records.

**Notes**  
Deletion may occur only through a separately authorised process applicable to the original record.

---

## REM-05-363 — Disputes must not alter the original assertion

**Source**  
Section 33: “rather than ... altering the original assertion.”

**Requirement**  
Creating a dispute MUST NOT rewrite or alter the original relationship assertion.

**Classification**  
Record integrity; independent claims; anti-tampering.

**Notes**  
The issuer of the original assertion retains responsibility for that assertion, while the disputing identity controls the dispute record.

---

## REM-05-364 — Applications may display the assertion

**Source**  
Section 33: “Applications may display: assertion.”

**Requirement**  
An application MAY display the disputed relationship assertion when presenting the dispute context.

**Classification**  
User interface; dispute presentation; transparency.

**Notes**  
Display remains subject to visibility, access and safety rules.

---

## REM-05-365 — Applications may display the issuer

**Source**  
Section 33: “Applications may display: issuer.”

**Requirement**  
An application MAY identify the issuer of a disputed relationship assertion.

**Classification**  
Attribution; dispute presentation; provenance.

**Notes**  
Issuer attribution helps users distinguish who made the original claim.

---

## REM-05-366 — Applications may display supporting evidence

**Source**  
Section 33: “Applications may display: evidence.”

**Requirement**  
An application MAY display evidence associated with a disputed relationship assertion where access and disclosure rules permit.

**Classification**  
Evidence presentation; dispute resolution; access control.

**Notes**  
Sensitive evidence may require restricted access or selective disclosure.

---

## REM-05-367 — Applications may display the dispute

**Source**  
Section 33: “Applications may display: dispute.”

**Requirement**  
An application MAY display the attributable dispute alongside the original relationship assertion.

**Classification**  
Counterclaim presentation; transparency; relationship status.

**Notes**  
The dispute should not be presented as though it originated from the original issuer.

---

## REM-05-368 — Applications may display current verification status

**Source**  
Section 33: “Applications may display: current verification status.”

**Requirement**  
An application MAY display the current verification status of a disputed relationship assertion.

**Classification**  
Verification status; dispute presentation; evidentiary state.

**Notes**  
The displayed status should reflect the current evidence and verification process without claiming legal finality unless such authority exists.

---

## REM-05-369 — Relay does not determine legal truth automatically

**Source**  
Section 33: “Relay does not determine legal truth automatically.”

**Requirement**  
The Relay protocol MUST NOT treat the existence of an assertion, dispute or protocol-level verification result as automatic determination of legal truth.

**Classification**  
Protocol boundary; legal neutrality; dispute semantics.

**Notes**  
Legal determinations may require competent external authorities, processes or evidence beyond protocol records.

---

## REM-05-370 — Relay preserves attributable claims

**Source**  
Section 33: “It preserves attributable claims and counterclaims.”

**Requirement**  
Relay MUST preserve attribution for relationship claims involved in a dispute.

**Classification**  
Claim provenance; attribution; dispute record.

**Notes**  
A claim must remain traceable to the identity or authority that made it.

---

## REM-05-371 — Relay preserves attributable counterclaims

**Source**  
Section 33: “It preserves attributable claims and counterclaims.”

**Requirement**  
Relay MUST preserve attribution for relationship counterclaims and disputes.

**Classification**  
Counterclaim provenance; attribution; dispute record.

**Notes**  
The protocol preserves the record of disagreement without automatically deciding which party is legally correct.

---

# 34. Blocks

## REM-05-372 — Block definition

**Source**  
Section 34: “A block is a private or restricted relationship declaration instructing applications and providers to prevent or reduce interaction with a target identity.”

**Requirement**  
A block MUST be represented as a private or restricted relationship declaration by a source identity against a target identity.

**Classification**  
Safety control; relationship type; privacy.

**Notes**  
A block is controlled by the blocking identity and is not a reciprocal relationship requiring target approval.

---

## REM-05-373 — Blocks instruct interaction prevention or reduction

**Source**  
Section 34: “instructing applications and providers to prevent or reduce interaction with a target identity.”

**Requirement**  
Applications and providers processing a valid block MUST apply the block as an instruction to prevent or reduce interaction with the target according to applicable policy and capability.

**Classification**  
Block enforcement; interaction control; safety.

**Notes**  
The exact effects may vary by application, provider and relationship schema.

---

## REM-05-374 — Blocks may affect content visibility

**Source**  
Section 34: “A block may affect: content visibility.”

**Requirement**  
A block MAY restrict or reduce the visibility of content associated with the blocked identity.

**Classification**  
Content visibility; block effect; safety control.

**Notes**  
This does not require deletion of the content from its canonical repository.

---

## REM-05-375 — Blocks may affect replies

**Source**  
Section 34: “A block may affect: replies.”

**Requirement**  
A block MAY prevent, suppress or reduce replies between the blocking identity and the blocked identity.

**Classification**  
Interaction control; replies; block effect.

**Notes**  
Applications should define the direction and extent of reply restrictions.

---

## REM-05-376 — Blocks may affect mentions

**Source**  
Section 34: “A block may affect: mentions.”

**Requirement**  
A block MAY prevent, suppress or reduce mention-related interactions involving the blocked identity.

**Classification**  
Interaction control; mentions; block effect.

**Notes**  
The block may affect notification, delivery, visibility or creation of mentions depending on implementation policy.

---

## REM-05-377 — Blocks may affect follows

**Source**  
Section 34: “A block may affect: follows.”

**Requirement**  
A block MAY prevent the creation, continuation or display of follow relationships involving the blocked identity.

**Classification**  
Relationship control; follows; block effect.

**Notes**  
A provider may need to derive or suppress mutual state without rewriting independently controlled historical records.

---

## REM-05-378 — Blocks may affect messages

**Source**  
Section 34: “A block may affect: messages.”

**Requirement**  
A block MAY prevent or reduce message delivery or initiation involving the blocked identity.

**Classification**  
Messaging safety; interaction control; block effect.

**Notes**  
Message handling remains subject to protocol, provider and legal obligations.

---

## REM-05-379 — Blocks may affect relationship requests

**Source**  
Section 34: “A block may affect: relationship requests.”

**Requirement**  
A block MAY prevent or suppress new relationship requests from the blocked identity.

**Classification**  
Request control; harassment prevention; block effect.

**Notes**  
The blocking identity need not receive or review every suppressed request.

---

## REM-05-380 — Blocks may affect event delivery

**Source**  
Section 34: “A block may affect: event delivery.”

**Requirement**  
A block MAY prevent or filter event delivery involving the blocked identity.

**Classification**  
Event filtering; block enforcement; privacy.

**Notes**  
Event suppression should not be confused with deletion of canonical events or records.

---

## REM-05-381 — Blocks may affect discovery

**Source**  
Section 34: “A block may affect: discovery.”

**Requirement**  
A block MAY reduce or prevent discovery of the blocked identity or its associated activity by the blocking identity.

**Classification**  
Discovery filtering; block effect; safety.

**Notes**  
The precise discovery effect may be local to an application or portable where block processing is shared.

---

## REM-05-382 — Blocks should normally be private

**Source**  
Section 34: “A block should normally be private.”

**Requirement**  
A block relationship SHOULD be private or otherwise restricted from unauthorised disclosure by default.

**Classification**  
Privacy by default; block relationship; sensitive preference.

**Notes**  
Public disclosure of blocks may create safety, retaliation or privacy risks.

---

## REM-05-383 — Block targets need not be informed

**Source**  
Section 34: “The target need not be informed unless required by the application or policy.”

**Requirement**  
A blocked target MUST NOT be assumed to require notification of the block.

**Classification**  
Notification policy; privacy; block handling.

**Notes**  
Notification may still occur where required by an application, provider policy or applicable law.

---

## REM-05-384 — Applications may require block notification

**Source**  
Section 34: “unless required by the application or policy.”

**Requirement**  
An application MAY notify a blocked target where the application’s disclosed and applicable policy requires notification.

**Classification**  
Application policy; notification; block handling.

**Notes**  
Notification should avoid exposing unnecessary private information about the blocker.

---

## REM-05-385 — Policy may require block notification

**Source**  
Section 34: “unless required by the application or policy.”

**Requirement**  
A provider or governing policy MAY require notification of a block where such notification is applicable.

**Classification**  
Provider policy; notification; compliance.

**Notes**  
The requirement should be explicit rather than inferred from the existence of the block.

---

## REM-05-386 — Blocks are not protocol-level deletion

**Source**  
Section 34: “A block is not equivalent to protocol-level deletion.”

**Requirement**  
A block MUST NOT be interpreted as protocol-level deletion of the blocked identity, its records or its relationships.

**Classification**  
Semantic boundary; deletion; block relationship.

**Notes**  
Blocking changes interaction and visibility behaviour; it does not erase canonical state.

---

## REM-05-387 — Blocks are not provider suspension

**Source**  
Section 34: “A block is not equivalent to ... provider suspension.”

**Requirement**  
A block MUST NOT be interpreted as suspension of the blocked identity by a Relay Provider.

**Classification**  
Semantic boundary; provider enforcement; block relationship.

**Notes**  
Provider suspension is a separate administrative or security action with different authority and effects.

---

# 35. Mutes

## REM-05-388 — Mute definition

**Source**  
Section 35: “A mute reduces visibility or notifications without necessarily preventing interaction.”

**Requirement**  
A mute MUST be represented as a preference that reduces visibility or notifications without necessarily preventing interaction.

**Classification**  
Preference control; visibility; notification filtering.

**Notes**  
A mute is less restrictive than a block unless an implementation explicitly defines additional effects.

---

## REM-05-389 — Mutes need not prevent interaction

**Source**  
Section 35: “without necessarily preventing interaction.”

**Requirement**  
A mute MUST NOT automatically be interpreted as preventing all interaction with the muted target.

**Classification**  
Semantic boundary; interaction; mute behaviour.

**Notes**  
Replies, messages or relationship requests may remain possible even when content or notifications are reduced.

---

## REM-05-390 — Mutes may apply to an identity

**Source**  
Section 35: “A mute may apply to: an identity.”

**Requirement**  
A mute MAY target a Relay Identity.

**Classification**  
Mute scope; identity; preference.

**Notes**  
The mute may reduce content visibility or notifications associated with that identity.

---

## REM-05-391 — Mutes may apply to a collection

**Source**  
Section 35: “A mute may apply to: a collection.”

**Requirement**  
A mute MAY target a record collection.

**Classification**  
Mute scope; collection; preference.

**Notes**  
Collection-level muting supports filtering of a class of records without muting the entire identity.

---

## REM-05-392 — Mutes may apply to a topic

**Source**  
Section 35: “A mute may apply to: a topic.”

**Requirement**  
A mute MAY target a topic.

**Classification**  
Mute scope; topic; content filtering.

**Notes**  
Topic matching and vocabulary are application or schema concerns unless standardised elsewhere.

---

## REM-05-393 — Mutes may apply to a record

**Source**  
Section 35: “A mute may apply to: a record.”

**Requirement**  
A mute MAY target a specific Relay Record.

**Classification**  
Mute scope; record-level preference; filtering.

**Notes**  
Muting a record does not delete, revoke or alter the canonical record.

---

## REM-05-394 — Mutes may apply to a relationship type

**Source**  
Section 35: “A mute may apply to: a relationship type.”

**Requirement**  
A mute MAY target a defined relationship type.

**Classification**  
Mute scope; relationship filtering; preference.

**Notes**  
For example, a user may suppress notifications associated with follows, endorsements or subscription activity without muting the underlying identities.

---

## REM-05-395 — Mutes are normally private

**Source**  
Section 35: “Mutes are normally private application or repository preferences.”

**Requirement**  
A mute SHOULD be private by default.

**Classification**  
Privacy by default; user preference; mute relationship.

**Notes**  
The muted party ordinarily has no need to know that the preference exists.

---

## REM-05-396 — Mutes may be application preferences

**Source**  
Section 35: “Mutes are normally private application or repository preferences.”

**Requirement**  
A mute MAY be maintained as an application-level preference.

**Classification**  
Application preference; local state; mute implementation.

**Notes**  
Application-local storage may be appropriate when the user does not expect the mute to survive application replacement.

---

## REM-05-397 — Mutes may be repository preferences

**Source**  
Section 35: “Mutes are normally private application or repository preferences.”

**Requirement**  
A mute MAY be maintained as a repository-level preference.

**Classification**  
Repository preference; portable state; mute implementation.

**Notes**  
Repository storage may support portability across compatible applications.

---

## REM-05-398 — Mutes may be portable

**Source**  
Section 35: “They may be portable where the user reasonably expects them to survive application changes.”

**Requirement**  
A mute MAY be portable across compatible applications where the user reasonably expects the preference to survive an application change.

**Classification**  
Preference portability; application replacement; user expectation.

**Notes**  
Portability should be explicit and should preserve the mute’s privacy classification.

---

## REM-05-399 — Portability must reflect reasonable user expectation

**Source**  
Section 35: “where the user reasonably expects them to survive application changes.”

**Requirement**  
An implementation deciding whether to persist or migrate a mute SHOULD consider the user’s reasonable expectation of continuity across application changes.

**Classification**  
User expectation; portability policy; preference continuity.

**Notes**  
A system should avoid surprising users either by silently discarding expected mutes or by unexpectedly exporting purely local preferences.

---

## Editorial QA summary

The completed extraction was reviewed for:

- exact coverage of Sections 31–35 only;
- continuous numbering from `REM-05-343` through `REM-05-399`;
- separation of termination, revocation and dispute semantics;
- preservation of independent control over each party’s historical relationship records;
- distinction between current authority and historical proof of earlier authority;
- non-destructive representation of assertions and counterclaims;
- distinction between blocking, protocol-level deletion and provider suspension;
- distinction between blocks and mutes;
- privacy treatment for blocks and mutes;
- traceability of every requirement to source wording; and
- preservation of the source model’s normative strength without importing requirements from other sections or earlier drafts.
