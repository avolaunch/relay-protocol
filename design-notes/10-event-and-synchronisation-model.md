# Relay Protocol v0.1  
## Core Object 10: Event and Synchronisation Model

### 1. Definition

A **Relay Event** is a structured notification that a meaningful change has occurred within a Relay Identity, Repository, Permission system, Relationship graph or associated service.

The **Event and Synchronisation Model** defines how authorised systems learn about those changes without repeatedly downloading and comparing entire repositories.

Events may communicate changes such as:

- a record being created;
- a record being updated;
- a record being deleted;
- a relationship being established or ended;
- a Permission Grant being issued or revoked;
- an Identity Document being updated;
- a repository being migrated;
- a signing key being rotated;
- a moderation label being issued;
- a repository fork being detected;
- a provider becoming unavailable.

An event is not automatically the canonical source of the change.

The underlying signed identity, repository or authority record remains canonical.

The event tells another system that it should inspect or synchronise that canonical state.

---

## 2. Purpose

The Event and Synchronisation Model exists to make Relay operational across:

- applications;
- providers;
- user devices;
- mirrors;
- indexers;
- backup services;
- moderation services;
- discovery systems;
- authorised AI services.

Without events, every participant would need to repeatedly ask:

```text
Has anything changed?
```

and potentially download large amounts of unchanged information.

Events allow authorised services to:

- react promptly;
- maintain local indexes;
- refresh cached records;
- stop access after revocation;
- follow migrations;
- deliver notifications;
- synchronise offline devices;
- detect missing updates;
- resume after interruption.

The primary design requirement is:

> Events accelerate awareness of canonical changes without becoming a second competing source of truth.

---

## 3. Core components

The Event and Synchronisation Model contains:

1. **Event**
2. **Event Type**
3. **Event Source**
4. **Event Subject**
5. **Event Cursor**
6. **Event Stream**
7. **Subscription**
8. **Delivery Endpoint**
9. **Delivery Attempt**
10. **Acknowledgement**
11. **Replay**
12. **Synchronisation Session**
13. **Change Set**
14. **Snapshot**
15. **Gap Detection**
16. **Backfill**
17. **Delivery Signature**
18. **Filtering Rule**

---

## 4. Event

A Relay Event is a structured notification describing a change or condition.

Example:

```json
{
  "id": "event_01JXB4F7",
  "type": "relay.record.updated",
  "source": "repo:relay:alice",
  "subject": "relay://rid:relay:alice/com.relay.post/post_123",
  "repositoryHead": "sha256:head-204...",
  "commit": "sha256:commit-204...",
  "occurredAt": "2026-08-24T18:00:00Z",
  "publishedAt": "2026-08-24T18:00:01Z",
  "cursor": "204",
  "data": {
    "collection": "com.relay.post",
    "version": 4
  }
}
```

The exact serialisation remains provisional.

---

## 5. Event purpose

An event may serve one or more purposes:

### Notification

Inform an application that something happened.

### Synchronisation

Tell a replica or device which canonical changes to retrieve.

### Security signalling

Communicate revocation, key compromise or authority change.

### Operational signalling

Communicate migration, suspension or service state.

### Index maintenance

Tell an authorised indexer that public or permitted information changed.

### User experience

Trigger a visible alert, badge, feed update or workflow.

Applications must not assume every event is intended for end-user display.

---

## 6. Event source

The **Event Source** identifies the system or authority that emitted the event.

Possible sources include:

- Relay Repository;
- Relay Identity service;
- authorisation service;
- Relationship index;
- moderation service;
- provider;
- application;
- witness;
- resolver.

Example:

```text
repo:relay:alice
```

The source must be distinguishable from the identity or record affected by the event.

---

## 7. Event subject

The **Event Subject** identifies the entity or object to which the event relates.

Possible subjects include:

- Relay Identity;
- Relay Repository;
- Relay Record;
- Permission Grant;
- relationship;
- application;
- provider;
- migration;
- schema;
- checkpoint.

Examples:

```text
rid:relay:alice
```

```text
relay://rid:relay:alice/com.relay.post/post_123
```

```text
grant_01JX8K
```

---

## 8. Event type

Every event must declare a stable machine-readable type.

Possible core event types include:

```text
relay.identity.document-updated
relay.identity.key-rotated
relay.identity.recovery-started
relay.identity.recovered
relay.identity.deactivated

relay.repository.commit-accepted
relay.repository.fork-detected
relay.repository.migration-started
relay.repository.migrated
relay.repository.read-only

relay.record.created
relay.record.updated
relay.record.deleted
relay.record.restored
relay.record.visibility-changed

relay.relationship.created
relay.relationship.ended
relay.relationship.requested
relay.relationship.accepted

relay.permission.granted
relay.permission.narrowed
relay.permission.revoked
relay.permission.expired

relay.application.suspended
relay.provider.service-degraded
relay.provider.service-restored

relay.moderation.label-issued
relay.moderation.label-revoked
```

Third parties may define additional namespaced event types.

---

## 9. Event type semantics

Each event type should define:

- triggering condition;
- required fields;
- visibility;
- whether delivery is security-critical;
- whether events may be coalesced;
- whether replay is required;
- which canonical object confirms the event;
- whether acknowledgement is required.

For example:

```text
relay.permission.revoked
```

is security-critical and should cause future access to stop.

By contrast:

```text
relay.record.updated
```

may simply instruct a feed client to refresh the record.

---

## 10. Event identity

Each event must have a unique Event Identifier.

The identifier should be unique within the event source and stable across delivery retries.

If the same event is delivered five times, it must retain the same Event Identifier.

This allows receivers to detect duplicates.

A retry must not appear as a new canonical event.

---

## 11. Event cursor

An **Event Cursor** identifies a position within an ordered event stream.

Example:

```text
cursor: 204
```

A cursor may be:

- a sequence number;
- an opaque token;
- a commit identifier;
- a compound stream position.

A consumer may use the cursor to request:

```text
Give me all events after cursor 204.
```

The cursor must not be treated as global across unrelated event streams unless the protocol explicitly defines a shared ordering.

---

## 12. Event ordering

Events emitted by one repository or authority source should have a deterministic order corresponding to canonical state changes.

For a repository, the preferred ordering anchor is the commit sequence.

Example:

```text
Commit 201 → Event cursor 201
Commit 202 → Event cursor 202
Commit 203 → Event cursor 203
```

Events from different repositories do not necessarily have one universal order.

Timestamp comparison alone must not be used to infer a globally authoritative sequence.

---

## 13. Event stream

An **Event Stream** is an ordered sequence of events published by one source or service.

Examples include:

- repository event stream;
- identity-authority stream;
- authorisation stream;
- public activity stream;
- private security stream;
- migration stream.

A source may expose several streams with different visibility and retention policies.

---

## 14. Stream separation

Relay should avoid placing all events into one public stream.

Possible stream classes include:

### Public stream

Contains events relating to public records and public identity state.

### Application stream

Contains events visible to a particular authorised application.

### Private controller stream

Contains private repository and security events.

### Administrative stream

Contains provider or organisation operations.

### Security stream

Contains revocation, compromise and recovery events.

Separation reduces unnecessary information disclosure.

---

## 15. Event payload

An event payload should contain only the information necessary for its purpose.

A public record-update event may contain:

- Record URI;
- collection;
- new version;
- commit;
- Repository Head.

It need not contain the entire record body.

An authorised application can retrieve the current canonical record after receiving the event.

This reduces:

- payload size;
- privacy exposure;
- duplication;
- stale embedded content.

---

## 16. Canonical confirmation

An event receiver must be able to confirm the event against canonical state.

For a record update, the receiver may:

1. verify the event signature;
2. resolve the current repository;
3. retrieve the referenced commit or record;
4. verify the record version and Repository Head.

The event is a signal.

The repository remains the source of record truth.

---

## 17. Events and commits

A repository event should normally reference the commit that caused it.

Example:

```json
{
  "type": "relay.record.updated",
  "commit": "sha256:commit-204...",
  "repositoryHead": "sha256:commit-204..."
}
```

Several record events may refer to one batch commit.

A consumer that needs full synchronisation may retrieve the commit rather than process each event independently.

---

## 18. Event generation

Events may be generated after:

- commit acceptance;
- Identity Document publication;
- Permission Grant state change;
- relationship state change;
- provider operational change;
- migration state transition;
- security action.

An event must not be published as successful before the underlying canonical operation has been accepted.

For example, a `record.created` event must not be emitted merely because an application requested creation.

---

## 19. Event publication timing

A provider should publish an event promptly after the canonical operation succeeds.

However, delivery may be delayed by:

- network failure;
- queue backlog;
- receiver unavailability;
- rate limiting;
- security review.

Receivers must not assume that event delivery time equals event occurrence time.

The event should distinguish:

- `occurredAt`;
- `publishedAt`;
- `receivedAt`.

---

## 20. Transactional event publication

A provider should use a transactional mechanism ensuring that:

- a canonical change is not committed without its event becoming publishable;
- an event is not permanently published for a change that failed.

A practical implementation may use:

- transactional outbox;
- commit event log;
- append-only event table;
- durable message queue integrated with repository state.

This prevents repository and event histories from drifting apart.

---

## 21. Subscription

A **Subscription** authorises or configures delivery of selected events to a receiver.

A subscription should identify:

- subscriber;
- source;
- event types;
- resources or collections;
- delivery method;
- starting cursor;
- expiration;
- visibility authority;
- filtering rules;
- acknowledgement requirements.

Example:

```json
{
  "id": "subscription_01JXB5",
  "subscriber": "rid:app:reader-client",
  "source": "repo:relay:alice",
  "eventTypes": [
    "relay.record.created",
    "relay.record.updated",
    "relay.record.deleted"
  ],
  "collections": [
    "com.relay.post",
    "com.relay.article"
  ],
  "delivery": {
    "mode": "webhook",
    "endpoint": "https://reader.example.com/relay/events"
  },
  "startingCursor": "200",
  "expiresAt": "2026-09-24T00:00:00Z"
}
```

---

## 22. Subscription authority

A subscription must not provide access beyond the subscriber’s existing authority.

For example, an application with permission to read public posts may subscribe to public post events.

It must not subscribe to:

- private drafts;
- restricted relationships;
- permission audit events;
- security events;

unless separately authorised.

Event access is part of the Permission Model.

---

## 23. Subscription filters

A subscriber may filter events by:

- event type;
- collection;
- specific Record URI;
- relationship type;
- visibility;
- subject identity;
- application;
- minimum severity;
- schema;
- commit range.

Filtering should reduce unnecessary delivery.

A filter must not broaden access.

---

## 24. Subscription duration

A subscription may be:

- one session;
- time-limited;
- linked to a Permission Grant;
- active until revoked;
- active while an application installation remains valid.

When the underlying grant expires or is revoked, the subscription must stop.

---

## 25. Subscription state

A subscription may have states such as:

```text
pending
active
paused
expired
revoked
delivery-failing
terminated
```

The subscriber and controller should be able to inspect current subscription state.

---

## 26. Delivery methods

Relay may support several delivery methods.

### Webhook delivery

The source sends events to a registered HTTPS endpoint.

### Pull stream

The subscriber requests events after a known cursor.

### Persistent stream

The subscriber maintains a WebSocket, Server-Sent Events or similar connection.

### Queue delivery

Events are delivered through an authorised message broker.

### Local device synchronisation

A client requests changes during app activation or background refresh.

The protocol should define common semantics across delivery transports.

---

## 27. Webhook delivery

Webhook delivery is suitable for server-side applications.

The source should:

- use secure transport;
- sign the delivery;
- include Event Identifier;
- include delivery timestamp;
- support retries;
- protect against replay;
- validate registered endpoints;
- avoid following arbitrary redirects.

The receiver should acknowledge successful processing.

---

## 28. Pull synchronisation

Pull synchronisation allows a consumer to request:

```text
Events after cursor 204
```

This is important when:

- webhooks are unavailable;
- a client was offline;
- delivery retries failed;
- mobile background access is limited;
- a subscriber wants controlled processing.

A pull API must support pagination and gap detection.

---

## 29. Persistent streams

Persistent streams support near-real-time applications such as:

- live feeds;
- collaborative tools;
- notification clients;
- administration dashboards.

The stream must still support resumption from a cursor after disconnection.

A dropped connection must not require full repository resynchronisation.

---

## 30. Delivery signature

Each delivered event or batch should be cryptographically signed or authenticated.

The signature should bind:

- event content;
- Event Identifier;
- source;
- delivery time;
- intended receiver where appropriate;
- batch identifier;
- protocol version.

This protects against tampering and impersonation.

---

## 31. Event source verification

The receiver must verify that:

- the source is authorised to emit the event type;
- the signature matches a valid source key;
- the key was valid at publication time;
- the event belongs to the expected subscription;
- the event has not been altered.

A valid provider signature does not automatically prove that the referenced canonical record exists.

The receiver may still confirm canonical state.

---

## 32. Replay protection

A malicious party may resend a valid old event.

Receivers should use:

- Event Identifier deduplication;
- delivery timestamp;
- nonce where appropriate;
- cursor position;
- subscription identifier;
- accepted replay window.

A duplicate event should not cause duplicate canonical actions.

---

## 33. At-least-once delivery

Relay v0.1 should assume **at-least-once delivery**.

This means:

- a valid event may be delivered more than once;
- the receiver must process events idempotently;
- the sender retries until acknowledged or policy limits are reached.

Exactly-once delivery is difficult to guarantee across independent systems.

The canonical repository state prevents duplicates from becoming duplicate truth.

---

## 34. Idempotent processing

A receiver should store processed Event Identifiers or cursor state.

If the same event arrives again, the receiver should:

- acknowledge it;
- avoid repeating side effects;
- avoid creating duplicate index entries;
- avoid notifying the user repeatedly unless appropriate.

---

## 35. Acknowledgement

A receiver may acknowledge:

```text
processed
accepted-for-processing
duplicate
rejected
temporarily-unavailable
invalid-signature
unauthorised
```

Acknowledgement should distinguish permanent and temporary failure.

A positive transport acknowledgement does not necessarily mean the application has completed every downstream action.

---

## 36. Delivery retry

If delivery fails temporarily, the source may retry using:

- increasing delay;
- capped exponential backoff;
- retry limits;
- dead-letter handling;
- pull-based recovery.

The same Event Identifier must be retained.

The source should not retry indefinitely without exposing failure status.

---

## 37. Dead-letter state

An event may enter a **dead-letter** state when repeated delivery fails.

The system should record:

- subscription;
- event;
- attempts;
- last error;
- first failure;
- last failure;
- recommended action.

The subscriber or user may:

- repair the endpoint;
- request replay;
- switch delivery method;
- terminate the subscription.

---

## 38. Event batching

Several events may be delivered in one batch.

A batch should identify:

- batch ID;
- source;
- subscription;
- first cursor;
- last cursor;
- event count;
- signature.

The receiver should be able to determine which events were processed successfully.

Batching must not obscure event identity or order.

---

## 39. Event coalescing

Some high-volume event types may be coalesced.

For example, three rapid updates to the same public profile may produce one notification:

```text
Profile changed; current version is 8.
```

Coalescing is appropriate where only the latest state matters.

It is not appropriate for:

- security events;
- permission revocations;
- financial or legal events;
- repository commit replication;
- auditable authority changes.

---

## 40. Security-critical events

Security-critical events include:

```text
relay.permission.revoked
relay.identity.key-rotated
relay.identity.recovered
relay.application.suspended
relay.repository.fork-detected
relay.repository.migrated
```

These events should receive:

- high delivery priority;
- durable retention;
- limited coalescing;
- explicit acknowledgement;
- rapid pull availability;
- canonical confirmation.

---

## 41. Event privacy

An event may reveal sensitive information even without including record content.

For example:

```text
Alice updated a health-related private record.
```

may itself be sensitive.

Private events should minimise metadata and use authorised streams.

Possible protections include:

- opaque subjects;
- encrypted payloads;
- event-type generalisation;
- batched delivery;
- private source endpoints.

---

## 42. Encrypted events

Restricted or private events may be encrypted for the intended subscriber.

The event envelope may expose only:

- source;
- subscription;
- cursor;
- encrypted payload;
- delivery metadata.

The receiver must possess appropriate decryption authority.

Encryption must not prevent the receiver from detecting duplicates and stream order.

---

## 43. Public events

Public repositories may publish public event streams.

These may be used by:

- search indexes;
- feeds;
- archival services;
- mirrors;
- public analytics.

A public event stream should not expose:

- private record existence;
- private relationship changes;
- application grants;
- recovery secrets;
- internal provider data.

---

## 44. Public indexing event

A public indexing event may contain:

```json
{
  "type": "relay.record.updated",
  "subject": "relay://rid:relay:alice/com.relay.article/article_42",
  "collection": "com.relay.article",
  "visibility": "public",
  "version": 3,
  "commit": "sha256:commit-204..."
}
```

The indexer retrieves the current canonical record separately.

---

## 45. Deletion events

A deletion event should allow authorised systems to:

- remove the record from active indexes;
- stop serving cached content;
- update feeds;
- retain only permitted tombstone data;
- stop future notification.

The event should identify:

- Record URI;
- deleted version;
- deletion commit;
- visibility;
- cache-handling instruction where applicable.

---

## 46. Deletion propagation

Relay can notify subscribers that a record was deleted.

It cannot guarantee that every external party destroys all copies.

Compliant subscribers should define:

- deletion response time;
- cache-retention policy;
- legal retention exceptions;
- index-removal behaviour.

Deletion propagation is an operational and contractual requirement as well as a technical event.

---

## 47. Permission revocation propagation

When a Permission Grant is revoked:

- access-token issuance must stop;
- existing refresh authority must fail;
- delegated keys must be rejected;
- event subscriptions under the grant must terminate;
- private event delivery must cease.

The canonical authorisation service must enforce revocation even if a revocation event is delayed.

The event helps connected systems react quickly but does not replace enforcement.

---

## 48. Migration events

Migration may generate events such as:

```text
relay.repository.migration-started
relay.repository.destination-ready
relay.repository.write-freeze-started
relay.repository.migrated
relay.repository.source-retired
```

Applications use these events to:

- avoid stale writes;
- refresh identity resolution;
- obtain new provider-issued credentials;
- resume event subscriptions;
- update caches.

---

## 49. Final source event

After successful migration, the source provider should publish a final event containing:

- final source cursor;
- final Repository Head;
- destination Identity Document reference;
- migration effective time;
- source write status.

This gives subscribers a clean stream boundary.

---

## 50. Destination stream start

The destination should establish its event stream from the migrated final Repository Head.

It must not replay the entire repository history as new activity unless the subscriber explicitly requests historical backfill.

A destination may start with a cursor representing:

```text
migration-start at canonical head 204
```

---

## 51. Cursor portability

Provider-specific cursor formats may not be portable.

During migration, subscribers may use:

- final source cursor;
- final source Repository Head;
- destination starting cursor;
- migration receipt mapping.

The Repository Head is the stronger continuity anchor.

---

## 52. Synchronisation

**Synchronisation** is the process of bringing a local or remote copy into agreement with canonical repository state.

A synchronising system may be:

- application cache;
- mobile device;
- desktop client;
- read-only mirror;
- backup provider;
- search index;
- destination provider;
- offline workspace.

---

## 53. Synchronisation modes

Relay should support:

### Full synchronisation

Retrieve the complete repository or authorised scope.

### Incremental synchronisation

Retrieve changes after a known commit or cursor.

### Collection synchronisation

Synchronise selected collections.

### Record synchronisation

Refresh one specific record.

### Snapshot synchronisation

Retrieve the current state at a declared Repository Head.

### Event-assisted synchronisation

Use events to determine which canonical objects require retrieval.

---

## 54. Synchronisation anchor

A synchronising system should store a verifiable anchor such as:

- Repository Head;
- last processed commit;
- event cursor;
- snapshot identifier;
- record version.

The preferred repository-level anchor is the last verified Commit Identifier.

An event cursor alone may be insufficient if event retention expires or streams change providers.

---

## 55. Incremental synchronisation

A consumer with verified head:

```text
sha256:head-200
```

may request:

```text
All canonical commits after head-200.
```

The provider returns:

```text
Commit 201
Commit 202
Commit 203
Commit 204
```

The consumer verifies and applies them in order.

This is stronger than relying only on record-update notifications.

---

## 56. Commit-based synchronisation

Commit-based synchronisation is suitable for:

- mirrors;
- backups;
- migrations;
- local-first devices;
- full repository clients.

It preserves:

- atomic operations;
- commit order;
- repository integrity;
- exact state progression.

A simple feed reader may instead use filtered record events and current-record retrieval.

---

## 57. Change set

A **Change Set** is the collection of canonical changes required to move a consumer from one verified repository state to another.

Example:

```json
{
  "repository": "repo:relay:alice",
  "fromHead": "sha256:head-200...",
  "toHead": "sha256:head-204...",
  "commits": [
    "sha256:commit-201...",
    "sha256:commit-202...",
    "sha256:commit-203...",
    "sha256:commit-204..."
  ]
}
```

A Change Set must preserve commit ordering.

---

## 58. Snapshot

A **Snapshot** is a consistent representation of repository state at one Repository Head.

A snapshot may contain:

- repository metadata;
- current records;
- tombstones;
- state root;
- blob manifest;
- relevant schemas;
- verification proof.

Snapshots support:

- initial synchronisation;
- recovery;
- migration;
- large-client bootstrapping.

---

## 59. Snapshot plus delta

A common synchronisation method is:

1. retrieve a snapshot at head 180;
2. retrieve commits 181 through 204;
3. verify resulting head 204.

This prevents a new client from replaying an entire long repository history.

---

## 60. Partial snapshots

A consumer may request a snapshot limited to:

- public records;
- one collection;
- one date range;
- records authorised under a grant;
- metadata only.

The snapshot must clearly declare its scope.

A partial snapshot must not be presented as the complete repository state.

---

## 61. Synchronisation filtering

A filtered client may synchronise only:

```text
com.relay.post
com.relay.article
```

It should still track the repository head or collection-specific state needed to detect missed changes.

The protocol must define how collection filtering interacts with atomic commits containing operations across several collections.

---

## 62. Atomic commits and partial clients

Suppose one commit:

- creates an article;
- updates a project;
- attaches a blob.

A client synchronising only articles may apply only the article-relevant result.

However, it must preserve enough information to know:

- which commit produced it;
- that the full commit had additional operations;
- that its local view is partial.

It must not claim to hold the complete repository state.

---

## 63. Local view

A **Local View** is a partial or derived representation maintained by an application.

The local view should record:

- source repository;
- authorised scope;
- last verified Repository Head;
- included collections;
- excluded collections;
- last event cursor;
- synchronisation time;
- known gaps.

This helps prevent an application cache from being mistaken for the canonical repository.

---

## 64. Gap detection

A **Gap** occurs when a consumer may have missed one or more events or commits.

Possible causes include:

- expired event retention;
- failed webhook delivery;
- cursor mismatch;
- provider migration;
- client offline period;
- queue corruption;
- stream reset.

A consumer must detect gaps rather than silently continuing from an uncertain state.

---

## 65. Gap indicators

A gap may be detected when:

- received cursor jumps unexpectedly;
- previous event hash does not match;
- source reports earliest retained cursor later than requested cursor;
- known Repository Head does not appear in ancestry;
- migration changed stream identity;
- event count differs from commit changes.

The consumer should then initiate backfill or resynchronisation.

---

## 66. Backfill

**Backfill** retrieves missed historical events or canonical changes.

Backfill may use:

- event replay;
- commit history;
- snapshot plus delta;
- record collection comparison;
- migration receipt.

The consumer should prefer canonical commit-based backfill where event history is incomplete.

---

## 67. Event retention

Providers may retain events for a limited period.

Example:

```text
Public events: 30 days
Private application events: 14 days
Security events: 365 days
```

Retention policy must be disclosed.

Canonical repository history should remain the recovery source after ordinary event retention expires.

---

## 68. Replay

A subscriber may request replay from:

- Event Identifier;
- cursor;
- timestamp;
- Repository Head;
- subscription start.

Replay must respect current authority.

An application must not use a historical grant to replay private events after the grant has been revoked.

---

## 69. Replay and revocation

After revocation, a subscriber may retain access only to event data already lawfully received and retained under the approved policy.

It must not replay new private events.

The provider may still expose the subscriber’s own audit history where appropriate without revealing protected repository content.

---

## 70. Synchronisation conflict

A client may hold local unsynchronised changes while canonical state has advanced.

Example:

```text
Client edited version 3.
Repository is now at version 4.
```

The client must not overwrite version 4 automatically.

It should:

- retrieve the current record;
- compare changes;
- offer merge where safe;
- create a new authorised operation;
- or preserve a conflict copy.

---

## 71. Offline operation

A client may operate offline by storing:

- last verified Repository Head;
- local drafts;
- pending operations;
- local device signatures;
- synchronisation metadata.

Offline operations are not canonical until accepted by the repository.

The interface should make this distinction visible.

---

## 72. Pending operation

A **Pending Operation** is a locally created change awaiting canonical acceptance.

It should identify:

- target record;
- expected version;
- local creation time;
- authorising device or user;
- intended application grant;
- synchronisation status.

Pending operations may be:

```text
queued
submitted
accepted
rejected
conflicted
cancelled
```

---

## 73. Multi-device synchronisation

Several devices may interact with one repository.

Each device should:

- maintain its last verified head;
- receive or poll for changes;
- submit operations against expected state;
- handle stale-head rejection;
- preserve unsynchronised drafts;
- support device revocation.

One device must not assume that its local state is current merely because it was current when last opened.

---

## 74. Device event subscription

A device may subscribe to:

- repository updates;
- security events;
- application grant changes;
- device revocation;
- migration state.

A revoked device must stop receiving protected events.

---

## 75. Mirror synchronisation

A read-only mirror should synchronise using canonical commits or verified snapshots.

The mirror must publish:

- source repository;
- mirrored Repository Head;
- last synchronisation time;
- lag;
- read-only status;
- verification result.

The mirror must not accept canonical writes.

---

## 76. Backup synchronisation

A backup provider may maintain:

- complete commits;
- encrypted blobs;
- Identity Document history;
- verification metadata.

Backup synchronisation should be durable and capable of detecting missing changes.

A backup that receives only best-effort notifications without verifying commit continuity is insufficient for emergency restoration.

---

## 77. Index synchronisation

An indexer may synchronise only public or authorised records.

It should maintain:

- source Record URI;
- observed version;
- observed Repository Head;
- indexing time;
- deletion state;
- source visibility.

The index must remove or update records after receiving deletion or visibility-change events, subject to disclosed policy.

---

## 78. Feed generation

A feed service may subscribe to public record and relationship events.

It may derive:

- chronological feeds;
- topic feeds;
- relationship feeds;
- recommended feeds.

Feed entries are projections.

The canonical records remain in their source repositories.

---

## 79. Notification service

A notification application may subscribe to events such as:

- reply received;
- relationship request;
- credential issued;
- grant expiring;
- migration completed.

The notification itself may be local or derived.

It should retain a reference to the canonical subject event or record.

---

## 80. Event aggregation

An aggregation service may combine events from many repositories.

Examples include:

- public firehose;
- community stream;
- organisation activity stream;
- search indexing stream.

The aggregator must preserve:

- original event source;
- Event Identifier;
- subject;
- canonical references;
- original cursor where meaningful;
- aggregation receipt time.

It must not replace source attribution.

---

## 81. Aggregated event ordering

An aggregator may assign its own sequence for delivery.

That sequence represents the order observed by the aggregator.

It does not establish universal chronological truth across repositories.

The original source event metadata must remain available.

---

## 82. Firehose service

A **Firehose Service** may expose a high-volume stream of public Relay activity.

This can support:

- public search;
- analytics;
- discovery;
- archival research;
- feed services.

Firehose access must remain limited to information intentionally public and allowed for such distribution.

Usage rights and legal restrictions remain separate from technical visibility.

---

## 83. Firehose decentralisation

Relay should not require one global public firehose.

Multiple aggregators may exist.

Applications may choose:

- direct repository events;
- regional aggregators;
- topic aggregators;
- public-interest archives;
- commercial indexing services.

This avoids creating one new indispensable graph and activity owner.

---

## 84. Event provenance

An event should identify how it was generated.

Possible provenance includes:

- direct canonical source;
- provider-derived;
- aggregator-republished;
- application-derived;
- moderation-service-issued.

A republished event must retain the original source and Event Identifier.

---

## 85. Derived events

Applications may create derived events such as:

```text
relay.application.trending-topic-detected
relay.application.recommendation-ready
relay.application.summary-generated
```

These are not canonical repository events unless explicitly accepted into a repository.

Derived events must identify their producer and source inputs where appropriate.

---

## 86. Event schema

Events themselves require schemas.

An event schema should define:

- Event Type;
- required fields;
- data payload;
- visibility;
- security priority;
- acknowledgement requirements;
- canonical confirmation path;
- retention guidance.

Third-party events should use namespaced types.

---

## 87. Unknown event types

A receiver may encounter an event type it does not understand.

It should:

- preserve basic envelope information;
- avoid performing unknown side effects;
- acknowledge according to policy;
- safely ignore or store the event;
- refresh canonical state if the event indicates a changed Repository Head.

Unknown security-critical categories must default to cautious handling where identifiable.

---

## 88. Event versioning

Event types should be versioned where payload or semantics change materially.

A new optional field may not require a new major event type.

A change to:

- security meaning;
- acknowledgement requirement;
- ordering semantics;
- subject interpretation;

should require a new version or event type.

---

## 89. Application event permissions

A Permission Grant may specify:

```text
subscribe-events
```

and limit it by:

- collection;
- event type;
- duration;
- background access;
- visibility;
- installation.

Read permission alone should not always imply continuous background event delivery.

---

## 90. Event minimisation

Applications should subscribe only to events needed for their function.

For example, a publishing client may need:

- post changes;
- permission changes;
- migration changes.

It may not need:

- private relationships;
- credential events;
- moderation activity;
- unrelated blob updates.

Event minimisation is part of permission minimisation.

---

## 91. Subscription inspection

The user should be able to see:

- which applications receive events;
- which event types;
- which collections;
- whether delivery is continuous;
- last successful delivery;
- recent failures;
- expiration;
- associated Permission Grant.

---

## 92. Subscription revocation

The controller may revoke a subscription without revoking the entire application.

After revocation:

- new event delivery stops;
- replay authority stops;
- delivery credentials become invalid;
- the application may still use separately granted interactive access.

---

## 93. Provider event authority

A provider may emit operational events about its own services.

Examples:

```text
service-degraded
maintenance-started
repository-read-only
storage-limit-near
```

These are provider assertions.

They should not be confused with user-authorised repository commits.

---

## 94. Service status events

Service-status events may help applications choose between:

- retrying;
- using a mirror;
- entering read-only mode;
- refreshing resolution;
- warning the user.

Status events should be signed and time-limited.

---

## 95. Event spoofing

A malicious sender may attempt to trigger:

- fake deletion;
- false migration;
- credential theft;
- cache poisoning;
- unauthorised background processing.

Receivers must verify:

- source identity;
- signature;
- subscription;
- event type;
- authority;
- freshness;
- canonical state where necessary.

An event must never directly override identity or repository authority without verification.

---

## 96. Event-driven write actions

An application may react to an event by attempting another repository operation.

Example:

```text
When a draft is approved, publish an article.
```

The event does not itself grant write authority.

The application still needs a valid Permission Grant for the resulting operation.

Event receipt and operation authority remain separate.

---

## 97. Event loops

Two automated applications may create an unintended loop.

Example:

1. Application A updates Record X.
2. Application B reacts and updates Record Y.
3. Application A reacts to Y and updates X again.

Events should support provenance such as:

- originating application;
- triggering event;
- automation chain ID;
- depth;
- correlation ID.

Applications should use loop-prevention policies.

---

## 98. Correlation identifier

A workflow may use a **Correlation Identifier** across several events and commits.

Example:

```text
correlation: workflow_01JXB9
```

This helps group:

- import workflow;
- publishing workflow;
- migration;
- moderation review;
- automated processing.

The correlation identifier does not replace Event Identifiers or Commit Identifiers.

---

## 99. Causation reference

An event or operation may reference the event that caused it.

Example:

```json
{
  "causedBy": "event_01JXB4F7"
}
```

This supports:

- workflow tracing;
- audit;
- loop detection;
- automation explanation.

Causation should be declared where known.

---

## 100. Synchronisation audit

A provider or client may record:

- synchronisation started;
- source head;
- target head;
- commits applied;
- records refreshed;
- blobs transferred;
- conflicts;
- result;
- completion time.

This is especially important for:

- migrations;
- backups;
- mirrors;
- offline recovery.

---

## 101. Synchronisation receipt

A successful synchronisation may produce:

```json
{
  "source": "repo:relay:alice",
  "consumer": "rid:service:backup-one",
  "fromHead": "sha256:head-200...",
  "toHead": "sha256:head-204...",
  "commitsApplied": 4,
  "verified": true,
  "completedAt": "2026-08-24T18:05:00Z"
}
```

The receipt proves what the consumer claims to have synchronised.

---

## 102. Failed synchronisation

A synchronisation failure should report:

- last verified head;
- expected target head;
- missing commits;
- invalid signatures;
- unavailable blobs;
- schema failures;
- authority failure;
- retry status.

The consumer must not advance its recorded verified head beyond the last successfully verified commit.

---

## 103. Synchronisation and forks

If a consumer encounters a fork:

- it must stop linear canonical synchronisation;
- preserve both branch references;
- report the fork;
- avoid silently selecting a branch;
- await canonical resolution.

After a Resolution Commit, synchronisation may resume from the resolved branch.

---

## 104. Synchronisation and recovery

After identity recovery, a client must:

- refresh the Identity Document;
- validate replacement keys;
- identify the recognised Repository Head;
- discard or quarantine invalid branch updates;
- revalidate its Permission Grant;
- resume from the recovery state.

Recovery events should receive high priority.

---

## 105. Schema synchronisation

A consumer may need to retrieve a new schema before applying a record change.

An event or commit may reference:

- Schema Identifier;
- revision;
- schema hash.

The consumer should:

1. retrieve the schema from a verified source;
2. verify integrity;
3. validate the record;
4. preserve it if unsupported.

---

## 106. Blob synchronisation

Record events may indicate that a blob reference changed.

The consumer may retrieve blobs:

- immediately;
- lazily on demand;
- according to size policy;
- according to media type;
- according to storage limits.

A synchronisation state should distinguish:

```text
record synchronised
blob pending
blob verified
blob unavailable
```

---

## 107. Large blob delivery

Large blobs should not normally be embedded directly in event payloads.

Events should provide:

- Blob Identifier;
- size;
- media type;
- authorised retrieval method;
- integrity hash.

Transfers should support resumption and verification.

---

## 108. Rate limiting

Event sources may rate-limit:

- subscription creation;
- pull requests;
- replay;
- webhook retries;
- high-volume public streams.

Rate limits should be disclosed and must not prevent security-critical revocation enforcement.

Applications should use batching and incremental sync responsibly.

---

## 109. Backpressure

A subscriber may be unable to process events as quickly as they are produced.

The system may support:

- acknowledgement windows;
- maximum in-flight events;
- pause and resume;
- batch size controls;
- pull mode;
- lag reporting.

The source should not silently discard events without exposing a gap condition.

---

## 110. Subscriber lag

A subscription may report:

```text
current source cursor: 10,400
subscriber acknowledged cursor: 10,120
lag: 280 events
```

Lag may indicate:

- temporary backlog;
- failing subscriber;
- inadequate processing capacity;
- network problems.

The user or operator should be able to inspect persistent lag.

---

## 111. Event retention and backpressure

If a subscriber falls behind beyond event-retention limits, the source should report:

```text
cursor no longer available; canonical resynchronisation required
```

The subscriber then uses:

- latest snapshot;
- commit history;
- collection sync;
- migration mapping.

---

## 112. Multi-provider event sources

In a future unbundled architecture, separate providers may emit events for:

- identity;
- repository;
- vault;
- blobs;
- permissions.

Each source must have:

- a clear authority domain;
- separate cursor;
- separate signing keys;
- discoverable endpoint;
- defined event types.

Applications must not assume one universal provider stream.

---

## 113. Cross-source coordination

One workflow may involve several sources.

Example:

1. Permission Grant issued by authorisation service.
2. Repository record created.
3. Blob stored.
4. Index updated.

Relay v0.1 should not require a global distributed transaction across all services.

Instead, each source emits attributable events and systems reconcile through canonical state and workflow identifiers.

---

## 114. Eventual consistency

Some derived systems will be eventually consistent.

For example:

- follower count;
- search result;
- public feed;
- moderation index;
- analytics.

The canonical repository may update before derived systems reflect the change.

Applications should disclose stale or delayed derived state where materially relevant.

---

## 115. Strong consistency boundaries

Certain operations require stronger consistency:

- repository commit acceptance;
- Permission Grant revocation;
- migration activation;
- key rotation;
- fork resolution.

The authoritative service must enforce these directly.

Eventual event delivery must not weaken the canonical security decision.

---

## 116. User notifications versus protocol events

A protocol event is structured system information.

A user notification is an application-specific presentation.

One event may produce:

- no visible notification;
- one notification;
- a digest entry;
- a badge;
- an email;
- a mobile push.

The protocol should not prescribe one notification experience.

---

## 117. Push notification privacy

Mobile push providers may learn metadata.

Applications should avoid including sensitive record content in generic push payloads.

A push may say:

```text
Relay update available
```

and retrieve protected details after authenticated app activation.

---

## 118. Event deletion

Events may be retained for operational history even after the underlying record is deleted.

A retained event should minimise deleted content.

It may preserve:

- Event Identifier;
- type;
- Record URI;
- commit;
- occurrence time;
- deletion state.

Event retention must respect privacy and legal policy.

---

## 119. Event correction

If an event contained incorrect non-canonical metadata, the source may issue a correction event.

The original event should not be silently replaced where auditability matters.

A correction should reference:

- original Event Identifier;
- corrected fields;
- reason;
- canonical confirmation.

---

## 120. Event cancellation

Some proposed or scheduled events may be cancelled before canonical action occurs.

However, canonical events describing accepted repository changes should not be “cancelled” as though they never occurred.

A later reversal should be represented through a new canonical event.

---

## 121. Conformance requirements

A compliant Relay event implementation must:

- assign stable Event Identifiers;
- preserve source attribution;
- support ordered cursors within a stream;
- permit resumption;
- sign or authenticate delivery;
- support duplicate-safe processing;
- expose replay or canonical resynchronisation;
- stop protected delivery after revocation;
- distinguish canonical and derived events;
- expose gap conditions;
- preserve event-to-commit references where applicable.

---

## 122. Required v0.1 event operations

A compliant implementation must support:

```text
Publish repository event
Publish identity event
Publish Permission Grant event
Create event subscription
Authorise subscription
Filter subscription
Read event stream
Read events after cursor
Deliver signed webhook
Acknowledge delivery
Retry failed delivery
Detect duplicate event
Pause subscription
Resume subscription
Revoke subscription
Report delivery failure
Request event replay
Report cursor gap
Initiate canonical resynchronisation
Retrieve commits after known head
Create repository snapshot
Apply incremental Change Set
Verify synchronised Repository Head
Detect synchronisation conflict
Detect repository fork
Produce synchronisation receipt
```

Public firehose aggregation and encrypted event payloads may remain optional in the first reference implementation.

---

## 123. Event invariants

The following rules must always remain true.

### Invariant 1

An event is a notification of canonical or derived state; it is not automatically the canonical state itself.

### Invariant 2

A retry of the same event retains the same Event Identifier.

### Invariant 3

Receivers must be able to process duplicate deliveries safely.

### Invariant 4

Event delivery must not grant access beyond the subscriber’s Permission Grant.

### Invariant 5

Revoking a grant terminates protected event delivery under that grant.

### Invariant 6

A repository event caused by a commit references that commit or Repository Head.

### Invariant 7

A delivery cursor orders events within its stream, not necessarily across all Relay identities.

### Invariant 8

A missed-event gap must be detectable.

### Invariant 9

Expired event history must be recoverable through canonical repository synchronisation where authorised.

### Invariant 10

Provider migration must establish a clear boundary between the source and destination event streams.

### Invariant 11

An event must not announce successful canonical action before that action is accepted.

### Invariant 12

Derived events must identify their producer and must not impersonate repository events.

### Invariant 13

Private event metadata must not be exposed through public streams.

### Invariant 14

A synchronising client must not advance beyond its last verified canonical state.

### Invariant 15

A fork must interrupt ordinary linear synchronisation until resolved.

---

## 124. Compliance scenario

A basic Event and Synchronisation implementation should pass the following test.

### Initial state

Alice’s repository is at:

```text
Repository Head:
sha256:head-200
```

Application A has permission to:

- read Alice’s public posts;
- subscribe to public post events.

Application B has permission to:

- read and update Alice’s posts;
- subscribe to post and permission events.

### Subscription creation

Application A creates a subscription beginning at cursor 200.

Application B creates a separate subscription beginning at cursor 200.

Each subscription is limited to its approved event scope.

### Record update

Application B updates:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

The repository accepts Commit 201.

The repository publishes:

```text
relay.record.updated
```

referencing Commit 201 and the new Repository Head.

### Duplicate delivery

Application A’s webhook acknowledgement is lost.

The source retries the same event with the same Event Identifier.

Application A recognises the duplicate and does not create a second feed entry.

### Offline period

Application A goes offline.

Alice’s repository advances through Commit 205.

When Application A returns, it requests events after its last acknowledged cursor.

It receives events 202 through 205 and refreshes the relevant canonical records.

### Event-retention gap

Application A later remains offline beyond the source’s event-retention period.

Its previous cursor is no longer available.

The source reports a gap.

Application A requests a collection snapshot plus canonical commits after the snapshot and verifies the resulting Repository Head.

### Permission revocation

Alice revokes Application B’s grant.

The authorisation service enforces revocation immediately and emits:

```text
relay.permission.revoked
```

Application B can no longer:

- obtain new tokens;
- submit repository updates;
- receive protected events.

The event assists Application B in cleaning up its session but is not the only enforcement mechanism.

### Migration

Alice migrates to Provider B.

Provider A publishes its final source event with:

- final cursor;
- final Repository Head;
- destination document reference.

Application A refreshes identity resolution and subscribes to Provider B’s destination stream from the migration boundary.

Historical events are not replayed as new activity.

### Fork detection

Application A receives a Repository Head that does not descend from its last verified head.

It pauses synchronisation and reports a possible fork rather than silently applying the new branch.

If all these actions occur without duplicate side effects, silent gaps, unauthorised delivery or confusion between events and canonical state, the implementation satisfies the basic Relay Event and Synchronisation objective.

---

## 125. Open design questions

### 125.1 Event transport

Which transports should Relay v0.1 require:

- signed webhooks;
- pull API;
- Server-Sent Events;
- WebSockets;
- another stream protocol?

### 125.2 Cursor format

Should event cursors be:

- commit sequence numbers;
- opaque tokens;
- Commit Identifiers;
- source-specific compound values?

### 125.3 Event retention

What minimum retention should compliant providers offer for:

- public events;
- application events;
- security events?

### 125.4 Event signing

Should each event be signed individually, or may a signed delivery batch be sufficient?

### 125.5 Private-event encryption

Should encrypted event payloads be included in v0.1 or deferred?

### 125.6 Collection synchronisation

How should partial clients verify collection completeness without downloading the full Repository State Root?

### 125.7 Migration cursor mapping

What exact mechanism maps a final source stream position to a destination starting position?

### 125.8 Public firehose

Should Relay define a standard public aggregation stream in v0.1?

### 125.9 Event schema governance

Which event types belong in the Relay core namespace?

### 125.10 Coalescing

Which events may be safely coalesced, and which must always be delivered individually?

### 125.11 Offline local commits

How should locally signed pending commits integrate with event-driven multi-device synchronisation?

### 125.12 Security event delivery

Should high-risk identity and revocation events require delivery to an independently registered recovery channel?

---

## 126. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- canonical repository changes generate structured events;
- events reference canonical commits or objects;
- Event Identifiers remain stable across retries;
- delivery is at least once;
- receivers process events idempotently;
- providers support a cursor-based pull API;
- providers may additionally support signed webhooks;
- subscriptions are limited by Permission Grants;
- protected subscriptions terminate after revocation;
- event gaps are detectable;
- canonical commit synchronisation repairs missing event history;
- one event stream has one ordered cursor domain;
- cross-repository events have no universal total order;
- security-critical events receive durable treatment;
- public and private event streams remain separate;
- migration establishes an explicit source and destination stream boundary;
- Repository Head remains the primary synchronisation anchor;
- full public firehose aggregation is optional;
- encrypted private event payloads may be deferred beyond the first reference implementation.

---

## 127. Core event principle

The Event and Synchronisation Model can be reduced to one rule:

> Relay events tell authorised systems that canonical state has changed, while signed repositories and identity documents remain the authority that proves what changed.

The next core object is the **Relay Provider and Service Compliance Model**: how hosting providers, resolvers, authorisation services, mirrors and other infrastructure operators declare their capabilities, fulfil portability obligations and prove that they are not silently recreating platform lock-in.