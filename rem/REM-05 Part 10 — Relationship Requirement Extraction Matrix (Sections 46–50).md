# REM-05 Part 10 — Relationship Requirement Extraction Matrix (Sections 46–50)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 46–50 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

46. Relationship duplication
47. Relationship uniqueness
48. Application-specific relationship metadata
49. Algorithms and relationships
50. Relationship-based access

Requirement identifiers continue sequentially from Part 9, beginning with `REM-05-506`.

---

# 46. Relationship duplication

## REM-05-506 — Equivalent relationships may originate through multiple applications

**Source**  
Section 46: “Multiple applications may attempt to create equivalent relationship records.”

**Requirement**  
A Relay repository MUST anticipate that multiple applications may independently attempt to create semantically equivalent relationship records for the same source, target and context.

**Classification**  
Relationship lifecycle; interoperability; duplicate handling.

**Notes**  
Application multiplicity must not cause the portable relationship graph to fragment into client-owned duplicates.

---

## REM-05-507 — Repositories should prevent accidental relationship duplication

**Source**  
Section 46: “The repository should prevent accidental duplication where the schema defines one active relationship per source, target and context.”

**Requirement**  
A Relay repository SHOULD prevent accidental duplicate active relationship records when the governing schema defines a single active relationship for a given source, target and context.

**Classification**  
Repository behaviour; duplicate prevention; schema enforcement.

**Notes**  
Duplicate prevention is conditional on the relationship schema defining the relevant uniqueness semantics.

---

## REM-05-508 — Duplicate prevention must respect source, target and context

**Source**  
Section 46: “one active relationship per source, target and context.”

**Requirement**  
Where a relationship schema defines uniqueness by source, target and context, duplicate detection MUST evaluate all of those dimensions rather than treating target identity alone as sufficient.

**Classification**  
Uniqueness; context; schema semantics.

**Notes**  
The same identities may legitimately have relationships of different types or in different contexts.

---

## REM-05-509 — Client changes must not require duplicate active follows

**Source**  
Section 46: “Alice should not need five separate active follow records for Bob merely because five clients were used.”

**Requirement**  
A user MUST NOT be required to create a separate active relationship record solely because the same relationship is accessed or managed through a different compatible application.

**Classification**  
Application portability; relationship continuity; duplicate prevention.

**Notes**  
The portable relationship is independent of the client through which it is created or used.

---

## REM-05-510 — Application-specific metadata may be separated from the core relationship

**Source**  
Section 46: “Application-specific metadata may be stored separately.”

**Requirement**  
An implementation MAY store application-specific metadata separately from the canonical relationship record.

**Classification**  
Metadata; application separation; data modelling.

**Notes**  
This allows applications to maintain local presentation or behavioural preferences without duplicating or mutating the underlying portable relationship.

---

# 47. Relationship uniqueness

## REM-05-511 — Relationship schemas may define uniqueness rules

**Source**  
Section 47: “A relationship schema may define a uniqueness rule.”

**Requirement**  
A relationship schema MAY define explicit uniqueness constraints governing how many active records of that relationship type may coexist for specified identity and context dimensions.

**Classification**  
Schema governance; uniqueness; relationship semantics.

---

## REM-05-512 — A follow schema may permit only one active source-to-target follow

**Source**  
Section 47 example: “One active follow from source to target.”

**Requirement**  
A follow relationship schema MAY define that only one active follow relationship may exist from a given source to a given target.

**Classification**  
Follow relationship; uniqueness; schema constraint.

**Notes**  
Such a rule prevents client-specific duplicate follow records while preserving a single portable follow declaration.

---

## REM-05-513 — A membership schema may scope uniqueness by organisation, member and role

**Source**  
Section 47 example: “One active membership per organisation, member and role.”

**Requirement**  
A membership relationship schema MAY define uniqueness across the combination of organisation, member and role.

**Classification**  
Membership; uniqueness; role semantics.

**Notes**  
Including role in the uniqueness key permits distinct legitimate memberships where the schema allows different roles.

---

## REM-05-514 — Repositories should enforce schema uniqueness constraints

**Source**  
Section 47: “The repository should enforce the schema’s uniqueness constraints.”

**Requirement**  
A Relay repository SHOULD enforce the uniqueness constraints declared by the governing relationship schema when accepting creation or activation of relationship records.

**Classification**  
Repository enforcement; schema validation; uniqueness.

---

## REM-05-515 — Uniqueness constraints must not collapse different relationship types

**Source**  
Section 47: “Different relationship types or contexts may coexist.”

**Requirement**  
A repository MUST NOT apply a uniqueness rule in a manner that prevents different relationship types from legitimately coexisting between the same identities unless the governing schema explicitly requires that restriction.

**Classification**  
Relationship semantics; coexistence; schema enforcement.

---

## REM-05-516 — Uniqueness constraints must not collapse different contexts

**Source**  
Section 47: “Different relationship types or contexts may coexist.”

**Requirement**  
A repository MUST permit relationships in distinct contexts to coexist where the governing schema treats those contexts as independently valid.

**Classification**  
Context; uniqueness; relationship multiplicity.

**Notes**  
A context-specific relationship must not be mistaken for a global relationship or for an equivalent relationship in another context.

---

# 48. Application-specific relationship metadata

## REM-05-517 — Applications may maintain custom relationship labels

**Source**  
Section 48: “Applications may maintain local metadata such as: custom labels.”

**Requirement**  
An application MAY maintain local custom labels associated with a relationship.

**Classification**  
Application metadata; user interface; local state.

**Notes**  
A local label does not redefine the protocol-level relationship type.

---

## REM-05-518 — Applications may maintain feed-priority metadata

**Source**  
Section 48: “Applications may maintain local metadata such as: feed priority.”

**Requirement**  
An application MAY maintain local feed-priority metadata for a relationship.

**Classification**  
Application metadata; feeds; ranking preference.

---

## REM-05-519 — Applications may maintain display-grouping metadata

**Source**  
Section 48: “Applications may maintain local metadata such as: display grouping.”

**Requirement**  
An application MAY maintain local display-grouping metadata associated with relationships.

**Classification**  
Application metadata; presentation; grouping.

---

## REM-05-520 — Applications may maintain notification-setting metadata

**Source**  
Section 48: “Applications may maintain local metadata such as: notification settings.”

**Requirement**  
An application MAY maintain local notification settings associated with a relationship.

**Classification**  
Application metadata; notifications; user preference.

---

## REM-05-521 — Applications may maintain private relationship notes

**Source**  
Section 48: “Applications may maintain local metadata such as: private notes.”

**Requirement**  
An application MAY maintain private notes associated with a relationship, subject to applicable privacy and access controls.

**Classification**  
Application metadata; private data; user preference.

---

## REM-05-522 — Portable relationship metadata may use a separate user-owned record

**Source**  
Section 48: “Portable metadata may be stored in a separate record owned by the user.”

**Requirement**  
Relationship metadata intended to remain portable across compatible applications MAY be represented in a separate record controlled by the user.

**Classification**  
Portability; metadata; user ownership.

**Notes**  
Separating portable metadata from the core relationship allows optional user preferences to travel without changing the relationship’s canonical semantics.

---

## REM-05-523 — Application interface needs must not rewrite the core relationship

**Source**  
Section 48: “The core relationship should not be rewritten merely to satisfy one application’s interface.”

**Requirement**  
An application SHOULD NOT rewrite the canonical relationship record merely to satisfy application-specific interface, presentation or local-state requirements.

**Classification**  
Application separation; canonical data; integrity.

**Notes**  
Application-specific state should remain separate where it does not alter the protocol-level meaning of the relationship.

---

# 49. Algorithms and relationships

## REM-05-524 — Relationship records may be inputs to feed algorithms

**Source**  
Section 49: “Applications may use relationship records as inputs to: feeds.”

**Requirement**  
Applications MAY use authorised relationship records as inputs when constructing or ranking feeds.

**Classification**  
Algorithms; feeds; relationship use.

---

## REM-05-525 — Relationship records may be inputs to recommendations

**Source**  
Section 49: “Applications may use relationship records as inputs to: recommendations.”

**Requirement**  
Applications MAY use authorised relationship records as inputs to recommendation systems.

**Classification**  
Algorithms; recommendations; relationship use.

---

## REM-05-526 — Relationship records may be inputs to search ranking

**Source**  
Section 49: “Applications may use relationship records as inputs to: search ranking.”

**Requirement**  
Applications MAY use authorised relationship records as inputs to search-ranking decisions.

**Classification**  
Algorithms; search; ranking.

---

## REM-05-527 — Relationship records may be inputs to access decisions

**Source**  
Section 49: “Applications may use relationship records as inputs to: access decisions.”

**Requirement**  
Applications and access-control systems MAY use authorised relationship records as inputs to access decisions where an applicable access rule permits relationship-based access.

**Classification**  
Access control; algorithms; relationship use.

**Notes**  
The existence of a relationship alone does not imply access; Section 50 requires the qualifying access rule to define the relevant relationship semantics.

---

## REM-05-528 — Relationship records may be inputs to trust calculations

**Source**  
Section 49: “Applications may use relationship records as inputs to: trust calculations.”

**Requirement**  
Applications MAY use authorised relationship records as inputs to contextual trust calculations.

**Classification**  
Trust; algorithms; derived data.

**Notes**  
This does not convert the underlying relationship into a universal trust score or prescribe a protocol-wide reputation interpretation.

---

## REM-05-529 — Relationships do not prescribe a single algorithmic interpretation

**Source**  
Section 49: “The relationship itself does not prescribe one algorithmic interpretation.”

**Requirement**  
A Relay relationship record MUST NOT be interpreted as prescribing a single mandatory feed, recommendation, ranking, access or trust algorithm.

**Classification**  
Algorithmic independence; relationship semantics; application autonomy.

---

## REM-05-530 — A follow may be interpreted as showing all posts

**Source**  
Section 49 example: “following Bob may mean: show all posts.”

**Requirement**  
An application MAY interpret a follow relationship as an instruction or preference to show all eligible posts from the followed identity.

**Classification**  
Follow semantics; feeds; client behaviour.

---

## REM-05-531 — A follow may be interpreted as prioritising posts

**Source**  
Section 49 example: “following Bob may mean: prioritise posts.”

**Requirement**  
An application MAY interpret a follow relationship as an input that prioritises eligible posts from the followed identity.

**Classification**  
Follow semantics; ranking; client behaviour.

---

## REM-05-532 — A follow may be interpreted as inclusion in a selected feed

**Source**  
Section 49 example: “following Bob may mean: include posts in a selected feed.”

**Requirement**  
An application MAY use a follow relationship to include eligible activity from the followed identity in a user-selected feed.

**Classification**  
Follow semantics; feeds; client behaviour.

---

## REM-05-533 — A follow may be interpreted as permitting notifications

**Source**  
Section 49 example: “following Bob may mean: permit notifications.”

**Requirement**  
An application MAY use a follow relationship as an input to notification eligibility, subject to the user’s applicable notification and subscription preferences.

**Classification**  
Follow semantics; notifications; client behaviour.

---

## REM-05-534 — Algorithmic effects are client or subscription choices

**Source**  
Section 49: “Those are client or subscription choices.”

**Requirement**  
The specific algorithmic effects assigned to a relationship MUST remain client-level or subscription-level choices unless a separate protocol rule explicitly defines an effect.

**Classification**  
Application autonomy; subscription semantics; algorithmic independence.

**Notes**  
Portable relationship semantics and application-specific algorithmic behaviour are separate layers.

---

# 50. Relationship-based access

## REM-05-535 — Records may grant access based on active relationships

**Source**  
Section 50: “A record may grant access based on an active relationship.”

**Requirement**  
A Relay record MAY define an access rule whose eligibility depends on the existence of an active qualifying relationship.

**Classification**  
Access control; relationship-based access; record policy.

---

## REM-05-536 — Relationship-based access may target current collaborators

**Source**  
Section 50 example: “Visible to current collaborators.”

**Requirement**  
An access rule MAY define current collaborators as an eligible relationship-based audience.

**Classification**  
Access control; collaboration; audience.

**Notes**  
The rule must still define what constitutes a qualifying current collaborator.

---

## REM-05-537 — Access rules must identify the qualifying relationship type

**Source**  
Section 50: “The access system must define: which relationship type qualifies.”

**Requirement**  
A relationship-based access rule MUST identify the relationship type that qualifies a requester for access.

**Classification**  
Access policy; relationship type; authorisation.

---

## REM-05-538 — Access rules must define reciprocity requirements

**Source**  
Section 50: “The access system must define: whether the relationship must be reciprocal.”

**Requirement**  
A relationship-based access rule MUST specify whether a qualifying relationship must be reciprocal or whether a unilateral relationship is sufficient.

**Classification**  
Access policy; reciprocity; authorisation.

---

## REM-05-539 — Access rules must define the applicable context

**Source**  
Section 50: “The access system must define: which context applies.”

**Requirement**  
A relationship-based access rule MUST identify the relationship context, where context is relevant to determining eligibility.

**Classification**  
Access policy; context; scope.

**Notes**  
A relationship in one project, organisation or role must not silently qualify a requester for access in an unrelated context.

---

## REM-05-540 — Access rules must define whether eligibility is evaluated dynamically

**Source**  
Section 50: “The access system must define: whether access is evaluated dynamically.”

**Requirement**  
A relationship-based access rule MUST specify whether relationship eligibility is evaluated dynamically at the time access is requested or exercised.

**Classification**  
Access control; dynamic evaluation; policy semantics.

---

## REM-05-541 — Access rules must define the effect of relationship termination

**Source**  
Section 50: “The access system must define: what happens when the relationship ends.”

**Requirement**  
A relationship-based access rule MUST define the effect that termination, revocation or expiration of the qualifying relationship has on access.

**Classification**  
Access lifecycle; relationship termination; policy semantics.

---

## REM-05-542 — Ending a relationship should revoke future dynamically evaluated access

**Source**  
Section 50: “Ending the relationship should revoke future access where the rule is dynamic.”

**Requirement**  
Where relationship-based access is dynamically evaluated, ending the qualifying relationship SHOULD revoke future access dependent on that relationship.

**Classification**  
Access revocation; dynamic policy; relationship lifecycle.

**Notes**  
This requirement concerns future access. It does not by itself assert retroactive deletion of data already lawfully obtained or actions already validly completed.

---

## Editorial QA

The extraction for Sections 46–50 has been reviewed for numbering, traceability, normative strength and separation of protocol layers.

- Requirement numbering is continuous from `REM-05-506` through `REM-05-542` with no gaps or duplicates.
- Every requirement traces to an explicit statement, list item or example in Sections 46–50 of the source model.
- Duplicate prevention and uniqueness are kept schema-dependent; the extraction does not invent a universal uniqueness key for all relationship types.
- Application-specific metadata is kept separate from the canonical relationship so that interface preferences do not become protocol semantics.
- Algorithmic use of relationships remains application- or subscription-specific; no relationship is converted into a mandatory ranking, feed or trust algorithm.
- Relationship-based access is treated as an explicit access-policy mechanism rather than as authority inherent in the social relationship itself.
- Dynamic termination affects future relationship-dependent access without being overstated as retroactive erasure.
