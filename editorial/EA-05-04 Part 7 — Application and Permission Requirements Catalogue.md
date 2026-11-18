# EA-05-04 — Application and Permission Requirements Catalogue

## Part 7 — Long-Running Access, Capability Tokens, Delegated Keys and Installations

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines renewable long-running access, capability-based authority, delegated application keys, multi-installation identity and background access.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 31–35 and `REM-04-391` through `REM-04-439`.

Verified non-normative entries `REM-04-400`–`REM-04-408`, `REM-04-420`–`REM-04-424` and `REM-04-432`–`REM-04-436` generate no catalogue requirements. No example capability, installation category or background use case is made mandatory.

Section 36 and later are deferred.

---

# 3. Requirements

---

## REL-APP-132

### Title

Preference for Short-Lived Access Tokens

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Relay implementations **SHOULD** prefer short-lived Access Tokens over unnecessarily long-lived tokens.

### Rationale

Short validity limits continued exercise after authority changes.

### Source

- REM-04-391
- `design-notes/04-application-and-permission-model.md`, Section 31

### Related Invariants

- CI-06

---

## REL-APP-133

### Title

Long-Running Access Mechanisms

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An implementation **MAY** support long-running access through refresh tokens, renewable capability sessions, delegated application keys, or periodic or event-triggered re-authorisation.

### Rationale

The source permits several renewable mechanisms without selecting one universal design.

### Source

- REM-04-392
- REM-04-393
- REM-04-394
- REM-04-395
- `design-notes/04-application-and-permission-model.md`, Section 31

### Related Invariants

- CI-06
- CI-12

---

## REL-APP-134

### Title

Independent Revocation of Refresh Authority

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Refresh authority **MUST** be revocable independently of Access Tokens that have already expired.

### Rationale

Long-running renewal authority remains a distinct revocable capability.

### Source

- REM-04-396
- `design-notes/04-application-and-permission-model.md`, Section 31

### Related Invariants

- CI-06

---

## REL-APP-135

### Title

Fresh Authentication for High-Authority Actions

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

High-authority actions **SHOULD** require fresh authentication.

### Rationale

Fresh authentication reduces reliance on stale background authority for constitutional or high-risk operations.

### Source

- REM-04-397
- `design-notes/04-application-and-permission-model.md`, Section 31

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-136

### Title

No Sole Reliance on Long-Lived Background Sessions

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

High-authority actions **SHOULD NOT** rely solely on a long-lived background session.

### Rationale

A persistent session alone is insufficient assurance for high-authority operations.

### Source

- REM-04-397
- `design-notes/04-application-and-permission-model.md`, Section 31

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-137

### Title

Capability-Based Access Support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Relay implementations **MAY** support capability-based access in addition to conventional scope-based access.

### Rationale

Capability access can express bounded object or operation authority without replacing ordinary scopes.

### Source

- REM-04-398
- `design-notes/04-application-and-permission-model.md`, Section 32

### Related Invariants

- CI-06
- CI-12

---

## REL-APP-138

### Title

Specific Capability Authority Target

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Capability Token **MUST** grant authority over a specifically identified object, operation or both.

### Rationale

A capability must define its authority target rather than confer ambiguous general access.

### Source

- REM-04-399
- `design-notes/04-application-and-permission-model.md`, Section 32

### Related Invariants

- CI-06

---

## REL-APP-139

### Title

Delegated Key Bound to an Identifiable Grant

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** receive a delegated key only where that key is associated with an identifiable Permission Grant.

### Rationale

Grant association keeps delegated cryptographic authority traceable and bounded.

### Source

- REM-04-409
- `design-notes/04-application-and-permission-model.md`, Section 33

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-140

### Title

Delegated Signing Within Grant Limits

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A delegated application key **MAY** sign repository submissions only within the limits of its associated Permission Grant.

### Rationale

Signature capability does not expand the underlying delegated authority.

### Source

- REM-04-410
- `design-notes/04-application-and-permission-model.md`, Section 33

### Related Invariants

- CI-06
- CI-07

---

## REL-APP-141

### Title

Delegated-Key Prohibited Authorities

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A delegated application key **MUST NOT** alter the Relay Identity, expand its own permissions, change recovery authority, migrate the repository, or create a valid operation outside its associated Permission Grant.

### Rationale

Delegated application keys remain subordinate to identity authority and their grants.

### Source

- REM-04-411
- REM-04-412
- REM-04-413
- REM-04-414
- REM-04-415
- `design-notes/04-application-and-permission-model.md`, Section 33

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-142

### Title

Delegated Submission Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Before accepting a delegated submission, the repository **MUST** verify both the delegated key's signature and the continuing validity of the underlying Permission Grant.

### Rationale

Both the cryptographic act and its authority basis must remain valid.

### Source

- REM-04-416
- REM-04-417
- `design-notes/04-application-and-permission-model.md`, Section 33

### Related Invariants

- CI-07
- CI-08

---

## REL-APP-143

### Title

No Acceptance Without Dual Validity

**Level:** Architectural

**Normative Keyword:** **MUST NOT**

### Statement

A delegated repository operation **MUST NOT** be accepted unless both the delegated signature and underlying Permission Grant are valid.

### Rationale

Failure of either validation removes the operation's authority basis.

### Source

- REM-04-418
- `design-notes/04-application-and-permission-model.md`, Section 33

### Related Invariants

- CI-07
- CI-08

---

## REL-APP-144

### Title

Multiple Installations per Application

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Permission Model **MUST** support one Application Identity being used across multiple installations.

### Rationale

Stable application identity must remain separate from installation-local execution contexts.

### Source

- REM-04-419
- `design-notes/04-application-and-permission-model.md`, Section 34

### Related Invariants

- CI-05

---

## REL-APP-145

### Title

Application, Installation, Device and Session Distinctions

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

The Permission Model **SHOULD** distinguish the stable Application Identity, a specific installation, its device and a specific authorisation or application session.

### Rationale

These layers have different continuity, credential and revocation boundaries.

### Source

- REM-04-425
- REM-04-426
- REM-04-427
- `design-notes/04-application-and-permission-model.md`, Section 34

### Related Invariants

- CI-05
- CI-11

---

## REL-APP-146

### Title

Application and Installation Revocation Options

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The Permission Model **MAY** support revocation of all application authority across installations and, where implementation support exists, revocation of one installation without revoking the entire application.

### Rationale

Granular revocation allows a lost or obsolete installation to be removed while preserving other valid installations.

### Source

- REM-04-428
- REM-04-429
- `design-notes/04-application-and-permission-model.md`, Section 34

### Related Invariants

- CI-06

---

## REL-APP-147

### Title

Continuous and Background Access Declaration

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An application requesting continuous or background access **MUST** explicitly declare the applicable access mode.

### Rationale

Persistent user-absent authority must be visible rather than inferred from ordinary interactive consent.

### Source

- REM-04-430
- REM-04-431
- `design-notes/04-application-and-permission-model.md`, Section 35

### Related Invariants

- CI-06

---

## REL-APP-148

### Title

Background Operation Explanation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The user-facing consent interface **MUST** explain that an application with background authority may act while the user is not actively using it.

### Rationale

The user must understand that authority can be exercised outside an active interaction.

### Source

- REM-04-437
- `design-notes/04-application-and-permission-model.md`, Section 35

### Related Invariants

- CI-06

---

## REL-APP-149

### Title

Narrow Renewable Background Authority

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Background access **SHOULD** use narrowly scoped, renewable authority wherever practical rather than unnecessarily permanent authority.

### Rationale

Narrow renewal limits persistent exposure while preserving legitimate background functions.

### Source

- REM-04-438
- REM-04-439
- `design-notes/04-application-and-permission-model.md`, Section 35

### Related Invariants

- CI-06

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-391` | Direct | `REL-APP-132` |
| `REM-04-392`–`REM-04-395` | Consolidated alternatives | `REL-APP-133` |
| `REM-04-396` | Direct | `REL-APP-134` |
| `REM-04-397` | Decomposed | `REL-APP-135`–`REL-APP-136` |
| `REM-04-398`–`REM-04-399` | Direct | `REL-APP-137`–`REL-APP-138` |
| `REM-04-400`–`REM-04-408` | Non-normative examples | Excluded |
| `REM-04-409`–`REM-04-410` | Direct | `REL-APP-139`–`REL-APP-140` |
| `REM-04-411`–`REM-04-415` | Consolidated prohibitions | `REL-APP-141` |
| `REM-04-416`–`REM-04-417` | Consolidated validation | `REL-APP-142` |
| `REM-04-418`–`REM-04-419` | Direct | `REL-APP-143`–`REL-APP-144` |
| `REM-04-420`–`REM-04-424` | Non-normative installation examples | Excluded |
| `REM-04-425`–`REM-04-427` | Consolidated distinctions | `REL-APP-145` |
| `REM-04-428`–`REM-04-429` | Consolidated revocation options | `REL-APP-146` |
| `REM-04-430`–`REM-04-431` | Consolidated declarations | `REL-APP-147` |
| `REM-04-432`–`REM-04-436` | Non-normative background examples | Excluded |
| `REM-04-437` | Direct | `REL-APP-148` |
| `REM-04-438`–`REM-04-439` | Consolidated recommendation | `REL-APP-149` |

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-131`; this part runs `REL-APP-132`–`REL-APP-149`.
- Total requirements: 18; numbering is continuous and unique.
- Long-running mechanisms retain `MAY`; short-lived preference retains `SHOULD`.
- High-authority fresh authentication is decomposed without losing either recommendation.
- Delegated keys cannot acquire identity, recovery, migration or self-expansion authority.
- Example capabilities, installations and background functions remain non-normative.
- No Section 36 or later content is imported.

---

# 6. Part conclusion

Part 7 establishes renewable long-running access and bounded cryptographic delegation across application installations.

Part 8 should begin with Section 36 and `REM-04-440`.
