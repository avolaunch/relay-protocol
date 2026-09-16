# EA-05-05 — Relationship Requirements Catalogue

## Part 6 — Subscriptions, Followers and Derived Audiences

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing subscriptions and the representation, indexing and presentation of follower-derived audiences.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-135`, following Part 5's coverage of relationship continuity and follow semantics. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 16–17 and REM-05 requirements `REM-05-152` through `REM-05-173`.

It defines normative requirements governing:

- subscription direction and activity-delivery scope;
- subscription specificity relative to follows;
- subscription filtering and delivery preferences;
- Target autonomy over requested delivery methods;
- portable follower representation;
- follower counts as derived rather than canonical graph state;
- distributed follower relationship records;
- optional follower indexes;
- coverage, visibility, blocking, availability, revocation and freshness dependencies of derived counts;
- truthful presentation of derived follower and audience counts.

Section 18 private relationships and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-135

### Title

Subscription as Directed Activity-Delivery Relationship

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A subscription **MUST** be represented as a directed relationship from a Source to a Target and **MUST** identify or permit identification of the category of activity whose delivery is requested.

### Rationale

Direction and defined activity scope together distinguish a subscription from an undifferentiated or reciprocal relationship. Both properties are contained in the source definition of a subscription.

### Source

- REM-05-152
- REM-05-153
- `design-notes/05-relationship-model.md`, Section 16

### Related Invariants

- AI-08
- CI-12

---

## REL-REL-136

### Title

Subscription Specificity Relative to Follow

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A subscription **MAY** apply narrower activity, content or delivery criteria than a follow relationship.

### Rationale

Subscriptions can express a more specific request than a general follow and therefore must not be assumed to be semantically interchangeable with follows.

### Source

- REM-05-154
- `design-notes/05-relationship-model.md`, Section 16

### Related Invariants

- CI-12

---

## REL-REL-137

### Title

Subscription Activity Filters

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A subscription **MAY** restrict requested delivery by one or more specified record collections, topics or event types.

### Rationale

Collections, topics and event types are the source-defined content and activity filters through which a subscription can narrow the requested delivery scope.

### Source

- REM-05-155
- REM-05-156
- REM-05-157
- `design-notes/05-relationship-model.md`, Section 16

### Related Invariants

- CI-12

---

## REL-REL-138

### Title

Subscription Delivery Preferences

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A subscription **MAY** declare a requested delivery method, delivery frequency, one or more language preferences, and requested priority.

### Rationale

These values describe subscriber delivery preferences rather than independent relationship types or guarantees that the Target will satisfy each preference.

### Source

- REM-05-158
- REM-05-159
- REM-05-160
- REM-05-161
- `design-notes/05-relationship-model.md`, Section 16

### Related Invariants

- AI-07

---

## REL-REL-139

### Title

Subscription Delivery Non-Guarantee

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A subscription request **MUST NOT** be interpreted as obligating the Target to provide every requested delivery method.

### Rationale

The subscription expresses the Source's request. It does not override the Target's supported delivery capabilities or autonomy.

### Source

- REM-05-162
- `design-notes/05-relationship-model.md`, Section 16

### Related Invariants

- CI-06

---

## REL-REL-140

### Title

Followers Not Reduced to Provider Counter

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A compliant relationship implementation **SHOULD NOT** represent a person's followers solely as a provider-maintained numeric counter.

### Rationale

A provider counter cannot substitute for the portable relationship records that constitute the underlying follower graph.

### Source

- REM-05-163
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-03
- CI-04

---

## REL-REL-141

### Title

Follower Count as Derived Data

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A follower count **MUST** be treated as a derived value rather than as the canonical relationship data itself.

### Rationale

The canonical graph consists of relationship declarations. Counts are computed views over those records and may vary with visibility, indexing and availability.

### Source

- REM-05-164
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-08

---

## REL-REL-142

### Title

Distributed Follower Graph

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The follower graph **MUST** be understood as relationship records distributed across the repositories of follower identities.

### Rationale

Incoming follower state is not canonically owned by the followed identity or by a central provider. Each follower's declaration remains part of the distributed relationship graph.

### Source

- REM-05-165
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-02
- CI-08

---

## REL-REL-143

### Title

Derived Follower Index

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A service **MAY** build an index or derived count of known active follower relationships, provided that the index is not treated as a replacement for the authoritative distributed relationship records.

### Rationale

Indexes are useful discovery and presentation services but remain derived views over independently authoritative relationship declarations.

### Source

- REM-05-166
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-08

---

## REL-REL-144

### Title

Derived Follower Count Coverage Dependencies

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A derived follower count **MUST** account for or appropriately disclose the effects of indexed-repository coverage, relationship visibility, applicable block rules, unavailable identities, revoked follow records and index freshness.

### Rationale

Section 17 identifies these six factors as dependencies of a derived follower count. They collectively determine whether the resulting count is current, visible and complete for a particular indexing context.

### Source

- REM-05-167
- REM-05-168
- REM-05-169
- REM-05-170
- REM-05-171
- REM-05-172
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-05
- AI-07
- AI-09

---

## REL-REL-145

### Title

No False Precision or Completeness for Derived Audiences

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** present a derived follower or audience count as more precise or complete than the underlying indexed data permits.

### Rationale

Derived graph statistics can be incomplete or stale. Presentation must therefore reflect the actual evidential limits of the indexed data rather than imply canonical completeness.

### Source

- REM-05-173
- `design-notes/05-relationship-model.md`, Section 17

### Related Invariants

- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express the same independently testable protocol behaviour or form one source-defined compound capability:

- `REM-05-152` and `REM-05-153` are consolidated into `REL-REL-135`. Both derive from the single Section 16 definition of a subscription as a directed relationship requesting delivery of a defined category of activity.
- `REM-05-155` through `REM-05-157` are consolidated into `REL-REL-137`. Collections, topics and event types are the three source-defined activity/content filtering dimensions of one optional subscription-filter capability.
- `REM-05-158` through `REM-05-161` are consolidated into `REL-REL-138`. Delivery method, frequency, language and priority are source-listed delivery preferences and do not create four distinct relationship semantics.
- `REM-05-167` through `REM-05-172` are consolidated into `REL-REL-144`. Section 17 presents indexed repositories, relationship visibility, block rules, unavailable identities, revoked records and index freshness as six dependencies of the same derived follower count. The consolidated requirement preserves every dependency and the mandatory treatment established by the verified extraction.

No other REM-05 entries in the covered range are consolidated. Subscription specificity and Target delivery autonomy are distinct behaviours; provider-counter avoidance, derived-data status, distributed graph structure and optional indexing define separate architectural properties; and truthful presentation of derived counts remains an independently testable application obligation.

All REM-05 requirements from `REM-05-152` through `REM-05-173` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 6 begins at `REM-05-152`, immediately after Part 5's final covered requirement `REM-05-151`.
- Coverage ends at `REM-05-173`, the end of source Section 17.
- Section 18 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 16–17.

## Numbering verification

- First catalogue requirement: `REL-REL-135`.
- Final catalogue requirement: `REL-REL-145`.
- Catalogue numbering continues directly from Part 5's `REL-REL-134`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Subscription filter and preference capabilities remain `MAY` rather than mandatory universal fields.
- The Target delivery non-guarantee remains a distinct `MUST NOT` semantic boundary.
- Follower counts remain derived data rather than canonical graph state.
- All six source-defined count dependencies remain visible after consolidation.
- The prohibition on false precision or completeness remains independently testable.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part distinguishes a subscription's requested delivery scope from any obligation on the Target to satisfy that request, then establishes follower audiences as derived views over a distributed graph of relationship records. Provider-maintained counters and indexes may assist presentation and discovery, but neither replaces the canonical relationship declarations from which follower state is derived.

The next catalogue part should begin with `REM-05-174` / source Section 18 and continue catalogue numbering from `REL-REL-146`.