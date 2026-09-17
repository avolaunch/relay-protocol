# EA-05-05 — Relationship Requirements Catalogue

## Part 25 — Basic Relationship Compliance Scenario

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the canonical catalogue requirements derived from the Relationship Model's basic compliance scenario.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-401`, following Part 24's coverage of the Relationship Model's mandatory invariants. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

Section 57 defines an implementation test with overall `SHOULD` strength. Accordingly, the requirements in this part preserve scenario-level `SHOULD` and `SHOULD NOT` strength and do not silently promote scenario behaviours to `MUST` or `MUST NOT` merely because equivalent mandatory principles are independently established elsewhere in the model.

---

# 2. Scope

This part covers source Section 57 and REM-05 requirements `REM-05-617` through `REM-05-635`.

It defines recommended compliance behaviours governing:

- the overall basic Relationship compliance scenario;
- source-controlled follow creation;
- stable Relay Identifier targeting;
- permission-aware application replacement;
- preservation of existing follows across application replacement;
- relationship continuity across provider migration;
- cross-application reciprocal collaboration;
- independently authorised reciprocal records;
- application non-ownership of collaboration state;
- participant-controlled relationship termination;
- reciprocal activation state following termination;
- protection against cross-participant record falsification;
- private-block enforcement and confidentiality; and
- demonstration of application and provider independence.

Section 58 open design questions and later requirements are intentionally deferred to subsequent catalogue treatment.

---

# 3. Requirements

---

## REL-REL-401

### Title

Basic Relationship Compliance Scenario

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

A basic Relay Relationship implementation **SHOULD** demonstrate the application replacement, provider migration, reciprocal collaboration, termination and private-block behaviours described by the Section 57 compliance scenario.

### Rationale

The scenario provides an integrated interoperability test of the Relationship Model's core portability, authority, lifecycle and privacy properties without converting the scenario itself into an additional mandatory conformance layer.

### Source

- REM-05-617
- `design-notes/05-relationship-model.md`, Section 57

### Related Invariants

- CI-02
- CI-03
- CI-04
- CI-05
- CI-06

---

## REL-REL-402

### Title

Source-Controlled Follow Creation in Basic Compliance

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic compliance scenario, a follow created on behalf of a source identity **SHOULD** be stored as that source identity's relationship record rather than as an application-owned record.

### Rationale

The initial follow demonstrates that the application facilitates creation while canonical relationship state belongs with the authorising identity.

### Source

- REM-05-618
- `design-notes/05-relationship-model.md`, Section 57, Initial follow

### Related Invariants

- CI-02
- CI-04

---

## REL-REL-403

### Title

Stable Relay Identifier Targeting in Basic Compliance

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic compliance scenario, a follow record **SHOULD** identify the followed identity using its stable Relay Identifier.

### Rationale

Stable identity targeting is necessary for the relationship to survive application replacement, provider migration and mutable human-readable identifiers.

### Source

- REM-05-619
- `design-notes/05-relationship-model.md`, Section 57, Initial follow

### Related Invariants

- CI-01
- CI-05

---

## REL-REL-404

### Title

Permission Before Replacement-Application Relationship Access

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

A replacement application **SHOULD** obtain appropriate permission before reading the user's existing follow records.

### Rationale

Application portability does not imply unrestricted access. Replacement applications remain subject to the user's permission boundary before consuming portable relationship state.

### Source

- REM-05-620
- `design-notes/05-relationship-model.md`, Section 57, Application replacement

### Related Invariants

- CI-06
- CI-11

---

## REL-REL-405

### Title

Existing Follow Continuity Across Application Replacement

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

A compatible replacement application **SHOULD** be able to present an existing supported follow relationship without requiring the user to recreate that follow.

### Rationale

The scenario demonstrates application-independent relationship continuity: replacing a client should not require reconstructing user-owned relationship state.

### Source

- REM-05-621
- `design-notes/05-relationship-model.md`, Section 57, Application replacement

### Related Invariants

- CI-04
- CI-05

---

## REL-REL-406

### Title

Follow Continuity Across Provider Migration

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic provider-migration compliance scenario:

- the existing follow Record URI **SHOULD** remain unchanged;
- the target Relay Identifier **SHOULD** remain unchanged; and
- a compatible application **SHOULD** resolve the source identity's new repository location and continue using the existing relationship record.

### Rationale

These behaviours collectively test whether relationship identity and usability survive provider replacement without recreation or rebinding to the former provider.

### Source

- REM-05-622
- REM-05-623
- REM-05-624
- `design-notes/05-relationship-model.md`, Section 57, Provider migration

### Related Invariants

- CI-03
- CI-05

---

## REL-REL-407

### Title

Cross-Application Reciprocal Collaboration

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

A reciprocal relationship workflow **SHOULD** permit a relationship proposal created through one compatible application to be accepted through another compatible application.

### Rationale

Reciprocal relationship coordination must be capable of crossing application boundaries if the relationship is genuinely protocol-level rather than application-owned.

### Source

- REM-05-625
- `design-notes/05-relationship-model.md`, Section 57, Reciprocal collaboration

### Related Invariants

- CI-04
- CI-05

---

## REL-REL-408

### Title

Independent Reciprocal Collaboration Records

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

The basic reciprocal-collaboration scenario **SHOULD** result in independently authorised relationship records for each participant, linked according to the reciprocal relationship schema.

### Rationale

The scenario tests reciprocal state without collapsing participant authority into a single shared application-owned declaration.

### Source

- REM-05-626
- `design-notes/05-relationship-model.md`, Section 57, Reciprocal collaboration

### Related Invariants

- CI-02
- CI-06

---

## REL-REL-409

### Title

Application Non-Ownership of Cross-Application Collaboration

**Level:** Compliance

**Normative Keyword:** **SHOULD NOT**

### Statement

In the basic compliance scenario, neither participating application **SHOULD** acquire canonical ownership of the collaboration merely by facilitating proposal or acceptance.

### Rationale

Cross-application collaboration demonstrates that applications coordinate user-authorised state without becoming its canonical owner. The corresponding mandatory principle is independently established by Section 56, Invariant 10.

### Source

- REM-05-627
- `design-notes/05-relationship-model.md`, Section 57, Reciprocal collaboration

### Related Invariants

- CI-02
- CI-04

---

## REL-REL-410

### Title

Participant-Controlled Collaboration Termination

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic compliance scenario, a participant **SHOULD** be able to end its own authorised side of a collaboration in accordance with the relationship schema.

### Rationale

Independent authority over reciprocal records includes the ability for a participant to terminate its own declaration without requiring another participant or application to rewrite that record.

### Source

- REM-05-628
- `design-notes/05-relationship-model.md`, Section 57, Relationship termination

### Related Invariants

- CI-02
- CI-06

---

## REL-REL-411

### Title

Mutual Inactivity Following Required-Side Termination

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic compliance scenario, where mutual activation requires both participants' active declarations, termination of one required declaration **SHOULD** cause the mutual relationship to cease being represented as active.

### Rationale

A reciprocal relationship cannot continue to be represented as mutually active when one of the independently required declarations has ended.

### Source

- REM-05-629
- `design-notes/05-relationship-model.md`, Section 57, Relationship termination

### Related Invariants

- CI-06
- CI-10

---

## REL-REL-412

### Title

No Cross-Participant Falsification of Terminated Relationship State

**Level:** Compliance

**Normative Keyword:** **SHOULD NOT**

### Statement

In the basic compliance scenario, a participant **SHOULD NOT** be able to rewrite another participant's terminated relationship record to falsely represent that declaration as active.

### Rationale

The scenario tests independent record authority and historical integrity. The corresponding mandatory prohibition is independently established by Section 56, Invariant 6.

### Source

- REM-05-630
- `design-notes/05-relationship-model.md`, Section 57, Relationship termination

### Related Invariants

- CI-07
- CI-10

---

## REL-REL-413

### Title

Private Block Enforcement by Authorised Applications

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

In the basic compliance scenario, a private block **SHOULD** be enforceable by applications authorised to access and apply the blocking identity's block state.

### Rationale

A private block must be practically useful to authorised applications while remaining subject to the blocking identity's access-control boundary.

### Source

- REM-05-631
- `design-notes/05-relationship-model.md`, Section 57, Private block

### Related Invariants

- CI-06
- CI-11

---

## REL-REL-414

### Title

Private Block Confidentiality in Basic Compliance

**Level:** Compliance

**Normative Keyword:** **SHOULD NOT**

### Statement

In the basic compliance scenario, a private block **SHOULD NOT** be exposed publicly or disclose its private block record to the blocked identity merely as a consequence of protocol representation or enforcement.

### Rationale

Enforcement of private block state must not itself defeat the privacy classification of that state. The two source prohibitions share the same confidentiality boundary while addressing public and target-specific disclosure.

### Source

- REM-05-632
- REM-05-633
- `design-notes/05-relationship-model.md`, Section 57, Private block

### Related Invariants

- CI-06
- AI-07

---

## REL-REL-415

### Title

Basic Relationship Independence From Applications and Providers

**Level:** Compliance

**Normative Keyword:** **SHOULD**

### Statement

A basic compliant implementation **SHOULD** demonstrate that the tested relationships are bound neither to a single application nor to a single Relay Provider.

### Rationale

Application and provider independence is the culminating objective of the Section 57 scenario. The preceding steps are successful as a Relay compliance demonstration only when relationship continuity does not depend on either replaceable intermediary.

### Source

- REM-05-634
- REM-05-635
- `design-notes/05-relationship-model.md`, Section 57

### Related Invariants

- CI-03
- CI-04
- CI-05

---

# 4. Consolidation and Traceability Record

This part consolidates only scenario requirements that form one source-defined behavioural test or one shared confidentiality/objective statement:

- `REM-05-622` through `REM-05-624` are consolidated into `REL-REL-406`. Together they define the Section 57 provider-migration test: preserve the Record URI, preserve the target identifier, resolve the migrated repository and continue using the relationship.
- `REM-05-632` and `REM-05-633` are consolidated into `REL-REL-414`. Both derive from the same private-block sentence and jointly preserve confidentiality against public exposure and disclosure to the blocked identity.
- `REM-05-634` and `REM-05-635` are consolidated into `REL-REL-415`. Together they state the culminating basic Relay Relationship objective that relationships not be bound to one application or one provider.

No other REM-05 entries in the covered range are consolidated. In particular, the separate stages of the reciprocal-collaboration and termination scenario remain independently testable.

All REM-05 requirements from `REM-05-617` through `REM-05-635` are represented exactly once in the catalogue mapping, either independently or through the three explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 25 begins at `REM-05-617`, immediately after Part 24's final covered requirement `REM-05-616`.
- Coverage ends at `REM-05-635`, the end of source Section 57.
- Section 58 open design questions are excluded from ordinary normative catalogue treatment in this part.
- The authoritative source was checked directly for the complete Section 57 scenario.

## Numbering verification

- First catalogue requirement: `REL-REL-401`.
- Final catalogue requirement: `REL-REL-415`.
- Catalogue numbering continues directly from Part 24's `REL-REL-400`.
- Catalogue identifiers in this part are continuous and unique.

## Normative-strength verification

- `REM-05-617` retains `SHOULD` strength for the overall scenario.
- Positive scenario behaviours retain `SHOULD` strength.
- `REM-05-627`, `REM-05-630`, `REM-05-632` and `REM-05-633` retain `SHOULD NOT` strength.
- No scenario requirement has been promoted to `MUST` or `MUST NOT` because a corresponding invariant or substantive requirement exists elsewhere.
- References to stronger independent principles appear only in rationale or related-invariant context and do not alter Section 57's normative force.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Follow creation remains source-controlled in the scenario.
- Follow targets remain stable Relay Identifiers.
- Replacement applications remain permission-bound.
- Existing relationships remain reusable across application replacement.
- Provider migration tests Record URI continuity, target-identifier continuity and repository re-resolution.
- Reciprocal collaboration remains cross-application and independently authorised.
- Applications remain non-owners of facilitated collaboration state at scenario strength.
- Participants retain scenario-level ability to terminate their own declarations.
- Mutual active state responds to termination of a required declaration.
- Cross-participant falsification remains prohibited at scenario strength.
- Private blocks remain enforceable by authorised applications without becoming public or disclosed to the blocked identity merely through enforcement.
- The scenario culminates in application and provider independence.

## Status-boundary verification

No explicitly non-normative REM entries occur within `REM-05-617` through `REM-05-635`.

The next source section is Section 58, whose `REM-05-636` through `REM-05-645` entries are explicitly **non-normative Open Design Issues**. They must be accounted for in catalogue traceability without generating ordinary `REL-REL` normative requirements and must not be silently resolved.

The subsequent special-status rules remain unchanged:

- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status wherever they enter catalogue treatment.
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

Section 57 is retained as a standalone compliance-oriented catalogue part because its normative function differs from the mandatory invariants in Part 24. It describes a recommended integrated test of Relay relationship portability, independent authority, lifecycle and privacy rather than redefining those underlying constitutional guarantees.

The next catalogue part should begin with `REM-05-636` / source Section 58. Because `REM-05-636` through `REM-05-645` are explicitly non-normative Open Design Issues, the next part must account for them without assigning ordinary `REL-REL` identifiers, and should determine whether the bounded part should continue into the explicitly **PROVISIONAL v0.1** Section 59 requirements beginning at `REM-05-646`. The next normative catalogue identifier remains `REL-REL-416`.