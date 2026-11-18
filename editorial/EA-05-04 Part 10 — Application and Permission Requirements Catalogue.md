# EA-05-04 — Application and Permission Requirements Catalogue

## Part 10 — Auditability, Attribution, Suspension and Key Compromise

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines authorisation audit events, user-visible activity history, application submission attribution, suspension and application-key-compromise handling.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 46–50 and `REM-04-539` through `REM-04-595`.

`REM-04-570`–`REM-04-573` are verified non-normative attribution fields. They generate no catalogue requirements and select no physical attribution schema.

Section 51 and later are deferred.

---

# 3. Requirements

---

## REL-APP-190

### Title

Structured Authorisation Audit Events

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The authorisation system **SHOULD** produce structured audit events for material permission, token, application and security actions.

### Rationale

Structured events support accountability and later inspection.

### Source

- REM-04-539
- `design-notes/04-application-and-permission-model.md`, Section 46

### Related Invariants

- CI-10

---

## REL-APP-191

### Title

Audited Authorisation Events

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The authorisation system **SHOULD** record audit events for permission requests, grants and denials; token issuance; high-authority actions; grant narrowing, renewal and revocation; manifest changes; reported application security incidents; and rejected unauthorised attempts.

### Rationale

These lifecycle and security events create a traceable history of delegated authority.

### Source

- REM-04-540
- REM-04-541
- REM-04-542
- REM-04-543
- REM-04-544
- REM-04-545
- REM-04-546
- REM-04-547
- REM-04-548
- REM-04-549
- REM-04-550
- `design-notes/04-application-and-permission-model.md`, Section 46

### Related Invariants

- CI-10

---

## REL-APP-192

### Title

Audit Event Attribution

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Each audit event **SHOULD** identify its time, associated Application Identity, applicable Permission Grant, affected resource, attempted or performed action, result, and relevant installation where available.

### Rationale

Attribution makes the event useful for investigation without requiring every field where it is inapplicable or unavailable.

### Source

- REM-04-551
- REM-04-552
- REM-04-553
- REM-04-554
- REM-04-555
- REM-04-556
- REM-04-557
- `design-notes/04-application-and-permission-model.md`, Section 46

### Related Invariants

- CI-10

---

## REL-APP-193

### Title

Private Sensitive Audit Information

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Sensitive audit information **MAY** be restricted from public disclosure and retained in a private audit context.

### Rationale

Auditability does not require exposure of private or security-sensitive evidence.

### Source

- REM-04-558
- `design-notes/04-application-and-permission-model.md`, Section 46

### Related Invariants

- CI-10
- CI-11

---

## REL-APP-194

### Title

User-Inspectable Application Activity

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A person **SHOULD** be able to inspect connected and revoked applications, current grants, recently used permissions, last access times, records created or changed, exports, active installations and background subscriptions.

### Rationale

The user needs a coherent view of current and historical application authority and activity.

### Source

- REM-04-559
- REM-04-560
- REM-04-561
- REM-04-562
- REM-04-563
- REM-04-564
- REM-04-565
- REM-04-566
- REM-04-567
- `design-notes/04-application-and-permission-model.md`, Section 47

### Related Invariants

- CI-02
- CI-10

---

## REL-APP-195

### Title

Human-Readable Activity History

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The access-history interface **SHOULD** present activity in meaningful human-readable terms rather than only token, grant or internal identifier values.

### Rationale

Users must be able to understand activity without interpreting implementation identifiers.

### Source

- REM-04-568
- `design-notes/04-application-and-permission-model.md`, Section 47

### Related Invariants

- CI-10

---

## REL-APP-196

### Title

Application Activity Attribution

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Repository changes made through an application **SHOULD** retain attribution identifying how the operation entered the repository.

### Rationale

Submission-path attribution supports accountability while remaining distinct from authorship.

### Source

- REM-04-569
- `design-notes/04-application-and-permission-model.md`, Section 48

### Related Invariants

- CI-10

---

## REL-APP-197

### Title

Attribution Does Not Establish Application Authorship

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Application activity attribution **MUST NOT** be interpreted as establishing the application as author of the affected record.

### Rationale

The authorising identity and submitting application have different roles.

### Source

- REM-04-574
- `design-notes/04-application-and-permission-model.md`, Section 48

### Related Invariants

- CI-02
- AI-07

---

## REL-APP-198

### Title

Attribution Does Not Establish Application Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Application activity attribution **MUST NOT** give the application ownership or control of the affected record.

### Rationale

Operational participation does not transfer repository authority.

### Source

- REM-04-575
- `design-notes/04-application-and-permission-model.md`, Section 48

### Related Invariants

- CI-02
- CI-04

---

## REL-APP-199

### Title

Attribution Represents Repository Entry Path

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Application activity attribution **MUST** represent the submission path by which the operation entered the repository.

### Rationale

The attribution records operational provenance rather than authorship or ownership.

### Source

- REM-04-576
- `design-notes/04-application-and-permission-model.md`, Section 48

### Related Invariants

- CI-10

---

## REL-APP-200

### Title

Application Suspension

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A Relay Provider or recognised ecosystem authority **MAY** mark an application as suspended.

### Rationale

Suspension permits ecosystem protection without deleting the application's identity or user records.

### Source

- REM-04-577
- `design-notes/04-application-and-permission-model.md`, Section 49

### Related Invariants

- CI-11

---

## REL-APP-201

### Title

Application Suspension Grounds

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** be suspended for compromised keys, malware, fraud, manifest deception, repeated permission abuse, an authorised controller request or an applicable legal restriction.

### Rationale

The source permits these grounds without requiring suspension in every case.

### Source

- REM-04-578
- REM-04-579
- REM-04-580
- REM-04-581
- REM-04-582
- REM-04-583
- REM-04-584
- `design-notes/04-application-and-permission-model.md`, Section 49

### Related Invariants

- CI-11

---

## REL-APP-202

### Title

Application Suspension Effects

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Application suspension **MAY** prevent new grants, token or refresh renewal, repository submissions, event delivery and background subscriptions.

### Rationale

Suspension may terminate future interaction paths proportionately to the risk.

### Source

- REM-04-585
- REM-04-586
- REM-04-587
- REM-04-588
- `design-notes/04-application-and-permission-model.md`, Section 49

### Related Invariants

- CI-06
- AI-05

---

## REL-APP-203

### Title

Suspension Does Not Delete User Records

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Suspending an application **MUST NOT** delete records under user repository authority merely because the application created, submitted or accessed them.

### Rationale

Application enforcement remains separate from user-controlled canonical state.

### Source

- REM-04-589
- `design-notes/04-application-and-permission-model.md`, Section 49

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-204

### Title

Manifest Update After Key Compromise

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

After application-key compromise, the controller **SHOULD** publish an updated Application Manifest reflecting the changed key state.

### Rationale

The current manifest should allow providers to discover valid replacement key information.

### Source

- REM-04-590
- `design-notes/04-application-and-permission-model.md`, Section 50

### Related Invariants

- CI-08
- CI-10

---

## REL-APP-205

### Title

Compromised-Key Revocation and Rejection

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Compromised application keys **SHOULD** be revoked, and providers **SHOULD** reject new permission requests, token requests and repository operations signed by known compromised keys.

### Rationale

Known compromised credentials must cease to support new authority or operations.

### Source

- REM-04-591
- REM-04-592
- `design-notes/04-application-and-permission-model.md`, Section 50

### Related Invariants

- CI-08

---

## REL-APP-206

### Title

Re-Authorisation After Application-Key Compromise

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Permission Grants affected by application-key compromise **MAY** require user re-authorisation.

### Rationale

The response can depend on whether grant continuity can be established safely.

### Source

- REM-04-593
- `design-notes/04-application-and-permission-model.md`, Section 50

### Related Invariants

- CI-06

---

## REL-APP-207

### Title

User Visibility of Suspicious Activity

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Suspicious activity associated with application-key compromise **SHOULD** be made visible to affected users in a meaningful and safe form.

### Rationale

Users need actionable awareness without unsafe disclosure of sensitive incident details.

### Source

- REM-04-594
- `design-notes/04-application-and-permission-model.md`, Section 50

### Related Invariants

- CI-10
- CI-11

---

## REL-APP-208

### Title

Application-Key Compromise Does Not Establish Root Identity Compromise

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Compromise of an application key **MUST NOT**, by itself, be treated as compromise of the user's root Relay Identity authority.

### Rationale

Application credentials and root identity authority remain cryptographically and constitutionally distinct.

### Source

- REM-04-595
- `design-notes/04-application-and-permission-model.md`, Section 50

### Related Invariants

- CI-02
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM range | Treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-539` | Direct | `REL-APP-190` |
| `REM-04-540`–`REM-04-550` | Consolidated audited event set | `REL-APP-191` |
| `REM-04-551`–`REM-04-557` | Consolidated event attribution | `REL-APP-192` |
| `REM-04-558` | Direct | `REL-APP-193` |
| `REM-04-559`–`REM-04-567` | Consolidated user inspection set | `REL-APP-194` |
| `REM-04-568`–`REM-04-569` | Direct | `REL-APP-195`–`REL-APP-196` |
| `REM-04-570`–`REM-04-573` | Non-normative example fields | Excluded |
| `REM-04-574`–`REM-04-577` | Direct | `REL-APP-197`–`REL-APP-200` |
| `REM-04-578`–`REM-04-584` | Consolidated suspension grounds | `REL-APP-201` |
| `REM-04-585`–`REM-04-588` | Consolidated suspension effects | `REL-APP-202` |
| `REM-04-589`–`REM-04-590` | Direct | `REL-APP-203`–`REL-APP-204` |
| `REM-04-591`–`REM-04-592` | Consolidated compromise response | `REL-APP-205` |
| `REM-04-593`–`REM-04-595` | Direct | `REL-APP-206`–`REL-APP-208` |

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-189`; this part runs `REL-APP-190`–`REL-APP-208`.
- Total requirements: 19; numbering is continuous.
- Sensitive audit data may remain private.
- Attribution remains distinct from authorship and ownership.
- Suspension and key-compromise responses do not erase user records or imply root identity compromise.
- Example attribution fields remain non-normative.
- No Section 51 or later content is imported.

---

# 6. Part conclusion

Part 10 establishes accountable authorisation history, submission-path attribution and proportionate application-security responses.

Part 11 should begin with Section 51 and `REM-04-596`.
