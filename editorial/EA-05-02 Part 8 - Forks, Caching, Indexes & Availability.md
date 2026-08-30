# EA-05-02 — Repository Requirements Catalogue
## Part 8 — Forks, Caching, Indexes & Availability

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Repository  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing Repository forks, caching, indexes and availability.

It establishes how compliant implementations may improve collaboration, performance and resilience while preserving the constitutional authority of the canonical Repository.

---

# 2. Scope

This part defines normative requirements governing:

- Repository Forks
- Repository Caching
- Repository Indexes
- Repository Availability
- Canonical Repository Authority

---

# 3. Requirements

## REL-REP-092

### Title
Repository Forks

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

A Relay Repository **MAY** be forked in accordance with protocol-defined rules.

### Rationale

Forks support collaboration and experimentation without altering the original Repository.

### Source

REM-02 — RREM-0171

### Related Invariants

- CI-03

---

## REL-REP-093

### Title
Fork Independence

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Every Fork **MUST** remain a distinct Repository possessing its own Repository identity while preserving provenance linking it to the originating Repository.

### Rationale

Forks create independent repositories rather than alternate views of the original.

### Source

REM-02 — RREM-0172 to RREM-0176

### Related Invariants

- CI-01
- CI-08

---

## REL-REP-094

### Title
Repository Caching

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Implementations **MAY** maintain Repository caches to improve performance.

### Rationale

Caching is an implementation optimisation rather than a protocol requirement.

### Source

REM-02 — RREM-0177

### Related Invariants

- CI-03

---

## REL-REP-095

### Title
Cache Authority

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

Cached Repository data **MUST NOT** replace or redefine the canonical Repository.

### Rationale

Caches are operational conveniences and never become protocol authority.

### Source

REM-02 — RREM-0178 to RREM-0180

### Related Invariants

- CI-08

---

## REL-REP-096

### Title
Repository Indexes

**Level:** Architectural

**Normative Keyword:** **MAY**

### Statement

Implementations **MAY** maintain Repository indexes to improve discovery and query performance.

### Rationale

Indexes support efficient access without affecting protocol semantics.

### Source

REM-02 — RREM-0181

### Related Invariants

- CI-03

---

## REL-REP-097

### Title
Index Integrity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Repository indexes **MUST** be derived from canonical Repository content, remain regenerable from canonical Repository state, and **MUST NOT** redefine or replace canonical Repository authority.

### Rationale

Indexes are derived operational structures.

### Source

REM-02 — RREM-0182 to RREM-0185

### Related Invariants

- CI-08

---

## REL-REP-098

### Title
Repository Availability

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

Repository availability **MUST** remain independent of any individual provider instance or service endpoint.

### Rationale

Repository existence is independent of operational infrastructure.

### Source

REM-02 — RREM-0186

### Related Invariants

- CI-03

---

## REL-REP-099

### Title
Availability Continuity

**Level:** Behavioural

**Normative Keyword:** **MUST**

### Statement

Temporary service interruption **MUST NOT** alter Repository identity, integrity or history, and loss of an individual endpoint **MUST NOT** constitute Repository loss.

### Rationale

Operational outages do not affect constitutional Repository existence.

### Source

REM-02 — RREM-0187 to RREM-0191

### Related Invariants

- CI-03
- CI-08

---

## REL-REP-100

### Title
Availability Neutrality

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement

Availability mechanisms **MUST** remain transparent to Repository semantics and preserve canonical Repository behaviour.

### Rationale

Availability strategies must not change protocol behaviour.

### Source

REM-02 — RREM-0192

### Related Invariants

- CI-03

---

# Editorial Review Notes

This part reinforces the constitutional distinction between the canonical Repository and auxiliary operational structures. Forks, caches, indexes and availability mechanisms improve collaboration, resilience and performance, but they never redefine Repository identity, authority or integrity. The Repository remains the sole canonical source of protocol truth.
