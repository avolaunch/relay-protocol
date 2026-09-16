# EA-05-05 — Relationship Requirements Catalogue

## Part 4 — Relationship Status, Lifecycle and Ownership

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing relationship status, lifecycle transitions and declarant control.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-090`, following Part 3's coverage of Relationship Type, direction, unilateral relationships and reciprocal relationships. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 11–13 and REM-05 requirements `REM-05-097` through `REM-05-131`.

It defines normative requirements governing:

- schema-governed relationship status;
- optional status states and activation patterns;
- evidence-dependent relationship validation;
- schema-defined lifecycle stages;
- proposal, acceptance and activation semantics;
- authorised relationship modification;
- suspension, termination, expiration and dispute semantics;
- verifiable relationship history;
- declarant control of relationship records;
- independent control of reciprocal declarations;
- protection against silent rewriting or deletion;
- self-revocation and historical-record control.

Section 14 relationship continuity and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-090

### Title

Schema-Governed Relationship Status

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A relationship schema **MUST** define or constrain the statuses permitted for records of that Relationship Type.

### Rationale

Relationship state is schema-dependent. A universal closed state machine would incorrectly impose lifecycle semantics on relationship types that do not require them.

### Source

- REM-05-097
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-091

### Title

Proposed Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `proposed` status for a declaration that has been initiated but is not yet accepted or operational.

### Rationale

Proposal-based relationship types may need to distinguish an initiated declaration from an accepted or active relationship.

### Source

- REM-05-098
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-092

### Title

Pending Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `pending` status where further approval, evidence or validation is required before activation.

### Rationale

Pending state permits a schema to represent incomplete authorisation or validation without falsely treating the relationship as active.

### Source

- REM-05-099
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-093

### Title

Active Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support an `active` status to identify a relationship that is currently operational under that schema.

### Rationale

An explicit active state can distinguish operational relationships from proposed, pending, suspended or ended declarations without implying authority or reciprocity beyond the schema.

### Source

- REM-05-100
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-094

### Title

Declined Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `declined` status where a required participant refuses a proposed or pending relationship.

### Rationale

A declined state records a workflow outcome without representing the relationship as active.

### Source

- REM-05-101
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-095

### Title

Ended Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support an `ended` status for a relationship that was previously operational but has been terminated.

### Rationale

An ended state permits termination to be represented without necessarily erasing historical evidence of the prior relationship.

### Source

- REM-05-102
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-096

### Title

Revoked Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `revoked` status where the authority underlying a declaration has been withdrawn.

### Rationale

Revocation must be distinguishable from ordinary termination where the schema treats withdrawal of authority as a separate lifecycle event.

### Source

- REM-05-103
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-097

### Title

Expired Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support an `expired` status where the relationship ceases automatically at the end of a defined validity period.

### Rationale

Time-bound relationships require a state that can distinguish automatic expiry from manual termination or revocation.

### Source

- REM-05-104
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-098

### Title

Disputed Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `disputed` status where a participant challenges an asserted or externally supported relationship.

### Rationale

Dispute state permits the challenge to be represented without itself deciding whether the original assertion is true or false.

### Source

- REM-05-105
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-099

### Title

Suspended Relationship Status

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** support a `suspended` status where the relationship temporarily stops producing effects without being permanently ended.

### Rationale

Suspension permits temporary interruption while retaining the distinction between current inactivity and permanent termination.

### Source

- REM-05-106
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-100

### Title

Direct Activation for Simple Relationships

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A schema for a simple unilateral relationship **MAY** permit creation directly in the active state without proposal or pending stages.

### Rationale

Simple relationships such as follows need not inherit approval-oriented lifecycle complexity where the governing schema does not require it.

### Source

- REM-05-107
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-101

### Title

Multi-Stage Collaboration Activation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A collaboration schema **MAY** require a staged transition from `proposed` to `pending` to `active`.

### Rationale

Reciprocal or approval-based relationships may require multiple lifecycle stages before becoming operational.

### Source

- REM-05-108
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- AI-09

---

## REL-REL-102

### Title

Credential-Based Relationship Validation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A schema for a verified employment or similarly evidence-dependent relationship **MAY** require an external credential rather than accepting an unsupported self-declaration.

### Rationale

Evidence-dependent relationship types must be able to distinguish an unsupported claim from a relationship whose required evidence has been supplied.

### Source

- REM-05-109
- `design-notes/05-relationship-model.md`, Section 11

### Related Invariants

- CI-10

---

## REL-REL-103

### Title

Schema-Defined Relationship Lifecycle

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A relationship schema **MAY** define a lifecycle containing one or more proposal, acceptance, activation, modification, suspension, termination, expiration and dispute stages.

### Rationale

The Relationship Model supplies lifecycle capabilities without requiring every Relationship Type to implement every stage.

### Source

- REM-05-110
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-09

---

## REL-REL-104

### Title

Proposal-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where a proposal stage exists, it **MUST** represent one identity proposing a reciprocal or approval-based relationship.

### Rationale

Proposal must remain semantically distinct from acceptance or activation.

### Source

- REM-05-111
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-08
- AI-09

---

## REL-REL-105

### Title

Acceptance-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where an acceptance stage exists, it **MUST** represent the Target independently authorising its side of the relationship.

### Rationale

Acceptance cannot be manufactured by the proposing identity because reciprocal authority remains independently controlled.

### Source

- REM-05-112
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-08
- AI-09

---

## REL-REL-106

### Title

Activation-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where an activation stage exists, it **MUST** identify the point at which the relationship becomes operational under the applicable schema.

### Rationale

Implementations need a schema-defined boundary between pre-operational workflow state and a relationship whose defined effects are active.

### Source

- REM-05-113
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-09

---

## REL-REL-107

### Title

Relationship Modification Support

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A relationship lifecycle **MAY** support authorised modification of relationship context, visibility, role or conditions where permitted by the governing schema and authority model.

### Rationale

Section 12 defines modification as a lifecycle capability and identifies four forms of change. They share the same underlying permission: authorised schema-governed modification of an existing relationship declaration.

### Source

- REM-05-114
- REM-05-115
- REM-05-116
- REM-05-117
- REM-05-118
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-108

### Title

Suspension-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where suspension is supported, a suspended relationship **MUST** temporarily stop producing its schema-defined effects without being represented as permanently ended.

### Rationale

Suspension is temporary interruption, not termination, and the protocol representation must preserve that distinction.

### Source

- REM-05-119
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-09

---

## REL-REL-109

### Title

Termination-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where termination is supported, the lifecycle **MUST** allow one or both authorised parties to end the relationship according to the schema's control rules.

### Rationale

Termination must respect the independent authority each participant holds over its own declaration rather than creating undeclared cross-party control.

### Source

- REM-05-120
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- CI-06
- AI-08
- AI-09

---

## REL-REL-110

### Title

Expiration-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where expiration is supported, the relationship **MUST** end automatically at the defined expiration time.

### Rationale

A defined expiry time must have operational meaning rather than functioning only as descriptive metadata.

### Source

- REM-05-121
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- AI-09

---

## REL-REL-111

### Title

Dispute-Stage Semantics

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where dispute handling is supported, the lifecycle **MUST** allow a party to challenge an externally issued or asserted relationship.

### Rationale

A dispute mechanism must preserve the distinction between the original assertion and the challenging party's response rather than allowing one to overwrite the other.

### Source

- REM-05-122
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- CI-10
- AI-09

---

## REL-REL-112

### Title

Verifiable Relationship History

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where required by the relationship schema, relationship lifecycle history **SHOULD** remain verifiable.

### Rationale

Verifiable history permits later confirmation of lifecycle state, responsible authority and relevant supporting records where the schema requires historical evidence.

### Source

- REM-05-123
- `design-notes/05-relationship-model.md`, Section 12

### Related Invariants

- CI-10

---

## REL-REL-113

### Title

Declarant Control of Relationship Records

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Each Relay Identity **MUST** retain independent control over its own relationship declaration, including its record in a reciprocal or mutual relationship.

### Rationale

The relationship model distributes authority across the participating identities. Mutuality does not create a shared record that one participant can control on behalf of another.

### Source

- REM-05-124
- REM-05-125
- REM-05-126
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-114

### Title

No Silent Rewriting of Another Declaration

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A relationship participant **MUST NOT** silently rewrite another participant's independently controlled relationship declaration.

### Rationale

Independent authority over relationship declarations would be defeated if another participant could rewrite the authoritative record without valid authority.

### Source

- REM-05-127
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-115

### Title

No Silent Deletion of Another Declaration

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A relationship participant **MUST NOT** silently delete another participant's independently controlled relationship declaration.

### Rationale

Ending one participant's involvement does not grant authority to erase the other participant's independently controlled declaration or history.

### Source

- REM-05-128
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-116

### Title

Self-Revocation of Relationship Participation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A participant **MAY** revoke or end its own active participation in a relationship where permitted by the governing schema.

### Rationale

Participant autonomy requires an identity to be able to control its own declaration without acquiring authority over another participant's declaration.

### Source

- REM-05-129
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- CI-02
- AI-08

---

## REL-REL-117

### Title

Reciprocal State After Participant Exit

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A participant's relationship record **MAY** reflect that a reciprocal relationship is no longer active after another participant ends its side, while preserving attribution to the independently controlled declarations.

### Rationale

A remaining participant must be able to represent loss of reciprocity without pretending to control or rewrite the declaration that caused that loss.

### Source

- REM-05-130
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- AI-08
- AI-09

---

## REL-REL-118

### Title

Historical Relationship Record Control

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A participant **MUST** retain control over its own historical relationship record after a reciprocal relationship ceases to be active.

### Rationale

Termination of reciprocity must not transfer or erase either participant's control over its own historical declaration.

### Source

- REM-05-131
- `design-notes/05-relationship-model.md`, Section 13

### Related Invariants

- CI-02
- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express the same independently testable protocol behaviour:

- `REM-05-114` through `REM-05-118` are consolidated into `REL-REL-107`. Section 12 defines modification as a single optional lifecycle capability whose listed forms are changes to context, visibility, role or conditions. The consolidated catalogue requirement preserves all four permitted modification dimensions and their schema/authority qualification without manufacturing four independent conformance obligations.
- `REM-05-124`, `REM-05-125` and `REM-05-126` are consolidated into `REL-REL-113`. The Section 13 Alice/Bob statements instantiate the same general rule already stated by the source: each identity controls its own declaration. Independent control in a reciprocal relationship is therefore preserved as one constitutional requirement with all contributing extraction identifiers retained.

No other REM-05 entries in the covered range are consolidated. Individual status states remain separate because support for one state does not imply support for another; lifecycle-stage semantics remain independently testable; rewriting and deletion remain distinct prohibited operations; and self-revocation, reciprocal-state reflection and historical-record control govern different behaviours.

All REM-05 requirements from `REM-05-097` through `REM-05-131` are represented exactly once in the catalogue mapping, either independently or through the two explicit consolidations above.

---

# 5. Editorial QA Record

## Scope verification

- Part 4 begins at `REM-05-097`, immediately after Part 3's final covered requirement `REM-05-096`.
- Coverage ends at `REM-05-131`, the end of source Section 13.
- Section 14 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 11–13.

## Numbering verification

- First catalogue requirement: `REL-REL-090`.
- Final catalogue requirement: `REL-REL-118`.
- Catalogue numbering continues directly from Part 3's `REL-REL-089`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Optional source examples remain `MAY` capabilities rather than mandatory universal states.
- `SHOULD` history verifiability has not been promoted to `MUST`.
- Illustrative Alice/Bob ownership wording is generalised only to the rule explicitly stated by Section 13 and does not create additional authority semantics.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. The catalogue rules remain binding for later parts:

- `REM-05-291` through `REM-05-295` must remain outside ordinary normative catalogue treatment;
- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part establishes the schema-governed state and lifecycle framework for Relationship records while preserving independent declarant control. It deliberately avoids turning the source's example status list into a mandatory universal state machine and preserves the distinction between lifecycle coordination and cross-party record authority.

The next catalogue part should begin with `REM-05-132` / source Section 14 and continue catalogue numbering from `REL-REL-119`.