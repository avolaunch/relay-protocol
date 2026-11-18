# EA-05-04 — Application and Permission Requirements Catalogue

## Part 1 — Application Foundations, Authority, Identity and Controllers

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the foundations of the Relay Application and Permission subsystem. It establishes applications as limited delegated actors, preserves separation between application experience and a person's digital continuity, defines the core permission-model components, and specifies stable Application Identity and controller-accountability requirements.

This catalogue part is generated from the completed and verified REM-04 extraction series. The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 1–5 and REM-04 entries `REM-04-001` through `REM-04-069`.

It defines requirements governing:

- limited application authority;
- application non-ownership;
- explicit, valid and revocable Permission Grants;
- separation of digital continuity, service experience and delegated authority;
- transparent, selective and limited permission approval;
- revocation, inspection and application replacement;
- core Application and Permission Model components;
- stable machine-readable Application Identity;
- application identity continuity; and
- controller identification, responsibility and role separation.

`REM-04-006` is an explicitly non-normative model example and generates no catalogue requirement.

Section 6 and later are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-APP-001

### Title

Application Actor with Limited Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Application **MUST** be treated as software that interacts with a Relay Identity or Relay Repository only through limited requested authority rather than unrestricted control.

### Rationale

This defines the application as a delegated protocol actor and prevents application participation from becoming general control over a person's identity or repository.

### Source

- REM-04-001
- REM-04-002
- `design-notes/04-application-and-permission-model.md`, Sections 1

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-002

### Title

Read-Authority Requests

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay Application **MAY** request authority to read specified information from a Relay Identity or Relay Repository.

### Rationale

Read access is a permitted application capability, but it remains subject to the scope and approval of a valid Permission Grant.

### Source

- REM-04-003
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-06

---

## REL-APP-003

### Title

Write-Authority Requests

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay Application **MAY** request authority to submit specified information or operations to a Relay Identity or Relay Repository.

### Rationale

Write interaction is permitted only as delegated authority and does not give the application ownership of resulting repository state.

### Source

- REM-04-004
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-06
- CI-07

---

## REL-APP-004

### Title

Other Defined Interaction Requests

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay Application **MAY** request explicitly defined interaction capabilities beyond reading and writing.

### Rationale

The model permits extensible application interactions while requiring their authority to remain explicit and bounded.

### Source

- REM-04-005
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-06
- CI-12

---

## REL-APP-005

### Title

No Application Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Application **MUST NOT** be treated as acquiring ownership of a Relay Identity, Relay Repository or Relay Record merely because it creates, reads, edits, displays or otherwise accesses that object.

### Rationale

Application interaction is delegated activity. Ownership and constitutional control remain separate from the application experience.

### Source

- REM-04-007
- REM-04-008
- REM-04-009
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-02
- CI-04
- AI-07

---

## REL-APP-006

### Title

Explicit Permission Grant Basis

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Application **MUST NOT** exercise non-public authority unless that authority is established through an explicit Permission Grant.

### Rationale

An explicit grant makes delegated authority inspectable and prevents authority from arising implicitly through installation, login or application use.

### Source

- REM-04-010
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-06

---

## REL-APP-007

### Title

Valid Permission Grant Basis

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Application **MUST NOT** exercise authority under an invalid, expired, malformed, superseded or otherwise non-effective Permission Grant.

### Rationale

Authority must remain tied to an effective grant rather than the application's possession of stale or defective authorisation material.

### Source

- REM-04-011
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-06

---

## REL-APP-008

### Title

Revocable Permission Grant Basis

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Application authority **MUST** be established through a Permission Grant that can be revoked.

### Rationale

Revocability preserves the controller's continuing ability to withdraw delegated authority.

### Source

- REM-04-012
- `design-notes/04-application-and-permission-model.md`, Section 1

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-009

### Title

Separation of Continuity, Experience and Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** keep a person's underlying digital continuity, an application's service experience and the authority granted to that application conceptually and technically distinct.

### Rationale

This separation prevents an application experience or its permission state from becoming the user's identity or owning the user's continuing repository state.

### Source

- REM-04-013
- REM-04-014
- REM-04-015
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-01
- CI-02
- CI-04
- CI-06

---

## REL-APP-010

### Title

Connection Without Identity Surrender

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow a person to connect a Relay Application without surrendering control of their Relay Identity.

### Rationale

Application use must not require transferring constitutional identity authority to the application.

### Source

- REM-04-016
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-02
- CI-04

---

## REL-APP-011

### Title

Permission-Request Transparency

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** provide sufficient information for a person to understand exactly what authority an application is requesting.

### Rationale

Meaningful approval depends on the approving person being able to identify the requested capabilities before a grant is issued.

### Source

- REM-04-017
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-012

### Title

Selective Capability Approval

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow a person to approve only the capabilities required for the intended application function.

### Rationale

Selective approval limits authority to the capabilities the person chooses rather than forcing acceptance of an indivisible request.

### Source

- REM-04-018
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-013

### Title

Resource-Limited Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow application authority to be limited by resource.

### Rationale

Resource limits prevent a grant for one object or collection from becoming general repository access.

### Source

- REM-04-019
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-014

### Title

Action-Limited Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow application authority to be limited by permitted action.

### Rationale

Separating read, create, update, delete and other actions prevents one approved capability from implying another.

### Source

- REM-04-020
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-015

### Title

Duration-Limited Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow application authority to be limited by duration.

### Rationale

Time limits constrain the period during which an application may exercise delegated authority.

### Source

- REM-04-021
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-016

### Title

Purpose-Limited Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow application authority to be limited by declared purpose.

### Rationale

Purpose limitation distinguishes permission to access information from permission to use it for every possible application purpose.

### Source

- REM-04-022
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-017

### Title

Application Access Revocation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow a person to revoke an application's granted access.

### Rationale

A person must retain continuing control over whether delegated application authority remains active.

### Source

- REM-04-023
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-018

### Title

Application Activity Inspection

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow a person to inspect material activity performed by an application under delegated authority.

### Rationale

Inspection makes application use of authority accountable and supports detection of misuse or unexpected behaviour.

### Source

- REM-04-024
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-019

### Title

Application Replacement Without Repository-State Loss

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The model **MUST** allow a person to replace an application without losing canonical Relay Repository state.

### Rationale

Repository continuity must survive application replacement so that applications remain replaceable interfaces rather than owners of user state.

### Source

- REM-04-025
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-020

### Title

Authorised Action on a Person's Behalf

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay Application **MAY** perform actions on behalf of a person where those actions are authorised by a valid Permission Grant.

### Rationale

Applications may act as delegated agents within approved limits without acquiring the person's identity or constitutional authority.

### Source

- REM-04-026
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-06

---

## REL-APP-021

### Title

Application and Person Distinction

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Application **MUST NOT** be represented or treated as the person or Relay Identity on whose behalf it acts.

### Rationale

Delegated action does not merge the application actor with the identity that authorised it.

### Source

- REM-04-027
- `design-notes/04-application-and-permission-model.md`, Section 2

### Related Invariants

- CI-01
- CI-02
- CI-04

---

## REL-APP-022

### Title

Core Permission-Model Components

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** include an Application Identity, Application Manifest, Permission Request, Permission Grant, Scope, Capability, Authorisation Session, authority-exercising Access Token or Capability Token, Audit Event, Revocation Record and Consent Receipt.

### Rationale

These components separate application identity, declared behaviour, requested and granted authority, credential exercise, accountability, revocation and consent evidence into distinct protocol objects or functions.

### Source

- REM-04-028
- REM-04-029
- REM-04-030
- REM-04-031
- REM-04-032
- REM-04-033
- REM-04-034
- REM-04-035
- REM-04-037
- REM-04-038
- REM-04-039
- `design-notes/04-application-and-permission-model.md`, Section 3

### Related Invariants

- CI-06
- CI-08
- CI-10

---

## REL-APP-023

### Title

Delegated-Key Component

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Where cryptographic delegation is supported, the Application and Permission Model **MUST** include a Delegated Key component.

### Rationale

A distinct delegated-key component permits cryptographic application authority to be bounded and evaluated separately from root identity authority.

### Source

- REM-04-036
- `design-notes/04-application-and-permission-model.md`, Section 3

### Related Invariants

- CI-02
- CI-06
- CI-08

---

## REL-APP-024

### Title

Stable Machine-Readable Application Identity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Relay Application **MUST** have a stable, machine-readable Application Identity.

### Rationale

A stable protocol identity allows grants, manifests, activity and revocation to refer to the application independently of changeable presentation or deployment details.

### Source

- REM-04-040
- REM-04-041
- `design-notes/04-application-and-permission-model.md`, Section 4

### Related Invariants

- CI-05
- CI-08

---

## REL-APP-025

### Title

Application Identity Distinct from Mutable or Local Attributes

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An Application Identity **MUST** remain distinct from any associated company name, visible product or brand name, domain, callback URL, installation, device or application version number.

### Rationale

Mutable branding, infrastructure and installation attributes cannot provide the stable protocol identity needed for grant continuity and accountability.

### Source

- REM-04-042
- REM-04-043
- REM-04-044
- REM-04-045
- REM-04-046
- REM-04-047
- REM-04-048
- `design-notes/04-application-and-permission-model.md`, Section 4

### Related Invariants

- CI-05

---

## REL-APP-026

### Title

Branding and Infrastructure Change with Identity Continuity

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** change its branding or infrastructure without creating a new Application Identity, provided identity continuity is authorised and verifiable.

### Rationale

Application identity should survive legitimate presentation and hosting changes when continuity can be established safely.

### Source

- REM-04-049
- REM-04-050
- `design-notes/04-application-and-permission-model.md`, Section 4

### Related Invariants

- CI-05

---

## REL-APP-027

### Title

Authorised Application Identity Continuity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Application Identity continuity across branding or infrastructure changes **MUST** be authorised by a valid authority for that Application Identity.

### Rationale

Continuity must not be self-asserted by an unauthorised party after a change of brand, domain or hosting infrastructure.

### Source

- REM-04-051
- `design-notes/04-application-and-permission-model.md`, Section 4

### Related Invariants

- CI-02
- CI-05

---

## REL-APP-028

### Title

Verifiable Application Identity Continuity

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Application Identity continuity across branding or infrastructure changes **MUST** be verifiable.

### Rationale

Other actors must be able to distinguish legitimate continuity from impersonation or an unauthorised takeover.

### Source

- REM-04-052
- `design-notes/04-application-and-permission-model.md`, Section 4

### Related Invariants

- CI-05
- CI-08

---

## REL-APP-029

### Title

Responsible Application Controller Identification

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Every Application Identity **MUST** identify the person, organisation or other authority responsible for controlling the application.

### Rationale

A stable application actor requires an accountable controller responsible for its declarations, credentials and use of authority.

### Source

- REM-04-053
- `design-notes/04-application-and-permission-model.md`, Section 5

### Related Invariants

- CI-02
- CI-10

---

## REL-APP-030

### Title

Supported Application Controller Categories

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** support an individual person, organisation, open-source project or Relay Identity as the responsible controller of an Application Identity.

### Rationale

Applications may be governed by different accountable authority structures, and the model must represent those structures without assuming a single corporate form.

### Source

- REM-04-054
- REM-04-055
- REM-04-056
- REM-04-057
- `design-notes/04-application-and-permission-model.md`, Section 5

### Related Invariants

- CI-02
- CI-12

---

## REL-APP-031

### Title

Application Controller Responsibilities

**Level:** Governance

**Normative Keyword:** **MUST**

### Statement

An application controller **MUST** be responsible for the accuracy of the Application Manifest, handling of granted access, security of credentials and keys, compliance with declared purposes and retention commitments, processing of revocation, and reporting of material security incidents affecting Relay authority or accessed information.

### Rationale

Concentrating these duties on the identified controller creates an accountable authority for the application's declarations, security posture and exercise of delegated access.

### Source

- REM-04-058
- REM-04-059
- REM-04-060
- REM-04-061
- REM-04-062
- REM-04-063
- REM-04-064
- `design-notes/04-application-and-permission-model.md`, Section 5

### Related Invariants

- CI-02
- CI-10
- CI-11

---

## REL-APP-032

### Title

Application Actor Role Distinctions

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The protocol **SHOULD** distinguish the Application Identity, application controller, hosting provider, software publisher and individual installation from one another.

### Rationale

Separating these roles prevents responsibility, identity and installation-specific state from being collapsed into one ambiguous application actor.

### Source

- REM-04-065
- REM-04-066
- REM-04-067
- REM-04-068
- REM-04-069
- `design-notes/04-application-and-permission-model.md`, Section 5

### Related Invariants

- CI-02
- CI-05
- CI-11

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-001`–`REM-04-002` | Consolidated | `REL-APP-001` |
| `REM-04-003`–`REM-04-005` | Represented separately | `REL-APP-002`–`REL-APP-004` |
| `REM-04-006` | Non-normative model example | Excluded; no `REL-APP` identifier |
| `REM-04-007`–`REM-04-009` | Consolidated | `REL-APP-005` |
| `REM-04-010`–`REM-04-012` | Represented separately | `REL-APP-006`–`REL-APP-008` |
| `REM-04-013`–`REM-04-015` | Consolidated | `REL-APP-009` |
| `REM-04-016`–`REM-04-027` | Direct or one-to-one representation | `REL-APP-010`–`REL-APP-021` |
| `REM-04-028`–`REM-04-035`, `REM-04-037`–`REM-04-039` | Consolidated component set | `REL-APP-022` |
| `REM-04-036` | Direct | `REL-APP-023` |
| `REM-04-040`–`REM-04-041` | Consolidated | `REL-APP-024` |
| `REM-04-042`–`REM-04-048` | Consolidated distinction set | `REL-APP-025` |
| `REM-04-049`–`REM-04-050` | Consolidated | `REL-APP-026` |
| `REM-04-051`–`REM-04-052` | Represented separately | `REL-APP-027`–`REL-APP-028` |
| `REM-04-053` | Direct | `REL-APP-029` |
| `REM-04-054`–`REM-04-057` | Consolidated controller-category set | `REL-APP-030` |
| `REM-04-058`–`REM-04-064` | Consolidated responsibility set | `REL-APP-031` |
| `REM-04-065`–`REM-04-069` | Consolidated role-distinction set | `REL-APP-032` |

Every in-scope REM entry is represented directly, consolidated without loss of its independently testable clauses, or explicitly excluded because of verified non-normative status.

---

# 5. Editorial QA record

## Scope verification

- Authoritative source content is limited to Sections 1–5.
- The verified extraction range is `REM-04-001` through `REM-04-069`.
- No requirement from Section 6 or later is imported.

## Identifier verification

- First identifier: `REL-APP-001`.
- Final identifier: `REL-APP-032`.
- Total catalogue requirements in this part: 32.
- Identifiers are continuous and unique.

## Source-status verification

- `REM-04-006` remains a non-normative example and generates no catalogue requirement.
- No example product category or interface type is made mandatory.
- Conditional support for Delegated Keys remains conditional on cryptographic delegation being supported.
- Branding or infrastructure continuity retains the requirements that continuity be authorised and verifiable.

## Consolidation verification

- Consolidated component, distinction and responsibility lists preserve each source-defined clause.
- Read, write and other interactions remain separately traceable.
- Explicit, valid and revocable grant properties remain separately testable.
- Resource, action, duration and purpose limitations remain separately testable.

---

# 6. Part conclusion

Part 1 establishes the Application and Permission Model's foundational authority boundaries, stable application identity and accountable controller requirements.

Part 2 should begin with source Section 6 and `REM-04-070`.
