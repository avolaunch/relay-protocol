# EA-05-04 — Application and Permission Requirements Catalogue

## Part 6 — Consent, Partial Approval, Authorisation Sessions and Access Tokens

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Application and Permission  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines consent presentation, partial approval, Consent Receipts, secure Authorisation Sessions and bounded Access Token semantics.

The authoritative design source remains `design-notes/04-application-and-permission-model.md`.

---

# 2. Scope

This part covers source Sections 26–30 and REM-04 entries `REM-04-323` through `REM-04-390`.

`REM-04-338` and `REM-04-339` are verified non-normative consent examples and generate no catalogue requirements. Their wording does not become a mandatory consent template.

Section 31 and later are deferred.

---

# 3. Requirements

---

## REL-APP-111

### Title

Consent Presentation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A Relay Provider or trusted authorisation service **SHOULD** present each Permission Request to the affected user before approval.

### Rationale

Presentation enables review before a grant is issued.

### Source

- REM-04-323
- `design-notes/04-application-and-permission-model.md`, Section 26

### Related Invariants

- CI-06

---

## REL-APP-112

### Title

Required Consent Disclosures

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

The consent interface **MUST** display the application's visible name, controller and verification status, and explain requested data, actions, duration, purpose, retention, AI processing, onward sharing, high-risk capabilities and material changes from previous requests or approvals.

### Rationale

These disclosures expose the actor, authority and consequences before consent.

### Source

- REM-04-324
- REM-04-325
- REM-04-326
- REM-04-327
- REM-04-328
- REM-04-329
- REM-04-330
- REM-04-331
- REM-04-332
- REM-04-333
- REM-04-334
- REM-04-335
- `design-notes/04-application-and-permission-model.md`, Section 26

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-113

### Title

No Sole Reliance on Vague Legalistic Descriptions

**Level:** Behavioural

**Normative Keyword:** **SHOULD NOT**

### Statement

The consent interface **SHOULD NOT** rely solely on vague or legalistic phrases that fail to describe the practical effect of a request.

### Rationale

Formal wording alone may conceal the actual consequences.

### Source

- REM-04-336
- `design-notes/04-application-and-permission-model.md`, Section 26

### Related Invariants

- CI-06

---

## REL-APP-114

### Title

Concrete Consequence Explanation

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

The consent interface **SHOULD** explain the concrete consequences of approval in ordinary language.

### Rationale

Concrete explanations support informed approval without making example wording mandatory.

### Source

- REM-04-337
- `design-notes/04-application-and-permission-model.md`, Section 26

### Related Invariants

- CI-06

---

## REL-APP-115

### Title

Granular Partial Approval

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

Where practical, the authorisation system **SHOULD** allow distinct scopes or capabilities to be approved or denied independently.

### Rationale

Granularity reduces unnecessary authority while preserving the source qualification.

### Source

- REM-04-340
- REM-04-341
- `design-notes/04-application-and-permission-model.md`, Section 27

### Related Invariants

- CI-06

---

## REL-APP-116

### Title

Application Response to Reduced Approval

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An application **MAY** operate with the approved subset, explain unavailable features, or decline to continue where a genuinely essential permission was refused.

### Rationale

The application may adapt without receiving denied authority.

### Source

- REM-04-342
- REM-04-343
- REM-04-344
- `design-notes/04-application-and-permission-model.md`, Section 27

### Related Invariants

- CI-06

---

## REL-APP-117

### Title

No False Essentiality Claims

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An application **MUST NOT** describe optional access as essential to pressure the user into granting it.

### Rationale

False essentiality undermines voluntary consent.

### Source

- REM-04-345
- `design-notes/04-application-and-permission-model.md`, Section 27

### Related Invariants

- CI-06
- CI-11

---

## REL-APP-118

### Title

Grant Limited to Approved Subset

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A Permission Grant following partial approval **MUST** contain only the approved scopes and capabilities.

### Rationale

Partial approval must produce correspondingly limited authority.

### Source

- REM-04-346
- `design-notes/04-application-and-permission-model.md`, Section 27

### Related Invariants

- CI-06

---

## REL-APP-119

### Title

Consent Receipt Issuance

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

After approval, the user **SHOULD** receive a Consent Receipt.

### Rationale

The receipt provides durable evidence of consent.

### Source

- REM-04-347
- `design-notes/04-application-and-permission-model.md`, Section 28

### Related Invariants

- CI-10

---

## REL-APP-120

### Title

Consent Receipt Contents

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

A Consent Receipt **SHOULD** identify the application, manifest version and resulting grant; record approved and denied scopes, purpose, retention and AI declarations, issue time and expiration; preserve the user-facing explanation; and permit reconstruction of the approved authority, purposes and conditions.

### Rationale

The receipt must show what was requested, denied, approved and explained.

### Source

- REM-04-348
- REM-04-349
- REM-04-350
- REM-04-351
- REM-04-352
- REM-04-353
- REM-04-354
- REM-04-355
- REM-04-356
- REM-04-357
- REM-04-358
- REM-04-359
- `design-notes/04-application-and-permission-model.md`, Section 28

### Related Invariants

- CI-10

---

## REL-APP-121

### Title

Consent Receipt Storage

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Consent Receipt **MAY** be stored privately in the user's Relay Repository or by the trusted authorisation service.

### Rationale

The source permits either storage boundary.

### Source

- REM-04-360
- REM-04-361
- `design-notes/04-application-and-permission-model.md`, Section 28

### Related Invariants

- CI-10

---

## REL-APP-122

### Title

Temporary Authorisation Session

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An Authorisation Session **MUST** be a temporary interaction for reviewing and approving a specific Permission Request.

### Rationale

The session is bounded to an authorisation decision.

### Source

- REM-04-362
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-06

---

## REL-APP-123

### Title

Authorisation-Session Attack Protections

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An Authorisation Session **SHOULD** protect against callback substitution, replay, request tampering, cross-site request forgery, session fixation and malicious redirects.

### Rationale

These protections address distinct flow-hijacking risks.

### Source

- REM-04-363
- REM-04-364
- REM-04-365
- REM-04-366
- REM-04-367
- REM-04-368
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-124

### Title

Current Secure-Authorisation Practices

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Implementations **SHOULD** follow current secure-authorisation practices appropriate to the application and threat model.

### Rationale

Security must remain suitable for current threats.

### Source

- REM-04-369
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-08

---

## REL-APP-125

### Title

Authorisation-Flow Validation Controls

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Authorisation flows **SHOULD** use exact callback matching, short-lived codes, an appropriate proof-key mechanism where applicable, state validation, and nonce validation where the selected mechanism uses nonces.

### Rationale

These controls bind the response to the correct client and session.

### Source

- REM-04-370
- REM-04-371
- REM-04-372
- REM-04-373
- REM-04-374
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-08

---

## REL-APP-126

### Title

Secure Authorisation Transport

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Authorisation Sessions **MUST** use secure transport appropriate to protect requests, credentials and responses in transit.

### Rationale

Transport compromise can invalidate consent and authority.

### Source

- REM-04-375
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-08

---

## REL-APP-127

### Title

Reuse of Established Authorisation Mechanisms

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Relay implementations **MAY** use established low-level authorisation standards and mechanisms rather than defining new ones unnecessarily.

### Rationale

Reuse can reduce protocol-specific security risk.

### Source

- REM-04-376
- `design-notes/04-application-and-permission-model.md`, Section 29

### Related Invariants

- CI-08
- CI-12

---

## REL-APP-128

### Title

Access Token Authority Boundaries

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

An Access Token **MUST** authorise only authority in its approved Permission Grant, remain grant-limited, have bounded validity, be audience-bound, resist undetected modification, and either support revocation or be sufficiently short-lived.

### Rationale

A token must not broaden, outlive or escape its grant context.

### Source

- REM-04-377
- REM-04-378
- REM-04-379
- REM-04-380
- REM-04-381
- REM-04-382
- `design-notes/04-application-and-permission-model.md`, Section 30

### Related Invariants

- CI-06
- CI-08

---

## REL-APP-129

### Title

Access Token Is Not Identity Ownership

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

An Access Token **MUST NOT** be treated as proof that the application owns or controls the Relay Identity.

### Rationale

A token proves delegated authority, not identity ownership.

### Source

- REM-04-383
- `design-notes/04-application-and-permission-model.md`, Section 30

### Related Invariants

- CI-02
- CI-06

---

## REL-APP-130

### Title

Recommended Access Token References

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

An Access Token **SHOULD** identify or reference the Application Identity, Relay Identity, Permission Grant, approved capabilities, expiration and intended provider or service.

### Rationale

These references permit validation against the authority context.

### Source

- REM-04-384
- REM-04-385
- REM-04-386
- REM-04-387
- REM-04-388
- REM-04-389
- `design-notes/04-application-and-permission-model.md`, Section 30

### Related Invariants

- CI-08
- CI-10

---

## REL-APP-131

### Title

Access Token Validation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

A receiving provider or service **MUST** validate an Access Token against the relevant grant, expiry, audience and revocation conditions before accepting it.

### Rationale

Possession is insufficient where authority is no longer effective.

### Source

- REM-04-390
- `design-notes/04-application-and-permission-model.md`, Section 30

### Related Invariants

- CI-06
- CI-08

---

# 4. REM coverage, consolidation and exclusions

| REM range | Catalogue treatment | Catalogue identifier or reason |
|---|---|---|
| `REM-04-323` | Direct | `REL-APP-111` |
| `REM-04-324`–`REM-04-335` | Consolidated required disclosures | `REL-APP-112` |
| `REM-04-336`–`REM-04-337` | Direct | `REL-APP-113`–`REL-APP-114` |
| `REM-04-338`–`REM-04-339` | Non-normative consent examples | Excluded |
| `REM-04-340`–`REM-04-341` | Consolidated | `REL-APP-115` |
| `REM-04-342`–`REM-04-344` | Consolidated permitted responses | `REL-APP-116` |
| `REM-04-345`–`REM-04-347` | Direct | `REL-APP-117`–`REL-APP-119` |
| `REM-04-348`–`REM-04-359` | Consolidated receipt contents | `REL-APP-120` |
| `REM-04-360`–`REM-04-361` | Consolidated storage alternatives | `REL-APP-121` |
| `REM-04-362` | Direct | `REL-APP-122` |
| `REM-04-363`–`REM-04-368` | Consolidated attack protections | `REL-APP-123` |
| `REM-04-369` | Direct | `REL-APP-124` |
| `REM-04-370`–`REM-04-374` | Consolidated validation controls | `REL-APP-125` |
| `REM-04-375`–`REM-04-376` | Direct | `REL-APP-126`–`REL-APP-127` |
| `REM-04-377`–`REM-04-382` | Consolidated token boundaries | `REL-APP-128` |
| `REM-04-383` | Direct | `REL-APP-129` |
| `REM-04-384`–`REM-04-389` | Consolidated token references | `REL-APP-130` |
| `REM-04-390` | Direct | `REL-APP-131` |

All normative clauses remain explicit within the consolidated requirements.

---

# 5. Editorial QA record

- Source scope is limited to Sections 26–30.
- Previous endpoint: `REL-APP-110`.
- First identifier: `REL-APP-111`.
- Final identifier: `REL-APP-131`.
- Total requirements: 21.
- Partial approval retains its practicality qualification.
- Consent examples generated no normative wording.
- Authorisation security recommendations remain `SHOULD`; secure transport remains `MUST`.
- Tokens remain grant-limited, time-bound, audience-bound and distinct from identity ownership.
- No Section 31 or later material is imported.

---

# 6. Part conclusion

Part 6 establishes meaningful consent, granular approval, durable consent evidence, secure authorisation flows and bounded token exercise.

Part 7 should begin with source Section 31 and `REM-04-391`.
