# REM-05 Part 6 — Relationship Requirement Extraction Matrix (Sections 26–30)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 26–30 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

26. Personal groups
27. Formal groups
28. Membership
29. Relationship requests
30. Relationship acceptance

Requirement identifiers continue sequentially from Part 5, beginning with `REM-05-279`.

---

# 26. Personal groups

## REM-05-279 — Personal-group control by one identity

**Source**  
Section 26: “A personal group is controlled by one identity...”

**Requirement**  
A personal group MUST be controlled by one Relay Identity.

**Classification**  
Group control; personal organisation; authority.

**Notes**  
The controlling identity determines the group’s membership and use. A personal group is not inherently a jointly governed or mutually recognised group.

---

## REM-05-280 — Personal groups may be private

**Source**  
Section 26: “A personal group is controlled by one identity and may be private.”

**Requirement**  
A personal group MAY be private.

**Classification**  
Privacy; group visibility; personal organisation.

**Notes**  
The source permits private personal groups but does not require every personal group to be private.

---

## REM-05-281 — Personal-group membership may be known only to the controller

**Source**  
Section 26: “Membership in this group may be known only to Alice.”

**Requirement**  
An implementation MUST support a personal group whose membership is visible only to the controlling identity.

**Classification**  
Membership privacy; confidentiality; personal groups.

**Notes**  
The example establishes that membership need not be disclosed to members, targets or external observers.

---

## REM-05-282 — Addition to a personal group does not imply acceptance

**Source**  
Section 26: “Adding Bob to the group does not mean Bob has accepted a public relationship label.”

**Requirement**  
Adding an identity to a personal group MUST NOT be interpreted as acceptance by that identity of the group membership or associated relationship label.

**Classification**  
Consent semantics; unilateral organisation; anti-misrepresentation.

**Notes**  
Personal-group inclusion is an act of the controlling identity, not a reciprocal declaration by the included identity.

---

## REM-05-283 — Addition to a personal group does not create a public relationship label

**Source**  
Section 26: “Adding Bob to the group does not mean Bob has accepted a public relationship label.”

**Requirement**  
An application MUST NOT present inclusion in a personal group as a publicly accepted relationship label unless the included identity has independently authorised that representation.

**Classification**  
Presentation integrity; privacy; consent.

**Notes**  
A controller may use a private label such as “Close Collaborators” for personal organisation without creating a public claim that the listed identities recognise that label.

---

## REM-05-284 — Personal groups may control visibility

**Source**  
Section 26, permitted uses: “visibility”.

**Requirement**  
A personal group MAY be used to define or assist with record visibility.

**Classification**  
Audience control; visibility; personal groups.

**Notes**  
Use of a personal group for visibility does not itself make group membership public.

---

## REM-05-285 — Personal groups may support feed filtering

**Source**  
Section 26, permitted uses: “feed filtering”.

**Requirement**  
A personal group MAY be used as an input to feed filtering.

**Classification**  
Personalisation; feed construction; personal groups.

**Notes**  
The group remains an organisational mechanism controlled by its owner.

---

## REM-05-286 — Personal groups may define access

**Source**  
Section 26, permitted uses: “access”.

**Requirement**  
A personal group MAY be used to define or assist with access decisions.

**Classification**  
Access control; audience grouping; personal groups.

**Notes**  
Any access effect must remain subject to the applicable record, permission and audience rules.

---

## REM-05-287 — Personal groups may support notifications

**Source**  
Section 26, permitted uses: “notifications”.

**Requirement**  
A personal group MAY be used to select, organise or route notifications.

**Classification**  
Notification management; personal organisation.

**Notes**  
The source does not require notification recipients to know the personal-group label used by the controller.

---

## REM-05-288 — Personal groups may support organisation

**Source**  
Section 26, permitted uses: “organisation”.

**Requirement**  
A personal group MAY be used for private or user-facing organisational purposes.

**Classification**  
Personal organisation; grouping; user experience.

**Notes**  
This is the broadest permitted use and includes categorisation that produces no external relationship effect.

---

# 27. Formal groups

## REM-05-289 — Formal groups may have their own Relay Identity

**Source**  
Section 27: “A formal group may have its own Relay Identity...”

**Requirement**  
A formal group MAY be represented by and operate through its own Relay Identity.

**Classification**  
Group identity; formal organisation; identity modelling.

**Notes**  
The source permits, but does not universally require, a distinct Relay Identity for every formal group.

---

## REM-05-290 — Formal groups may define governance rules

**Source**  
Section 27: “A formal group may have its own Relay Identity and governance rules.”

**Requirement**  
A formal group MAY define governance rules applicable to its membership, authority and operation.

**Classification**  
Governance; formal groups; authority.

**Notes**  
Governance rules may determine how invitations, approvals or multi-party decisions are made.

---

## REM-05-291 — Formal-group model must support organisations

**Source**  
Section 27, examples: “organisation”.

**Requirement**  
The formal-group model SHOULD support organisations as formal groups.

**Classification**  
Group taxonomy; organisational modelling; recommendation.

**Notes**  
The example identifies organisations as an intended formal-group use case.

---

## REM-05-292 — Formal-group model must support associations

**Source**  
Section 27, examples: “association”.

**Requirement**  
The formal-group model SHOULD support associations as formal groups.

**Classification**  
Group taxonomy; association modelling; recommendation.

**Notes**  
An association may use governance and membership rules different from a company or informal team.

---

## REM-05-293 — Formal-group model must support project teams

**Source**  
Section 27, examples: “project team”.

**Requirement**  
The formal-group model SHOULD support project teams as formal groups.

**Classification**  
Group taxonomy; project collaboration; recommendation.

**Notes**  
Project-team membership may be contextual and time-bound.

---

## REM-05-294 — Formal-group model must support communities

**Source**  
Section 27, examples: “community”.

**Requirement**  
The formal-group model SHOULD support communities as formal groups.

**Classification**  
Group taxonomy; community modelling; recommendation.

**Notes**  
Community governance may include moderators, membership rules and participation conditions.

---

## REM-05-295 — Formal-group model must support cooperatives

**Source**  
Section 27, examples: “cooperative”.

**Requirement**  
The formal-group model SHOULD support cooperatives as formal groups.

**Classification**  
Group taxonomy; cooperative governance; recommendation.

**Notes**  
The model must not assume all formal groups use a single-controller governance structure.

---

## REM-05-296 — Formal membership may require invitation

**Source**  
Section 27, membership conditions: “invitation”.

**Requirement**  
A formal-group membership schema MAY require an invitation before membership can be established.

**Classification**  
Membership admission; invitation; formal groups.

**Notes**  
Invitation alone need not activate membership unless the schema’s remaining conditions are also satisfied.

---

## REM-05-297 — Formal membership may require acceptance

**Source**  
Section 27, membership conditions: “acceptance”.

**Requirement**  
A formal-group membership schema MAY require acceptance by the prospective member.

**Classification**  
Membership consent; acceptance; formal groups.

**Notes**  
This supports independently authorised membership rather than unilateral assignment of formal status.

---

## REM-05-298 — Formal membership may require administrator approval

**Source**  
Section 27, membership conditions: “administrator approval”.

**Requirement**  
A formal-group membership schema MAY require approval by an authorised administrator.

**Classification**  
Membership governance; administrative approval.

**Notes**  
The administrator’s authority must derive from the group’s governance and authority model.

---

## REM-05-299 — Formal membership may require a credential

**Source**  
Section 27, membership conditions: “credential”.

**Requirement**  
A formal-group membership schema MAY require a valid credential.

**Classification**  
Credential-backed membership; evidence; verification.

**Notes**  
The credential may establish eligibility, status or authority required by the group.

---

## REM-05-300 — Formal membership may require payment

**Source**  
Section 27, membership conditions: “payment”.

**Requirement**  
A formal-group membership schema MAY make membership conditional on payment.

**Classification**  
Conditional membership; payment status; formal groups.

**Notes**  
The source identifies payment as a possible condition but does not define payment processing rules.

---

## REM-05-301 — Formal membership may require multi-party authorisation

**Source**  
Section 27, membership conditions: “multi-party authorisation”.

**Requirement**  
A formal-group membership schema MAY require authorisation from multiple parties before membership becomes active.

**Classification**  
Multi-party governance; membership approval; threshold authority.

**Notes**  
The schema or governance rules must determine the required parties or approval threshold.

---

## REM-05-302 — Formal membership should use independently verifiable records

**Source**  
Section 27: “Formal group membership should be represented through independently verifiable relationship records.”

**Requirement**  
Formal-group membership SHOULD be represented through independently verifiable relationship records.

**Classification**  
Membership verification; relationship records; recommendation.

**Notes**  
A provider-maintained list or application-only database is insufficient where it cannot be independently resolved and verified through Relay records.

---

# 28. Membership

## REM-05-303 — Membership may be open

**Source**  
Section 28, membership states or modes: “open”.

**Requirement**  
A membership schema MAY support open membership.

**Classification**  
Membership mode; admission policy.

**Notes**  
The schema must still define how open membership becomes represented and active.

---

## REM-05-304 — Membership may be requested

**Source**  
Section 28, membership states or modes: “requested”.

**Requirement**  
A membership schema MAY represent membership as requested.

**Classification**  
Membership lifecycle; request state.

**Notes**  
A requested membership is not necessarily active.

---

## REM-05-305 — Membership may be invited

**Source**  
Section 28, membership states or modes: “invited”.

**Requirement**  
A membership schema MAY represent membership as invited.

**Classification**  
Membership lifecycle; invitation state.

**Notes**  
An invitation may await acceptance or other activation conditions.

---

## REM-05-306 — Membership may be approved

**Source**  
Section 28, membership states or modes: “approved”.

**Requirement**  
A membership schema MAY represent membership as approved.

**Classification**  
Membership lifecycle; approval state.

**Notes**  
Approval may be one of several conditions required for activation.

---

## REM-05-307 — Membership may be credential-based

**Source**  
Section 28, membership states or modes: “credential-based”.

**Requirement**  
A membership schema MAY define membership as credential-based.

**Classification**  
Credential-backed membership; verification.

**Notes**  
The applicable credential and its validity must be evaluated under the relevant schema.

---

## REM-05-308 — Membership may be paid

**Source**  
Section 28, membership states or modes: “paid”.

**Requirement**  
A membership schema MAY define a paid membership mode or state.

**Classification**  
Membership mode; commercial condition.

**Notes**  
The relationship model records the membership condition or status; it does not by itself define the payment system.

---

## REM-05-309 — Membership may be temporary

**Source**  
Section 28, membership states or modes: “temporary”.

**Requirement**  
A membership schema MAY support temporary membership.

**Classification**  
Time-bound membership; lifecycle.

**Notes**  
Temporary membership should be associated with an explicit validity period or expiration rule where applicable.

---

## REM-05-310 — Membership may be revoked

**Source**  
Section 28, membership states or modes: “revoked”.

**Requirement**  
A membership schema MAY represent membership as revoked.

**Classification**  
Membership lifecycle; revocation.

**Notes**  
Revocation terminates current membership effect without necessarily erasing historical records.

---

## REM-05-311 — Membership may be expired

**Source**  
Section 28, membership states or modes: “expired”.

**Requirement**  
A membership schema MAY represent membership as expired.

**Classification**  
Membership lifecycle; expiration.

**Notes**  
An expired membership may remain historically verifiable while no longer conferring current status or authority.

---

## REM-05-312 — Membership schema should define issuers

**Source**  
Section 28: “A membership schema should define: who may issue membership...”

**Requirement**  
A membership schema SHOULD define which identity or authority may issue membership.

**Classification**  
Membership authority; schema definition; recommendation.

**Notes**  
This prevents an unauthorised party from creating an apparently valid formal membership.

---

## REM-05-313 — Membership schema should define acceptance requirements

**Source**  
Section 28: “A membership schema should define... whether member acceptance is required...”

**Requirement**  
A membership schema SHOULD define whether acceptance by the member is required.

**Classification**  
Consent; membership schema; recommendation.

**Notes**  
The requirement distinguishes unilateral issuance from mutually accepted membership.

---

## REM-05-314 — Membership schema should define public visibility

**Source**  
Section 28: “A membership schema should define... whether membership is public...”

**Requirement**  
A membership schema SHOULD define whether membership may or must be public.

**Classification**  
Visibility; membership privacy; recommendation.

**Notes**  
The schema may permit restricted or selectively disclosed membership where public disclosure is inappropriate.

---

## REM-05-315 — Membership schema should define roles

**Source**  
Section 28: “A membership schema should define... roles...”

**Requirement**  
A membership schema SHOULD define the roles that may be assigned within the membership relationship.

**Classification**  
Role modelling; membership schema; recommendation.

**Notes**  
Roles should not be assumed to confer authority beyond what the schema or an explicit authority declaration provides.

---

## REM-05-316 — Membership schema should define authority

**Source**  
Section 28: “A membership schema should define... authority...”

**Requirement**  
A membership schema SHOULD define whether and what authority a membership relationship conveys.

**Classification**  
Authority; membership schema; recommendation.

**Notes**  
Any authority must remain explicitly bounded rather than inferred from the generic fact of membership.

---

## REM-05-317 — Membership schema should define expiration

**Source**  
Section 28: “A membership schema should define... expiration...”

**Requirement**  
A membership schema SHOULD define applicable expiration behaviour.

**Classification**  
Lifecycle; expiration; recommendation.

**Notes**  
This may include a fixed end time, renewable term or condition-based expiry.

---

## REM-05-318 — Membership schema should define removal rules

**Source**  
Section 28: “A membership schema should define... removal rules.”

**Requirement**  
A membership schema SHOULD define the rules under which membership may be removed or ended.

**Classification**  
Membership termination; governance; recommendation.

**Notes**  
Removal rules should identify the relevant authority and preserve independent control of each party’s records.

---

## REM-05-319 — Organisation cannot rewrite member repository

**Source**  
Section 28: “The organisation cannot rewrite the member’s personal repository...”

**Requirement**  
An organisation MUST NOT rewrite the member’s personal repository merely by virtue of the membership relationship.

**Classification**  
Repository authority; membership independence; integrity.

**Notes**  
The organisation controls its own membership declarations, not the member’s repository history.

---

## REM-05-320 — Member cannot rewrite organisation membership record

**Source**  
Section 28: “...and the member cannot rewrite the organisation’s membership record.”

**Requirement**  
A member MUST NOT rewrite the organisation’s membership record merely by virtue of being its subject or participant.

**Classification**  
Repository authority; membership independence; integrity.

**Notes**  
The member may create or update the member’s own corresponding declaration where authorised, but does not control the organisation’s record.

---

# 29. Relationship requests

## REM-05-321 — Consent-based relationships begin with a request

**Source**  
Section 29: “A relationship requiring consent begins with a request record or protocol message.”

**Requirement**  
A relationship requiring consent MUST begin with a request record or protocol message.

**Classification**  
Consent workflow; relationship initiation; lifecycle.

**Notes**  
The request initiates the approval process but does not itself establish the active reciprocal relationship.

---

## REM-05-322 — Request should identify requesting identity

**Source**  
Section 29, request content: “requesting identity”.

**Requirement**  
A relationship request SHOULD identify the requesting identity.

**Classification**  
Request provenance; identity; recommendation.

**Notes**  
The target must be able to determine who is proposing the relationship.

---

## REM-05-323 — Request should identify target identity

**Source**  
Section 29, request content: “target identity”.

**Requirement**  
A relationship request SHOULD identify the target identity.

**Classification**  
Request addressing; identity; recommendation.

**Notes**  
The request must not be ambiguously addressed where consent is identity-specific.

---

## REM-05-324 — Request should identify relationship type

**Source**  
Section 29, request content: “relationship type”.

**Requirement**  
A relationship request SHOULD identify the proposed relationship type.

**Classification**  
Relationship semantics; request content; recommendation.

**Notes**  
The target must know what relationship is being proposed before deciding whether to accept it.

---

## REM-05-325 — Request should identify context

**Source**  
Section 29, request content: “context”.

**Requirement**  
A relationship request SHOULD identify the context in which the proposed relationship would apply.

**Classification**  
Context scoping; request content; recommendation.

**Notes**  
A context-specific proposal must not be presented as a global relationship request.

---

## REM-05-326 — Request should identify requested role

**Source**  
Section 29, request content: “requested role”.

**Requirement**  
A relationship request SHOULD identify any role being requested.

**Classification**  
Role proposal; request content; recommendation.

**Notes**  
The role should be evaluated separately from any authority it may or may not confer.

---

## REM-05-327 — Request should identify expiration

**Source**  
Section 29, request content: “expiration”.

**Requirement**  
A relationship request SHOULD identify its expiration or the proposed relationship’s relevant expiration condition.

**Classification**  
Request lifecycle; time limitation; recommendation.

**Notes**  
An expired request must not later be treated as an active outstanding proposal without renewal or reissuance.

---

## REM-05-328 — Request should identify visibility proposal

**Source**  
Section 29, request content: “visibility proposal”.

**Requirement**  
A relationship request SHOULD identify the proposed visibility of the resulting relationship.

**Classification**  
Visibility consent; request content; recommendation.

**Notes**  
Acceptance of the relationship type must not silently imply acceptance of an undisclosed public visibility setting.

---

## REM-05-329 — Request should identify supporting evidence

**Source**  
Section 29, request content: “supporting evidence”.

**Requirement**  
A relationship request SHOULD include or reference supporting evidence where relevant.

**Classification**  
Evidence; request validation; recommendation.

**Notes**  
Evidence may be required by the relationship schema or used by the target to evaluate the proposal.

---

## REM-05-330 — Target may accept a request

**Source**  
Section 29: “The target may: accept...”

**Requirement**  
The target of a relationship request MAY accept the request.

**Classification**  
Consent response; acceptance.

**Notes**  
Acceptance remains subject to the schema’s activation conditions.

---

## REM-05-331 — Target may decline a request

**Source**  
Section 29: “The target may... decline...”

**Requirement**  
The target of a relationship request MAY decline the request.

**Classification**  
Consent response; denial.

**Notes**  
Declining a request does not create an active reciprocal relationship.

---

## REM-05-332 — Target may ignore a request

**Source**  
Section 29: “The target may... ignore...”

**Requirement**  
The target of a relationship request MAY ignore the request.

**Classification**  
Consent response; non-response.

**Notes**  
Absence of a response MUST NOT be interpreted as acceptance.

---

## REM-05-333 — Target may counter-propose

**Source**  
Section 29: “The target may... counter-propose...”

**Requirement**  
The target of a relationship request MAY issue a counter-proposal.

**Classification**  
Relationship negotiation; consent workflow.

**Notes**  
A counter-proposal is a new or modified proposal and must not be treated as acceptance of the original terms.

---

## REM-05-334 — Target may block future requests

**Source**  
Section 29: “The target may... block future requests.”

**Requirement**  
The target MAY block future relationship requests from the requesting identity or for the applicable request category.

**Classification**  
Request control; blocking; abuse prevention.

**Notes**  
The exact scope of the block should be made clear by the implementation or applicable schema.

---

## REM-05-335 — Request is not an active reciprocal relationship

**Source**  
Section 29: “A request is not itself an active reciprocal relationship.”

**Requirement**  
A relationship request MUST NOT be treated or presented as an active reciprocal relationship.

**Classification**  
Lifecycle integrity; consent; anti-misrepresentation.

**Notes**  
The requesting identity’s proposal does not establish the target’s independent declaration or approval.

---

# 30. Relationship acceptance

## REM-05-336 — Acceptance should create an independently authorised record

**Source**  
Section 30: “Acceptance should create an independently authorised record in the accepting identity’s repository.”

**Requirement**  
Acceptance of a consent-based relationship SHOULD create an independently authorised record in the accepting identity’s repository.

**Classification**  
Acceptance; independent authority; repository record; recommendation.

**Notes**  
The accepting identity’s record establishes that identity’s own declaration and must not be controlled by the requester.

---

## REM-05-337 — Acceptance record may reference the proposal

**Source**  
Section 30: “It may reference the original proposal.”

**Requirement**  
An acceptance record MAY reference the original relationship proposal.

**Classification**  
Traceability; reciprocal linkage; lifecycle.

**Notes**  
The reference can connect the request and acceptance histories without collapsing them into one authority record.

---

## REM-05-338 — Activation depends on schema conditions

**Source**  
Section 30: “The relationship becomes active only when the schema’s activation conditions are satisfied.”

**Requirement**  
A consent-based relationship MUST become active only after all activation conditions defined by its schema have been satisfied.

**Classification**  
Activation; schema validation; lifecycle.

**Notes**  
A single acceptance action may be insufficient where the schema also requires credentials, approvals or matching records.

---

## REM-05-339 — Mutual friendship may require two active records

**Source**  
Section 30: “For a mutual friendship, this may require two active records.”

**Requirement**  
A mutual-friendship schema MAY require two independently authorised active relationship records before the friendship is considered active.

**Classification**  
Reciprocity; friendship; activation conditions.

**Notes**  
Each participating identity retains control of its own record.

---

## REM-05-340 — Organisation membership may require organisation approval

**Source**  
Section 30, organisation-membership conditions: “organisation approval”.

**Requirement**  
An organisation-membership schema MAY require approval by the organisation before membership becomes active.

**Classification**  
Membership activation; organisation approval.

**Notes**  
The approving party must have valid authority under the organisation’s governance model.

---

## REM-05-341 — Organisation membership may require member acceptance

**Source**  
Section 30, organisation-membership conditions: “member acceptance”.

**Requirement**  
An organisation-membership schema MAY require acceptance by the prospective member before membership becomes active.

**Classification**  
Membership activation; member consent.

**Notes**  
Organisation approval alone does not establish member acceptance where the schema requires both.

---

## REM-05-342 — Organisation membership may require a valid credential

**Source**  
Section 30, organisation-membership conditions: “a valid membership credential”.

**Requirement**  
An organisation-membership schema MAY require a valid membership credential before membership becomes active.

**Classification**  
Membership activation; credential validation.

**Notes**  
The credential must remain valid under its own expiration and revocation rules at the time it is relied upon.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 26–30 of `design-notes/05-relationship-model.md`.
- Section 25 was used only to confirm the transition into personal and formal group models and was not re-extracted.
- Section 31 and later content was excluded.
- Examples were used only to clarify source meaning and were not promoted into universal requirements beyond the source language.

## Numbering verification

- First requirement: `REM-05-279`.
- Final requirement: `REM-05-342`.
- Requirement numbering continues directly from Part 5.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, list item, definition or necessary decomposition of a compound statement.
- Personal-group uses, formal-membership conditions, membership-schema fields, request contents and target response options were extracted separately because each represents independently testable behaviour.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions or options.
- Descriptive examples were converted to `SHOULD` only where they identify intended model support, and were not elevated to unconditional protocol validity rules.

## Editorial verification

- Personal-group inclusion remains a unilateral organisational act and is not represented as target consent.
- Formal-group membership remains independently verifiable rather than dependent on one provider-maintained list.
- Organisation and member repositories remain independently controlled.
- Relationship requests remain proposals and are not represented as active reciprocal relationships.
- Non-response remains distinct from acceptance.
- Acceptance creates independent authority and remains subject to schema-defined activation conditions.
- Matching records, approvals and credentials remain separate possible conditions rather than being collapsed into a single generic acceptance event.
