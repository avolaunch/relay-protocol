# Relay Protocol v0.1  
## Core Object 5: Relay Relationship Model

### 1. Definition

A **Relay Relationship** is a structured, portable record describing a connection between Relay Identities, Relay Records or recognised external entities.

Examples include:

- follows;
- subscribes to;
- collaborates with;
- works for;
- is a member of;
- endorses;
- trusts;
- blocks;
- is represented by;
- authored;
- owns;
- manages;
- is connected to.

A Relay Relationship must not depend solely on the continued existence of the application through which it was created.

An application may help establish, display, filter or interpret a relationship, but it does not automatically own that relationship.

---

## 2. Purpose

The Relationship Model exists to preserve **relationship continuity**.

It must allow a person to:

- establish a connection through one application;
- view or act on that connection through another compatible application;
- retain the connection after changing providers;
- distinguish public relationships from private ones;
- revoke or change their side of a relationship;
- verify which identity authorised each relationship claim;
- prevent applications from converting every relationship into permanent platform lock-in.

A list of exported usernames is not sufficient.

A relationship is operationally portable only when another compatible service can resolve the identities involved and continue interpreting the connection.

---

## 3. Relationship as a record

A Relay Relationship is represented as a Relay Record.

It is normally stored in the repository of the identity making the relationship declaration.

Example:

```json
{
  "schema": "com.relay.relationship.follow.v1",
  "uri": "relay://rid:relay:alice/com.relay.relationship/follow_01JX91",
  "source": "rid:relay:alice",
  "target": "rid:relay:bob",
  "relationship": "follow",
  "createdAt": "2026-08-24T10:00:00Z",
  "visibility": {
    "classification": "public"
  }
}
```

Alice’s repository is the canonical source of Alice’s declaration that she follows Bob.

Bob’s repository does not need to contain the same record for Alice’s declaration to exist.

---

## 4. Relationship components

A relationship record may contain:

1. **Source**
2. **Target**
3. **Relationship Type**
4. **Direction**
5. **Status**
6. **Visibility**
7. **Audience**
8. **Context**
9. **Provenance**
10. **Validity Period**
11. **Reciprocal Reference**
12. **Authority**
13. **Conditions**

Not every relationship requires every component.

---

## 5. Source

The **Source** is the identity or record making the relationship declaration.

Example:

```text
Alice follows Bob.
```

Alice is the source.

The source must normally correspond to the Relay Identity controlling the repository in which the relationship record exists.

An application may submit the declaration under delegated authority, but the application is not the relationship source unless the application itself is intentionally acting as a Relay Identity.

---

## 6. Target

The **Target** is the identity, record or recognised external entity to which the relationship points.

A target may be:

- a Relay Identity;
- a Relay Record;
- a defined group;
- an organisation;
- a credential;
- an application;
- an external identifier where no Relay Identity exists.

Examples:

```text
Alice follows Bob.
Alice authored Article X.
Alice trusts Moderation Service Y.
Alice belongs to Organisation Z.
```

The target should use a stable Relay identifier wherever possible.

Temporary provider URLs and visible handles should not be used as the sole permanent target reference.

---

## 7. Relationship type

The **Relationship Type** defines the meaning of the connection.

Examples include:

```text
follow
subscribe
friend
colleague
collaborator
member
employee
employer
author
owner
manager
endorser
trusts
blocks
mutes
represents
parent-of
guardian-of
```

Each relationship type must be defined by a schema.

The schema should specify:

- direction;
- whether reciprocity is required;
- whether approval is required;
- whether the relationship may be public;
- whether it may expire;
- whether it conveys authority;
- whether evidence or credentials are required;
- how it may be revoked.

---

## 8. Direction

A relationship may be:

### Directed

One identity makes a declaration about another.

Examples:

```text
Alice follows Bob.
Alice subscribes to Bob.
Alice blocks Bob.
```

Bob does not need to make a matching declaration.

### Reciprocal

Both identities separately confirm a relationship.

Examples:

```text
Alice and Bob are collaborators.
Alice and Bob are friends.
```

### Undirected by interpretation

Two matching directed declarations may be presented as one mutual relationship.

The underlying records should still identify each identity’s independent authority.

### Authority-bearing

A relationship may convey limited authority.

Examples:

```text
Alice represents Organisation Z.
Bob may administer Team Q.
```

Authority-bearing relationships require stricter validation than ordinary social connections.

---

## 9. Unilateral relationships

A unilateral relationship requires only the source identity’s authorisation.

Examples include:

- follow;
- subscribe;
- block;
- mute;
- endorse;
- trust;
- bookmark;
- watch.

The target may be notified, but does not need to approve the relationship.

A unilateral relationship must not be presented as though the target agreed to it.

For example:

```text
Alice considers Bob a trusted source.
```

does not mean:

```text
Bob has accepted or verified Alice’s judgement.
```

---

## 10. Reciprocal relationships

A reciprocal relationship requires independent authorisation from each participating identity.

For example:

```text
Alice proposes collaboration with Bob.
Bob accepts.
```

This may produce two linked records:

### Alice’s record

```json
{
  "source": "rid:relay:alice",
  "target": "rid:relay:bob",
  "relationship": "collaborator",
  "status": "active",
  "reciprocalRecord": "relay://rid:relay:bob/com.relay.relationship/collab_77"
}
```

### Bob’s record

```json
{
  "source": "rid:relay:bob",
  "target": "rid:relay:alice",
  "relationship": "collaborator",
  "status": "active",
  "reciprocalRecord": "relay://rid:relay:alice/com.relay.relationship/collab_21"
}
```

Neither identity controls the other’s declaration.

---

## 11. Relationship status

A relationship may have a status such as:

```text
proposed
pending
active
declined
ended
revoked
expired
disputed
suspended
```

The allowed states depend on the relationship schema.

A simple follow may move directly from nonexistent to active.

A collaboration may require:

```text
proposed → pending → active
```

A verified employment relationship may require an external credential rather than a simple self-declaration.

---

## 12. Relationship lifecycle

A relationship lifecycle may include:

### Proposal

One identity proposes a reciprocal or approval-based relationship.

### Acceptance

The target authorises its side.

### Activation

The relationship becomes operational.

### Modification

Context, visibility, role or conditions change.

### Suspension

The relationship temporarily stops producing effects without being permanently ended.

### Termination

One or both parties end the relationship.

### Expiration

The relationship ends automatically at a defined time.

### Dispute

One party challenges an externally issued or asserted relationship.

The relationship history should remain verifiable where the schema requires it.

---

## 13. Relationship ownership

Each identity owns and controls its own relationship declaration.

For a mutual relationship:

- Alice controls Alice’s record;
- Bob controls Bob’s record.

Neither party may silently rewrite or delete the other party’s declaration.

If Alice ends a collaboration, Alice may revoke her own active participation.

Bob’s record may then reflect that the reciprocal relationship is no longer active, but Bob retains control over Bob’s historical record.

---

## 14. Relationship continuity

A relationship remains operationally portable when:

- both identities retain stable Relay Identifiers;
- the relationship records preserve stable Record URIs;
- compatible applications understand the relationship schema;
- provider migration does not alter source or target identity;
- applications can discover the current repositories involved.

Changing from Application A to Application B must not require recreating the underlying relationship.

Changing Relay Provider must not alter the relationship’s source or target.

---

## 15. Follows

A **follow** is a directed declaration that the source wishes to receive, discover or prioritise public activity from the target.

Example:

```json
{
  "schema": "com.relay.relationship.follow.v1",
  "source": "rid:relay:alice",
  "target": "rid:relay:bob",
  "relationship": "follow",
  "status": "active"
}
```

A follow does not automatically grant:

- access to restricted records;
- messaging rights;
- endorsement;
- friendship;
- authority;
- reciprocal following.

Applications may use follow records as one input when constructing feeds.

---

## 16. Subscriptions

A **subscription** is a directed relationship requesting delivery of a defined category of activity.

A subscription may be more specific than a follow.

Example:

```json
{
  "source": "rid:relay:alice",
  "target": "rid:relay:bob",
  "relationship": "subscribe",
  "filters": {
    "collections": [
      "com.relay.article",
      "com.relay.project"
    ]
  },
  "delivery": {
    "mode": "feed"
  }
}
```

A subscription may specify:

- collections;
- topics;
- event types;
- delivery method;
- frequency;
- language;
- priority.

The target is not required to provide every requested delivery method.

---

## 17. Followers and audiences

A person’s followers should not be represented only as a provider-maintained counter.

The count is a derived value.

The underlying graph consists of relationship records distributed across follower repositories.

A service may build an index showing:

```text
Bob has 20,000 known active followers.
```

That count depends on:

- indexed repositories;
- relationship visibility;
- block rules;
- unavailable identities;
- revoked records;
- index freshness.

Applications must not present derived counts as more precise or complete than their data permits.

---

## 18. Private relationships

Not every relationship should be public.

Private relationships may include:

- friendship;
- family connection;
- private collaboration;
- trusted contact;
- client relationship;
- medical or legal relationship;
- membership in a sensitive group.

A private relationship record should not expose its target or meaning to unauthorised observers.

Possible implementations include:

- restricted record access;
- encrypted relationship records;
- opaque audience identifiers;
- separately stored private relationship repositories.

Relay v0.1 may initially support restricted relationship records while deferring advanced private graph protection to a later version.

---

## 19. Visibility

A relationship may be:

```text
public
unlisted
restricted
private
```

Visibility may apply separately to:

- existence of the relationship;
- relationship type;
- target identity;
- context;
- dates;
- associated evidence.

For example, a person may publicly disclose:

```text
Member of Organisation Z
```

without exposing:

```text
Internal role or membership number
```

The schema should support selective disclosure where needed.

---

## 20. Relationship context

A relationship may exist within a defined context.

Examples:

```text
collaborator on Project X
member of Organisation Z
subscriber to Photography posts
employee during 2024–2026
moderator of Community Q
```

Example:

```json
{
  "relationship": "collaborator",
  "target": "rid:relay:bob",
  "context": {
    "record": "relay://rid:relay:alice/com.relay.project/project_42",
    "role": "designer"
  }
}
```

The same two identities may have multiple relationships in different contexts.

A global relationship should not be inferred from a context-specific one.

---

## 21. Relationship validity period

A relationship may define:

- start time;
- end time;
- expiration;
- renewal;
- effective date.

Example:

```json
{
  "validFrom": "2026-01-01T00:00:00Z",
  "validUntil": "2026-12-31T23:59:59Z"
}
```

An expired relationship may remain historically verifiable while no longer producing current authority or access.

---

## 22. Relationship evidence

Some relationships are self-declared.

Others require evidence.

Examples:

- employment;
- professional membership;
- legal representation;
- guardianship;
- company directorship;
- ownership;
- academic affiliation.

Evidence may include:

- a Verifiable Credential;
- a reciprocal signed relationship;
- an organisation-issued assertion;
- a recognised registry reference;
- a legal document;
- an application-specific attestation.

The relationship record should indicate whether it is:

```text
self-declared
reciprocally confirmed
issuer-attested
credential-backed
externally verified
disputed
```

---

## 23. Claimed versus verified relationships

Relay must distinguish between:

```text
Alice says she works for Company Z.
```

and:

```text
Company Z has issued a signed employment credential to Alice.
```

Both may exist as records, but they carry different evidentiary weight.

Applications should not describe a self-declared relationship as verified.

Verification should identify:

- verifier;
- method;
- date;
- scope;
- expiration;
- revocation status.

---

## 24. Authority-bearing relationships

Some relationships grant the source or target authority.

Examples:

- administrator of an organisation;
- legal representative;
- guardian;
- application operator;
- delegated publisher;
- repository custodian.

Such relationships must specify:

- exact capabilities;
- scope;
- duration;
- approval requirements;
- revocation mechanism;
- evidence;
- whether authority may be re-delegated.

Example:

```json
{
  "relationship": "administrator",
  "source": "rid:relay:organisation-z",
  "target": "rid:relay:alice",
  "authority": {
    "actions": [
      "publish",
      "manage-members"
    ],
    "validUntil": "2027-01-01T00:00:00Z",
    "mayRedelegate": false
  }
}
```

A generic relationship label must not silently confer broad authority.

---

## 25. Groups

A **Relay Group** is a defined set of identities used for relationships, access or communication.

Examples:

- close collaborators;
- family;
- team members;
- subscribers;
- project participants;
- community moderators.

A group may be represented by:

- a group record;
- membership relationship records;
- a group-controlled Relay Identity;
- a private access list.

The group model must distinguish between:

- a personal organisational list;
- a mutually recognised group;
- a formal organisation;
- an application-generated audience segment.

---

## 26. Personal groups

A personal group is controlled by one identity and may be private.

Example:

```text
Alice’s “Close Collaborators” group
```

Membership in this group may be known only to Alice.

Adding Bob to the group does not mean Bob has accepted a public relationship label.

Personal groups may be used for:

- visibility;
- feed filtering;
- access;
- notifications;
- organisation.

---

## 27. Formal groups

A formal group may have its own Relay Identity and governance rules.

Examples:

- organisation;
- association;
- project team;
- community;
- cooperative.

Membership may require:

- invitation;
- acceptance;
- administrator approval;
- credential;
- payment;
- multi-party authorisation.

Formal group membership should be represented through independently verifiable relationship records.

---

## 28. Membership

Membership may be:

```text
open
requested
invited
approved
credential-based
paid
temporary
revoked
expired
```

A membership schema should define:

- who may issue membership;
- whether member acceptance is required;
- whether membership is public;
- roles;
- authority;
- expiration;
- removal rules.

The organisation cannot rewrite the member’s personal repository, and the member cannot rewrite the organisation’s membership record.

---

## 29. Relationship requests

A relationship requiring consent begins with a request record or protocol message.

A request should contain:

- requesting identity;
- target identity;
- relationship type;
- context;
- requested role;
- expiration;
- visibility proposal;
- supporting evidence.

The target may:

- accept;
- decline;
- ignore;
- counter-propose;
- block future requests.

A request is not itself an active reciprocal relationship.

---

## 30. Relationship acceptance

Acceptance should create an independently authorised record in the accepting identity’s repository.

It may reference the original proposal.

The relationship becomes active only when the schema’s activation conditions are satisfied.

For a mutual friendship, this may require two active records.

For organisation membership, it may require:

- organisation approval;
- member acceptance;
- a valid membership credential.

---

## 31. Relationship termination

A source identity may end its own relationship declaration.

For unilateral relationships, termination normally ends the relationship immediately.

For reciprocal relationships, one party’s withdrawal should cause the mutual state to become inactive.

The other party may retain a historical record such as:

```text
Previously collaborated with Alice.
```

provided the schema and visibility rules allow it.

Termination must not allow one party to falsify the other’s historical record.

---

## 32. Relationship revocation

Revocation is particularly important for authority-bearing relationships.

Revocation should identify:

- relationship record;
- revoking authority;
- effective time;
- reason where appropriate;
- affected capabilities;
- whether existing actions remain valid.

After revocation, new authority-based actions must be rejected.

The system may retain historical proof that the authority existed during an earlier period.

---

## 33. Relationship disputes

An identity may dispute a relationship assertion.

Example:

```text
Company Z claims Alice is an employee.
Alice disputes the claim.
```

The dispute should be represented separately rather than deleting or altering the original assertion.

Applications may display:

- assertion;
- issuer;
- evidence;
- dispute;
- current verification status.

Relay does not determine legal truth automatically.

It preserves attributable claims and counterclaims.

---

## 34. Blocks

A **block** is a private or restricted relationship declaration instructing applications and providers to prevent or reduce interaction with a target identity.

A block may affect:

- content visibility;
- replies;
- mentions;
- follows;
- messages;
- relationship requests;
- event delivery;
- discovery.

A block should normally be private.

The target need not be informed unless required by the application or policy.

A block is not equivalent to protocol-level deletion or provider suspension.

---

## 35. Mutes

A **mute** reduces visibility or notifications without necessarily preventing interaction.

A mute may apply to:

- an identity;
- a collection;
- a topic;
- a record;
- a relationship type.

Mutes are normally private application or repository preferences.

They may be portable where the user reasonably expects them to survive application changes.

---

## 36. Trust relationships

A trust relationship expresses that the source chooses to rely on the target for a defined purpose.

Examples:

```text
Trust this identity for photography recommendations.
Trust this service for moderation labels.
Trust this organisation to verify qualifications.
```

Trust must always be scoped.

Example:

```json
{
  "relationship": "trusts",
  "target": "rid:relay:moderation-service",
  "context": {
    "purpose": "moderation-labels",
    "categories": [
      "spam",
      "malware"
    ]
  }
}
```

A general universal trust score should not be inferred from a narrow trust relationship.

---

## 37. Endorsements

An endorsement is a directed assertion expressing support for a person, record, skill or claim.

An endorsement should identify:

- endorser;
- target;
- subject;
- context;
- date;
- visibility;
- whether evidence is included.

Example:

```json
{
  "relationship": "endorses",
  "target": "rid:relay:bob",
  "context": {
    "subject": "software-architecture"
  }
}
```

Endorsements remain controlled by the endorsing identity.

The target cannot rewrite or fabricate them.

---

## 38. Reputation as a derived layer

Relay v0.1 should not define a universal reputation score.

Reputation may be derived from:

- relationships;
- credentials;
- endorsements;
- activity;
- moderation labels;
- application-specific behaviour;
- community participation.

Different applications may calculate reputation differently.

Any reputation result must identify:

- the service producing it;
- source inputs;
- relevant context;
- calculation time;
- limitations.

The underlying relationship records remain separate from the derived score.

---

## 39. Relationship privacy risks

A portable graph may create serious privacy risks.

Relationship data can reveal:

- political associations;
- health conditions;
- religious communities;
- family structures;
- workplaces;
- personal interests;
- private support networks;
- physical location.

Therefore:

- relationships must not all be public by default;
- private relationships should support encryption;
- indexes should respect visibility;
- applications should request only necessary relationship access;
- relationship exports must preserve access classifications;
- private group membership should not leak through counts or metadata.

A decentralised graph can become more invasive than a centralised one if privacy is poorly designed.

---

## 40. Relationship discovery

Applications may discover relationships through:

- the source repository;
- an authorised relationship index;
- reciprocal records;
- event subscriptions;
- public graph services.

A repository is not required to provide global reverse lookup.

For example, Bob’s repository need not efficiently list every public identity that follows Bob.

A separate indexer may provide that service.

---

## 41. Reverse relationships

A reverse relationship is an index-derived view.

Example:

```text
Who follows Bob?
```

The canonical records are distributed across follower repositories.

A reverse index may collect those records and expose a derived result.

The index should preserve:

- source Record URIs;
- observed versions;
- retrieval times;
- visibility status;
- deletion updates.

The reverse index is not the canonical owner of the relationships.

---

## 42. Relationship indexes

A relationship index may support:

- follower counts;
- mutual connections;
- organisation membership lookup;
- professional graph search;
- trust paths;
- community discovery.

Indexes may have incomplete coverage.

Applications should not imply that the absence of a relationship from one index proves it does not exist.

---

## 43. Event delivery

Relationship changes may generate events such as:

```text
follow-created
follow-ended
relationship-requested
relationship-accepted
relationship-revoked
membership-expired
block-created
credential-revoked
```

Event delivery must respect visibility and permission rules.

A private block event must not be broadcast to public indexers.

---

## 44. Relationship imports

A user may import relationships from an external platform.

Imported relationships must include provenance.

Example:

```json
{
  "provenance": {
    "method": "imported",
    "sourceService": "example-network",
    "importedAt": "2026-08-24T10:00:00Z"
  }
}
```

An imported username should not automatically be treated as a verified Relay Identity.

The importer may:

- match a verified external account to a Relay Identity;
- ask the user to confirm matches;
- retain unresolved external references;
- later upgrade the reference when verified.

---

## 45. Legacy external relationships

A relationship target may temporarily use an external identifier.

Example:

```json
{
  "target": {
    "type": "external",
    "service": "example-social-network",
    "identifier": "user_8821"
  }
}
```

This is less portable than a Relay target.

If the external account later verifies a Relay Identity, the relationship may be updated or linked without losing import provenance.

---

## 46. Relationship duplication

Multiple applications may attempt to create equivalent relationship records.

The repository should prevent accidental duplication where the schema defines one active relationship per source, target and context.

For example, Alice should not need five separate active follow records for Bob merely because five clients were used.

Application-specific metadata may be stored separately.

---

## 47. Relationship uniqueness

A relationship schema may define a uniqueness rule such as:

```text
One active follow from source to target.
```

or:

```text
One active membership per organisation, member and role.
```

The repository should enforce the schema’s uniqueness constraints.

Different relationship types or contexts may coexist.

---

## 48. Application-specific relationship metadata

Applications may maintain local metadata such as:

- custom labels;
- feed priority;
- display grouping;
- notification settings;
- private notes.

Portable metadata may be stored in a separate record owned by the user.

The core relationship should not be rewritten merely to satisfy one application’s interface.

---

## 49. Algorithms and relationships

Applications may use relationship records as inputs to:

- feeds;
- recommendations;
- search ranking;
- access decisions;
- trust calculations.

The relationship itself does not prescribe one algorithmic interpretation.

For example, following Bob may mean:

- show all posts;
- prioritise posts;
- include posts in a selected feed;
- permit notifications.

Those are client or subscription choices.

---

## 50. Relationship-based access

A record may grant access based on an active relationship.

Example:

```text
Visible to current collaborators.
```

The access system must define:

- which relationship type qualifies;
- whether the relationship must be reciprocal;
- which context applies;
- whether access is evaluated dynamically;
- what happens when the relationship ends.

Ending the relationship should revoke future access where the rule is dynamic.

---

## 51. Relationship-based permissions

A relationship must not automatically grant broad application authority.

For example:

```text
Alice is Bob’s colleague.
```

does not mean Alice may edit Bob’s repository.

Any authority must be explicitly declared within an authority-bearing relationship or Permission Grant.

Social meaning and technical authority must remain separate.

---

## 52. Provider migration

When a source or target moves Relay Provider:

- the Relay Identifier remains unchanged;
- the relationship Record URI remains unchanged;
- the Identity Document points to the new provider;
- applications resolve the new repository location;
- no follow, membership or collaboration needs to be recreated.

This is the key portability test for the Relationship Model.

---

## 53. Application replacement

When a user changes applications:

- the new application reads authorised relationship records;
- supported relationships continue operating;
- unsupported relationship types remain preserved;
- application-specific views may differ;
- no relationship is transferred into application ownership.

A new client may choose not to display every relationship type.

It must not delete or silently alter unsupported relationships.

---

## 54. Relationship schema governance

Relay should define a limited set of core relationship schemas.

Possible core schemas include:

```text
com.relay.relationship.follow.v1
com.relay.relationship.subscribe.v1
com.relay.relationship.block.v1
com.relay.relationship.mute.v1
com.relay.relationship.member.v1
com.relay.relationship.collaborator.v1
com.relay.relationship.trust.v1
com.relay.relationship.endorse.v1
```

Third parties may define additional schemas.

A custom schema must clearly define:

- semantics;
- direction;
- consent requirements;
- authority implications;
- lifecycle;
- privacy expectations.

---

## 55. Required v0.1 relationship operations

A compliant implementation must support:

```text
Create unilateral relationship
Read relationship
List relationships by type
Update relationship metadata
End relationship
Delete or tombstone relationship
Create relationship request
Accept relationship request
Decline relationship request
Link reciprocal relationship records
Verify relationship authority
Change relationship visibility
Add relationship context
Set expiration
Revoke authority-bearing relationship
Create block
Create mute
Import external relationship
Preserve unknown relationship schemas
Resolve target identity
```

Advanced encrypted graph operations may remain outside the first reference implementation.

---

## 56. Relationship invariants

The following rules must always remain true.

### Invariant 1

A relationship declaration belongs to the identity that authorised it.

### Invariant 2

Changing applications does not change the source or target Relay Identifier.

### Invariant 3

Changing Relay Provider does not require recreating the relationship.

### Invariant 4

A unilateral relationship must not be presented as mutual consent.

### Invariant 5

A reciprocal relationship requires independent authority from each participating identity.

### Invariant 6

One identity cannot rewrite another identity’s relationship record.

### Invariant 7

A relationship label does not imply technical authority unless authority is explicitly defined.

### Invariant 8

Private relationships must not become public merely because an application indexes the graph.

### Invariant 9

A derived follower count is not the canonical relationship graph.

### Invariant 10

An application does not own a relationship merely because it introduced the participants.

### Invariant 11

A released handle must not redirect historical relationships to a new identity.

### Invariant 12

A self-declared relationship must not be represented as externally verified.

### Invariant 13

Ending a relationship does not permit falsification of its historical existence.

### Invariant 14

Blocks and mutes are not protocol-level deletion or identity suspension.

---

## 57. Compliance scenario

A basic relationship implementation should pass the following test.

### Initial follow

Alice uses Application A to follow Bob.

Application A creates a follow record in Alice’s repository:

```text
relay://rid:relay:alice/com.relay.relationship/follow_123
```

Bob’s Relay Identifier is the target.

### Application replacement

Alice stops using Application A and opens Application B.

Application B receives permission to read Alice’s follow records.

Bob appears in Alice’s following list without Alice following him again.

### Provider migration

Alice moves her repository from Provider A to Provider B.

The follow Record URI and Bob’s target identifier remain unchanged.

Application B resolves Alice’s new repository and continues displaying the relationship.

### Reciprocal collaboration

Alice proposes a collaboration with Bob.

Bob accepts through a different application.

Alice and Bob each create independently authorised linked records.

Neither application owns the collaboration.

### Relationship termination

Bob ends his side of the collaboration.

The mutual relationship becomes inactive.

Alice cannot rewrite Bob’s record to make it appear active.

### Private block

Alice blocks another identity.

The block affects authorised applications but is not exposed publicly or to the blocked identity.

If these actions occur without binding the relationships to one application or provider, the implementation satisfies the basic Relay Relationship objective.

---

## 58. Open design questions

### 58.1 Distributed graph indexing

How should public reverse relationships be indexed efficiently without creating one indispensable global graph owner?

### 58.2 Reciprocal activation

Should reciprocal relationships become active through linked records, a shared transaction or an external coordination service?

### 58.3 Private graph encryption

How should private relationship records remain portable while preventing providers and indexers from learning the graph?

### 58.4 Dynamic audiences

How should relationship-based access be evaluated efficiently and revoked promptly?

### 58.5 Relationship requests

Should requests be repository records, direct protocol messages or both?

### 58.6 Authority relationships

Which authority-bearing relationships belong in the Relationship Model, and which should instead use Permission Grants or credentials?

### 58.7 Identity recovery

What happens to trusted-contact and guardian relationships when an identity recovery occurs?

### 58.8 Historical mutuality

How should applications represent a relationship that was once reciprocal but is now active on only one side?

### 58.9 External identity matching

What evidence is sufficient to connect an imported external account with a Relay Identity?

### 58.10 Schema conflicts

How should applications handle two schemas that use similar labels but define materially different relationship meanings?

---

## 59. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- relationships are Relay Records;
- the declaring identity stores its own canonical relationship record;
- unilateral and reciprocal relationships are distinct;
- reciprocal relationships use independently authorised linked records;
- stable Relay Identifiers are used as source and target;
- follows and subscriptions survive application and provider changes;
- public reverse graph queries are provided by optional indexes;
- visibility may be public, unlisted, restricted or private;
- private relationships require explicit access controls;
- authority-bearing relationships must define exact capabilities;
- self-declared, reciprocally confirmed and externally verified relationships are distinguishable;
- follower counts and reputation are derived values;
- blocks and mutes are normally private;
- unknown relationship schemas must survive migration;
- advanced end-to-end encrypted graph privacy may be deferred beyond the first reference implementation.

---

## 60. Core relationship principle

The Relationship Model can be reduced to one rule:

> A relationship exists between persistent identities, not inside the application that happened to introduce them.

The next core object is the **Relay Migration and Portability Model**: how identities, repositories, records, blobs, grants and relationships move between providers without breaking continuity.