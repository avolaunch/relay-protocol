# EA-05-04 — Application and Permission Requirements Catalogue

## Part 9 — Revocation Effects, Grant Narrowing and Re-Authorisation

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the future effects of revocation, application-independent record continuity, partial grant narrowing and re-authorisation after material change.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 41–45 and `REM-04-495` through `REM-04-538`.

`REM-04-508`–`REM-04-511` and `REM-04-515` are verified non-normative examples and generate no requirements.

Section 46 and later are deferred.

---

# 3. Requirements

---

## REL-APP-172

### Title

No New Tokens After Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

After a Permission Grant is revoked, the authorisation system **MUST NOT** issue a new Access Token under that grant.

### Rationale

Revoked authority cannot support new credentials.

### Source

- REM-04-495
- `design-notes/04-application-and-permission-model.md`, Section 41

### Related Invariants

- CI-06

---

## REL-APP-173

### Title

Operational Revocation Effects

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

After revocation, refresh authority and delegated keys **MUST** become invalid, background subscriptions and event delivery **MUST** cease, repositories **MUST** reject new submissions under the grant, and retained data **MUST** be handled according to the approved retention declaration.

### Rationale

Revocation must terminate every future exercise path while preserving approved data-handling obligations.

### Source

- REM-04-496
- REM-04-497
- REM-04-498
- REM-04-499
- REM-04-500
- REM-04-501
- `design-notes/04-application-and-permission-model.md`, Section 41

### Related Invariants

- CI-06
- AI-05

---

## REL-APP-174

### Title

No Automatic Erasure from Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Revocation **MUST NOT** automatically erase canonical records, lawfully disclosed copies or audit history, and **MUST NOT** be represented as overriding another party's lawful retention obligation.

### Rationale

Revocation terminates future authority but does not rewrite valid history or external legal duties.

### Source

- REM-04-502
- REM-04-503
- REM-04-504
- REM-04-505
- `design-notes/04-application-and-permission-model.md`, Section 41

### Related Invariants

- CI-10
- AI-07

---

## REL-APP-175

### Title

Prospective Effect of Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Revocation **MUST** terminate future authority under the affected grant without retroactively invalidating actions that were validly authorised before revocation.

### Rationale

The protocol separates future authority from the validity of completed authorised operations.

### Source

- REM-04-506
- `design-notes/04-application-and-permission-model.md`, Section 41

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-176

### Title

No Record Deletion Solely from Application Revocation

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Revoking an application **MUST NOT** delete a record solely because that application created or submitted it.

### Rationale

Canonical records belong to repository continuity rather than application availability.

### Source

- REM-04-507
- `design-notes/04-application-and-permission-model.md`, Section 42

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-177

### Title

Separate User-Directed Record Deletion

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The user **MAY** separately authorise deletion of records previously created through a revoked application.

### Rationale

Application revocation and record deletion remain distinct decisions.

### Source

- REM-04-512
- `design-notes/04-application-and-permission-model.md`, Section 42

### Related Invariants

- CI-02
- AI-07

---

## REL-APP-178

### Title

Application-Independent Record Continuity

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Permission and Record Models **MUST** preserve canonical records independently of the continued availability or authorisation of the application that created them.

### Rationale

Application replacement requires repository state to survive the originating client.

### Source

- REM-04-513
- `design-notes/04-application-and-permission-model.md`, Section 42

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-179

### Title

Partial Grant Narrowing

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A user **MUST** be able to narrow a Permission Grant without revoking it in full.

### Rationale

The user can remove excessive authority while preserving unrelated approved access.

### Source

- REM-04-514
- `design-notes/04-application-and-permission-model.md`, Section 43

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-180

### Title

Safe Grant-Narrowing Lifecycle

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A narrowed grant **SHOULD** supersede the previous grant, invalidate removed tokens, capabilities and delegated keys, preserve an audit trail of the change, and avoid unnecessary full reconnection where remaining authority can safely continue.

### Rationale

These lifecycle steps make narrowing effective, traceable and minimally disruptive.

### Source

- REM-04-516
- REM-04-517
- REM-04-518
- REM-04-519
- `design-notes/04-application-and-permission-model.md`, Section 43

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-181

### Title

Revised Grant Defines Maximum Authority

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

After narrowing, the revised Permission Grant **MUST** define the application's maximum current authority.

### Rationale

Superseded or removed authority cannot remain exercisable beside the revised grant.

### Source

- REM-04-520
- `design-notes/04-application-and-permission-model.md`, Section 43

### Related Invariants

- CI-06

---

## REL-APP-182

### Title

Re-Authorisation Triggers

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

An application **MUST** request re-authorisation after grant expiration, before broader scopes, after controller change, before relying on materially changed retention or AI use, before new onward sharing, after a materially different manifest, or after a security event invalidates existing authority.

### Rationale

Each trigger changes or removes the basis on which the existing approval was granted.

### Source

- REM-04-521
- REM-04-522
- REM-04-523
- REM-04-524
- REM-04-525
- REM-04-526
- REM-04-527
- REM-04-528
- `design-notes/04-application-and-permission-model.md`, Section 44

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-183

### Title

No Silent Reliance on Old Approval

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** rely silently on an earlier approval to justify materially new behaviour.

### Rationale

Existing consent cannot be reinterpreted to cover an undisclosed material change.

### Source

- REM-04-529
- `design-notes/04-application-and-permission-model.md`, Section 44

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-184

### Title

Re-Authorisation Before Changed Behaviour

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Where re-authorisation is required, the application **MUST** obtain the new Permission Grant before performing the materially changed behaviour.

### Rationale

Review must precede exercise of the changed authority.

### Source

- REM-04-530
- `design-notes/04-application-and-permission-model.md`, Section 44

### Related Invariants

- CI-06

---

## REL-APP-185

### Title

Manifest-Version Comparison

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Relay Provider **SHOULD** compare the manifest version approved by the user with the application's current valid manifest.

### Rationale

Comparison detects drift from the declarations on which consent was based.

### Source

- REM-04-531
- `design-notes/04-application-and-permission-model.md`, Section 45

### Related Invariants

- CI-10

---

## REL-APP-186

### Title

Provider Responses to Material Manifest Drift

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Where material manifest drift is detected, a Relay Provider **MAY** pause access, restrict the application to previously approved behaviour, require user review, or revoke the affected grant where severe risk warrants it.

### Rationale

The source permits proportionate responses rather than mandating one response for every change.

### Source

- REM-04-532
- REM-04-533
- REM-04-534
- REM-04-535
- `design-notes/04-application-and-permission-model.md`, Section 45

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-187

### Title

No Mandatory Re-Authorisation for Non-Material Change

**Level:** Behavioural

**Normative Keyword:** **NEED NOT**

### Statement

A minor, non-material Application Manifest change **NEED NOT** trigger a full re-authorisation flow.

### Rationale

This avoids unnecessary consent repetition where the approved behaviour and risk have not materially changed.

### Source

- REM-04-536
- `design-notes/04-application-and-permission-model.md`, Section 45

### Related Invariants

- CI-06

---

## REL-APP-188

### Title

Defined Manifest-Change Materiality

**Level:** Governance

**Normative Keyword:** **SHOULD**

### Statement

The Relay protocol **SHOULD** define which Application Manifest changes are material for re-authorisation and provider enforcement.

### Rationale

Shared materiality rules improve consistent treatment across providers.

### Source

- REM-04-537
- `design-notes/04-application-and-permission-model.md`, Section 45

### Related Invariants

- CI-12

---

## REL-APP-189

### Title

Proportionate Manifest-Drift Response

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A provider's response to manifest drift **SHOULD** be proportionate to the materiality and risk of the detected change.

### Rationale

Minor and severe changes should not automatically receive identical treatment.

### Source

- REM-04-538
- `design-notes/04-application-and-permission-model.md`, Section 45

### Related Invariants

- CI-11

---

# 4. REM coverage, consolidation and exclusions

| REM range | Treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-495` | Direct | `REL-APP-172` |
| `REM-04-496`–`REM-04-501` | Consolidated revocation effects | `REL-APP-173` |
| `REM-04-502`–`REM-04-505` | Consolidated non-erasure rules | `REL-APP-174` |
| `REM-04-506`–`REM-04-507` | Direct | `REL-APP-175`–`REL-APP-176` |
| `REM-04-508`–`REM-04-511` | Non-normative examples | Excluded |
| `REM-04-512`–`REM-04-514` | Direct | `REL-APP-177`–`REL-APP-179` |
| `REM-04-515` | Non-normative example | Excluded |
| `REM-04-516`–`REM-04-519` | Consolidated narrowing lifecycle | `REL-APP-180` |
| `REM-04-520` | Direct | `REL-APP-181` |
| `REM-04-521`–`REM-04-528` | Consolidated triggers | `REL-APP-182` |
| `REM-04-529`–`REM-04-531` | Direct | `REL-APP-183`–`REL-APP-185` |
| `REM-04-532`–`REM-04-535` | Consolidated provider options | `REL-APP-186` |
| `REM-04-536`–`REM-04-538` | Direct | `REL-APP-187`–`REL-APP-189` |

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-171`; this part runs `REL-APP-172`–`REL-APP-189`.
- Total requirements: 18; numbering is continuous.
- Revocation terminates future authority without erasing valid history.
- Record continuity remains independent of application authorisation.
- Grant narrowing does not require full revocation.
- Material-change triggers and prior-approval limits retain `MUST` or `MUST NOT`.
- Non-material changes retain `NEED NOT`.
- No Section 46 or later content is imported.

---

# 6. Part conclusion

Part 9 defines prospective revocation, record continuity, grant narrowing and re-authorisation.

Part 10 should begin with Section 46 and `REM-04-539`.
