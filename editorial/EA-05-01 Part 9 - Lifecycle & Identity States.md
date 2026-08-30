# EA-05-01 — Identity Requirements Catalogue
## Part 9 — Lifecycle & Identity States

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Identity  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the normative requirements governing the lifecycle of a Relay Identity, including identity transfer, deletion, operational states, suspension and termination.

It is derived from the approved REM-01 and the Lifecycle & Identity States sections of the Identity Model.

---

# 2. Scope

This part covers:

- Identity transfer
- Identity deletion
- Operational identity states
- Provider suspension
- Hosting suspension
- Lifecycle distinctions

---

# 3. Requirements

## REL-ID-088

### Title
Explicit Identity Transfer

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Identity transfer **MUST** occur only through an explicit and verifiable protocol process.

### Rationale
Constitutional identity ownership cannot change implicitly.

### Source
REM-01 — IREM-0051

### Related Invariants
- CI-02

---

## REL-ID-089

### Title
Transfer by Provider Sale

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** transfer solely because a provider account is sold.

### Source
REM-01 — IREM-0052

### Related Invariants
- CI-03

---

## REL-ID-090

### Title
Transfer by Domain Change

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** transfer solely because a domain expires or changes ownership.

### Source
REM-01 — IREM-0053

### Related Invariants
- CI-03

---

## REL-ID-091

### Title
Transfer by Handle Reassignment

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement
A Relay Identity **MUST NOT** transfer solely because a username or Handle is reassigned.

### Source
REM-01 — IREM-0055

### Related Invariants
- CI-01

---

## REL-ID-092

### Title
Identifier Reassignment

**Level:** Constitutional

**Normative Keyword:** **SHOULD NOT**

### Statement
A Relay Identifier **SHOULD NOT** be reassigned to another entity after identity deletion.

### Source
REM-01 — IREM-0058

### Related Invariants
- CI-05

---

## REL-ID-093

### Title
Operational Identity States

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** recognise the protocol-defined operational identity states.

### Source
REM-01 — IREM-0060

### Related Invariants
- CI-01

---

## REL-ID-094

### Title
Provider Suspension

**Level:** Behavioural

**Normative Keyword:** **MUST NOT**

### Statement
Provider suspension **MUST NOT** automatically terminate the underlying Relay Identity.

### Source
REM-01 — IREM-0061

### Related Invariants
- CI-03

---

## REL-ID-095

### Title
Moderation Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** distinguish protocol identity state from application moderation decisions.

### Source
REM-01 — IREM-0062

### Related Invariants
- CI-03

---

## REL-ID-096

### Title
Hosting Ownership Separation

**Level:** Architectural

**Normative Keyword:** **MUST**

### Statement
Provider hosting status **MUST** remain distinct from ownership of a Relay Identity.

### Source
REM-01 — IREM-0063

### Related Invariants
- CI-03

---

## REL-ID-097

### Title
Repository Export

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Providers **SHOULD** permit repository export where legally permissible.

### Source
REM-01 — IREM-0064

### Related Invariants
- CI-03

---

## REL-ID-098

### Title
Migration Support

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Providers **SHOULD** support identity migration where legally permissible.

### Source
REM-01 — IREM-0065

### Related Invariants
- CI-03

---

## REL-ID-099

### Title
Recovery Information Access

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement
Providers **SHOULD** provide access to recovery information where legally permissible.

### Source
REM-01 — IREM-0066

### Related Invariants
- CI-02

---

## REL-ID-100

### Title
Protocol State Separation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement
Implementations **MUST** distinguish provider suspension, application blocking, community moderation and protocol-level identity termination.

### Rationale
Operational and governance states must not be conflated.

### Source
REM-01 — IREM-0068

### Related Invariants
- CI-03

---

# Editorial Review Notes

This part formalises the lifecycle boundaries of a Relay Identity. It distinguishes constitutional identity from hosting, provider accounts and application moderation, ensuring that operational events do not inadvertently redefine ownership or continuity.
