# EA-05-05 — Relationship Requirements Catalogue

## Part 14 — Blocks and Mutes

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing blocks and mutes as distinct user-controlled relationship and preference mechanisms.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-250`, following Part 13's coverage of termination, revocation and disputes. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 34–35 and REM-05 requirements `REM-05-372` through `REM-05-399`.

It defines normative requirements governing:

- block representation and enforcement;
- block effects on visibility, interaction, relationships, event delivery and discovery;
- block privacy and notification treatment;
- the distinction between blocking, protocol-level deletion and provider suspension;
- mute representation and interaction semantics;
- mute targets and scope;
- mute privacy;
- application-level and repository-level mute storage;
- mute portability and reasonable user expectations of continuity.

Section 36 trust relationships and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-250

### Title

Block Relationship Representation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A block **MUST** be represented as a private or restricted relationship declaration by a Source identity against a Target identity.

### Rationale

A block is controlled by the blocking identity and expresses an interaction restriction rather than a reciprocal relationship requiring Target approval.

### Source

- REM-05-372
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-251

### Title

Block Interaction Enforcement

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Applications and providers processing a valid block **MUST** apply it as an instruction to prevent or reduce interaction with the Target according to applicable policy and capability.

### Rationale

A block must have operational effect. Its precise consequences may vary by application or provider, but processing a valid block cannot ignore its interaction-control semantics.

### Source

- REM-05-373
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-10

---

## REL-REL-252

### Title

Block Interaction and Visibility Effects

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A block **MAY** prevent, suppress, filter or reduce applicable content visibility, replies, mentions, follows, messages, relationship requests, event delivery and discovery involving the blocked identity.

### Rationale

Section 34 identifies these as representative effects through which applications and providers may implement the block's interaction-control purpose. They are optional effects rather than a mandatory closed bundle, allowing policy and capability to determine the precise enforcement surface.

### Source

- REM-05-374
- REM-05-375
- REM-05-376
- REM-05-377
- REM-05-378
- REM-05-379
- REM-05-380
- REM-05-381
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-253

### Title

Block Privacy by Default

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A block relationship **SHOULD** be private or otherwise restricted from unauthorised disclosure by default.

### Rationale

Block state can itself be sensitive. Default restriction reduces unnecessary disclosure, retaliation and safety risks while allowing explicit policy to govern exceptional cases.

### Source

- REM-05-382
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-10

---

## REL-REL-254

### Title

No Presumed Block Notification

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement

A blocked Target **MUST NOT** be assumed to require notification merely because a block exists.

### Rationale

The source expressly permits blocks to remain undisclosed to their targets. Treating notification as inherent would undermine the privacy and safety properties of blocking.

### Source

- REM-05-383
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-10

---

## REL-REL-255

### Title

Policy-Required Block Notification

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application, provider or governing policy **MAY** require or perform notification of a blocked Target where such notification is explicitly applicable.

### Rationale

Although block notification is not presumed, Section 34 allows application or policy requirements to create an exception. Such notification should arise from an explicit applicable rule rather than from the block relationship itself.

### Source

- REM-05-384
- REM-05-385
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-256

### Title

Block Is Not Protocol-Level Deletion

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A block **MUST NOT** be interpreted as protocol-level deletion of the blocked identity, its records or its relationships.

### Rationale

Blocking changes interaction and visibility behaviour; it does not erase canonical state. Deletion is a separate lifecycle operation with different authority and effects.

### Source

- REM-05-386
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-257

### Title

Block Is Not Provider Suspension

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A block **MUST NOT** be interpreted as suspension of the blocked identity by a Relay Provider.

### Rationale

Provider suspension is an administrative or security action exercised under separate authority. A user's block cannot manufacture provider-level enforcement status.

### Source

- REM-05-387
- `design-notes/05-relationship-model.md`, Section 34

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-258

### Title

Mute Preference Representation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A mute **MUST** be represented as a preference that reduces visibility or notifications without necessarily preventing interaction.

### Rationale

A mute is semantically distinct from a block. Its defining function is filtering what the user sees or is notified about, not necessarily prohibiting interaction with the muted target.

### Source

- REM-05-388
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-10

---

## REL-REL-259

### Title

Mute Does Not Imply Interaction Prevention

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A mute **MUST NOT** automatically be interpreted as preventing all interaction with the muted Target.

### Rationale

Replies, messages or relationship requests may remain possible while visibility or notifications are reduced. Treating a mute as a block would collapse two distinct user controls.

### Source

- REM-05-389
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-260

### Title

Mute Target Scope

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A mute **MAY** target a Relay Identity, record collection, topic, specific Relay Record or defined relationship type.

### Rationale

Section 35 defines these as optional scopes of the same filtering preference. Supporting multiple target classes allows users to suppress unwanted visibility or notifications without unnecessarily muting broader entities or relationships.

### Source

- REM-05-390
- REM-05-391
- REM-05-392
- REM-05-393
- REM-05-394
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-261

### Title

Mute Privacy by Default

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A mute **SHOULD** be private by default.

### Rationale

A mute normally expresses the user's private visibility or notification preference. The muted party ordinarily has no operational need to know that the preference exists.

### Source

- REM-05-395
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-10

---

## REL-REL-262

### Title

Mute Storage Scope

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A mute **MAY** be maintained as an application-level preference or as a repository-level preference.

### Rationale

Section 35 permits both local and repository-backed mute state. Application storage can suit deliberately local preferences, while repository storage can support continuity across compatible applications.

### Source

- REM-05-396
- REM-05-397
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-263

### Title

Mute Portability

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A mute **MAY** be portable across compatible applications where the user reasonably expects the preference to survive an application change.

### Rationale

Portability can preserve user-controlled filtering across application replacement, but it is not universally required because some mutes may intentionally be application-local.

### Source

- REM-05-398
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-03
- CI-10

---

## REL-REL-264

### Title

Mute Portability and Reasonable User Expectation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An implementation deciding whether to persist or migrate a mute **SHOULD** consider the user's reasonable expectation of continuity across application changes.

### Rationale

Portability should neither silently discard filtering that users reasonably expect to survive nor unexpectedly export a preference that users reasonably understand to be local.

### Source

- REM-05-399
- `design-notes/05-relationship-model.md`, Section 35

### Related Invariants

- CI-03
- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only source requirements that form one explicit option set or one shared implementation choice:

- `REM-05-374` through `REM-05-381` are consolidated into `REL-REL-252`. Content visibility, replies, mentions, follows, messages, relationship requests, event delivery and discovery are the eight source-defined optional effects of a block and share `MAY` strength.
- `REM-05-384` and `REM-05-385` are consolidated into `REL-REL-255`. Application and provider/governing-policy notification are the source-defined policy exceptions to the rule that block notification is not presumed and share `MAY` strength.
- `REM-05-390` through `REM-05-394` are consolidated into `REL-REL-260`. Identity, collection, topic, record and relationship type are the five source-defined optional mute target scopes and share `MAY` strength.
- `REM-05-396` and `REM-05-397` are consolidated into `REL-REL-262`. Application-level and repository-level storage are the two source-defined implementation locations for mute preferences and share `MAY` strength.

No other REM-05 entries in the covered range are consolidated. Block representation, enforcement, privacy, notification presumption, deletion and suspension boundaries remain independently meaningful requirements. Mute representation, interaction semantics, privacy, portability and portability-expectation treatment likewise remain independently testable.

All REM-05 requirements from `REM-05-372` through `REM-05-399` are represented exactly once in the catalogue mapping, either independently or through the four explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 14 begins at `REM-05-372`, immediately after Part 13's final covered requirement `REM-05-371`.
- Coverage ends at `REM-05-399`, the end of source Section 35 and REM-05 Part 7.
- Section 36 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 34–35.

## Numbering verification

- First catalogue requirement: `REL-REL-250`.
- Final catalogue requirement: `REL-REL-264`.
- Catalogue numbering continues directly from Part 13's `REL-REL-249`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Block representation and enforcement remain mandatory.
- Block effects remain optional and are not converted into a mandatory closed bundle.
- Block privacy retains `SHOULD` strength.
- Block notification is not presumed, while explicit application or policy notification remains optional.
- Blocks remain distinct from protocol-level deletion and provider suspension under `MUST NOT` semantics.
- Mute representation remains mandatory while automatic interaction prevention remains prohibited.
- Mute target classes remain optional.
- Mute privacy retains `SHOULD` strength.
- Application-level and repository-level storage remain optional implementation choices.
- Portability remains optional and its user-expectation criterion retains `SHOULD` strength.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part keeps blocks and mutes semantically distinct while preserving both as user-controlled safety and preference mechanisms. A block is a private or restricted relationship declaration with enforceable interaction-control semantics, but it does not delete protocol state or suspend an identity at provider level. A mute is a visibility or notification preference that need not prevent interaction and may remain local or become portable according to the user's reasonable expectation of continuity. Neither mechanism silently acquires broader authority than the source model grants it.

The next catalogue part should begin with `REM-05-400` / source Section 36 and continue catalogue numbering from `REL-REL-265`.