# Relay Editorial Audit 03

## Protocol Invariants

**Corpus:** Relay Protocol v0.1 design corpus  
**Scope:** `00-relay-at-a-glance.md` and Core Objects `01`–`15`  
**Status:** Draft for founder review  
**Method:** Extraction and consolidation of the explicit invariant sections contained in the source corpus  
**Source count:** 222 explicit invariant statements across the 15 Core Objects

---

## 1. Purpose

This audit identifies the rules the Relay design corpus treats as permanently or structurally true.

It does not invent new protocol behaviour.

Its purpose is to distinguish between:

1. **constitutional invariants** — guarantees that define Relay’s identity as a protocol;
2. **architectural invariants** — rules required to preserve Relay’s separation of authority, ownership and canonical state;
3. **subsystem invariants** — precise rules belonging to identity, repositories, records, permissions, migration, events, schemas and other technical chapters;
4. **conformance and governance invariants** — rules governing how compatibility is demonstrated and how Relay evolves.

The final consolidated specification should not place all 222 source statements into one undifferentiated list.

Instead, it should define a small constitutional set near the beginning of the specification and retain the more detailed rules in their relevant normative chapters.

---

## 2. Method

Each Core Object’s explicit `Invariants` section was extracted directly from the Markdown corpus.

The extracted statements were then compared for:

- exact duplication;
- semantic overlap;
- dependency;
- level of abstraction;
- whether the rule defines Relay itself or only one subsystem;
- whether the rule is testable;
- whether the rule belongs in the constitutional layer, architecture, a technical chapter, compliance, conformance or governance.

No source invariant has been deleted from the traceability record.

Where several source statements express one underlying guarantee, this report proposes one consolidated invariant and records the source groups that support it.

---

## 3. Principal Finding

The design corpus contains a coherent invariant system.

Although there are 222 explicit invariant statements, most are specialised expressions of a much smaller number of underlying guarantees.

The corpus supports:

- **12 constitutional invariants**
- **10 architectural invariants**
- subsystem-specific invariants that should remain distributed across normative chapters
- governance and conformance invariants that protect the protocol’s evolution and compatibility claims

No source document establishes a competing constitutional model.

The repeated themes are consistent:

- identity continuity;
- stable protocol identifiers;
- replaceability of Providers and Applications;
- explicit, limited and revocable authority;
- canonical state controlled through authorised repository operations;
- independent verification;
- preservation of unknown valid data;
- separation between protocol validity, policy, moderation and factual truth;
- transparent compliance and governance;
- preservation of the right to implement and extend Relay independently.

---

# Part I — Proposed Constitutional Invariants

## 4. Status of This List

The following 12 invariants are recommended as the constitutional invariant set for the consolidated Relay specification.

They are not quotations copied from one source section.

They are editorial consolidations of repeated source rules.

The exact normative wording must be approved before inclusion in `SPECIFICATION.md`.

---

## CI-01 — Persistent Identity

> A Relay Identity remains the same protocol identity when its handle, Provider, Application, device, service location or cryptographic keys change.

### Source support

- Identity Model: Invariants 1–3
- Discovery and Resolution Model: Invariants 1–4
- Migration and Portability Model: Invariant 1
- Provider Compliance Model: Invariant 2
- Application and Client Compliance Model: Invariant 15

### Rationale

Relay cannot preserve digital continuity if ordinary operational changes create a new identity.

### Consequences

- Handles are references to identities, not identities themselves.
- Provider URLs are service locations, not identity identifiers.
- Key rotation changes authority material, not identity.
- Application replacement does not create a new identity.
- A terminated Relay Identifier must not be reassigned.

---

## CI-02 — Controller Authority

> Ultimate authority over a Relay Identity belongs to its valid Controller and must not arise merely from hosting, application access, technical possession, indexing, witnessing, certification or governance.

### Source support

- Identity Model: Invariants 4, 5 and 10
- Ecosystem Roles: Invariants 1, 2, 5–10 and 15
- Commit and Verification Model: Invariant 9
- Provider Compliance Model: Invariants 1, 4 and 10
- Conformance Testing Model: Invariant 13
- Governance and Evolution Model: Invariants 1 and 3

### Rationale

Relay separates operational roles from identity authority.

### Consequences

- A Provider does not own hosted identities.
- An Application does not become Controller by creating records.
- A Resolver does not assign authority.
- A Witness observes; it does not control.
- Certification does not confer authority.
- Governance stewards the protocol; it does not own identities or repositories.

---

## CI-03 — Provider Replaceability

> A Controller can replace a Relay Provider without changing the Relay Identifier, Repository Identifier, existing Record URIs, valid history or relationship continuity.

### Source support

- Identity Model: Invariants 2 and 6
- Repository Model: Invariants 1, 2 and 10
- Relationship Model: Invariant 3
- Migration and Portability Model: Invariants 1–3 and 14
- Provider Compliance Model: Invariants 2, 3, 8 and 9
- Governance and Evolution Model: Invariant 5

### Rationale

Provider portability is operational continuity, not merely file export.

### Consequences

- Migration must result in one identifiable authoritative repository.
- A data download alone is not completed migration.
- The source must stop canonical writes after cutover.
- Relationships continue to point to stable identities, not Provider locations.

---

## CI-04 — Application Replaceability

> A Controller can replace an Application without losing canonical supported records, stable Record URIs, relationships or repository continuity.

### Source support

- Repository Model: Invariant 5
- Record Model: Invariants 9–11
- Relationship Model: Invariants 2 and 10
- Application and Permission Model: Invariants 4, 10 and 13
- Application and Client Compliance Model: Invariants 1–9, 13, 17–19
- Conformance Testing Model: Invariant 7

### Rationale

Applications create experiences over canonical user-controlled state; they do not become the permanent home of that state.

### Consequences

- An Application’s private database must not be an undisclosed superior source of user-created truth.
- Revocation stops future authority but does not erase canonical records.
- Application URLs do not replace Record URIs.
- Application disappearance must not destroy supported canonical records.
- First-party and third-party Applications follow the same ownership rules.

---

## CI-05 — Stable Canonical Identifiers

> Protocol-level identifiers remain stable across ordinary lifecycle changes and must not be replaced by Provider-, Application- or implementation-specific identifiers.

### Source support

- Identity Model: Invariants 1–3 and 7
- Repository Model: Invariants 1, 2 and 12
- Record Model: Invariants 1 and 2
- Relationship Model: Invariants 2 and 11
- Discovery and Resolution Model: Invariants 1–5 and 15
- Migration and Portability Model: Invariants 1–3
- Application and Client Compliance Model: Invariants 3 and 17

### Rationale

References cannot remain portable if identifiers change with infrastructure or presentation.

### Consequences

- A Record URI identifies one logical record and is not reassigned.
- A released handle does not inherit historical continuity.
- Internal database keys cannot replace protocol identifiers.
- Service URLs and Application URLs remain locators or views, not canonical identity.

---

## CI-06 — Explicit and Limited Authority

> Every non-public action requires valid, attributable and limited authority; authority for one action, purpose, resource or role does not imply another.

### Source support

- Application and Permission Model: Invariants 1–3, 5–7, 9, 11, 12 and 14
- Ecosystem Roles: Invariants 1, 12–14
- Event and Synchronisation Model: Invariants 4 and 5
- Migration and Portability Model: Invariant 4
- Provider Compliance Model: Invariants 5, 10 and 13
- Application and Client Compliance Model: Invariants 9–12
- Relationship Model: Invariants 4–7

### Rationale

Relay authority is delegated, scoped and revocable rather than inferred from access or role.

### Consequences

- Read permission does not imply retention, redistribution, training, deletion or migration.
- An Application cannot expand its own grant.
- A token is evidence of delegated authority, not ownership.
- Receiving an event does not grant write authority.
- Reciprocal relationships require independent authority from each participant.
- AI inference permission does not imply model-training permission.

---

## CI-07 — Canonical State Through Authorised Acceptance

> Data or derived output becomes canonical only through valid acceptance into the authoritative Relay Repository under applicable protocol rules.

### Source support

- Repository Model: Invariants 3, 4, 9 and 11
- Record Model: Invariants 3, 4 and 9
- Commit and Verification Model: Invariants 1, 4–8
- Event and Synchronisation Model: Invariants 1, 6, 11, 12 and 14
- Application and Client Compliance Model: Invariants 8, 13 and 16
- Provider Compliance Model: Invariant 5

### Rationale

Caches, projections, events, indexes, local drafts and derived outputs must not become competing sources of truth.

### Consequences

- A local draft is not canonical before repository acceptance.
- A rejected Commit does not change repository state.
- Accepted Commit operations are atomic.
- The Repository Head identifies one current canonical Commit.
- A cache or index remains derived.
- An Event signals state; it is not automatically canonical state.
- Derived data becomes canonical only after valid acceptance.

---

## CI-08 — Independent Verifiability

> Relay’s claims about identity authority, repository history, records, exports and migrations must be verifiable independently of the current Provider, Application, Resolver or governance operator.

### Source support

- Commit and Verification Model: Invariants 2–4, 10, 11, 13 and 14
- Discovery and Resolution Model: Invariants 6–11
- Migration and Portability Model: Invariants 5, 6, 10 and 15
- Provider Compliance Model: Invariants 7, 16 and 18
- Conformance Testing Model: Invariants 2, 3 and 8
- Governance and Evolution Model: Invariants 2 and 9

### Rationale

Replaceability without independent evidence would still require blind trust in the incumbent.

### Consequences

- Resolver output must contain verifiable evidence.
- Migration requires destination verification before activation.
- Exports must match their declared Repository Head and state.
- Historical Commits remain verifiable after migration and key rotation.
- Marketing claims do not substitute for observable behaviour.
- The reference implementation does not override the specification.

---

## CI-09 — Preservation Without Understanding

> A compliant Relay system preserves unknown but valid records, schemas, extensions, collections and integrity evidence even when it cannot interpret, render or edit them.

### Source support

- Repository Model: Invariant 6
- Record Model: Invariant 8
- Commit and Verification Model: Invariant 15
- Migration and Portability Model: Invariant 9
- Schema and Interoperability Model: Invariants 4, 5, 9 and 12
- Provider Compliance Model: Invariant 6
- Application and Client Compliance Model: Invariant 7
- Conformance Testing Model: Invariant 5

### Rationale

A system that destroys unfamiliar data recreates application and Provider lock-in.

### Consequences

- Unsupported records are preserved rather than silently converted.
- Applications do not rewrite records they do not understand.
- Schema publisher disappearance does not make records non-portable.
- Preservation must be tested through actual round trips.

---

## CI-10 — Provenance and Historical Integrity

> Relay preserves sufficient provenance and historical integrity to distinguish current state, prior valid state, deletion, translation, derivation, authority and factual truth.

### Source support

- Identity Model: Invariant 6
- Repository Model: Invariant 7
- Record Model: Invariants 7, 10 and 12
- Relationship Model: Invariants 12 and 13
- Commit and Verification Model: Invariants 3, 10–13
- Schema and Interoperability Model: Invariants 2, 3, 7, 8, 10 and 13
- Application and Client Compliance Model: Invariants 14 and 16

### Rationale

Relay verifies authorised history; it does not pretend that deletion, translation, moderation or a valid signature proves something it does not.

### Consequences

- Deletion does not require pretending a record never existed.
- Ending a relationship does not falsify historical existence.
- Translation preserves provenance and discloses loss.
- A valid signature does not establish factual truth.
- Schema validity does not establish safety or truth.
- Moderation does not alter repository validity.
- Deleted content may be erased while minimum integrity evidence remains.

---

## CI-11 — Role Separation and Purpose Limitation

> Performing one Relay role or possessing data for one purpose does not grant the authority or permission associated with another role or purpose.

### Source support

- Ecosystem Roles: Invariants 1–14
- Application and Permission Model: Invariants 5–7 and 10
- Provider Compliance Model: Invariants 12–14 and 17
- Application and Client Compliance Model: Invariants 10, 11, 14 and 19
- Relationship Model: Invariant 7

### Rationale

Relay’s separation of concerns fails if organisations can reuse technical access across undeclared roles.

### Consequences

- Hosting access does not authorise advertising, indexing or model training.
- Combined roles remain separately declared and authorised.
- A Backup or Mirror does not become canonical by possessing a copy.
- A relationship label does not itself create technical authority.
- Application moderation is separate from protocol validity.
- Provider policy is separate from protocol invalidity.

---

## CI-12 — Constitutional Continuity and Open Evolution

> Relay may evolve, but ordinary governance cannot remove migration, replaceability, independent implementation, public traceability or the Controller’s enduring continuity.

### Source support

- Governance and Evolution Model: Invariants 1–15
- Schema and Interoperability Model: Invariants 2, 3, 7–9, 14 and 15
- Conformance Testing Model: Invariants 1, 4, 10–12 and 15
- Provider Compliance Model: Invariant 20
- Application and Client Compliance Model: Invariant 20

### Rationale

A protocol designed against platform capture must also resist capture by its own implementation, governance, namespace or certification system.

### Consequences

- No implementation becomes the specification through popularity.
- No single Provider or Application receives unilateral protocol authority.
- Migration and replaceability cannot be removed through ordinary change.
- Third parties may create schemas and extensions without central product approval.
- Normative changes remain publicly traceable.
- Tests remain linked to published requirements.
- The governance body remains replaceable.
- Compliance claims identify their precise profile and limitations.

---

# Part II — Architectural Invariants

## 5. Purpose of the Architectural Set

The following invariants are broader than one technical subsystem but more operational than the constitutional set.

They should appear in the System Architecture chapter or immediately after the constitutional invariants.

---

## AI-01 — One Canonical Repository State

At any ordinary point in time, one repository state is identified as canonical for a Relay Repository.

Conflicting heads form a detectable fork and must not both be presented as the single canonical state.

### Principal sources

- Repository Model: Invariant 11
- Commit and Verification Model: Invariants 7 and 8
- Event and Synchronisation Model: Invariant 15
- Migration and Portability Model: Invariants 7, 13 and 15

---

## AI-02 — Commit-Backed Change

Every accepted canonical repository change belongs to a valid authorised Commit, and every non-genesis canonical Commit references the prior canonical Commit.

### Principal sources

- Repository Model: Invariants 3 and 4
- Record Model: Invariant 3
- Commit and Verification Model: Invariants 1, 4–6
- Provider Compliance Model: Invariant 5

---

## AI-03 — Atomic Acceptance

A Commit is either accepted as a valid atomic change or rejected without altering repository state.

### Principal sources

- Commit and Verification Model: Invariants 5 and 6

---

## AI-04 — Safe Migration Boundary

Migration establishes a verified transition from one authoritative Provider state to another, including a clear source/destination boundary and an identifiable authoritative state after failure or rollback.

### Principal sources

- Repository Model: Invariant 10
- Migration and Portability Model: Invariants 4–7, 13 and 15
- Event and Synchronisation Model: Invariant 10
- Provider Compliance Model: Invariants 8 and 9

---

## AI-05 — Event Non-Authority

Events communicate canonical or derived changes but do not themselves create authority or replace canonical state.

### Principal sources

- Event and Synchronisation Model: Invariants 1, 4, 6, 11 and 12
- Application and Client Compliance Model: Invariant 12

---

## AI-06 — Detectable Synchronisation Gaps

A synchronising system must detect missed state and must not advance beyond its last verified canonical state.

### Principal sources

- Event and Synchronisation Model: Invariants 7–9 and 14
- Conformance Testing Model: Invariant 9

---

## AI-07 — Visibility, Rights and Ownership Are Distinct

Visibility, indexing, moderation, access and usage rights do not independently determine ownership, canonical authority or protocol validity.

### Principal sources

- Record Model: Invariants 6 and 11
- Relationship Model: Invariants 8, 9 and 14
- Discovery and Resolution Model: Invariant 14
- Provider Compliance Model: Invariant 14
- Application and Client Compliance Model: Invariant 14

---

## AI-08 — Mutuality Requires Independent Acts

A unilateral relationship declaration must not be represented as reciprocal or mutually authorised.

### Principal sources

- Relationship Model: Invariants 1, 4–6 and 12

---

## AI-09 — Schema Evolution Preserves History

Published schema versions remain historically identifiable; breaking semantic changes use new major versions; deprecation does not invalidate existing records.

### Principal sources

- Schema and Interoperability Model: Invariants 2, 3, 7, 8 and 15

---

## AI-10 — Exact Compliance Claims

A compliance or conformance claim applies only to its named version, role, profile, capabilities, validation level and limitations.

### Principal sources

- Provider Compliance Model: Invariant 20
- Application and Client Compliance Model: Invariant 20
- Conformance Testing Model: Invariants 1, 2, 4, 10 and 11

---

# Part III — Subsystem Invariants

## 6. Why the Full 222 Should Not Be Flattened

The source corpus contains detailed invariants that are essential but should remain in their own chapters.

Examples include:

- a retry retains the same Event Identifier;
- unknown enumeration values require safe fallback;
- a deleted Blob is not available merely because its hash survives;
- a released handle does not transfer historical continuity;
- a self-declared relationship is not externally verified;
- schema extensions cannot redefine protocol-level core fields;
- private event metadata does not enter public streams;
- a Resolver must not present a Mirror as the canonical write Provider.

These rules are normative and testable.

They are not all constitutional.

Moving them into one top-level invariant list would make the specification harder to understand and could imply that every implementation profile must support every subsystem.

---

## 7. Recommended Distribution

### Constitutional chapter

Include CI-01 through CI-12.

### System Architecture chapter

Include AI-01 through AI-10.

### Identity and Resolution chapters

Retain detailed rules concerning:

- handles;
- key rotation;
- recovery;
- identity conflicts;
- termination;
- Provider disappearance;
- pseudonymity;
- resolution evidence.

### Repository, Record and Commit chapters

Retain detailed rules concerning:

- Commit ancestry;
- atomic operations;
- state roots;
- stale writes;
- deletion evidence;
- Blob availability;
- forks;
- Record URI lifecycle.

### Permission and Application chapters

Retain detailed rules concerning:

- Permission Grant scope;
- partial approval;
- token handling;
- purpose change;
- AI uses;
- local drafts;
- application manifests;
- non-portable state.

### Migration chapter

Retain detailed rules concerning:

- source and destination authority;
- cutover;
- write freeze;
- rollback;
- incomplete transfers;
- encryption portability;
- residual data.

### Event and Synchronisation chapter

Retain detailed rules concerning:

- stable Event Identifiers;
- duplicate processing;
- cursor scope;
- replay;
- gaps;
- stream boundaries;
- private event metadata.

### Schema chapter

Retain detailed rules concerning:

- immutable published definitions;
- semantic versioning;
- extension protection;
- translation;
- namespace control;
- preservation.

### Compliance, Conformance and Governance chapters

Retain detailed rules concerning:

- profile claims;
- evidence;
- test scope;
- reference implementation status;
- open test suites;
- conflicts of interest;
- funding;
- emergency powers;
- stewardship succession.

---

# Part IV — Duplication and Consolidation Findings

## 8. High-Frequency Invariant Clusters

### Cluster A — Stable identity and identifiers

Repeated across:

- Identity
- Repository
- Record
- Relationships
- Discovery and Resolution
- Migration
- Provider Compliance
- Application Compliance

**Editorial treatment:** one constitutional guarantee plus subsystem-specific identifier rules.

### Cluster B — No ownership through service role

Repeated across:

- Identity
- Repository
- Record
- Relationships
- Application and Permission
- Ecosystem Roles
- Provider Compliance
- Application Compliance
- Governance

**Editorial treatment:** one Controller Authority invariant plus role-specific prohibitions.

### Cluster C — Replaceability

Repeated across:

- Identity
- Repository
- Relationships
- Migration
- Provider Compliance
- Application Compliance
- Governance
- Conformance

**Editorial treatment:** separate Provider and Application replaceability constitutional invariants.

### Cluster D — Canonical versus derived state

Repeated across:

- Repository
- Record
- Commit
- Events
- Application Compliance
- Indexing and moderation rules

**Editorial treatment:** one constitutional canonical-acceptance rule plus technical state rules.

### Cluster E — Explicit authority

Repeated across:

- Application and Permission
- Relationships
- Migration
- Events
- Ecosystem Roles
- Provider Compliance
- Application Compliance

**Editorial treatment:** one constitutional authority rule plus detailed capabilities and revocation requirements.

### Cluster F — Preservation of unknown information

Repeated across:

- Repository
- Record
- Commit
- Migration
- Schemas
- Provider Compliance
- Application Compliance
- Conformance

**Editorial treatment:** one preservation invariant plus schema-, Provider-, Application- and migration-specific obligations.

### Cluster G — Independent verification

Repeated across:

- Commit
- Resolution
- Migration
- Provider Compliance
- Conformance
- Governance

**Editorial treatment:** one constitutional invariant plus verification procedures and tests.

### Cluster H — Protocol versus policy or truth

Repeated across:

- Commit
- Record
- Relationships
- Discovery and Resolution
- Schemas
- Provider Compliance
- Application Compliance

**Editorial treatment:** one provenance/historical-integrity invariant and one architecture rule distinguishing protocol validity, policy, moderation, legal rights and factual truth.

---

## 9. No Constitutional Conflict Found

No explicit invariant in one Core Object directly requires the negation of an invariant in another Core Object.

The main risks are not contradiction but:

- different abstraction levels;
- duplicated wording;
- local rules being mistaken for universal constitutional rules;
- compliance statements being mistaken for base definitions;
- future consolidation accidentally dropping a specialised exception or safeguard.

The traceability map should therefore be preserved when drafting the specification.

---

# Part V — Traceability Rules

## 10. Requirement for the Consolidated Specification

Every final constitutional and architectural invariant should have:

- a stable invariant identifier;
- approved normative wording;
- source Core Objects;
- linked normative requirements;
- linked conformance tests;
- version introduced;
- revision history.

Suggested identifiers:

```text
REL-CI-001
REL-CI-002
...
REL-AI-001
REL-AI-002
...
```

The prefix is provisional.

---

## 11. Invariant Change Control

The consolidated specification should distinguish:

### Clarification

Wording changes without changing conformant behaviour.

### Strengthening

Adds protection or closes a loophole without removing prior continuity.

### Technical migration

Changes a mechanism while preserving the invariant.

### Constitutional amendment

Changes the guarantee itself.

Under the Governance and Evolution Model, ordinary protocol change must not remove migration or replaceability or weaken constitutional continuity.

---

# Part VI — Proposed Editorial Decisions

## 12. ED-014 — Two-Level Invariant Model

Relay will maintain:

- a small constitutional invariant set;
- distributed subsystem invariants in normative chapters.

---

## 13. ED-015 — Stable Invariant Identifiers

Every approved constitutional and architectural invariant will receive a stable identifier.

---

## 14. ED-016 — Traceability Required

Every consolidated invariant must retain links to all source Core Objects that materially support it.

---

## 15. ED-017 — No Silent Promotion

A subsystem rule may not be promoted into a constitutional invariant without explicit editorial and governance review.

---

## 16. ED-018 — No Silent Weakening

Consolidation may remove duplicate wording but must not remove a substantive safeguard expressed by the source invariants.

---

## 17. ED-019 — Protocol Validity Is Limited

The final specification must consistently distinguish:

- cryptographic validity;
- canonical acceptance;
- factual truth;
- legal ownership and usage rights;
- Provider policy;
- Application moderation;
- external trust.

---

# Part VII — Review Questions

## 18. Decisions Requiring Founder Approval

Before these invariants become canonical, the following choices require explicit approval:

### Question 1

Should the constitutional set contain 12 invariants, or should the two replaceability guarantees be combined into one broader “Service Replaceability” invariant?

**Recommendation:** Keep Provider and Application replaceability separate. They protect against different lock-in mechanisms.

### Question 2

Should preservation of unknown valid data be constitutional?

**Recommendation:** Yes. Without it, nominally compatible systems can recreate lock-in by discarding unfamiliar records.

### Question 3

Should independent verifiability be constitutional?

**Recommendation:** Yes. Portability without independent verification leaves the incumbent as the final source of truth.

### Question 4

Should provenance and historical integrity be one constitutional invariant or only an architectural invariant?

**Recommendation:** Constitutional. Relay’s continuity promise depends on distinguishing current state from valid history without pretending that technical validity proves factual truth.

### Question 5

Should open evolution and governance replaceability remain in the runtime specification’s constitutional set?

**Recommendation:** Yes, but its detailed requirements belong in Governance. A protocol designed around replaceable services should not make its own stewardship permanently irreplaceable.

---

# Part VIII — Conclusion

## 19. Audit Result

**Editorial Audit 03: Protocol Invariants — Complete**

The source corpus contains 222 explicit subsystem invariants.

These can be consolidated without loss into:

- 12 proposed constitutional invariants;
- 10 proposed architectural invariants;
- distributed chapter-level subsystem invariants;
- explicit conformance and governance protections.

The corpus does not show constitutional drift.

Its repeated rules consistently protect:

- stable identity;
- Controller authority;
- Provider and Application replaceability;
- stable identifiers;
- delegated authority;
- canonical repository state;
- independent verification;
- preservation of unknown valid data;
- historical integrity;
- role separation;
- open and replaceable governance.

---

## 20. Recommended Next Artifact

The next editorial artifact should be:

```text
editorial/04-canonical-terminology-map.md
```

It should use this invariant model together with Editorial Audit 02 to establish:

- canonical term;
- definition source;
- approved short form;
- deprecated or ambiguous synonym;
- constitutional or architectural relevance;
- exact future glossary location;
- unresolved wording decision.

The Canonical Terminology Map should be approved before the Requirements Audit begins.
