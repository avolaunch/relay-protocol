# Relay Protocol

Relay is an open protocol for portable digital identity, user-controlled data and application interoperability.

It explores an alternative to today’s platform-centred internet: one in which people and organisations can retain the same digital identity, records, relationships and permissions while changing applications or service providers.

## Current status

Relay Protocol is currently at the architectural design stage.

This repository begins with the original Relay design corpus:

* **Part 0:** Relay at a Glance
* **Core Objects 1–15:** the foundational identity, repository, record, permissions, relationships, migration, verification, resolution, schemas, synchronisation, ecosystem, compliance, conformance and governance models

These documents are being preserved as the source material from which the formal Relay Protocol Specification will be developed.

## Repository structure

```text
relay-protocol/

├── README.md
├── design-notes/
│   ├── 00-relay-at-a-glance.md
│   ├── 01-identity-model.md
│   ├── 02-repository-model.md
│   ├── 03-record-model.md
│   ├── 04-application-and-permission-model.md
│   ├── 05-relationship-model.md
│   ├── 06-migration-and-portability-model.md
│   ├── 07-commit-and-verification-model.md
│   ├── 08-discovery-and-resolution-model.md
│   ├── 09-schema-and-interoperability-model.md
│   ├── 10-event-and-synchronisation-model.md
│   ├── 11-ecosystem-roles.md
│   ├── 12-provider-compliance-model.md
│   ├── 13-application-and-client-compliance-model.md
│   ├── 14-conformance-testing-model.md
│   └── 15-governance-and-evolution-model.md
│
├── specification/
├── schemas/
├── examples/
├── diagrams/
├── conformance/
└── reference-implementation/
```

Only the original design corpus is included at this stage. The empty project areas will be added as the protocol progresses.

## Core premise

Applications should create experiences, not ownership.

Providers should compete through service, not lock-in.

A person should be able to replace either without losing their digital continuity.

## Status notice

The documents in `design-notes/` are architectural design materials, not yet a final or implementable protocol standard.

The formal specification, security model, schemas, test vectors and reference implementation remain under development.
