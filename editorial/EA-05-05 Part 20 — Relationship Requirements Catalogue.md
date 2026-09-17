# EA-05-05 — Relationship Requirements Catalogue

## Part 20 — Algorithmic Use and Relationship-Based Access

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing application use of relationship records as algorithmic inputs and explicit relationship-based access rules.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-334`, following Part 19's coverage of relationship duplication, uniqueness and application-specific metadata. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 49–50 and REM-05 requirements `REM-05-524` through `REM-05-542`.

It defines normative requirements governing:

- optional use of authorised relationship records in feeds, recommendations, search ranking, access decisions and contextual trust calculations;
- separation of portable relationship semantics from application-specific algorithmic interpretation;
- optional follow-based feed, ranking and notification behaviours;
- client-level and subscription-level control of algorithmic effects;
- optional relationship-based access rules;
- qualifying relationship type, reciprocity and context;
- dynamic relationship-eligibility evaluation;
- access consequences of relationship termination, revocation or expiration; and
- revocation of future dynamically evaluated access when a qualifying relationship ends.

Section 51 relationship-based permissions and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-334

### Title

Authorised Relationship Records as Algorithmic Inputs

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** use authorised relationship records as inputs to feed construction or ranking, recommendation systems, search ranking, access decisions governed by applicable relationship-based access rules, and contextual trust calculations.

### Rationale

Relationship data can inform multiple application behaviours without prescribing any single algorithm. Authorisation remains necessary because relationship records may be private or context-restricted, and access decisions remain subject to explicit access-policy semantics.

### Source

- REM-05-524
- REM-05-525
- REM-05-526
- REM-05-527
- REM-05-528
- `design-notes/05-relationship-model.md`, Section 49

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-335

### Title

No Mandatory Algorithmic Interpretation of Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay relationship record **MUST NOT** be interpreted as prescribing a single mandatory feed, recommendation, ranking, access or trust algorithm.

### Rationale

The relationship model defines portable relationship meaning, not a universal application algorithm. Compatible applications may make different authorised use of the same relationship state.

### Source

- REM-05-529
- `design-notes/05-relationship-model.md`, Section 49

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-336

### Title

Optional Follow Algorithm Interpretations

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** interpret a follow relationship as an input to show all eligible posts from the followed identity, prioritise eligible posts, include eligible activity in a selected feed, or permit notifications subject to applicable user preferences.

### Rationale

The source provides these as examples of legitimate client-level interpretations of a portable follow relationship. They are optional behaviours rather than protocol-defined consequences of following.

### Source

- REM-05-530
- REM-05-531
- REM-05-532
- REM-05-533
- `design-notes/05-relationship-model.md`, Section 49

### Related Invariants

- CI-12

---

## REL-REL-337

### Title

Client or Subscription Control of Algorithmic Effects

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The specific algorithmic effects assigned to a relationship **MUST** remain client-level or subscription-level choices unless a separate protocol rule explicitly defines an effect.

### Rationale

Portable relationship semantics and application-specific algorithmic behaviour are separate layers. Preserving that separation prevents one application's ranking or notification model from becoming an unintended protocol requirement.

### Source

- REM-05-534
- `design-notes/05-relationship-model.md`, Section 49

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-338

### Title

Relationship-Based Access Rule Capability

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay record **MAY** define an access rule whose eligibility depends on the existence of an active qualifying relationship.

### Rationale

Relationship state can provide a useful explicit audience criterion while remaining distinct from broad authority inherent in the social meaning of the relationship.

### Source

- REM-05-535
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-339

### Title

Collaborator Relationship-Based Audience

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship-based access rule **MAY** define current collaborators as an eligible audience, provided the rule defines what constitutes a qualifying current collaborator.

### Rationale

“Current collaborators” is a source-defined example of a relationship-derived audience, not an independently self-defining protocol category.

### Source

- REM-05-536
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-340

### Title

Qualifying Relationship Type for Access

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship-based access rule **MUST** identify the relationship type that qualifies a requester for access.

### Rationale

The mere existence of some relationship between identities is insufficient to establish access. Eligibility must be tied to an explicitly identified relationship type.

### Source

- REM-05-537
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-341

### Title

Relationship Reciprocity Requirement for Access

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship-based access rule **MUST** specify whether the qualifying relationship must be reciprocal or whether a unilateral relationship is sufficient.

### Rationale

Reciprocal and unilateral relationships express different states of agreement. Access policy must not leave that distinction implicit.

### Source

- REM-05-538
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-342

### Title

Relationship Context for Access

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship-based access rule **MUST** identify the applicable relationship context where context is relevant to determining eligibility.

### Rationale

A relationship valid in one project, organisation, role or other context must not silently confer access in an unrelated context.

### Source

- REM-05-539
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-343

### Title

Dynamic Relationship Eligibility Evaluation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship-based access rule **MUST** specify whether relationship eligibility is evaluated dynamically at the time access is requested or exercised.

### Rationale

Dynamic and non-dynamic access models have materially different lifecycle consequences. The policy must state which model applies rather than leaving consumers to infer it.

### Source

- REM-05-540
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-344

### Title

Relationship Termination Effect on Access

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship-based access rule **MUST** define the effect that termination, revocation or expiration of the qualifying relationship has on access.

### Rationale

Access policy must remain determinate across relationship lifecycle changes. Otherwise an ended relationship could leave ambiguous residual authority.

### Source

- REM-05-541
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-345

### Title

Future Access Revocation for Ended Dynamic Relationships

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where relationship-based access is dynamically evaluated, ending the qualifying relationship **SHOULD** revoke future access dependent on that relationship.

### Rationale

A dynamically evaluated rule derives current eligibility from current relationship state. Once the qualifying relationship ends, future access should normally cease. This does not by itself require retroactive deletion of data already lawfully obtained or invalidate actions already validly completed.

### Source

- REM-05-542
- `design-notes/05-relationship-model.md`, Section 50

### Related Invariants

- CI-10
- CI-12

---

# 4. Consolidation and Traceability Record

This part consolidates only source requirements that form one explicit option set:

- `REM-05-524` through `REM-05-528` are consolidated into `REL-REL-334`. Feeds, recommendations, search ranking, access decisions and contextual trust calculations are the five source-defined optional algorithmic uses of authorised relationship records and share `MAY` strength.
- `REM-05-530` through `REM-05-533` are consolidated into `REL-REL-336`. Showing all eligible posts, prioritising posts, selected-feed inclusion and notification eligibility are the four source-defined optional interpretations of a follow relationship and share `MAY` strength.

No other REM-05 entries in the covered range are consolidated. The prohibition on a single prescribed algorithm, client/subscription control, relationship-based access capability, collaborator audience example, qualifying type, reciprocity, context, dynamic evaluation, lifecycle consequences and dynamic future-access revocation remain independently meaningful and testable requirements.

All REM-05 requirements from `REM-05-524` through `REM-05-542` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 20 begins at `REM-05-524`, immediately after Part 19's final covered requirement `REM-05-523`.
- Coverage ends at `REM-05-542`, the end of source Section 50 and REM-05 Part 10.
- Section 51 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 49–50.

## Numbering verification

- First catalogue requirement: `REL-REL-334`.
- Final catalogue requirement: `REL-REL-345`.
- Catalogue numbering continues directly from Part 19's `REL-REL-333`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Algorithmic uses of authorised relationship records remain optional.
- Relationships remain prohibited from prescribing a single mandatory algorithmic interpretation.
- Follow-based feed, ranking and notification interpretations remain optional examples.
- Specific algorithmic effects remain client-level or subscription-level choices unless separately defined by protocol rule.
- Relationship-based access remains optional and policy-driven.
- Qualifying relationship type, reciprocity, applicable context, dynamic-evaluation treatment and relationship-ending consequences remain mandatory policy declarations.
- Dynamic relationship termination retains `SHOULD` strength for revocation of future dependent access.
- REM-05 Part 10's remediated treatment remains intact; no requirement in this part re-strengthens the remediated semantics of Sections 46–48.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves a clear separation between portable relationship meaning and application behaviour. Relationships may be used as authorised inputs to algorithms, but they do not dictate a universal feed, ranking, recommendation, trust or access interpretation. Where relationships are used for access, the authority comes from an explicit access rule whose qualifying type, reciprocity, context and lifecycle semantics are defined, rather than from social meaning alone.

The next catalogue part should begin with `REM-05-543` / source Section 51 and continue catalogue numbering from `REL-REL-346`.