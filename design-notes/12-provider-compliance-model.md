# Relay Protocol v0.1  
## Core Object 12: Provider Compliance Model

### 1. Definition

A **Relay-compatible Provider** is a service operator that hosts or operates one or more Relay services while preserving the Controller’s ability to replace that Provider without losing identity, repository or relationship continuity.

Provider compliance is not established merely by:

- offering data export;
- using Relay terminology;
- publishing an API;
- allowing third-party applications;
- claiming that users own their data;
- releasing some source code.

A Provider is Relay-compatible only when its technical and operational behaviour satisfies the requirements of this model.

The central requirement is:

> A Relay Provider must be useful while remaining replaceable.

---

## 2. Purpose

The Provider Compliance Model defines the minimum obligations a service must satisfy before describing itself as:

- Relay-compatible;
- Relay-compliant;
- a Relay Provider;
- a compatible Relay host;
- a portable Relay service.

These obligations exist to prevent nominal portability in which a Provider:

- offers files but not operational migration;
- retains exclusive identity authority;
- uses proprietary identifiers;
- strips unsupported records;
- blocks competing applications;
- prevents independent verification;
- continues controlling the identity after departure.

Compliance must be demonstrated through observable behaviour, not only policy statements.

---

## 3. Compliance scope

Provider compliance may apply to one or more service roles.

Possible profiles include:

```text
Identity Provider
Repository Provider
Authorisation Provider
Event Provider
Blob Provider
Migration Provider
Recovery Provider
Full Relay Provider
```

A Provider must declare which profiles it implements.

A service compliant only as a Blob Provider must not claim compliance with repository or identity-hosting requirements.

---

## 4. Full Relay Provider

A **Full Relay Provider** operates the minimum bundled service set required for the first reference implementation.

This includes:

- Identity Document hosting;
- Repository Service;
- Authorisation Service;
- Event Service;
- Blob Service;
- export;
- migration;
- recovery support.

A Full Relay Provider may use subcontractors, but remains responsible for compliance across the declared service.

---

## 5. Compliance levels

Relay v0.1 may recognise the following compliance levels:

### Self-declared

The Provider states that it follows the specification but has not completed independent testing.

### Test-validated

The Provider has passed the relevant automated conformance suite.

### Independently verified

An approved independent party has tested the Provider’s implementation.

### Certified

The Provider has passed technical, operational and portability requirements defined by Relay governance.

These labels must not be represented as interchangeable.

---

## 6. Provider manifest

Every compliant Provider must publish a signed, versioned **Provider Manifest**.

The manifest should identify:

- Provider Identity;
- legal or accountable operator;
- roles performed;
- service endpoints;
- supported Relay versions;
- supported compliance profiles;
- public keys;
- jurisdictions;
- data locations where relevant;
- storage and size limits;
- supported schema behaviour;
- migration capabilities;
- recovery capabilities;
- event-retention policy;
- export formats;
- content-policy reference;
- security contact;
- incident endpoint;
- service status endpoint;
- manifest version;
- signature.

Example:

```json
{
  "id": "rid:provider:alpha",
  "name": "Provider Alpha",
  "operator": "rid:relay:alpha-company",
  "manifestVersion": 3,
  "relayVersions": [
    "relay-0.1"
  ],
  "profiles": [
    "identity-provider",
    "repository-provider",
    "authorization-provider",
    "event-provider",
    "blob-provider",
    "migration-provider"
  ],
  "services": {
    "identity": "https://alpha.example/identity",
    "repository": "https://alpha.example/repository",
    "authorization": "https://alpha.example/authorize",
    "events": "https://alpha.example/events",
    "migration": "https://alpha.example/migration"
  },
  "jurisdictions": [
    "ZA"
  ],
  "unknownSchemaPreservation": true,
  "signature": "..."
}
```

The exact structure remains provisional.

---

# Part I — Identity Compliance

## 7. Provider-independent identity

A compliant Provider must not make the Relay Identifier dependent on:

- the Provider’s domain;
- an internal database key;
- the Provider’s account number;
- the Provider’s application username;
- a Provider-owned blockchain token;
- a proprietary registry inaccessible to other implementations.

The Relay Identifier must remain valid after the Controller leaves.

---

## 8. Identity Document access

The Provider must allow authorised access to:

- the current Identity Document;
- required historical Identity Documents;
- public keys;
- service descriptors;
- document version;
- document integrity data;
- migration status;
- identity state.

The Provider must not conceal information required for independent resolution or migration.

---

## 9. Identity authority separation

The Provider must distinguish between:

- Provider account access;
- ordinary authentication;
- repository signing;
- root identity authority;
- recovery authority;
- migration authority.

Access to a Provider account must not automatically confer unrestricted identity authority.

---

## 10. Independent update authority

The Provider must not be the sole authority capable of publishing a replacement Identity Document.

A compliant identity-hosting arrangement must support at least one Provider-independent authority path, such as:

- Controller-held root authority;
- recovery key;
- trusted-device threshold;
- recovery quorum;
- independently controlled domain;
- external resolution authority.

---

## 11. Identity export

The Provider must allow the Controller to export identity metadata required for continuity, including:

- Relay Identifier;
- current Identity Document;
- relevant document history;
- public keys;
- key-status metadata;
- verified-handle records;
- service descriptors;
- recovery configuration references;
- identity-state information;
- verification data.

Private key material must not be exported insecurely.

---

## 12. Handle portability

The Provider must distinguish:

- Provider-issued handles;
- independently controlled handles;
- Relay Identifier.

A Provider-issued handle may cease functioning after departure.

The Provider must not imply that loss of that handle means loss of the Relay Identity.

Where policy permits, the Provider should support temporary signed redirection after migration.

---

## 13. Identity termination

The Provider must not terminate the underlying Relay Identity merely because:

- the hosting account is closed;
- payment ends;
- the Provider suspends service;
- the user changes Provider;
- the Provider discontinues a product.

The Provider may terminate its service relationship.

Protocol-level identity termination requires valid Controller authority or another recognised legal and technical basis.

---

# Part II — Repository Compliance

## 14. Canonical repository identifiers

A compliant Provider must preserve:

- Repository Identifier;
- Record URIs;
- collection names;
- Record Keys;
- schema identifiers;
- commit identifiers.

Provider migration must not require new canonical identifiers.

---

## 15. Authorised commits only

The Repository Service must accept canonical changes only through valid authority.

It must validate:

- commit structure;
- expected Repository Head;
- signatures;
- key validity;
- Permission Grant validity;
- schema validity;
- repository-state constraints.

Provider administrators must not create or rewrite canonical user records outside a recorded authority path.

---

## 16. Repository Head availability

The Provider must expose the current canonical Repository Head to authorised clients and verifiers.

It must not serve multiple incompatible heads as one canonical state.

Known fork conditions must be disclosed.

---

## 17. Commit-history integrity

The Provider must preserve enough commit history and verification data to support the declared verification level.

It must not:

- reorder commits;
- silently remove accepted commits;
- rewrite commit contents;
- change signatures;
- conceal known forks;
- fabricate historical ancestry.

---

## 18. Unknown schema preservation

A compliant Repository Provider must preserve unknown but structurally valid schemas.

It may classify them as:

```text
fully supported
read-only
preserve-only
unsupported for rendering
```

It must not discard them merely because:

- the Provider does not have a user interface for them;
- the original application is unavailable;
- the schema is commercially inconvenient;
- the Provider prefers another format.

---

## 19. Unknown field preservation

The Provider must preserve valid unknown extension fields during:

- read and write operations;
- export;
- import;
- backup;
- migration;
- restoration.

It must not round-trip a record through its API and silently remove unsupported extensions.

---

## 20. Record-version preservation

The Provider must preserve record-version information according to the declared history-retention profile.

Where earlier content has been erased, it must retain the minimum permitted integrity evidence, such as:

- version number;
- content hash;
- deletion commit;
- tombstone;
- authorising authority.

---

## 21. Deletion accuracy

The Provider must distinguish between:

- active record;
- hidden record;
- logically deleted record;
- content-erased record;
- Provider-restricted record;
- legally withheld record;
- unavailable record.

It must not report content as deleted merely because it has stopped displaying it.

---

## 22. Fork handling

The Provider must detect and report repository forks.

During an unresolved fork, it must not silently choose a canonical branch without a valid resolution basis.

It should support:

- read-only safety mode;
- branch inspection;
- Resolution Commit processing;
- Controller-authorised reconciliation.

---

## 23. Independent verification

The Provider must expose sufficient information for an independent verifier to check:

- Identity Document chain;
- commit ancestry;
- commit signatures;
- repository state;
- records;
- blobs;
- export integrity;
- migration integrity.

A Provider-controlled dashboard alone is not independent verification.

---

# Part III — Export Compliance

## 24. Standard export

A compliant Provider must support a documented Provider-independent Relay export.

The export must not require:

- proprietary Provider software to read;
- an active paid subscription to verify;
- an application-specific account;
- access to undocumented internal APIs;
- continued operation of the source Provider.

---

## 25. Export contents

A complete export must include or validly reference:

- Relay Identifier;
- Repository Identifier;
- Identity Document information;
- repository metadata;
- current Repository Head;
- commit history required by the declared profile;
- records;
- tombstones;
- blobs or blob manifest;
- schemas or verifiable schema references;
- application grant metadata required for continuity;
- integrity data;
- export manifest;
- completeness declaration.

---

## 26. Export completeness declaration

Every export must state whether it is:

```text
complete
partial
public-only
metadata-only
collection-limited
date-limited
recovery export
```

A Provider must not label a partial archive as a complete Relay export.

---

## 27. Export availability

The Controller must be able to request an export without unreasonable friction.

A Provider may apply proportionate controls for:

- fresh authentication;
- private-data protection;
- large transfer preparation;
- abuse prevention;
- unpaid storage charges where lawful;
- legal restrictions.

It must not use artificial delay or unnecessary manual review to obstruct departure.

---

## 28. Export frequency

A Provider should support periodic exports or backup synchronisation.

The Provider Manifest must disclose:

- whether on-demand export is supported;
- rate limits;
- expected preparation method;
- incremental-export support;
- recovery-export options.

---

## 29. Export verification

The export must include enough data for an independent tool to verify:

- identity consistency;
- repository consistency;
- commit validity;
- record integrity;
- blob integrity;
- export completeness;
- declared Repository Head.

---

## 30. Export encryption

Exports containing restricted or private records must support secure encryption.

The Provider must not produce sensitive exports through:

- publicly accessible URLs;
- unencrypted email attachments;
- permanent reusable links;
- weak shared passwords.

The Controller must retain a usable way to decrypt the export independently of the source Provider.

---

# Part IV — Migration Compliance

## 31. Operational migration

A compliant Provider must support operational migration, not merely export.

Operational migration includes:

- destination authorisation;
- repository transfer;
- blob transfer or verified reference transfer;
- integrity verification;
- incremental synchronisation;
- cutover;
- Identity Document update;
- source-write deactivation;
- transitional redirection where supported.

---

## 32. Source Provider duties

As a source, the Provider must:

- verify migration authority;
- produce the required export;
- expose the Migration Snapshot head;
- transfer or expose required data;
- preserve changes created during transfer;
- provide final synchronisation;
- participate in final-head agreement;
- stop accepting canonical writes after cutover;
- disclose residual-data retention.

---

## 33. Destination Provider duties

As a destination, the Provider must:

- verify migration authority;
- declare capabilities;
- disclose unsupported features;
- preserve unknown schemas;
- verify imported history;
- verify blobs;
- confirm the final Repository Head;
- avoid serving incomplete state as complete;
- issue new operational credentials;
- activate only after valid cutover.

---

## 34. No migration ransom

A Provider must not make migration technically impossible as a retention mechanism.

Reasonable charges may be permitted for:

- very large data transfer;
- physical media;
- exceptional support;
- lawful outstanding obligations.

Charges must be disclosed and must not function as an artificial lock-in penalty.

---

## 35. Migration refusal

Where a Provider cannot perform all or part of a migration, it must identify the reason.

Possible reasons include:

- legal prohibition;
- invalid authority;
- unresolved identity compromise;
- destination incompatibility;
- active repository fork;
- unavailable encryption key;
- temporary infrastructure failure.

A generic refusal such as:

```text
Migration unavailable
```

is insufficient where a more precise explanation can safely be provided.

---

## 36. Migration receipt

The source and destination should produce or support a Migration Receipt containing:

- source;
- destination;
- migration scope;
- initial snapshot head;
- final Repository Head;
- verification result;
- activation time;
- residual source-data policy;
- grant continuity status;
- unsupported items;
- signatures.

---

## 37. Emergency migration support

A compliant Full Relay Provider must support restoration from a verified recovery export or replica.

It must accurately disclose:

- last recovered Repository Head;
- missing commit range;
- missing blobs;
- unresolved conflicts;
- restored identity state.

It must not claim complete continuity where data was lost.

---

# Part V — Application Access Compliance

## 38. Open application access

A compliant Provider must permit compatible third-party Applications to request access through documented interfaces.

It may require:

- Application Manifest;
- security controls;
- callback registration;
- rate limits;
- user approval;
- abuse prevention;
- conformance with relevant protocol requirements.

It must not restrict access solely to its own first-party Applications.

---

## 39. First-party neutrality

A Provider’s first-party Application must not receive hidden protocol access unavailable to equivalent third-party Applications, except for:

- necessary Provider administration;
- explicitly disclosed integrated-service features;
- security-sensitive internal operations that are not application capabilities.

Optional first-party features must remain distinguishable from mandatory hosting operations.

---

## 40. Permission enforcement

The Provider must enforce Permission Grants according to:

- resource;
- action;
- duration;
- purpose where technically enforceable;
- installation;
- user-present or background mode;
- revocation state.

The Provider must not issue broader access tokens than the approved grant.

---

## 41. Partial approval

Where the Application and protocol profile support it, the Provider must allow the Controller to approve a subset of requested scopes.

The Provider must not force all-or-nothing approval for unrelated optional capabilities.

---

## 42. Revocation enforcement

After revocation, the Provider must stop:

- issuing new access tokens;
- renewing access;
- accepting delegated-key operations;
- sending protected events;
- allowing background access;
- accepting operations under the revoked grant.

Revocation must not delete records previously created through the Application.

---

## 43. Application activity visibility

The Provider should allow the Controller to inspect:

- connected Applications;
- granted scopes;
- recent access;
- recent record changes;
- background subscriptions;
- active installations;
- exports;
- revocations;
- failed high-risk attempts.

---

## 44. Application replacement

The Provider must not bind canonical records to the Application that created them.

Another authorised compatible Application must be able to:

- read supported records;
- update supported records;
- preserve unsupported records;
- continue relationships;
- use stable Record URIs.

---

# Part VI — Event Compliance

## 45. Event availability

A compliant Provider must support at least one durable event or incremental synchronisation method.

Relay v0.1 provisionally requires:

- cursor-based pull events or commit retrieval;
- gap detection;
- resumption;
- canonical backfill.

Signed webhook support may be optional for some profiles.

---

## 46. Event correctness

The Provider must not emit a successful canonical event before the underlying operation is accepted.

Repository events should reference:

- canonical commit;
- Repository Head;
- affected record or collection;
- stable Event Identifier.

---

## 47. Duplicate-safe delivery

Where event delivery is retried, the Provider must retain the same Event Identifier.

The Provider should document that delivery is at least once.

---

## 48. Event gap disclosure

If requested events are no longer available, the Provider must return a clear gap response and offer a canonical resynchronisation path.

It must not return only the latest event while implying that no events were missed.

---

## 49. Protected event access

Private or restricted events must be limited by active authority.

Revocation of the underlying grant must stop protected event delivery.

---

## 50. Migration event boundary

After migration, the source Provider must expose a clear final stream boundary where supported.

The destination must avoid replaying historical repository activity as new events unless explicitly requested.

---

# Part VII — Blob Compliance

## 51. Content integrity

The Provider must verify stored and transferred blobs against declared content hashes.

A matching filename, media type or byte size is not sufficient.

---

## 52. Blob portability

The Provider must support migration or export of blobs required by active records.

A Provider URL must not be the permanent blob identifier.

---

## 53. Blob access

The Provider must enforce blob access consistently with the associated records and grants.

It must not make a restricted blob public merely because its storage URL is known.

---

## 54. Blob deletion

The Provider must distinguish between:

- removing a blob reference;
- deleting one physical copy;
- deleting all unreferenced copies;
- retaining a legal or backup copy;
- content-addressed deduplication.

The user-facing status must accurately describe what occurred.

---

## 55. Provider-only encryption prohibition

A Provider must not make private blobs portable in ciphertext while retaining the only usable decryption authority.

The Controller must retain a migration path that preserves authorised decryption.

---

# Part VIII — Security Compliance

## 56. Secure transport

All sensitive Relay service communications must use current secure transport.

Providers must protect against:

- credential interception;
- callback substitution;
- replay;
- session fixation;
- unauthorised endpoint redirection;
- downgrade attacks.

---

## 57. Key protection

The Provider must protect:

- repository signing keys;
- Provider signing keys;
- delegated application keys;
- token-signing keys;
- encryption keys;
- recovery-related secrets.

The Provider Manifest or security documentation should describe whether keys are:

- software-held;
- hardware-backed;
- user-held;
- Provider-held under delegation.

---

## 58. Key rotation

The Provider must support secure rotation of its operational keys.

Rotation must preserve:

- historical verification;
- manifest continuity;
- valid transition periods;
- revocation information.

---

## 59. Least privilege

Internal Provider systems and personnel should receive only the access necessary for their role.

A customer-support account should not automatically possess:

- raw private-vault access;
- root identity authority;
- unrestricted repository signing;
- migration authority.

---

## 60. Administrative actions

Material administrative actions affecting a user’s Relay service should be attributable.

Examples include:

- Provider suspension;
- legal restriction;
- manual record removal;
- migration override;
- recovery intervention;
- account-access reset.

The Provider should retain an internal audit trail.

---

## 61. Security incident reporting

A compliant Provider must publish a security contact and incident process.

Where a material incident affects Relay users, the Provider should disclose:

- affected services;
- affected time period;
- affected authority;
- likely impact;
- required user action;
- key rotation or revocation;
- migration implications.

---

## 62. Compromise containment

Compromise of one role should not automatically compromise every role.

For example:

- first-party Application compromise should not expose root identity authority;
- Blob Service compromise should not permit repository commits;
- Resolver compromise should not permit valid Identity Document signing;
- support-system compromise should not permit migration.

---

## 63. Recovery safeguards

Provider-assisted recovery must use stronger controls than ordinary password reset where it can affect identity authority.

Recovery should support:

- delay;
- device notification;
- secondary approval;
- audit event;
- key replacement;
- emergency revocation.

---

## 64. Abuse prevention

The Provider may apply reasonable controls against:

- spam;
- malware;
- denial of service;
- automated scraping abuse;
- fraudulent identities;
- illegal content;
- excessive resource use.

These controls must not be disguised as identity ownership.

Where lawful and possible, suspension should preserve export or migration capability for unaffected lawful data.

---

# Part IX — Privacy and Data-Practice Compliance

## 65. Role-based processing

A multi-role Provider must separate processing performed as:

- host;
- Application;
- Indexer;
- AI Service;
- Backup Provider;
- analytics provider.

Hosting access must not silently authorise optional secondary uses.

---

## 66. Data minimisation

The Provider should collect only information necessary for:

- operating the service;
- security;
- billing;
- legal compliance;
- explicitly approved optional features.

Relay compliance does not permit unlimited Provider surveillance.

---

## 67. Private-record confidentiality

Restricted and private records must not be exposed to:

- unauthorised Applications;
- public Indexers;
- unrelated Provider roles;
- other customers;
- logs without appropriate controls.

---

## 68. Access logging

Sensitive-data access by Provider personnel or privileged systems should be logged where practical.

The Provider should distinguish:

- ordinary automated storage access;
- application access;
- administrative access;
- emergency access;
- legal access.

---

## 69. Retention disclosure

The Provider must disclose retention for:

- active repository data;
- deleted records;
- blobs;
- backups;
- events;
- audit logs;
- migration copies;
- suspended accounts;
- closed accounts.

It must distinguish operational retention from legal retention.

---

## 70. Residual-data handling

After migration or account closure, the Provider must disclose:

- what remains;
- why it remains;
- where it remains;
- whether it remains accessible;
- planned deletion time;
- legal exceptions.

---

## 71. Optional processing

Optional services such as:

- recommendations;
- advertising;
- analytics;
- AI assistance;
- public indexing;
- training;
- cross-service personalisation;

must be separately declared and authorised where required.

---

# Part X — Availability and Operational Compliance

## 72. Service status

The Provider must expose meaningful service status for its declared roles.

Possible states include:

```text
available
degraded
read-only
migrating
suspended
unavailable
retiring
terminated
```

The Provider must not represent an unavailable repository as a nonexistent identity.

---

## 73. Read-only operation

When possible, a Provider experiencing partial failure should prefer read-only operation over serving inconsistent writes.

The Repository Head must remain clearly identified.

---

## 74. Backup and recovery

A Full Relay Provider must maintain a documented backup and recovery process.

The process should define:

- backup frequency;
- verification;
- geographic or infrastructure separation;
- recovery-point objectives;
- recovery-time objectives;
- user-held recovery-export support;
- test frequency.

Exact performance thresholds may be profile-specific.

---

## 75. Data-loss disclosure

If the Provider loses accepted repository data, it must disclose:

- last verified Repository Head;
- affected commit range;
- affected blobs;
- recovery source;
- restoration status;
- possible migration consequences.

It must not silently restore an older state and present it as complete.

---

## 76. Provider shutdown plan

A compliant Provider must publish a service-exit plan.

The plan should cover:

- user notice;
- exports;
- migrations;
- API availability;
- billing closure;
- recovery copies;
- transitional resolution;
- residual deletion;
- support channels.

---

## 77. Service retirement notice

A Provider should give reasonable notice before discontinuing a service, except where impossible due to:

- insolvency;
- emergency;
- legal order;
- severe security event.

The Provider should prioritise migration access during the notice period.

---

## 78. Provider disappearance resilience

A Full Relay Provider should support at least one mechanism reducing catastrophic dependence on its continued existence, such as:

- user-held recovery exports;
- independent backup service;
- mirrored Identity Documents;
- external recovery authority;
- replicated signed state.

---

# Part XI — Policy and Moderation Compliance

## 79. Provider policy rights

A Provider may define and enforce:

- acceptable-use rules;
- content restrictions;
- storage limits;
- rate limits;
- legal requirements;
- payment terms;
- regional availability.

Relay compliance does not require every Provider to host every user or record.

---

## 80. Policy transparency

The Provider must distinguish between:

- protocol-invalid operation;
- Permission failure;
- security rejection;
- Provider policy rejection;
- legal restriction;
- service-limit rejection.

These should not all appear as a generic protocol error.

---

## 81. Suspension accuracy

A Provider suspension must not be represented as:

- identity deletion;
- cryptographic invalidity;
- user revocation;
- repository termination;

unless those states separately apply.

---

## 82. Portability during suspension

Where technically and legally possible, a suspended Controller should retain access to:

- identity metadata;
- repository export;
- migration;
- lawful records;
- recovery configuration.

A Provider may restrict records or operations that would violate law or security requirements.

---

## 83. Moderation separation

The Provider may refuse to serve a record.

It must not alter the canonical record silently to enforce presentation policy.

Possible actions include:

- withhold serving;
- attach Provider status;
- require migration;
- limit public distribution;
- preserve record for export where lawful.

---

# Part XII — Version and Compatibility Compliance

## 84. Supported versions

The Provider Manifest must list:

- supported Relay versions;
- preferred version;
- deprecated versions;
- minimum security version;
- planned end-of-support dates.

---

## 85. Version negotiation

The Provider must negotiate mutually supported protocol versions without unsafe downgrade.

It must not silently interpret a newer object using older incompatible semantics.

---

## 86. Deprecation

Before ending support for a Relay version, the Provider should:

- publish notice;
- provide migration guidance;
- maintain export access;
- identify affected schemas and Applications;
- provide a reasonable transition path.

---

## 87. Backward preservation

Ending active support for an old schema or protocol version must not justify deleting valid user records.

The Provider should preserve or export them even where it can no longer fully operate them.

---

## 88. Extension behaviour

Provider-specific extensions must be:

- namespaced;
- documented;
- optional where possible;
- preserved during export;
- distinguishable from core Relay behaviour.

A Provider must not call a proprietary extension part of Relay core.

---

# Part XIII — Conformance and Audit

## 89. Conformance suite

A Provider claiming Relay compliance must run or submit to the relevant conformance suite.

Tests may include:

- identifier preservation;
- unknown schema preservation;
- record round-trip;
- commit verification;
- export completeness;
- migration;
- revocation enforcement;
- event-gap recovery;
- fork detection;
- application replacement;
- source-token invalidation.

---

## 90. Test environment

Providers should expose a test or sandbox environment where practical.

The test environment should support:

- disposable identities;
- test migrations;
- test Applications;
- test events;
- failure simulation;
- schema fixtures.

Sandbox behaviour must not be represented as proof that production is compliant without production-relevant validation.

---

## 91. Conformance report

A conformance report should identify:

- Provider;
- manifest version;
- tested Relay version;
- tested profiles;
- test-suite version;
- pass and failure results;
- test date;
- tester;
- known limitations;
- certification status.

---

## 92. Continuous compliance

Passing one test does not guarantee permanent compliance.

Material changes may require retesting, including:

- repository-engine replacement;
- migration-flow changes;
- authorisation redesign;
- key-management changes;
- new private-data processing;
- manifest-role expansion;
- major protocol upgrade.

---

## 93. Audit evidence

A Provider may support independent audit through:

- signed manifests;
- migration receipts;
- verification receipts;
- export samples;
- conformance logs;
- security reports;
- incident history;
- availability history.

Sensitive customer data must not be exposed merely for audit.

---

## 94. False compliance claims

An operator must not claim full Relay compliance when it supports only selected features.

For example:

```text
Supports Relay record import
```

is not equivalent to:

```text
Relay-compatible Provider
```

Compliance claims must identify the relevant profile and level.

---

# Part XIV — Provider User Experience Requirements

## 95. Clear ownership language

The Provider interface should accurately explain that:

- the Provider hosts the Relay;
- the Controller retains the Relay Identity;
- Applications receive limited access;
- migration is available;
- Provider-issued handles may not be permanent;
- public visibility does not equal unlimited usage permission.

---

## 96. Connected-service dashboard

A Full Relay Provider should offer a user-accessible view of:

- Relay Identifier;
- current handles;
- current Provider services;
- connected Applications;
- Permission Grants;
- event subscriptions;
- recovery authorities;
- backups;
- mirrors;
- exports;
- migration status;
- recent high-authority activity.

---

## 97. Export interface

The export interface should state:

- export scope;
- included records;
- included blobs;
- Repository Head;
- encryption status;
- verification method;
- whether the export is complete.

---

## 98. Migration interface

The migration interface should show:

- source and destination;
- compatibility;
- unsupported records;
- data size;
- private-data handling;
- expected service interruption;
- application continuity;
- residual source-data policy;
- activation step.

---

## 99. Suspension interface

Where a service is suspended, the Provider should state:

- which service is suspended;
- whether the identity remains active;
- whether export is available;
- whether migration is available;
- whether appeal is available;
- whether any legal restrictions apply.

---

# Part XV — Required Provider Operations

## 100. Required Full Relay Provider operations

A compliant Full Relay Provider must support operations equivalent to:

```text
Create Relay Identity
Publish Identity Document
Read Identity Document
Update service descriptors
Create repository
Read Repository Head
Submit authorised commit
Verify commit
Read record
Create record
Update record
Delete record
Preserve unknown record
Upload blob
Retrieve blob
Issue Permission Grant
Issue short-lived access token
Revoke Permission Grant
List connected Applications
Create event subscription
Read events after cursor
Report event gap
Create complete export
Verify export
Initiate migration
Transfer repository
Transfer blobs
Synchronise final commits
Activate destination
Deactivate source writes
Publish migration notice
Produce Migration Receipt
Create recovery export
Restore recovery export
Report service status
Publish Provider Manifest
```

A specialised Provider profile is responsible only for the operations relevant to that profile.

---

# Part XVI — Provider Invariants

## 101. Provider compliance invariants

The following rules must always remain true.

### Invariant 1

Hosting a Relay Identity does not give the Provider ownership of it.

### Invariant 2

A Controller can replace the Provider without changing the Relay Identifier.

### Invariant 3

Migration does not change Repository Identifiers or Record URIs.

### Invariant 4

The Provider does not become the sole root authority by default.

### Invariant 5

Only authorised commits alter canonical repository state.

### Invariant 6

Unknown valid schemas and extensions survive storage, export and migration.

### Invariant 7

A standard export is independently readable and verifiable.

### Invariant 8

An export alone is not represented as completed operational migration.

### Invariant 9

The Provider stops canonical writes after migration cutover.

### Invariant 10

Provider-specific tokens do not constitute portable identity authority.

### Invariant 11

Revoking an Application stops future access but does not delete its previous canonical records.

### Invariant 12

First-party Applications remain distinguishable from Provider infrastructure.

### Invariant 13

Private hosting access does not authorise unrelated indexing, advertising or model training.

### Invariant 14

A Provider policy decision must not be misrepresented as protocol invalidity.

### Invariant 15

A suspended hosting service does not automatically terminate the Relay Identity.

### Invariant 16

Independent tools can verify the Provider’s repository and export claims.

### Invariant 17

A Backup or Mirror does not become canonical without valid activation authority.

### Invariant 18

A Provider must disclose incomplete, lost or unsupported migration data.

### Invariant 19

Provider-only encryption must not make lawful migration unusable.

### Invariant 20

Compliance claims identify their exact profile and validation level.

---

# Part XVII — Compliance Scenario

## 102. Provider compliance test

Provider Alpha claims compliance as a Full Relay Provider.

### Identity creation

Alice creates:

```text
Relay Identifier:
rid:relay:alice
```

The identifier does not contain Provider Alpha’s domain.

Alice’s Identity Document includes Provider Alpha’s service endpoints and a Provider-independent recovery authority.

### Record creation

Alice connects Application X.

Application X receives permission to create posts.

It creates:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

Provider Alpha accepts the change through a signed commit.

### Unknown schema

Application Y creates:

```text
com.example.design.canvas.v1
```

Provider Alpha cannot render the format but stores and preserves it.

### Export

Alice requests a complete export.

The export includes:

- identity metadata;
- current Repository Head;
- commits;
- records;
- unknown design record;
- blobs;
- schemas;
- verification information.

An independent tool verifies the export.

### Application revocation

Alice revokes Application X.

Provider Alpha stops:

- token renewal;
- repository writes under the grant;
- protected event delivery.

The existing post remains in Alice’s repository.

### Application replacement

Application Z receives permission to read and update posts.

It edits the post originally created through Application X.

### Migration

Alice selects Provider Beta.

Provider Alpha:

- creates a Migration Snapshot;
- transfers records and blobs;
- provides incremental commits;
- enters a short write freeze;
- agrees on the final Repository Head;
- stops canonical writes after cutover;
- publishes a signed migration notice.

Provider Beta verifies the repository and becomes active.

Alice retains:

- the same Relay Identifier;
- the same Repository Identifier;
- the same Record URIs;
- the same supported relationships;
- the unknown design record.

### Residual data

Provider Alpha discloses that encrypted backup copies will remain for 30 days before deletion.

After the period, it issues deletion confirmation.

### Independent test

A conformance suite verifies:

- stable identifiers;
- unknown schema preservation;
- export integrity;
- revocation;
- application replacement;
- migration;
- source-write deactivation.

If all these behaviours are observed, Provider Alpha satisfies the Full Relay Provider compliance objective.

---

# Part XVIII — Non-Compliant Examples

## 103. Download-only portability

A service offers a ZIP file of posts and images but:

- does not preserve Record URIs;
- does not export commit history;
- cannot move application grants;
- cannot resume as the same identity elsewhere.

This is data export, not Relay migration compliance.

---

## 104. Provider-owned identity

A service uses:

```text
alice@provider.example
```

as the permanent identity and cannot resolve Alice after she leaves.

This is not identity portability.

---

## 105. Proprietary-record loss

A Provider exports known records but silently omits unknown application schemas.

This is not repository compliance.

---

## 106. First-party lock-in

A Provider claims Relay support but allows only its own Application to create or update records.

This is not application-access compliance.

---

## 107. Hidden AI processing

A Provider uses private hosted records for general model training without a separate declared role and valid authority.

This violates role and permission compliance.

---

## 108. Migration without cutover integrity

A Provider copies repository files to a destination but continues accepting writes at both locations without fork controls.

This is not compliant migration.

---

## 109. Unverifiable export

A Provider exports data without hashes, commits or a declared Repository Head and requires the Provider’s own software to interpret it.

This is not independent export compliance.

---

# Part XIX — Open Design Questions

## 110. Minimum compliance profile

Which service set must be implemented before an operator may use the unqualified term:

```text
Relay Provider
```

rather than a specialised profile name?

---

## 111. Mandatory recovery independence

Should every Full Relay Provider be required to support a Provider-independent recovery authority from account creation?

---

## 112. Export timing

Should v0.1 specify maximum time limits for generating ordinary and very large exports?

---

## 113. Migration pricing

What rules distinguish reasonable transfer costs from anti-competitive migration penalties?

---

## 114. Event retention

What minimum event-retention periods should apply to:

- public events;
- application events;
- security events;
- migration events?

---

## 115. History retention

What minimum commit and tombstone history must a Provider retain to claim full repository compliance?

---

## 116. Private encryption

Which encryption and key-portability model should be mandatory for restricted and private records?

---

## 117. Provider transparency

Which metrics should Providers publish, such as:

- uptime;
- export success;
- migration success;
- data-loss incidents;
- unresolved forks;
- security incidents?

---

## 118. Certification governance

Who may certify Providers, and how can certification avoid becoming a commercial gatekeeper?

---

## 119. First-party advantages

Which Provider-only operational capabilities are legitimate, and which create unfair application lock-in?

---

## 120. Suspension portability

What minimum export and migration access should remain available during:

- policy suspension;
- billing suspension;
- security suspension;
- legal restriction?

---

## 121. Jurisdiction disclosure

How detailed must a Provider’s data-location and jurisdiction disclosure be?

---

## 122. Source-code requirements

Should Relay compliance require open-source Provider software, or is open protocol behaviour and conformance sufficient?

Relay v0.1 currently assumes open source is desirable but not mandatory for compliance.

---

# Part XX — Provisional Decisions for v0.1

## 123. Provisional provider decisions

Relay v0.1 will provisionally assume:

- compliance is profile-based;
- a Full Relay Provider operates identity, repository, authorisation, events, blobs, export and migration;
- Providers publish signed manifests;
- Relay Identifiers remain Provider-independent;
- Controllers retain a Provider-independent identity authority path;
- Providers preserve unknown schemas and extensions;
- standard exports are complete, documented and independently verifiable;
- operational migration is required for Full Provider compliance;
- a short write freeze is acceptable during cutover;
- source Providers stop canonical writes after activation;
- third-party Applications may request access through documented interfaces;
- first-party Applications remain subject to the Permission Model;
- revocation is enforced promptly;
- cursor-based incremental synchronisation is required;
- private and restricted event delivery stops after revocation;
- Providers disclose retention, residual copies and legal restrictions;
- Provider suspension remains distinct from identity termination;
- conformance claims identify the tested profile and level;
- independent verification is required for higher compliance labels;
- open-source implementation is not mandatory, but open formats and interoperable behaviour are;
- detailed certification and time-based service thresholds will be defined in the Conformance Testing Model.

---

## 124. Core Provider principle

The Provider Compliance Model can be reduced to one rule:

> A Provider may charge for operating a Relay, secure it, support it and enforce lawful hosting rules, but it cannot make itself technically indispensable to the identity it serves.

The next core object is the **Relay Application Compliance Model**: the minimum obligations an Application must satisfy when reading, creating, displaying, transforming or synchronising Relay Records under user authority.