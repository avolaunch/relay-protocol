# EA-05-04 — Application and Permission Requirements Catalogue

## Part 14 — Permission Invariants and Compliance Scenario

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part catalogues the mandatory permission invariants and the recommendation-level end-to-end compliance scenario.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 66–67 and `REM-04-748` through `REM-04-792`.

Section 67 remains a `SHOULD`-level scenario. Its decomposition does not promote scenario narrative to invariant-level `MUST`.

Section 68 and later are deferred.

---

# 3. Requirements

---

## REL-APP-284

### Title

Continuous Permission Invariants

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every compliant Relay Application and Permission implementation **MUST** preserve all Section 66 permission invariants at all times.

### Rationale

The invariants govern every lifecycle stage and are not optional guidance.

### Source

- REM-04-748
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06

---

## REL-APP-285

### Title

Authority Requires a Valid Basis

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** exercise protected authority without a currently valid Permission Grant or applicable public-access rule.

### Rationale

Registration, authentication or credential possession alone does not create authority.

### Source

- REM-04-749
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06

---

## REL-APP-286

### Title

Grant Cannot Exceed Approval

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Permission Grant **MUST NOT** authorise resources, actions, purposes, duration, interaction modes, retention, onward sharing, AI use or conditions beyond explicit approval.

### Rationale

Issued authority must faithfully encode the approval.

### Source

- REM-04-750
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06

---

## REL-APP-287

### Title

No Application Grant Self-Expansion

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** expand, replace or reinterpret its own grant to obtain additional authority without valid approval.

### Rationale

Applications cannot control expansion of their authority.

### Source

- REM-04-751
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06

---

## REL-APP-288

### Title

Revocation Does Not Delete Canonical Records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Revocation **MUST NOT**, solely because of revocation, delete canonical records created or submitted through the application.

### Rationale

Revocation affects future authority, not valid repository state.

### Source

- REM-04-752
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-289

### Title

Read Permission Has No Implied Secondary Uses

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Permission to read a resource **MUST NOT** be interpreted as permission to retain an external copy, redistribute or disclose it, or use it for model training.

### Rationale

Reading, retention, sharing and training are independent authorities.

### Source

- REM-04-753
- REM-04-754
- REM-04-755
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-290

### Title

Create Permission Has No Implied Destructive or Visibility Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Permission to create a record **MUST NOT** be interpreted as permission to delete records or change record visibility or audience.

### Rationale

Creation does not include destructive or exposure-changing actions.

### Source

- REM-04-756
- REM-04-757
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06
- AI-07

---

## REL-APP-291

### Title

Ordinary Content Access Has No Constitutional Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Ordinary content access **MUST NOT** be interpreted as authority over the Relay Identity, controlling keys, recovery mechanisms or provider or repository migration.

### Rationale

Constitutional authority remains separate from content permissions.

### Source

- REM-04-758
- REM-04-759
- REM-04-760
- REM-04-761
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-292

### Title

Visible Name Is Not Protocol Identity

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application's visible product name, brand or display label **MUST NOT** be used as its permanent protocol identity.

### Rationale

Mutable presentation cannot replace stable Application Identity.

### Source

- REM-04-762
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-05

---

## REL-APP-293

### Title

Renewed Approval for Material Purpose Change

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An application **MUST** obtain renewed approval before using previously granted access for a materially changed purpose.

### Rationale

Prior consent does not cover materially new use.

### Source

- REM-04-763
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-294

### Title

Provider-Built Clients Remain Applications

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A client built, distributed or operated by the current provider **MUST** remain subject to the Application and Permission Model.

### Rationale

Provider affiliation does not remove application obligations.

### Source

- REM-04-764
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-04
- CI-11

---

## REL-APP-295

### Title

Inspectable Active Grants

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The user or authorised controller **MUST** be able to inspect all active Permission Grants affecting the Relay Identity or Repository.

### Rationale

Active authority must remain visible.

### Source

- REM-04-765
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-296

### Title

Revocable Active Grants

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The user or authorised controller **MUST** be able to revoke active Permission Grants.

### Rationale

Continuing control requires withdrawal capability.

### Source

- REM-04-766
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-297

### Title

Migration Cannot Broaden Application Access

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Provider or repository migration **MUST NOT** silently broaden application resources, actions, purposes, duration or other authority.

### Rationale

Migration preserves constraints unless a change is explicitly approved.

### Source

- REM-04-767
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-298

### Title

Suspension Cannot Erase User Records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Application suspension **MUST NOT** erase user-controlled or user-owned repository records.

### Rationale

Application enforcement remains separate from repository ownership.

### Source

- REM-04-768
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-299

### Title

Tokens Evidence Delegated Authority Only

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An Access Token, Capability Token, refresh token or equivalent credential **MUST** be treated only as evidence of delegated authority within its grant and not as proof of ownership or broader control of the Relay Identity.

### Rationale

Credential possession establishes bounded authority, not constitutional ownership.

### Source

- REM-04-769
- `design-notes/04-application-and-permission-model.md`, Section 66

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-300

### Title

Basic Compliance Scenario

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A basic implementation **SHOULD** pass the complete Section 67 compliance scenario while preserving user authority and application replaceability.

### Rationale

The scenario tests the permission lifecycle end to end.

### Source

- REM-04-770
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-02
- CI-04

---

## REL-APP-301

### Title

Scenario Request and Partial Approval

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The compliance scenario **SHOULD** represent requested resources, actions and AI purposes distinctly and support approval of a proper subset without requiring full approval.

### Rationale

The scenario must demonstrate granular consent.

### Source

- REM-04-771
- REM-04-772
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-06

---

## REL-APP-302

### Title

Scenario Grant Excludes Denied Authority

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The scenario's grant **SHOULD** exclude denied deletion, private-draft and model-training authority and contain only expressly approved capabilities.

### Rationale

The issued grant must reflect the partial decision.

### Source

- REM-04-773
- REM-04-774
- REM-04-775
- REM-04-776
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-06

---

## REL-APP-303

### Title

Scenario Operation Attribution

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

For a record created under the scenario grant, the repository **SHOULD** record the authorising Relay Identity, submitting Application Identity and a verifiable reference to the Permission Grant.

### Rationale

The scenario must demonstrate attributable delegated submission.

### Source

- REM-04-777
- REM-04-778
- REM-04-779
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-10

---

## REL-APP-304

### Title

Scenario Rejection of Unauthorised Deletion

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The repository **SHOULD** reject the scenario application's deletion attempt where its grant lacks deletion authority.

### Rationale

The scenario verifies action-scope enforcement.

### Source

- REM-04-780
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-06
- CI-07

---

## REL-APP-305

### Title

Scenario Material Purpose Change

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A manifest or policy change permitting general model training **SHOULD** leave the existing grant unchanged and require user review and approval before the changed purpose is exercised.

### Rationale

The scenario verifies that material purpose change cannot expand prior consent.

### Source

- REM-04-781
- REM-04-782
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-306

### Title

Scenario Revocation Effects

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

After scenario revocation, new token issuance, update submissions and private event delivery **SHOULD** cease while the validly created record remains in the repository.

### Rationale

The scenario verifies prospective revocation without record deletion.

### Source

- REM-04-783
- REM-04-784
- REM-04-785
- REM-04-786
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-04
- CI-06
- AI-01

---

## REL-APP-307

### Title

Scenario Application Replacement

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The scenario **SHOULD** allow a separately authorised replacement application to read and update the existing record without export, copying, identity recreation or repository-state recreation.

### Rationale

The scenario verifies application replaceability over portable state.

### Source

- REM-04-787
- REM-04-788
- REM-04-789
- REM-04-790
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-04

---

## REL-APP-308

### Title

Scenario Preservation of User Authority and Replaceability

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The scenario **SHOULD** preserve the user's underlying authority and ability to replace applications without losing or recreating repository state.

### Rationale

These properties define successful completion of the scenario.

### Source

- REM-04-791
- REM-04-792
- `design-notes/04-application-and-permission-model.md`, Section 67

### Related Invariants

- CI-02
- CI-04

---

# 4. REM coverage and consolidation

All entries `REM-04-748` through `REM-04-792` are represented. Related invariant clauses and scenario steps are consolidated only where their independently testable effects remain explicit.

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-283`; this part runs `REL-APP-284`–`REL-APP-308`.
- Total requirements: 25; numbering is continuous.
- Section 66 invariants retain `MUST` or `MUST NOT`.
- Read, create and ordinary-content permissions do not imply distinct secondary or constitutional authority.
- Section 67 remains entirely at `SHOULD` strength.
- The scenario preserves partial approval, enforcement, attribution, prospective revocation and application replacement.
- No Section 68 or later content is imported.

---

# 6. Part conclusion

Part 14 preserves the Application and Permission Model's invariants and executable compliance scenario.

Part 15 should begin with Section 68 and `REM-04-793`.
