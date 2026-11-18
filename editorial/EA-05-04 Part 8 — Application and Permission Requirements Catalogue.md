# EA-05-04 — Application and Permission Requirements Catalogue

## Part 8 — Interaction Modes, High Authority and Revocation

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part distinguishes interactive and background authority, protects high-authority operations, bounds delegated permission management and defines granular revocation.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 36–40 and `REM-04-440` through `REM-04-494`.

`REM-04-444` and `REM-04-481`–`REM-04-493` are verified non-normative examples. They generate no catalogue requirements and select no interaction field, Revocation Record schema or reason vocabulary.

Section 41 and later are deferred.

---

# 3. Requirements

---

## REL-APP-150

### Title

Interaction-Mode Distinction

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay **SHOULD** distinguish user-present and user-absent actions when representing or evaluating application authority.

### Rationale

The modes have different consent and risk characteristics.

### Source

- REM-04-440
- `design-notes/04-application-and-permission-model.md`, Section 36

### Related Invariants

- CI-06

---

## REL-APP-151

### Title

User-Present Action Semantics

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A user-present classification **MUST** mean that the user is actively interacting with the application when the action occurs.

### Rationale

The classification must describe an actual contemporaneous interaction.

### Source

- REM-04-441
- `design-notes/04-application-and-permission-model.md`, Section 36

### Related Invariants

- CI-06

---

## REL-APP-152

### Title

User-Absent Action Semantics

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A user-absent classification **MUST** mean that the application acts later, automatically or continuously without active user interaction at execution time.

### Rationale

Background authority must remain distinguishable from interactive authority.

### Source

- REM-04-442
- `design-notes/04-application-and-permission-model.md`, Section 36

### Related Invariants

- CI-06

---

## REL-APP-153

### Title

Independent Interaction-Mode Authority

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Permission Grant **MAY** authorise an action in one interaction mode while withholding it in the other.

### Rationale

Authority can be limited to the risk profile the user approved.

### Source

- REM-04-443
- `design-notes/04-application-and-permission-model.md`, Section 36

### Related Invariants

- CI-06

---

## REL-APP-154

### Title

No Implicit Background Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Authority for a user-present action **MUST NOT** be interpreted as authority to perform the same action while the user is absent.

### Rationale

Interactive approval does not silently become continuing background authority.

### Source

- REM-04-445
- `design-notes/04-application-and-permission-model.md`, Section 36

### Related Invariants

- CI-06

---

## REL-APP-155

### Title

Stronger Protection for High-Authority Operations

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Operations classified as high-authority **MUST** receive stronger protection than ordinary content operations.

### Rationale

These operations can alter constitutional control or broad repository state.

### Source

- REM-04-446
- `design-notes/04-application-and-permission-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-156

### Title

High-Authority Operation Classes

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Provider migration, export containing private records, controlling-key rotation, recovery changes, identity-control transfer, repository-wide erasure and delegation of permission management **MUST** be treated as high-authority operations.

### Rationale

The source identifies each operation as requiring heightened protection.

### Source

- REM-04-447
- REM-04-448
- REM-04-449
- REM-04-450
- REM-04-451
- REM-04-452
- REM-04-453
- `design-notes/04-application-and-permission-model.md`, Section 37

### Related Invariants

- CI-02
- CI-03
- CI-06

---

## REL-APP-157

### Title

No High Authority in Ordinary Content Tokens

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A normal content-application token **MUST NOT** authorise a protocol-defined high-authority operation.

### Rationale

Ordinary content access cannot become identity, recovery, migration or permission-control authority.

### Source

- REM-04-454
- `design-notes/04-application-and-permission-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-158

### Title

High-Authority Safeguards

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A high-authority action **SHOULD** require fresh and stronger authentication, explicit confirmation and an operation-specific capability, and should support delay, secondary approval or an equivalent safeguard where risk warrants it.

### Rationale

Layered safeguards reduce accidental or compromised execution of consequential operations.

### Source

- REM-04-455
- REM-04-456
- REM-04-457
- REM-04-458
- REM-04-459
- `design-notes/04-application-and-permission-model.md`, Section 37

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-159

### Title

No Ordinary Application Self-Escalation

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** normally be permitted to grant itself additional permissions.

### Rationale

Applications should not control expansion of their own authority.

### Source

- REM-04-460
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-06

---

## REL-APP-160

### Title

No Ordinary Third-Party Permission Granting

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

An application **SHOULD NOT** normally be permitted to grant additional permissions to other applications.

### Rationale

Delegating authority to other actors is a separate high-authority capability.

### Source

- REM-04-461
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-06

---

## REL-APP-161

### Title

Permission Management Is High Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Permission-management authority **MUST** be classified and protected as a high-authority capability.

### Rationale

Permission management can expand, narrow or revoke access across applications.

### Source

- REM-04-462
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-162

### Title

Delegated Permission-Management Boundaries

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A delegated permission-management grant **MUST** define the applications the delegate may manage, maximum scopes, maximum grant duration, whether individual actions require user confirmation, and whether the delegate may revoke grants.

### Rationale

Explicit boundaries prevent a permission delegate from acquiring open-ended authorisation power.

### Source

- REM-04-463
- REM-04-464
- REM-04-465
- REM-04-466
- REM-04-467
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-06

---

## REL-APP-163

### Title

Managed-Identity Permission Delegation

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

The protocol **MAY** support delegated permission management for enterprise-managed or guardian-managed identities.

### Rationale

The model permits managed contexts without making delegation the default for every user.

### Source

- REM-04-468
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-12

---

## REL-APP-164

### Title

No Default Consumer Permission Delegation

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Delegated permission-management authority **SHOULD NOT** be enabled as standard consumer behaviour.

### Rationale

High-impact delegation should require an explicit managed-identity context and approval.

### Source

- REM-04-469
- `design-notes/04-application-and-permission-model.md`, Section 38

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-165

### Title

User Grant Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The user **MUST** be able to revoke an issued Permission Grant.

### Rationale

Continuing user authority requires the ability to terminate delegated access.

### Source

- REM-04-470
- `design-notes/04-application-and-permission-model.md`, Section 39

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-166

### Title

Whole-Application Revocation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The revocation model **MUST** support revocation of all authority granted to an application.

### Rationale

A user must be able to disconnect an application comprehensively.

### Source

- REM-04-471
- `design-notes/04-application-and-permission-model.md`, Section 39

### Related Invariants

- CI-06

---

## REL-APP-167

### Title

Installation-Specific Revocation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Where installations are distinguished, the revocation model **SHOULD** support revocation of one installation without necessarily revoking the Application Identity.

### Rationale

Installation-level revocation limits disruption when only one device or installation is affected.

### Source

- REM-04-472
- `design-notes/04-application-and-permission-model.md`, Section 39

### Related Invariants

- CI-06

---

## REL-APP-168

### Title

Granular Revocation Targets

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The revocation model **MUST** support withdrawal of one scope, one collection, one record, one delegated key, refresh authority or a specified active session without requiring revocation of unrelated authority.

### Rationale

Granular revocation allows the affected authority to end while preserving independent valid permissions.

### Source

- REM-04-473
- REM-04-474
- REM-04-475
- REM-04-476
- REM-04-477
- REM-04-478
- `design-notes/04-application-and-permission-model.md`, Section 39

### Related Invariants

- CI-06

---

## REL-APP-169

### Title

Prompt Future Effect of Revocation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

A revocation **MUST** become effective against future access as quickly as practical.

### Rationale

The qualification recognises propagation realities while requiring prompt termination of new authority exercise.

### Source

- REM-04-479
- `design-notes/04-application-and-permission-model.md`, Section 39

### Related Invariants

- CI-06

---

## REL-APP-170

### Title

Revocation Record Semantics

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Revocation Record **MUST** identify authority that is no longer valid.

### Rationale

The record provides persistent evidence that an authority object cannot support future access.

### Source

- REM-04-480
- `design-notes/04-application-and-permission-model.md`, Section 40

### Related Invariants

- CI-10

---

## REL-APP-171

### Title

Privacy-Preserving Revocation Reason

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Revocation Record **MAY** keep its detailed reason private or expose only a generalised reason where fuller disclosure would create security, privacy or safety risk.

### Rationale

Revocation can remain effective without revealing sensitive policy or incident details.

### Source

- REM-04-494
- `design-notes/04-application-and-permission-model.md`, Section 40

### Related Invariants

- CI-10
- CI-11

---

# 4. REM coverage, consolidation and exclusions

| REM range | Treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-440`–`REM-04-443` | Direct | `REL-APP-150`–`REL-APP-153` |
| `REM-04-444` | Non-normative example | Excluded |
| `REM-04-445`–`REM-04-446` | Direct | `REL-APP-154`–`REL-APP-155` |
| `REM-04-447`–`REM-04-453` | Consolidated operation classes | `REL-APP-156` |
| `REM-04-454` | Direct | `REL-APP-157` |
| `REM-04-455`–`REM-04-459` | Consolidated safeguards | `REL-APP-158` |
| `REM-04-460`–`REM-04-462` | Direct | `REL-APP-159`–`REL-APP-161` |
| `REM-04-463`–`REM-04-467` | Consolidated boundaries | `REL-APP-162` |
| `REM-04-468`–`REM-04-472` | Direct | `REL-APP-163`–`REL-APP-167` |
| `REM-04-473`–`REM-04-478` | Consolidated revocation targets | `REL-APP-168` |
| `REM-04-479`–`REM-04-480` | Direct | `REL-APP-169`–`REL-APP-170` |
| `REM-04-481`–`REM-04-493` | Non-normative example schema and vocabulary | Excluded |
| `REM-04-494` | Direct | `REL-APP-171` |

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-149`; this part runs `REL-APP-150`–`REL-APP-171`.
- Total requirements: 22; numbering is continuous.
- User-present authority does not imply background authority.
- High-authority classifications and ordinary-token prohibition retain `MUST` or `MUST NOT`.
- Granular revocation preserves the source's promptness qualification.
- Illustrative Revocation Record fields and reasons remain non-normative.
- No Section 41 or later content is imported.

---

# 6. Part conclusion

Part 8 establishes interaction-mode separation, heightened protection for constitutional operations and granular revocation.

Part 9 should begin with Section 41 and `REM-04-495`.
