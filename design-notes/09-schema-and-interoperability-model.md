# Relay Protocol v0.1  
## Core Object 9: Schema and Interoperability Model

### 1. Definition

A **Relay Schema** is a versioned, machine-readable definition describing the structure, meaning and validation rules of a Relay Record.

The Schema and Interoperability Model determines how applications:

- understand shared record types;
- create compatible records;
- preserve records they do not understand;
- extend existing records safely;
- translate between formats;
- evolve record structures over time;
- avoid making one application the permanent owner of a data format.

A schema defines how information is represented.

It does not own the records created using that representation.

---

## 2. Purpose

The Schema and Interoperability Model exists to balance two competing requirements:

### Shared understanding

Applications need predictable structures for common concepts such as:

- profiles;
- posts;
- articles;
- projects;
- relationships;
- credentials;
- permissions;
- media;
- moderation labels.

### Open-ended expression

Relay must not require every future record type to be approved by one company or standards body.

Developers must be able to introduce new record types without breaking portability or forcing every provider to understand them immediately.

The core objective is:

> Applications should be able to understand what they support, preserve what they do not understand and extend the ecosystem without taking ownership of the user’s records.

---

## 3. Core components

The Schema and Interoperability Model contains:

1. **Schema Identifier**
2. **Schema Namespace**
3. **Schema Version**
4. **Schema Definition**
5. **Validation Rules**
6. **Semantic Definition**
7. **Compatibility Declaration**
8. **Extension Mechanism**
9. **Schema Registry**
10. **Schema Publisher**
11. **Translation Profile**
12. **Preservation Rules**
13. **Core Relay Schemas**
14. **Application Schemas**

---

## 4. Schema Identifier

Every Relay Schema must have a stable, globally unique identifier.

Example:

```text
com.relay.post.v1
```

A Schema Identifier should identify:

- the namespace;
- the record concept;
- the major schema version.

Possible structure:

```text
<namespace>.<record-type>.v<major-version>
```

Examples:

```text
com.relay.profile.v1
com.relay.post.v1
com.relay.relationship.follow.v1
com.example.music.track.v1
org.example.research.observation.v2
```

The exact syntax remains provisional.

---

## 5. Schema namespace

The **Schema Namespace** identifies the authority responsible for defining the schema.

Examples:

```text
com.relay
com.example
org.university
za.co.example
```

A namespace should be uniquely associated with a publisher.

Possible namespace control methods include:

- verified domain ownership;
- signed namespace registration;
- Relay Identity ownership;
- registry-issued allocation.

The namespace defines authorship of the schema definition.

It does not define ownership of records created using that schema.

---

## 6. Namespace ownership

A Schema Publisher should be able to prove authority over its namespace.

For example:

```text
com.example
```

may be linked to:

```text
example.com
```

through:

- DNS;
- a well-known file;
- signed namespace declaration;
- Relay Identity verification.

A provider must not allow one publisher to silently define or replace schemas under another publisher’s namespace.

---

## 7. Relay core namespace

The namespace:

```text
com.relay
```

is reserved for core protocol schemas.

Core schemas should be limited to concepts necessary for interoperability.

Possible core schemas include:

```text
com.relay.profile.v1
com.relay.post.v1
com.relay.article.v1
com.relay.relationship.follow.v1
com.relay.relationship.subscribe.v1
com.relay.permission.grant.v1
com.relay.moderation.label.v1
com.relay.credential.reference.v1
```

The Relay core namespace should not attempt to standardise every possible application feature.

Over-expansion would turn the protocol into a central product-design authority.

---

## 8. Application namespace

Applications may define their own schemas.

Example:

```text
com.example.design.canvas.v1
```

Such a schema may represent:

- design documents;
- game saves;
- musical projects;
- application preferences;
- specialised workflows;
- industry records.

A Relay Provider must be able to preserve these records even when it cannot interpret them fully.

---

## 9. Schema version

A schema must declare an explicit version.

Relay should distinguish between:

- major version;
- minor revision;
- editorial revision.

A major version changes the schema identifier.

Example:

```text
com.relay.post.v1
com.relay.post.v2
```

Minor or editorial updates may retain the same major identifier where they do not break compatibility.

---

## 10. Major version

A new major version is required when a schema change may cause an existing compliant application to misinterpret a record.

Examples include:

- removing a required field;
- changing the meaning of a field;
- changing a field’s type;
- changing visibility semantics;
- changing authorship semantics;
- changing uniqueness rules;
- changing whether records are mutable;
- changing security-sensitive behaviour.

Major versions must coexist.

Publishing v2 must not make valid v1 records invalid.

---

## 11. Minor revision

A minor revision may include:

- adding optional fields;
- clarifying constraints;
- adding non-breaking enumerated values;
- improving documentation;
- adding optional extension points.

Applications supporting the schema should ignore unknown optional fields unless the schema marks them as security-critical.

---

## 12. Schema immutability

A published schema version must not be silently rewritten.

If the meaning or validation rules change materially, the publisher must issue:

- a new revision;
- or a new major version.

Historical records must remain verifiable against the schema definition that applied when they were accepted.

A publisher must not be able to invalidate historical records by replacing the online definition with different rules.

---

## 13. Schema integrity

Every schema definition should have a cryptographic integrity hash.

Example:

```text
sha256:94fa...
```

A record or commit may reference:

- Schema Identifier;
- schema revision;
- schema hash.

Example:

```json
{
  "schema": "com.relay.post.v1",
  "schemaRevision": "1.2",
  "schemaHash": "sha256:94fa..."
}
```

This enables historical validation even if a registry or publisher later changes infrastructure.

---

## 14. Schema definition

A schema definition should contain:

- Schema Identifier;
- title;
- description;
- publisher;
- version;
- publication date;
- field definitions;
- required fields;
- allowed data types;
- validation constraints;
- default visibility rules;
- mutability rules;
- uniqueness rules;
- reference rules;
- blob rules;
- compatibility declaration;
- extension points;
- security considerations;
- human-readable documentation;
- integrity hash;
- publisher signature.

---

## 15. Machine-readable structure

Relay v0.1 should use a machine-readable schema language.

The schema language must support:

- objects;
- arrays;
- strings;
- numbers;
- booleans;
- nullability;
- enumerated values;
- pattern constraints;
- length constraints;
- date and time types;
- Relay Identifiers;
- Record URIs;
- Blob Identifiers;
- references;
- extensions.

The final schema language remains open.

A JSON-compatible schema system is the likely starting point.

---

## 16. Semantic definition

Structural validation alone is insufficient.

For example:

```json
{
  "relationship": "friend"
}
```

may be structurally valid, but applications still need to know whether:

- friendship requires mutual acceptance;
- it is public by default;
- it grants access;
- it expires;
- it can be self-declared.

Each schema should therefore contain a semantic definition explaining the meaning of the record and its fields.

---

## 17. Protocol semantics versus presentation

A schema may define what a field means.

It should not prescribe a single interface.

For example, a post schema may define:

```text
text
createdAt
replyTo
media
```

Different applications may render that record as:

- a social feed card;
- a blog entry;
- a timeline item;
- a compact notification;
- an audio reading.

Interoperability requires shared meaning, not identical presentation.

---

## 18. Required fields

A schema must identify fields required for a valid record.

Example:

```json
{
  "required": [
    "text",
    "createdAt"
  ]
}
```

Required fields should be limited to information genuinely necessary for shared understanding.

Excessive required fields make schemas difficult to adopt and extend.

---

## 19. Optional fields

Optional fields allow richer application behaviour without breaking basic interoperability.

Example:

```text
language
contentWarning
location
attachments
estimatedReadingTime
```

Applications that do not understand an optional field must:

- preserve it;
- avoid modifying it accidentally;
- avoid misrepresenting its meaning.

---

## 20. Unknown fields

Relay should define whether unknown fields are:

- permitted;
- prohibited;
- or permitted only inside extension containers.

For portability, the preferred model is:

- strict validation for core fields;
- namespaced extensions for unknown application-specific data.

This reduces collisions and prevents two applications from giving the same field name different meanings.

---

## 21. Extension container

A record may include an extension container such as:

```json
{
  "extensions": {
    "com.example.analytics": {
      "campaignCode": "SPRING26"
    },
    "org.example.accessibility": {
      "readingLevel": "plain-language"
    }
  }
}
```

Each extension must use a controlled namespace.

Applications may ignore unknown extensions while preserving them.

---

## 22. Core-field protection

Extensions must not redefine or override core fields.

For example, an extension may not redefine:

```text
authorisedBy
visibility
Record URI
schema
createdAt
```

Security-sensitive protocol fields remain governed by the Relay Record Model.

---

## 23. Field ownership

The fact that an application introduced a field does not mean it owns the value stored in that field.

If the user later edits the record through another compatible application, the second application may update supported fields where authorised.

Unsupported extension fields should normally be preserved unchanged.

---

## 24. Validation levels

Schema validation may occur at several levels.

### 24.1 Structural validation

Checks field presence and types.

### 24.2 Constraint validation

Checks:

- lengths;
- ranges;
- patterns;
- enumerated values;
- uniqueness.

### 24.3 Reference validation

Checks whether referenced identifiers and record forms are syntactically valid.

### 24.4 Semantic validation

Checks schema-defined state rules.

Examples:

- a reply must include a target;
- a singleton profile may not be duplicated;
- an immutable credential may not be updated.

### 24.5 External validation

Checks information outside the record.

Examples:

- whether a domain resolves;
- whether a credential issuer is active;
- whether a blob is safe.

External validation must not be confused with core schema validity.

---

## 25. Validation determinism

Protocol-level validation should be deterministic.

Given the same:

- record;
- schema;
- repository state;
- protocol version;

two compliant implementations should reach the same validity result.

Application-specific moderation or business rules should not alter core protocol validity.

---

## 26. Security-sensitive fields

Schemas should identify security-sensitive fields.

Examples include:

- visibility;
- audience;
- authority;
- executable content;
- external links;
- encryption metadata;
- embedded HTML;
- script references;
- automatic actions.

Applications must not ignore an unknown security-sensitive field while presenting the record as fully supported.

They may instead:

- reject creation;
- preserve but not render;
- display in a safe reduced mode;
- require a newer implementation.

---

## 27. Safe rendering

A structurally valid record may contain unsafe content.

Applications must safely handle:

- HTML;
- scripts;
- embedded resources;
- file attachments;
- links;
- rich text;
- executable document formats.

The schema may describe content.

It does not eliminate the need for secure rendering and content sanitisation.

---

## 28. Schema compatibility

A schema should declare compatibility information.

Possible relationships include:

```text
backward-compatible
forward-preservable
read-compatible
write-compatible
convertible
incompatible
```

An application may support a schema at one of several levels.

---

## 29. Application support levels

A Relay Application should be able to declare:

### Full support

The application can:

- read;
- create;
- update;
- preserve;
- validate;
- render the schema correctly.

### Read-only support

The application can interpret and display records but does not safely edit them.

### Preserve-only support

The application does not understand the schema but can store and migrate it without alteration.

### Converted support

The application can transform the schema into another supported representation.

### Unsupported

The application cannot safely process the record.

Unsupported records must not be discarded from the repository.

---

## 30. Provider support levels

A Relay Provider may similarly declare:

```text
validate-and-serve
serve-only
preserve-only
unsupported-security-model
```

A provider may preserve records without presenting a user interface for them.

A provider that cannot preserve unknown schemas does not satisfy Relay portability requirements.

---

## 31. Preservation rule

A compliant repository must preserve unknown but structurally valid records during:

- ordinary storage;
- export;
- migration;
- backup;
- restoration.

Preservation includes:

- Record URI;
- collection;
- schema identifier;
- schema reference;
- content;
- extensions;
- blob references;
- visibility;
- provenance;
- version history.

---

## 32. Opaque preservation

A provider may preserve an unknown record as an opaque object.

It must still retain enough protocol metadata to:

- verify the record;
- maintain its identifier;
- enforce basic access controls;
- migrate it;
- restore it.

Opaque preservation does not require semantic understanding.

---

## 33. Editing unknown records

An application must not rewrite a record it does not understand.

It may safely update protocol-level metadata only where the operation does not risk invalidating unknown semantics.

For example, changing visibility may be allowed if:

- the user authorises it;
- the schema permits visibility changes;
- the application understands the security implications.

Otherwise, the record should remain unchanged.

---

## 34. Schema publication

A Schema Publisher should publish:

- machine-readable definition;
- human-readable documentation;
- namespace proof;
- version history;
- integrity hash;
- compatibility information;
- migration guidance;
- security considerations;
- deprecation status;
- contact details.

The schema should remain retrievable independently of the publisher’s application interface.

---

## 35. Schema registry

A **Schema Registry** is a searchable directory of schema definitions and metadata.

A registry may provide:

- schema lookup;
- namespace verification;
- version history;
- integrity hashes;
- compatibility declarations;
- publisher information;
- deprecation status;
- security advisories.

The registry does not own user records.

---

## 36. Registry decentralisation

Relay should not require one permanent global schema registry.

Possible models include:

- one reference registry;
- multiple mirrored registries;
- publisher-hosted schemas;
- content-addressed schema retrieval;
- signed registry indexes;
- application-bundled schema copies.

Applications should be able to verify schemas independently of the registry that delivered them.

---

## 37. Registry disagreement

Two registries may return different definitions for the same schema identifier.

The application should compare:

- schema hash;
- publisher signature;
- revision;
- namespace authority;
- publication history.

A conflicting schema definition must not be silently accepted.

---

## 38. Schema publisher identity

A Schema Publisher should have a stable identity.

This may be:

- a Relay Identity;
- a verified domain authority;
- an organisation identity;
- a standards body.

The publisher identity should sign schema releases.

Changing infrastructure should not change the publisher identity.

---

## 39. Publisher disappearance

If the publisher disappears:

- existing schemas remain valid;
- historical schema copies remain usable;
- records continue to be preserved;
- another party may fork or adopt the schema under a new namespace;
- the original namespace must not be silently reassigned.

A vanished application must not make user data unreadable by design.

---

## 40. Schema deprecation

A publisher may mark a schema as deprecated.

Deprecation means:

- new records should preferably use a replacement;
- existing records remain valid;
- providers continue preserving the schema;
- applications may warn users;
- migration guidance should be provided.

Deprecation must not automatically delete or rewrite records.

---

## 41. Schema withdrawal

A schema may need to be withdrawn for severe reasons such as:

- security flaw;
- dangerous executable behaviour;
- legal prohibition;
- namespace compromise.

Withdrawal should still preserve historical integrity.

Applications may refuse to render or create affected records while retaining them for export or forensic review where lawful.

---

## 42. Schema security advisory

A registry or publisher may issue an advisory containing:

- affected schema;
- affected versions;
- risk description;
- recommended handling;
- replacement schema;
- mitigation;
- publication time;
- signature.

Providers and applications may use advisories to restrict unsafe behaviour.

---

## 43. Schema governance

Core Relay schemas require a governance process.

That process should define:

- who may propose changes;
- review period;
- compatibility requirements;
- security review;
- public discussion;
- approval threshold;
- release procedure;
- deprecation process.

Core schema governance should be transparent and separate from any one commercial client.

---

## 44. Minimal core

Relay should keep the core schema set deliberately small.

A schema belongs in the core only where:

- several unrelated applications need shared meaning;
- portability materially depends on standardisation;
- the concept is stable enough to define;
- failure to standardise would create ecosystem fragmentation.

Specialised records should remain in external namespaces.

---

## 45. Profile schema

A core profile schema may define fields such as:

```text
displayName
description
avatar
preferredHandle
links
languages
```

It should avoid requiring:

- legal name;
- date of birth;
- gender;
- address;
- employer;
- government identifier.

Applications may request or define additional profile records where necessary.

---

## 46. Post schema

A core post schema may define:

```text
text
createdAt
language
media
replyTo
contentWarning
```

It should not assume:

- one maximum character length;
- one feed algorithm;
- one visual layout;
- one business model.

Application-specific post features may use extensions or specialised schemas.

---

## 47. Article schema

A core article schema may support:

```text
title
summary
body
authors
publishedAt
media
references
```

The body may use a defined portable rich-text format rather than proprietary editor state.

Application-specific editing history may be stored separately.

---

## 48. Portable rich text

Relay should avoid making raw application-specific HTML the only portable rich-text representation.

A portable rich-text model should support:

- paragraphs;
- headings;
- emphasis;
- links;
- lists;
- quotations;
- code;
- media references;
- semantic annotations.

It should exclude unsafe executable content.

The exact representation remains an open design question.

---

## 49. Relationship schemas

Relationship schemas should define:

- direction;
- reciprocity;
- consent;
- visibility;
- context;
- expiration;
- authority;
- uniqueness.

Applications must not infer these rules merely from a relationship label.

---

## 50. Authority schemas

Schemas involving authority require stronger review.

Examples include:

- permission grants;
- administrator relationships;
- guardian authority;
- migration approvals;
- recovery authority.

Such schemas must define:

- precise capabilities;
- scope;
- revocation;
- expiration;
- signing requirements;
- security consequences.

---

## 51. Credential schemas

Relay may reference externally issued credentials.

The schema should distinguish between:

- credential content;
- issuer;
- subject;
- holder;
- issuance;
- expiration;
- revocation;
- verification method.

Relay should avoid inventing a separate incompatible credential system where an established credential format can be referenced safely.

---

## 52. Moderation schemas

Moderation labels should remain separate records.

A moderation schema may define:

```text
issuer
subject
label
severity
reasonCode
issuedAt
expiresAt
appealReference
```

It must not modify the target record.

Applications remain free to choose which moderation schemas and issuers they trust.

---

## 53. Schema inheritance

Relay may support limited schema inheritance.

Example:

```text
com.example.photo-post.v1
extends
com.relay.post.v1
```

Inheritance may allow an application to add fields while retaining compatibility with the base type.

However, inheritance can become complex and ambiguous.

Relay v0.1 may prefer composition and extensions over unrestricted inheritance.

---

## 54. Schema composition

A record may reference reusable schema components.

Examples:

- media object;
- postal address;
- language tag;
- person reference;
- rights declaration;
- date range.

Reusable components reduce duplication and inconsistent definitions.

Components must also be versioned and integrity-addressed.

---

## 55. Embedded versus referenced objects

A schema should define whether related information is:

- embedded inside the record;
- referenced as another record;
- represented as a blob;
- represented as a relationship.

Example:

A project may embed:

```text
title
summary
```

but reference:

```text
contributors
media
related articles
```

Shared objects should not be duplicated unnecessarily.

---

## 56. Record granularity

Schemas should avoid both extremes:

### One enormous record

A single record containing the person’s entire digital life becomes difficult to update, permission and verify.

### Excessive fragmentation

Thousands of tiny records may create unnecessary complexity and transaction overhead.

A schema should define a meaningful independently addressable object.

---

## 57. Schema uniqueness rules

A schema may define uniqueness constraints.

Examples:

```text
One primary profile per repository
One active follow per source-target pair
One current permission grant per grant identifier
```

Uniqueness rules must be deterministic and enforceable by the repository.

---

## 58. Schema mutability rules

A schema should declare whether records are:

```text
mutable
immutable
append-only
superseding
state-machine-controlled
```

Examples:

- a normal post may be mutable;
- an issued credential may be immutable but revocable;
- an audit event may be append-only;
- a policy may be superseded by a new record.

Applications must follow the schema’s lifecycle.

---

## 59. Schema state machine

Some schemas may define allowed transitions.

Example:

```text
draft → published → archived
```

or:

```text
pending → accepted → revoked
```

Invalid transitions must be rejected at the repository-validation level where they affect shared semantics.

---

## 60. Default values

Schemas may define default values.

Defaults must be deterministic.

Security-sensitive defaults should be conservative.

For example, a missing visibility field should not silently make a record public.

Relay may require explicit visibility for schemas capable of containing private information.

---

## 61. Enumerated values

Schemas may define controlled values.

Example:

```text
public
unlisted
restricted
private
```

Publishers should avoid changing the meaning of existing values.

New values may require:

- optional handling;
- application fallback behaviour;
- compatibility declaration.

---

## 62. Unknown enumeration values

Applications may encounter an unfamiliar value.

They should follow schema-defined fallback rules.

For security-sensitive values, the safe behaviour may be:

- preserve;
- do not render;
- deny access;
- request upgrade.

It should not automatically map an unknown value to the least restrictive known value.

---

## 63. Schema migration

A **Schema Migration** converts a record from one schema version to another.

Example:

```text
com.example.project.v1
→ com.example.project.v2
```

A migration may be:

- lossless;
- lossy;
- reversible;
- irreversible;
- automatic;
- user-approved.

The migration definition should declare which applies.

---

## 64. Record conversion

A conversion operation should preserve:

- source Record URI;
- source schema;
- source version;
- conversion tool;
- conversion time;
- resulting record;
- omitted fields;
- warnings;
- provenance.

The original record should remain available unless deletion or replacement is explicitly authorised.

---

## 65. In-place upgrade versus new record

A schema migration may:

### Update the existing logical record

The Record URI remains unchanged.

Suitable where the new schema represents the same logical object and conversion is safe.

### Create a new record

The new record references the old record as its source.

Suitable where meaning changes materially or conversion is lossy.

The schema migration profile should specify the preferred behaviour.

---

## 66. Automatic migration

Automatic migration should be allowed only when:

- compatibility is well defined;
- conversion is deterministic;
- no information is lost;
- no user-visible meaning changes;
- no permissions are broadened;
- no security classification is weakened.

Otherwise, user approval is required.

---

## 67. Lossy migration

A lossy migration must disclose:

- which fields are omitted;
- which meanings cannot be preserved;
- whether original records remain available;
- whether reversal is possible.

A destination provider must not perform lossy conversion merely to make migration easier without explicit approval.

---

## 68. Cross-schema translation

Different schemas may represent similar concepts.

Example:

```text
com.example.blog.entry.v1
com.relay.article.v1
```

A **Translation Profile** may define how to convert between them.

Translation may support interoperability without requiring one universal schema.

---

## 69. Translation profile

A Translation Profile should contain:

- source schema;
- target schema;
- field mappings;
- semantic differences;
- default handling;
- omitted information;
- reversibility;
- transformation publisher;
- version;
- integrity hash;
- signature.

---

## 70. Translation trust

A translation is an interpretation.

Different translators may produce different results.

Applications should record:

- which translator was used;
- whether the source remains available;
- whether the output is canonical;
- whether information was lost.

A translation service must not present its output as the original record.

---

## 71. Canonical versus derived translation

A translated representation may be:

### Temporary projection

Used only for display.

It does not enter the repository.

### Cached derived record

Stored for performance with provenance.

### Canonical converted record

Explicitly accepted into the repository by the controller.

Only the third becomes part of canonical repository history.

---

## 72. Interoperability profiles

A group of schemas may form an **Interoperability Profile**.

Example:

```text
Relay Social Profile v0.1
```

It may require support for:

- profile;
- post;
- follow;
- reply;
- reaction;
- media.

Another profile may define:

```text
Relay Professional Profile v0.1
```

with:

- profile;
- project;
- credential reference;
- organisation membership;
- article.

Profiles help applications declare meaningful compatibility without supporting every Relay schema.

---

## 73. Profile compliance

An application claiming compliance with an interoperability profile must identify:

- supported schemas;
- support level;
- protocol version;
- known limitations;
- unsupported optional features.

A provider or application must not claim full compatibility merely because it can import plain text.

---

## 74. Schema negotiation

When two applications interact, they may negotiate shared formats.

For example:

1. Application A supports post v1 and v2.
2. Application B supports post v1.
3. The shared format is post v1.

The negotiation must not downgrade a record in a way that loses information without approval.

---

## 75. Write-format selection

An application creating a new record should choose a schema supported by:

- the repository;
- the application;
- expected interoperating clients;
- the user’s selected compatibility preference.

The latest schema is not always the best choice if ecosystem support is limited.

---

## 76. Read fallback

If an application cannot understand a record fully, it may provide a safe fallback such as:

```text
This record uses a format this application cannot display.
```

It may still show:

- schema name;
- publisher;
- creation time;
- safe metadata;
- an option to open a supporting application.

It must not display corrupted or misleading content.

---

## 77. Open-with discovery

A provider may help the user discover applications supporting a schema.

Example:

```text
Open com.example.design.canvas.v1 with:
- Application A
- Application B
```

This application directory is optional.

The schema publisher must not have exclusive control over which applications may support the format.

---

## 78. Proprietary encryption

An application must not deliberately encrypt ordinary user records solely to prevent other compatible clients from reading them.

Encryption is appropriate where required for:

- privacy;
- user security;
- protected intellectual property;
- legal restrictions.

Where application-specific encryption is used, the user must retain a portable way to decrypt or transfer the record.

---

## 79. Proprietary blobs

A schema may reference specialised binary formats.

The schema documentation should disclose:

- file format;
- version;
- media type;
- whether the format is documented;
- required software;
- conversion options;
- licensing restrictions.

Providers must preserve the blob even if they cannot open it.

---

## 80. Executable records

Schemas containing executable code or automation require heightened safeguards.

They should declare:

- execution environment;
- permissions;
- network access;
- filesystem access;
- side effects;
- signature requirements;
- sandbox expectations.

A provider must not execute unknown records merely because they are schema-valid.

---

## 81. Schema and permissions

Permission Grants should reference schemas or collections.

Example:

```text
Read com.relay.profile.v1
Create com.relay.post.v1
Preserve com.example.design.canvas.v1
```

Permission to access one schema must not automatically grant access to unrelated schemas in the same repository.

---

## 82. Schema and visibility

Schemas may define allowed visibility classifications.

For example:

- a public profile may support public or restricted;
- a private recovery record may never be public;
- a moderation label may default to public but permit restricted evidence.

The repository must reject visibility states forbidden by the schema.

---

## 83. Schema and rights

A schema may support structured usage-rights fields.

It should define:

- allowed rights vocabulary;
- inheritance rules;
- whether rights apply to blobs;
- whether rights may be changed;
- how external licences are referenced.

Visibility and rights remain separate.

---

## 84. Schema and provenance

Schemas should indicate whether provenance is:

- optional;
- required;
- issuer-signed;
- application-attested;
- user-declared.

High-trust assertions may require stronger provenance than ordinary posts.

---

## 85. Schema and AI declarations

Schemas may support creation-method declarations such as:

```text
human-created
human-assisted
AI-assisted
AI-generated
automated
unknown
```

The schema should identify:

- who made the declaration;
- whether evidence is included;
- whether the field is self-declared;
- whether tools are listed.

Relay should not infer authorship mode solely from content analysis.

---

## 86. Schema and localisation

Schemas should support localisation through:

- language tags;
- translated fields;
- directionality;
- locale-sensitive formatting;
- alternative text.

Applications must not assume all content is English or left-to-right.

---

## 87. Schema and accessibility

Schemas involving visual or audio media should support accessibility metadata where appropriate.

Examples:

- alternative text;
- captions;
- transcripts;
- content warnings;
- language;
- reading order.

Accessibility fields should remain portable rather than trapped inside one application.

---

## 88. Schema and deletion

Schemas should define:

- whether deletion is allowed;
- whether tombstones are required;
- whether restoration is allowed;
- whether records must instead be revoked;
- minimum retained metadata.

An immutable credential may use revocation rather than deletion.

A normal post may support deletion and restoration.

---

## 89. Schema and historical versions

Schemas should define whether prior versions are:

- fully retained;
- hash-retained;
- non-retrievable;
- privacy-sensitive;
- externally archived.

The repository’s broader retention policy still applies.

---

## 90. Schema and record transfer

A schema should declare whether a record may change controlling repository.

Possible cases include:

- transferable asset;
- assigned project;
- organisational record;
- non-transferable personal post.

Where transfer is permitted, the protocol must preserve provenance and authority history.

Relay v0.1 may defer general record transfer.

---

## 91. Schema test suite

A schema publisher should provide test cases including:

- valid examples;
- invalid examples;
- boundary cases;
- upgrade cases;
- unknown-field cases;
- security-sensitive cases;
- reference cases.

Test suites improve consistency across implementations.

---

## 92. Conformance fixtures

Relay may publish standard fixtures for core schemas.

A compliant implementation should be able to:

- validate valid fixtures;
- reject invalid fixtures;
- preserve unknown extensions;
- round-trip records without changing meaning;
- migrate supported schema versions correctly.

---

## 93. Round-trip preservation

A record should survive the following process without loss:

1. exported from Provider A;
2. imported by Provider B;
3. read and preserved by Application X;
4. exported again;
5. compared with the original logical record.

Normal serialisation differences may occur.

The meaning, identifiers, content and unknown extensions must remain intact.

---

## 94. Round-trip test

A preservation test should verify:

- same Record URI;
- same schema identifier;
- same supported field values;
- same unknown extensions;
- same blob references;
- same visibility;
- same provenance;
- same content hash where canonical encoding is unchanged.

---

## 95. Interoperability failure

An interoperability failure occurs when a system:

- discards unknown fields;
- converts records without disclosure;
- changes meaning;
- strips provenance;
- changes Record URIs;
- exposes private fields;
- rewrites unsupported records;
- treats an application-specific format as provider-owned.

Such failures should be detectable through export comparison and verification.

---

## 96. Schema conflict

Two schemas may use similar names but different meanings.

Example:

```text
com.example.friend.v1
org.other.friend.v1
```

Applications must not assume semantic equivalence from the final word alone.

Full Schema Identifiers and semantic definitions must be used.

---

## 97. Schema alias

A registry may declare that two schema identifiers are related.

Possible relationships include:

```text
equivalent-to
supersedes
derived-from
partially-compatible-with
translatable-to
```

An alias does not automatically guarantee lossless conversion.

---

## 98. Schema fork

A schema may be forked when:

- the original publisher disappears;
- governance disagrees;
- a community needs different behaviour;
- licensing prevents continued development.

The fork must use a new namespace or identifier.

It may declare derivation from the original.

Existing records remain under the original schema identifier.

---

## 99. Core schema amendment

A core Relay schema should not be amended casually.

A change proposal should consider:

- interoperability impact;
- security;
- privacy;
- migration;
- existing implementations;
- backward compatibility;
- governance legitimacy.

Core schema stability is more important than rapid feature expansion.

---

## 100. Required v0.1 schema operations

A compliant implementation must support:

```text
Resolve Schema Identifier
Retrieve schema definition
Verify schema integrity
Verify schema publisher
Validate record structure
Validate schema constraints
Preserve unknown schema
Preserve unknown extensions
List supported schemas
Declare support level
Publish application schema
Publish schema revision
Publish major schema version
Mark schema deprecated
Read compatibility declaration
Translate record through explicit profile
Record translation provenance
Export schema references
Import schema references
Detect conflicting schema definitions
Run schema conformance fixtures
```

A shared automated schema registry may be limited in the first reference implementation.

---

## 101. Schema invariants

The following rules must always remain true.

### Invariant 1

A schema defines structure and meaning; it does not own records created using it.

### Invariant 2

A published schema version must not be silently rewritten.

### Invariant 3

Historical records remain valid against the schema definition active when they were accepted.

### Invariant 4

A provider must preserve unknown but structurally valid schemas.

### Invariant 5

An application must not rewrite records it does not understand.

### Invariant 6

Extensions must not redefine protocol-level core fields.

### Invariant 7

A major semantic change requires a new major schema version.

### Invariant 8

Deprecation does not invalidate or delete existing records.

### Invariant 9

Schema publishers may disappear without making records non-portable.

### Invariant 10

Translation must preserve provenance and disclose information loss.

### Invariant 11

Search rank or registry preference does not determine schema authority.

### Invariant 12

Unsupported records must not be converted silently.

### Invariant 13

Schema validity does not guarantee content safety or factual truth.

### Invariant 14

Core Relay schemas must remain limited to concepts necessary for broad interoperability.

### Invariant 15

A schema namespace must not be reassigned silently to another publisher.

---

## 102. Compliance scenario

A basic Schema and Interoperability implementation should pass the following test.

### Core record creation

Application A creates a record using:

```text
com.relay.post.v1
```

Provider A validates it against the verified schema definition.

### External schema creation

Application B creates:

```text
com.example.design.canvas.v1
```

Provider A does not understand the design format fully, but preserves the record, its extensions and blobs.

### Application replacement

Application C reads the repository.

It supports:

```text
com.relay.post.v1
```

but not:

```text
com.example.design.canvas.v1
```

Application C displays the post and safely identifies the design record as unsupported.

It does not delete or rewrite the design record.

### Provider migration

The repository moves to Provider B.

Provider B preserves both schemas and all associated records.

The design record remains available to a compatible design application.

### Schema update

The publisher releases:

```text
com.example.design.canvas.v2
```

The v1 record remains valid.

The publisher provides an optional migration profile.

### Lossless migration

The user approves a deterministic conversion from v1 to v2.

The conversion records:

- source schema;
- source Record URI;
- translator;
- migration time;
- resulting schema;
- provenance.

### Publisher disappearance

The original schema publisher later closes.

The schema definition remains available through:

- export;
- registry mirrors;
- content-addressed copies.

The user’s design record remains preservable and verifiable.

If these events occur without data loss, silent reinterpretation or application ownership of the format, the implementation satisfies the basic Relay Schema and Interoperability objective.

---

## 103. Open design questions

### 103.1 Schema language

Should Relay use:

- JSON Schema;
- a restricted JSON Schema profile;
- CDDL;
- a custom schema language;
- another format?

### 103.2 Canonical schema storage

Should schema definitions be:

- registry-hosted;
- publisher-hosted;
- content-addressed;
- bundled in exports;
- or all of the above?

### 103.3 Namespace verification

What mechanism proves control over a schema namespace?

### 103.4 Core schema governance

Which organisation or process controls the `com.relay` namespace?

### 103.5 Unknown fields

Should unknown fields be allowed anywhere, or only inside extension containers?

### 103.6 Schema inheritance

Should v0.1 support inheritance, or prefer composition only?

### 103.7 Rich text

What portable rich-text representation should core publishing schemas use?

### 103.8 Translation profiles

How should translation tools publish and sign mappings?

### 103.9 Security advisories

Who may issue authoritative schema security warnings?

### 103.10 Executable records

Should executable or automation schemas be permitted in v0.1?

### 103.11 Interoperability profiles

Which minimum profiles should the first reference implementation support?

### 103.12 Schema rights

What licence should apply to core schemas and registry metadata?

---

## 104. Provisional decisions for v0.1

Relay v0.1 will provisionally assume:

- schema-based JSON-compatible records;
- globally unique namespaced Schema Identifiers;
- explicit major schema versions;
- signed, integrity-addressed schema definitions;
- immutable published schema revisions;
- a small Relay core namespace;
- open application-defined namespaces;
- strict core fields with namespaced extension containers;
- deterministic protocol-level validation;
- preservation of unknown schemas and extensions;
- explicit application and provider support levels;
- optional schema translation with provenance;
- no silent lossy conversion;
- deprecation without invalidation;
- registry mirrors and export-bundled schema copies;
- composition preferred over unrestricted inheritance;
- no requirement that every application support every schema;
- interoperability profiles used to describe meaningful groups of supported schemas.

---

## 105. Core schema principle

The Schema and Interoperability Model can be reduced to one rule:

> Relay standardises enough meaning for applications to cooperate, while preserving the freedom to invent new record types without trapping the user inside the application that invented them.

The next core object is the **Relay Event and Synchronisation Model**: how applications, providers, mirrors and indexers learn that records, identities, permissions or relationships have changed without repeatedly downloading entire repositories.