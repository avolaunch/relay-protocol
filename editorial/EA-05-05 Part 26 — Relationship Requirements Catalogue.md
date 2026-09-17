# EA-05-05 — Relationship Requirements Catalogue

## Part 26 — Open Design Issues and Provisional v0.1 Decisions

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part records the Relationship Model's unresolved Section 58 design questions without converting them into normative requirements, and defines the canonical catalogue treatment of the explicitly provisional working decisions in Section 59.

It continues the Relationship Requirements Catalogue after Part 25. The next available normative catalogue identifier is `REL-REL-416`.

The status boundary in this part is essential:

- Section 58 is **non-normative** and remains unresolved;
- Section 59 is an explicit **PROVISIONAL v0.1** working baseline, not a set of final immutable protocol commitments.

The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 58–59 and REM-05 entries `REM-05-636` through `REM-05-671`.

It accounts for:

- ten unresolved Open Design Issues, which generate no ordinary normative `REL-REL` identifiers; and
- the provisional v0.1 working assumptions governing relationship representation, canonical storage, reciprocity, stable identity references, portability, indexing, visibility, access control, authority semantics, evidentiary state, derived values, block/mute privacy, migration compatibility and deferred encrypted-graph work.

Section 60 is intentionally deferred to the final Relationship catalogue part because it contains both the model's final normative core principle (`REM-05-672`) and a non-normative hand-off (`REM-05-673`).

---

# 3. Non-Normative Open Design Issue Accounting

The following REM-05 entries are retained for complete traceability but **do not generate `REL-REL` catalogue requirements**. No design choice is made, preferred or implied by their inclusion here.

| REM-05 | Open Design Issue | Catalogue Treatment |
|---|---|---|
| REM-05-636 | Efficient public reverse indexing without an indispensable global graph owner | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-637 | Reciprocal activation mechanism | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-638 | Portable private graph secrecy from providers and indexers | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-639 | Efficient dynamic-audience evaluation and prompt revocation | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-640 | Relationship-request transport mechanism | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-641 | Boundary between authority relationships, Permission Grants and credentials | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-642 | Trusted-contact and guardian lifecycle during identity recovery | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-643 | Representation of historically reciprocal but currently one-sided relationships | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-644 | Evidence threshold for matching imported external accounts to Relay Identities | Non-normative; unresolved; no `REL-REL` identifier |
| REM-05-645 | Interoperability treatment of similarly labelled but semantically different schemas | Non-normative; unresolved; no `REL-REL` identifier |

These questions remain available for later authoritative design resolution. Their catalogue accounting must not be interpreted as resolution, recommendation or normative guidance.

---

# 4. PROVISIONAL v0.1 Requirements

Every requirement in this section is explicitly **PROVISIONAL v0.1**. The normative keyword records the strength of the current v0.1 working assumption; it does not remove the provisional status established by Section 59.

---

## REL-REL-416

### Title

PROVISIONAL v0.1 — Relationship Representation as Relay Records

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** relationships **MUST** be represented as Relay Records under the current v0.1 working baseline.

### Rationale

Using the common Relay Record abstraction gives relationship state portable identity, versioning and repository semantics while the v0.1 representation remains subject to later confirmation.

### Source

- REM-05-646
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-05
- CI-07

---

## REL-REL-417

### Title

PROVISIONAL v0.1 — Declaring Identity Canonical Relationship Storage

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** the declaring identity's repository **MUST** store that identity's canonical relationship declaration under the current working baseline.

### Rationale

The working model locates canonical declaration state with the identity that authorised it rather than with an application or counterparty.

### Source

- REM-05-647
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-02
- CI-04

---

## REL-REL-418

### Title

PROVISIONAL v0.1 — Distinct Unilateral and Reciprocal Relationship Models

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** unilateral and reciprocal relationships **MUST** remain distinct relationship models under the current working baseline.

### Rationale

The distinction preserves the different consent and activation semantics of one-sided declarations and mutually authorised relationships.

### Source

- REM-05-648
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-02
- CI-06

---

## REL-REL-419

### Title

PROVISIONAL v0.1 — Independently Authorised Linked Reciprocal Records

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** reciprocal relationships **MUST** use independently authorised linked relationship records under the current working baseline.

### Rationale

The provisional mechanism preserves independent participant authority while permitting applications to derive reciprocal state from linked declarations.

### Source

- REM-05-649
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-02
- CI-06

---

## REL-REL-420

### Title

PROVISIONAL v0.1 — Stable Relay Identifier Relationship References

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** stable Relay Identifiers **MUST** identify relationship sources and Relay relationship targets under the current working baseline, subject to the Relationship Model's explicit allowance for external target references.

### Rationale

Stable identity references allow relationships to survive application and provider changes without binding canonical relationship identity to mutable handles or application-local identifiers.

### Source

- REM-05-650
- REM-05-651
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-01
- CI-05

---

## REL-REL-421

### Title

PROVISIONAL v0.1 — Follow Portability Across Applications and Providers

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** follow relationships **MUST** survive compatible application changes and Relay Provider changes under the current working baseline.

### Rationale

Follow portability demonstrates that a user-owned relationship persists independently of both the application that presents it and the provider that hosts its canonical record.

### Source

- REM-05-652
- REM-05-653
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-03
- CI-04
- CI-05

---

## REL-REL-422

### Title

PROVISIONAL v0.1 — Subscription Portability Across Applications and Providers

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** subscription relationships **MUST** survive compatible application changes and Relay Provider changes under the current working baseline.

### Rationale

Subscription state is provisionally treated as portable relationship state rather than as a subscription list owned by a particular client or hosting provider.

### Source

- REM-05-654
- REM-05-655
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-03
- CI-04
- CI-05

---

## REL-REL-423

### Title

PROVISIONAL v0.1 — Optional Indexes for Public Reverse Graph Queries

**Level:** Provisional v0.1

**Normative Keyword:** **MAY**

### Statement

**PROVISIONAL v0.1:** public reverse graph querying **MAY** be provided by optional indexes rather than by a mandatory global reverse-query capability of every repository under the current working baseline.

### Rationale

The working baseline permits derived indexing without requiring a universal global graph owner. The detailed distributed-index architecture remains unresolved by Section 58.1.

### Source

- REM-05-656
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-07
- AI-01

---

## REL-REL-424

### Title

PROVISIONAL v0.1 — Relationship Visibility Classifications

**Level:** Provisional v0.1

**Normative Keyword:** **MAY**

### Statement

**PROVISIONAL v0.1:** relationship visibility **MAY** use the following classifications under the current working baseline:

- `public`;
- `unlisted`;
- `restricted`; and
- `private`.

### Rationale

The provisional visibility vocabulary provides interoperable privacy classifications while leaving room for later specification refinement.

### Source

- REM-05-657
- REM-05-658
- REM-05-659
- REM-05-660
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-425

### Title

PROVISIONAL v0.1 — Explicit Access Controls for Private Relationships

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** private relationships **MUST** require explicit access controls under the current working baseline.

### Rationale

A private classification is meaningful only if access to the protected relationship state is explicitly bounded rather than inferred from repository possession or application participation.

### Source

- REM-05-661
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-06
- CI-11

---

## REL-REL-426

### Title

PROVISIONAL v0.1 — Exact Capabilities for Authority-Bearing Relationships

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** an authority-bearing relationship **MUST** define the exact technical capabilities it grants under the current working baseline.

### Rationale

Explicit capability definition prevents social or descriptive relationship labels from being interpreted as unbounded technical authority. The precise boundary between relationship-based authority, Permission Grants and credentials remains an open design issue under Section 58.6.

### Source

- REM-05-662
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-06
- CI-11

---

## REL-REL-427

### Title

PROVISIONAL v0.1 — Distinguishable Relationship Evidentiary States

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** self-declared, reciprocally confirmed and externally verified relationships **MUST** remain distinguishable as different evidentiary states under the current working baseline.

### Rationale

Different forms of relationship evidence support different claims. Preserving their distinction prevents self-declaration or reciprocal confirmation from being silently represented as independent external verification.

### Source

- REM-05-663
- REM-05-664
- REM-05-665
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-08
- CI-10

---

## REL-REL-428

### Title

PROVISIONAL v0.1 — Follower Counts and Reputation as Derived Values

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** follower counts and reputation results **MUST** be treated as derived values rather than canonical relationship declarations under the current working baseline.

### Rationale

Counts and reputation are computed views over relationship evidence and may vary by index, coverage, freshness or algorithm. They therefore remain distinct from canonical user-authorised relationship declarations.

### Source

- REM-05-666
- REM-05-667
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-07
- AI-01

---

## REL-REL-429

### Title

PROVISIONAL v0.1 — Blocks and Mutes Normally Private

**Level:** Provisional v0.1

**Normative Keyword:** **SHOULD**

### Statement

**PROVISIONAL v0.1:** blocks and mutes **SHOULD** normally be private under the current working baseline.

### Rationale

Blocks and mutes commonly encode sensitive interaction preferences. The provisional baseline therefore treats privacy as the normal case without asserting that every schema or policy context must make them universally private.

### Source

- REM-05-668
- REM-05-669
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-430

### Title

PROVISIONAL v0.1 — Unknown Relationship Schema Migration Preservation

**Level:** Provisional v0.1

**Normative Keyword:** **MUST**

### Statement

**PROVISIONAL v0.1:** unknown relationship schemas **MUST** survive migration under the current working baseline.

### Rationale

Migration must preserve relationship records even when the receiving implementation does not understand their schema semantics. Otherwise provider portability would depend on every provider recognising every present and future relationship schema.

### Source

- REM-05-670
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-03
- CI-09

---

## REL-REL-431

### Title

PROVISIONAL v0.1 — Deferral of Advanced End-to-End Encrypted Graph Privacy

**Level:** Provisional v0.1

**Normative Keyword:** **MAY**

### Statement

**PROVISIONAL v0.1:** advanced end-to-end encrypted graph-privacy mechanisms **MAY** be deferred beyond the first reference implementation.

### Rationale

The provisional implementation scope allows advanced encrypted-graph mechanisms to follow the first reference implementation. This deferral does not remove privacy, visibility or access-control requirements applicable to relationship data the implementation supports, and it does not resolve the private-graph architecture question in Section 58.3.

### Source

- REM-05-671
- `design-notes/05-relationship-model.md`, Section 59

### Related Invariants

- CI-06
- AI-07

---

# 5. Consolidation and Traceability Record

## Section 58 — non-normative accounting

`REM-05-636` through `REM-05-645` are all explicitly accounted for in Section 3 of this catalogue part. None generates an ordinary `REL-REL` identifier. No open design question has been answered, preferred, narrowed or strengthened by this catalogue treatment.

## Section 59 — provisional consolidations

The following consolidations preserve single source propositions or tightly coupled provisional decisions without losing traceability:

- `REM-05-650` + `REM-05-651` → `REL-REL-420`: stable Relay Identifiers as relationship source and Relay-target references.
- `REM-05-652` + `REM-05-653` → `REL-REL-421`: follow portability across application and provider changes.
- `REM-05-654` + `REM-05-655` → `REL-REL-422`: subscription portability across application and provider changes.
- `REM-05-657` through `REM-05-660` → `REL-REL-424`: the four provisional visibility classifications from one source proposition.
- `REM-05-663` through `REM-05-665` → `REL-REL-427`: the three evidentiary states that Section 59 requires to remain distinguishable.
- `REM-05-666` + `REM-05-667` → `REL-REL-428`: follower counts and reputation as derived values.
- `REM-05-668` + `REM-05-669` → `REL-REL-429`: blocks and mutes as normally private.

All other Section 59 entries remain independently represented.

Every REM-05 identifier from `REM-05-636` through `REM-05-671` is therefore accounted for exactly once: either as a non-normative Open Design Issue with no catalogue identifier, or as a contributor to an explicitly **PROVISIONAL v0.1** catalogue requirement.

---

# 6. Editorial QA Record

## Scope verification

- Part 26 begins at `REM-05-636`, immediately after Part 25's final covered requirement `REM-05-635`.
- It covers all of Section 58 and all of Section 59 through `REM-05-671`.
- Section 60 is excluded and remains for the final Relationship catalogue part.
- The authoritative source was checked directly for all ten Section 58 questions and all fifteen Section 59 provisional source propositions.

## Numbering verification

- No `REL-REL` identifiers are consumed by `REM-05-636` through `REM-05-645`.
- The first catalogue requirement created in this part is `REL-REL-416`, derived from `REM-05-646`.
- The final catalogue requirement created in this part is `REL-REL-431`, derived from `REM-05-671`.
- Catalogue numbering is continuous from Part 25's `REL-REL-415`.

## Status-boundary verification

- Section 58 remains explicitly non-normative and unresolved.
- No Section 58 alternative has been selected or transformed into a requirement.
- Every Section 59 catalogue requirement visibly carries **PROVISIONAL v0.1** in its title and statement.
- Provisional status is not flattened into final protocol status by the assigned normative keyword.
- `MUST`, `SHOULD` and `MAY` describe the strength of the current working baseline only.
- `REM-05-671` retains explicit `MAY` deferral semantics.
- The provisional decisions concerning optional indexes, authority-bearing relationships and encrypted graph privacy do not silently resolve the related Section 58 questions.

## Traceability verification

- `REM-05-636` through `REM-05-645`: all accounted for without catalogue requirement creation.
- `REM-05-646` through `REM-05-671`: all represented in `REL-REL-416` through `REL-REL-431`.
- All consolidations retain every contributing REM identifier.
- No REM identifier in the covered range is omitted or multiply assigned.

## Remaining Relationship boundary

Two REM-05 entries remain after this part:

- `REM-05-672` — normative Core Relationship Principle;
- `REM-05-673` — explicitly non-normative Migration and Portability Model hand-off.

The next catalogue part must create the next normative identifier, `REL-REL-432`, for `REM-05-672`, explicitly account for `REM-05-673` without creating a normative catalogue requirement, and then perform final REM-05 Relationship Catalogue coverage and numbering closure.

---

# Editorial Review Notes

Sections 58 and 59 are intentionally treated together because they expose the boundary between unresolved architecture and the temporary choices required to make a v0.1 implementation possible. Section 58 preserves questions that remain open; Section 59 records the working assumptions Relay can use while those broader questions await authoritative resolution.

This treatment prevents two opposite editorial errors: converting open questions into invented protocol law, and allowing provisional implementation choices to masquerade as permanent architectural commitments.

The next catalogue part should begin with `REM-05-672` / source Section 60, continue normative catalogue numbering from `REL-REL-432`, account for `REM-05-673` non-normatively, and close the EA-05-05 Relationship Requirements Catalogue with a full end-to-end traceability check.