# Relay Editorial Audit 04

# Canonical Terminology Map

**Document ID:** EA-04  
**Status:** Founder Review Draft

---

# 1. Purpose

This document establishes the canonical vocabulary of the Relay Protocol.

It does **not** redefine protocol concepts.

Its purpose is to identify:

- the approved protocol term;
- approved short forms;
- deprecated or ambiguous alternatives;
- the authoritative source chapter;
- where the glossary should define the concept.

The glossary in the future specification should be derived from this map.

---

# 2. Canonical Vocabulary

| Canonical Term | Approved Short Form | Avoid / Retire | Canonical Source | Classification |
|---|---|---|---|---|
| Relay Identity | Identity | Digital Identity | Identity Model | Constitutional |
| Controller | Controller | Identity Controller (as separate defined term) | Identity Model | Constitutional |
| Relay Repository | Repository | Data Store | Repository Model | Constitutional |
| Relay Record | Record | Entry / Item | Record Model | Constitutional |
| Relay Relationship | Relationship | Link | Relationship Model | Constitutional |
| Relay Application | Application | Client (when referring to the protocol object) | Application & Permission Model | Constitutional |
| Relay Provider | Provider | Host | Ecosystem Roles | Constitutional |
| Permission Grant | Permission Grant | Permission Token (as the concept) | Application & Permission Model | Behavioural |
| Commit | Commit | Relay Commit (except on first introduction if desired) | Commit & Verification Model | Behavioural |
| Event | Event | Notification | Event & Synchronisation Model | Behavioural |
| Synchronisation | Synchronisation | Sync State | Event & Synchronisation Model | Behavioural |
| Migration | Migration | Transfer | Migration & Portability Model | Behavioural |
| Discovery | Discovery | Lookup | Discovery & Resolution Model | Behavioural |
| Resolution | Resolution | Resolve Lookup | Discovery & Resolution Model | Behavioural |
| Identity Document | Identity Document | Identity File | Identity Model | Structural |
| Repository Head | Repository Head | Current Commit | Commit & Verification Model | Structural |
| Schema | Schema | Data Model | Schema & Interoperability Model | Structural |
| Namespace | Namespace | Domain | Schema & Interoperability Model | Structural |
| Blob | Blob | Binary Object | Repository Model | Structural |
| Handle | Handle | Username | Discovery & Resolution Model | Structural |
| Witness | Witness | - | Ecosystem Roles | Structural Role |
| Client | Client | Application (when referring to implementation) | Application & Client Compliance | Structural Role |
| Conformance | Conformance | - | Conformance Testing | Governance |
| Compliance | Compliance | - | Compliance Chapters | Governance |
| Certification | Certification | - | Conformance Testing | Governance |
| Stewardship | Stewardship | Governance Body | Governance & Evolution | Governance |
| Constitutional Principle | Constitutional Principle | Principle | Governance & Evolution | Governance |

---

# 3. Terminology Rules

## TM-001

Every capitalised Relay protocol term shall have exactly one canonical definition.

## TM-002

Every later chapter shall reference that definition instead of restating it.

## TM-003

Compliance chapters add obligations.

They do not redefine concepts.

## TM-004

Ecosystem Roles define actors.

They do not redefine protocol objects.

## TM-005

Implementation terminology must not replace protocol terminology.

---

# 4. Terms Requiring Editorial Care

The following terms require consistent wording throughout the specification:

- Controller
- Commit
- Relay Application
- Witness
- Conformance
- Compliance
- Certification

---

# 5. Glossary Generation Order

The future GLOSSARY.md should define terms in this order:

1. Constitutional
2. Behavioural
3. Structural
4. Governance

This ensures readers understand the protocol's foundations before its mechanics.

---

# Editorial Decisions

**ED-020** — Canonical terminology is established by this map.

**ED-021** — The glossary shall be generated directly from this map.

**ED-022** — Deprecated or ambiguous synonyms shall not appear as defined protocol terms.

---

## Audit Result

**Editorial Audit 04: Canonical Terminology Map — Complete**
