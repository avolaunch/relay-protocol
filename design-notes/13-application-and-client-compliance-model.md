# Relay Protocol v0.1  
## Core Object 13: Application and Client Compliance Model

### 1. Definition

A **Relay-compatible Application or Client** is software that interacts with Relay Identities, Repositories, Records, Relationships, Permissions or Events while preserving the user’s ability to replace that software without losing canonical digital continuity.

Applications and Clients may include:

- web applications;
- mobile applications;
- desktop software;
- browser extensions;
- command-line tools;
- AI assistants;
- automation agents;
- background services;
- import and export tools;
- collaborative editors;
- feed readers;
- publishing clients.

A Relay-compatible Application may create powerful, proprietary and highly differentiated experiences.

It must not make itself the only place where the user’s identity, records, relationships or authority remain operational.

The central requirement is:

> Applications create experiences, not ownership.

---

## 2. Purpose

The Application and Client Compliance Model defines the minimum obligations software must satisfy when it:

- requests access to a Relay Identity;
- reads Relay Records;
- creates or updates records;
- renders canonical content;
- stores local application state;
- creates derived data;
- synchronises repository state;
- invokes AI or automation services;
- handles unknown schemas;
- loses or has its permission revoked.

The model exists to prevent application-level lock-in.

A Provider may be technically replaceable while an Application still traps the user through:

- proprietary internal records;
- hidden relationship state;
- incomplete Relay synchronisation;
- undocumented extensions;
- local-only revisions;
- non-portable formatting;
- application-owned identifiers;
- undisclosed derived profiles;
- inaccessible collaborative history.

Relay compatibility therefore requires more than connecting to a Relay API.

It requires the Application to preserve the distinction between:

- canonical user-owned state;
- portable application extensions;
- derived application outputs;
- temporary local state;
- interface-specific behaviour.

---

# Part I — Application Scope

## 3. Application

A **Relay Application** is software identified by an Application Identity and described by an Application Manifest.

The Application may:

- request Permission Grants;
- retrieve authorised records;
- submit repository operations;
- create derived views;
- maintain caches;
- subscribe to authorised events;
- invoke delegated services;
- provide user interfaces.

The Application is not:

- the Relay Identity;
- the canonical Repository;
- the owner of records created through it;
- the permanent owner of relationships created through it;
- the authority that defines whether another Application may access compatible records.

---

## 4. Client

A **Relay Client** is an Application or Application component used directly or indirectly to interact with Relay services.

Examples include:

- mobile app;
- desktop editor;
- website;
- terminal client;
- local-first workspace;
- embedded device interface;
- background synchronisation agent.

The terms Application and Client may overlap.

This model uses **Application** for the registered software actor and **Client** for a particular implementation, interface or installation.

---

## 5. Application installation

One Application may have multiple installations.

Examples:

```text
Application:
Example Writing Client

Installations:
Web browser session
Desktop application
Mobile phone
Background publishing worker
```

Each installation may have its own:

- device credential;
- session;
- local cache;
- event cursor;
- revocation state;
- security risk.

A compliant Application should distinguish the Application Identity from individual installations where technically relevant.

---

## 6. Application compliance profiles

Applications may claim compliance under specific profiles.

Possible profiles include:

```text
Read-only Client
Publishing Client
Editing Client
Local-first Client
Relationship Client
AI Client
Automation Client
Import Client
Migration Client
Full Relay Client
```

A read-only feed client is not required to support every operation expected of a full editing client.

Compliance claims must identify the relevant profile.

---

# Part II — Foundational Principles

## 7. Application replaceability

A user must be able to stop using an Application without losing canonical records that the Application created under Relay authority.

For supported schemas, another compatible Application should be able to:

- retrieve the same records;
- preserve the same Record URIs;
- display the same canonical content;
- submit authorised updates;
- continue supported relationships;
- retain provenance;
- follow repository migration.

The replacement Application need not reproduce the same interface or proprietary features.

It must be able to interact with the canonical state the user reasonably expected to own.

---

## 8. Experience-layer principle

An Application may own and differentiate through:

- interface design;
- workflows;
- visual layout;
- editing tools;
- recommendation algorithms;
- notifications;
- ranking methods;
- productivity features;
- collaborative experiences;
- performance optimisations;
- branding;
- commercial model.

These are experience-layer assets.

The Application must not claim ownership merely through its experience layer over:

- the user’s Relay Identity;
- canonical records;
- stable Record URIs;
- relationships;
- credentials;
- Permission Grants;
- repository history;
- source provenance.

---

## 9. UI ownership principle

Relay does not standardise one universal user interface.

Applications remain free to decide:

- how records are displayed;
- which supported features are emphasised;
- which feeds are generated;
- which workflows are offered;
- which communities are served;
- which design conventions are used.

This freedom does not permit the Application to conceal canonical ownership or portability.

The governing rule is:

> The Application may own the interface through which the user experiences a record, but not the underlying record itself.

---

## 10. Canonical Record Rule

A compliant Application must not intentionally make its hidden internal representation materially more complete than the user’s Relay representation where doing so creates undisclosed dependency on the Application.

If the Application stores material user-created state outside Relay, it must classify and disclose that state.

Examples include:

- advanced formatting;
- revisions;
- collaborative comments;
- annotations;
- embedded objects;
- project structure;
- publishing configuration;
- relationship metadata;
- moderation decisions;
- automation rules;
- editing history.

The Application should use one of the following models:

### Canonical Relay record

The state is stored directly as a Relay Record.

### Portable extension record

The state is stored through a documented namespaced Relay schema.

### Derived application state

The state is generated from canonical records and can be rebuilt.

### Temporary local state

The state is intentionally short-lived and not reasonably expected to survive Application replacement.

### Non-portable feature state

The state cannot currently be represented portably and is clearly disclosed to the user.

An Application must not silently present non-portable state as though it belongs to the user’s canonical Relay history.

---

## 11. No concealed canonical substitute

An Application must not maintain a private internal database as the real source of user-created truth while writing only a reduced or decorative copy to Relay.

For example, an Application must not:

- store the full article privately while placing only a summary in Relay;
- store relationship membership privately while exporting only follower counts;
- store complete design documents privately while writing only preview images;
- keep comments and revisions privately while claiming the Relay post is fully portable.

A reduced Relay representation is permitted only where:

- the limitation is inherent to the feature;
- the user is informed;
- the Application identifies what is non-portable;
- the Application offers export where practical;
- the Application does not falsely claim full Relay compatibility for that feature.

---

# Part III — Application Identity and Manifest

## 12. Application Identity

Every Application requesting non-public access must have a stable Application Identity.

The Application Identity must remain distinguishable from:

- visible product name;
- company name;
- domain;
- installation;
- software version;
- OAuth client identifier;
- internal account identifier.

A branding or infrastructure change does not necessarily create a new Application Identity.

A controller change or material trust change may require a new identity or re-authorisation.

---

## 13. Application Manifest

A compliant Application must publish a signed, versioned Application Manifest.

The manifest should include:

- Application Identity;
- visible name;
- accountable operator;
- verified domains;
- application category;
- protocol versions;
- redirect locations;
- public keys;
- supported schemas;
- support levels;
- requested capability catalogue;
- data-retention practices;
- onward-sharing practices;
- AI usage;
- background operation;
- sub-processors;
- security contact;
- incident endpoint;
- manifest version;
- signature.

---

## 14. Manifest accuracy

The Application Manifest must accurately describe current behaviour.

The Application must not:

- request one purpose while performing another;
- omit a material sub-processor;
- declare temporary retention while retaining indefinitely;
- declare no AI training while conducting model training;
- describe background access as session-only;
- claim full schema support where only partial rendering exists.

Material changes require a new manifest version.

---

## 15. Material manifest changes

The following changes should normally require user review or re-authorisation:

- expanded data access;
- new write capabilities;
- new deletion capabilities;
- general model training;
- new human review;
- onward sharing;
- new background access;
- changed Application Controller;
- materially longer retention;
- new private-data categories;
- added high-authority operations.

Cosmetic or non-material changes need not require renewed approval.

---

# Part IV — Permission Compliance

## 16. Permission request minimisation

An Application must request only the access reasonably required for the intended functionality.

It must not request:

```text
Read entire repository
```

when it needs only:

```text
Read public profile and article records
```

It must not request deletion rights merely because deletion may be useful later.

---

## 17. Permission clarity

Permission requests must describe concrete consequences.

A compliant request should explain:

- which record types are accessed;
- whether the Application may create, edit or delete;
- whether access continues in the background;
- whether data is retained externally;
- whether AI processing occurs;
- whether third parties receive data;
- when the permission expires.

The Application must not rely solely on vague phrases such as:

```text
Improve your experience
Access your account
Use your data
```

---

## 18. Partial permission support

Where technically possible, the Application should continue operating with a reduced Permission Grant.

If the user denies optional access, the Application may disable the affected feature.

It must not falsely describe optional permissions as essential.

---

## 19. No self-expansion

An Application must never:

- expand its own Permission Grant;
- mint new capabilities beyond the grant;
- use one installation to authorise another without permission;
- convert record access into identity-management authority;
- infer access to related records from one granted record.

All expanded authority requires valid approval.

---

## 20. Permission enforcement awareness

The Provider enforces canonical access, but the Application is also responsible for limiting its own behaviour.

A compliant Application must not attempt to:

- probe unauthorised records;
- reuse expired tokens;
- retain access after revocation;
- bypass collection restrictions;
- use public endpoints to reconstruct restricted information;
- continue private event subscriptions after permission ends.

---

## 21. Revocation response

After revocation, the Application must:

- stop requesting protected data;
- stop background processing;
- stop using delegated keys;
- terminate protected subscriptions;
- stop submitting repository operations;
- handle retained data according to the approved policy;
- update its interface to reflect the disconnected state.

The Application must not repeatedly pressure the user to reconnect through deceptive interface behaviour.

---

## 22. Record survival after revocation

The Application must not delete canonical records merely because access has been revoked.

Records created through the Application remain under repository authority.

The Application may lose access to them.

It does not gain the right to erase them.

---

# Part V — Canonical Record Handling

## 23. Stable identifiers

Applications must use:

- Relay Identifiers;
- Repository Identifiers;
- Record URIs;
- Blob Identifiers;
- Schema Identifiers;

as the durable references to Relay objects.

Application-internal identifiers may exist, but they must not replace protocol-level identifiers.

---

## 24. No Record URI substitution

An Application must not rewrite:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

into an Application-owned identity such as:

```text
https://application.example/posts/8821
```

and then treat the latter as canonical.

An Application URL may point to a presentation of the record.

It is not the permanent record identity.

---

## 25. Canonical source labelling

Where an Application displays cached or indexed content, it should retain:

- source Record URI;
- source Relay Identifier;
- observed version;
- observed Repository Head where relevant;
- retrieval time.

The Application should not present stale cached content as current without appropriate qualification.

---

## 26. Canonical write acceptance

An Application must not tell the user that a change is safely published or saved before the repository accepts it.

The interface should distinguish:

```text
Local draft
Pending synchronisation
Submitted
Accepted into Relay Repository
Rejected
Conflict detected
```

---

## 27. Local drafts

Applications may store local drafts.

They must accurately disclose whether a draft is:

- only on the current device;
- in Application cloud storage;
- synchronised as a private Relay Record;
- accepted into the canonical Repository.

A local draft must not be presented as canonical or fully backed up when it is not.

---

## 28. Pending operations

A pending operation must retain enough information to determine:

- target Record URI;
- expected record version;
- intended operation;
- Application Identity;
- local timestamp;
- synchronisation status.

If repository state changes before acceptance, the Application must handle the conflict rather than silently overwrite.

---

## 29. Optimistic concurrency

Editing Applications must submit the record version or Repository Head against which an update was prepared.

If canonical state has advanced, the Application should:

- refresh;
- compare changes;
- offer merge;
- preserve the user’s work;
- request explicit overwrite where permitted.

Silent last-write-wins behaviour is not compliant for canonical edits unless the schema explicitly defines it.

---

## 30. Record deletion

An Application may request deletion only when its Permission Grant allows it.

The interface should explain the difference between:

- removing a record from the Application’s view;
- deleting the canonical record;
- requesting content erasure;
- hiding a record locally;
- applying an Application moderation decision.

These must not be conflated.

---

## 31. Record restoration

If restoration is supported, the Application must treat it as a new canonical operation.

It must not erase the historical deletion event.

---

## 32. Unsupported records

An Application encountering an unsupported schema must:

- preserve the record;
- avoid destructive editing;
- display safe metadata where possible;
- explain that the format is unsupported;
- offer an appropriate compatible Application where available.

It must not convert the record silently into a reduced format.

---

## 33. Preserve-only behaviour

An Application claiming preserve-only support must preserve:

- Record URI;
- schema;
- content;
- extensions;
- blob references;
- provenance;
- visibility;
- version metadata.

It need not render or edit the record.

---

## 34. Unknown fields

Applications must preserve unknown valid extension fields when editing records they otherwise support.

An Application must not parse, rewrite and save a record in a manner that strips fields belonging to another Application.

---

## 35. Round-trip safety

A compliant editing Application should pass a round-trip test:

1. retrieve a record containing known and unknown fields;
2. modify a supported field;
3. submit an update;
4. preserve all unknown fields that remain valid;
5. retain the same Record URI and schema.

---

# Part VI — Application Extensions

## 36. Extension schemas

Applications may define portable extension schemas for specialised functionality.

Examples include:

```text
com.example.editor.revision.v1
com.example.design.canvas.v1
com.example.workflow.rule.v1
```

The Application should publish:

- schema definition;
- documentation;
- version history;
- integrity hash;
- examples;
- migration guidance;
- security considerations.

---

## 37. Extension openness

An Application must not require competing Applications to obtain secret permission merely to interpret user-owned records encoded in a published Relay extension schema.

The Application may retain intellectual property in:

- implementation;
- interface;
- algorithms;
- services.

It must not use undocumented schema secrecy as the primary lock-in mechanism for canonical user records.

---

## 38. Proprietary file formats

An Application may use proprietary binary formats where justified.

It must disclose:

- format version;
- whether documentation exists;
- whether other Applications may implement it;
- export alternatives;
- conversion limitations;
- what becomes non-portable.

The Provider must still preserve the associated blob.

---

## 39. Extension degradation

If another Application cannot interpret an extension, it may still display the underlying core record.

For example:

```text
Core article:
Readable and editable.

Application-specific collaborative revision layer:
Preserved but unsupported.
```

The unsupported extension must not prevent access to the portable core unless technically unavoidable.

---

## 40. No deliberate compatibility sabotage

An Application must not intentionally:

- generate malformed records to block other Clients;
- encrypt ordinary public records solely to prevent interoperability;
- change undocumented fields to break competitors;
- misuse extensions to override core semantics;
- create unstable identifiers that fail outside the Application.

---

# Part VII — Local and Derived State

## 41. Local application state

Applications may keep local state that is not canonical.

Examples include:

- open tab;
- window size;
- scroll position;
- dismissed tooltip;
- temporary filter;
- render cache;
- unsaved form input.

This state need not be portable unless the Application represents it as persistent user-owned state.

---

## 42. User-expected continuity test

An Application should consider storing state portably when a reasonable user would expect it to survive replacing the Application.

Examples may include:

- saved draft;
- project structure;
- reading list;
- notification preferences;
- custom content organisation;
- automation rules;
- long-term annotations.

The test is:

> Would loss of this state make the user feel that their substantive work or ongoing digital life remained trapped in the Application?

---

## 43. Derived data

An Application may derive:

- recommendation scores;
- feed rankings;
- summaries;
- inferred topics;
- analytics;
- search indexes;
- engagement estimates;
- reputation projections.

Derived data is not automatically canonical.

---

## 44. Derived-data provenance

Where derived data is displayed or saved, the Application should identify:

- producer;
- source records;
- derivation time;
- methodology category;
- whether the result is current;
- whether the result entered the canonical Repository.

---

## 45. Canonicalisation of derived output

A derived output becomes canonical only when:

- the Controller approves or authorises it;
- the repository accepts it;
- provenance is retained;
- its schema permits canonical storage.

An Application must not fill the user’s Repository with inferred records without authority.

---

## 46. Hidden user profiles

An Application must not create undisclosed persistent behavioural profiles from Relay data.

Where the Application creates:

- interest profiles;
- risk scores;
- inferred identity traits;
- advertising segments;
- commercial audience categories;

it must disclose the processing and obtain authority where required.

Such profiles must not be presented as user-authored canonical Relay Records unless explicitly accepted.

---

# Part VIII — Relationships

## 47. Relationship portability

Applications creating relationships must use Relay Relationship Records where the relationship is intended to survive Application replacement.

Examples include:

- follows;
- subscriptions;
- collaborators;
- memberships;
- endorsements.

The Application must not keep the operational relationship solely in its private database while presenting it as a Relay relationship.

---

## 48. Relationship counters

Follower, reaction and membership counts are derived values.

An Application must not treat a count as the canonical relationship graph.

Where a count is incomplete or index-dependent, the interface should not imply universal precision.

---

## 49. Relationship ownership

An Application that introduces two identities does not own their relationship.

It may:

- render the connection;
- facilitate the request;
- apply community rules;
- choose not to display it.

It may not prevent compatible Clients from reading the canonical relationship record where authorised.

---

## 50. Blocks and mutes

Blocks and mutes may be:

- canonical private Relay Records;
- portable preference records;
- Application-local settings.

The Application must disclose which model applies.

A user should not assume that an Application-local block automatically applies across all Relay Clients.

---

# Part IX — Event and Synchronisation Compliance

## 51. Event subscriptions

An Application must subscribe only to events permitted by its grant.

It should request the narrowest practical event scope.

It must stop protected event delivery after revocation.

---

## 52. Duplicate-safe processing

Applications must process at-least-once event delivery safely.

The Application should use:

- Event Identifier;
- cursor;
- canonical Record URI;
- commit reference;

to avoid duplicate side effects.

---

## 53. Event confirmation

Security-sensitive and canonical events should be confirmed against the authoritative service.

For example:

- a migration event triggers identity re-resolution;
- a record-update event triggers canonical record retrieval;
- a revocation event triggers token invalidation;
- a key-rotation event triggers Identity Document refresh.

The Application must not blindly trust an unauthenticated notification.

---

## 54. Event gaps

If the Application detects or is informed of an event gap, it must not assume its local cache is current.

It should perform:

- event replay;
- commit synchronisation;
- collection refresh;
- snapshot synchronisation;
- another authorised recovery process.

---

## 55. Synchronisation status

A synchronising Application should track:

- source repository;
- authorised scope;
- last verified Repository Head;
- last event cursor;
- known gaps;
- pending operations;
- unresolved conflicts;
- last synchronisation time.

---

## 56. Offline support

A local-first or offline Application may allow changes without an active connection.

It must distinguish:

- local-only state;
- queued operations;
- repository-accepted state;
- conflicts.

The Application must not imply successful canonical publication while offline.

---

## 57. Provider migration

After provider migration, the Application must:

1. refresh identity resolution;
2. verify the new Identity Document;
3. identify the new service endpoints;
4. validate its continuing Permission Grant;
5. obtain new provider-issued credentials;
6. re-establish event subscriptions;
7. resume from the migration boundary.

The Application must not bind the user permanently to a cached provider URL.

---

# Part X — Caching and Retention

## 58. Cache classification

Applications should distinguish:

- temporary cache;
- offline working copy;
- retained external copy;
- derived index;
- canonical Relay Record.

These categories must not be represented interchangeably.

---

## 59. Cache freshness

Cached records should retain:

- Record URI;
- observed version;
- retrieval time;
- source Repository Head where relevant.

The Application should refresh according to risk and user expectations.

---

## 60. Deletion handling

After receiving or discovering canonical deletion, the Application must follow its declared retention policy.

It should:

- remove the record from active views;
- stop distributing it;
- update indexes;
- retain only permitted metadata;
- disclose legal or archival exceptions.

---

## 61. Visibility changes

If a record changes from public to restricted or private, the Application must update future access and distribution.

A previously public cache does not grant indefinite authority to continue displaying the record as public under Relay compliance.

Legal and archival exceptions may apply separately.

---

## 62. External retention declaration

The Application must declare whether it retains Relay data outside the source Repository.

Possible declarations include:

```text
No retention
Session-only
Temporary cache
Offline device copy
Retained until revocation
Retained for specified period
Retained indefinitely
```

The declaration must match actual behaviour.

---

# Part XI — AI Client Compliance

## 63. AI role disclosure

An Application invoking AI must disclose whether it performs:

- inference;
- summarisation;
- generation;
- personalisation;
- embedding;
- retrieval;
- fine-tuning;
- evaluation;
- general model training;
- human review.

It must not combine all AI uses under one permission.

---

## 64. Model-provider disclosure

Where an external model provider receives Relay data, the Application should identify:

- the provider;
- data categories sent;
- processing purpose;
- retention;
- training policy;
- region where relevant;
- whether humans may review data.

---

## 65. AI context minimisation

An AI Client must send only the records reasonably necessary for the requested task.

It should not transmit the entire Repository when a limited record set is sufficient.

---

## 66. AI output status

AI-generated output must be clearly classified as:

- temporary output;
- local draft;
- suggested edit;
- derived record;
- canonical record.

The output becomes canonical only after valid repository acceptance.

---

## 67. Training separation

Permission for AI inference does not imply permission for:

- general model training;
- fine-tuning;
- evaluation;
- human review;
- embedding retention.

Each materially distinct use requires appropriate authority.

---

## 68. AI provenance

Where an AI-generated or AI-assisted output is saved as a Relay Record, the Application should preserve structured provenance, including:

- Application;
- model service where appropriate;
- creation mode;
- source records;
- generation time;
- human approval status.

---

## 69. Personal agent authority

An AI Agent acting on behalf of a user must still operate through valid Permission Grants.

The fact that it is described as “the user’s agent” does not grant:

- unrestricted repository access;
- identity-management authority;
- migration authority;
- permission to train models;
- authority to contact other identities.

---

# Part XII — Automation Client Compliance

## 70. Automation declaration

An Automation Client must declare:

- trigger;
- schedule or event source;
- actions;
- resources;
- background operation;
- duration;
- failure behaviour;
- loop-prevention behaviour.

---

## 71. User-absent actions

An Application acting while the user is absent must have explicit background authority.

A normal interactive grant must not be silently converted into permanent automation authority.

---

## 72. Triggered authority

Receiving an event does not itself grant permission to perform a write.

The Automation Client must separately possess authority for the resulting operation.

---

## 73. Automation attribution

Canonical records created through automation should identify:

- controlling Relay Identity;
- Automation Application;
- triggering event or schedule;
- Permission Grant;
- correlation or workflow identifier.

---

## 74. Loop prevention

Automation Clients should support:

- causation references;
- correlation identifiers;
- workflow depth limits;
- duplicate-event detection;
- rate limits;
- user-visible pause controls.

---

# Part XIII — Import and Export Client Compliance

## 75. Import Client

An Import Client converts external data into Relay Records.

It must preserve provenance such as:

- source service;
- source identifier;
- import time;
- conversion tool;
- information loss;
- matching confidence;
- user confirmation.

---

## 76. No false verification

Imported data must not be represented as cryptographically verified merely because it was imported.

For example, an imported username is not automatically a verified Relay Identity.

---

## 77. Import idempotence

Repeated import of the same source data should not create uncontrolled duplicates where the importer can recognise prior import.

The importer should retain source identifiers and import history.

---

## 78. Export Client

An Export Client must preserve:

- protocol identifiers;
- schemas;
- records;
- blobs;
- provenance;
- integrity data;
- completeness declaration.

It must not flatten a complete Relay export into an incomplete format while labelling it complete.

---

# Part XIV — Security Compliance

## 79. Secure credential handling

Applications must protect:

- access tokens;
- refresh authority;
- delegated keys;
- device credentials;
- local private caches;
- encryption keys.

Sensitive credentials should not be exposed in:

- logs;
- URLs;
- analytics;
- crash reports;
- browser storage without appropriate controls.

---

## 80. Redirect security

Applications using browser-based authorisation must protect against:

- callback substitution;
- state manipulation;
- replay;
- malicious redirects;
- session fixation;
- intercepted authorisation codes.

---

## 81. Installation isolation

Compromise of one installation should not automatically compromise:

- every installation;
- root identity authority;
- recovery authority;
- migration authority.

Where supported, each installation should have independent revocation.

---

## 82. Local storage protection

Applications storing restricted or private records locally should use suitable device security, such as:

- platform-secured storage;
- encryption;
- authenticated sessions;
- secure deletion where practical;
- inactivity locking.

---

## 83. Application incident response

The Application Controller must publish a security contact and have a process for:

- key compromise;
- token compromise;
- malicious release;
- data leak;
- unauthorised retention;
- sub-processor compromise.

Affected users and Providers should be informed where materially necessary.

---

## 84. Compromised Application

If an Application is compromised, it should:

- revoke affected keys;
- publish an updated manifest;
- notify Providers;
- stop unsafe processing;
- support user review;
- identify affected installations or grants;
- require re-authorisation where needed.

The compromise must not automatically invalidate canonical records previously created through valid authority.

---

# Part XV — Privacy and Data Use

## 85. Purpose limitation

Applications must use Relay data only for approved and lawful purposes.

Possession of a record does not imply permission to use it for:

- advertising;
- profiling;
- resale;
- general training;
- unrelated analytics;
- identity inference.

---

## 86. Data minimisation

Applications should retrieve and retain only the data necessary for their function.

A Client should not synchronise unrelated private collections merely because broader access is available.

---

## 87. Onward sharing

Applications must disclose onward sharing to:

- processors;
- analytics services;
- model providers;
- advertisers;
- affiliates;
- storage providers;
- human reviewers.

The Application remains responsible for ensuring delegated processing remains within the approved scope.

---

## 88. Role separation

A company operating both an Application and another Relay role must not use Application-authorised data for another role without valid authority.

Examples:

- publishing Client data used by an Indexer;
- private editor content used by an AI trainer;
- social Client relationships used by an advertising profile service.

---

# Part XVI — Moderation and Presentation

## 89. Application moderation

An Application may decide which records it displays.

It may:

- hide content;
- apply labels;
- rank content;
- block identities;
- restrict participation;
- enforce community standards.

It must distinguish Application moderation from:

- canonical deletion;
- repository invalidity;
- identity termination;
- Provider suspension.

---

## 90. Hidden record accuracy

If an Application hides a valid record, it should not falsely state:

```text
This record does not exist.
```

A more accurate status may be:

```text
This record is not displayed under this Application’s policy.
```

where disclosure is appropriate.

---

## 91. Source preservation

When displaying transformed, shortened or moderated versions of records, the Application should retain the canonical source reference.

---

## 92. Presentation integrity

An Application must not materially alter the apparent meaning or attribution of a record without making the transformation clear.

Examples include:

- quoting out of context;
- replacing author identity;
- changing timestamps;
- omitting material provenance;
- presenting an AI summary as the original record.

---

# Part XVII — Application Shutdown and Exit

## 93. Application shutdown plan

An Application claiming durable Relay compatibility should publish an exit plan addressing:

- final manifest status;
- key revocation;
- user notification;
- local-data export;
- external retained data;
- event-subscription closure;
- delegated-key revocation;
- schema preservation;
- open-source or replacement options where offered.

---

## 94. Application disappearance

If an Application disappears:

- canonical Relay Records remain in user Repositories;
- other Applications may continue reading supported schemas;
- unsupported extension records remain preserved;
- active grants should expire or be revocable;
- delegated keys should cease to function.

---

## 95. Schema continuity after shutdown

An Application shutting down must not make published schemas disappear where this would strand user records.

It should preserve or mirror:

- schema definitions;
- documentation;
- integrity hashes;
- conformance fixtures;
- migration guidance.

---

# Part XVIII — Conformance Requirements

## 96. Minimum Application compliance

A Relay-compatible Application must:

- publish a valid Application Manifest;
- request explicit limited permissions;
- use stable Relay identifiers;
- distinguish local from canonical state;
- preserve unknown valid extensions;
- handle revocation;
- avoid hidden canonical substitutes;
- disclose non-portable features;
- follow migration and resolution updates;
- process events safely;
- preserve provenance;
- protect credentials;
- accurately state its support level.

---

## 97. Application conformance tests

The conformance suite may test:

- partial Permission Grant behaviour;
- revoked-grant enforcement;
- Record URI preservation;
- unknown-field round trip;
- unsupported-schema preservation;
- stale-update conflict handling;
- local-versus-canonical status;
- duplicate event handling;
- event-gap recovery;
- provider migration reconnection;
- AI purpose separation;
- background-authority enforcement;
- application replacement;
- shutdown continuity.

---

## 98. Canonical Record Rule test

A test Application may be required to demonstrate that:

- material user-created state is written to canonical Relay records;
- portable extension records are documented;
- derived state can be rebuilt;
- local-only state is classified;
- non-portable state is disclosed.

The test may compare the Application’s internal user-facing features with the exported Relay representation.

---

## 99. Round-trip test

A compliant editing Application should:

1. read a record containing known and unknown extensions;
2. edit a supported field;
3. submit the update;
4. preserve unsupported valid data;
5. retain the Record URI;
6. retain provenance;
7. produce a valid canonical update.

---

## 100. Replacement test

Application A creates and edits supported canonical records.

Application B then:

- connects independently;
- reads those records;
- edits supported fields;
- preserves unknown extensions;
- continues supported relationships.

Application A must not be required for Application B to continue.

---

# Part XIX — Application Invariants

## 101. Application compliance invariants

The following rules must always remain true.

### Invariant 1

An Application does not own a Relay Identity merely because the user accesses it through that Application.

### Invariant 2

An Application does not own canonical records it creates under user authority.

### Invariant 3

A Record URI remains stable across Application replacement.

### Invariant 4

An Application may own its interface and software, but not the user’s canonical digital continuity.

### Invariant 5

The Application’s hidden internal database must not become an undisclosed superior source of user-created truth.

### Invariant 6

Non-portable feature state must be classified and disclosed.

### Invariant 7

Unknown valid schemas and extensions must not be destroyed.

### Invariant 8

A local draft is not canonical until the Repository accepts it.

### Invariant 9

Revoking an Application stops future authority but does not delete canonical records previously created through it.

### Invariant 10

Permission for one action or purpose does not imply another.

### Invariant 11

AI inference permission does not imply model-training permission.

### Invariant 12

Receiving an event does not grant write authority.

### Invariant 13

Cached data does not become canonical.

### Invariant 14

Application moderation does not alter repository validity.

### Invariant 15

Changing Relay Provider must not require creation of a new Application-owned identity.

### Invariant 16

Derived data does not become canonical without valid acceptance.

### Invariant 17

An Application URL does not replace the canonical Record URI.

### Invariant 18

Application disappearance must not destroy canonical supported records.

### Invariant 19

First-party and third-party Applications are subject to the same fundamental ownership rules.

### Invariant 20

Compliance claims must identify the supported profile and limitations.

---

# Part XX — Compliance Scenario

## 102. Publishing Application scenario

Application A is a Relay-compatible writing Client.

Alice grants it permission to:

```text
Read profile
Read articles
Create articles
Update articles
Upload article media
Subscribe to article events
```

Alice does not grant deletion or AI training.

### Article creation

Alice writes an article.

Application A stores:

- title;
- portable rich-text body;
- media references;
- publication metadata;

as a canonical Relay article record.

The Application also supports collaborative revision history through:

```text
com.application-a.editor.revision.v1
```

The extension schema is documented and stored in Alice’s Repository.

### Local draft

Before publication, Alice creates an offline draft.

Application A shows:

```text
Saved on this device
Not yet synchronised to Relay
```

After synchronisation and repository acceptance, it shows:

```text
Saved to Relay
```

### Unknown extension

The article also contains an accessibility extension created by Application B.

Application A does not understand all of it.

When Alice edits the article, Application A preserves the extension unchanged.

### Stale update

Alice edits the article on two devices.

Device 1 publishes version 4.

Device 2 attempts to publish an edit based on version 3.

Application A detects the stale version and offers a merge rather than silently overwriting version 4.

### Revocation

Alice revokes Application A.

Application A stops:

- token renewal;
- background synchronisation;
- event receipt;
- repository updates.

The article and revision extension remain in Alice’s Repository.

### Application replacement

Alice connects Application C.

Application C fully supports the core article schema and preserve-only support for Application A’s revision extension.

It reads and edits the article while preserving the unsupported revision records.

### Provider migration

Alice migrates her Relay from Provider Alpha to Provider Beta.

Application C refreshes identity resolution, receives new Provider credentials and continues editing the same Record URI.

### AI feature

Application C offers an optional article summary.

It requests:

```text
Read selected article for temporary AI inference
No model training
No human review
No retained embedding
```

Alice approves.

The summary remains a temporary derived output until Alice chooses to save it as a Relay Record.

If these behaviours occur without hidden lock-in, authority expansion or loss of canonical state, the Application satisfies the Relay Application and Client compliance objective.

---

# Part XXI — Non-Compliant Examples

## 103. Decorative Relay copy

An Application stores the full project privately but writes only a title and preview image to Relay.

It claims that the project is portable.

This violates the Canonical Record Rule unless the limitation is clearly disclosed.

---

## 104. Unknown-field destruction

An Application reads a Relay record, edits one known field and saves it after stripping all unknown extensions.

This is not compliant editing behaviour.

---

## 105. Application-owned relationships

An Application stores follows only in its private database while presenting them as portable Relay relationships.

This is not relationship compliance.

---

## 106. Hidden training

An AI Client requests permission to summarise private notes and then uses them for general model training.

This violates purpose separation.

---

## 107. False save status

A mobile Client shows:

```text
Published
```

when the change exists only in a local queue and has not been accepted by the Repository.

This is not compliant state representation.

---

## 108. Revocation retaliation

After the user revokes access, the Application deletes records it previously created.

This violates repository authority.

---

## 109. Proprietary identity substitution

An Application stores only its own internal user identifier and cannot reconnect to the same Relay Identity after provider migration.

This is not Relay identity compatibility.

---

## 110. Hidden non-portable collaboration

An editor claims full Relay portability while storing all comments, revisions and collaborator roles in an inaccessible private database.

This is not full feature portability.

---

# Part XXII — Open Design Questions

## 111. Canonical completeness threshold

How should conformance tests determine whether an Application’s Relay representation is materially complete enough for the feature it claims to support?

---

## 112. Non-portable feature disclosure

What standard vocabulary should describe:

```text
Portable
Partially portable
Preserved but unsupported
Application-dependent
Local-only
Derived
```

---

## 113. Rich editing state

Which collaborative editing concepts should receive common Relay schemas rather than remain application extensions?

---

## 114. Client-side encryption

How should Applications support end-to-end encrypted records while preserving multi-Application interoperability?

---

## 115. Application manifests

Should every command-line tool and local open-source Client require a registered Application Identity, or may some use user-controlled local credentials?

---

## 116. Local-first authority

How should locally signed offline commits interact with Provider-issued Permission Grants and multi-device conflict resolution?

---

## 117. Application certification

Which compliance profiles should require automated testing, independent review or full certification?

---

## 118. Proprietary formats

What minimum documentation or export obligation should apply when an Application uses a proprietary canonical blob format?

---

## 119. Derived profiling

Which inferred profiles require explicit consent, and which may remain transient Application behaviour?

---

## 120. AI Agent autonomy

What additional safeguards should apply when an AI Client can act continuously across several Relay collections?

---

## 121. Shutdown obligations

Should Applications with widely adopted extension schemas be required to escrow or permanently archive schema documentation?

---

## 122. First-party advantages

Which integrated capabilities may a Provider’s first-party Application legitimately use without creating unfair lock-in?

---

# Part XXIII — Provisional Decisions for v0.1

## 123. Provisional Application decisions

Relay v0.1 will provisionally assume:

- Applications and Clients are covered by one compliance model;
- compliance claims are profile-specific;
- every networked non-public Application has a stable Application Identity and signed manifest;
- Applications request limited, explicit and revocable permissions;
- Applications use stable Relay identifiers rather than internal identifiers as canonical references;
- user-created canonical state must be stored in Relay records or documented portable extensions where practical;
- material non-portable state must be disclosed;
- unknown valid schemas and extension fields must be preserved;
- local drafts and pending operations remain clearly distinguishable from canonical state;
- stale updates require conflict handling;
- Application revocation does not remove canonical records;
- Application moderation remains separate from repository validity;
- AI inference, embeddings, fine-tuning, evaluation and general training remain distinct permission purposes;
- background Automation requires explicit authority;
- event delivery is processed idempotently;
- event gaps trigger canonical resynchronisation;
- Applications follow provider migration through identity resolution;
- first-party Applications remain subject to the same canonical ownership principles;
- proprietary experience design remains unrestricted;
- Application disappearance must not destroy supported canonical records;
- Application compliance does not require all features to be portable, but requires honest classification of what is and is not portable.

---

## 124. Core Application principle

The Application and Client Compliance Model can be reduced to one rule:

> Build any experience, workflow, algorithm or interface you can imagine—but do not make the user surrender their identity, records, relationships or continuity in exchange for using it.

The next core object is the **Relay Conformance Testing Model**: how Providers, Applications, Resolvers, Migration Services and other implementations are tested against observable protocol behaviour rather than self-declared compatibility.