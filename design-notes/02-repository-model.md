# Relay Protocol v0.1  
## Core Object 2: Relay Repository

### 1. Definition

A **Relay Repository** is the canonical, portable and verifiable collection of records associated with a Relay Identity.

It stores the identity’s authorised digital records independently of the applications used to create, display or interact with them.

The repository must be capable of surviving:

- a change of application;
- a change of Relay Provider;
- a change of device;
- a change of handle;
- key rotation;
- temporary service interruption;
- migration between compatible implementations.

A Relay Repository is not simply a database account or downloaded archive.

It is an operational record system that compatible applications can continue to use.

---

## 2. Purpose

The repository exists to preserve **record continuity**.

It must allow a person to:

- create records through one application;
- access those records through another application;
- verify who authorised each record;
- inspect the sequence of repository changes;
- export the repository in a standard format;
- migrate it to another Relay Provider;
- continue using it after migration.

The repository is the canonical source for records under the identity’s authority.

Applications may maintain temporary indexes, caches or derived views, but those copies must not silently replace the repository as the authoritative source.

---

## 3. Repository authority

A Relay Repository is associated with exactly one Relay Identity.

Example:

```text
Relay Identity:
rid:relay:7fs82k9m4v

Repository:
repo:relay:7fs82k9m4v
```

The repository may use the same underlying identifier component as the Relay Identity, but identity and repository remain conceptually distinct.

The identity defines:

- who the entity is;
- who controls it;
- where its services are located.

The repository defines:

- which records belong to that identity’s canonical history;
- how those records are organised;
- how changes are authorised and verified.

---

## 4. Repository components

A Relay Repository consists of the following components:

1. **Repository Identifier**
2. **Record Collections**
3. **Records**
4. **Blobs**
5. **Commits**
6. **Repository Head**
7. **Schema References**
8. **Export Manifest**

These components must be portable between compliant Relay Providers.

---

## 5. Repository Identifier

The **Repository Identifier** uniquely identifies the canonical repository associated with a Relay Identity.

It must not depend on the current Relay Provider’s domain or infrastructure.

The repository identifier may be derived from, or directly associated with, the Relay Identifier.

Example:

```text
repo:relay:7fs82k9m4v
```

Changing providers must not create a new canonical repository.

A provider may create an internal storage identifier, but that identifier is implementation-specific and must not replace the protocol-level Repository Identifier.

---

## 6. Record

A **Record** is the smallest independently addressable structured object stored in a Relay Repository.

Examples may include:

- profile information;
- posts;
- articles;
- projects;
- photographs;
- comments;
- reactions;
- relationship declarations;
- application preferences;
- public contact methods;
- credentials;
- permission declarations;
- deletion markers.

A record must contain enough information to determine:

- its type;
- its identity within the repository;
- its authorising identity;
- its creation time;
- its current version;
- its schema;
- its content;
- its integrity hash;
- and, where required, its signature.

Example:

```json
{
  "uri": "relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A",
  "repository": "repo:relay:7fs82k9m4v",
  "collection": "com.relay.post",
  "recordKey": "post_01JX9A",
  "schema": "com.relay.post.v1",
  "createdAt": "2026-08-24T10:00:00Z",
  "updatedAt": "2026-08-24T10:00:00Z",
  "authorisedBy": "rid:relay:7fs82k9m4v",
  "content": {
    "text": "My first Relay post."
  }
}
```

The exact representation remains provisional.

---

## 7. Record URI

Every record must have a stable protocol-level address.

A possible structure is:

```text
relay://<relay-identifier>/<collection>/<record-key>
```

Example:

```text
relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A
```

The record URI must remain unchanged when:

- the repository changes provider;
- the record is read through another application;
- the record’s content is updated;
- the identity changes handle.

The URI identifies the logical record.

A specific version of the record may additionally be identified using a version, commit or content hash.

---

## 8. Collection

A **Collection** groups records of a related schema family.

Examples:

```text
com.relay.profile
com.relay.post
com.relay.article
com.relay.project
com.relay.relationship
com.relay.permission
com.relay.credential
```

Collections provide a predictable way for applications to request only the categories of records they understand or are authorised to access.

An application might request:

```text
Read:
com.relay.profile
com.relay.post
com.relay.project
```

without receiving access to all repository contents.

### 8.1 Collection ownership

The namespace of a collection indicates who defines its schema, not who owns the resulting record.

For example:

```text
com.example.photography.portfolio
```

may be defined by a photography application or standards body.

A record created using that schema remains part of the person’s repository and is not owned by the schema publisher merely because it uses that namespace.

### 8.2 Core and external collections

Relay may define a small set of protocol-level core collections.

Third parties may define additional application-specific collections.

A compliant repository must preserve unknown collections even when the current provider or application does not understand them.

This prevents migration from destroying records merely because the receiving system lacks a native interface for them.

---

## 9. Record key

The **Record Key** uniquely identifies a record within its collection.

Example:

```text
post_01JX9A
```

Record keys should be:

- unique within the collection;
- stable for the lifetime of the logical record;
- non-semantic where practical;
- independent of visible titles or filenames;
- safe to use in URLs and exports.

Changing a post title, profile name or project label must not change its Record Key.

---

## 10. Record lifecycle

A record may move through the following lifecycle:

```text
created
active
updated
deleted
restored
superseded
```

Not every record type must support every state.

### 10.1 Create

A new record is introduced into the repository.

Creation must be authorised by:

- the Relay Identity;
- or an application holding a valid permission grant.

### 10.2 Read

A record may be read by:

- the controller;
- an authorised application;
- an external observer if the record is public.

### 10.3 Update

An update changes the current content of an existing logical record.

An update must not silently erase repository history.

The repository should retain enough information to prove:

- that an earlier version existed;
- when the update occurred;
- who authorised it;
- which version became current.

### 10.4 Delete

Deletion marks a record as no longer active or available.

The protocol must distinguish between:

- logical deletion;
- content removal;
- cryptographic history;
- external copies already made by other parties.

### 10.5 Restore

Where permitted, a deleted record may be restored through a new authorised change.

### 10.6 Supersede

Some records may be replaced by a different record rather than updated in place.

For example, a credential or policy document may point to a newer record that supersedes it.

---

## 11. Immutable history and mutable content

Relay must support both:

- an auditable history of repository changes;
- the practical need to update or remove content.

These requirements are not contradictory.

The repository may preserve evidence that a change occurred without permanently retaining all prior content in publicly retrievable form.

For example, after deleting a photograph, the repository might retain:

```json
{
  "action": "delete",
  "record": "relay://rid:relay:7fs82k9m4v/com.relay.photo/photo_123",
  "previousContentHash": "sha256:...",
  "deletedAt": "2026-08-25T12:00:00Z"
}
```

The photograph itself may be removed from storage.

The remaining history proves that a record with a particular hash was deleted, without continuing to expose the original file.

---

## 12. Commit

A **Commit** is an authorised, verifiable set of repository operations.

A commit may contain one or more actions:

- create record;
- update record;
- delete record;
- add blob;
- detach blob;
- update repository metadata.

Example:

```json
{
  "repository": "repo:relay:7fs82k9m4v",
  "commitId": "sha256:4be1...",
  "previousCommit": "sha256:31fd...",
  "createdAt": "2026-08-24T10:00:00Z",
  "operations": [
    {
      "action": "create",
      "record": "relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A",
      "contentHash": "sha256:98c2..."
    }
  ],
  "authorisedBy": {
    "identity": "rid:relay:7fs82k9m4v",
    "key": "key-signing-3"
  },
  "signature": "..."
}
```

### 12.1 Commit requirements

Every commit must:

- identify the repository;
- identify the previous valid commit;
- list its operations;
- include a creation time;
- identify the authorising authority;
- contain or reference an integrity hash;
- contain a valid signature.

### 12.2 Atomicity

A commit must be applied atomically.

Either all operations in the commit become valid, or none do.

An application must not observe a partially applied commit.

### 12.3 Ordered history

Commits form an ordered history.

Each valid commit points to the previous valid commit.

This creates a verifiable chain of repository state changes without requiring a public blockchain.

---

## 13. Repository Head

The **Repository Head** identifies the latest valid commit.

Example:

```text
Repository Head:
sha256:4be1...
```

Applications can compare repository heads to determine whether:

- the repository has changed;
- a local cache is current;
- migration copied the complete history;
- two providers disagree about repository state.

The Repository Head must be signed or verifiable through the latest commit.

---

## 14. Integrity structure

Relay v0.1 should use a content-integrity structure that allows verification of repository state.

Possible approaches include:

- a hash-linked commit chain;
- a Merkle tree;
- a Merkle search tree;
- a content-addressed directed acyclic graph;
- another deterministic authenticated data structure.

The final choice remains open.

The structure must support:

- verifying individual records;
- verifying complete repository state;
- efficient synchronisation;
- detecting missing or altered content;
- comparing two repository versions;
- migration validation.

Relay v0.1 does not require global consensus over the repository state.

The controller’s authorised commit history defines the valid state.

---

## 15. Signatures

Repository commits must be signed by an authority valid for the Relay Identity at the time of the commit.

The signature proves that the change was authorised.

A signature does not necessarily prove:

- that every statement inside the record is factually true;
- that the record was personally typed by the human controller;
- that the application creating it behaved honestly.

It proves that the repository accepted the change under valid authority.

### 15.1 Application-created records

An application may create records using delegated authority.

The repository history should distinguish between:

- the controlling identity;
- the application that submitted the operation;
- the key or permission grant used;
- the final repository authorisation.

Example:

```json
{
  "controller": "rid:relay:7fs82k9m4v",
  "submittedByApplication": "rid:app:photo-client",
  "permissionGrant": "grant_01JX8K",
  "signedBy": "delegated-key-7"
}
```

This creates an audit trail without making the application the owner of the record.

---

## 16. Record provenance

A record should support provenance metadata describing how it entered the repository.

Possible provenance information includes:

- created directly by the controller;
- created by an authorised application;
- imported from another service;
- generated by an AI system;
- derived from another record;
- issued by an external credential authority;
- migrated from an earlier repository format.

Example:

```json
{
  "provenance": {
    "method": "application-created",
    "application": "rid:app:writing-client",
    "sourceRecord": null,
    "aiAssistance": "declared"
  }
}
```

Provenance must be factual and structured where possible.

It must not become a universal judgement about originality, quality or human authorship.

---

## 17. Blob

A **Blob** is a binary object associated with one or more records.

Examples include:

- images;
- audio;
- video;
- PDFs;
- archives;
- design files;
- attachments.

A blob should be identified by a content hash.

Example:

```text
blob:sha256:84b3...
```

Blob metadata may include:

```json
{
  "blobId": "blob:sha256:84b3...",
  "mediaType": "image/jpeg",
  "size": 2841934,
  "createdAt": "2026-08-24T10:00:00Z",
  "storageLocation": "https://media.provider.example/blobs/84b3..."
}
```

### 17.1 Content addressing

Where practical, a blob’s protocol-level identity should be derived from its content hash.

Changing the blob content creates a new blob identity.

### 17.2 Storage location independence

The storage URL is not the blob’s permanent identity.

A blob may move between storage providers while retaining the same content hash.

### 17.3 Deduplication

A provider may store one physical copy of identical blobs referenced by multiple records or repositories.

Deduplication must not weaken access controls or deletion obligations.

### 17.4 Blob deletion

Deleting a record does not always require immediate deletion of its blobs.

A blob may still be referenced by another active record.

A blob may be removed when:

- no active records reference it;
- no legal or retention obligation requires it;
- no user-selected backup policy retains it.

---

## 18. Public, restricted and private records

Every record must have a defined access classification.

Relay v0.1 may support:

### Public

Readable without a private permission grant.

### Restricted

Readable only by specified identities, applications or permission holders.

### Private

Readable only by the controller and explicitly authorised services.

The first reference implementation may focus primarily on public and restricted records.

Highly sensitive private-vault data may require additional encryption and threat modelling beyond the base repository.

### 18.1 Classification is not ownership

Making a record public does not transfer ownership to applications, providers or observers.

Public access and legal usage rights are separate questions.

### 18.2 Classification changes

A record may change from:

- private to public;
- public to restricted;
- restricted to private.

Changing classification affects future authorised access.

It cannot guarantee deletion of copies already obtained while access was valid.

---

## 19. Encryption

Public records may be stored unencrypted at rest, subject to provider security practices.

Restricted and private records should support encryption.

The protocol must distinguish between:

- encryption controlled only by the provider;
- encryption controlled through identity-associated keys;
- end-to-end encryption in which the provider cannot read the content.

Relay v0.1 does not need to standardise every encryption mode, but exports and migrations must preserve the ability to decrypt authorised records.

A provider migration must not leave the user with encrypted data whose only decryption key belongs to the former provider.

---

## 20. Schema

Every structured record must declare a **Schema**.

The schema defines:

- required fields;
- optional fields;
- data types;
- validation rules;
- record semantics;
- version;
- compatibility expectations.

Example:

```text
com.relay.post.v1
```

### 20.1 Versioning

Schema versions must be explicit.

A new schema version may:

- add optional fields;
- change field meaning;
- remove fields;
- introduce new validation rules.

Breaking changes require a new major schema version.

### 20.2 Unknown schemas

A compliant provider must preserve records using unknown schemas.

It may decline to interpret, render or validate application-specific semantics beyond basic structural and security checks.

### 20.3 Schema availability

Schemas must be retrievable from a stable registry or another verifiable location.

A schema should include:

- namespace owner;
- version;
- publication date;
- integrity hash;
- compatibility information.

### 20.4 Schema authority

Publishing a schema does not grant the publisher authority over records created using it.

Applications must not be able to revoke or disable user records simply by withdrawing the schema definition.

---

## 21. Canonical and derived records

The repository should distinguish between **canonical records** and **derived records**.

### Canonical record

A record directly accepted into the identity’s authoritative repository history.

Examples:

- a post;
- profile details;
- a relationship declaration;
- a portfolio item.

### Derived record

A record calculated from other records.

Examples:

- a feed ranking;
- a reputation score;
- an AI-generated summary;
- an analytics result;
- an inferred interest category.

Derived records must identify:

- their source records where possible;
- the system that produced them;
- the time of derivation;
- whether they are canonical or merely cached results.

An application must not silently promote an external inference into the person’s canonical repository without permission.

---

## 22. External references

A Relay record may refer to records outside its own repository.

Example:

```json
{
  "replyTo": "relay://rid:relay:another-user/com.relay.post/post_88A"
}
```

External references must use stable protocol-level identifiers where available.

A record should not rely solely on a temporary provider URL.

The repository cannot guarantee that externally controlled records will remain available.

It may retain:

- the external URI;
- a content hash;
- limited quoted context;
- a timestamp;
- a relationship type.

---

## 23. Repository export

A Relay Repository must be exportable in a documented, provider-independent format.

An export must contain, or reliably reference:

- Repository Identifier;
- Relay Identifier;
- Identity Document reference;
- collections;
- records;
- commits;
- current Repository Head;
- schemas or schema references;
- blobs or blob manifests;
- permission metadata required for continuity;
- integrity hashes;
- signatures;
- export timestamp;
- export format version.

A possible structure is:

```text
relay-export/
├── manifest.json
├── identity/
│   └── identity-document.json
├── repository/
│   ├── head.json
│   ├── commits/
│   └── records/
├── blobs/
├── schemas/
└── verification/
```

### 23.1 Export completeness

An export must declare whether it is:

- complete;
- partial;
- public-only;
- metadata-only;
- date-limited;
- collection-limited.

A provider must not label an incomplete archive as a complete Relay export.

### 23.2 Export verification

The receiving system must be able to verify:

- that records match their hashes;
- that commits form a valid sequence;
- that signatures were valid;
- that the declared Repository Head matches the exported state.

---

## 24. Repository migration

Migration transfers operational hosting of the repository from one compatible provider to another.

Migration is not merely downloading a copy.

A successful migration must result in the new provider being able to:

- serve the repository;
- accept authorised commits;
- provide current records;
- preserve record URIs;
- preserve commit history;
- preserve blob references or copies;
- prove repository integrity;
- continue authorised application access where permitted;
- become discoverable through the Identity Document.

### 24.1 Migration stages

A migration may use the following stages:

```text
requested
exporting
transferring
verifying
synchronising
activating
completed
failed
rolled back
```

### 24.2 Final synchronisation

If the repository remains active during transfer, the providers must synchronise commits created after the initial export.

### 24.3 Activation

The new provider becomes authoritative only after:

- the repository is verified;
- final synchronisation is complete;
- the Identity Document points to the new provider;
- the new provider confirms readiness.

### 24.4 Old provider behaviour

After migration, the old provider may temporarily:

- redirect repository requests;
- serve a migration notice;
- forward events;
- retain a backup according to policy.

It must not continue accepting new authoritative commits unless the migration is reversed or a defined multi-provider model is being used.

---

## 25. Forks and conflicting histories

A repository may develop conflicting histories if:

- two providers accept commits simultaneously;
- an offline device submits changes after migration;
- a compromised key signs unauthorised commits;
- network partitions occur;
- a migration is incorrectly completed twice.

Relay must detect rather than silently merge conflicting commit histories.

### 25.1 Fork detection

A fork exists when two valid-looking commits reference the same previous commit but produce different successors.

### 25.2 Fork resolution

Relay v0.1 should use an explicit resolution operation authorised by the identity controller.

Possible outcomes include:

- select one branch;
- create a reconciled commit;
- invalidate a compromised branch;
- retain both branches as historical evidence while designating one canonical head.

Automatic last-write-wins behaviour is unsuitable for high-authority repository history.

---

## 26. Caching

Applications and indexers may cache repository records.

A cache must not present itself as the canonical repository.

Cached data should retain:

- original Record URI;
- source Relay Identifier;
- source Repository Identifier;
- content hash;
- observed commit or version;
- retrieval time.

Applications should define:

- cache duration;
- update behaviour;
- deletion propagation;
- handling of stale records.

A provider migration must not require every cached copy to change its canonical identifiers.

---

## 27. Indexes

A repository is not required to provide global search or discovery.

Separate indexers may process public records and offer:

- search;
- feeds;
- recommendations;
- analytics;
- moderation labels;
- topic indexes.

Indexes are derived services.

They do not become the canonical owner of indexed records.

An indexer should retain enough provenance to identify:

- the source repository;
- the source record;
- the version indexed;
- when it was observed.

---

## 28. Repository availability

A Relay Provider should expose service availability and repository status.

Possible states include:

```text
available
read-only
migrating
temporarily unavailable
suspended
archived
terminated
```

A repository becoming unavailable does not mean its Relay Identity has ceased to exist.

Applications should distinguish between:

- unresolved identity;
- unavailable repository;
- deleted record;
- suspended provider;
- blocked identity.

---

## 29. Repository deletion

Deleting a repository is a high-authority operation.

It may affect:

- all canonical records;
- blobs;
- commit availability;
- connected applications;
- relationships;
- external references;
- credentials.

The protocol must distinguish between:

### Repository deactivation

No new commits are accepted, but records remain available.

### Repository archival

The repository becomes read-only and may be moved to archival storage.

### Repository erasure

Stored content is permanently removed where technically and legally possible.

### Identity termination

The associated Relay Identity is retired.

These operations must not be represented as interchangeable.

Relay v0.1 should require a verified export or explicit waiver before a managed provider completes destructive repository erasure.

---

## 30. Provider obligations

A compliant Relay Provider must:

- preserve record identifiers;
- preserve unknown collections;
- verify authorised commits;
- prevent unauthorised repository changes;
- provide a standard export;
- support migration;
- expose the current Repository Head;
- maintain sufficient history for verification;
- distinguish public, restricted and private records;
- report repository status accurately;
- avoid claiming ownership merely through hosting.

A provider may impose:

- storage limits;
- acceptable-use policies;
- pricing;
- lawful content restrictions;
- security controls.

Those conditions must not alter the protocol’s underlying portability requirements.

---

## 31. Application obligations

A compliant application interacting with a repository must:

- request only required permissions;
- use stable Record URIs;
- identify itself when creating records;
- respect record classifications;
- handle revocation;
- avoid presenting cached data as canonical;
- preserve provenance when transforming records;
- avoid changing unknown records;
- submit operations through valid repository interfaces.

An application must not require the person to surrender their Repository Identifier as a condition of use.

---

## 32. Required v0.1 repository operations

A compliant implementation must support:

```text
Create repository
Read repository metadata
Read Repository Head
List collections
Read record
Create record
Update record
Delete record
List record versions
Verify record
Submit commit
Verify commit
List commits
Upload blob
Read blob metadata
Export repository
Import repository
Verify export
Initiate migration
Synchronise migration
Complete migration
Detect conflicting history
```

Some operations may be restricted according to record classification and permission grants.

---

## 33. Repository invariants

The following rules must always remain true.

### Invariant 1

Changing Relay Provider does not change the Repository Identifier.

### Invariant 2

Changing Relay Provider does not change existing Record URIs.

### Invariant 3

Every accepted repository change belongs to a valid authorised commit.

### Invariant 4

Every valid commit points to the previous canonical commit, except the initial commit.

### Invariant 5

An application cannot become the canonical owner of a record merely because it created or displayed it.

### Invariant 6

Unknown but structurally valid collections survive export and migration.

### Invariant 7

A record update does not silently erase evidence that a previous version existed.

### Invariant 8

A deleted blob is not considered available merely because its hash remains in repository history.

### Invariant 9

A cache or index does not become the canonical repository.

### Invariant 10

A migration is not complete until the receiving repository has been verified and made discoverable.

### Invariant 11

Two conflicting repository heads must not both be presented as the single canonical state.

### Invariant 12

Provider-specific internal identifiers must not replace protocol-level identifiers.

---

## 34. Compliance scenario

A basic repository implementation should pass the following test.

### Initial state

A person has:

```text
Relay Identity:
rid:relay:7fs82k9m4v

Repository:
repo:relay:7fs82k9m4v

Provider:
Provider A
```

### Action 1: Create through Application X

Application X receives permission to create posts.

It creates:

```text
relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A
```

The record is included in a signed commit.

### Action 2: Read through Application Y

Application Y receives read permission for the post collection.

It retrieves and displays the same canonical post.

No copying or manual import is required.

### Action 3: Update through Application Y

Application Y updates the post.

A new commit is created.

The Record URI remains unchanged.

The prior version remains historically verifiable.

### Action 4: Revoke Application X

The person revokes Application X’s permission.

Application X can no longer create repository records.

The post it previously created remains in the person’s repository.

### Action 5: Migrate to Provider B

The repository is exported, transferred and verified.

The Identity Document is updated to point to Provider B.

The Repository Identifier and Record URI remain unchanged.

### Action 6: Continue through Application Y

Application Y resolves the identity, discovers Provider B and retrieves the updated post.

The person does not re-upload the post or recreate the application account.

If these actions occur without losing record identity, history or application continuity, the implementation satisfies the basic Relay Repository objective.

---

## 35. Open design questions

### 35.1 Repository data structure

Which authenticated data structure best balances:

- verification;
- synchronisation;
- mutation;
- implementation complexity;
- partial retrieval?

### 35.2 Commit granularity

Should applications create one commit per action, or may providers batch several authorised actions into one commit?

### 35.3 Record signatures

Should every record be individually signed, or is signing the containing commit sufficient?

### 35.4 Historical retention

How much previous record content must a compliant provider retain?

### 35.5 Tombstones

What minimum deletion metadata must remain after record content is removed?

### 35.6 Private records

Should restricted and private records exist in the same repository structure as public records, or in a separate encrypted repository?

### 35.7 Fork resolution

What exact rules determine the canonical branch after conflicting histories arise?

### 35.8 Blob portability

Must every migration physically copy all blobs, or may a verified external storage reference remain valid?

### 35.9 Large repositories

How should partial synchronisation and collection-based migration work for repositories containing very large media histories?

### 35.10 Schema registry

Should Relay operate one canonical schema registry, use distributed schema publication, or support both?

---

## 36. Provisional decisions for v0.1

To keep the first implementation achievable, Relay v0.1 will provisionally assume:

- one canonical repository per Relay Identity;
- one primary Relay Provider at a time;
- stable Record URIs;
- schema-based JSON records;
- content-addressed blobs;
- signed hash-linked commits;
- one current canonical Repository Head;
- provider-independent export format;
- migration through copy, verification, synchronisation and identity update;
- preservation of unknown collections;
- logical deletion with retained tombstone metadata;
- no public blockchain;
- public and moderately restricted records as the initial focus;
- explicit detection of repository forks;
- manual controller-authorised resolution of conflicting histories.

---

## 37. Core repository principle

The repository model can be reduced to one rule:

> A Relay Repository is the identity’s portable source of record truth, not the private database of whichever application or provider currently serves it.

The next core object is the **Relay Record Model** in greater detail: how record schemas, authorship, visibility, revisions, deletion and interoperability work across applications.