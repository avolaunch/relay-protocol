# REM-05 Part 8 — Relationship Requirement Extraction Matrix (Sections 36–40)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 36–40 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

36. Trust relationships
37. Endorsements
38. Reputation as a derived layer
39. Relationship privacy risks
40. Relationship discovery

Requirement identifiers continue sequentially from Part 7, beginning with `REM-05-400`.

---

# 36. Trust relationships

## REM-05-400 — Trust relationship definition

**Source**  
Section 36: “A trust relationship expresses that the source chooses to rely on the target for a defined purpose.”

**Requirement**  
A Relay trust relationship MUST represent an attributable choice by the source identity to rely on a target for a defined purpose.

**Classification**  
Relationship semantics; trust; source authority.

**Notes**  
Trust is a declaration by the source. It is not an objective or universal assessment of the target.

---

## REM-05-401 — Trust target may be an identity

**Source**  
Section 36 example: “Trust this identity for photography recommendations.”

**Requirement**  
A trust relationship MUST be capable of targeting a Relay Identity.

**Classification**  
Trust target; identity relationship.

**Notes**  
The purpose for which the identity is trusted must remain explicit.

---

## REM-05-402 — Trust target may be a service

**Source**  
Section 36 example: “Trust this service for moderation labels.”

**Requirement**  
A trust relationship MUST be capable of targeting a service used for a defined function.

**Classification**  
Trust target; service relationship.

**Notes**  
Trust in a service for one function does not imply trust in all outputs or activities of that service.

---

## REM-05-403 — Trust target may be an organisation

**Source**  
Section 36 example: “Trust this organisation to verify qualifications.”

**Requirement**  
A trust relationship MUST be capable of targeting an organisation for a defined verification or reliance purpose.

**Classification**  
Trust target; organisational relationship.

**Notes**  
The relationship should identify the organisation through a stable identifier wherever possible.

---

## REM-05-404 — Trust must always be scoped

**Source**  
Section 36: “Trust must always be scoped.”

**Requirement**  
Every trust relationship MUST define the scope within which the source relies on the target.

**Classification**  
Core invariant; trust scope; least authority.

**Notes**  
An unqualified declaration of universal trust is not sufficient for compliant interpretation.

---

## REM-05-405 — Trust scope must identify purpose

**Source**  
Section 36 example context: `"purpose": "moderation-labels"`.

**Requirement**  
A trust relationship’s context MUST be capable of identifying the purpose for which trust is granted.

**Classification**  
Trust context; purpose limitation.

**Notes**  
Purpose provides the primary semantic boundary of the trust declaration.

---

## REM-05-406 — Trust scope may identify categories

**Source**  
Section 36 example context categories: `"spam"` and `"malware"`.

**Requirement**  
A trust relationship MUST support further limitation by categories relevant to the declared purpose.

**Classification**  
Trust context; category scope.

**Notes**  
Category restrictions allow an identity to trust the same service for some judgements but not others.

---

## REM-05-407 — Narrow trust must not produce universal trust

**Source**  
Section 36: “A general universal trust score should not be inferred from a narrow trust relationship.”

**Requirement**  
An application or derived service MUST NOT infer or present a general universal trust score from a trust relationship limited to a particular purpose, category or context.

**Classification**  
Inference limitation; trust integrity; derived data.

**Notes**  
This prevents context-specific reliance from being transformed into a broad reputation claim.

---

# 37. Endorsements

## REM-05-408 — Endorsement definition

**Source**  
Section 37: “An endorsement is a directed assertion expressing support for a person, record, skill or claim.”

**Requirement**  
A Relay endorsement MUST be represented as a directed assertion by an endorsing identity expressing support for a defined target or subject.

**Classification**  
Relationship semantics; endorsement; directed assertion.

**Notes**  
An endorsement is attributable to the endorser and does not become a statement authored by the target.

---

## REM-05-409 — Endorsement may support a person

**Source**  
Section 37: “support for a person”.

**Requirement**  
An endorsement MUST be capable of targeting a person represented by a Relay Identity.

**Classification**  
Endorsement target; identity.

**Notes**  
The endorsement should still identify the specific subject or context of support where applicable.

---

## REM-05-410 — Endorsement may support a record

**Source**  
Section 37: “support for a … record”.

**Requirement**  
An endorsement MUST be capable of targeting a specific Relay Record.

**Classification**  
Endorsement target; record.

**Notes**  
A stable Record URI should be used for the target where available.

---

## REM-05-411 — Endorsement may support a skill

**Source**  
Section 37: “support for a … skill”.

**Requirement**  
An endorsement MUST be capable of expressing support for a defined skill associated with the target.

**Classification**  
Endorsement subject; skill.

**Notes**  
The skill should be represented in the endorsement subject or context rather than inferred from an unqualified endorsement.

---

## REM-05-412 — Endorsement may support a claim

**Source**  
Section 37: “support for a … claim”.

**Requirement**  
An endorsement MUST be capable of targeting or supporting a defined claim.

**Classification**  
Endorsement subject; claim.

**Notes**  
Supporting a claim does not by itself verify that the claim is factually true.

---

## REM-05-413 — Endorsement must identify endorser

**Source**  
Section 37: “An endorsement should identify: endorser”.

**Requirement**  
An endorsement SHOULD identify the identity responsible for issuing the endorsement.

**Classification**  
Attribution; endorsement provenance.

**Notes**  
Without an attributable endorser, the assertion cannot be independently evaluated or revoked by its source.

---

## REM-05-414 — Endorsement must identify target

**Source**  
Section 37: “An endorsement should identify: target”.

**Requirement**  
An endorsement SHOULD identify the person, record, skill-bearing identity or claim being endorsed.

**Classification**  
Target identification; endorsement structure.

**Notes**  
Stable Relay identifiers or Record URIs should be preferred over provider-specific handles or URLs.

---

## REM-05-415 — Endorsement must identify subject

**Source**  
Section 37: “An endorsement should identify: subject”.

**Requirement**  
An endorsement SHOULD identify the subject for which support is being expressed.

**Classification**  
Semantic scope; endorsement subject.

**Notes**  
The subject prevents a narrow endorsement from being interpreted as broad approval of the target.

---

## REM-05-416 — Endorsement must identify context

**Source**  
Section 37: “An endorsement should identify: context”.

**Requirement**  
An endorsement SHOULD identify relevant context that limits or explains the assertion.

**Classification**  
Context; endorsement interpretation.

**Notes**  
Context may include a project, role, period, domain or other relationship boundary.

---

## REM-05-417 — Endorsement must identify date

**Source**  
Section 37: “An endorsement should identify: date”.

**Requirement**  
An endorsement SHOULD identify the date or time at which it was issued.

**Classification**  
Temporal metadata; endorsement provenance.

**Notes**  
Applications should avoid presenting old endorsements as current without appropriate temporal context.

---

## REM-05-418 — Endorsement must identify visibility

**Source**  
Section 37: “An endorsement should identify: visibility”.

**Requirement**  
An endorsement SHOULD define its visibility or access classification.

**Classification**  
Visibility; access control; endorsement privacy.

**Notes**  
The fact that an endorsement exists does not require it to be publicly discoverable.

---

## REM-05-419 — Endorsement must indicate evidence inclusion

**Source**  
Section 37: “An endorsement should identify … whether evidence is included.”

**Requirement**  
An endorsement SHOULD indicate whether supporting evidence accompanies or is referenced by the assertion.

**Classification**  
Evidence; endorsement provenance.

**Notes**  
The presence of evidence should not be confused with independent verification unless the evidence and verifier support that conclusion.

---

## REM-05-420 — Endorsement context may identify a specific subject

**Source**  
Section 37 example: `"subject": "software-architecture"`.

**Requirement**  
An endorsement’s context MUST be capable of identifying a specific subject such as a skill or professional domain.

**Classification**  
Endorsement context; semantic precision.

**Notes**  
The example demonstrates that endorsement meaning should not depend on a generic label alone.

---

## REM-05-421 — Endorsement remains controlled by endorser

**Source**  
Section 37: “Endorsements remain controlled by the endorsing identity.”

**Requirement**  
The endorsing identity MUST retain control over its endorsement declaration.

**Classification**  
Relationship ownership; source control.

**Notes**  
Control includes the ability to revise, revoke or otherwise manage the endorsement according to the applicable record and schema rules.

---

## REM-05-422 — Target cannot rewrite endorsement

**Source**  
Section 37: “The target cannot rewrite … them.”

**Requirement**  
The target of an endorsement MUST NOT be permitted to rewrite the endorser’s endorsement record or assertion.

**Classification**  
Integrity; independent authority; relationship ownership.

**Notes**  
The target may create a separate response or counter-record where supported but cannot alter the source declaration.

---

## REM-05-423 — Target cannot fabricate endorsement

**Source**  
Section 37: “The target cannot … fabricate them.”

**Requirement**  
The target of an endorsement MUST NOT be able to create an endorsement falsely attributed to another identity.

**Classification**  
Forgery prevention; attribution integrity.

**Notes**  
Signature and authority validation should ensure that the stated endorser actually authorised the assertion.

---

# 38. Reputation as a derived layer

## REM-05-424 — No universal reputation score in Relay v0.1

**Source**  
Section 38: “Relay v0.1 should not define a universal reputation score.”

**Requirement**  
Relay v0.1 SHOULD NOT define or mandate a universal reputation score applicable across identities, applications or contexts.

**Classification**  
Protocol scope; reputation; anti-centralisation.

**Notes**  
Applications may calculate contextual reputation, but the protocol does not establish one authoritative universal score.

---

## REM-05-425 — Reputation may derive from relationships

**Source**  
Section 38: “Reputation may be derived from: relationships”.

**Requirement**  
A reputation service MAY use relationship records as one input to a derived reputation result.

**Classification**  
Derived data; reputation input.

**Notes**  
Use of relationship records remains subject to visibility and permission rules.

---

## REM-05-426 — Reputation may derive from credentials

**Source**  
Section 38: “Reputation may be derived from: credentials”.

**Requirement**  
A reputation service MAY use credentials as an input to a derived reputation result.

**Classification**  
Derived data; credential input.

**Notes**  
The service should account for credential scope, issuer, validity and revocation status.

---

## REM-05-427 — Reputation may derive from endorsements

**Source**  
Section 38: “Reputation may be derived from: endorsements”.

**Requirement**  
A reputation service MAY use endorsements as an input to a derived reputation result.

**Classification**  
Derived data; endorsement input.

**Notes**  
Endorsements remain independent source-controlled records even when used in a derived calculation.

---

## REM-05-428 — Reputation may derive from activity

**Source**  
Section 38: “Reputation may be derived from: activity”.

**Requirement**  
A reputation service MAY use attributable activity as an input to a derived reputation result.

**Classification**  
Derived data; activity input.

**Notes**  
The service should disclose which activity categories were considered and any coverage limitations.

---

## REM-05-429 — Reputation may derive from moderation labels

**Source**  
Section 38: “Reputation may be derived from: moderation labels”.

**Requirement**  
A reputation service MAY use moderation labels as an input to a derived reputation result.

**Classification**  
Derived data; moderation input.

**Notes**  
The issuer, category, status and context of labels should remain distinguishable from the derived score.

---

## REM-05-430 — Reputation may derive from application-specific behaviour

**Source**  
Section 38: “Reputation may be derived from: application-specific behaviour”.

**Requirement**  
An application MAY incorporate behaviour observed within its own defined context into a reputation result.

**Classification**  
Application-specific derivation; reputation input.

**Notes**  
Application-specific behaviour must not be presented as complete ecosystem-wide behaviour.

---

## REM-05-431 — Reputation may derive from community participation

**Source**  
Section 38: “Reputation may be derived from: community participation”.

**Requirement**  
A reputation service MAY use attributable community participation as an input to a contextual reputation result.

**Classification**  
Derived data; participation input.

**Notes**  
The relevant community and the basis of evaluation should be identified.

---

## REM-05-432 — Applications may calculate reputation differently

**Source**  
Section 38: “Different applications may calculate reputation differently.”

**Requirement**  
The protocol MUST permit different applications or services to calculate reputation using different methodologies and inputs.

**Classification**  
Application autonomy; derived services; methodological plurality.

**Notes**  
A result from one service must not be treated as the protocol’s canonical reputation assessment.

---

## REM-05-433 — Reputation result must identify producing service

**Source**  
Section 38: “Any reputation result must identify: the service producing it”.

**Requirement**  
Every derived reputation result MUST identify the application or service that produced it.

**Classification**  
Attribution; derived result provenance.

**Notes**  
The producing service is responsible for its methodology and presentation.

---

## REM-05-434 — Reputation result must identify source inputs

**Source**  
Section 38: “Any reputation result must identify: source inputs”.

**Requirement**  
Every derived reputation result MUST identify the source inputs or input categories used in its calculation.

**Classification**  
Transparency; derived result provenance.

**Notes**  
This does not require disclosure of private data to unauthorised viewers; an appropriately generalised description may be necessary.

---

## REM-05-435 — Reputation result must identify context

**Source**  
Section 38: “Any reputation result must identify: relevant context”.

**Requirement**  
Every derived reputation result MUST identify the context within which the result is intended to be interpreted.

**Classification**  
Context; reputation limitation.

**Notes**  
Context may include a community, activity type, professional domain, application or time period.

---

## REM-05-436 — Reputation result must identify calculation time

**Source**  
Section 38: “Any reputation result must identify: calculation time”.

**Requirement**  
Every derived reputation result MUST identify when it was calculated or last updated.

**Classification**  
Temporal metadata; result freshness.

**Notes**  
A calculation time helps prevent stale results from being presented as current.

---

## REM-05-437 — Reputation result must identify limitations

**Source**  
Section 38: “Any reputation result must identify: limitations.”

**Requirement**  
Every derived reputation result MUST disclose material limitations affecting its coverage, accuracy or interpretation.

**Classification**  
Transparency; uncertainty; derived result integrity.

**Notes**  
Limitations may include incomplete indexes, hidden relationships, stale data, narrow context or unavailable credentials.

---

## REM-05-438 — Relationship records remain separate from reputation score

**Source**  
Section 38: “The underlying relationship records remain separate from the derived score.”

**Requirement**  
A derived reputation result MUST remain a separate object or view from the underlying relationship records used to calculate it.

**Classification**  
Data separation; canonical records; derived layer.

**Notes**  
The score must not overwrite, replace or become the canonical owner of the source relationships.

---

# 39. Relationship privacy risks

## REM-05-439 — Portable graphs create material privacy risk

**Source**  
Section 39: “A portable graph may create serious privacy risks.”

**Requirement**  
Relay implementations MUST treat portable relationship graphs as potentially sensitive datasets requiring explicit privacy protections.

**Classification**  
Privacy; threat model; relationship graph.

**Notes**  
Portability increases user control but may also increase aggregation and correlation risks.

---

## REM-05-440 — Relationship data may reveal sensitive associations

**Source**  
Section 39: “Relationship data can reveal” political associations, health conditions, religious communities, family structures, workplaces, personal interests, private support networks and physical location.

**Requirement**  
Privacy and access-control design MUST account for the possibility that relationship records and graph-derived metadata reveal sensitive personal associations or attributes.

**Classification**  
Sensitive data; privacy risk; inference risk.

**Notes**  
A relationship may be sensitive even when neither endpoint record is independently classified as sensitive.

---

## REM-05-441 — Relationships must not be public by default

**Source**  
Section 39: “relationships must not all be public by default”.

**Requirement**  
Relay implementations MUST NOT apply public visibility as the universal default for all relationship records.

**Classification**  
Privacy by default; visibility.

**Notes**  
Defaults may vary by relationship schema, sensitivity and user choice.

---

## REM-05-442 — Private relationships should support encryption

**Source**  
Section 39: “private relationships should support encryption”.

**Requirement**  
Private relationship records SHOULD support encryption appropriate to their confidentiality requirements.

**Classification**  
Confidentiality; encryption; private relationships.

**Notes**  
Encryption design must still permit authorised resolution and lifecycle management.

---

## REM-05-443 — Indexes must respect relationship visibility

**Source**  
Section 39: “indexes should respect visibility”.

**Requirement**  
Relationship indexes SHOULD enforce the visibility and access classifications of the relationship records they observe.

**Classification**  
Index compliance; visibility; privacy.

**Notes**  
Indexing a record does not create authority to broaden its audience.

---

## REM-05-444 — Applications should request only necessary relationship access

**Source**  
Section 39: “applications should request only necessary relationship access”.

**Requirement**  
Applications SHOULD request the narrowest relationship access required for their declared functionality.

**Classification**  
Data minimisation; permissions; least privilege.

**Notes**  
Broad access to an entire relationship graph should not be requested when a smaller collection, type or context is sufficient.

---

## REM-05-445 — Exports must preserve access classifications

**Source**  
Section 39: “relationship exports must preserve access classifications”.

**Requirement**  
An export containing relationship records MUST preserve each record’s visibility and access classification metadata.

**Classification**  
Export integrity; privacy; portability.

**Notes**  
Export must not silently convert restricted or private relationships into public data.

---

## REM-05-446 — Private group membership must not leak through counts

**Source**  
Section 39: “private group membership should not leak through counts or metadata”.

**Requirement**  
Implementations SHOULD prevent private group membership from being inferred through publicly exposed counts.

**Classification**  
Inference prevention; group privacy.

**Notes**  
Small or changing counts may reveal individual membership even without displaying member identities.

---

## REM-05-447 — Private group membership must not leak through metadata

**Source**  
Section 39: “private group membership should not leak through counts or metadata”.

**Requirement**  
Implementations SHOULD prevent private group membership from being inferred through exposed metadata, identifiers, event patterns or related graph information.

**Classification**  
Metadata privacy; inference prevention.

**Notes**  
Protection must consider indirect disclosure rather than only direct member lists.

---

## REM-05-448 — Decentralisation does not guarantee privacy

**Source**  
Section 39: “A decentralised graph can become more invasive than a centralised one if privacy is poorly designed.”

**Requirement**  
Relay privacy design MUST NOT assume that decentralisation or portability alone protects relationship data from surveillance, aggregation or inference.

**Classification**  
Privacy principle; decentralised systems; threat model.

**Notes**  
Privacy protections must be explicit at the record, index, application, export and event layers.

---

# 40. Relationship discovery

## REM-05-449 — Discovery through source repository

**Source**  
Section 40: “Applications may discover relationships through: the source repository”.

**Requirement**  
Applications MAY discover relationship records by resolving and querying the source identity’s repository where visibility and permission rules allow.

**Classification**  
Discovery; source repository.

**Notes**  
The source repository remains the canonical location of the source identity’s declaration.

---

## REM-05-450 — Discovery through authorised relationship index

**Source**  
Section 40: “Applications may discover relationships through: an authorised relationship index”.

**Requirement**  
Applications MAY discover relationship information through a relationship index that is authorised to process and expose the relevant records.

**Classification**  
Discovery; index service; authorisation.

**Notes**  
Index results remain derived and may be incomplete or stale.

---

## REM-05-451 — Discovery through reciprocal records

**Source**  
Section 40: “Applications may discover relationships through: reciprocal records”.

**Requirement**  
Applications MAY use authorised reciprocal record references to discover the independently controlled declarations participating in a reciprocal relationship.

**Classification**  
Discovery; reciprocal relationships; record linkage.

**Notes**  
A reciprocal reference does not give either party control over the other party’s record.

---

## REM-05-452 — Discovery through event subscriptions

**Source**  
Section 40: “Applications may discover relationships through: event subscriptions”.

**Requirement**  
Applications MAY discover relationship creation, modification or termination through authorised event subscriptions.

**Classification**  
Discovery; events; synchronisation.

**Notes**  
Event delivery must remain subject to relationship visibility and application permission rules.

---

## REM-05-453 — Discovery through public graph services

**Source**  
Section 40: “Applications may discover relationships through: public graph services.”

**Requirement**  
Applications MAY discover publicly accessible relationship information through public graph services.

**Classification**  
Discovery; public graph; derived service.

**Notes**  
A public graph service is not the canonical owner of the underlying relationship records.

---

## REM-05-454 — Repository need not provide global reverse lookup

**Source**  
Section 40: “A repository is not required to provide global reverse lookup.”

**Requirement**  
A Relay Repository MUST NOT be considered non-compliant merely because it does not provide a global reverse-relationship lookup service.

**Classification**  
Repository scope; discovery limitation; reverse lookup.

**Notes**  
The repository’s primary obligation is to serve records it controls according to protocol and access rules, not to index declarations stored across the ecosystem.

---

## REM-05-455 — Target repository need not enumerate all followers

**Source**  
Section 40: “Bob’s repository need not efficiently list every public identity that follows Bob.”

**Requirement**  
A target identity’s repository MUST NOT be required to enumerate every external identity whose separate repository contains a relationship directed at that target.

**Classification**  
Distributed graph; reverse lookup; repository responsibility.

**Notes**  
Follower declarations are canonically distributed across follower repositories rather than owned by the target repository.

---

## REM-05-456 — Separate indexer may provide reverse discovery

**Source**  
Section 40: “A separate indexer may provide that service.”

**Requirement**  
A separate indexer MAY provide global or reverse relationship-discovery services that individual repositories are not required to provide.

**Classification**  
Indexer role; reverse discovery; ecosystem service.

**Notes**  
The indexer must respect visibility, deletion, revocation and freshness constraints and must not claim canonical ownership.

---

## REM-05-457 — Discovery path does not alter canonical ownership

**Source**  
Section 40’s distinction among source repositories, indexes, reciprocal records, event subscriptions and public graph services.

**Requirement**  
The mechanism through which an application discovers a relationship MUST NOT alter which repository or identity is the canonical source of the underlying relationship declaration.

**Classification**  
Canonical authority; discovery integrity; portability.

**Notes**  
Discovery services provide access paths or derived views; they do not transfer ownership of relationship records.
