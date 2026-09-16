# EA-05-05 — Relationship Requirements Catalogue

## Part 5 — Relationship Continuity and Follows

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing operational relationship portability and the semantics and limitations of follow relationships.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-119`, following Part 4's coverage of relationship status, lifecycle and ownership. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 14–15 and REM-05 requirements `REM-05-132` through `REM-05-151`.

It defines normative requirements governing:

- stable identity and Record URI continuity;
- compatible schema understanding;
- source and Target continuity across provider migration;
- discovery of current repositories;
- application replacement without relationship recreation;
- follow direction and public-activity semantics;
- follow use as a receipt, discovery and prioritisation signal;
- limitations on access, messaging, endorsement, friendship, authority and reciprocity;
- use of follow records as one feed-construction input.

Section 16 subscriptions and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-119

### Title

Stable Relay Identity for Relationship Portability

**Level:** Constitutional

**Normative Keyword:** **REQUIRES**

### Statement

Operational relationship portability **REQUIRES** each participating Relay Identity to retain a stable Relay Identifier.

### Rationale

Relationships cannot remain portable if participant identity changes merely because an application or provider changes. Stable Relay Identifiers anchor the relationship independently of mutable handles or provider-local usernames.

### Source

- REM-05-132
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-01
- CI-05

---

## REL-REL-120

### Title

Stable Relationship Record URI

**Level:** Constitutional

**Normative Keyword:** **REQUIRES**

### Statement

Operational relationship portability **REQUIRES** the relevant relationship records to preserve stable Record URIs.

### Rationale

The logical declaration must remain addressable across application replacement and repository migration rather than becoming a new relationship solely because infrastructure changed.

### Source

- REM-05-133
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-03
- CI-08

---

## REL-REL-121

### Title

Compatible Relationship Schema Understanding

**Level:** Architectural

**Normative Keyword:** **REQUIRES**

### Statement

Operational relationship portability **REQUIRES** compatible applications to understand the applicable relationship schema sufficiently to interpret the connection.

### Rationale

Stable identifiers alone do not provide semantic interoperability. A compatible application must understand enough of the governing schema to interpret the relationship it is reading.

### Source

- REM-05-134
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-12

---

## REL-REL-122

### Title

Provider Migration Preserves Relationship Source

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing Relay Provider **MUST NOT** alter the Source identity of a relationship declaration solely because the provider changed.

### Rationale

Provider migration is an infrastructure event. It must not change who made the relationship declaration.

### Source

- REM-05-135
- REM-05-139
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-01
- CI-03

---

## REL-REL-123

### Title

Provider Migration Preserves Relationship Target

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Changing Relay Provider **MUST NOT** alter the Target identity or Target reference of a relationship declaration solely because the provider changed.

### Rationale

Migration of repository infrastructure must not silently become a semantic change to the object of the relationship.

### Source

- REM-05-136
- REM-05-140
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-03
- CI-05

---

## REL-REL-124

### Title

Current Repository Discovery for Portable Relationships

**Level:** Architectural

**Normative Keyword:** **REQUIRES**

### Statement

Operational relationship portability **REQUIRES** applications to be able to discover the current repositories associated with the identities or records involved.

### Rationale

Stable identifiers remain operational after migration only if compatible applications can resolve them to the repositories that currently hold the relevant authoritative records.

### Source

- REM-05-137
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-03
- CI-05

---

## REL-REL-125

### Title

Application Replacement Without Relationship Recreation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Replacing one compatible application with another **MUST NOT** require recreation of the underlying relationship record solely because the application changed.

### Rationale

Relationship state belongs to the participating identities and repositories rather than to the application that happens to present or operate on it.

### Source

- REM-05-138
- `design-notes/05-relationship-model.md`, Section 14

### Related Invariants

- CI-04
- AI-07

---

## REL-REL-126

### Title

Follow as Directed Declaration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A follow relationship **MUST** be represented as a directed declaration from a Source to a Target.

### Rationale

A follow is unilateral: its existence depends on the Source declaration and does not require a matching declaration by the Target.

### Source

- REM-05-141
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- AI-08

---

## REL-REL-127

### Title

Follow as Public-Activity Interest Signal

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A follow **MAY** indicate that the Source wishes to receive, discover or prioritise public activity from the Target.

### Rationale

Section 15 defines these three purposes as aspects of the same follow declaration. The relationship supplies an interest signal without prescribing guaranteed delivery, discovery or a universal ranking algorithm.

### Source

- REM-05-142
- REM-05-143
- REM-05-144
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- AI-07

---

## REL-REL-128

### Title

Follow Does Not Grant Restricted-Record Access

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A follow relationship **MUST NOT** be interpreted as granting access to restricted records.

### Rationale

Following is an interest relationship, not an access-control grant. Restricted access requires a separate valid visibility, audience or permission basis.

### Source

- REM-05-145
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-129

### Title

Follow Does Not Grant Messaging Rights

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A follow relationship **MUST NOT** be interpreted as granting messaging rights.

### Rationale

Communication eligibility is a separate capability and cannot be inferred solely from a unilateral follow declaration.

### Source

- REM-05-146
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- CI-06

---

## REL-REL-130

### Title

Follow Does Not Imply Endorsement

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A follow relationship **MUST NOT** be represented as an endorsement by the Source of the Target.

### Rationale

Interest in another identity's public activity does not establish approval, verification or endorsement of that identity.

### Source

- REM-05-147
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- CI-12

---

## REL-REL-131

### Title

Follow Does Not Imply Friendship

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A follow relationship **MUST NOT** be represented as friendship.

### Rationale

Friendship is a distinct relationship meaning and may require reciprocity or other schema-defined conditions that a unilateral follow does not satisfy.

### Source

- REM-05-148
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- CI-12
- AI-08

---

## REL-REL-132

### Title

Follow Does Not Convey Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A follow relationship **MUST NOT** be interpreted as conveying authority over the Target, the Target's repository or the Target's records.

### Rationale

Authority-bearing relationships require explicit semantics and stricter validation. A follow alone cannot create technical authority.

### Source

- REM-05-149
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- CI-06

---

## REL-REL-133

### Title

Follow Does Not Imply Reciprocity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A follow by one identity **MUST NOT** be interpreted as a reciprocal follow by the Target.

### Rationale

A reciprocal follow exists only where the Target independently creates or authorises its own follow declaration.

### Source

- REM-05-150
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- AI-08

---

## REL-REL-134

### Title

Follow Records as Feed Input

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Applications **MAY** use follow records as one input when constructing feeds.

### Rationale

Follow state can inform application behaviour without making Relay responsible for one mandatory feed or ranking algorithm.

### Source

- REM-05-151
- `design-notes/05-relationship-model.md`, Section 15

### Related Invariants

- AI-07

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express the same independently testable protocol behaviour:

- `REM-05-135` and `REM-05-139` are consolidated into `REL-REL-122`. Both express the same Section 14 requirement that Relay Provider migration must not alter the relationship Source.
- `REM-05-136` and `REM-05-140` are consolidated into `REL-REL-123`. Both express the same Section 14 requirement that Relay Provider migration must not alter the relationship Target.
- `REM-05-142`, `REM-05-143` and `REM-05-144` are consolidated into `REL-REL-127`. The source defines receipt, discovery and prioritisation as three purposes of one follow declaration. The consolidated requirement preserves all three permitted uses without treating them as three independently required capabilities.

No other REM-05 entries in the covered range are consolidated. Stable identity, Record URI, schema understanding and repository discovery are distinct portability conditions; application replacement is distinct from provider migration; and each follow limitation remains separate because access, messaging, endorsement, friendship, authority and reciprocity are independently meaningful semantic boundaries.

All REM-05 requirements from `REM-05-132` through `REM-05-151` are represented exactly once in the catalogue mapping, either independently or through the three explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 5 begins at `REM-05-132`, immediately after Part 4's final covered requirement `REM-05-131`.
- Coverage ends at `REM-05-151`, the end of source Section 15.
- Section 16 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 14–15.

## Numbering verification

- First catalogue requirement: `REL-REL-119`.
- Final catalogue requirement: `REL-REL-134`.
- Catalogue numbering continues directly from Part 4's `REL-REL-118`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- The Section 14 portability conditions remain independent except where the source repeats the same Source/Target migration rule.
- The Section 15 public-activity purposes remain `MAY` semantics rather than guaranteed delivery or algorithmic requirements.
- Follow limitations retain their individual `MUST NOT` boundaries.
- No application feed algorithm has been inferred or prescribed.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes the operational continuity conditions that make relationships portable across applications and Relay Providers, then applies the model to the first concrete relationship type: follow. Follow remains a unilateral interest signal and is deliberately prevented from silently acquiring access, messaging, endorsement, friendship, authority or reciprocal semantics.

The next catalogue part should begin with `REM-05-152` / source Section 16 and continue catalogue numbering from `REL-REL-135`.