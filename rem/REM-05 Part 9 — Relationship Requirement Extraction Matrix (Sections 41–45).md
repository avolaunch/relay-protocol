# REM-05 Part 9 — Relationship Requirement Extraction Matrix (Sections 41–45)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 41–45 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

41. Reverse relationships
42. Relationship indexes
43. Event delivery
44. Relationship imports
45. Legacy external relationships

Requirement identifiers continue sequentially from Part 8, beginning with `REM-05-458`.

---

# 41. Reverse relationships

## REM-05-458 — Reverse relationships are derived views

**Source**  
Section 41: “A reverse relationship is an index-derived view.”

**Requirement**  
A Relay implementation MUST treat a reverse relationship view as a derived index result rather than as an independently authoritative relationship declaration.

**Classification**  
Derived data; indexing; relationship authority.

**Notes**  
A query such as “Who follows Bob?” is answered from records distributed across source repositories and does not create a new canonical relationship record in Bob’s repository.

---

## REM-05-459 — Reverse relationship queries may identify incoming relationships

**Source**  
Section 41 example: “Who follows Bob?”

**Requirement**  
A relationship index MAY expose reverse queries that identify relationship records whose targets match a specified identity, record or entity.

**Classification**  
Discovery; reverse lookup; index service.

**Notes**  
Support for reverse lookup is an index capability and is not required of the target repository itself.

---

## REM-05-460 — Canonical reverse-query records remain distributed

**Source**  
Section 41: “The canonical records are distributed across follower repositories.”

**Requirement**  
For a reverse relationship result, the canonical relationship records MUST remain the records controlled by their respective source repositories.

**Classification**  
Canonical authority; distributed graph; provenance.

**Notes**  
The index aggregates references to those records; it does not relocate or assume ownership of them.

---

## REM-05-461 — Reverse indexes may aggregate canonical records

**Source**  
Section 41: “A reverse index may collect those records and expose a derived result.”

**Requirement**  
A reverse index MAY collect discoverable relationship records and expose an aggregated result derived from those records.

**Classification**  
Indexing; aggregation; derived service.

**Notes**  
Collection remains subject to the records’ visibility, access and permission rules.

---

## REM-05-462 — Reverse indexes preserve source Record URIs

**Source**  
Section 41: “The index should preserve: source Record URIs.”

**Requirement**  
A reverse relationship index SHOULD preserve the source Record URI for every indexed relationship result.

**Classification**  
Traceability; source attribution; index integrity.

**Notes**  
The Record URI allows a consumer to resolve or verify the originating record rather than relying solely on the index copy.

---

## REM-05-463 — Reverse indexes preserve observed versions

**Source**  
Section 41: “The index should preserve: observed versions.”

**Requirement**  
A reverse relationship index SHOULD record the version of each relationship record that it observed.

**Classification**  
Version traceability; index freshness; verification.

**Notes**  
This supports detection of stale, superseded or changed index entries.

---

## REM-05-464 — Reverse indexes preserve retrieval times

**Source**  
Section 41: “The index should preserve: retrieval times.”

**Requirement**  
A reverse relationship index SHOULD record when each indexed relationship record was retrieved or last refreshed.

**Classification**  
Freshness metadata; auditability; indexing.

**Notes**  
Retrieval time helps applications qualify the currency of a derived result.

---

## REM-05-465 — Reverse indexes preserve visibility status

**Source**  
Section 41: “The index should preserve: visibility status.”

**Requirement**  
A reverse relationship index SHOULD preserve and enforce the visibility status applicable to each indexed relationship record.

**Classification**  
Privacy; visibility enforcement; indexing.

**Notes**  
Indexing a record must not convert restricted or private information into public graph data.

---

## REM-05-466 — Reverse indexes process deletion updates

**Source**  
Section 41: “The index should preserve: deletion updates.”

**Requirement**  
A reverse relationship index SHOULD process and retain sufficient deletion-update state to stop presenting relationship records that are no longer validly available.

**Classification**  
Deletion propagation; index maintenance; graph accuracy.

**Notes**  
Historical or audit retention, where permitted, must remain distinct from presenting the relationship as currently active.

---

## REM-05-467 — Reverse indexes are not canonical owners

**Source**  
Section 41: “The reverse index is not the canonical owner of the relationships.”

**Requirement**  
A reverse relationship index MUST NOT represent itself as the canonical owner or authoritative origin of the relationship records it indexes.

**Classification**  
Ownership boundary; canonical authority; index integrity.

**Notes**  
The source identity’s repository remains authoritative for the source identity’s declaration.

---

# 42. Relationship indexes

## REM-05-468 — Relationship indexes may provide follower counts

**Source**  
Section 42: “A relationship index may support: follower counts.”

**Requirement**  
A relationship index MAY calculate and expose follower counts from the relationship records within its authorised and discoverable coverage.

**Classification**  
Derived metric; indexing; follower graph.

**Notes**  
Any count remains subject to coverage, freshness, visibility and deletion limitations.

---

## REM-05-469 — Relationship indexes may identify mutual connections

**Source**  
Section 42: “A relationship index may support: mutual connections.”

**Requirement**  
A relationship index MAY derive mutual-connection views from compatible relationship records.

**Classification**  
Graph derivation; relationship discovery; indexing.

**Notes**  
A mutual view must preserve the independent authority and status of the underlying declarations.

---

## REM-05-470 — Relationship indexes may support membership lookup

**Source**  
Section 42: “A relationship index may support: organisation membership lookup.”

**Requirement**  
A relationship index MAY support organisation-membership lookup where the relevant membership records are visible and indexable.

**Classification**  
Membership discovery; indexing; organisation graph.

**Notes**  
Private or restricted membership must not be exposed merely because the index supports this query type.

---

## REM-05-471 — Relationship indexes may support professional graph search

**Source**  
Section 42: “A relationship index may support: professional graph search.”

**Requirement**  
A relationship index MAY provide professional graph search derived from relationship records, credentials and permitted contextual information.

**Classification**  
Search; professional graph; derived service.

**Notes**  
Search results must preserve evidentiary distinctions such as self-declared, credential-backed and disputed relationships.

---

## REM-05-472 — Relationship indexes may derive trust paths

**Source**  
Section 42: “A relationship index may support: trust paths.”

**Requirement**  
A relationship index MAY derive trust paths from compatible, purpose-scoped trust relationship records.

**Classification**  
Trust graph; derivation; indexing.

**Notes**  
A derived path must not broaden the purpose or scope of the underlying trust declarations.

---

## REM-05-473 — Relationship indexes may support community discovery

**Source**  
Section 42: “A relationship index may support: community discovery.”

**Requirement**  
A relationship index MAY support community discovery using relationship and membership records that are authorised for that purpose.

**Classification**  
Discovery; community graph; indexing.

**Notes**  
Sensitive or private group membership must not leak through discovery results, counts or metadata.

---

## REM-05-474 — Relationship indexes may have incomplete coverage

**Source**  
Section 42: “Indexes may have incomplete coverage.”

**Requirement**  
Relationship index results MUST be designed and presented on the assumption that index coverage may be incomplete.

**Classification**  
Coverage limitation; derived data; user-interface accuracy.

**Notes**  
Incomplete coverage may arise from inaccessible repositories, private records, indexing delays, blocks, revocations or service scope.

---

## REM-05-475 — Index absence does not prove relationship nonexistence

**Source**  
Section 42: “Applications should not imply that the absence of a relationship from one index proves it does not exist.”

**Requirement**  
An application SHOULD NOT represent the absence of a relationship from a particular index as proof that no such relationship exists.

**Classification**  
Inference limitation; index completeness; presentation accuracy.

**Notes**  
The correct interpretation is that the selected index has no qualifying record within its current coverage and state.

---

## REM-05-476 — Index results identify their derived nature

**Source**  
Sections 41–42: reverse relationships are index-derived, and indexes may have incomplete coverage.

**Requirement**  
An application presenting relationship-index results SHOULD identify that the result is derived and, where material, disclose the index or service that produced it.

**Classification**  
Transparency; derived results; attribution.

**Notes**  
This avoids confusing an index response with a canonical repository assertion.

---

# 43. Event delivery

## REM-05-477 — Relationship changes may generate events

**Source**  
Section 43: “Relationship changes may generate events.”

**Requirement**  
A Relay implementation MAY generate events when relationship records or their effective states change.

**Classification**  
Event model; relationship lifecycle; synchronisation.

**Notes**  
Event generation does not change the canonical status of the underlying relationship record.

---

## REM-05-478 — Follow creation event

**Source**  
Section 43 event list: `follow-created`.

**Requirement**  
An implementation MAY emit a `follow-created` event when a follow relationship becomes validly active.

**Classification**  
Event type; follow lifecycle; notification.

**Notes**  
Delivery remains subject to the visibility and permission rules governing the follow record.

---

## REM-05-479 — Follow ending event

**Source**  
Section 43 event list: `follow-ended`.

**Requirement**  
An implementation MAY emit a `follow-ended` event when an active follow relationship ends.

**Classification**  
Event type; follow lifecycle; synchronisation.

**Notes**  
Consumers should update derived views without treating the event as authority to erase unrelated historical audit data.

---

## REM-05-480 — Relationship request event

**Source**  
Section 43 event list: `relationship-requested`.

**Requirement**  
An implementation MAY emit a `relationship-requested` event when a consent-based relationship request is validly submitted.

**Classification**  
Event type; relationship request; workflow.

**Notes**  
The event must not imply that the requested relationship is active or accepted.

---

## REM-05-481 — Relationship acceptance event

**Source**  
Section 43 event list: `relationship-accepted`.

**Requirement**  
An implementation MAY emit a `relationship-accepted` event when the relevant identity independently authorises acceptance.

**Classification**  
Event type; acceptance; reciprocal relationship.

**Notes**  
The relationship becomes operational only when all schema-defined activation conditions are satisfied.

---

## REM-05-482 — Relationship revocation event

**Source**  
Section 43 event list: `relationship-revoked`.

**Requirement**  
An implementation MAY emit a `relationship-revoked` event when relationship authority is validly revoked.

**Classification**  
Event type; revocation; authority lifecycle.

**Notes**  
After revocation, new authority-dependent actions must be rejected as required by the relationship schema.

---

## REM-05-483 — Membership expiration event

**Source**  
Section 43 event list: `membership-expired`.

**Requirement**  
An implementation MAY emit a `membership-expired` event when a membership passes its valid expiration point.

**Classification**  
Event type; membership lifecycle; expiration.

**Notes**  
The expired membership may remain historically verifiable while no longer producing current membership effects.

---

## REM-05-484 — Block creation event

**Source**  
Section 43 event list: `block-created`.

**Requirement**  
An implementation MAY generate a `block-created` event for authorised internal enforcement and synchronisation.

**Classification**  
Event type; safety control; privacy-sensitive event.

**Notes**  
Because blocks are normally private, the event requires particularly strict delivery controls.

---

## REM-05-485 — Credential revocation event

**Source**  
Section 43 event list: `credential-revoked`.

**Requirement**  
An implementation MAY emit or consume a `credential-revoked` event where credential revocation affects a relationship’s evidence, status or authority.

**Classification**  
Event type; credential evidence; relationship verification.

**Notes**  
The event may require applications to recalculate whether a relationship remains verified or authority-bearing.

---

## REM-05-486 — Event delivery respects visibility

**Source**  
Section 43: “Event delivery must respect visibility and permission rules.”

**Requirement**  
Relationship event delivery MUST enforce the visibility rules applicable to the underlying relationship and event data.

**Classification**  
Privacy; event delivery; access control.

**Notes**  
The existence, type, target, context or evidence of a relationship may each have different disclosure restrictions.

---

## REM-05-487 — Event delivery respects permissions

**Source**  
Section 43: “Event delivery must respect visibility and permission rules.”

**Requirement**  
A relationship event MUST NOT be delivered to an application, index or subscriber that lacks the permission or public-access basis required to receive it.

**Classification**  
Authorisation; event delivery; permission enforcement.

**Notes**  
Subscription to an event channel does not independently confer access to protected relationship data.

---

## REM-05-488 — Private block events are not publicly broadcast

**Source**  
Section 43: “A private block event must not be broadcast to public indexers.”

**Requirement**  
A private block event MUST NOT be broadcast or otherwise disclosed to a public relationship indexer.

**Classification**  
Privacy invariant; block confidentiality; event routing.

**Notes**  
Internal providers or applications may receive only the minimum information needed to enforce the block under valid authority.

---

# 44. Relationship imports

## REM-05-489 — Users may import external relationships

**Source**  
Section 44: “A user may import relationships from an external platform.”

**Requirement**  
A Relay implementation MAY allow a user to import relationship data from an external platform.

**Classification**  
Import; portability; external relationship data.

**Notes**  
An import creates or stages Relay records or references under the importing identity’s authority; it does not make the external platform authoritative for Relay state.

---

## REM-05-490 — Imported relationships include provenance

**Source**  
Section 44: “Imported relationships must include provenance.”

**Requirement**  
Every imported relationship MUST include provenance identifying that the relationship originated through an import process.

**Classification**  
Provenance; import integrity; traceability.

**Notes**  
Imported data must remain distinguishable from relationships established natively through Relay authorisation.

---

## REM-05-491 — Import provenance records the method

**Source**  
Section 44 example: `"method": "imported"`.

**Requirement**  
Imported relationship provenance MUST identify the provenance method as imported or an equivalent machine-readable import classification.

**Classification**  
Provenance field; import classification; machine readability.

**Notes**  
This supports consistent interpretation across applications and later editorial or compliance review.

---

## REM-05-492 — Import provenance identifies the source service

**Source**  
Section 44 example: `"sourceService": "example-network"`.

**Requirement**  
Imported relationship provenance MUST identify the external service from which the relationship data was imported where that service is known.

**Classification**  
Source attribution; import provenance; external service.

**Notes**  
A stable service identifier should be used where available.

---

## REM-05-493 — Import provenance records import time

**Source**  
Section 44 example: `"importedAt": "2026-08-24T10:00:00Z"`.

**Requirement**  
Imported relationship provenance MUST record when the import occurred.

**Classification**  
Timestamp; import provenance; auditability.

**Notes**  
Import time is distinct from any original relationship creation date supplied by the external platform.

---

## REM-05-494 — Imported usernames are not automatically verified Relay identities

**Source**  
Section 44: “An imported username should not automatically be treated as a verified Relay Identity.”

**Requirement**  
An importer SHOULD NOT treat an imported username, handle or external identifier as a verified match to a Relay Identity without an appropriate verification basis.

**Classification**  
Identity matching; verification; import safety.

**Notes**  
Visible-name similarity or possession of an exported username list is insufficient verification.

---

## REM-05-495 — Importers may match verified external accounts

**Source**  
Section 44: “The importer may: match a verified external account to a Relay Identity.”

**Requirement**  
An importer MAY link an external relationship target to a Relay Identity when the external account has been validly verified as belonging to that Relay Identity.

**Classification**  
Identity resolution; verified matching; import upgrade.

**Notes**  
The verification method and scope should remain traceable.

---

## REM-05-496 — Importers may request user confirmation of matches

**Source**  
Section 44: “The importer may: ask the user to confirm matches.”

**Requirement**  
An importer MAY ask the importing user to confirm proposed matches between external identifiers and Relay Identities.

**Classification**  
User confirmation; identity matching; import workflow.

**Notes**  
User confirmation is a statement by the importer’s user and should not automatically be represented as independent verification by the target identity.

---

## REM-05-497 — Importers may retain unresolved external references

**Source**  
Section 44: “The importer may: retain unresolved external references.”

**Requirement**  
An importer MAY retain an unresolved external relationship reference when no verified Relay Identity match is available.

**Classification**  
Legacy reference; unresolved identity; import continuity.

**Notes**  
The reference must remain explicitly typed as external or unresolved.

---

## REM-05-498 — Imported references may later be upgraded

**Source**  
Section 44: “The importer may: later upgrade the reference when verified.”

**Requirement**  
An importer MAY later link or upgrade an unresolved external reference when a verified Relay Identity match becomes available.

**Classification**  
Reference upgrade; identity resolution; lifecycle.

**Notes**  
The update must preserve the relationship’s import provenance.

---

# 45. Legacy external relationships

## REM-05-499 — Relationship targets may temporarily be external identifiers

**Source**  
Section 45: “A relationship target may temporarily use an external identifier.”

**Requirement**  
A relationship record MAY temporarily identify its target using an external identifier when no verified Relay target is available.

**Classification**  
External target; legacy compatibility; transitional identity reference.

**Notes**  
External targets are a portability bridge and should not be confused with stable Relay identifiers.

---

## REM-05-500 — External target records identify their type

**Source**  
Section 45 example: `"type": "external"`.

**Requirement**  
A legacy external relationship target MUST be explicitly typed as external or with an equivalent unambiguous machine-readable classification.

**Classification**  
Schema requirement; external reference; type safety.

**Notes**  
Explicit typing prevents applications from interpreting the value as a Relay Identifier.

---

## REM-05-501 — External targets identify the source service

**Source**  
Section 45 example: `"service": "example-social-network"`.

**Requirement**  
A legacy external relationship target MUST identify the external service or namespace in which its identifier is meaningful.

**Classification**  
Namespace; external identity; reference integrity.

**Notes**  
An identifier without its service context may be ambiguous or resolve to the wrong entity.

---

## REM-05-502 — External targets preserve the external identifier

**Source**  
Section 45 example: `"identifier": "user_8821"`.

**Requirement**  
A legacy external relationship target MUST preserve the external identifier used by the source service.

**Classification**  
External reference; import fidelity; identity matching.

**Notes**  
The identifier should be stored without falsely converting it into Relay identity syntax.

---

## REM-05-503 — External targets are less portable than Relay targets

**Source**  
Section 45: “This is less portable than a Relay target.”

**Requirement**  
Implementations MUST treat external relationship targets as less portable and less reliably resolvable than stable Relay targets.

**Classification**  
Portability limitation; external dependency; relationship continuity.

**Notes**  
The external service may rename accounts, restrict access, disappear or expose identifiers that cannot be independently resolved.

---

## REM-05-504 — Verified Relay identity linkage may update the relationship

**Source**  
Section 45: “If the external account later verifies a Relay Identity, the relationship may be updated or linked.”

**Requirement**  
If an external account later verifies a Relay Identity, the relationship record MAY be updated or linked to reference that verified Relay Identity.

**Classification**  
Identity upgrade; relationship maintenance; verification.

**Notes**  
The implementation should avoid creating unnecessary duplicate active relationships where the schema defines uniqueness.

---

## REM-05-505 — Identity upgrade preserves import provenance

**Source**  
Section 45: the relationship may be updated or linked “without losing import provenance.”

**Requirement**  
Updating or linking an external relationship target to a verified Relay Identity MUST NOT remove or obscure the relationship’s original import provenance.

**Classification**  
Provenance preservation; identity upgrade; auditability.

**Notes**  
Consumers must remain able to determine that the relationship originated from imported external data and was later resolved to a Relay Identity.

---

## Editorial QA summary

- Sections 41–45 were extracted directly from `design-notes/05-relationship-model.md`.
- Requirement numbering was verified as continuous from `REM-05-458` through `REM-05-505`.
- Reverse relationships and relationship indexes remain explicitly derived rather than canonical.
- Index incompleteness is preserved as a presentation and inference constraint.
- Relationship-event delivery remains subordinate to visibility and permission rules.
- Imported external identifiers are not elevated to verified Relay identities without a verification basis.
- Legacy external targets remain explicitly typed, service-scoped and less portable than Relay targets.
- Upgrading an external reference to a verified Relay Identity preserves the original import provenance.
