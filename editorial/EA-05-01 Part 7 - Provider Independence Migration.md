# EA-05-01 — Identity Requirements Catalogue
## Part 7 — Provider Independence & Migration

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing provider independence, service locations and migration of Relay Identities.

It is derived from the approved REM-01 and the Provider Independence & Migration sections of the Identity Model.

---

# 2. Scope

This part covers:

- Service locations
- Provider independence
- Provider migration
- Multi-provider architectures
- Identity creation and hosting neutrality

---

# 3. Requirements

## REL-ID-066

### Title
Replaceable Service Locations

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Service locations **MUST** be replaceable without altering the associated Relay Identity.

### Rationale
Operational hosting must remain independent from constitutional identity.

### Source
REM-01 — IREM-0039

### Related Invariants
- CI-03
- CI-05

---

## REL-ID-067

### Title
Service Location Changes

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Changing a service location **MUST NOT** alter the associated Relay Identifier.

### Source
REM-01 — IREM-0039

### Related Invariants
- CI-03
- CI-05

---

## REL-ID-068

### Title
Migration Updates

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Provider migration **MUST** update the current Identity Document to reflect the new operational state.

### Source
REM-01 — IREM-0040

### Related Invariants
- CI-08

---

## REL-ID-069

### Title
Migration Discovery

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Provider migration **MUST** publish sufficient information to enable discovery of the new service location.

### Source
REM-01 — IREM-0040

### Related Invariants
- CI-03

---

## REL-ID-070

### Title
Identity Continuity During Migration

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Provider migration **MUST** preserve identity continuity.

### Rationale
Migration changes operational hosting, not constitutional identity.

### Source
REM-01 — IREM-0040

### Related Invariants
- CI-01
- CI-03

---

## REL-ID-071

### Title
Temporary Migration Redirection

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
Implementations **MAY** provide temporary redirection mechanisms during provider migration.

### Source
REM-01 — IREM-0040

### Related Invariants
- CI-03

---

## REL-ID-072

### Title
Multi-Provider Support

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement
The architecture **MAY** support multiple providers delivering different identity-related services.

### Source
REM-01 — IREM-0041

### Related Invariants
- CI-03

---

## REL-ID-073

### Title
Provider Coupling

**Level:** Architectural

**Normative Keyword:** **SHOULD NOT**

### Statement
Identity-related services **SHOULD NOT** be permanently coupled to a single provider.

### Source
REM-01 — IREM-0041

### Related Invariants
- CI-03

---

## REL-ID-074

### Title
Identity Creation Outputs

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement
Identity creation **MUST** produce the protocol artefacts required to establish a valid Relay Identity.

### Rationale
Creation establishes the initial protocol state from which all future operations derive.

### Source
REM-01 — IREM-0042

### Related Invariants
- CI-01
- CI-08

---

## REL-ID-075

### Title
Initial Trust Establishment

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
The initial Identity Document **MUST** establish the first recognised authority for the Relay Identity.

### Source
REM-01 — IREM-0043

### Related Invariants
- CI-02
- CI-08

---

## REL-ID-076

### Title
Provider-Assisted Creation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement
Providers **MAY** assist in the creation of Relay Identities.

### Source
REM-01 — IREM-0044

### Related Invariants
- CI-02

---

## REL-ID-077

### Title
Creation Without Provider Lock-In

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
Provider-assisted identity creation **MUST NOT** grant the provider exclusive authority that prevents future migration.

### Source
REM-01 — IREM-0044

### Related Invariants
- CI-03

---

## REL-ID-078

### Title
Hosting Neutrality

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Self-hosted and commercially hosted Relay Identities **MUST** follow the same protocol-level rules.

### Rationale
Protocol behaviour must remain independent of hosting model.

### Source
REM-01 — IREM-0045

### Related Invariants
- CI-03

---

# Editorial Review Notes

This part establishes provider independence as a constitutional property of Relay. Providers may host, assist, or facilitate identity operations, but they do not define the identity itself. Migration, hosting changes and provider-assisted creation are therefore treated as operational concerns that preserve identity continuity rather than alter it.
