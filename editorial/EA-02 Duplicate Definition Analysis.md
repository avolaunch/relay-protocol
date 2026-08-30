# Relay Editorial Audit 02

## Duplicate Definition Analysis

**Corpus:** Relay Protocol v0.1 design corpus  
**Scope:** `00-relay-at-a-glance.md` and Core Objects `01`–`15`  
**Status:** Draft for review  
**Purpose:** Identify repeated definitions, distinguish compatible restatement from semantic conflict, and recommend one future canonical source for each duplicated term.

---

## 1. Executive Summary

The corpus contains substantial repetition because each Core Object was written to remain understandable in isolation. Most repetition is compatible and does not indicate architectural contradiction.

The audit found:

- **3 direct duplicate-definition groups requiring a canonical wording decision**
- **6 compatible duplicate-definition groups requiring one authoritative source**
- **5 role-versus-compliance or object-versus-service overlaps that must remain distinct**
- **2 terminology collisions that could mislead implementers if left unresolved**
- **no evidence that the underlying Relay architecture has materially diverged across the corpus**

The two highest-priority terminology issues are:

1. **Controller** versus **Identity Controller**
2. **Relay Commit** versus **Commit**

The most important editorial rule arising from this audit is:

> The consolidated specification should define each protocol term once, then use role, compliance and operational chapters to add obligations without redefining the underlying concept.

---

## 2. Method

The 16 Markdown files were compared directly.

The review extracted:

- explicit definition sentences using forms such as “A **Term** is…”;
- repeated capitalised protocol terms;
- definitions restated in ecosystem, compliance or operational documents;
- terms whose scope changes between documents;
- nearby concepts that appear similar but represent different layers.

Each finding is classified as one of the following:

### A. Compatible duplicate

The definitions describe the same concept without material conflict.

### B. Scope expansion

A later definition broadens or narrows the original concept.

### C. Layer distinction

Two similar terms should remain separate because one describes a role, status, service or compliance claim rather than the underlying object.

### D. Terminology collision

The same or similar term is used in a way that could cause implementers to infer different protocol behaviour.

---

## 3. Summary Matrix

| # | Term or term group | Classification | Risk | Recommended canonical source |
|---|---|---|---|---|
| 1 | Relay Identity | Scope expansion | Medium | Identity Model |
| 2 | Controller / Identity Controller | Terminology collision | High | Identity Model, with Ecosystem Roles adding role detail |
| 3 | Relay Repository | Compatible duplicate | Low | Repository Model |
| 4 | Record / Relay Record | Compatible duplicate | Medium | Record Model |
| 5 | Relay Application | Scope expansion | High | Application and Permission Model |
| 6 | Application / Client | Layer distinction | Medium | Application and Client Compliance Model |
| 7 | Relay Provider / Relay-compatible Provider | Layer distinction | Medium | Ecosystem Roles for role; Provider Compliance for compliance status |
| 8 | Commit / Relay Commit | Terminology collision | High | Commit and Verification Model |
| 9 | Repository Head | Compatible duplicate | Low | Commit and Verification Model |
| 10 | Schema Registry | Compatible duplicate | Low | Schema and Interoperability Model |
| 11 | Witness | Scope expansion | Medium | Ecosystem Roles for role; Commit Model for repository-witness behaviour |
| 12 | Discovery / Resolution / Resolver / Discovery Service | Layer distinction | Medium | Discovery and Resolution Model |
| 13 | Migration / Migration Service | Layer distinction | Low | Migration Model for process; Ecosystem Roles for role |
| 14 | Permission Grant | Compatible duplicate | Low | Application and Permission Model |
| 15 | Relationship / Relay Relationship | Compatible duplicate | Low | Relationship Model |
| 16 | Conformance / certification / compliance | Layer distinction | High | Conformance Testing Model, with compliance documents retaining role-specific obligations |

---

# Part I — Direct Duplicate Definitions

## 4. Relay Identity

### Source definitions

**Identity Model, line 6**

> A Relay Identity is the persistent protocol-level entity through which a person or organisation exercises authority over records, relationships and application permissions.

**Ecosystem Roles, line 187**

> The Relay Identity is the persistent protocol entity represented by a Relay Identifier.

### Analysis

These definitions are compatible, but the Ecosystem Roles wording is narrower.

The Identity Model defines Relay Identity through:

- persistence;
- protocol-level existence;
- authority over records, relationships and permissions.

The Ecosystem Roles definition defines it mainly through representation by a Relay Identifier.

Being represented by a Relay Identifier is an attribute of Relay Identity, not its full meaning.

### Recommendation

Use the **Identity Model** as the canonical semantic source.

The consolidated glossary should define Relay Identity once using the broader Identity Model concept. Ecosystem Roles should reference the glossary and explain the Identity’s place among ecosystem actors without redefining it.

### Decision

**Canonical source:** Identity Model  
**Later treatment:** Reference only

---

## 5. Controller and Identity Controller

### Source definitions

**Identity Model, line 272**

> The Controller is the person, organisation or authorised authority capable of making changes to the Relay Identity.

**Migration and Portability Model, line 94**

> The Controller is the authority that approves migration.

**Ecosystem Roles, line 120**

> The Identity Controller is the human, organisation or authorised authority that holds ultimate control over a Relay Identity.

### Analysis

The Migration definition is not a complete definition of Controller. It describes one high-authority capability of the Controller within the migration context.

The Ecosystem Roles document introduces **Identity Controller**, while the earlier documents use **Controller**. The two terms appear to identify the same role.

There is no clear evidence in the corpus that “Identity Controller” is intended to be a separate protocol actor from “Controller.”

This creates a terminology collision because implementers could infer:

- Controller is a generic authority;
- Identity Controller is a separate subtype;
- Migration Controller is another role.

The corpus does not support those distinctions.

### Recommendation

Adopt **Controller** as the canonical term.

Use “Identity Controller” only as explanatory prose if necessary, not as a second defined protocol term.

The canonical definition should preserve the Ecosystem Roles concept of ultimate control while remaining broad enough to include:

- a person;
- an organisation;
- a threshold group;
- a guardian;
- another authorised authority.

Migration should state that the Controller authorises migration rather than redefining Controller.

### Decision

**Canonical term:** Controller  
**Retire as separate defined term:** Identity Controller  
**Canonical source:** Identity Model, enriched by Ecosystem Roles

---

## 6. Relay Repository

### Source definitions

**Repository Model, line 6**

> A Relay Repository is the canonical, portable and verifiable collection of records associated with a Relay Identity.

**Identity Model, line 861**

> The Relay Repository: the canonical collection of records associated with a Relay Identity and the mechanism through which those records remain verifiable, portable and usable across applications.

### Analysis

These definitions are compatible.

The Identity Model occurrence is a transition into the next Core Object, not an independent competing definition.

### Recommendation

Use the **Repository Model** as the sole canonical definition.

The Identity chapter should state that a Relay Identity may designate or control a Relay Repository and then reference the Repository section.

### Decision

**Canonical source:** Repository Model  
**Conflict:** None

---

## 7. Record and Relay Record

### Source definitions

**Repository Model, line 115**

> A Record is the smallest independently addressable structured object stored in a Relay Repository.

**Record Model, line 6**

> A Relay Record is a structured, independently addressable unit of information accepted into a Relay Repository.

### Analysis

The definitions are substantially compatible but differ in two meaningful ways:

- “smallest” appears only in the Repository Model;
- “accepted into” appears only in the Record Model.

“Smallest independently addressable” could be interpreted as a strict granularity requirement. Elsewhere, the corpus allows schemas to choose meaningful granularity and warns against excessive fragmentation. Therefore, “smallest” may be too absolute.

“Accepted into a Relay Repository” better reflects canonical state: a locally created draft is not a Relay Record merely because an application constructed it.

### Recommendation

Use **Relay Record** as the first-defined canonical term and permit **Record** as its shortened form after definition.

Use the **Record Model** as the semantic source.

Do not carry the unqualified word “smallest” into the canonical definition unless the later requirements explicitly define how minimum granularity is assessed.

### Decision

**Canonical term:** Relay Record; shortened form Record  
**Canonical source:** Record Model  
**Wording requiring review:** “smallest”

---

## 8. Relay Application

### Source definitions

**Application and Permission Model, line 6**

> A Relay Application is software that requests limited authority to read from, write to or otherwise interact with a Relay Identity or Relay Repository.

**Application and Client Compliance Model, line 78**

> A Relay Application is software identified by an Application Identity and described by an Application Manifest.

**Ecosystem Roles, line 577**

> A Relay Application is software that interacts with Relay Identities and Records through public access or valid Permission Grants.

### Analysis

The three definitions describe different aspects:

- the Permission Model defines the Application by delegated authority;
- the Compliance Model defines registration and identification;
- Ecosystem Roles defines the valid access paths.

They are compatible, but none alone is complete.

The most important semantic property is that a Relay Application is software that interacts with Relay resources under public access or explicit delegated authority. Application Identity and Application Manifest are requirements for non-public networked applications, not the fundamental meaning of Application itself.

### Recommendation

Use the **Application and Permission Model** as the canonical conceptual source, supplemented by the Ecosystem Roles restriction that interaction occurs through public access or valid Permission Grants.

Move Application Identity and Application Manifest into normative requirements rather than the base definition.

### Decision

**Canonical source:** Application and Permission Model  
**Supporting source:** Ecosystem Roles  
**Compliance wording:** Becomes obligations, not definition

---

# Part II — Compatible Duplicates

## 9. Permission Grant

### Source

**Application and Permission Model, line 309**

> A Permission Grant is a signed authorisation issued by the Relay Identity in response to a Permission Request.

The term is also repeatedly described in the Application Compliance, Provider Compliance, Migration and Event documents.

### Analysis

No competing formal definition was found.

Later documents add lifecycle and enforcement requirements, including:

- scope;
- revocation;
- expiration;
- event-subscription effects;
- migration handling.

These are obligations attached to Permission Grants, not alternative meanings.

### Recommendation

Keep the Application and Permission Model definition as canonical.

Do not redefine Permission Grant in compliance or event sections.

---

## 10. Repository Head

### Source definitions

**Repository Model, line 437**

> The Repository Head identifies the latest valid commit.

The Commit and Verification Model treats Repository Head as one of its core components and uses it throughout verification, fork and migration behaviour.

### Analysis

There is no contradictory definition.

However, Repository Head belongs semantically closer to commit history and verification than to general repository structure.

### Recommendation

Define Repository Head canonically in the **Commit and Verification** chapter, while the Repository chapter lists it as a required repository component and references the canonical definition.

---

## 11. Schema Registry

### Source definitions

**Schema and Interoperability Model, line 800**

> A Schema Registry is a searchable directory of schema definitions and metadata.

**Ecosystem Roles, line 925**

> A Schema Registry indexes and distributes schema definitions.

### Analysis

The definitions are compatible.

The first describes the object/service function. The second describes the ecosystem role.

### Recommendation

Use the Schema and Interoperability Model as the canonical definition.

Ecosystem Roles should specify capabilities and limitations without introducing a second definition.

---

## 12. Relay Relationship

### Source

**Relationship Model, line 6**

> A Relay Relationship is a structured, portable record describing a connection between Relay Identities, Relay Records or recognised external entities.

Other documents refer to relationships as persistent or portable connections but do not provide a competing formal definition.

### Analysis

No definition conflict was found.

The only editorial issue is that some explanatory text says relationships exist “between Records,” while the formal model permits:

- identities;
- records;
- groups;
- organisations;
- credentials;
- applications;
- external identifiers.

### Recommendation

Use the Relationship Model definition and avoid narrower shorthand elsewhere.

---

# Part III — Terminology Collisions

## 13. Relay Commit and Commit

### Source definitions

**Commit and Verification Model, line 6**

> A Relay Commit is a signed, ordered and verifiable statement that one or more changes have been accepted into a Relay Repository.

**Repository Model, line 371**

> A Commit is an authorised, verifiable set of repository operations.

**Commit and Verification Model, line 192**

> A Commit is an atomic group of validated operations accepted into the repository history.

### Analysis

These definitions overlap but are not identical.

The first defines a Commit as a signed statement of acceptance.

The second defines it as a set of operations.

The third defines it as an atomic group of validated operations.

All three concepts appear to be intended as one protocol object, but their wording leaves uncertainty over whether a Commit is:

- the operation collection itself;
- the signed envelope containing the operation collection;
- the statement that the operations were accepted.

This is the most significant technical definition issue found in the audit.

### Recommendation

Use one canonical term: **Commit**.

The future definition should explicitly distinguish:

- the Commit envelope;
- the operations contained within it;
- its signature;
- its previous-commit reference;
- the resulting repository state.

Use “Relay Commit” only on first introduction or when distinguishing it from non-Relay uses of the word.

The Commit and Verification chapter must be the canonical source.

### Decision

**Canonical term:** Commit  
**Canonical source:** Commit and Verification Model  
**Required future reconciliation:** Yes

---

## 14. Witness

### Source definitions

**Commit and Verification Model, line 964**

> A Witness is an independent service that observes and signs a repository state or commit.

**Ecosystem Roles, line 990**

> A Witness observes and signs a repository state, Identity Document or checkpoint.

### Analysis

The Ecosystem Roles definition broadens the scope from repository evidence to Identity Documents and checkpoints.

The definitions are compatible only if Witness is intended as a general role with several possible witnessing profiles.

If not clarified, an implementation could claim to be a Relay Witness after supporting only one narrow evidence type.

### Recommendation

Define **Witness** broadly in Ecosystem Roles as an actor that observes and signs a defined Relay state or checkpoint.

Define specific profiles or capability labels such as:

- Repository Witness;
- Identity Witness;
- Checkpoint Witness.

The Commit chapter should define repository-witness behaviour, not redefine the general role.

### Decision

**Canonical role source:** Ecosystem Roles  
**Technical profile source:** Commit and Verification Model

---

## 15. Scope

### Source

**Application and Permission Model, line 358**

> A Scope defines the boundary of access.

### Analysis

This is the only direct formal definition, but “scope” is also used generically throughout the corpus to mean:

- migration scope;
- export scope;
- verification scope;
- permission scope;
- subscription scope.

Capitalising **Scope** in the Permission Model risks implying that every later use refers to the Permission protocol object.

### Recommendation

Reserve **Permission Scope** for the defined permission construct.

Use lowercase “scope” for ordinary boundaries in migration, export, verification and testing.

This avoids turning a generic English word into an accidentally universal protocol object.

---

# Part IV — Terms That Must Remain Distinct

## 16. Application and Client

### Source definitions

**Application and Client Compliance Model, line 78**

> A Relay Application is software identified by an Application Identity and described by an Application Manifest.

**Application and Client Compliance Model, line 103**

> A Relay Client is an Application or Application component used directly or indirectly to interact with Relay services.

### Analysis

The corpus explicitly distinguishes these terms:

- **Application** is the registered software actor;
- **Client** is an implementation, interface or component.

This distinction should be retained.

The phrase “Application or Client” is useful in compliance headings but should not imply exact synonymy.

### Recommendation

Keep both terms and define their relationship once.

---

## 17. Relay Provider and Relay-compatible Provider

### Source definitions

**Ecosystem Roles, line 272**

> A Relay Provider is an organisation or individual that operates one or more Relay services for Controllers.

**Provider Compliance Model, line 6**

> A Relay-compatible Provider is a service operator that hosts or operates one or more Relay services while preserving the Controller’s ability to replace that Provider without losing identity, repository or relationship continuity.

### Analysis

These are intentionally different:

- **Relay Provider** describes a role;
- **Relay-compatible Provider** is a compliance claim.

A service could perform Provider-like functions without satisfying the Relay Provider compliance profile.

### Recommendation

Preserve the distinction.

The final specification should avoid calling an untested service “Relay-compatible” merely because it performs a Provider role.

---

## 18. Migration and Migration Service

### Analysis

**Relay Migration** is a protocol process.

**Migration Service** is an ecosystem actor that coordinates or performs that process.

These terms should remain distinct.

### Recommendation

Define Migration in the Migration chapter and Migration Service in Ecosystem Roles.

---

## 19. Discovery, Resolution, Resolver and Discovery Service

### Analysis

The Discovery and Resolution Model combines two related processes:

- **Discovery** finds possible identities, records, applications or services;
- **Resolution** obtains current verifiable operational information for a known handle, identifier or Record URI.

The Ecosystem Roles document separately identifies:

- **Resolver**;
- **Discovery Service**.

This separation is valid and should be made more explicit.

### Recommendation

Use these definitions:

- Discovery: candidate-finding process;
- Discovery Service: actor performing candidate discovery;
- Resolution: verification-oriented lookup process;
- Resolver: actor or service performing resolution.

Discovery results are not identity authority.

---

## 20. Conformance, Compliance and Certification

### Analysis

The corpus uses three closely related terms:

- **Compliance** in Provider and Application compliance documents;
- **Conformance** in the test model;
- **Certification** as a higher validation status.

The intended distinction appears to be:

- compliance: satisfying obligations;
- conformance: demonstrated protocol behaviour against a profile;
- certification: formal recognition under a governance-approved programme.

This distinction is useful but is not yet stated once in a shared canonical section.

### Recommendation

Define all three terms together in the Conformance chapter.

Compliance documents should state obligations. Conformance tests demonstrate observable satisfaction. Certification is an optional recognised status.

This is a high-priority clarification because the words are often treated as synonyms outside Relay.

---

# Part V — Cross-Corpus Definition Policy

## 21. Canonical Definition Hierarchy

The consolidated specification should use the following hierarchy:

1. **Glossary**  
   Provides the concise canonical semantic definition.

2. **Concept chapter**  
   Provides complete structure, lifecycle and protocol behaviour.

3. **Ecosystem Roles chapter**  
   Adds actor capabilities and limitations without redefining the concept.

4. **Compliance chapters**  
   Add MUST, MUST NOT, SHOULD and MAY obligations.

5. **Conformance chapter**  
   Defines how those obligations are tested.

6. **Governance chapter**  
   Defines how the definitions and obligations may evolve.

---

## 22. Terms Recommended for Immediate Canonicalisation

The following terms should be settled before drafting substantive specification chapters:

1. Controller
2. Relay Identity
3. Relay Record / Record
4. Relay Application / Application
5. Client
6. Relay Provider
7. Relay-compatible Provider
8. Commit
9. Witness
10. Permission Scope
11. Conformance
12. Compliance
13. Certification

---

## 23. Terms Requiring No Conceptual Change

The following duplicates appear compatible and can be consolidated editorially without altering protocol meaning:

- Relay Repository
- Permission Grant
- Repository Head
- Schema Registry
- Relay Relationship
- Migration / Migration Service
- Discovery / Resolution role distinctions

---

## 24. Terms Requiring Future Wording Reconciliation

### Commit

The specification must settle whether the signed Commit is:

- the envelope;
- the operation collection;
- the acceptance statement;
- or a defined object containing all three.

### Controller

The specification must merge the Identity Model and Ecosystem Roles wording while retiring “Identity Controller” as a separate defined term.

### Relay Application

The specification must combine:

- software actor;
- public or delegated authority;
- Application Identity;
- Application Manifest;

without making every local or offline client depend on central registration.

### Witness

The specification must determine whether Witness is:

- one broad role with capability profiles;
- or several formally distinct witness roles.

---

# Part VI — Findings and Decisions

## 25. Finding Summary

### Finding DD-01

The design corpus contains repetition by design, but little true semantic contradiction.

### Finding DD-02

Most later definitions in Ecosystem Roles and compliance documents should become role descriptions or obligations rather than independent definitions.

### Finding DD-03

The terms Controller, Commit and Relay Application require the most careful consolidation.

### Finding DD-04

Several pairs that look duplicated are valid layer distinctions and must not be collapsed:

- Application / Client;
- Provider / Relay-compatible Provider;
- Migration / Migration Service;
- Discovery / Resolution;
- Compliance / Conformance / Certification.

### Finding DD-05

The corpus supports a single coherent semantic model and does not show evidence that the original premise has been diluted across the 15 Core Objects.

---

## 26. Editorial Decisions Proposed

### ED-008 — Single Definition Rule

Each capitalised protocol term will have one canonical definition.

### ED-009 — Concept Before Obligation

Concept chapters define terms. Compliance chapters add obligations without redefining them.

### ED-010 — Canonical Controller Term

Use **Controller** as the canonical term. Do not define **Identity Controller** separately.

### ED-011 — Canonical Commit Term

Use **Commit** as the canonical term and explicitly define its envelope, operations, signature and resulting state.

### ED-012 — Role and Status Separation

Preserve the distinction between a role and a compliance status, especially:

- Relay Provider;
- Relay-compatible Provider.

### ED-013 — Generic Word Protection

Generic terms such as “scope,” “authority,” “profile” and “state” should be capitalised only when referring to a specifically defined Relay construct.

---

## 27. Recommended Next Artifact

The next editorial artifact should be:

```text
editorial/03-canonical-terminology-map.md
```

It should convert the findings in this report into a controlled table containing:

- canonical term;
- approved short form;
- deprecated synonym;
- source definition;
- future glossary location;
- related terms;
- unresolved wording issue.

That map should be approved before the full Requirements Audit begins.

---

## 28. Audit Status

**Editorial Audit 02: Duplicate Definition Analysis — Complete**

The corpus is ready for canonical terminology mapping.

