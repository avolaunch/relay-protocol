# Relay Protocol v0.1  
## Core Object 11: Ecosystem Roles

### 1. Definition

The **Relay Ecosystem** consists of independent actors that create, host, resolve, interpret, verify, transport, index or interact with Relay Identities and Relay Records.

A single organisation may perform several roles.

For example, one company may operate:

- a Relay Provider;
- a Resolver;
- an Application;
- a Backup Service;
- a Discovery Service.

However, those roles remain conceptually separate.

Performing one role must not silently grant the organisation the authority associated with another role.

A company that hosts a repository does not automatically gain application permission to analyse private records.

An application that displays records does not automatically become an Identity Resolver.

A backup provider does not automatically become the active repository provider.

---

## 2. Purpose

The Ecosystem Roles Model exists to define:

- who participates in Relay;
- which authority each participant may exercise;
- which services each participant may provide;
- where one role ends and another begins;
- which forms of control are explicitly prohibited;
- how responsibilities remain understandable when one organisation performs several roles.

The model is intended to prevent Relay from recreating platform lock-in through role confusion.

The governing principle is:

> Relay authority comes from an explicit role and valid delegation, not merely from technical access or commercial power.

---

## 3. Role separation

Relay distinguishes between:

- **ownership or control**;
- **hosting**;
- **access**;
- **interpretation**;
- **verification**;
- **discovery**;
- **replication**;
- **derived processing**;
- **governance**.

These functions may be combined operationally, but their authority must not be conflated.

For example:

```text
The Provider stores the repository.
The Application reads selected records.
The Resolver locates the identity.
The Indexer builds search.
The Witness observes repository state.
```

None of these functions independently grants control of the Relay Identity.

---

## 4. Core ecosystem roles

Relay v0.1 recognises the following primary roles:

1. Identity Controller  
2. Relay Identity  
3. Relay Provider  
4. Repository Service  
5. Authorisation Service  
6. Relay Application  
7. Application Controller  
8. Resolver  
9. Discovery Service  
10. Schema Publisher  
11. Schema Registry  
12. Indexer  
13. Feed Generator  
14. Mirror  
15. Backup Provider  
16. Migration Service  
17. Recovery Authority  
18. Witness  
19. Transparency Service  
20. Credential Issuer  
21. Credential Holder  
22. Credential Verifier  
23. Moderation Label Provider  
24. Automation Service  
25. AI Service  
26. Blob Storage Provider  
27. Independent Verifier  
28. Relay Governance Body

Additional roles may be introduced through later protocol versions.

---

# Part I — Identity and Control Roles

## 5. Identity Controller

The **Identity Controller** is the human, organisation or authorised authority that holds ultimate control over a Relay Identity.

The Controller may authorise:

- Identity Document updates;
- key rotation;
- provider migration;
- recovery configuration;
- application permissions;
- repository termination;
- delegated authority.

The Controller may be:

- one person;
- several people operating through a threshold rule;
- an organisation;
- a guardian;
- an estate representative;
- another legally or technically recognised authority.

### 5.1 Controller authority

The Controller may exercise high-authority actions according to the identity’s control rules.

The Controller is not necessarily:

- the current account user;
- the active device;
- the current Relay Provider;
- the person who created a particular record;
- the holder of every operational key.

### 5.2 Controller limitations

The Controller cannot:

- rewrite another identity’s repository;
- alter another party’s signed credential;
- force an application to display content;
- compel a provider to violate law;
- make self-declared statements externally verified merely through control of the identity.

### 5.3 What the Controller owns

The Controller retains authority over:

- the Relay Identity;
- its Identity Document;
- its repository authority;
- application grants;
- migration;
- recovery;
- records controlled by the identity.

This does not automatically grant ownership of:

- externally issued credentials;
- third-party replies;
- other identities’ relationship declarations;
- application software;
- provider infrastructure.

---

## 6. Relay Identity

The **Relay Identity** is the persistent protocol entity represented by a Relay Identifier.

The Identity is not itself a service operator.

It is the subject and authority anchor around which other roles operate.

A Relay Identity may represent:

- a person;
- an organisation;
- a project;
- a publication;
- a group;
- an automated agent;
- another recognised entity.

### 6.1 Identity capabilities

A Relay Identity may:

- control a repository;
- hold records;
- issue grants;
- participate in relationships;
- receive credentials;
- issue signed statements;
- delegate authority.

### 6.2 Identity limitations

An Identity does not automatically imply:

- legal personhood;
- verified real-world identity;
- human control;
- trustworthiness;
- factual truth;
- eligibility for every service.

---

## 7. Recovery Authority

A **Recovery Authority** is an actor or mechanism authorised to help restore control of a Relay Identity.

A Recovery Authority may be:

- a recovery key;
- a trusted person;
- a group of trusted people;
- a managed recovery provider;
- a hardware device;
- an organisational quorum;
- a legal representative.

### 7.1 Recovery capabilities

A Recovery Authority may be permitted to:

- replace compromised keys;
- recover identity control;
- publish a replacement Identity Document;
- authorise emergency migration;
- restore from a verified repository backup.

### 7.2 Recovery limitations

A Recovery Authority must not automatically gain:

- routine access to repository contents;
- application permission;
- authority to create ordinary records;
- permanent control after recovery;
- the right to inspect private data.

### 7.3 Recovery authority principle

> The ability to restore control must not silently become the ability to exercise ordinary control.

---

# Part II — Hosting and Infrastructure Roles

## 8. Relay Provider

A **Relay Provider** is an organisation or individual that operates one or more Relay services for Controllers.

A Provider may offer:

- identity hosting;
- repository hosting;
- authorisation;
- events;
- blobs;
- recovery;
- migration;
- backups;
- public profile hosting.

### 8.1 Provider capabilities

A Relay Provider may:

- store repository data;
- validate commits;
- serve records;
- operate service endpoints;
- enforce hosting policy;
- process migrations;
- issue operational credentials;
- maintain backups;
- provide support.

### 8.2 Provider limitations

A Provider does not automatically own:

- the Relay Identity;
- the Repository Identifier;
- Record URIs;
- relationships;
- application grants;
- public reputation;
- imported or created records.

A Provider must not represent hosting as identity ownership.

### 8.3 Provider replacement

A Relay Provider must remain replaceable.

The Controller must be able to migrate to another compatible Provider while preserving identity continuity.

### 8.4 Multi-role provider

A Provider may also operate an Application, Resolver or Indexer.

When it does so, it must disclose the separate roles and apply the correct authority model to each.

---

## 9. Repository Service

A **Repository Service** stores and operates the canonical Relay Repository.

It may be operated by the Relay Provider or by a separate infrastructure operator.

### 9.1 Repository Service capabilities

It may:

- accept authorised commits;
- validate operations;
- maintain the Repository Head;
- serve records;
- provide exports;
- support migration;
- generate repository events;
- produce verification proofs.

### 9.2 Repository Service limitations

It must not:

- create arbitrary canonical records without authority;
- expand application grants;
- reassign Record URIs;
- rewrite valid history silently;
- treat internal database identifiers as protocol identifiers;
- continue authoritative writes after completed migration.

### 9.3 Canonical authority

The Repository Service operates canonical state only while validly designated by the current Identity Document and repository authority.

---

## 10. Authorisation Service

An **Authorisation Service** manages Permission Requests, Permission Grants, tokens and application sessions.

### 10.1 Authorisation Service capabilities

It may:

- display permission requests;
- issue grants;
- issue access tokens;
- validate application identity;
- renew valid access;
- revoke grants;
- record consent receipts;
- expose connected applications;
- enforce user policies.

### 10.2 Authorisation Service limitations

It must not:

- broaden a grant beyond approval;
- substitute vague consent for explicit scope;
- give applications hidden access;
- treat a token as identity ownership;
- preserve access after revocation;
- make itself permanently required after provider migration.

### 10.3 Separate authority

The Authorisation Service operates delegated access.

It does not become the Controller.

---

## 11. Blob Storage Provider

A **Blob Storage Provider** stores binary content referenced by Relay Records.

Examples include:

- images;
- video;
- audio;
- documents;
- archives;
- design files.

### 11.1 Blob Provider capabilities

It may:

- store blobs;
- serve blobs;
- replicate blobs;
- scan for malware;
- enforce storage limits;
- support content-addressed retrieval;
- transfer blobs during migration.

### 11.2 Blob Provider limitations

It must not:

- redefine Blob Identifiers;
- claim record ownership through storage;
- change blob contents without changing integrity references;
- make provider URLs permanent blob identities;
- prevent migration through provider-only encryption.

### 11.3 Blob authority

Blob storage does not establish authorship, rights ownership or factual provenance.

---

## 12. Mirror

A **Mirror** is a non-canonical copy of a repository or selected public records.

A Mirror may improve:

- availability;
- geographic performance;
- resilience;
- censorship resistance;
- archival access.

### 12.1 Mirror capabilities

It may:

- synchronise canonical commits;
- serve read-only records;
- expose its mirrored Repository Head;
- provide availability during source disruption;
- participate in verification.

### 12.2 Mirror limitations

A Mirror must not:

- accept canonical writes;
- present itself as the active Provider;
- expand record visibility;
- omit its replication status;
- silently become authoritative.

### 12.3 Mirror disclosure

A Mirror must identify:

- canonical source;
- mirrored Repository Head;
- synchronisation time;
- lag;
- read-only status.

---

## 13. Backup Provider

A **Backup Provider** maintains recoverable copies of Relay data.

A backup may include:

- commits;
- records;
- blobs;
- Identity Document history;
- schemas;
- verification metadata;
- encrypted private data.

### 13.1 Backup Provider capabilities

It may:

- receive incremental updates;
- verify repository continuity;
- store encrypted backups;
- produce recovery exports;
- restore data to an authorised destination.

### 13.2 Backup Provider limitations

It must not:

- become canonical automatically;
- activate a repository without authority;
- inspect encrypted private data without permission;
- issue application grants;
- publish records merely because it stores them.

### 13.3 Backup versus mirror

A Mirror primarily serves available copies.

A Backup Provider primarily preserves recoverable copies.

One service may perform both roles, but the distinction must remain explicit.

---

## 14. Migration Service

A **Migration Service** coordinates or performs movement between Providers.

It may be operated by:

- the source Provider;
- the destination Provider;
- an independent company;
- the Controller;
- an open-source tool.

### 14.1 Migration Service capabilities

It may:

- request exports;
- transfer records and blobs;
- verify repository integrity;
- synchronise final commits;
- produce migration reports;
- coordinate cutover;
- assist with application reconnection.

### 14.2 Migration Service limitations

It must not:

- initiate migration without valid authority;
- change the Relay Identifier;
- alter Record URIs;
- discard unsupported schemas silently;
- retain copied private data beyond approved policy;
- become the active Provider merely through possession of an export.

### 14.3 Migration authority

The Migration Service performs a process.

The Controller authorises the change of operational authority.

---

# Part III — Application and Processing Roles

## 15. Relay Application

A **Relay Application** is software that interacts with Relay Identities and Records through public access or valid Permission Grants.

Examples include:

- social clients;
- publishing tools;
- portfolio builders;
- mobile apps;
- professional networks;
- messaging clients;
- analytics tools;
- import tools.

### 15.1 Application capabilities

An Application may:

- request permission;
- read authorised records;
- create records;
- update records;
- render records;
- subscribe to authorised events;
- create derived views;
- maintain local caches.

### 15.2 Application limitations

An Application must not:

- own the user’s identity;
- expand its own grant;
- retain hidden access;
- convert local copies into canonical truth;
- delete repository records after revocation unless separately authorised;
- misrepresent unsupported records;
- treat cached handles as permanent identity references.

### 15.3 Application replaceability

A user must be able to replace an Application without losing supported canonical records and relationships.

---

## 16. Application Controller

The **Application Controller** is the person or organisation responsible for a Relay Application.

It is accountable for:

- the Application Manifest;
- permission requests;
- data handling;
- security;
- retention;
- onward sharing;
- incident response.

### 16.1 Application Controller limitations

The Controller of an Application is not the Controller of the user’s Relay Identity.

Owning the software does not grant ownership of records created through it.

---

## 17. Automation Service

An **Automation Service** performs actions in response to schedules, rules or events.

Examples include:

- scheduled publishing;
- content transformation;
- workflow automation;
- periodic backups;
- cross-application synchronisation.

### 17.1 Automation capabilities

It may:

- subscribe to authorised events;
- create or update records under a grant;
- run user-defined rules;
- trigger approved workflows;
- act while the user is absent.

### 17.2 Automation limitations

It must not:

- infer authority from event receipt;
- act outside its granted conditions;
- create hidden self-expanding workflows;
- ignore revocation;
- conceal automated authorship;
- trigger indefinite event loops.

### 17.3 Automation attribution

Automated changes should identify:

- the Automation Service;
- the Permission Grant;
- the triggering event or schedule;
- the controlling identity.

---

## 18. AI Service

An **AI Service** processes Relay data using machine-learning or generative systems.

It may provide:

- summarisation;
- recommendations;
- generation;
- search;
- classification;
- personal assistance;
- translation;
- moderation;
- analysis.

### 18.1 AI Service capabilities

An AI Service may:

- read authorised records;
- generate derived outputs;
- create records where permitted;
- build private indexes or embeddings where permitted;
- provide personalised assistance.

### 18.2 AI Service limitations

It must not treat one permission labelled “AI” as permission for all AI activities.

It must separately declare and obtain authority for:

- inference;
- personalisation;
- embeddings;
- fine-tuning;
- evaluation;
- general model training;
- human review;
- external model processing.

### 18.3 AI outputs

An AI output is not automatically canonical.

It becomes a Relay Record only when accepted into a Repository through valid authority.

### 18.4 AI Service principle

> Permission to reason over a person’s records is not permission to absorb those records permanently into a general model.

---

# Part IV — Resolution and Discovery Roles

## 19. Resolver

A **Resolver** translates a Relay Identifier or verified handle into the current valid Identity Document and service locations.

### 19.1 Resolver capabilities

It may:

- resolve Relay Identifiers;
- resolve handles;
- return Identity Documents;
- return handle proofs;
- detect stale documents;
- report migration;
- report resolution conflicts.

### 19.2 Resolver limitations

It must not:

- assign ownership of an identity;
- choose identity authority based on search rank;
- silently prefer one Provider’s document;
- treat its own response as unverifiable truth;
- become the only permanent route to an identity.

### 19.3 Verifiable output

Resolver output must contain enough evidence for independent verification.

---

## 20. Discovery Service

A **Discovery Service** helps users find identities, records, applications, schemas or providers.

Examples include:

- people search;
- public profile search;
- application directories;
- provider directories;
- topic discovery.

### 20.1 Discovery capabilities

It may:

- index public metadata;
- rank results;
- recommend identities;
- surface verified handles;
- suggest compatible applications;
- show provider options.

### 20.2 Discovery limitations

It must not:

- become identity authority;
- treat absence from its index as non-existence;
- transfer identity continuity through ranking;
- present inferred matches as verified identities;
- hide the Relay Identifier behind application-only identity.

### 20.3 Search versus truth

Discovery produces candidates.

Resolution verifies identities.

---

## 21. Indexer

An **Indexer** processes public or authorised records into searchable or queryable structures.

Examples include:

- public search engines;
- follower indexes;
- professional graph indexes;
- topic indexes;
- content archives.

### 21.1 Indexer capabilities

It may:

- ingest public events;
- retrieve public records;
- maintain search indexes;
- calculate reverse relationships;
- expose derived counts;
- process authorised restricted data.

### 21.2 Indexer limitations

It must not:

- claim indexed records as canonical;
- ignore deletion and visibility changes;
- expose restricted content publicly;
- present incomplete graph coverage as complete;
- remove source provenance;
- retain private access after revocation.

### 21.3 Index incompleteness

An Indexer must disclose that its view may be incomplete, delayed or filtered.

---

## 22. Feed Generator

A **Feed Generator** produces ordered or recommended collections of Relay Records.

It may generate:

- chronological feeds;
- topic feeds;
- relationship feeds;
- personalised feeds;
- editorial feeds.

### 22.1 Feed Generator capabilities

It may:

- consume public or authorised events;
- retrieve records;
- rank records;
- apply filters;
- produce feed projections.

### 22.2 Feed Generator limitations

It must not:

- become the canonical owner of feed content;
- alter source records;
- imply that ranking is neutral or universal;
- use private records without authority;
- convert following relationships into application-owned audiences.

### 22.3 Algorithm independence

Several Feed Generators may operate over the same underlying records and relationships.

---

# Part V — Schema and Verification Roles

## 23. Schema Publisher

A **Schema Publisher** defines and publishes a Relay Schema under a controlled namespace.

### 23.1 Schema Publisher capabilities

It may:

- publish schemas;
- issue revisions;
- publish major versions;
- provide conformance fixtures;
- publish deprecation notices;
- issue security advisories;
- provide conversion guidance.

### 23.2 Schema Publisher limitations

It must not:

- own records using its schema;
- rewrite published schema versions silently;
- remotely invalidate user records;
- prevent competing applications from implementing the schema;
- reassign its namespace without valid authority.

---

## 24. Schema Registry

A **Schema Registry** indexes and distributes schema definitions.

### 24.1 Registry capabilities

It may:

- resolve Schema Identifiers;
- verify publisher identity;
- retain schema history;
- mirror definitions;
- expose compatibility information;
- distribute security notices.

### 24.2 Registry limitations

It must not:

- become the sole owner of schema meaning;
- change a signed schema definition;
- assign record ownership;
- delete historical schemas silently;
- require every schema to be centrally approved.

---

## 25. Independent Verifier

An **Independent Verifier** checks Relay identities, repositories, commits, exports or migrations without acting as the active Provider.

### 25.1 Verifier capabilities

It may:

- verify Identity Document chains;
- verify commit history;
- verify Repository Heads;
- verify blobs;
- detect forks;
- verify exports;
- produce reports and receipts.

### 25.2 Verifier limitations

It must not:

- become canonical authority merely through verification;
- alter repository state;
- resolve disputes beyond its evidence;
- present cryptographic validity as factual truth;
- conceal the scope of verification performed.

### 25.3 Verification scope

A Verifier must state whether it performed:

- full verification;
- snapshot verification;
- record verification;
- migration verification;
- limited verification.

---

## 26. Witness

A **Witness** observes and signs a repository state, Identity Document or checkpoint.

### 26.1 Witness capabilities

It may:

- attest that it observed a state;
- publish observation time;
- help detect equivocation;
- retain signed checkpoints;
- support recovery evidence.

### 26.2 Witness limitations

A Witness must not:

- control the identity;
- make repository changes;
- become the sole source of validity;
- inspect private contents unnecessarily;
- claim factual truth beyond what it observed.

### 26.3 Witness statement

A Witness proves observation, not ownership or authorship.

---

## 27. Transparency Service

A **Transparency Service** maintains an append-only log of selected high-authority Relay events.

It may log:

- Identity Document updates;
- key changes;
- provider migrations;
- repository checkpoints;
- application manifest changes;
- schema releases.

### 27.1 Transparency Service capabilities

It may:

- publish append-only entries;
- provide inclusion proofs;
- expose signed checkpoints;
- detect inconsistent histories;
- support public auditing.

### 27.2 Transparency Service limitations

It must not:

- control the identities it logs;
- require public disclosure of private record contents;
- become a mandatory global ledger;
- rewrite or remove valid historical entries silently.

### 27.3 Optionality

Relay may support several Transparency Services.

No single service should be permanently mandatory.

---

# Part VI — Credential and Trust Roles

## 28. Credential Issuer

A **Credential Issuer** creates signed claims about a subject.

Examples include:

- university;
- employer;
- professional body;
- government;
- community;
- certification authority.

### 28.1 Issuer capabilities

It may:

- issue credentials;
- define expiration;
- revoke credentials;
- publish status;
- sign claims;
- provide supporting evidence.

### 28.2 Issuer limitations

It must not:

- control the holder’s Relay Identity;
- rewrite a holder’s repository;
- force a holder to display a credential;
- make unrelated claims through one credential;
- prevent the holder from retaining historical proof of issuance.

---

## 29. Credential Holder

A **Credential Holder** is the identity that receives, stores or presents a credential.

The Holder may:

- store the credential;
- present it;
- hide it;
- grant selective access;
- prove possession;
- remove it from active display.

The Holder may not alter the Issuer’s signed claim without invalidating it.

---

## 30. Credential Verifier

A **Credential Verifier** evaluates a credential presented by a Holder.

### 30.1 Verifier capabilities

It may check:

- issuer signature;
- subject;
- expiration;
- revocation;
- schema;
- evidence;
- applicability.

### 30.2 Verifier limitations

It must not:

- infer unrelated facts;
- retain credential data without authority;
- present validation as universal trustworthiness;
- modify the credential;
- make itself the owner of the claim.

---

## 31. Moderation Label Provider

A **Moderation Label Provider** issues labels or assessments about identities or records.

Possible labels include:

- spam;
- malware;
- graphic content;
- impersonation;
- misinformation category;
- age restriction;
- community-policy status.

### 31.1 Label Provider capabilities

It may:

- issue labels;
- revoke labels;
- attach reason codes;
- provide evidence;
- publish label feeds;
- process appeals.

### 31.2 Label Provider limitations

It must not:

- alter the target record;
- claim universal authority over moderation;
- present application policy as protocol invalidity;
- conceal issuer identity;
- use one label outside its declared context.

### 31.3 Multiple label systems

Applications may choose which Label Providers to trust.

---

# Part VII — Governance Role

## 32. Relay Governance Body

A **Relay Governance Body** is an organisation or process responsible for maintaining the Relay specification and core namespace.

It may be:

- a foundation;
- a standards consortium;
- an open technical committee;
- another transparent governance structure.

### 32.1 Governance capabilities

It may:

- publish protocol versions;
- maintain core schemas;
- coordinate security advisories;
- define conformance tests;
- manage reserved namespaces;
- publish implementation guidance;
- oversee specification change procedures.

### 32.2 Governance limitations

It must not:

- own Relay Identities;
- operate as the mandatory global Provider;
- access user repositories by default;
- approve every third-party schema;
- require all Applications to use one commercial service;
- convert protocol governance into ecosystem ownership.

### 32.3 Governance separation

The organisation governing Relay should be structurally distinguishable from companies selling Relay hosting or applications.

---

# Part VIII — Role Combination

## 33. Combined roles

One organisation may perform several roles.

Example:

```text
Company A operates:
- a Relay Provider;
- an Application;
- a Resolver;
- an Indexer.
```

This is permitted.

However, Company A must not use authority obtained in one role as though it were granted in another.

---

## 34. Role-bound access

Access must be tied to the role under which it is exercised.

For example:

### Provider role

May store encrypted private records as part of hosting.

### Application role

May read those private records only with a valid Permission Grant.

### Indexer role

May index public records but may not index private records merely because the same company hosts them.

The system should record which role performed an action.

---

## 35. First-party Application

A Provider may offer its own first-party Application.

The Application must still:

- publish an Application Manifest;
- request permissions;
- respect revocation;
- separate optional application processing from required hosting operations;
- identify its data-retention practices.

The Provider must not hide Application access inside infrastructure access.

---

## 36. Provider-operated Resolver

A Provider may operate a Resolver.

The Resolver must be capable of resolving identities hosted by other Providers where the protocol supports them.

It must not return preferentially false or incomplete results merely to discourage migration.

---

## 37. Provider-operated Indexer

A Provider may index public content hosted by itself and others.

It must distinguish:

- canonical repository data;
- indexed copies;
- provider-internal administrative data;
- private hosting data.

Hosting access does not grant indexing authority over private records.

---

## 38. Combined-role disclosure

An organisation performing several roles should disclose:

- each role;
- which legal entity operates it;
- which data each role accesses;
- which permissions apply;
- whether data crosses role boundaries;
- how users can disable optional roles;
- whether the roles share infrastructure.

---

## 39. Internal data barriers

Where one organisation performs several roles, it may need technical and organisational barriers.

Examples include:

- separate service credentials;
- separate audit logs;
- separate encryption scopes;
- access-control boundaries;
- role-specific retention;
- internal purpose restrictions.

A policy statement alone may be insufficient for high-risk role combinations.

---

# Part IX — Role Authority Rules

## 40. Explicit authority

No role receives authority merely because it possesses technical access.

Examples:

- storing a record does not grant publishing rights;
- seeing an event does not grant write authority;
- holding a backup does not grant activation rights;
- indexing a post does not grant editing rights;
- verifying a credential does not grant retention rights.

Authority must be established by:

- protocol role;
- Permission Grant;
- controller delegation;
- public-access rule;
- signed credential;
- service designation;
- lawful requirement.

---

## 41. Least-authority principle

Each actor should exercise the minimum authority required for its role.

Examples:

```text
A Feed Generator needs public records, not recovery authority.
A Backup Provider needs encrypted commits, not application tokens.
A Resolver needs Identity Documents, not private repository content.
An AI Service needs selected records, not the entire repository.
```

---

## 42. No authority by inference

Relay must not infer authority from relationships such as:

- same company;
- same domain;
- same cloud account;
- same administrator;
- same user session;
- same database;
- same commercial contract.

Authority must remain explicit and machine-verifiable where possible.

---

## 43. Delegated authority

A role may delegate limited authority to another actor.

For example:

- Provider delegates blob storage;
- Application delegates model inference;
- Controller delegates scheduled publishing;
- Governance Body delegates schema review.

Delegation must identify:

- delegator;
- recipient;
- capabilities;
- scope;
- duration;
- onward delegation;
- revocation.

---

## 44. Sub-processors

An actor may rely on a sub-processor.

Examples:

- Application uses an AI model provider;
- Provider uses object storage;
- Indexer uses a search infrastructure vendor.

The primary actor remains responsible for representing:

- the sub-processor’s role;
- data accessed;
- purpose;
- retention;
- onward sharing;
- security implications.

A hidden sub-processor must not receive broader access than the primary actor.

---

## 45. Role revocation

Authority associated with a role may end when:

- a Permission Grant is revoked;
- a Provider migration completes;
- an Application is suspended;
- a credential expires;
- a recovery relationship is replaced;
- an organisation changes controllers;
- a service designation is withdrawn.

Ending the role’s authority does not necessarily erase historical records of actions performed while authority was valid.

---

# Part X — Role Identification

## 46. Role identity

Each infrastructure or application actor should have a stable protocol identity where appropriate.

Examples:

```text
rid:provider:alpha
rid:app:writing-client
rid:service:resolver-one
rid:service:backup-one
```

The exact identifier scheme remains provisional.

A stable role identity supports:

- signed manifests;
- audit trails;
- delegation;
- revocation;
- reputation;
- migration;
- accountability.

---

## 47. Role manifest

A service actor should publish a signed manifest describing:

- identity;
- operator;
- roles performed;
- service endpoints;
- protocol versions;
- public keys;
- jurisdiction;
- capabilities;
- policies;
- contact details;
- incident endpoint;
- manifest version.

An Application Manifest is one specialised form of role manifest.

---

## 48. Role verification

A role may have verification states such as:

```text
self-declared
domain-verified
controller-verified
security-reviewed
conformance-tested
certified
suspended
revoked
```

Verification must specify what was verified.

For example:

```text
Relay v0.1 migration conformance tested
```

is more meaningful than:

```text
Trusted provider
```

---

## 49. Role reputation

Relay v0.1 should not define a universal service reputation score.

Reputation may be derived from:

- conformance history;
- uptime;
- security incidents;
- migration success;
- audit results;
- user reports;
- governance actions.

Any derived reputation must identify its issuer and methodology.

---

# Part XI — Actor Interactions

## 50. Application and Provider

An Application interacts with a Provider through:

- identity resolution;
- authorisation;
- repository APIs;
- event subscriptions;
- blob APIs.

The Application receives only the authority granted to its role.

The Provider must not require the Application to adopt provider-owned user identities.

---

## 51. Provider and Backup Provider

The Provider may send:

- commits;
- encrypted blobs;
- schemas;
- Identity Document history;

to a Backup Provider under Controller authority.

The Backup Provider does not become canonical through replication.

---

## 52. Resolver and Provider

The Resolver locates the Provider designated by the current Identity Document.

The Provider does not own the Resolver.

The Resolver does not assign the Provider.

Both rely on valid identity authority.

---

## 53. Application and AI Service

An Application may delegate processing to an AI Service.

The user-facing permission model should identify:

- the AI Service where relevant;
- records shared;
- activity performed;
- retention;
- training use;
- human review.

The Application remains responsible for ensuring the AI Service operates within the granted scope.

---

## 54. Indexer and Feed Generator

An Indexer may provide searchable data to a Feed Generator.

The Feed Generator may rank indexed records.

Neither becomes canonical.

Both must retain source provenance.

---

## 55. Schema Publisher and Application

A Schema Publisher defines a record format.

An Application implements it.

The Publisher cannot prevent compatible Applications from reading user-owned records merely because it originally designed the schema.

---

## 56. Credential Issuer and Holder

The Issuer controls its signed claim.

The Holder controls whether and how it is presented.

Neither controls the other’s broader identity or repository.

---

## 57. Witness and Provider

A Witness may observe states served by a Provider.

The Witness may expose inconsistency.

It cannot replace the Controller’s identity authority merely because it observed one state.

---

# Part XII — Prohibited Role Confusion

## 58. Hosting mistaken for ownership

A Provider must not claim that:

```text
We host the repository, therefore the identity and records belong to us.
```

Hosting authority is operational and replaceable.

---

## 59. Application account mistaken for identity

An Application must not require the user’s durable identity to exist only as:

```text
user_id_8821 in Application A
```

Application-local identifiers may exist, but the Relay Identifier remains the portable identity anchor.

---

## 60. Index mistaken for canonical source

An Indexer must not present its cached record as the authoritative version when the source repository reports a newer state or deletion.

---

## 61. Resolver mistaken for registry owner

A Resolver returns verifiable identity information.

It does not own or assign the identity merely because applications consult it.

---

## 62. Backup mistaken for active repository

A Backup Provider must not begin serving canonical writes without valid activation or migration authority.

---

## 63. Verification mistaken for truth

A Verifier may prove that a signed claim exists.

It does not necessarily prove that the claim is factually correct.

---

## 64. Moderation mistaken for protocol validity

An Application or Label Provider may hide a valid record.

It must not present the record as cryptographically invalid merely because it violates a policy.

---

## 65. Schema publication mistaken for record ownership

A Schema Publisher may define a format.

It does not own records encoded in that format.

---

## 66. AI processing mistaken for training permission

An AI Service permitted to perform inference must not infer permission to train a broader model.

---

# Part XIII — Required Role Declarations

## 67. Minimum role declaration

A Relay service actor should declare:

- stable identity;
- role or roles;
- operator;
- service endpoints;
- public keys;
- protocol versions;
- jurisdiction where relevant;
- capabilities;
- limitations;
- data practices;
- security contact.

---

## 68. Multi-role declaration

Where one actor performs several roles, the declaration should identify:

```text
Role: Relay Provider
Purpose: Repository hosting

Role: Relay Application
Purpose: Social client

Role: Indexer
Purpose: Public search
```

Each role should have separate authority and data-use descriptions.

---

## 69. Role change

A material role change may require:

- manifest update;
- user notification;
- re-authorisation;
- new conformance testing;
- updated service designation.

For example, an Application becoming an AI training service is a material role change.

---

## 70. Undeclared role

An actor must not perform a materially different processing role without declaring it.

Examples include:

- Provider secretly acting as advertising profiler;
- Application secretly acting as general model trainer;
- Backup Provider acting as commercial data broker;
- Resolver acting as behaviour-tracking service.

---

# Part XIV — Required v0.1 Role Capabilities

## 71. Controller capabilities

A compliant implementation must allow the Controller to:

```text
Inspect service roles
Inspect connected Applications
Inspect current Provider
Inspect recovery authority
Inspect backups and mirrors
Inspect active subscriptions
Revoke delegated authority
Change Provider
Replace Applications
```

---

## 72. Service-role capabilities

A service actor should support:

```text
Publish role manifest
Publish public keys
Declare protocol versions
Declare capabilities
Declare data practices
Rotate keys
Report security incident
Report service suspension
Update role manifest
Terminate service cleanly
```

---

## 73. Role audit capabilities

The ecosystem should make it possible to determine:

- which actor performed an action;
- under which role;
- under which authority;
- against which resource;
- at what time;
- with what result.

---

# Part XV — Role Invariants

## 74. Ecosystem role invariants

The following rules must always remain true.

### Invariant 1

Performing one Relay role does not automatically grant the authority of another role.

### Invariant 2

A Provider does not own the Relay Identities it hosts.

### Invariant 3

An Application does not own the records it creates under user authority.

### Invariant 4

A Resolver does not assign identity authority.

### Invariant 5

An Indexer does not become the canonical source of indexed records.

### Invariant 6

A Backup Provider does not become active merely because it holds a copy.

### Invariant 7

A Schema Publisher does not own records encoded with its schema.

### Invariant 8

A Witness observes authority but does not become authority.

### Invariant 9

A Credential Verifier does not own or rewrite the credential.

### Invariant 10

A Moderation Label Provider does not alter the target record.

### Invariant 11

An AI Service must distinguish inference from training and other AI activities.

### Invariant 12

Combined roles must remain separately declared and separately authorised.

### Invariant 13

Technical possession of data does not imply permission to use it for another purpose.

### Invariant 14

Delegated authority must remain limited, attributable and revocable.

### Invariant 15

The Governance Body governs the protocol but does not own identities or repositories.

---

# Part XVI — Compliance Scenario

## 75. Multi-role company scenario

Company A operates:

- Provider A;
- Social Application A;
- Resolver A;
- Public Indexer A;
- AI Service A.

Alice creates a Relay Identity hosted by Provider A.

### Hosting role

Provider A stores Alice’s repository.

It can:

- validate commits;
- serve records;
- create exports;
- support migration.

It cannot use Alice’s private records for AI training merely because it stores them.

### Application role

Alice chooses to connect Social Application A.

The Application requests:

```text
Read public profile
Read posts
Create posts
Subscribe to post events
```

Alice approves.

The Application may now act within that grant.

The fact that the Application and Provider share a corporate owner does not remove the need for the grant.

### Resolver role

Resolver A resolves Alice’s Relay Identifier and returns her signed Identity Document.

It also resolves identities hosted by Provider B.

Resolver A cannot falsely return Provider A as the current provider after Alice migrates.

### Indexer role

Public Indexer A indexes Alice’s public posts.

It may not index her private drafts.

If Alice deletes a public post, the Indexer processes the deletion event and updates its index.

### AI role

Social Application A offers an optional summary feature using AI Service A.

It separately requests:

```text
Read selected posts for AI inference
No general model training
No human review
Temporary processing only
```

Alice approves the inference request.

AI Service A may produce the summary.

It may not use Alice’s posts for general training.

### Migration

Alice migrates to Provider B.

Provider A stops canonical writes after cutover.

Social Application A may remain connected if its grant continues.

Public Indexer A continues indexing public records from Provider B.

Resolver A returns Provider B as current.

The roles remain operationally separate despite the shared corporate ownership.

If these boundaries are maintained, the system satisfies the basic Ecosystem Roles objective.

---

# Part XVII — Open Design Questions

## 76. Role identity format

Should Providers, Applications, Resolvers and other actors use:

- specialised Relay Identifier types;
- ordinary Relay Identities with role manifests;
- existing organisational identifiers;
- a combination?

---

## 77. Role manifest format

Should all service roles use one common manifest format with role-specific extensions?

---

## 78. Combined-role enforcement

Which role separations should be:

- architectural;
- cryptographic;
- contractual;
- auditable;
- organisational?

---

## 79. Governance Body structure

What governance model best prevents the commercial operator of a major Relay service from controlling the protocol?

---

## 80. Service certification

Which roles should require formal conformance testing before using Relay compatibility claims?

Possible candidates include:

- Providers;
- Resolvers;
- Migration Services;
- Authorisation Services;
- Independent Verifiers.

---

## 81. AI Service identity

Should external model providers appear as directly declared Relay actors, even where the user interacts only with the primary Application?

---

## 82. Sub-processor visibility

How much detail should users see about infrastructure subcontractors and service dependencies?

---

## 83. Role-specific legal responsibility

How should protocol roles map to legal roles such as:

- data controller;
- data processor;
- joint controller;
- custodian;
- publisher?

Relay terminology should not falsely imply one universal legal classification.

---

## 84. Role reputation

Should Relay define standard service-performance records, or leave all reputation systems external?

---

## 85. Recovery Authority safeguards

Which Recovery Authority combinations provide usability without creating a new central identity gatekeeper?

---

## 86. Service exit

What minimum exit and migration behaviour should each service role support?

---

# Part XVIII — Provisional Decisions for v0.1

## 87. Provisional role decisions

Relay v0.1 will provisionally assume:

- one organisation may perform several roles;
- each role remains separately declared;
- authority is role-bound and purpose-bound;
- every Application has a stable Application Identity and manifest;
- Providers remain replaceable;
- Repository Services operate canonical state only while designated;
- Resolvers return independently verifiable results;
- Indexers and Feed Generators produce derived views;
- Mirrors and Backups are non-canonical;
- Migration Services require explicit Controller authority;
- Recovery Authorities are distinct from ordinary application access;
- Schema Publishers do not own user records;
- Independent Verifiers and Witnesses do not become canonical authorities;
- Credential Issuers, Holders and Verifiers remain separate;
- AI Services distinguish inference, training, embeddings, evaluation and related activities;
- first-party Applications remain subject to the same permission rules as third-party Applications;
- combined-role organisations disclose cross-role data use;
- the Governance Body does not operate as the mandatory global Provider;
- role-specific compliance requirements will be defined in subsequent protocol sections.

---

## 88. Core ecosystem principle

The Ecosystem Roles Model can be reduced to one rule:

> In Relay, authority belongs to the role explicitly granted to an actor; no company gains control over a person’s digital continuity merely by performing several useful services around it.

The next core object is the **Relay Provider Compliance Model**: the minimum technical, operational and portability obligations a service must satisfy before describing itself as a Relay-compatible Provider.