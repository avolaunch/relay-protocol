# EA-05-05 — Relationship Requirements Catalogue

## Part 13 — Relationship Termination, Revocation and Disputes

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing relationship termination, revocation of authority-bearing relationships and disputes concerning relationship assertions.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-235`, following Part 12's coverage of relationship requests and acceptance. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 31–33 and REM-05 requirements `REM-05-343` through `REM-05-371`.

It defines normative requirements governing:

- source-controlled relationship termination;
- termination effects for unilateral and reciprocal relationships;
- historical relationship retention and integrity;
- revocation of authority-bearing relationships;
- revocation identification, provenance, timing, reason, capability scope and prior-action treatment;
- rejection of new actions after authority revocation;
- historical proof of previously valid authority;
- relationship disputes and separately attributable counterclaims;
- non-destructive dispute representation;
- dispute presentation;
- the boundary between protocol evidence and legal truth;
- preservation of claim and counterclaim attribution.

Section 34 blocks and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-235

### Title

Source-Controlled Relationship Termination

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A source identity **MUST** be able to terminate a relationship declaration that it controls.

### Rationale

Relationship portability and independent authority require the Source to retain lifecycle control over its own declaration without gaining authority over another identity's records.

### Source

- REM-05-343
- `design-notes/05-relationship-model.md`, Section 31

### Related Invariants

- CI-02
- AI-09

---

## REL-REL-236

### Title

Unilateral Relationship Termination Effect

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

For a unilateral relationship, termination by the Source **SHOULD** make that relationship inactive immediately unless the governing schema specifies a different valid transition.

### Rationale

A unilateral declaration depends on the Source's continuing authorisation. Its withdrawal should therefore normally end the active state without requiring consent from the Target.

### Source

- REM-05-344
- `design-notes/05-relationship-model.md`, Section 31

### Related Invariants

- CI-02
- AI-09

---

## REL-REL-237

### Title

Reciprocal Withdrawal Deactivates Mutual State

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

When one participant withdraws from a reciprocal relationship, the shared or derived mutual state **SHOULD** become inactive.

### Rationale

A mutual state depends on the continuing participation of both parties. Withdrawal ends that operational reciprocity without rewriting either participant's independently controlled history.

### Source

- REM-05-345
- `design-notes/05-relationship-model.md`, Section 31

### Related Invariants

- CI-02
- CI-10
- AI-09

---

## REL-REL-238

### Title

Historical Relationship Retention

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A participant **MAY** retain a historical record of a terminated relationship where the governing schema and applicable visibility rules permit that retention and disclosure.

### Rationale

Termination need not erase legitimate history, but historical continuity remains bounded by the relationship schema and visibility controls. Retention does not reactivate the relationship.

### Source

- REM-05-346
- REM-05-347
- REM-05-348
- `design-notes/05-relationship-model.md`, Section 31

### Related Invariants

- CI-10
- AI-09

---

## REL-REL-239

### Title

Termination Cannot Falsify Another Party's History

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Termination **MUST NOT** allow one party to alter, erase, misrepresent or otherwise falsify another party's historical relationship record.

### Rationale

Each participant remains authoritative over its own declaration and history. Ending a relationship cannot confer retrospective control over another party's independently maintained record.

### Source

- REM-05-349
- `design-notes/05-relationship-model.md`, Section 31

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-240

### Title

Authority-Bearing Relationship Revocation Support

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relay implementations **MUST** support revocation for authority-bearing relationships.

### Rationale

Authority-bearing relationships can enable consequential actions. A protocol that permits authority grants without a revocation mechanism would allow obsolete or withdrawn authority to remain operational.

### Source

- REM-05-350
- `design-notes/05-relationship-model.md`, Section 32

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-241

### Title

Relationship Revocation Metadata

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship revocation **SHOULD** identify the affected relationship record, revoking authority, effective time, reason where appropriate, affected capabilities, and whether actions validly completed before the effective revocation time remain valid.

### Rationale

These source-defined dimensions together establish what is revoked, who authorised the revocation, when it takes effect, why it occurred where appropriate, which powers cease, and how prior valid actions are treated. Keeping them explicit supports auditability and partial revocation without assuming retroactive invalidation.

### Source

- REM-05-351
- REM-05-352
- REM-05-353
- REM-05-354
- REM-05-355
- REM-05-356
- `design-notes/05-relationship-model.md`, Section 32

### Related Invariants

- CI-06
- CI-10
- AI-09

---

## REL-REL-242

### Title

Rejection of New Actions After Authority Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

After an authority-bearing relationship has been revoked, all new actions that depend on the revoked authority **MUST** be rejected from the revocation's effective time.

### Rationale

Revocation must have operational effect. Continuing to accept new actions under revoked authority would make the revocation record informational rather than enforceable.

### Source

- REM-05-357
- `design-notes/05-relationship-model.md`, Section 32

### Related Invariants

- CI-06
- AI-09

---

## REL-REL-243

### Title

Historical Proof of Revoked Authority

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The system **MAY** retain verifiable historical evidence that an authority-bearing relationship was valid during an earlier period, provided the retained proof preserves sufficient temporal context to distinguish that earlier valid period from the current revoked state.

### Rationale

Revocation ends current authority but need not erase evidence that the authority previously existed. Temporal context is necessary to prevent historical proof from being mistaken for a current grant.

### Source

- REM-05-358
- REM-05-359
- `design-notes/05-relationship-model.md`, Section 32

### Related Invariants

- CI-06
- CI-10
- AI-09

---

## REL-REL-244

### Title

Relationship Dispute Capability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Identity **MUST** be able to issue a dispute against a relationship assertion concerning that identity or its controlled interests.

### Rationale

Relay preserves attributable claims rather than treating every assertion as uncontested truth. An affected identity therefore needs an independently attributable mechanism for recording disagreement.

### Source

- REM-05-360
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-245

### Title

Separate Dispute Representation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A relationship dispute **SHOULD** be represented as a separate record or separately attributable protocol object rather than by modifying the original assertion.

### Rationale

Separate representation preserves the provenance and integrity of both the original claim and the counterclaim, allowing each to be evaluated independently.

### Source

- REM-05-361
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-246

### Title

Non-Destructive Relationship Disputes

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Creating a relationship dispute **MUST NOT** automatically delete, rewrite or alter the original relationship assertion.

### Rationale

A counterclaim does not grant its issuer authority over the original claimant's record. Both claims must remain independently attributable unless a separately authorised process changes the original record.

### Source

- REM-05-362
- REM-05-363
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-247

### Title

Relationship Dispute Presentation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

When presenting a relationship dispute, an application **MAY** display the disputed assertion, its issuer, permitted supporting evidence, the attributable dispute and the current verification status.

### Rationale

Section 33 defines these as optional presentation elements that together can communicate the claim, provenance, evidence, counterclaim and current evidentiary state. Display remains subject to visibility, access and safety constraints.

### Source

- REM-05-364
- REM-05-365
- REM-05-366
- REM-05-367
- REM-05-368
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-248

### Title

No Automatic Protocol Determination of Legal Truth

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

The Relay protocol **MUST NOT** treat the existence of an assertion, dispute or protocol-level verification result as automatic determination of legal truth.

### Rationale

Protocol records preserve claims, evidence and verification states but cannot substitute automatically for competent legal processes or authorities where legal truth is contested.

### Source

- REM-05-369
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-10

---

## REL-REL-249

### Title

Attributable Claims and Counterclaims

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Relay **MUST** preserve attribution for both relationship claims and relationship counterclaims or disputes.

### Rationale

The protocol's role in a dispute is to preserve who asserted what, including disagreement, rather than silently merging claims or determining which party is legally correct.

### Source

- REM-05-370
- REM-05-371
- `design-notes/05-relationship-model.md`, Section 33

### Related Invariants

- CI-02
- CI-10

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined permission subject to source-defined constraints, one metadata structure, or inseparable paired integrity semantics:

- `REM-05-346` through `REM-05-348` are consolidated into `REL-REL-238`. Historical retention is the source's `MAY` capability, while schema and visibility compliance are mandatory conditions on exercising that permission. The catalogue statement preserves both constraints rather than treating them as independent permissions.
- `REM-05-351` through `REM-05-356` are consolidated into `REL-REL-241`. Relationship record, revoking authority, effective time, reason where appropriate, affected capabilities and prior-action treatment are the six source-defined fields of one revocation-metadata recommendation and share `SHOULD` strength.
- `REM-05-358` and `REM-05-359` are consolidated into `REL-REL-243`. Historical proof is the source's `MAY` capability; preserving temporal context is a mandatory condition necessary to distinguish historical authority from current revoked state.
- `REM-05-362` and `REM-05-363` are consolidated into `REL-REL-246`. Deletion and alteration are the two source-prohibited destructive effects of creating a dispute and share `MUST NOT` strength.
- `REM-05-364` through `REM-05-368` are consolidated into `REL-REL-247`. Assertion, issuer, evidence, dispute and current verification status are the five source-defined optional dispute-presentation elements and share `MAY` strength.
- `REM-05-370` and `REM-05-371` are consolidated into `REL-REL-249`. Claims and counterclaims are the paired attributable records explicitly preserved by the source and share `MUST` strength.

No other REM-05 entries in the covered range are consolidated. Source-controlled termination, unilateral termination effects, reciprocal withdrawal, historical-integrity protection, revocation support, post-revocation enforcement, dispute capability, separate dispute representation and the legal-truth boundary remain independently meaningful and testable requirements.

All REM-05 requirements from `REM-05-343` through `REM-05-371` are represented exactly once in the catalogue mapping, either independently or through the six explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 13 begins at `REM-05-343`, immediately after Part 12's final covered requirement `REM-05-342`.
- Coverage ends at `REM-05-371`, the end of source Section 33.
- Section 34 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 31–33.

## Numbering verification

- First catalogue requirement: `REL-REL-235`.
- Final catalogue requirement: `REL-REL-249`.
- Catalogue numbering continues directly from Part 12's `REL-REL-234`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Source-controlled termination remains `MUST` capability.
- Unilateral termination and reciprocal withdrawal retain `SHOULD` strength.
- Historical retention remains optional while preserving mandatory schema, visibility and temporal-integrity constraints.
- Authority-bearing relationship revocation remains mandatory.
- Revocation metadata retains `SHOULD` strength.
- New actions based on revoked authority remain mandatory rejections.
- Dispute capability and attribution preservation remain mandatory.
- Separate dispute representation remains `SHOULD`.
- Dispute creation remains prohibited from deleting or altering the original assertion.
- Dispute presentation remains optional.
- Relay remains prohibited from treating protocol records as automatic determinations of legal truth.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves independent control across the end of a relationship as carefully as at its creation. A Source can terminate its own declaration without rewriting another party's history; revocation must make withdrawn authority operationally unusable while permitting properly contextualised historical proof; and disputes remain separately attributable counterclaims rather than destructive edits to the original assertion. Relay consequently preserves evidence and disagreement without automatically converting protocol state into a determination of legal truth.

The next catalogue part should begin with `REM-05-372` / source Section 34 and continue catalogue numbering from `REL-REL-250`.