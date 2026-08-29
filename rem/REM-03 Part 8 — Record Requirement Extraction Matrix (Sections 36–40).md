# REM-03 Part 8 — Record Requirement Extraction Matrix (Sections 36–40)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 36–40 of `design-notes/03-record-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

36. Reactions
37. Reposts and references
38. Moderation labels
39. Record conflict
40. Batch operations

Requirement identifiers continue sequentially from Part 7, beginning with `REM-03-361`.

---

# 36. Reactions

## REM-03-361 — Reaction represented as a record

**Source**  
Section 36: “A reaction should normally be represented as a record owned by the reacting identity.”

**Requirement**  
A reaction SHOULD normally be represented as an independently addressable Relay Record.

**Classification**  
Record modelling; activity records; recommendation.

**Notes**  
The source establishes record representation as the normal model while leaving room for exceptional schema-specific approaches.

---

## REM-03-362 — Reaction ownership by reacting identity

**Source**  
Section 36: “A reaction should normally be represented as a record owned by the reacting identity.”

**Requirement**  
A reaction record SHOULD normally be controlled by the Relay Repository and authority of the identity that performed the reaction.

**Classification**  
Ownership; repository authority; identity control; recommendation.

**Notes**  
The identity controlling the target content does not thereby own reactions made by other identities.

---

## REM-03-363 — Reaction target reference

**Source**  
Section 36 example containing a `subject` Record URI.

**Requirement**  
A reaction record SHOULD identify the record or object to which the reaction applies using an explicit protocol reference.

**Classification**  
Referential structure; reaction semantics; recommendation.

**Notes**  
The example uses the `subject` field, but the exact schema field name remains schema-defined.

---

## REM-03-364 — Reaction type declaration

**Source**  
Section 36 example containing `"reaction": "like"`.

**Requirement**  
A reaction record SHOULD declare the reaction type or value applied to its target.

**Classification**  
Schema content; semantic interoperability; recommendation.

**Notes**  
The permitted reaction vocabulary is determined by the applicable schema.

---

## REM-03-365 — Reaction aggregation permitted

**Source**  
Section 36: “Applications may aggregate reactions into counts.”

**Requirement**  
Applications MAY aggregate individual reaction records into counts or equivalent derived summaries.

**Classification**  
Application behaviour; aggregation; derived data.

**Notes**  
Aggregation does not replace the underlying canonical reaction records.

---

## REM-03-366 — Reaction count is derived

**Source**  
Section 36: “The count is a derived value.”

**Requirement**  
An aggregate reaction count MUST be treated as a derived value rather than as the underlying canonical reaction objects.

**Classification**  
Derived data; canonical-state distinction.

**Notes**  
A count may change as reaction records are created, deleted, restricted or become unavailable.

---

## REM-03-367 — Individual reactions remain canonical

**Source**  
Section 36: “The individual reaction records are the underlying canonical objects.”

**Requirement**  
Individual accepted reaction records MUST remain the underlying canonical objects from which aggregate reaction values are derived.

**Classification**  
Canonical records; provenance; aggregation integrity.

**Notes**  
Applications must not substitute an untraceable count for the canonical reaction records where record-level verification or ownership matters.

---

# 37. Reposts and references

## REM-03-368 — Repost must not imply copied authorship

**Source**  
Section 37: “A repost should not require copying the original record into the reposter’s repository as if they authored it.”

**Requirement**  
A repost SHOULD NOT require the original record to be copied into the reposter’s repository in a form that represents the reposter as the original author.

**Classification**  
Authorship integrity; repost modelling; recommendation.

**Notes**  
A cached or embedded representation may still exist, but it must preserve source provenance and must not misstate authorship.

---

## REM-03-369 — Repost represented through source reference

**Source**  
Section 37: “Instead, the repost record references the source.”

**Requirement**  
A repost record SHOULD reference the original source record using its stable protocol identifier.

**Classification**  
Referential structure; repost modelling; recommendation.

**Notes**  
The repost is a distinct logical record whose meaning depends on its reference to the source.

---

## REM-03-370 — Repost may contain reposter commentary

**Source**  
Section 37 example containing a source `subject` and a `comment`.

**Requirement**  
A repost schema MAY permit the reposter to attach commentary or other schema-defined content to the source reference.

**Classification**  
Schema behaviour; repost content; extensibility.

**Notes**  
The commentary belongs to the repost record and does not modify the original source record.

---

## REM-03-371 — Repost belongs to reposter

**Source**  
Section 37: “The repost belongs to the reposter.”

**Requirement**  
The repost record MUST remain controlled by the repository and authorising identity of the reposter.

**Classification**  
Ownership; repository authority; identity control.

**Notes**  
The reposter may control the repost without gaining control of the referenced original.

---

## REM-03-372 — Original remains under original-author control

**Source**  
Section 37: “The original remains controlled by the original author.”

**Requirement**  
Creation of a repost MUST NOT transfer control of the original record away from its original authoritative repository and authorising identity.

**Classification**  
Ownership separation; source control; authorship integrity.

**Notes**  
The original author may update or delete the source according to its own schema and repository rules, independently of the repost.

---

# 38. Moderation labels

## REM-03-373 — Moderation decision represented separately

**Source**  
Section 38: “Moderation decisions should be represented separately from the target record.”

**Requirement**  
A moderation decision SHOULD be represented as a separate record rather than as an in-place rewrite of the target record.

**Classification**  
Moderation modelling; separation of concerns; recommendation.

**Notes**  
Separate representation preserves the distinction between original content and a third-party judgement about that content.

---

## REM-03-374 — Moderation-label issuer identification

**Source**  
Section 38 example containing an `issuer`.

**Requirement**  
A moderation-label record SHOULD identify the identity or service that issued the label.

**Classification**  
Issuer accountability; moderation provenance; recommendation.

**Notes**  
Applications require issuer identity in order to choose which label providers they trust.

---

## REM-03-375 — Moderation-label target identification

**Source**  
Section 38 example containing a target `subject` Record URI.

**Requirement**  
A moderation-label record SHOULD identify the record or object to which the moderation decision applies.

**Classification**  
Referential structure; moderation semantics; recommendation.

**Notes**  
The label record and target record remain separately addressable objects.

---

## REM-03-376 — Moderation-label value declaration

**Source**  
Section 38 example containing `"label": "graphic-content"`.

**Requirement**  
A moderation-label record SHOULD declare the moderation label or decision assigned to the target.

**Classification**  
Schema content; moderation interoperability; recommendation.

**Notes**  
The permitted label vocabulary and semantics are schema-defined.

---

## REM-03-377 — Moderation issuance time

**Source**  
Section 38 example containing `issuedAt`.

**Requirement**  
A moderation-label record SHOULD identify when the label was issued.

**Classification**  
Temporal metadata; moderation provenance; recommendation.

**Notes**  
Time information supports auditability, expiration and policy evaluation.

---

## REM-03-378 — Label does not alter original record

**Source**  
Section 38: “A label does not alter the original record.”

**Requirement**  
Issuing or applying a moderation label MUST NOT alter the canonical content or history of the original target record.

**Classification**  
Record integrity; moderation separation; canonical history.

**Notes**  
An application may change how it displays or serves the target based on the label without rewriting the target itself.

---

## REM-03-379 — Application choice of trusted label providers

**Source**  
Section 38: “Applications may choose which label providers and policies they trust.”

**Requirement**  
Applications MAY choose which moderation-label issuers and moderation policies they trust or enforce.

**Classification**  
Application autonomy; trust policy; moderation.

**Notes**  
Different applications may therefore produce different moderation outcomes from the same underlying records and labels.

---

## REM-03-380 — No universal moderation policy in Relay v0.1

**Source**  
Section 38: “Relay v0.1 does not define a universal moderation policy...”

**Requirement**  
Relay v0.1 MUST NOT be interpreted as defining one universal moderation policy that all applications must apply.

**Classification**  
Protocol scope; moderation governance; application autonomy.

**Notes**  
The protocol supplies interoperable moderation records, not a universal content-policy authority.

---

## REM-03-381 — Support for independently issued labels

**Source**  
Section 38: “...the record model must support independently issued labels.”

**Requirement**  
The Relay Record Model MUST support moderation labels issued independently of the repository or identity controlling the target record.

**Classification**  
Moderation interoperability; third-party assertions; extensibility.

**Notes**  
Independent issuance requires clear issuer, subject and provenance information.

---

# 39. Record conflict

## REM-03-382 — Conflict definition

**Source**  
Section 39: “A record conflict occurs when two updates attempt to replace the same current version.”

**Requirement**  
An implementation MUST recognise a record conflict when two or more update operations attempt to replace the same current Record Version.

**Classification**  
Concurrency; conflict detection; versioning.

**Notes**  
The requirement applies regardless of whether the updates originate from the same or different applications.

---

## REM-03-383 — No silent dual linear acceptance

**Source**  
Section 39: “The repository must not silently accept both as a single linear continuation.”

**Requirement**  
The repository MUST NOT silently accept conflicting updates as though both formed one unambiguous linear continuation of the record history.

**Classification**  
Repository integrity; concurrency control; conflict handling.

**Notes**  
The repository must expose or resolve the conflict through an explicit outcome.

---

## REM-03-384 — Conflict outcome: reject later submission

**Source**  
Section 39, possible outcome: “reject the later submission”.

**Requirement**  
A repository MAY resolve a record conflict by rejecting the later conflicting submission.

**Classification**  
Conflict resolution; repository behaviour.

**Notes**  
Rejection should provide sufficient information for the application or user to understand that the expected version was no longer current.

---

## REM-03-385 — Conflict outcome: request user review

**Source**  
Section 39, possible outcome: “request user review”.

**Requirement**  
A repository or application MAY require user review before resolving a record conflict.

**Classification**  
Conflict resolution; user control.

**Notes**  
User review is particularly appropriate where neither update can safely be discarded automatically.

---

## REM-03-386 — Conflict outcome: reconciled version

**Source**  
Section 39, possible outcome: “create a new reconciled version”.

**Requirement**  
A conflict-resolution process MAY create a new reconciled Record Version.

**Classification**  
Conflict resolution; versioning; reconciliation.

**Notes**  
The reconciled version is a new accepted state and must not retroactively rewrite the conflicting proposals as though no conflict occurred.

---

## REM-03-387 — Conflict outcome: preserve candidates

**Source**  
Section 39, possible outcome: “preserve both proposed versions as conflict candidates”.

**Requirement**  
A repository MAY preserve conflicting proposed versions as separately identifiable conflict candidates.

**Classification**  
Conflict preservation; auditability; repository history.

**Notes**  
Candidate preservation allows later review without presenting both candidates as the single current version.

---

## REM-03-388 — Application-assisted merge

**Source**  
Section 39: “For text and other mergeable formats, an application may offer a merge.”

**Requirement**  
For text or other mergeable record formats, an application MAY offer a merge of conflicting proposals.

**Classification**  
Application behaviour; conflict resolution; merge support.

**Notes**  
The ability to merge is format- and schema-dependent.

---

## REM-03-389 — Explicit authorisation of merged record

**Source**  
Section 39: “The resulting merged record must still be explicitly authorised.”

**Requirement**  
A merged record produced during conflict resolution MUST receive explicit valid authorisation before it becomes an accepted current Record Version.

**Classification**  
Authority; conflict resolution; repository acceptance.

**Notes**  
Technical merge success does not substitute for repository authority or controller approval.

---

# 40. Batch operations

## REM-03-390 — Multiple record changes in one commit

**Source**  
Section 40: “An application may submit several record changes as one commit.”

**Requirement**  
An application MAY submit multiple record changes together as one repository commit.

**Classification**  
Batch operations; commit model; application behaviour.

**Notes**  
The changes may include heterogeneous operations affecting different records and collections.

---

## REM-03-391 — Atomic batch success or failure

**Source**  
Section 40: “The commit either succeeds in full or fails in full.”

**Requirement**  
A batch commit MUST be atomic: all included record changes MUST be accepted together, or none of them MUST be accepted.

**Classification**  
Atomicity; repository integrity; transaction semantics.

**Notes**  
Partial acceptance would leave repository state inconsistent with the submitted commit boundary.

---

## REM-03-392 — Independent addressability after batch acceptance

**Source**  
Section 40: “The records remain independently addressable after acceptance.”

**Requirement**  
Each record affected or created by an accepted batch commit MUST remain independently addressable after acceptance.

**Classification**  
Addressing; batch operations; record identity.

**Notes**  
Batching changes for atomic acceptance must not collapse the participating records into one inseparable logical object.

---

## REM-03-393 — Batch commit does not replace record identity

**Source**  
Section 40, combined atomic-commit and independent-addressability rules.

**Requirement**  
The identity of the batch commit MUST remain distinct from the stable logical identity of each record included in that commit.

**Classification**  
Commit identity; record identity; separation of concerns.

**Notes**  
The commit identifies the accepted state transition, while each Record URI continues to identify its own logical record.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 36–40 of `design-notes/03-record-model.md`.
- Section 41 and later content was excluded.
- Examples were used to clarify fields and relationships but were not promoted into final mandatory schema syntax.

## Numbering verification

- First requirement: `REM-03-361`.
- Final requirement: `REM-03-393`.
- Requirement numbering continues directly from Part 7.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Every requirement is traceable to an explicit source sentence, example field, listed outcome or necessary decomposition of a compound statement.
- Recommended source behaviour remains expressed as `SHOULD` or `SHOULD NOT`.
- Permitted application and repository choices remain expressed as `MAY`.
- Mandatory integrity, authority and atomicity rules remain expressed as `MUST` or `MUST NOT`.

## Editorial verification

- Reaction aggregates remain derived from canonical individual reaction records.
- Repost authorship remains separate from authorship and control of the original record.
- Moderation labels remain separate assertions and do not rewrite target records.
- Application trust in moderation providers remains configurable.
- Conflict handling cannot silently manufacture a false linear history.
- Any merged conflict result still requires explicit authorisation.
- Batch commits are atomic while participating records remain independently addressable.
