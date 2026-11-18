# EA-05-04 — Application and Permission Requirements Catalogue

## Part 11 — Application Security, Portability, Replacement and Provider Authority

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines damage limitation for malicious applications, application infrastructure portability and replacement, grant continuity during provider migration, and provider operational authority.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers Sections 51–55 and `REM-04-596` through `REM-04-647`. No later material is imported.

---

# 3. Requirements

---

## REL-APP-209

### Title

No Claim of Eliminating Malicious Software

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Relay implementations and documentation **MUST NOT** represent the protocol as capable of eliminating malicious or deceptive software.

### Rationale

The model limits damage and improves accountability but cannot guarantee benign software.

### Source

- REM-04-596
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-08

---

## REL-APP-210

### Title

Mandatory Application Damage-Limitation Controls

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** use narrow grants, signed manifests, verified callback locations, explicit purpose declarations where required, prompt future-effective revocation and separation of high-authority operations from ordinary permissions.

### Rationale

These controls reduce the authority and opportunity available to malicious, deceptive or compromised applications.

### Source

- REM-04-597
- REM-04-598
- REM-04-599
- REM-04-600
- REM-04-603
- REM-04-604
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-211

### Title

Recommended Damage-Limitation Controls

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Implementations **SHOULD** use short-lived Access Tokens and auditable material permission activity.

### Rationale

Short credential lifetimes and auditability reduce exposure and improve detection.

### Source

- REM-04-601
- REM-04-602
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-212

### Title

Application Reputation and Verification Inputs

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Providers and ecosystem services **MAY** use application reputation and verification layers as additional decision inputs before granting or continuing access.

### Rationale

Trust signals can inform decisions without becoming authority themselves.

### Source

- REM-04-605
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-08
- CI-11

---

## REL-APP-213

### Title

Pre-Approval Trust Policies

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Providers and users **MAY** apply trust policies before approving a Permission Request.

### Rationale

Trust policy can filter or require review before consent.

### Source

- REM-04-606
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-11

---

## REL-APP-214

### Title

Trust Policy Does Not Expand Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A favourable trust-policy result **MUST NOT** create or expand application authority beyond the explicit Permission Grant.

### Rationale

Trust and authority remain separate.

### Source

- REM-04-607
- `design-notes/04-application-and-permission-model.md`, Section 51

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-215

### Title

Application Infrastructure Portability

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** change hosting provider or infrastructure while retaining the same Application Identity.

### Rationale

Stable application identity need not change solely because infrastructure changes.

### Source

- REM-04-608
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-05

---

## REL-APP-216

### Title

Authorised Manifest Update for Infrastructure Change

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An infrastructure change affecting manifest information **MUST** be represented through an authorised Application Manifest update.

### Rationale

Current operational information must remain authoritative and traceable.

### Source

- REM-04-609
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-08
- CI-10

---

## REL-APP-217

### Title

Controller Continuity Across Infrastructure Change

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Retention of an Application Identity across an infrastructure move **MUST** require verifiable continuity of controller authority.

### Rationale

Infrastructure portability cannot enable an unauthorised takeover.

### Source

- REM-04-610
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-02
- CI-05

---

## REL-APP-218

### Title

Updated Infrastructure Manifest Information

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

After an infrastructure move, the current Application Manifest **MUST** identify changed service locations and any new authorised keys or callback locations.

### Rationale

Providers must resolve the current authorised endpoints and credentials.

### Source

- REM-04-611
- REM-04-612
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-08

---

## REL-APP-219

### Title

No Permission Expansion Through Infrastructure Move

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application infrastructure move **MUST NOT** silently expand existing grant scope, purpose, duration or other authority.

### Rationale

Portability changes location, not approved authority.

### Source

- REM-04-613
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-06

---

## REL-APP-220

### Title

No New Identity Solely for Server Movement

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

Users **SHOULD NOT** be required to approve an entirely new Application Identity solely because an application moved servers or hosting infrastructure.

### Rationale

Legitimate infrastructure portability should preserve application continuity.

### Source

- REM-04-614
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-05

---

## REL-APP-221

### Title

No Bypass of Material-Change Review

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Application portability **MUST NOT** bypass re-authorisation or review required by material changes to controller, data practices, purposes or requested authority.

### Rationale

Infrastructure movement cannot conceal a substantive application change.

### Source

- REM-04-615
- `design-notes/04-application-and-permission-model.md`, Section 52

### Related Invariants

- CI-06
- CI-10

---

## REL-APP-222

### Title

Application Replacement Support

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

The Application and Permission Model **MUST** allow a person to stop using one application and begin using another.

### Rationale

Application choice must not be locked to the original client.

### Source

- REM-04-616
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-04

---

## REL-APP-223

### Title

Replacement Application Authority

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A replacement application **MAY** receive permission to read the same profile and posts, update existing records and interact with the same relationships, subject to ordinary scope, schema and authority rules.

### Rationale

Portable state can be used by another authorised application without inheriting the prior application's grant.

### Source

- REM-04-617
- REM-04-618
- REM-04-619
- REM-04-620
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-04
- CI-06

---

## REL-APP-224

### Title

No Repository-State Recreation for Application Replacement

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Replacing an application **MUST NOT** require recreation of portable underlying repository state.

### Rationale

Existing canonical state survives client replacement.

### Source

- REM-04-621
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-04
- AI-01

---

## REL-APP-225

### Title

Unsupported Application-Specific Records

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A replacement application **MAY** decline to interpret or render application-specific record types it does not support.

### Rationale

Application replacement does not require universal schema understanding.

### Source

- REM-04-622
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-09

---

## REL-APP-226

### Title

Preservation of Unsupported Records

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Valid application-specific records **MUST** be preserved even where the replacement application does not support their schema or presentation.

### Rationale

Lack of interpretation does not justify loss of valid state.

### Source

- REM-04-623
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-09

---

## REL-APP-227

### Title

Replacement Application Requires Its Own Grant

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A replacement application **MUST** receive its own explicit Permission Grant.

### Rationale

Authority is application-specific even when repository state is portable.

### Source

- REM-04-624
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-04
- CI-06

---

## REL-APP-228

### Title

No Automatic Grant Inheritance Between Applications

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A replacement application **MUST NOT** automatically inherit the previous application's Permission Grant.

### Rationale

Application replacement does not transfer delegated authority.

### Source

- REM-04-624
- `design-notes/04-application-and-permission-model.md`, Section 53

### Related Invariants

- CI-04
- CI-06

---

## REL-APP-229

### Title

Conditional Grant Continuity After Provider Migration

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An existing Permission Grant **MAY** continue after provider migration only when every applicable continuation condition is satisfied.

### Rationale

Migration continuity is conditional rather than automatic.

### Source

- REM-04-625
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-230

### Title

Provider-Independent Continuing Grant

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Permission Grant **MUST** be provider-independent to remain valid across provider migration.

### Rationale

Provider-bound authority cannot automatically survive a provider change.

### Source

- REM-04-626
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-231

### Title

New-Provider Capability Condition

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A grant **MAY** continue after migration only where the new provider supports its required capabilities.

### Rationale

A provider cannot safely honour unsupported authority semantics.

### Source

- REM-04-627
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03

---

## REL-APP-232

### Title

Secure Discovery of New Provider

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Before exercising a continuing grant, the application **MUST** securely discover and verify the new authoritative provider.

### Rationale

The application must not redirect authority to an unverified service.

### Source

- REM-04-628
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-08

---

## REL-APP-233

### Title

No Revival of Revoked Grant Through Migration

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A revoked grant **MUST NOT** regain validity because the repository migrated.

### Rationale

Migration cannot undo revocation.

### Source

- REM-04-629
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-06

---

## REL-APP-234

### Title

Migration-Policy Continuation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A grant **MAY** continue after migration only where applicable migration policy permits continuation.

### Rationale

Migration policy can impose additional safety conditions.

### Source

- REM-04-630
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03

---

## REL-APP-235

### Title

No Direct Copying of Provider-Specific Tokens

**Level:** Architectural

**Normative Keyword:** **SHOULD NOT**

### Statement

Provider-specific tokens **SHOULD NOT** be copied directly to the new provider as the mechanism for continuing access.

### Rationale

Provider-bound tokens should be replaced rather than reused outside their audience.

### Source

- REM-04-631
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-08

---

## REL-APP-236

### Title

New Tokens from Continuing Grant

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The new provider **MAY** issue new Access Tokens based on a continuing valid Permission Grant.

### Rationale

New credentials can reflect the new provider audience while preserving valid authority.

### Source

- REM-04-632
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-237

### Title

Migration Re-Authorisation for High-Risk Grants

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

Migration policy **MAY** require high-risk grants to be re-authorised after migration.

### Rationale

Higher-risk authority may warrant renewed consent despite otherwise valid continuity.

### Source

- REM-04-633
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-238

### Title

Preservation of Continuing Grant Constraints

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A grant continued after migration **MUST** retain its approved scope, purpose, duration, restrictions and revocation status unless the user explicitly authorises a change.

### Rationale

Migration cannot silently broaden or reset authority.

### Source

- REM-04-634
- `design-notes/04-application-and-permission-model.md`, Section 54

### Related Invariants

- CI-03
- CI-06

---

## REL-APP-239

### Title

Explicit Provider Operational Access

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A Relay Provider's access to a hosted repository **MUST** be explicitly defined.

### Rationale

Hosting does not itself justify undefined access.

### Source

- REM-04-635
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-11

---

## REL-APP-240

### Title

Permitted Provider Hosting Operations

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A hosting agreement and protocol role **MAY** authorise a provider to store and serve records, validate commits, deliver authorised events, create backups, scan for malware within its documented role, and enforce applicable legal restrictions.

### Rationale

The source permits defined operational authority without converting it into application authority.

### Source

- REM-04-636
- REM-04-637
- REM-04-638
- REM-04-639
- REM-04-640
- REM-04-641
- REM-04-642
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-11

---

## REL-APP-241

### Title

Hosting Access Is Not an Unrestricted Application Grant

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A Relay Provider **MUST NOT** treat repository-hosting access as an unrestricted application Permission Grant.

### Rationale

Provider operations and optional application access have different authority bases.

### Source

- REM-04-643
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-11

---

## REL-APP-242

### Title

Separate Provider Operational Documentation

**Level:** Governance

**Normative Keyword:** **SHOULD**

### Statement

Provider operational authority **SHOULD** be documented separately from application Permission Grants.

### Rationale

Separate documentation makes the provider's hosting role and user-facing applications distinguishable.

### Source

- REM-04-644
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-11

---

## REL-APP-243

### Title

Provider Operational Authority Boundaries

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Relay Provider's operational authority **MUST** remain limited to its hosting agreement and defined protocol role.

### Rationale

Provider access cannot expand beyond the documented operational basis.

### Source

- REM-04-645
- REM-04-646
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-11

---

## REL-APP-244

### Title

Separate Authority for Provider Applications

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

An optional user-facing application operated by a provider **MUST** use its own Application Identity and applicable Permission Grant rather than the provider's hosting authority.

### Rationale

First-party applications remain applications and cannot evade the Permission Model.

### Source

- REM-04-647
- `design-notes/04-application-and-permission-model.md`, Section 55

### Related Invariants

- CI-04
- CI-11

---

# 4. REM coverage and consolidation

All entries `REM-04-596` through `REM-04-647` are represented directly, through source-compatible consolidation, or through decomposition of `REM-04-624` into separate own-grant and non-inheritance obligations.

Key consolidations preserve:

- mandatory and recommended damage-limitation controls;
- application infrastructure continuity and manifest updates;
- replacement-application access categories;
- every provider-migration continuation condition; and
- the provider's permitted operational functions and mandatory authority boundaries.

---

# 5. Editorial QA record

- Previous endpoint: `REL-APP-208`.
- First identifier: `REL-APP-209`.
- Final identifier: `REL-APP-244`.
- Total requirements: 36; numbering is continuous.
- Protocol damage limitation is not represented as eliminating malicious software.
- Application replacement preserves records but never transfers grants automatically.
- Provider migration preserves grant restrictions and revocation status.
- Hosting authority remains distinct from application authority.
- No Section 56 or later content is imported.

---

# 6. Part conclusion

Part 11 establishes secure application continuity and strict separation between provider operations and application permissions.

Part 12 should begin with Section 56 and `REM-04-648`.
