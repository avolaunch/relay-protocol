# EA-05-05 — Relationship Requirements Catalogue

## Part 10 — Authority-Bearing Relationships and Groups

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing authority-bearing relationships and the foundational Relay Group model.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-182`, following Part 9's coverage of relationship evidence and verification. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 24–25 and REM-05 requirements `REM-05-251` through `REM-05-278`.

It defines normative requirements governing:

- support for authority-bearing relationships;
- representative authority-bearing relationship types;
- explicit authority capabilities, scope, duration, approval, revocation, evidence and re-delegation rules;
- prevention of implicit broad authority from generic relationship labels;
- Relay Group definition and permitted relationship, access and communication uses;
- alternative group representations;
- semantic distinction among personal lists, mutually recognised groups, formal organisations and application-generated audience segments.

Section 26 personal groups and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-182

### Title

Authority-Bearing Relationship Support

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relationship Model **MUST** support relationship types that convey explicitly defined authority to a Source or Target.

### Rationale

Relay relationships are not limited to descriptive or social connections. Some relationships carry operational authority and therefore require explicit, independently interpretable authority semantics.

### Source

- REM-05-251
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-183

### Title

Representative Authority-Bearing Relationship Types

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** represent administrator, legal-representative, guardian, application-operator, delegated-publisher or repository-custodian relationships that convey defined authority.

### Rationale

Section 24 presents these as representative authority-bearing relationship types. They demonstrate the breadth of the model without creating a closed vocabulary or implying identical capabilities for different roles.

### Source

- REM-05-252
- REM-05-253
- REM-05-254
- REM-05-255
- REM-05-256
- REM-05-257
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-184

### Title

Explicit Authority Capabilities

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify the exact capabilities it conveys.

### Rationale

A role label cannot safely substitute for an explicit capability set. Authority must be sufficiently defined for implementations to determine what actions are actually permitted.

### Source

- REM-05-258
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06

---

## REL-REL-185

### Title

Explicit Authority Scope

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify the scope within which its capabilities apply.

### Rationale

Authority must be bounded to the organisation, repository, collection, record, context or other defined domain in which the capabilities are valid.

### Source

- REM-05-259
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06

---

## REL-REL-186

### Title

Explicit Authority Duration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify its duration or continuing-validity condition.

### Rationale

Authority must have an interpretable lifecycle. Even where duration is indefinite, implementations need a defined basis for determining whether the authority remains current.

### Source

- REM-05-260
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-187

### Title

Explicit Authority Approval Requirements

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify the approvals required for its creation, activation or continuation.

### Rationale

Authority cannot safely arise from ambiguous or assumed consent. The relationship must identify the approval conditions under which its authority becomes or remains valid.

### Source

- REM-05-261
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06

---

## REL-REL-188

### Title

Explicit Authority Revocation Mechanism

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify how the conveyed authority can be revoked.

### Rationale

Authority must not become irrevocable merely because a relationship record exists. Its lifecycle needs a defined revocation path that implementations can evaluate and enforce.

### Source

- REM-05-262
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-189

### Title

Explicit Authority Evidence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify or reference the evidence supporting the authority.

### Rationale

Because authority-bearing relationships can enable consequential actions, their authority must have an explicit evidentiary basis rather than relying solely on an asserted role label.

### Source

- REM-05-263
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- CI-10

---

## REL-REL-190

### Title

Explicit Authority Re-Delegation Rule

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An authority-bearing relationship **MUST** specify whether the granted authority may be delegated onward.

### Rationale

Re-delegation materially changes the reach of an authority grant. The relationship must therefore make re-delegation permission explicit rather than allowing silence to be interpreted as permission.

### Source

- REM-05-264
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06

---

## REL-REL-191

### Title

No Implicit Broad Authority From Generic Relationship Labels

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A generic relationship label **MUST NOT**, by itself, confer authority beyond the explicit capabilities and scope defined by the relationship record and applicable schema.

### Rationale

Labels such as `administrator` can carry different meanings in different systems. Relay must not convert a broad semantic label into unspecified privilege.

### Source

- REM-05-265
- `design-notes/05-relationship-model.md`, Section 24

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-192

### Title

Relay Group Definition

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Group **MUST** represent a defined set of identities used for one or more relationship, access or communication purposes.

### Rationale

The group abstraction provides a portable way to address identity sets without requiring every set to be a formal organisation or mutually recognised social entity.

### Source

- REM-05-266
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-12

---

## REL-REL-193

### Title

Relay Group Functional Uses

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Where the applicable schema permits it, a Relay Group **MAY** be used as a relationship context, Source, Target or organisational set; as an access audience or access-control set; or as a participant or audience set for communication.

### Rationale

Section 25 defines groups as identity sets usable across relationship, access and communication functions. These uses are optional and do not themselves establish one universal group semantic or messaging service.

### Source

- REM-05-267
- REM-05-268
- REM-05-269
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-194

### Title

Relay Group Representation Options

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Group **MAY** be represented by a dedicated group record, membership relationship records, a group-controlled Relay Identity, a private access list, or a compatible combination of these representations.

### Rationale

Section 25 intentionally permits multiple group representations. Different group semantics and governance models may require different combinations of group metadata, membership provenance, identity control and private access state.

### Source

- REM-05-270
- REM-05-271
- REM-05-272
- REM-05-273
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-02
- CI-08
- CI-12

---

## REL-REL-195

### Title

Material Group-Type Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Group model **MUST** distinguish materially different group types rather than treating all identity sets as semantically equivalent.

### Rationale

A private list, mutually recognised group, formal organisation and application-generated audience can contain similar identity sets while carrying fundamentally different ownership, consent and governance semantics.

### Source

- REM-05-274
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-196

### Title

Personal Organisational List Distinction

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Group model **MUST** distinguish a personal organisational list controlled by one identity from other group types.

### Rationale

Membership in a personal list can be unilateral and private. It therefore must not be treated as evidence that listed identities recognised or joined a mutual group.

### Source

- REM-05-275
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-197

### Title

Mutually Recognised Group Distinction

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Group model **MUST** distinguish a group whose participating identities mutually recognise the group or their membership.

### Rationale

Mutual recognition carries consent and authorisation semantics that are absent from unilateral personal lists and derived application audiences.

### Source

- REM-05-276
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-198

### Title

Formal Organisation Distinction

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Relay Group model **MUST** distinguish a formal organisation from an informal or personal grouping.

### Rationale

Formal organisations may possess their own identity, governance, authority and evidence requirements and therefore cannot safely be collapsed into generic group semantics.

### Source

- REM-05-277
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-199

### Title

Application-Generated Audience Segment Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Relay Group model **MUST** distinguish an application-generated audience segment from a user-controlled or mutually recognised group.

### Rationale

An application-derived segment reflects application processing, not necessarily member knowledge, consent or group recognition. Keeping that distinction explicit prevents derived audiences from being misrepresented as voluntarily constituted groups.

### Source

- REM-05-278
- `design-notes/05-relationship-model.md`, Section 25

### Related Invariants

- CI-10
- CI-12

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined example set, functional capability set or representation set:

- `REM-05-252` through `REM-05-257` are consolidated into `REL-REL-183`. Administrator, legal representative, guardian, application operator, delegated publisher and repository custodian are Section 24 examples of authority-bearing relationship types. They remain optional schema capabilities rather than six mandatory relationship schemas.
- `REM-05-267` through `REM-05-269` are consolidated into `REL-REL-193`. Relationship, access and communication are the three source-defined functional uses of a Relay Group and share optional semantics.
- `REM-05-270` through `REM-05-273` are consolidated into `REL-REL-194`. Group record, membership relationship records, group-controlled Relay Identity and private access list are the four source-listed representation options for one Relay Group abstraction.

No other REM-05 entries in the covered range are consolidated. Exact capabilities, scope, duration, approvals, revocation, evidence and re-delegation remain separate mandatory authority constraints because each is independently necessary and testable. The generic-label prohibition remains distinct from those positive specification requirements. The overall group-type distinction and each required concrete distinction remain separate so that implementations cannot satisfy the taxonomy requirement while omitting one of the source-mandated semantic boundaries.

All REM-05 requirements from `REM-05-251` through `REM-05-278` are represented exactly once in the catalogue mapping, either independently or through the three explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 10 begins at `REM-05-251`, immediately after Part 9's final covered requirement `REM-05-250`.
- Coverage ends at `REM-05-278`, the end of source Section 25.
- Section 26 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 24–25.

## Numbering verification

- First catalogue requirement: `REL-REL-182`.
- Final catalogue requirement: `REL-REL-199`.
- Catalogue numbering continues directly from Part 9's `REL-REL-181`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Authority-bearing relationship examples remain `MAY` schema capabilities rather than mandatory universal relationship types.
- All seven source-mandated authority dimensions remain separate `MUST` requirements.
- Generic role labels remain prohibited from silently conveying unspecified broad authority.
- Relay Group functional uses and representations remain `MAY` options.
- The group model's taxonomy requirement and all four source-defined group distinctions retain `MUST` strength.
- Application-generated audiences remain explicitly distinguishable from user-controlled or mutually recognised groups.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes that authority in Relay must be explicit rather than inferred from role labels: capabilities, scope, duration, approvals, revocation, evidence and re-delegation are independently specified dimensions of an authority-bearing relationship. It then establishes Relay Groups as a flexible identity-set abstraction while preserving the semantic differences among unilateral personal lists, mutually recognised groups, formal organisations and application-generated audiences.

The next catalogue part should begin with `REM-05-279` / source Section 26 and continue catalogue numbering from `REL-REL-200`.