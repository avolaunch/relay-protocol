# EA-05-05 — Relationship Requirements Catalogue

## Part 17 — Reverse Relationships, Indexes and Event Delivery

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing reverse relationship views, relationship-index capabilities and limitations, and event delivery for relationship lifecycle changes.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-293`, following Part 16's coverage of relationship privacy and discovery. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 41–43 and REM-05 requirements `REM-05-458` through `REM-05-488`.

It defines normative requirements governing:

- reverse relationships as derived index views;
- distributed canonical ownership of reverse-query records;
- reverse-index aggregation and provenance metadata;
- reverse-index visibility, deletion and ownership boundaries;
- optional relationship-index graph services;
- incomplete index coverage and absence-of-evidence limitations;
- transparency concerning derived index results;
- optional relationship lifecycle events; and
- visibility, permission and private-block constraints on event delivery.

Section 44 relationship imports and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-293

### Title

Reverse Relationships as Derived Views

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay implementation **MUST** treat a reverse relationship view as a derived index result rather than as an independently authoritative relationship declaration.

### Rationale

A reverse query aggregates declarations that remain canonically distributed across their respective Source repositories. The derived view does not create a new relationship owned by the Target or index.

### Source

- REM-05-458
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-294

### Title

Reverse Relationship Query Capability

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship index **MAY** expose reverse queries that identify relationship records whose targets match a specified identity, record or entity.

### Rationale

Reverse lookup is an optional derived-service capability rather than an obligation of the Target repository.

### Source

- REM-05-459
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-03

---

## REL-REL-295

### Title

Distributed Canonical Ownership of Reverse-Query Records

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

For a reverse relationship result, the canonical relationship records **MUST** remain the records controlled by their respective Source repositories.

### Rationale

Aggregation by a reverse index does not relocate or transfer ownership of the declarations it discovers.

### Source

- REM-05-460
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-296

### Title

Reverse Relationship Aggregation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A reverse index **MAY** collect relationship records that it is authorised to discover and expose an aggregated result derived from those records.

### Rationale

Aggregation enables ecosystem-wide reverse discovery while retaining the distinction between a derived service and canonical record storage.

### Source

- REM-05-461
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-297

### Title

Reverse Index Provenance and Freshness Metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A reverse relationship index **SHOULD** preserve, for each indexed relationship result, the source Record URI, observed record version and retrieval or last-refresh time.

### Rationale

These source-defined metadata elements allow consumers to trace a derived result back to its canonical record, identify the version observed by the index and assess result freshness.

### Source

- REM-05-462
- REM-05-463
- REM-05-464
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-298

### Title

Reverse Index Visibility Preservation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A reverse relationship index **SHOULD** preserve and enforce the visibility status applicable to each indexed relationship record.

### Rationale

Indexing cannot convert restricted or private relationship information into public graph data.

### Source

- REM-05-465
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-299

### Title

Reverse Index Deletion Updates

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A reverse relationship index **SHOULD** process and retain sufficient deletion-update state to stop presenting relationship records that are no longer validly available.

### Rationale

Derived graph services require deletion propagation to avoid presenting stale relationships as current. Any permitted historical retention remains distinct from current-state presentation.

### Source

- REM-05-466
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-03
- AI-09

---

## REL-REL-300

### Title

Reverse Index Is Not Canonical Owner

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A reverse relationship index **MUST NOT** represent itself as the canonical owner or authoritative origin of the relationship records it indexes.

### Rationale

The Source identity's repository remains authoritative for the Source identity's declaration regardless of where a derived reverse result is exposed.

### Source

- REM-05-467
- `design-notes/05-relationship-model.md`, Section 41

### Related Invariants

- CI-02
- CI-03

---

## REL-REL-301

### Title

Relationship Index Derived Capabilities

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship index **MAY**, within its authorised and discoverable coverage, provide follower counts, mutual-connection views, organisation-membership lookup, professional graph search, purpose-scoped trust paths and community discovery.

### Rationale

Section 42 defines these as optional derived graph services. Each remains subject to the visibility, evidentiary, contextual and authority semantics of the underlying relationship records.

### Source

- REM-05-468
- REM-05-469
- REM-05-470
- REM-05-471
- REM-05-472
- REM-05-473
- `design-notes/05-relationship-model.md`, Section 42

### Related Invariants

- CI-03
- CI-10
- CI-12

---

## REL-REL-302

### Title

Relationship Index Incomplete-Coverage Assumption

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relationship-index results **MUST** be designed and presented on the assumption that index coverage may be incomplete.

### Rationale

Repositories, private records, access restrictions, indexing delays and service scope can all prevent an index from observing the complete graph.

### Source

- REM-05-474
- `design-notes/05-relationship-model.md`, Section 42

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-303

### Title

Index Absence Does Not Prove Relationship Nonexistence

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** represent the absence of a relationship from a particular index as proof that no such relationship exists.

### Rationale

An absent index result establishes only that the selected index has no qualifying record within its current coverage and state.

### Source

- REM-05-475
- `design-notes/05-relationship-model.md`, Section 42

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-304

### Title

Derived Index Result Transparency

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An application presenting relationship-index results **SHOULD** identify that the result is derived and, where material, disclose the index or service that produced it.

### Rationale

Consumers should be able to distinguish an index response from a canonical repository assertion, particularly where coverage or freshness limitations affect interpretation.

### Source

- REM-05-476
- `design-notes/05-relationship-model.md`, Sections 41–42

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-305

### Title

Relationship Lifecycle Event Generation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay implementation **MAY** generate relationship lifecycle events, including `follow-created`, `follow-ended`, `relationship-requested`, `relationship-accepted`, `relationship-revoked`, `membership-expired`, `block-created` and `credential-revoked`, when the corresponding underlying state change validly occurs.

### Rationale

Section 43 defines event generation as optional and supplies representative lifecycle event types. Events communicate changes for notification, enforcement or synchronisation but do not independently establish canonical relationship state.

### Source

- REM-05-477
- REM-05-478
- REM-05-479
- REM-05-480
- REM-05-481
- REM-05-482
- REM-05-483
- REM-05-484
- REM-05-485
- `design-notes/05-relationship-model.md`, Section 43

### Related Invariants

- CI-02
- CI-10
- AI-09

---

## REL-REL-306

### Title

Relationship Event Visibility Enforcement

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relationship event delivery **MUST** enforce the visibility rules applicable to the underlying relationship and event data.

### Rationale

Event delivery is another disclosure surface for relationship information. It cannot expose existence, type, Target, context, evidence or other protected information beyond the applicable visibility rules.

### Source

- REM-05-486
- `design-notes/05-relationship-model.md`, Section 43

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-307

### Title

Relationship Event Permission Enforcement

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A relationship event **MUST NOT** be delivered to an application, index or subscriber that lacks the permission or public-access basis required to receive it.

### Rationale

Subscription to an event mechanism does not itself confer access to protected relationship data.

### Source

- REM-05-487
- `design-notes/05-relationship-model.md`, Section 43

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-308

### Title

No Public Broadcast of Private Block Events

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A private block event **MUST NOT** be broadcast or otherwise disclosed to a public relationship indexer.

### Rationale

Block relationships are normally privacy-sensitive safety controls. Broadcasting their lifecycle events to public graph services would disclose information that the underlying relationship is not authorised to reveal.

### Source

- REM-05-488
- `design-notes/05-relationship-model.md`, Section 43

### Related Invariants

- CI-10
- CI-12

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that form one source-defined metadata structure, capability set or lifecycle-event vocabulary:

- `REM-05-462` through `REM-05-464` are consolidated into `REL-REL-297`. Source Record URI, observed version and retrieval time are the three source-defined provenance/freshness metadata fields and share `SHOULD` strength.
- `REM-05-468` through `REM-05-473` are consolidated into `REL-REL-301`. Follower counts, mutual connections, organisation-membership lookup, professional graph search, trust paths and community discovery are the six source-defined optional relationship-index capabilities and share `MAY` strength.
- `REM-05-477` through `REM-05-485` are consolidated into `REL-REL-305`. The general event-generation permission and eight named lifecycle events form the source-defined optional event capability and retain `MAY` strength. Consolidation does not imply that the events have identical trigger semantics.

No other REM-05 entries in the covered range are consolidated. Reverse-view derivation, reverse-query capability, canonical ownership, aggregation, visibility, deletion handling, index ownership boundary, incomplete-coverage treatment, absence inference, derived-result transparency and the three event-delivery controls remain independently meaningful and testable requirements.

All REM-05 requirements from `REM-05-458` through `REM-05-488` are represented exactly once in the catalogue mapping, either independently or through the three explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 17 begins at `REM-05-458`, immediately after Part 16's final covered requirement `REM-05-457`.
- Coverage ends at `REM-05-488`, the end of source Section 43.
- Section 44 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 41–43.

## Numbering verification

- First catalogue requirement: `REL-REL-293`.
- Final catalogue requirement: `REL-REL-308`.
- Catalogue numbering continues directly from Part 16's `REL-REL-292`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Reverse relationships remain derived rather than independently authoritative.
- Canonical records remain distributed across their Source repositories.
- Reverse querying and aggregation remain optional index capabilities.
- Reverse-index provenance/freshness metadata, visibility and deletion handling retain `SHOULD` strength.
- Reverse indexes remain prohibited from claiming canonical ownership.
- Relationship-index graph capabilities remain optional.
- Incomplete coverage remains a mandatory design and presentation assumption.
- Absence from one index remains insufficient evidence of relationship nonexistence.
- Derived-result transparency retains `SHOULD` strength.
- Event generation and the named event types remain optional.
- Event visibility enforcement remains mandatory.
- Delivery without permission and public broadcast of private block events remain prohibited.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves the derived nature of ecosystem-wide graph views. Reverse relationships and relationship-index services can aggregate useful views across distributed declarations, but their results remain coverage-limited and cannot acquire canonical ownership through aggregation. Event delivery follows the same authority boundary: lifecycle events may improve synchronisation and responsiveness, but they cannot disclose relationship information beyond the visibility and permission basis of the underlying state.

The next catalogue part should begin with `REM-05-489` / source Section 44 and continue catalogue numbering from `REL-REL-309`.