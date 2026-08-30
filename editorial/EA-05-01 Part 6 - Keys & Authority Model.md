# EA-05-01 — Identity Requirements Catalogue
## Part 6 — Keys & Authority Model

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing cryptographic keys, delegated authority and key lifecycle within Relay Identity.

It is derived from the approved REM-01 and the Keys & Authority sections of the Identity Model.

---

# 2. Scope

This part covers:

- Signing keys
- Authentication keys
- Recovery authority
- Delegated application keys
- Key lifecycle

---

# 3. Requirements

## REL-ID-054

### Title
Signing Key Purpose

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Signing keys **MUST** be used to authorise protocol records and commits.

### Rationale
Signing authority is distinct from authentication authority.

### Source
REM-01 — IREM-0030

### Related Invariants
- CI-02

---

## REL-ID-055

### Title
Signing Key Rotation

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Rotation of signing keys **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0030

### Related Invariants
- CI-05

---

## REL-ID-056

### Title
Authentication Key Scope

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Authentication keys **MUST** establish authenticated sessions without implicitly granting identity authority.

### Source
REM-01 — IREM-0031

### Related Invariants
- CI-02

---

## REL-ID-057

### Title
Identity Document Authority

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Authentication keys **MUST NOT** by themselves authorise Identity Document changes.

### Source
REM-01 — IREM-0031

### Related Invariants
- CI-02
- CI-08

---

## REL-ID-058

### Title
Recovery Authority Separation

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement
Recovery authority **SHOULD** remain separate from ordinary signing authority.

### Rationale
Independent recovery authority reduces the impact of routine credential compromise.

### Source
REM-01 — IREM-0032

### Related Invariants
- CI-02

---

## REL-ID-059

### Title
Delegated Key Capabilities

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
Delegated application keys **MAY** be granted limited protocol capabilities.

### Source
REM-01 — IREM-0033

### Related Invariants
- CI-02

---

## REL-ID-060

### Title
Delegated Key Restriction

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Delegated application keys **MUST NOT** become general identity authority keys.

### Source
REM-01 — IREM-0033

### Related Invariants
- CI-02

---

## REL-ID-061

### Title
Key Addition

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
The protocol **MUST** support adding new keys to an identity.

### Source
REM-01 — IREM-0034

### Related Invariants
- CI-02

---

## REL-ID-062

### Title
Key Retirement

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
The protocol **MUST** support retiring existing keys.

### Source
REM-01 — IREM-0035

### Related Invariants
- CI-02

---

## REL-ID-063

### Title
Key Revocation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
The protocol **MUST** support revocation of compromised keys.

### Source
REM-01 — IREM-0036

### Related Invariants
- CI-02

---

## REL-ID-064

### Title
Key Validity Metadata

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
The protocol **MUST** record sufficient validity metadata for each key to support later verification.

### Source
REM-01 — IREM-0037

### Related Invariants
- CI-08

---

## REL-ID-065

### Title
Historical Signature Validation

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Historical signatures **MUST** be validated against the key state that existed when the signatures were created.

### Rationale
Historical verification must remain reliable after subsequent key changes.

### Source
REM-01 — IREM-0038

### Related Invariants
- CI-08

---

# Editorial Review Notes

This part establishes the separation of signing authority, authentication authority, recovery authority and delegated authority. It also defines the lifecycle requirements for keys, ensuring that key evolution preserves identity continuity and supports long-term verification.
