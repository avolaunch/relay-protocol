# EA-05-05 — Relationship Requirements Catalogue

## Part 7 — Private Relationships and Visibility

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing private relationships, relationship visibility and selective disclosure.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-146`, following Part 6's coverage of subscriptions, followers and derived audiences. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 18–19 and REM-05 requirements `REM-05-174` through `REM-05-199`.

It defines normative requirements governing:

- support for non-public relationships;
- representative private relationship categories;
- protection of private relationship Targets and semantics;
- optional private-relationship protection mechanisms;
- the initial v0.1 private-graph implementation scope;
- public, unlisted, restricted and private visibility;
- independent visibility control for relationship existence, type, Target, context, dates and evidence;
- selective disclosure of high-level relationship information while withholding sensitive details;
- schema support for selective disclosure.

Section 20 relationship context and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-146

### Title

Support for Non-Public Relationships

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The Relationship Model **SHOULD** support relationships that are not publicly visible.

### Rationale

Portability of relationship state must not depend on making sensitive graph information public. The model therefore needs a path for relationships whose existence or details are restricted.

### Source

- REM-05-174
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-147

### Title

Private Relationship Categories

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The Relationship Model **MAY** represent friendship, family connection, private collaboration, trusted-contact, client, medical, legal and sensitive-group-membership relationships as private relationships.

### Rationale

Section 18 provides these categories as illustrative examples of relationships whose existence or meaning may itself be sensitive. The list demonstrates the breadth of the privacy requirement without making any individual schema mandatory.

### Source

- REM-05-175
- REM-05-176
- REM-05-177
- REM-05-178
- REM-05-179
- REM-05-180
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-09

---

## REL-REL-148

### Title

Private Relationship Target Confidentiality

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A private relationship record **SHOULD NOT** expose its Target identity to an unauthorised observer.

### Rationale

The identity of the Target can itself disclose sensitive graph information even when other relationship fields remain concealed.

### Source

- REM-05-181
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-149

### Title

Private Relationship Semantic Confidentiality

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement

A private relationship record **SHOULD NOT** expose the semantic meaning or Relationship Type to an unauthorised observer.

### Rationale

Knowing the meaning of a private relationship may disclose sensitive information even if the Target identity is hidden. Target confidentiality and semantic confidentiality are therefore independently relevant protections.

### Source

- REM-05-182
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-150

### Title

Private Relationship Protection Mechanisms

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An implementation **MAY** protect private relationships through restricted record access, encrypted relationship records, opaque audience identifiers, separately stored private relationship repositories, or a compatible combination of those mechanisms.

### Rationale

Section 18 identifies these as possible implementation approaches rather than prescribing one mandatory privacy architecture. Consolidating them preserves implementation flexibility while retaining every source-defined option.

### Source

- REM-05-183
- REM-05-184
- REM-05-185
- REM-05-186
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-151

### Title

Initial v0.1 Private-Graph Scope

**Level:** Implementation

**Normative Keyword:** **MAY**

### Statement

Relay v0.1 **MAY** initially implement private relationships using restricted relationship records while deferring advanced private-graph protections to a later version.

### Rationale

The source explicitly permits staged implementation. Deferral of advanced graph privacy does not relax the access rules protecting relationship records that are already classified as restricted.

### Source

- REM-05-187
- `design-notes/05-relationship-model.md`, Section 18

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-152

### Title

Relationship Visibility Classes

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Relationship Model **MAY** support `public`, `unlisted`, `restricted` and `private` relationship visibility classes.

### Rationale

Section 19 defines four visibility values that permit relationship disclosure to range from public access through progressively narrower forms of discovery and confidentiality.

### Source

- REM-05-188
- REM-05-189
- REM-05-190
- REM-05-191
- `design-notes/05-relationship-model.md`, Section 19

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-153

### Title

Field-Level Relationship Visibility

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Relationship Model **MAY** control disclosure independently for the existence of a relationship, its Relationship Type, Target identity, context, dates and associated evidence.

### Rationale

Relationship privacy is not necessarily record-wide. Section 19 explicitly permits different visibility treatment for individual semantic and evidentiary dimensions of the same relationship.

### Source

- REM-05-192
- REM-05-193
- REM-05-194
- REM-05-195
- REM-05-196
- REM-05-197
- `design-notes/05-relationship-model.md`, Section 19

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-154

### Title

High-Level Relationship Disclosure Withheld Internal Detail

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The Relationship Model **SHOULD** permit a relationship to disclose a public high-level statement while withholding more sensitive internal details.

### Rationale

The source example distinguishes public membership from internal role or membership-number disclosure. The requirement generalises that selective-disclosure behaviour without making the example's organisation schema mandatory.

### Source

- REM-05-198
- `design-notes/05-relationship-model.md`, Section 19

### Related Invariants

- CI-06
- CI-09

---

## REL-REL-155

### Title

Schema Support for Selective Disclosure

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship schema **SHOULD** support selective disclosure where its fields have materially different visibility requirements.

### Rationale

Selective disclosure must be expressible at the relationship-schema level where required rather than existing only as an application presentation convention.

### Source

- REM-05-199
- `design-notes/05-relationship-model.md`, Section 19

### Related Invariants

- CI-06
- CI-09

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express a single source-defined capability or illustrative category set:

- `REM-05-175` through `REM-05-180` are consolidated into `REL-REL-147`. Section 18 presents friendship, family connection, private collaboration, trusted contact, client/medical/legal relationships and sensitive-group membership as examples of private relationships. They remain optional illustrative categories rather than six independent schema obligations.
- `REM-05-183` through `REM-05-186` are consolidated into `REL-REL-150`. Restricted record access, encryption, opaque audience identifiers and separate private repositories are four possible implementations of one private-relationship protection capability. None is promoted into a mandatory mechanism.
- `REM-05-188` through `REM-05-191` are consolidated into `REL-REL-152`. Public, unlisted, restricted and private are the four source-listed visibility classes of one optional relationship-visibility model.
- `REM-05-192` through `REM-05-197` are consolidated into `REL-REL-153`. Existence, type, Target identity, context, dates and evidence are six fields or dimensions to which the same independent-visibility capability may apply.

No other REM-05 entries in the covered range are consolidated. The general requirement to support non-public relationships, Target confidentiality, semantic confidentiality, v0.1 implementation scope, high-level selective disclosure and schema-level selective-disclosure support each express independently meaningful protocol behaviour.

All REM-05 requirements from `REM-05-174` through `REM-05-199` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 7 begins at `REM-05-174`, immediately after Part 6's final covered requirement `REM-05-173`.
- Coverage ends at `REM-05-199`, the end of source Section 19.
- Section 20 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 18–19.

## Numbering verification

- First catalogue requirement: `REL-REL-146`.
- Final catalogue requirement: `REL-REL-155`.
- Catalogue numbering continues directly from Part 6's `REL-REL-145`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Source examples of private relationship categories remain `MAY` examples rather than mandatory schemas.
- Possible privacy implementations remain optional and no single privacy architecture is silently selected.
- Target and semantic confidentiality remain separate `SHOULD NOT` protections because either dimension can independently leak sensitive relationship information.
- Visibility classes and field-level visibility are kept distinct: one defines available visibility states, while the other defines what relationship dimensions may be controlled independently.
- Section 19's `SHOULD` selective-disclosure requirements have not been promoted to `MUST`.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes that relationship portability does not require public graph disclosure. It separates the privacy of a relationship's Target and meaning, leaves implementation mechanisms flexible, and defines visibility as capable of applying selectively to different relationship dimensions. The source's illustrative private relationship categories and possible privacy mechanisms remain examples and options rather than silently becoming universal schema requirements.

The next catalogue part should begin with `REM-05-200` / source Section 20 and continue catalogue numbering from `REL-REL-156`.