# EA-05-04 — Application and Permission Requirements Catalogue

## Part 13 — Denial, Standing Policy, Emergency Revocation and Required Operations

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines denial, standing policies, stale-grant handling, emergency revocation and required Relay v0.1 application operations.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 61–65 and `REM-04-694` through `REM-04-747`.

`REM-04-702`–`REM-04-706` are verified non-normative standing-policy examples and generate no requirements.

Section 66 and later are deferred.

---

# 3. Requirements

---

## REL-APP-264

### Title

Permission Request Denial

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A user **MAY** deny a Permission Request.

### Rationale

Consent remains voluntary.

### Source

- REM-04-694
- `design-notes/04-application-and-permission-model.md`, Section 61

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-265

### Title

Supported Denial Modes

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The authorisation model **MUST** support complete, partial, temporary and standing-policy-based denial of a Permission Request.

### Rationale

Different denial modes allow authority to be withheld proportionately and conditionally.

### Source

- REM-04-695
- REM-04-696
- REM-04-697
- REM-04-698
- `design-notes/04-application-and-permission-model.md`, Section 61

### Related Invariants

- CI-06

---

## REL-APP-266

### Title

Private Denial Policy Protection

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The authorisation system **SHOULD** avoid disclosing unnecessary private policy details and support a generic denial response where detail would reveal such information.

### Rationale

An application needs the denial result but not every private reason behind it.

### Source

- REM-04-699
- REM-04-700
- `design-notes/04-application-and-permission-model.md`, Section 61

### Related Invariants

- CI-11

---

## REL-APP-267

### Title

Standing Authorisation Policies

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A user **MAY** define standing rules governing evaluation of Permission Requests.

### Rationale

Standing policy supports consistent preconfigured decisions.

### Source

- REM-04-701
- `design-notes/04-application-and-permission-model.md`, Section 62

### Related Invariants

- CI-06

---

## REL-APP-268

### Title

Authorisation-Service Policy Evaluation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An authorisation service **MAY** evaluate Permission Requests against applicable standing policies.

### Rationale

Policy evaluation can automate constraints while remaining subordinate to user authority.

### Source

- REM-04-707
- `design-notes/04-application-and-permission-model.md`, Section 62

### Related Invariants

- CI-06

---

## REL-APP-269

### Title

Low-Risk Limit on Automatic Approval

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Automatic approval **SHOULD** be limited to low-risk conditions explicitly pre-authorised by the user or governing authority.

### Rationale

Automation must not silently create broad or high-risk authority.

### Source

- REM-04-708
- `design-notes/04-application-and-permission-model.md`, Section 62

### Related Invariants

- CI-06

---

## REL-APP-270

### Title

Inactive-Grant Policy Responses

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An inactive Permission Grant **MAY** be flagged for review, expire under applicable user policy, be restricted pending re-authentication, or remain unchanged where policy and risk controls permit.

### Rationale

The source permits risk-sensitive treatment rather than one universal inactivity rule.

### Source

- REM-04-709
- REM-04-710
- REM-04-711
- REM-04-712
- `design-notes/04-application-and-permission-model.md`, Section 63

### Related Invariants

- CI-06

---

## REL-APP-271

### Title

Visibility of Stale Permissions

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The system **SHOULD** allow users to identify stale or long-unused permissions.

### Rationale

Visibility supports informed review and revocation.

### Source

- REM-04-713
- `design-notes/04-application-and-permission-model.md`, Section 63

### Related Invariants

- CI-02
- CI-10

---

## REL-APP-272

### Title

Discourage Forgotten Indefinite Access

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Relay implementations **SHOULD** discourage indefinite access that remains active but forgotten by the user.

### Rationale

Long-unused authority creates avoidable risk.

### Source

- REM-04-714
- `design-notes/04-application-and-permission-model.md`, Section 63

### Related Invariants

- CI-06

---

## REL-APP-273

### Title

Emergency Revocation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A user **SHOULD** be able to invoke an emergency revocation action affecting all applications.

### Rationale

A broad emergency control supports rapid containment.

### Source

- REM-04-715
- `design-notes/04-application-and-permission-model.md`, Section 64

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-274

### Title

Emergency Revocation Scenarios

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Emergency revocation **SHOULD** support containment after device theft, during or after identity recovery, on suspected compromise and after malicious application activity.

### Rationale

These scenarios require rapid termination of application authority.

### Source

- REM-04-716
- REM-04-717
- REM-04-718
- REM-04-719
- `design-notes/04-application-and-permission-model.md`, Section 64

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-275

### Title

Emergency Revocation Preservation

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Emergency revocation **SHOULD NOT** delete repository records, terminate the Relay Identity or erase audit history.

### Rationale

Emergency containment affects authority, not identity existence, canonical records or evidence.

### Source

- REM-04-720
- REM-04-721
- REM-04-722
- `design-notes/04-application-and-permission-model.md`, Section 64

### Related Invariants

- CI-01
- CI-10
- AI-01

---

## REL-APP-276

### Title

Application Identity and Manifest Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support registering an Application Identity and resolving and verifying an Application Manifest.

### Rationale

These operations establish and validate the application actor and its declarations.

### Source

- REM-04-723
- REM-04-724
- REM-04-725
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-05
- CI-08

---

## REL-APP-277

### Title

Permission Request Decision Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support submitting and displaying Permission Requests and approving them fully, approving them partially or denying them.

### Rationale

These operations cover the complete consent decision path.

### Source

- REM-04-726
- REM-04-727
- REM-04-728
- REM-04-729
- REM-04-730
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-06

---

## REL-APP-278

### Title

Permission Grant Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support issuing, reading, narrowing, revoking and expiring Permission Grants, and requiring re-authorisation where continuing authority is invalid or insufficient.

### Rationale

These operations manage the grant through its complete lifecycle.

### Source

- REM-04-731
- REM-04-732
- REM-04-739
- REM-04-740
- REM-04-743
- REM-04-744
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-06

---

## REL-APP-279

### Title

Token and Renewable Access Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support issuing short-lived Access Tokens, renewing access while authority remains valid and validating tokens before use.

### Rationale

Credential operations must remain tied to continuing authority.

### Source

- REM-04-733
- REM-04-734
- REM-04-735
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-280

### Title

Delegated Key and Installation Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support creating a delegated application key associated with a Permission Grant and revoking a specific installation or delegated key.

### Rationale

These operations provide bounded cryptographic delegation and granular revocation.

### Source

- REM-04-736
- REM-04-741
- REM-04-742
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-281

### Title

Application Inspection Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support listing connected applications and inspecting application activity.

### Rationale

Users need visibility into actors and their use of authority.

### Source

- REM-04-737
- REM-04-738
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-02
- CI-10

---

## REL-APP-282

### Title

Consent and Audit Recording Operations

**Level:** Operational

**Normative Keyword:** **MUST**

### Statement

A compliant Relay v0.1 implementation **MUST** support recording Consent Receipts and relevant authorisation Audit Events.

### Rationale

Receipts and events provide consent and activity evidence.

### Source

- REM-04-745
- REM-04-746
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-10

---

## REL-APP-283

### Title

Limited Initial High-Authority Capability Support

**Level:** Operational

**Normative Keyword:** **MAY**

### Statement

The first Relay v0.1 reference implementation **MAY** limit support for high-authority capability grants.

### Rationale

The initial implementation can remain narrower without changing the model's authority distinctions.

### Source

- REM-04-747
- `design-notes/04-application-and-permission-model.md`, Section 65

### Related Invariants

- CI-12

---

# 4. REM coverage, consolidation and exclusions

All normative entries `REM-04-694` through `REM-04-747` are represented directly or through source-compatible consolidation. The required operation list is grouped by lifecycle domain without omitting any operation. `REM-04-702` through `REM-04-706` remain non-normative policy examples and generate no catalogue identifiers.

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-263`; this part runs `REL-APP-264`–`REL-APP-283`.
- Total requirements: 20; numbering is continuous.
- Denial modes remain mandatory capabilities while denial itself remains a user permission.
- Automatic approval retains its low-risk and explicit-pre-authorisation qualifications.
- Emergency revocation preserves identity, records and audit history.
- Every Section 65 operation is represented.
- No example standing policy became mandatory.
- No Section 66 or later content is imported.

---

# 6. Part conclusion

Part 13 establishes denial and policy controls, emergency containment and the required v0.1 operational surface.

Part 14 should begin with Section 66 and `REM-04-748`.
