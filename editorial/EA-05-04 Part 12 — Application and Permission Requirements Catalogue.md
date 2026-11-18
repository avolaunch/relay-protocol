# EA-05-04 — Application and Permission Requirements Catalogue

## Part 12 — First-Party Clients, Service Actors, Indexers and Delegated Consent

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part governs provider-built clients, service-to-service applications, indexers, delegated consent and multi-party organisational approval.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 56–60 and `REM-04-648` through `REM-04-693`.

`REM-04-655`–`REM-04-659` and `REM-04-679`–`REM-04-683` are verified non-normative examples and generate no catalogue requirements.

Section 61 and later are deferred.

---

# 3. Requirements

---

## REL-APP-245

### Title

First-Party Client Identifies as Application

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An application built or supplied by the current Relay Provider **MUST** identify itself as a Relay Application.

### Rationale

Provider involvement does not remove application-actor status.

### Source

- REM-04-648
- `design-notes/04-application-and-permission-model.md`, Section 56

### Related Invariants

- CI-04
- CI-11

---

## REL-APP-246

### Title

Provider and Application Role Visibility

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The user **SHOULD** be able to distinguish provider infrastructure, provider administration, optional first-party clients and third-party applications.

### Rationale

Visible separation prevents hosting and administrative roles from being confused with application permission.

### Source

- REM-04-649
- REM-04-650
- REM-04-651
- REM-04-652
- `design-notes/04-application-and-permission-model.md`, Section 56

### Related Invariants

- CI-11

---

## REL-APP-247

### Title

No First-Party Evasion of Permission Model

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Provider **MUST NOT** evade the Permission Model because it developed, distributes or operates the user interface.

### Rationale

First-party clients remain subject to the same authority boundaries as other applications.

### Source

- REM-04-653
- `design-notes/04-application-and-permission-model.md`, Section 56

### Related Invariants

- CI-04
- CI-11

---

## REL-APP-248

### Title

Applications Without Direct User Interfaces

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** support application actors that operate without a direct end-user interface.

### Rationale

Backend and service actors can exercise consequential authority and must remain governed.

### Source

- REM-04-654
- `design-notes/04-application-and-permission-model.md`, Section 57

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-249

### Title

Service-to-Service Application Requirements

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every service-to-service application actor **MUST** have an Application Identity and Manifest, operate under defined scopes, declare its purpose, remain limited by approved resources, actions, purpose, duration and conditions, and define and support revocation behaviour.

### Rationale

Lack of a direct user interface does not remove identity, disclosure, scope or revocation obligations.

### Source

- REM-04-660
- REM-04-661
- REM-04-662
- REM-04-663
- REM-04-664
- REM-04-665
- `design-notes/04-application-and-permission-model.md`, Section 57

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-250

### Title

Hidden Backend Integrations Remain Applications

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A backend integration **MUST NOT** be excluded from the Application and Permission Model merely because it is hidden or invoked indirectly.

### Rationale

Invisible execution does not remove application-actor responsibility.

### Source

- REM-04-666
- `design-notes/04-application-and-permission-model.md`, Section 57

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-251

### Title

Conditional Public Indexing

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A public indexer **MAY** read public records without a private Permission Grant only where applicable protocol policy permits such access.

### Rationale

Public availability is conditioned by protocol policy and does not imply private authority.

### Source

- REM-04-667
- `design-notes/04-application-and-permission-model.md`, Section 58

### Related Invariants

- CI-06

---

## REL-APP-252

### Title

Explicit Authority for Non-Public Indexing

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Indexing restricted or private records **MUST** require explicit authority.

### Rationale

Public indexing rules cannot be extended to non-public repository state.

### Source

- REM-04-668
- REM-04-669
- `design-notes/04-application-and-permission-model.md`, Section 58

### Related Invariants

- CI-06
- AI-07

---

## REL-APP-253

### Title

Indexer Declarations

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

An indexer **SHOULD** declare its indexing purpose, refresh behaviour, deletion handling, retention, creation of embeddings or comparable representations, model-training use, and user index-removal process.

### Rationale

These declarations expose persistence, derived processing and removal behaviour beyond ordinary reading.

### Source

- REM-04-670
- REM-04-671
- REM-04-672
- REM-04-673
- REM-04-674
- REM-04-675
- REM-04-676
- `design-notes/04-application-and-permission-model.md`, Section 58

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-254

### Title

Indexer Is Not Canonical Source

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An indexer **MUST NOT** be treated as the canonical source of a Relay Record because it stores, transforms, ranks or exposes an indexed representation.

### Rationale

Canonical state remains anchored in the Relay Repository.

### Source

- REM-04-677
- `design-notes/04-application-and-permission-model.md`, Section 58

### Related Invariants

- AI-01

---

## REL-APP-255

### Title

Delegated Consent Support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Permission Model **MAY** support another authority approving permissions on behalf of a Relay Identity.

### Rationale

Delegated consent is permitted where a valid authority basis exists.

### Source

- REM-04-678
- `design-notes/04-application-and-permission-model.md`, Section 59

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-256

### Title

Delegated Consent Evidence

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

For delegated consent, the system **MUST** record the approving identity or authority, the delegation basis, the controller's override rights and the delegation expiration.

### Rationale

These records establish who approved, why they could approve, how the controller remains involved and when authority ends.

### Source

- REM-04-684
- REM-04-685
- REM-04-686
- REM-04-687
- `design-notes/04-application-and-permission-model.md`, Section 59

### Related Invariants

- CI-02
- CI-10

---

## REL-APP-257

### Title

No Delegation Inferred from Account Access

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Consent delegation **MUST NOT** be inferred solely from access to an account, session, device or repository interface.

### Rationale

Possession or access is not proof of representative authority.

### Source

- REM-04-688
- `design-notes/04-application-and-permission-model.md`, Section 59

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-258

### Title

Multi-Party Organisational Approval

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The Permission Model **MAY** support organisational Relay Identities that require approval from multiple authorised parties.

### Rationale

Organisational authority may be distributed rather than controlled by one individual.

### Source

- REM-04-689
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-02
- CI-12

---

## REL-APP-259

### Title

Threshold Organisational Approval

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An organisational grant **MAY** require a defined threshold of authorised approvers for a sensitive operation or capability.

### Rationale

Threshold approval permits governance proportional to organisational risk.

### Source

- REM-04-690
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-02

---

## REL-APP-260

### Title

Pending Organisational Grant

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An organisational Permission Grant **MAY** remain pending before its required approval threshold is satisfied.

### Rationale

Pending state represents incomplete authority without rejecting the request outright.

### Source

- REM-04-691
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-02

---

## REL-APP-261

### Title

No Exercise Before Approval Threshold

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A pending organisational Permission Grant **MUST NOT** become exercisable before its required approval threshold is satisfied.

### Rationale

Incomplete multi-party approval cannot create active authority.

### Source

- REM-04-691
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-262

### Title

Basic v0.1 Multi-Controller Support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Relay v0.1 **MAY** implement only basic multi-controller and multi-approver functionality.

### Rationale

The model permits an incremental first implementation.

### Source

- REM-04-692
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-12

---

## REL-APP-263

### Title

No Universal Single-Click Consent Assumption

**Level:** Architectural

**Normative Keyword:** **SHOULD NOT**

### Statement

The Permission Model **SHOULD NOT** assume that every Permission Grant results from one person's approval action or a single interface click.

### Rationale

The model must accommodate organisational and delegated approval patterns.

### Source

- REM-04-693
- `design-notes/04-application-and-permission-model.md`, Section 60

### Related Invariants

- CI-02
- CI-12

---

# 4. REM coverage, consolidation and exclusions

| REM range | Treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-648` | Direct | `REL-APP-245` |
| `REM-04-649`–`REM-04-652` | Consolidated role visibility | `REL-APP-246` |
| `REM-04-653`–`REM-04-654` | Direct | `REL-APP-247`–`REL-APP-248` |
| `REM-04-655`–`REM-04-659` | Non-normative service examples | Excluded |
| `REM-04-660`–`REM-04-665` | Consolidated service obligations | `REL-APP-249` |
| `REM-04-666`–`REM-04-667` | Direct | `REL-APP-250`–`REL-APP-251` |
| `REM-04-668`–`REM-04-669` | Consolidated | `REL-APP-252` |
| `REM-04-670`–`REM-04-676` | Consolidated declarations | `REL-APP-253` |
| `REM-04-677`–`REM-04-678` | Direct | `REL-APP-254`–`REL-APP-255` |
| `REM-04-679`–`REM-04-683` | Non-normative delegation examples | Excluded |
| `REM-04-684`–`REM-04-687` | Consolidated evidence | `REL-APP-256` |
| `REM-04-688`–`REM-04-690` | Direct | `REL-APP-257`–`REL-APP-259` |
| `REM-04-691` | Decomposed | `REL-APP-260`–`REL-APP-261` |
| `REM-04-692`–`REM-04-693` | Direct | `REL-APP-262`–`REL-APP-263` |

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-244`; this part runs `REL-APP-245`–`REL-APP-263`.
- Total requirements: 19; numbering is continuous.
- Provider-built and hidden service actors remain subject to the Permission Model.
- Public indexing remains policy-qualified; non-public indexing requires explicit authority.
- Delegated consent requires evidence and is never inferred from access alone.
- Pending organisational grants cannot be exercised before threshold approval.
- Example service and delegate categories remain non-normative.
- No Section 61 or later content is imported.

---

# 6. Part conclusion

Part 12 establishes consistent application treatment across first-party, backend, indexing, delegated and organisational contexts.

Part 13 should begin with Section 61 and `REM-04-694`.
