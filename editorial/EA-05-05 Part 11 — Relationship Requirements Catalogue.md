# EA-05-05 — Relationship Requirements Catalogue

## Part 11 — Personal Groups, Formal Groups and Membership

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing personal groups, formal groups and membership semantics.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-200`, following Part 10's coverage of authority-bearing relationships and foundational group semantics. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 26–28 and REM-05 entries `REM-05-279` through `REM-05-320`.

It defines normative requirements governing:

- single-identity control and optional privacy of personal groups;
- private personal-group membership and consent boundaries;
- permitted personal-group uses;
- formal-group identity and governance;
- optional formal-membership admission conditions;
- independently verifiable formal membership;
- membership modes and lifecycle states;
- membership-schema issuer, consent, visibility, role, authority, expiration and removal definitions;
- independent repository authority between organisations and members.

`REM-05-291` through `REM-05-295` are retained in this part's traceability record as explicit non-normative model examples. They do not receive `REL-REL` catalogue identifiers and do not create normative protocol requirements.

Section 29 relationship requests and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-200

### Title

Single-Identity Control of Personal Groups

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A personal group **MUST** be controlled by one Relay Identity.

### Rationale

A personal group is a unilateral organisational construct. Its control semantics distinguish it from mutually recognised or jointly governed groups.

### Source

- REM-05-279
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-201

### Title

Private Personal Groups

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A personal group **MAY** be private.

### Rationale

Personal organisation must not require disclosure of the group itself or its membership to participants or external observers.

### Source

- REM-05-280
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-202

### Title

Controller-Only Personal-Group Membership Visibility

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An implementation **MUST** support a personal group whose membership is visible only to the controlling identity.

### Rationale

The source explicitly permits membership knowledge to remain solely with the group controller. Inclusion therefore cannot depend on disclosure to the included identity or third parties.

### Source

- REM-05-281
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-203

### Title

Personal-Group Inclusion Does Not Imply Member Acceptance

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Adding an identity to a personal group **MUST NOT** be interpreted as acceptance by that identity of the group membership or associated relationship label.

### Rationale

Personal-group inclusion is an action by the controller, not an independently authorised declaration by the included identity.

### Source

- REM-05-282
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-204

### Title

No Public Acceptance Claim From Personal-Group Inclusion

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** present inclusion in a personal group as a publicly accepted relationship label unless the included identity has independently authorised that representation.

### Rationale

A controller's private organisational label must not be transformed into a public claim about another identity's consent or relationship status.

### Source

- REM-05-283
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-09
- CI-10

---

## REL-REL-205

### Title

Personal-Group Functional Uses

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A personal group **MAY** be used for visibility, feed filtering, access, notifications and organisational purposes.

### Rationale

Section 26 defines these as permitted uses of the same unilateral personal-group construct. Using a group for one of these purposes does not itself alter its privacy or consent semantics.

### Source

- REM-05-284
- REM-05-285
- REM-05-286
- REM-05-287
- REM-05-288
- `design-notes/05-relationship-model.md`, Section 26

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-206

### Title

Formal-Group Relay Identity

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A formal group **MAY** be represented by and operate through its own Relay Identity.

### Rationale

A distinct Relay Identity allows a formal group to act as a protocol participant where its governance model requires independent group identity, without requiring every formal group to use that representation.

### Source

- REM-05-289
- `design-notes/05-relationship-model.md`, Section 27

### Related Invariants

- CI-02
- CI-12

---

## REL-REL-207

### Title

Formal-Group Governance Rules

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A formal group **MAY** define governance rules applicable to its membership, authority and operation.

### Rationale

Formal groups may require explicit governance for admission, approval and multi-party decisions rather than relying on the unilateral control semantics of personal groups.

### Source

- REM-05-290
- `design-notes/05-relationship-model.md`, Section 27

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-208

### Title

Formal-Group Membership Admission Conditions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A formal-group membership schema **MAY** require invitation, prospective-member acceptance, authorised-administrator approval, a valid credential, payment, multi-party authorisation, or a compatible combination of these conditions before membership becomes active.

### Rationale

Section 27 lists these as alternative or combinable admission conditions. Consolidation preserves the optional character of each condition while keeping admission policy schema-governed.

### Source

- REM-05-296
- REM-05-297
- REM-05-298
- REM-05-299
- REM-05-300
- REM-05-301
- `design-notes/05-relationship-model.md`, Section 27

### Related Invariants

- CI-06
- CI-10
- CI-12

---

## REL-REL-209

### Title

Independently Verifiable Formal-Group Membership

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Formal-group membership **SHOULD** be represented through independently verifiable relationship records.

### Rationale

Formal membership should remain resolvable and verifiable independently of a provider-maintained list or application-only database.

### Source

- REM-05-302
- `design-notes/05-relationship-model.md`, Section 27

### Related Invariants

- CI-08
- CI-10

---

## REL-REL-210

### Title

Membership Modes and Lifecycle States

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A membership schema **MAY** support `open`, `requested`, `invited`, `approved`, `credential-based`, `paid`, `temporary`, `revoked` and `expired` membership modes or lifecycle states as applicable to the schema.

### Rationale

Section 28 defines these as optional membership states or modes. They describe different admission, evidence, commercial and lifecycle conditions and do not require every membership schema to implement every value.

### Source

- REM-05-303
- REM-05-304
- REM-05-305
- REM-05-306
- REM-05-307
- REM-05-308
- REM-05-309
- REM-05-310
- REM-05-311
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-10
- CI-12
- AI-09

---

## REL-REL-211

### Title

Membership Issuer Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define which identity or authority may issue membership.

### Rationale

Explicit issuer rules prevent unauthorised parties from creating records that appear to establish valid formal membership.

### Source

- REM-05-312
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-06
- CI-10

---

## REL-REL-212

### Title

Membership Acceptance Requirement Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define whether acceptance by the prospective member is required.

### Rationale

This distinguishes unilateral membership issuance from membership whose validity depends on the member's independent consent.

### Source

- REM-05-313
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-213

### Title

Membership Visibility Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define whether membership may or must be public.

### Rationale

Membership can itself be sensitive. Its visibility therefore needs schema-level semantics rather than an application silently assuming public disclosure.

### Source

- REM-05-314
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-09
- CI-12

---

## REL-REL-214

### Title

Membership Role Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define the roles that may be assigned within the membership relationship.

### Rationale

Role semantics must be explicit and must not be treated as automatically conveying unspecified authority.

### Source

- REM-05-315
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-215

### Title

Membership Authority Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define whether and what authority a membership relationship conveys.

### Rationale

The fact of membership must not be used as an implicit source of broad authority. Any authority arising from membership needs explicit schema semantics.

### Source

- REM-05-316
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-216

### Title

Membership Expiration Definition

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define applicable expiration behaviour.

### Rationale

Membership validity may be time-bound, renewable or condition-dependent. Explicit expiration semantics allow implementations to distinguish current membership from historical membership.

### Source

- REM-05-317
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-12
- AI-09

---

## REL-REL-217

### Title

Membership Removal Rules

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A membership schema **SHOULD** define the rules under which membership may be removed or ended.

### Rationale

Termination semantics must identify the relevant authority and lifecycle rules rather than allowing either participant to silently rewrite the other's records.

### Source

- REM-05-318
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-02
- CI-06
- AI-09

---

## REL-REL-218

### Title

Organisation Cannot Rewrite Member Repository

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An organisation **MUST NOT** rewrite a member's personal repository merely by virtue of the membership relationship.

### Rationale

The organisation controls its own declarations and authorised resources, not the member's independently controlled repository history.

### Source

- REM-05-319
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-02
- CI-08

---

## REL-REL-219

### Title

Member Cannot Rewrite Organisation Membership Record

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A member **MUST NOT** rewrite the organisation's membership record merely by virtue of being its subject or participant.

### Rationale

Independent repository authority applies in both directions. A member may control the member's own declaration but does not thereby gain control over the organisation's record.

### Source

- REM-05-320
- `design-notes/05-relationship-model.md`, Section 28

### Related Invariants

- CI-02
- CI-08

---

# 4. Non-Normative Source Entries

The following REM-05 entries fall within this part's source range but were explicitly remediated by `REM-05R-01` and verified by `REM-05R-02` as non-normative model examples. They are retained here solely for complete traceability and **do not** receive `REL-REL` catalogue identifiers:

| REM identifier | Source example | Catalogue treatment |
|---|---|---|
| REM-05-291 | Organisation | Non-normative model example; no catalogue requirement created |
| REM-05-292 | Association | Non-normative model example; no catalogue requirement created |
| REM-05-293 | Project team | Non-normative model example; no catalogue requirement created |
| REM-05-294 | Community | Non-normative model example; no catalogue requirement created |
| REM-05-295 | Cooperative | Non-normative model example; no catalogue requirement created |

These examples illustrate possible formal-group forms in Section 27. Their presence in the source does not impose a protocol obligation to support any named group type.

---

# 5. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined functional set, admission-condition set or membership-state vocabulary:

- `REM-05-284` through `REM-05-288` are consolidated into `REL-REL-205`. Visibility, feed filtering, access, notifications and organisation are the five source-listed permitted uses of one personal-group construct and share `MAY` strength.
- `REM-05-296` through `REM-05-301` are consolidated into `REL-REL-208`. Invitation, acceptance, administrator approval, credential, payment and multi-party authorisation are the six source-listed optional conditions for formal membership and share `MAY` strength.
- `REM-05-303` through `REM-05-311` are consolidated into `REL-REL-210`. The nine source-listed membership modes or lifecycle states form one optional membership vocabulary and share `MAY` strength.

`REM-05-291` through `REM-05-295` are explicitly accounted for in Section 4 without normative catalogue creation.

No other REM-05 entries in the covered range are consolidated. Personal-group control, privacy, controller-only visibility, consent semantics and public-presentation integrity remain independently meaningful. Formal-group identity, governance and independent verifiability remain separate. The seven membership-schema definition recommendations remain separate because issuer, acceptance, visibility, role, authority, expiration and removal are independently meaningful and testable dimensions. The two repository-authority prohibitions remain separate because they constrain opposite directions of control.

Every REM-05 identifier from `REM-05-279` through `REM-05-320` is therefore accounted for exactly once: either by an ordinary normative catalogue requirement or, for `REM-05-291` through `REM-05-295`, by explicit non-normative traceability treatment.

---

# 6. Editorial QA Record

## Scope verification

- Part 11 begins at `REM-05-279`, immediately after Part 10's final covered requirement `REM-05-278`.
- Coverage ends at `REM-05-320`, the end of source Section 28.
- Section 29 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 26–28.

## Numbering verification

- First catalogue requirement: `REL-REL-200`.
- Final catalogue requirement: `REL-REL-219`.
- Catalogue numbering continues directly from Part 10's `REL-REL-199`.
- Catalogue identifiers in this part are continuous and unique.
- No catalogue-number gaps were introduced for `REM-05-291` through `REM-05-295`; those entries are non-normative and intentionally receive no `REL-REL` identifiers.

## Traceability verification

- Every REM-05 identifier in the covered range is explicitly accounted for.
- Consolidated requirements retain all contributing REM-05 identifiers.
- `REM-05-291` through `REM-05-295` remain non-normative and are not converted into ordinary catalogue requirements.
- Normative strength is preserved from the verified extraction.
- Personal-group uses remain `MAY` rather than becoming mandatory features.
- Formal-group admission conditions remain optional `MAY` conditions.
- Formal membership's independent-verifiability recommendation remains `SHOULD` rather than `MUST`.
- Membership modes and lifecycle states remain optional `MAY` capabilities.
- All seven membership-schema definition requirements retain `SHOULD` strength.
- Both repository-authority boundaries retain `MUST NOT` strength.

## Status-boundary verification

This part directly encounters the first special remediation range identified by `REM-05R-02`:

- `REM-05-291` through `REM-05-295` are correctly retained only as non-normative model examples and excluded from ordinary normative catalogue numbering.

The remaining special treatments continue to bind later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves the constitutional distinction between unilateral personal organisation and formal membership. A personal group may be private even from the identities it contains, and inclusion cannot be converted into a claim of consent. Formal groups may instead establish governance and admission conditions, with membership preferably represented through independently verifiable relationship records. Membership semantics remain schema-defined, while organisation and member retain independent control of their respective repositories and declarations.

The next catalogue part should begin with `REM-05-321` / source Section 29 and continue catalogue numbering from `REL-REL-220`.