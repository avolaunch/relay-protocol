# Relay Protocol v0.1  
## Core Object 3: Relay Record Model

### 1. Definition

A **Relay Record** is a structured, independently addressable unit of information accepted into a Relay Repository.

A record represents a specific object, statement, action or relationship associated with a Relay Identity.

Examples include:

- a profile;
- a post;
- an article;
- a project;
- a photograph;
- a comment;
- a reaction;
- a relationship declaration;
- an application preference;
- a credential;
- a permission grant;
- a moderation label;
- a deletion marker.

A record is not defined by the application that created it.

An application may create, edit or display a record, but the record belongs to the repository in which it was authorised.

---

## 2. Purpose

The Relay Record Model exists to make digital objects usable across applications without making every application interpret all information identically.

It must provide enough consistency for applications to:

- locate a record;
- determine its type;
- validate its structure;
- verify its repository history;
- understand who authorised it;
- determine its visibility;
- identify its current version;
- preserve it during migration;
- and refer to it from other records.

At the same time, the model must allow third parties to introduce new record types without requiring permission from a central platform.

---

## 3. Record envelope and record content

Every Relay Record consists of two conceptual layers:

1. the **Record Envelope**;
2. the **Record Content**.

The envelope contains protocol-level metadata required for identification, verification, access and interoperability.

The content contains the information defined by the record’s schema.

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
  "visibility": {
    "classification": "public"
  },
  "authorisation": {
    "controller": "rid:relay:7fs82k9m4v",
    "submittedBy": "rid:app:writing-client",
    "grant": "grant_01JX8K"
  },
  "content": {
    "text": "My first Relay post."
  }
}
```

The exact serialisation remains provisional.

---

## 4. Required envelope fields

Every active Relay Record must include or inherit the following information:

- Record URI;
- Repository Identifier;
- collection;
- Record Key;
- schema identifier;
- creation time;
- current update time;
- authorising Relay Identity;
- visibility classification;
- content;
- integrity reference.

Additional fields may be required depending on the schema or operation.

---

## 5. Record URI

The **Record URI** is the stable identifier of the logical record.

Example:

```text
relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A
```

The Record URI must remain stable when:

- the record is edited;
- the repository changes providers;
- the identity changes handles;
- another application displays it;
- the media storage location changes.

The Record URI identifies the logical object, not one particular version of its content.

---

## 6. Record version

Each accepted change to a record creates a new **Record Version**.

A version may be identified by:

- the commit in which it was accepted;
- a monotonically increasing version number;
- a content hash;
- or a combination of these.

Example:

```json
{
  "record": "relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A",
  "version": 3,
  "commit": "sha256:4be1...",
  "contentHash": "sha256:98c2..."
}
```

### 6.1 Logical identity versus version identity

The Record URI identifies the continuing logical record.

A version reference identifies a particular historical state.

For example:

```text
Logical record:
relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A

Specific version:
relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A?version=3
```

The exact version-reference syntax remains open.

### 6.2 Current version

The repository must clearly indicate which version is current.

An application must not treat an older cached version as current without identifying that it may be stale.

---

## 7. Record type and schema

The schema identifier defines the record’s type and structure.

Example:

```text
com.relay.post.v1
```

The schema must define:

- required fields;
- optional fields;
- field types;
- validation constraints;
- meaning of each field;
- supported operations;
- compatibility rules;
- whether the record is singleton or repeatable;
- whether updates or only superseding records are allowed.

### 7.1 Record type is not application ownership

A record using:

```text
com.example.music.track.v1
```

does not belong to Example Music.

The namespace identifies the schema authority.

The record remains controlled by its repository and authorising identity.

### 7.2 Schema-specific behaviour

Schemas may define behaviour such as:

- whether comments may reference the record;
- whether the record supports revisions;
- whether the record can expire;
- whether the record may be public;
- whether a field contains another Record URI;
- whether a blob is required;
- whether multiple instances are allowed.

Protocol-level validation must remain separate from application-specific presentation.

---

## 8. Core record categories

Relay v0.1 should distinguish several broad categories.

### 8.1 Entity records

Describe a persistent entity or object.

Examples:

- profile;
- project;
- publication;
- organisation;
- media item.

### 8.2 Activity records

Describe an action or event.

Examples:

- publish;
- react;
- follow;
- endorse;
- revoke;
- announce.

### 8.3 Relationship records

Describe a directed or mutual relationship between identities or records.

Examples:

- follows;
- collaborates with;
- authored;
- member of;
- replies to.

### 8.4 Authority records

Describe permission or control.

Examples:

- permission grant;
- delegated key;
- recovery authority;
- application authorisation.

### 8.5 Assertion records

Describe a claim.

Examples:

- qualification;
- employment;
- authorship;
- verification;
- moderation label.

### 8.6 Tombstone records

Record the deletion or retirement of another record without retaining its full active content.

These categories may share common fields while using different schemas.

---

## 9. Singleton and repeatable records

A schema may define a collection as either singleton or repeatable.

### Singleton

Only one active logical record of that schema or role exists per repository.

Examples might include:

```text
Primary profile
Current repository preferences
Primary public contact settings
```

### Repeatable

Multiple records may exist.

Examples include:

```text
Posts
Projects
Photographs
Credentials
Relationships
```

A singleton update should normally create a new version of the same logical record rather than a second competing current record.

---

## 10. Authorship, authority and submission

Relay must distinguish between three concepts:

- **subject**;
- **authorising identity**;
- **submitting application or agent**.

These are often the same today, but they do not have to be.

### 10.1 Subject

The identity or object the record concerns.

Example:

```text
This employment credential concerns Alice.
```

### 10.2 Authorising identity

The identity under whose repository authority the record is accepted.

Example:

```text
Alice authorised the record to exist in Alice’s repository.
```

### 10.3 Submitter

The application or agent that transmitted the operation.

Example:

```text
A portfolio application submitted the record.
```

A record should be able to represent all three without conflating them.

Example:

```json
{
  "subject": "rid:relay:alice",
  "authorisedBy": "rid:relay:alice",
  "submittedBy": "rid:app:portfolio-client"
}
```

---

## 11. Issued assertions

Some records are assertions made by another identity.

For example:

- a university issues a qualification;
- an employer confirms employment;
- a professional body issues a licence;
- a community issues a moderation label.

Such a record must distinguish:

- issuer;
- subject;
- holder repository;
- issuance time;
- expiration;
- revocation status;
- issuer signature.

Example:

```json
{
  "schema": "com.relay.credential.education.v1",
  "issuer": "rid:relay:example-university",
  "subject": "rid:relay:alice",
  "issuedAt": "2026-06-01T00:00:00Z",
  "expiresAt": null,
  "credential": {
    "qualification": "Bachelor of Science"
  },
  "issuerSignature": "..."
}
```

The holder may store the credential in their repository, but cannot alter the issuer’s signed claim without invalidating it.

---

## 12. Record provenance

Every record should support structured provenance.

Provenance may identify:

- whether it was created directly;
- whether it was imported;
- the originating service;
- a source record;
- a source file;
- an AI system involved;
- a transformation process;
- a migration event.

Example:

```json
{
  "provenance": {
    "method": "imported",
    "sourceService": "example-social-network",
    "sourceIdentifier": "post_99881",
    "importedAt": "2026-08-24T10:00:00Z",
    "importedBy": "rid:app:relay-importer"
  }
}
```

### 12.1 Provenance must not imply verification

A declared source does not automatically prove that the source is authentic.

Provenance may be:

- self-declared;
- application-attested;
- cryptographically verified;
- externally issued.

The record should indicate which level applies.

---

## 13. Human, assisted and automated creation

Relay records may be created through different forms of authorship.

Possible declarations include:

```text
human-created
human-assisted
AI-assisted
AI-generated
automated
imported
unknown
```

These labels must not be inferred solely from style or content.

They should be declared by:

- the controller;
- the submitting application;
- a trusted creation system;
- or an external verification service.

A Relay record may contain richer information such as:

```json
{
  "creation": {
    "mode": "human-assisted",
    "tools": [
      {
        "name": "Example Writing Assistant",
        "role": "editing"
      }
    ]
  }
}
```

Relay v0.1 should preserve these declarations but must not claim to solve universal proof of human authorship.

---

## 14. Visibility model

Every record must declare or inherit an access classification.

Relay v0.1 should support:

- public;
- unlisted;
- restricted;
- private.

### 14.1 Public

Readable by any observer capable of resolving the repository.

### 14.2 Unlisted

Readable by anyone possessing the stable Record URI, but not intended for public indexing or general discovery.

Applications and indexers should honour the unlisted status.

### 14.3 Restricted

Readable only by identities, applications or groups holding valid access authority.

### 14.4 Private

Readable only by the controller and explicitly authorised private services.

Example:

```json
{
  "visibility": {
    "classification": "restricted",
    "audience": [
      "rid:relay:bob",
      "group:relay:close-collaborators"
    ]
  }
}
```

---

## 15. Audience

A restricted record may identify its intended audience using:

- specific Relay Identities;
- approved applications;
- relationship-based groups;
- named access groups;
- valid permission grants;
- another defined access rule.

Examples:

```text
Only Bob
Only current collaborators
Only Application X
Only identities holding a valid membership credential
```

### 15.1 Dynamic audiences

An audience based on a changing relationship must define whether access is evaluated:

- at publication time;
- at access time;
- or through another rule.

For example:

```text
Visible to current followers
```

could mean that a later follower gains access to earlier records, unless the schema or record states otherwise.

### 15.2 Audience removal

Removing an identity from an audience revokes future authorised access.

It cannot guarantee deletion of copies already received.

---

## 16. Usage rights

Visibility and usage rights are separate.

A public record may be viewable without granting unlimited rights to:

- reproduce it;
- commercially exploit it;
- train models on it;
- modify it;
- syndicate it.

A record may include a structured rights declaration.

Example:

```json
{
  "rights": {
    "view": "public",
    "redistribution": "attribution-required",
    "commercialUse": "prohibited",
    "modelTraining": "prohibited",
    "derivatives": "permission-required"
  }
}
```

The protocol can express these terms.

It cannot guarantee that every external observer will obey them.

Enforcement may depend on:

- contracts;
- application policies;
- technical controls;
- licensing systems;
- applicable law.

---

## 17. Record creation

Creating a record requires:

1. a valid schema;
2. a unique Record Key;
3. content that passes schema validation;
4. a valid visibility classification;
5. valid repository authority;
6. inclusion in an accepted commit.

A record is not canonical merely because an application generated it locally.

It becomes canonical only when accepted by the repository.

---

## 18. Record validation

Validation occurs at several levels.

### 18.1 Envelope validation

Checks protocol-level structure.

Examples:

- valid URI;
- valid identifier;
- required metadata;
- supported encoding;
- valid timestamp.

### 18.2 Schema validation

Checks the content against the declared schema.

Examples:

- required fields;
- value types;
- permitted lengths;
- allowed references.

### 18.3 Authority validation

Checks that the operation was authorised.

Examples:

- valid controller signature;
- valid delegated application grant;
- non-revoked key;
- operation within scope.

### 18.4 Repository-state validation

Checks the operation against current state.

Examples:

- Record Key does not already exist;
- version being updated is current;
- referenced commit is valid;
- singleton constraints are respected.

### 18.5 Semantic validation

An application may perform additional meaning-based checks.

Examples:

- whether a URL is reachable;
- whether a media file is suitable;
- whether text violates community policy.

Semantic validation is generally application-specific and must not be confused with protocol validity.

---

## 19. Record update

An update changes the content or metadata of an existing logical record.

An update must identify:

- the Record URI;
- the version being replaced;
- the new content;
- the authorising authority;
- the commit accepting the update.

### 19.1 Optimistic concurrency

An update should state which current version it expects.

Example:

```json
{
  "record": "relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A",
  "expectedVersion": 3,
  "newContent": {
    "text": "Updated text."
  }
}
```

If the current version is already 4, the repository should reject the update or require explicit conflict resolution.

This prevents silent overwriting.

### 19.2 Metadata-only updates

Changes to:

- visibility;
- audience;
- rights;
- title;
- labels;
- blob references;

may create a new version even where the primary content remains unchanged.

---

## 20. Immutable records

Some schemas may define records as immutable after creation.

Examples may include:

- signed credentials;
- historical attestations;
- issued receipts;
- completed audit events.

An immutable record may be:

- revoked;
- superseded;
- annotated;
- or deleted where legally necessary.

It cannot be silently rewritten as though the original assertion had always been different.

---

## 21. Record deletion

Deleting a record is an authorised repository operation.

The deletion must identify:

- the Record URI;
- the version deleted;
- deletion time;
- authorising authority;
- deletion mode;
- tombstone requirements.

Possible modes include:

### Soft deletion

The active record is hidden, but the provider retains its prior content.

### Content erasure

The prior content is removed, while minimum verification metadata remains.

### Expiring deletion

The record becomes unavailable after a stated date.

### Legal restriction

The content is withheld because of a legal or regulatory requirement.

### Provider removal

The current provider refuses to serve the record, without necessarily changing the canonical repository history.

These states must not be presented as equivalent.

---

## 22. Tombstone

A **Tombstone** is the minimum persistent record indicating that a logical record previously existed but is no longer active or available.

A tombstone may contain:

```json
{
  "uri": "relay://rid:relay:7fs82k9m4v/com.relay.post/post_01JX9A",
  "status": "deleted",
  "deletedAt": "2026-08-25T12:00:00Z",
  "deletedVersion": 4,
  "previousContentHash": "sha256:98c2...",
  "authorisedBy": "rid:relay:7fs82k9m4v"
}
```

A tombstone should not contain more deleted content than is necessary to preserve repository integrity and prevent identifier reuse.

### 22.1 Record key reuse

A deleted Record Key must not be reused for a different logical record.

The tombstone preserves the fact that the identifier has already been used.

---

## 23. Restoration

A deleted record may be restored if:

- the schema permits restoration;
- the deleted content remains available;
- the controller authorises restoration;
- a new commit records the operation.

Restoration creates a new current version.

It does not erase the deletion event from repository history.

---

## 24. Expiration

A schema or record may define an expiration time.

Examples:

- temporary announcement;
- limited-duration access invitation;
- expiring credential;
- short-lived status.

Example:

```json
{
  "expiresAt": "2026-09-01T00:00:00Z"
}
```

Expiration may mean:

- no longer publicly displayed;
- no longer valid as an assertion;
- no longer accessible;
- eligible for deletion.

The schema must specify which interpretation applies.

---

## 25. References between records

A record may refer to another Relay Record using its stable Record URI.

Examples include:

```text
replyTo
quotes
derivedFrom
supersedes
memberOf
attachedTo
endorses
labels
```

A reference should identify its semantic relationship.

Example:

```json
{
  "references": [
    {
      "type": "replyTo",
      "uri": "relay://rid:relay:bob/com.relay.post/post_88A"
    }
  ]
}
```

### 25.1 Version-pinned references

A reference may point to:

- the current logical record;
- or a specific historical version.

A quotation or signed assertion may need to reference the exact version observed at the time.

### 25.2 Broken references

A referenced record may later become:

- deleted;
- restricted;
- unavailable;
- migrated;
- blocked by an application.

The referring record remains valid, but the application must handle the unavailable target accurately.

---

## 26. Embedded content

A record may contain a limited embedded representation of another object.

Examples:

- quoted text;
- thumbnail;
- preview title;
- author handle at time of publication.

Embedded content should include provenance.

Example:

```json
{
  "embed": {
    "source": "relay://rid:relay:bob/com.relay.post/post_88A",
    "observedVersion": 2,
    "observedAt": "2026-08-24T10:00:00Z",
    "preview": {
      "text": "A quoted excerpt."
    }
  }
}
```

An embed is a historical observation, not necessarily the current state of the source record.

---

## 27. Blob references

A record may refer to one or more blobs.

Example:

```json
{
  "media": [
    {
      "blob": "blob:sha256:84b3...",
      "mediaType": "image/jpeg",
      "purpose": "primary-image",
      "altText": "A description of the image."
    }
  ]
}
```

Blob references should include:

- blob identifier;
- media type;
- intended role;
- accessibility metadata where applicable;
- optional dimensions or duration;
- integrity hash.

The record must not treat a temporary storage URL as the blob’s permanent identity.

---

## 28. Lists and ordering

Some records contain ordered items.

Examples:

- portfolio ordering;
- image gallery;
- playlist;
- article sections.

The schema must define whether ordering is:

- part of the record content;
- derived by an application;
- maintained through separate relationship records.

Applications should not assume a repository-wide universal order where the schema does not define one.

---

## 29. Local application state

Not every application preference belongs in the canonical Relay Repository.

Examples that may remain local include:

- window size;
- dismissed tooltip state;
- temporary draft position;
- client-specific cache configuration.

A record belongs in the canonical repository when portability or continuity provides meaningful user value.

The protocol should discourage applications from filling the repository with irrelevant implementation details.

A useful test is:

> Would the person reasonably expect this information or state to survive when changing applications?

If not, it may remain local.

---

## 30. Draft records

Applications may create local drafts before repository acceptance.

A draft is not canonical until committed.

A repository may optionally support private draft records.

A draft should clearly indicate:

- that it is incomplete;
- whether it is synchronised;
- which application created it;
- whether another application may edit it.

Applications must not present unsynchronised local drafts as safely stored canonical records.

---

## 31. Application-specific records

An application may define a custom record type.

Example:

```text
com.example.design.canvas.v1
```

A custom record should remain portable even if only one application currently understands it.

A new application may:

- preserve it without rendering it;
- render limited metadata;
- interpret it after implementing the schema;
- transform it into another schema with permission.

The originating application must not encrypt or obscure the record solely to prevent competing clients from using it, unless the content genuinely requires encryption for user security.

---

## 32. Schema extension

Relay should allow controlled schema extension.

Possible approaches include:

- optional extension fields;
- referenced extension records;
- schema inheritance;
- namespaced metadata.

Extensions must not redefine the meaning of required core fields.

For example, an application may add:

```json
{
  "extensions": {
    "com.example.analytics": {
      "campaignCode": "SPRING26"
    }
  }
}
```

Another application may ignore the extension while preserving it.

---

## 33. Record translation

Applications may translate one record schema into another.

Example:

```text
com.example.blog.article.v2
→ com.relay.article.v1
```

A translated record must preserve provenance, including:

- source Record URI;
- source schema;
- transformation application;
- transformation time;
- whether the translation is reversible;
- any information omitted.

Translation must not silently replace the source record unless the controller explicitly authorises that change.

---

## 34. Canonical records and projections

A **Projection** is an application-specific representation derived from one or more records.

Examples:

- social feed card;
- public profile page;
- search result;
- professional résumé;
- recommendation score.

A projection is not automatically a Relay Record.

It becomes a repository record only if the controller deliberately saves it.

This distinction prevents application-generated views from polluting the person’s canonical history.

---

## 35. Comments and replies

A reply should normally be a record in the replying identity’s repository.

Example:

```text
Alice’s post:
relay://rid:relay:alice/com.relay.post/post_1

Bob’s reply:
relay://rid:relay:bob/com.relay.comment/comment_7
```

Bob’s reply contains:

```json
{
  "replyTo": "relay://rid:relay:alice/com.relay.post/post_1"
}
```

Alice’s provider or application may index and display Bob’s reply, but Bob’s repository remains the canonical source of the reply.

This means:

- Bob can edit or delete the reply through another client;
- Alice does not own Bob’s comment;
- different applications may apply different moderation policies;
- the reply survives the disappearance of the application used to create it.

---

## 36. Reactions

A reaction should normally be represented as a record owned by the reacting identity.

Example:

```json
{
  "schema": "com.relay.reaction.v1",
  "subject": "relay://rid:relay:alice/com.relay.post/post_1",
  "reaction": "like"
}
```

Applications may aggregate reactions into counts.

The count is a derived value.

The individual reaction records are the underlying canonical objects.

---

## 37. Reposts and references

A repost should not require copying the original record into the reposter’s repository as if they authored it.

Instead, the repost record references the source.

Example:

```json
{
  "schema": "com.relay.repost.v1",
  "subject": "relay://rid:relay:alice/com.relay.post/post_1",
  "comment": "Worth reading."
}
```

The repost belongs to the reposter.

The original remains controlled by the original author.

---

## 38. Moderation labels

Moderation decisions should be represented separately from the target record.

Example:

```json
{
  "schema": "com.relay.moderation.label.v1",
  "issuer": "rid:relay:moderation-service",
  "subject": "relay://rid:relay:alice/com.relay.post/post_1",
  "label": "graphic-content",
  "issuedAt": "2026-08-24T10:00:00Z"
}
```

A label does not alter the original record.

Applications may choose which label providers and policies they trust.

Relay v0.1 does not define a universal moderation policy, but the record model must support independently issued labels.

---

## 39. Record conflict

A record conflict occurs when two updates attempt to replace the same current version.

The repository must not silently accept both as a single linear continuation.

Possible outcomes include:

- reject the later submission;
- request user review;
- create a new reconciled version;
- preserve both proposed versions as conflict candidates.

For text and other mergeable formats, an application may offer a merge.

The resulting merged record must still be explicitly authorised.

---

## 40. Batch operations

An application may submit several record changes as one commit.

For example:

```text
Create article
Upload cover image
Update project index
Add publication relationship
```

The commit either succeeds in full or fails in full.

The records remain independently addressable after acceptance.

---

## 41. Record portability

A record is portable when another compliant provider can:

- preserve its Record URI;
- preserve its collection and schema;
- validate its envelope;
- preserve its content;
- preserve blob references;
- preserve its version history;
- preserve unknown extensions;
- continue serving it according to its visibility rules.

A migration that converts every record into flat files without operational meaning does not satisfy Relay portability.

---

## 42. Record interoperability

Relay interoperability does not require every application to support every record type.

A compliant application may state:

```text
Fully supports com.relay.post.v1
Read-only support for com.relay.article.v1
Preserves but does not display com.example.design.canvas.v1
```

The minimum requirement is that unsupported records are not damaged, misrepresented or discarded.

---

## 43. Required v0.1 record operations

A compliant implementation must support:

```text
Create record
Read current record
Read specific record version
List records by collection
Validate record envelope
Validate record schema
Update record
Delete record
Restore record where permitted
Read tombstone
Verify record integrity
Resolve record references
Upload and attach blob
Change visibility
Change audience
Inspect provenance
Preserve unknown record types
Detect update conflict
```

---

## 44. Record invariants

The following rules must always remain true.

### Invariant 1

A Record URI identifies one logical record and must not be reassigned.

### Invariant 2

Editing a record does not change its Record URI.

### Invariant 3

Every current record version belongs to an accepted repository commit.

### Invariant 4

The submitting application is not necessarily the authorising identity.

### Invariant 5

Using a schema does not give the schema publisher ownership of the record.

### Invariant 6

Visibility does not determine legal ownership or usage rights.

### Invariant 7

A record may be deleted without pretending that it never existed in repository history.

### Invariant 8

Unknown but valid fields and extensions must survive migration.

### Invariant 9

An application projection is not canonical unless deliberately accepted into the repository.

### Invariant 10

A cached copy must retain the canonical Record URI and source provenance.

### Invariant 11

A public record may be indexed, but the index does not become its canonical owner.

### Invariant 12

A reply, reaction or repost belongs to the identity that authorised that record, not to the owner of the referenced content.

---

## 45. Compliance scenario

A basic record implementation should pass the following test.

### Initial record

Application A creates a public post:

```text
relay://rid:relay:alice/com.relay.post/post_123
```

The repository accepts it as version 1.

### Update through another application

Application B reads the record and updates the text.

The repository accepts version 2.

The Record URI remains unchanged.

### Concurrent update

Application A attempts to update version 1 after version 2 already exists.

The repository rejects the stale update or marks it as a conflict.

It does not silently overwrite version 2.

### Reply from another identity

Bob creates a reply in Bob’s repository referencing Alice’s post.

Alice’s application displays the reply.

Bob remains the controller of the reply record.

### Visibility change

Alice changes the post from public to restricted.

A new version records the change.

Future unauthorised access is refused.

### Deletion

Alice deletes the post.

Its active content is removed according to policy.

A tombstone prevents reuse of the Record URI and preserves minimum verification history.

### Migration

Alice moves her repository to another provider.

The post’s versions, tombstone and Record URI remain intact.

If these operations occur without confusing application ownership, record identity, historical versions or visibility state, the implementation satisfies the basic Relay Record objective.

---

## 46. Open design questions

### 46.1 Envelope structure

Which fields belong directly inside every record, and which should be inherited from the containing commit or collection?

### 46.2 Individual signatures

Should records be individually signed in addition to being covered by a signed commit?

### 46.3 Visibility enforcement

Should restricted records use repository access controls only, or require content-level encryption?

### 46.4 Usage rights vocabulary

Should Relay define a basic rights vocabulary, rely on existing licensing standards, or allow external vocabularies?

### 46.5 AI provenance

What minimum structured information should be required when a participating application declares AI involvement?

### 46.6 History retention

Which historical versions must remain retrievable, and which may be reduced to hashes or tombstones?

### 46.7 Schema governance

Who may publish schemas under the Relay core namespace?

### 46.8 Dynamic audiences

How should relationship-based audiences be evaluated and cached?

### 46.9 Cross-repository transactions

Can one operation safely require changes to records in two independent repositories?

### 46.10 Record transfer

Can a logical record ever move from one Relay Identity’s repository to another while preserving its identity, or should transfer always create a new record with provenance?

---

## 47. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- JSON-compatible structured records;
- stable Record URIs;
- versioned schemas;
- one current version per logical record;
- optimistic concurrency checks;
- signed repository commits as the minimum authority proof;
- optional individual record signatures for externally issued assertions;
- public, unlisted, restricted and private visibility classifications;
- logical deletion with tombstones;
- no reuse of deleted Record Keys;
- content-addressed blob references;
- structured provenance;
- preservation of unknown fields and schemas;
- replies, reactions and reposts stored in the acting identity’s repository;
- application projections remaining non-canonical unless explicitly saved;
- moderation labels represented as separate records;
- schema-specific rules layered on top of a common protocol envelope.

---

## 48. Core record principle

The Record Model can be reduced to one rule:

> A Relay Record is a stable, portable object under repository authority, not a disposable row inside the application that happened to create it.

The next core object is the **Relay Application and Permission Model**: how applications identify themselves, request narrowly defined authority, act on behalf of a person and lose access cleanly when permission is revoked.