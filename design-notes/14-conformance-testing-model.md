# Relay Protocol v0.1  
## Core Object 14: Conformance Testing Model

### 1. Definition

**Relay Conformance Testing** is the process of verifying that an implementation behaves according to the observable requirements of the Relay Protocol.

Conformance testing applies to roles such as:

- Relay Providers;
- Repository Services;
- Authorisation Services;
- Applications and Clients;
- Resolvers;
- Migration Services;
- Backup Providers;
- Mirrors;
- Independent Verifiers;
- Schema Registries;
- Event Services.

An implementation is conformant only to the specific:

- Relay version;
- role;
- compliance profile;
- capability set;
- test-suite version;

that it has successfully completed.

A service that passes one profile must not imply that every part of its system is Relay-compliant.

The central rule is:

> Relay compatibility must be demonstrated through interoperable behaviour, not declared through branding.

---

## 2. Purpose

The Conformance Testing Model exists to make claims such as:

```text
Relay-compatible
```

technically meaningful.

Without conformance testing, an operator could claim Relay support while:

- changing identifiers during migration;
- stripping unknown fields;
- supporting export but not operational portability;
- accepting invalid commits;
- failing to enforce revocation;
- supporting only its own Applications;
- serving unverifiable resolution results;
- recreating lock-in through undocumented extensions.

Conformance testing must establish whether independent implementations can interact without relying on private agreements or shared internal systems.

---

## 3. What conformance means

Conformance means that an implementation satisfies the requirements of a declared profile under defined test conditions.

It does not necessarily mean that the implementation is:

- secure against every attack;
- legally compliant in every jurisdiction;
- highly available;
- well designed;
- trustworthy;
- financially stable;
- free of defects;
- suitable for every user.

Conformance is narrower.

It establishes that the implementation follows specified protocol behaviour.

---

## 4. Conformance claim structure

Every conformance claim should identify:

```text
Relay version
Role
Profile
Test-suite version
Validation level
Date tested
Known limitations
```

Example:

```text
Relay Protocol: v0.1
Role: Repository Provider
Profile: Repository Core
Test Suite: 0.1.4
Validation: Independently verified
Tested: 2026-08-25
Limitations: Private encrypted records not supported
```

The unqualified statement:

```text
Fully Relay compliant
```

should be avoided unless a governance-approved full profile exists and has been passed.

---

# Part I — Conformance Profiles

## 5. Profile-based testing

Relay conformance is profile-based.

Each profile defines:

- required capabilities;
- optional capabilities;
- prohibited behaviour;
- test scenarios;
- pass criteria;
- evidence requirements.

An implementation may pass several profiles.

---

## 6. Core profile categories

Relay v0.1 may define the following profile categories:

### Identity profiles

- Identity Resolution Core
- Identity Hosting Core
- Identity Recovery
- Handle Verification

### Repository profiles

- Repository Read
- Repository Write
- Repository Verification
- Repository Export
- Repository Migration

### Application profiles

- Read-only Client
- Editing Client
- Publishing Client
- Local-first Client
- AI Client
- Automation Client

### Service profiles

- Authorisation Service
- Event Service
- Blob Service
- Resolver
- Backup Provider
- Mirror
- Migration Service
- Independent Verifier

### Combined profiles

- Full Relay Provider
- Full Relay Client

---

## 7. Minimum core profiles

The first Relay reference implementation should prioritise the following profiles:

```text
Identity Resolution Core
Repository Core
Application Authorisation Core
Repository Export
Repository Migration
Read-only Client
Editing Client
Event Synchronisation Core
Independent Verification
```

These profiles are sufficient to test the central Relay promise:

> Identity, records, relationships and application continuity survive replacement of both Provider and Application.

---

## 8. Profile dependencies

Some profiles depend on others.

For example:

```text
Repository Migration
requires:
- Repository Core
- Repository Export
- Repository Verification
- Identity Resolution Core
```

A Provider cannot claim migration conformance while failing repository-verification requirements.

Profile dependencies must be machine-readable where possible.

---

# Part II — Validation Levels

## 9. Self-tested

The operator runs the official conformance suite and publishes the results.

Self-testing is useful for:

- development;
- open-source projects;
- early implementations;
- continuous integration.

It does not constitute independent verification.

---

## 10. Test-validated

The implementation passes the official automated suite in a reproducible environment.

Evidence may include:

- test logs;
- signed test report;
- implementation version;
- deployment fingerprint;
- test fixture versions.

---

## 11. Independently verified

A separate authorised or recognised tester performs the conformance tests.

The tester should not be controlled by the implementation operator.

The report must identify:

- test environment;
- production or staging target;
- limitations;
- failures;
- retests;
- scope.

---

## 12. Certified

Certification may include:

- automated conformance;
- independent testing;
- operational evidence;
- security controls;
- migration demonstration;
- ongoing compliance obligations.

Certification is broader than protocol conformance and may be introduced through governance.

A certification mark must not conceal the exact profiles tested.

---

## 13. Continuous validation

Conformance may change after:

- software updates;
- infrastructure changes;
- new Provider policies;
- key-management redesign;
- migration changes;
- API changes;
- schema changes;
- role expansion.

Implementations should run automated conformance continuously where practical.

---

# Part III — Test Architecture

## 14. Conformance test suite

The official Relay Conformance Suite should include:

- automated protocol tests;
- interoperability fixtures;
- reference identities;
- reference repositories;
- invalid test cases;
- migration scenarios;
- failure simulations;
- security-boundary tests;
- round-trip tests;
- manual review checklists.

---

## 15. Black-box testing

The primary conformance suite should test observable behaviour through public protocol interfaces.

A tester should not require:

- source-code access;
- database access;
- Provider-admin access;
- knowledge of internal architecture.

This allows proprietary and open-source implementations to be tested under the same behavioural standard.

---

## 16. White-box testing

Some certification levels may include optional white-box assessment of:

- key handling;
- internal role separation;
- data retention;
- access controls;
- administrative tooling;
- incident processes.

White-box review is not required for basic protocol conformance unless the profile specifically includes it.

---

## 17. Reference implementation

Relay should maintain at least one reference implementation.

The reference implementation serves as:

- executable specification aid;
- test harness target;
- example implementation;
- interoperability baseline.

It must not become the only implementation against which others can work.

Conformance is determined by the specification and official tests, not by reproducing every internal choice of the reference server.

---

## 18. Test harness

The test harness should be able to act as:

- Controller;
- Relay Identity;
- Application;
- source Provider;
- destination Provider;
- Resolver;
- event subscriber;
- verifier;
- malicious or faulty peer.

This allows controlled interoperability testing.

---

## 19. Test isolation

Tests should use disposable:

- identities;
- repositories;
- Applications;
- handles;
- keys;
- Permission Grants;
- event subscriptions;
- blobs.

Conformance testing must not risk real user data.

---

## 20. Reproducibility

A test result should be reproducible from:

- implementation version;
- test-suite version;
- profile;
- configuration;
- fixture set;
- environment assumptions.

A report should identify any non-standard configuration used to pass.

---

# Part IV — Identity Conformance Tests

## 21. Stable identifier test

The implementation creates a Relay Identity.

The test then changes:

- handle;
- Provider;
- service endpoint;
- signing key.

The Relay Identifier must remain unchanged.

---

## 22. Handle resolution test

The test:

1. creates a verified handle;
2. resolves it to a Relay Identifier;
3. retrieves the Identity Document;
4. verifies bidirectional binding.

The implementation must not treat the handle as the identity itself.

---

## 23. Handle reassignment test

A handle is released from Identity A and assigned to Identity B.

The implementation must ensure that:

- historical records remain linked to Identity A;
- relationships do not transfer;
- credentials do not transfer;
- cached resolution refreshes;
- Identity B does not inherit continuity.

---

## 24. Identity Document chain test

The test publishes several Identity Document versions.

The implementation must verify:

- signatures;
- predecessor references;
- key validity;
- current version;
- service descriptors.

A forged higher version must not override a valid chain.

---

## 25. Provider disappearance test

The active Provider becomes unavailable.

Using valid independent authority, the test publishes a replacement Identity Document.

Resolvers must return the new Provider without requiring cooperation from the unavailable Provider.

---

## 26. Identity fork test

Two Identity Documents are published from the same predecessor.

The implementation must:

- detect the conflict;
- avoid silently choosing one;
- expose a resolution-conflict state;
- restrict high-authority actions where required.

---

# Part V — Repository Conformance Tests

## 27. Repository creation test

The implementation creates:

- Repository Identifier;
- Genesis Commit;
- initial Repository Head;
- association with the Relay Identity.

All identifiers and signatures must verify.

---

## 28. Record lifecycle test

The test performs:

```text
create
read
update
delete
restore
```

The implementation must preserve:

- stable Record URI;
- version history;
- commit references;
- tombstone requirements;
- authority evidence.

---

## 29. Stale update test

Two Applications read version 3.

Application A successfully writes version 4.

Application B then attempts an update against version 3.

The implementation must:

- reject the stale update;
- or enter explicit conflict resolution.

It must not silently overwrite version 4.

---

## 30. Atomic commit test

A commit contains several operations.

One operation is invalid.

The implementation must reject the entire commit.

No partial canonical state may remain.

---

## 31. Invalid signature test

The test submits a commit with:

- altered content;
- wrong key;
- revoked key;
- invalid signature.

The implementation must reject it without advancing the Repository Head.

---

## 32. Unknown schema preservation test

The test stores a valid record under an unknown schema.

The Provider then:

- exports it;
- imports it;
- migrates it;
- serves it again.

The record must retain:

- Record URI;
- schema;
- content;
- extensions;
- blobs;
- provenance;
- visibility.

---

## 33. Unknown field round-trip test

A supported record contains unknown namespaced extensions.

A Client updates one supported field.

The unknown extensions must survive unchanged unless separately modified with authority.

---

## 34. Deletion integrity test

The test deletes a record and requests content erasure.

The implementation must:

- stop serving active content;
- retain required tombstone metadata;
- preserve record identifier non-reuse;
- retain verification evidence according to profile.

---

## 35. Fork-detection test

Two commits are submitted with the same predecessor.

The system must detect the fork and must not present both branches as one linear canonical history.

---

## 36. Resolution Commit test

A Controller issues a valid Resolution Commit.

The implementation must:

- designate the resolved canonical branch;
- preserve fork evidence;
- reject further use of the invalid branch;
- resume canonical commits from the resolved state.

---

# Part VI — Application and Permission Tests

## 37. Permission minimisation test

An Application requests several scopes.

The user approves only a subset.

The issued grant and access token must include only approved capabilities.

---

## 38. Unauthorised action test

An Application has:

```text
read
create
```

but not:

```text
delete
```

A deletion request must fail.

The failure must not alter canonical state.

---

## 39. Permission-expansion test

An Application attempts to expand its own grant.

The system must reject the attempt.

---

## 40. Revocation test

A grant is revoked.

The test verifies that:

- new tokens are refused;
- refresh fails;
- delegated keys fail;
- protected events stop;
- repository writes fail;
- existing records remain.

---

## 41. Manifest-change test

An Application changes from:

```text
AI inference only
```

to:

```text
general model training
```

Existing grants must not silently expand.

Re-authorisation must be required.

---

## 42. Application replacement test

Application A creates and updates a record.

Application B then connects independently and:

- reads the record;
- edits a supported field;
- preserves extensions;
- retains Record URI;
- continues event synchronisation.

Application A must not be required.

---

## 43. Canonical Record Rule test

A test feature creates material user content.

The tester compares:

- user-visible feature state;
- canonical Relay records;
- portable extensions;
- local state disclosures.

The Application fails if material work is silently held only in an inaccessible internal database while the feature is represented as portable.

---

## 44. Local-save status test

The Application loses network access.

The user edits a record.

The interface must not represent the change as canonical until repository acceptance occurs.

---

## 45. Application shutdown test

The Application is disabled or removed.

The test confirms that:

- canonical records remain accessible;
- extension schemas remain resolvable or bundled;
- grants can be revoked;
- another Application can continue supported operations.

---

# Part VII — Migration Tests

## 46. Full migration test

The test creates an identity and repository at Provider A.

It then migrates to Provider B while preserving:

- Relay Identifier;
- Repository Identifier;
- Record URIs;
- commit history;
- Repository Head;
- supported grants;
- relationships;
- unknown schemas;
- blobs.

---

## 47. Incremental migration test

The repository continues receiving valid commits after the initial snapshot.

The migration must:

- transfer the snapshot;
- transfer later commits;
- perform final synchronisation;
- agree on one final Repository Head;
- avoid missing changes.

---

## 48. Write-freeze test

During cutover, Provider A enters a controlled write freeze.

The test verifies that:

- no untracked source writes occur;
- Provider B does not accept canonical writes before activation;
- queued writes are handled explicitly.

---

## 49. Source deactivation test

After cutover:

- Provider A must stop accepting canonical writes;
- source tokens must fail for writes;
- Provider A may expose signed migration information;
- Provider B must be current through resolution.

---

## 50. Migration integrity test

Provider B must independently verify:

- Identity Document chain;
- commit chain;
- state root;
- records;
- tombstones;
- blobs;
- final Repository Head.

Activation must fail if critical verification fails.

---

## 51. Unknown schema migration test

Provider A stores records unknown to Provider B.

Provider B must preserve them even if it cannot render them.

---

## 52. Failed migration test

A blob or commit is corrupted during transfer.

The destination must:

- detect the failure;
- refuse activation;
- preserve the source as authoritative;
- report the precise failure.

---

## 53. Emergency migration test

Provider A becomes unavailable.

The test restores from a recovery export at an older verified head.

Provider B must:

- preserve the Relay Identifier;
- disclose the recovered head;
- disclose missing commit range;
- publish a valid recovery Identity Document.

---

## 54. Split-brain test

Provider A and Provider B both accept conflicting commits.

The implementation must:

- detect the fork;
- suspend ordinary linear synchronisation;
- require explicit resolution;
- preserve branch evidence.

---

# Part VIII — Event and Synchronisation Tests

## 55. Stable event identity test

A delivery attempt fails and is retried.

The Event Identifier must remain unchanged.

---

## 56. Duplicate delivery test

The same event is delivered more than once.

The receiving Client must process it idempotently.

---

## 57. Cursor-resumption test

The subscriber disconnects after cursor 20.

On reconnection it requests events after cursor 20.

The Provider must return the correct ordered continuation.

---

## 58. Gap-detection test

The requested cursor has expired from retention.

The Provider must report a gap and provide a canonical resynchronisation path.

It must not imply continuity where events are missing.

---

## 59. Canonical backfill test

After an event gap, the Client retrieves a snapshot or commits and reaches the current verified Repository Head.

---

## 60. Revoked-subscription test

An Application’s grant is revoked.

Protected event delivery must stop.

Historical replay under the revoked grant must be denied.

---

## 61. Migration stream-boundary test

After migration:

- the source exposes a final boundary;
- the destination begins from the migrated head;
- historical events are not presented as new activity;
- the Client can resume without duplication or gap.

---

# Part IX — Resolver Tests

## 62. Resolver independence test

The Resolver returns:

- Identity Document;
- verification chain;
- service descriptors.

The Client must be able to verify the result without trusting the Resolver operator blindly.

---

## 63. Stale resolver test

Resolver A returns an older Provider location.

The Client retrieves newer valid identity evidence and must reject the stale result.

---

## 64. Resolver disagreement test

Two Resolvers return incompatible current documents.

The Client must detect the conflict rather than selecting one arbitrarily.

---

## 65. Record URI resolution test

The test resolves a Record URI after Provider migration.

The same Record URI must retrieve the record from the new Provider.

---

## 66. Read-only mirror test

A Resolver returns both:

- canonical write Provider;
- read-only Mirror.

The Client must not submit canonical writes to the Mirror.

---

# Part X — Blob Tests

## 67. Blob-integrity test

A blob is transferred.

The receiver must verify its declared cryptographic hash.

---

## 68. Blob-location test

The blob moves to a new storage endpoint.

The Blob Identifier and referencing Record URI remain unchanged.

---

## 69. Restricted-blob test

A restricted blob URL becomes known to an unauthorised Client.

The Client must still be denied access.

Knowledge of the storage URL is not authority.

---

## 70. Blob deletion test

A blob referenced by two records must not be physically deleted while one valid reference remains.

---

## 71. Provider-only encryption test

A migration must fail conformance if the destination receives encrypted content that only the source Provider can decrypt and no valid portable decryption path exists.

---

# Part XI — Schema Tests

## 72. Schema immutability test

A published schema revision is retrieved twice.

The same identifier and revision must not resolve to materially different signed definitions.

---

## 73. Historical-schema validation test

A record created under schema revision 1 must remain valid after revision 2 is published.

---

## 74. Schema disappearance test

The original Schema Publisher becomes unavailable.

The record must remain verifiable using:

- bundled schema copy;
- registry mirror;
- content-addressed schema;
- another valid preservation path.

---

## 75. Lossy conversion test

A conversion removes fields.

The implementation must disclose:

- omitted fields;
- information loss;
- source record;
- conversion tool;
- user approval.

---

## 76. Translation provenance test

A record translated between schemas must preserve source provenance and must not be represented as the original unmodified record.

---

# Part XII — Security-Boundary Tests

## 77. Role-separation test

A company operates both Provider and Application.

The test verifies that Provider hosting access does not silently grant the Application private-data access.

---

## 78. Root-authority separation test

An ordinary Application token attempts to:

- migrate the identity;
- rotate root keys;
- change recovery authority.

All attempts must fail.

---

## 79. Compromised installation test

One Application installation is revoked.

Other installations may remain active if separately authorised.

Root identity authority must remain unaffected.

---

## 80. Replay-attack test

A previously valid authorisation message, event or token is replayed outside its valid context.

The implementation must reject or safely deduplicate it.

---

## 81. Downgrade test

A malicious peer attempts to force an older insecure Relay version.

The implementation must enforce minimum supported security policy.

---

## 82. Callback-substitution test

An authorisation code is redirected to an unregistered callback.

The Authorisation Service must reject the flow.

---

# Part XIII — Failure and Adversarial Testing

## 83. Fault injection

The conformance suite should simulate:

- network interruption;
- duplicate messages;
- delayed events;
- stale caches;
- corrupted blobs;
- missing commits;
- Provider outage;
- Resolver disagreement;
- clock drift;
- revoked keys;
- partial migration;
- storage exhaustion.

Relay compliance must include correct failure behaviour, not only ideal-path success.

---

## 84. Malicious Provider simulation

The test harness may simulate a Provider that:

- serves different heads;
- strips unknown records;
- delays migration;
- returns stale Identity Documents;
- continues writing after cutover.

Clients and verifiers should detect the relevant failures where the protocol provides evidence.

---

## 85. Malicious Application simulation

The test harness may simulate an Application that:

- requests broad permissions;
- attempts undeclared actions;
- strips fields;
- reuses revoked tokens;
- submits stale writes;
- performs background activity without authority.

Providers must reject invalid operations.

---

## 86. Malicious Resolver simulation

A Resolver may return:

- forged documents;
- stale documents;
- false Provider endpoints;
- downgraded protocol versions.

Clients must verify the returned evidence.

---

## 87. Partial-support testing

An implementation that claims preserve-only support must be tested differently from one claiming full editing support.

The suite should not penalise honest limited support.

It should penalise misrepresentation.

---

# Part XIV — Test Evidence

## 88. Machine-readable report

The conformance suite should produce a machine-readable report containing:

```json
{
  "relayVersion": "0.1",
  "profile": "repository-core",
  "suiteVersion": "0.1.4",
  "implementation": "Provider Alpha 2.3.1",
  "result": "pass",
  "testsPassed": 112,
  "testsFailed": 0,
  "testsSkipped": 4,
  "limitations": [
    "private-encrypted-record profile not tested"
  ],
  "testedAt": "2026-08-25T10:00:00Z"
}
```

---

## 89. Human-readable report

The report should explain:

- what was tested;
- what passed;
- what failed;
- what was not tested;
- whether production behaviour may differ;
- known limitations;
- retest requirements.

---

## 90. Signed test result

A conformance result may be signed by:

- the implementation operator;
- the independent tester;
- the certification authority;
- the test harness.

The signature proves attribution of the report.

It does not guarantee future compliance.

---

## 91. Public result registry

Relay governance may maintain a public registry of conformance results.

The registry may list:

- actor;
- role;
- profile;
- Relay version;
- test date;
- result;
- report;
- expiry or retest date;
- certification status.

The registry must not become the only way to run or verify tests.

---

## 92. Expiring conformance status

A conformance result may expire after:

- a defined period;
- major implementation change;
- protocol update;
- security incident;
- failed surveillance test;
- material role change.

Expired status does not mean automatic non-compliance.

It means the prior evidence is no longer current enough.

---

# Part XV — Interoperability Events

## 93. Plugfest

Relay governance may coordinate interoperability events where independent implementations test against one another.

Possible scenarios include:

- cross-Provider migration;
- cross-Application editing;
- resolver disagreement;
- event resumption;
- unknown schema preservation;
- emergency recovery.

These events help identify ambiguities that isolated conformance tests may miss.

---

## 94. Pairwise interoperability

Two implementations may both pass the same test suite but still expose an ambiguity.

Pairwise tests should confirm that:

- Provider A can migrate to Provider B;
- Application A can edit records created by Application B;
- Resolver A and Resolver B agree on valid identity state;
- Verifier A can verify Provider B’s export.

---

## 95. Implementation diversity

The ecosystem should test implementations built with different:

- programming languages;
- databases;
- cryptographic libraries;
- hosting models;
- operating systems;
- organisational structures.

A protocol that works only between clones of one codebase is not genuinely interoperable.

---

# Part XVI — Certification Marks and Claims

## 96. Conformance badge

A Provider or Application may display a conformance badge only for the exact tested profile.

Example:

```text
Relay v0.1
Editing Client
Independently Verified
```

The badge should link to or reference the test report.

---

## 97. No blanket trust badge

Relay should avoid vague labels such as:

```text
Safe
Trusted
Approved
Official
```

unless the exact criteria are defined.

Protocol conformance does not equal general trustworthiness.

---

## 98. False claims

An implementation making materially false conformance claims may face:

- removal from official directories;
- revoked certification;
- public correction;
- retesting requirement;
- governance action.

This does not terminate user identities hosted by the implementation.

---

# Part XVII — Conformance Lifecycle

## 99. Initial validation

An implementation completes testing before making a formal compliance claim.

---

## 100. Routine retesting

Retesting may occur:

- on a schedule;
- after major releases;
- after material infrastructure changes;
- after security incidents;
- after failed interoperability reports.

---

## 101. Regression testing

Every bug fix or feature change should run the relevant automated tests.

A previously passed requirement must not regress silently.

---

## 102. Surveillance testing

Certification programmes may perform periodic limited tests against production behaviour.

Examples include:

- export verification;
- migration initiation;
- resolver correctness;
- manifest validity;
- revocation enforcement.

Surveillance tests must avoid real user data.

---

## 103. Incident-triggered review

A serious incident may trigger:

- focused retesting;
- temporary certification suspension;
- public status update;
- remediation deadline.

The review should remain limited to the affected profiles unless broader risk is established.

---

## 104. Conformance withdrawal

An operator may voluntarily withdraw a claim.

The operator should:

- update its manifest;
- stop displaying the badge;
- disclose affected profiles;
- preserve user migration rights.

---

# Part XVIII — Reference Compliance Scenarios

## 105. End-to-end continuity test

The strongest Relay v0.1 conformance scenario should test the complete continuity promise.

### Initial state

Alice creates a Relay Identity at Provider A.

She connects Application A.

Application A creates:

- profile;
- article;
- follow relationship;
- application-specific extension;
- media blob.

### Application replacement

Alice connects Application B.

Application B:

- reads the same profile;
- edits the article;
- preserves the unknown extension;
- continues the relationship;
- resolves the same blob.

### Revocation

Alice revokes Application A.

Application A loses future authority.

All canonical records remain.

### Provider migration

Alice migrates to Provider B.

The test verifies:

- same Relay Identifier;
- same Repository Identifier;
- same Record URIs;
- same relationship targets;
- same commit history;
- same unknown extension;
- verified blob integrity;
- successful Application B reconnection.

### Resolver refresh

A stale Resolver returns Provider A.

The Client detects a newer valid Identity Document and moves to Provider B.

### Event resumption

Application B resumes after the migration event boundary without duplication or gap.

If this complete scenario succeeds between independently implemented systems, the core Relay proposition has been demonstrated.

---

## 106. Provider-failure continuity test

Provider A becomes unavailable without cooperation.

Alice restores from a valid recovery export to Provider B.

The test verifies:

- identity continuity;
- recoverable repository state;
- accurate disclosure of missing commits;
- new Identity Document publication;
- Application reconnection.

---

## 107. Application-failure continuity test

Application A disappears.

The test verifies:

- schema availability;
- record availability;
- extension preservation;
- grant revocation;
- replacement Application access.

---

# Part XIX — Required v0.1 Test Assets

## 108. Required fixtures

Relay v0.1 should publish fixtures for:

- Identity Documents;
- valid and invalid commits;
- common record schemas;
- unknown extension records;
- tombstones;
- migration packages;
- Permission Grants;
- revocation records;
- events;
- repository forks;
- schema versions;
- blobs;
- recovery exports.

---

## 109. Reference actors

The test harness should include reference implementations of:

- Controller;
- Application;
- source Provider;
- destination Provider;
- Resolver;
- Verifier;
- event subscriber;
- malicious peer.

---

## 110. Public test repository

Relay should maintain a repository containing:

- conformance suite;
- fixtures;
- profile definitions;
- expected results;
- issue tracker;
- test proposals;
- version history.

The test suite should be openly reviewable.

---

# Part XX — Conformance Invariants

## 111. Conformance invariants

The following rules must always remain true.

### Invariant 1

A conformance claim applies only to the specified role, profile and Relay version.

### Invariant 2

Self-declaration is not equivalent to independent verification.

### Invariant 3

Observable behaviour takes precedence over marketing language.

### Invariant 4

Passing one profile does not imply passing unrelated profiles.

### Invariant 5

Unknown schema preservation must be tested through actual round trips.

### Invariant 6

Migration conformance requires operational continuity, not only data download.

### Invariant 7

Application conformance requires correct revocation and replacement behaviour.

### Invariant 8

Resolver conformance requires independently verifiable output.

### Invariant 9

Failure behaviour is part of conformance.

### Invariant 10

A conformance report must disclose skipped and unsupported requirements.

### Invariant 11

Material implementation changes may invalidate earlier results.

### Invariant 12

The reference implementation does not define conformance beyond the specification.

### Invariant 13

Certification does not confer ownership or authority over user identities.

### Invariant 14

Conformance tests must not require access to real user data.

### Invariant 15

False compliance claims must be correctable without harming hosted identities.

---

# Part XXI — Open Design Questions

## 112. Profile boundaries

What exact capabilities define:

- Repository Core;
- Editing Client;
- Full Relay Provider;
- Full Relay Client?

---

## 113. Mandatory production testing

Which tests may run only in a sandbox, and which must be demonstrated against production behaviour?

---

## 114. Certification authority

Should certification be performed by:

- one foundation;
- multiple accredited testers;
- community review;
- automated public infrastructure;
- a combination?

---

## 115. Conformance expiry

How long should test results remain current before retesting is required?

---

## 116. Privacy review

Should Full Relay Provider certification include privacy and role-separation review beyond black-box protocol tests?

---

## 117. Security review

Which profiles require penetration testing or cryptographic implementation review?

---

## 118. Canonical Record Rule measurement

How should the suite determine whether an Application has kept materially important state outside Relay?

This may require a combination of:

- automated inspection;
- declared feature maps;
- manual review;
- export comparison.

---

## 119. Interoperability matrix

Should Relay governance publish a matrix showing which tested Providers and Applications have successfully interoperated directly?

---

## 120. Test-suite governance

Who may add, modify or remove conformance tests?

---

## 121. Non-deterministic systems

How should tests evaluate AI, ranking and recommendation behaviour where exact output is intentionally non-deterministic?

---

## 122. Legal and regulatory claims

Should legal compliance remain entirely outside Relay conformance, or should optional jurisdictional profiles be introduced?

---

# Part XXII — Provisional Decisions for v0.1

## 123. Provisional conformance decisions

Relay v0.1 will provisionally assume:

- conformance is profile-based;
- every claim names the Relay version and test-suite version;
- automated black-box testing is the baseline;
- independent verification is distinct from self-testing;
- certification may add operational and security requirements;
- the official test harness acts as several Relay roles;
- unknown records and extensions are tested through round-trip scenarios;
- migration is tested between independent source and destination implementations;
- Application replacement is a mandatory core scenario;
- revocation, stale writes, event gaps and forks are mandatory failure tests;
- reports are machine-readable and human-readable;
- results disclose skipped tests and limitations;
- test evidence may be signed and publicly registered;
- conformance status may expire or require retesting after material changes;
- pairwise interoperability testing supplements isolated profile tests;
- the complete identity–Application–Provider continuity scenario is the highest-value v0.1 test;
- the conformance suite will be open and independently implementable;
- legal compliance, general trustworthiness and business quality remain separate from protocol conformance.

---

## 124. Core conformance principle

The Conformance Testing Model can be reduced to one rule:

> An implementation earns the right to call itself Relay-compatible by proving that another independent implementation can replace it, interact with it and verify its claims without losing the user’s continuity.

The next core object is the **Relay Governance and Evolution Model**: how the protocol, core schemas, reserved namespaces and conformance rules change over time without allowing one company, Provider or implementation to take ownership of Relay itself.