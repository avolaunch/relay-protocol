# Relay Protocol v0.1  
## Core Object 15: Governance and Evolution Model

### 1. Definition

The **Relay Governance and Evolution Model** defines how the Relay Protocol, core schemas, reserved namespaces, conformance profiles and official specifications may change over time.

Relay governance does not own:

- Relay Identities;
- Relay Repositories;
- Relay Records;
- Provider infrastructure;
- Applications;
- implementations;
- user relationships;
- third-party schemas.

Its role is stewardship.

Governance exists to maintain the shared technical commons required for independent implementations to interoperate without allowing one company, Provider, Application or implementation to redefine Relay unilaterally.

The central requirement is:

> Relay must be capable of evolving without becoming owned.

---

## 2. Purpose

The Governance and Evolution Model exists to answer:

- who may propose changes;
- who reviews proposals;
- how decisions are made;
- which principles may not be weakened;
- how specifications are versioned;
- how core namespaces are maintained;
- how conformance requirements evolve;
- how security emergencies are handled;
- how governance itself may be replaced.

The model must protect Relay from two opposite failures.

### Governance capture

One organisation gains practical control over the protocol and bends it toward its commercial interests.

### Governance paralysis

The protocol becomes unable to respond to:

- security failures;
- cryptographic changes;
- interoperability problems;
- new technologies;
- implementation experience;
- legitimate user needs.

Relay must remain stable enough to trust and adaptable enough to survive.

---

# Part I — Constitutional Foundation

## 3. Constitutional layer

Relay distinguishes between:

1. **Constitutional principles**
2. **Protocol requirements**
3. **Implementation choices**
4. **Application and Provider policy**

These layers have different change thresholds.

### Constitutional principles

Define the permanent ownership and continuity guarantees of Relay.

### Protocol requirements

Define interoperable technical behaviour.

### Implementation choices

Define how one implementation satisfies those requirements internally.

### Application and Provider policy

Define optional service, moderation and commercial decisions within protocol boundaries.

A popular implementation or policy must not silently become a constitutional rule.

---

## 4. The Continuity Principle

Relay’s primary constitutional rule is:

> No future Relay version may intentionally reduce a Controller’s ownership, portability or continuity compared with the minimum guarantees of an earlier compliant version.

This means future Relay versions must not make:

- Relay Identities permanently Provider-owned;
- repository migration optional for compliant Providers;
- Record URIs dependent on Applications;
- Permission Grants irrevocable;
- application replacement impossible;
- identity recovery dependent on one commercial service;
- canonical records inseparable from proprietary interfaces;
- unknown valid data disposable during migration.

A future version may introduce new models that are:

- more secure;
- more private;
- more efficient;
- easier to use;
- more decentralised;
- more interoperable.

It must not remove the underlying ability of a person to preserve continuity.

---

## 5. Constitutional objects

The following are constitutional objects within Relay:

- Relay Identity;
- Controller authority;
- Provider replaceability;
- Application replaceability;
- Repository portability;
- stable Record identity;
- explicit permission;
- revocation;
- relationship continuity;
- independent verification;
- preservation of unknown valid data;
- role separation;
- open implementation rights.

These objects may be clarified or strengthened.

They may not be removed merely because doing so benefits a dominant implementation.

---

## 6. Non-constitutional technical choices

The following are not permanently constitutional and may evolve:

- hash algorithms;
- signature algorithms;
- serialisation;
- compression;
- transport protocols;
- database architecture;
- event-delivery mechanisms;
- schema language;
- identifier encoding;
- storage systems;
- synchronisation optimisations.

Changes to these systems must still preserve constitutional continuity.

---

## 7. Constitutional regression

A proposal constitutes a **Constitutional Regression** when it would materially weaken one or more of the following:

- Controller authority;
- portability;
- migration;
- application replaceability;
- Provider replaceability;
- permission boundaries;
- independent verification;
- durable record identity;
- open implementation.

Examples include:

```text
Allowing a Provider to refuse all operational migration while remaining fully compliant.

Allowing an Application to become the sole authority for canonical records.

Allowing identity resolution to depend permanently on one commercial registry.

Allowing general model training under ordinary read permission.
```

Constitutional regressions must not be accepted through ordinary protocol evolution.

---

## 8. Constitutional amendment

Relay may require a mechanism for correcting or redefining a constitutional rule under extraordinary circumstances.

A constitutional amendment should require:

- a clearly identified necessity;
- public rationale;
- documented alternatives;
- compatibility analysis;
- user-impact analysis;
- extended review period;
- extraordinary approval threshold;
- implementation diversity;
- migration path;
- explicit acknowledgement that the change affects constitutional guarantees.

Some changes may remain prohibited even with broad support where they would negate Relay’s purpose.

---

# Part II — Permanent Design Principles

## 9. People are persistent

People and other valid Controllers are the persistent entities of Relay.

Providers and Applications are replaceable participants.

---

## 10. Applications compete through experience

Applications should differentiate through:

- design;
- workflow;
- algorithms;
- features;
- community;
- performance.

They must not compete by capturing identity or canonical data.

---

## 11. Providers compete through service

Providers should compete through:

- reliability;
- security;
- support;
- price;
- jurisdiction;
- storage;
- privacy;
- recovery;
- performance.

They must not compete by making departure technically impossible.

---

## 12. Migration is valid operation

Migration is not a failure, breach or exceptional concession.

It is a normal protocol capability.

A successful Provider may still lose a customer to another Provider without the user losing continuity.

---

## 13. Unknown data should survive

A compliant system should preserve valid records and extensions it does not understand.

Lack of interpretation is not permission to destroy.

---

## 14. Backward continuity matters

Protocol evolution should preserve the ability to:

- resolve older identities;
- verify older records;
- interpret earlier schemas;
- migrate earlier repositories;
- understand historical signatures.

Backward continuity does not require every old feature to remain actively recommended forever.

---

## 15. Interoperability outranks dominance

A widely used implementation does not gain the right to redefine Relay unilaterally.

Market share does not equal specification authority.

---

## 16. Usability is part of control

Relay must not preserve theoretical ownership while making ordinary use impractical.

Governance should consider:

- recovery;
- onboarding;
- permissions;
- migration;
- comprehensibility;
- accessibility.

A system that only experts can control has failed part of its purpose.

---

## 17. Security must not become captivity

Security improvements must not quietly make:

- Providers permanently indispensable;
- user-held recovery impossible;
- independent verification inaccessible;
- migration dependent on one vendor.

Strong security and replaceability must be designed together.

---

## 18. Governance must be replaceable

Relay applies its own principles to its governance.

The governance body must remain capable of being replaced or reorganised without destroying the protocol, core namespace or specification history.

---

# Part III — Governance Structure

## 19. Stewardship body

Relay should be stewarded by an independent organisation or process.

A mature structure may take the form of:

- non-profit foundation;
- standards consortium;
- public technical organisation;
- federated governance body;
- multi-stakeholder institution.

The Stewardship Body should not be structurally identical to one dominant commercial Relay Provider.

---

## 20. Stewardship responsibilities

The Stewardship Body may:

- publish official specifications;
- maintain constitutional principles;
- coordinate protocol versions;
- maintain reserved namespaces;
- publish core schemas;
- govern conformance profiles;
- maintain test suites;
- coordinate security disclosures;
- archive specification history;
- facilitate public technical discussion;
- recognise independent certification bodies.

---

## 21. Stewardship limitations

The Stewardship Body must not:

- own Relay Identities;
- operate the mandatory global Provider;
- require all traffic through its infrastructure;
- approve every third-party schema;
- control every Application directory;
- access private repositories by default;
- convert specification stewardship into commercial platform ownership.

---

## 22. Governance constituencies

Relay governance should include representation from several constituencies.

Possible constituencies include:

- individual users;
- accessibility advocates;
- privacy and security specialists;
- Application developers;
- Provider operators;
- independent implementers;
- civil-society organisations;
- researchers;
- standards experts;
- enterprise and organisational users;
- public-interest representatives.

No one constituency should permanently control ordinary protocol development.

---

## 23. Technical Steering Council

A **Technical Steering Council** may oversee:

- specification quality;
- protocol consistency;
- version planning;
- technical proposals;
- test-suite alignment;
- implementation feedback.

Its members should disclose:

- employers;
- financial interests;
- Provider affiliations;
- Application affiliations;
- relevant conflicts.

---

## 24. Constitutional Council

A separate **Constitutional Council** may review whether major proposals comply with Relay’s foundational guarantees.

Its responsibility is not to design APIs.

It evaluates whether changes weaken:

- continuity;
- portability;
- authority;
- replaceability;
- openness;
- role separation.

This function may be performed by a dedicated council or through a formal review stage.

---

## 25. Working groups

Governance may establish topic-specific Working Groups.

Examples:

```text
Identity and Resolution
Repository and Verification
Permissions and Privacy
Migration
Schemas
Applications
Conformance
Cryptography
Accessibility
AI and Automation
```

Working Groups may draft proposals.

They do not independently redefine the official protocol.

---

## 26. Editors

Specification Editors maintain:

- document structure;
- terminology;
- issue tracking;
- accepted proposal integration;
- publication formatting;
- change logs.

Editors do not gain unilateral authority to introduce substantive behavioural changes.

---

## 27. Implementer Forum

An **Implementer Forum** may provide structured feedback from organisations and individuals building Relay systems.

It may identify:

- ambiguous requirements;
- incompatible interpretations;
- performance issues;
- deployment challenges;
- missing test cases;
- migration failures.

Implementation popularity does not automatically determine protocol policy, but practical evidence must be considered seriously.

---

## 28. User Forum

A **User Forum** or public-interest review process should examine:

- migration usability;
- consent clarity;
- recovery;
- data-loss risks;
- accessibility;
- real-world lock-in;
- non-technical harms.

Relay governance must not become exclusively an engineering exercise.

---

# Part IV — Decision Authority

## 29. Specification authority

The official Relay specification is authoritative for protocol conformance.

Neither:

- the reference implementation;
- the largest Provider;
- the most popular Application;
- the test suite alone;
- an unofficial documentation site;

may silently redefine normative behaviour.

Where specification and test suite conflict, the conflict must be resolved openly.

---

## 30. Reference implementation authority

The reference implementation is:

- an example;
- a test target;
- an implementation aid;
- a source of practical feedback.

It is not automatically correct merely because it is official or widely deployed.

Implementation behaviour inconsistent with the specification must be treated as a bug or specification ambiguity.

---

## 31. Conformance-suite authority

The conformance suite operationalises the specification.

It must not introduce material normative behaviour absent from the published specification.

Every normative test should reference the requirement it tests.

---

## 32. Precedent

Past implementation behaviour may inform proposals.

It does not become permanent protocol law merely through long use.

Where widespread behaviour diverges from the specification, governance may:

- update implementations;
- clarify the specification;
- formalise a compatible extension;
- define a migration path;
- deprecate the behaviour.

---

# Part V — Proposal Process

## 33. Relay Improvement Proposal

Substantive changes should be introduced through a **Relay Improvement Proposal**, or RIP.

A RIP may propose:

- protocol feature;
- core schema;
- new conformance profile;
- governance change;
- security improvement;
- deprecation;
- clarification;
- interoperability profile.

The acronym is provisional.

---

## 34. Proposal contents

A proposal should include:

- title;
- author or authors;
- status;
- change category;
- affected protocol sections;
- problem statement;
- proposed behaviour;
- rationale;
- alternatives considered;
- compatibility impact;
- migration plan;
- security impact;
- privacy impact;
- accessibility impact;
- implementation experience;
- conformance implications;
- constitutional assessment.

---

## 35. Proposal states

A proposal may move through:

```text
Draft
Under Discussion
Experimental
Candidate
Accepted
Rejected
Deferred
Withdrawn
Superseded
Final
Deprecated
```

The exact state model may be refined.

---

## 36. Draft

A Draft is incomplete and open to substantial change.

It has no normative effect.

---

## 37. Experimental

An Experimental proposal may be implemented for learning without becoming part of core Relay compliance.

Experimental features must be:

- namespaced;
- optional;
- non-destructive;
- clearly identified;
- unable to weaken existing compliant behaviour.

---

## 38. Candidate

A Candidate proposal is considered technically mature enough for:

- implementation trials;
- interoperability testing;
- security review;
- conformance-draft preparation.

It remains non-final.

---

## 39. Accepted

An Accepted proposal has completed the required review and approval process.

It may still require integration into a versioned specification before becoming normative.

---

## 40. Final

A Final proposal has been incorporated into an official Relay specification, profile or governance document.

---

## 41. Rejected

A Rejected proposal remains archived with:

- rationale;
- objections;
- relevant discussion;
- possible conditions for reconsideration.

Rejected ideas should not disappear from institutional memory.

---

# Part VI — Change Categories

## 42. Editorial change

An Editorial Change affects:

- spelling;
- formatting;
- broken references;
- wording without behavioural effect.

It may use an expedited review process.

---

## 43. Clarification

A Clarification makes existing intended behaviour more precise without changing conformant outcomes.

If two reasonable implementations would behave differently before the clarification, it may be more than editorial and require broader review.

---

## 44. Compatible addition

A Compatible Addition introduces optional capability without breaking existing compliant systems.

Examples include:

- optional event transport;
- new schema extension point;
- additional verification proof;
- optional service descriptor.

---

## 45. New profile

A New Profile defines an optional interoperable capability set.

Existing implementations need not support it unless they claim that profile.

---

## 46. Core schema addition

A proposal may introduce a new schema under the reserved Relay namespace.

It must satisfy the Minimal Core test.

---

## 47. Deprecation

Deprecation discourages future use while preserving:

- historical verification;
- migration;
- export;
- documented replacement path.

Deprecation is not immediate removal.

---

## 48. Breaking protocol change

A Breaking Change causes previously compliant implementations or objects to become incompatible without adaptation.

It requires:

- strong justification;
- migration plan;
- long transition;
- dual support where feasible;
- elevated approval threshold.

---

## 49. Security emergency

A Security Emergency addresses an active severe vulnerability.

It may use accelerated procedures while preserving:

- accountability;
- limited scope;
- later public review;
- rollback or revision;
- constitutional constraints.

Emergency authority must not become a general shortcut around governance.

---

## 50. Constitutional amendment

A Constitutional Amendment changes foundational guarantees or governance structure.

It requires the highest level of scrutiny and approval.

A proposal intended primarily to weaken portability or Controller authority should be presumptively rejected.

---

# Part VII — Review Requirements

## 51. Technical review

Technical review should consider:

- consistency;
- implementability;
- interoperability;
- complexity;
- performance;
- failure modes;
- migration;
- testability.

---

## 52. Security review

Security review should consider:

- new authority paths;
- key compromise;
- replay;
- downgrade;
- privacy leakage;
- denial of service;
- role confusion;
- malicious Provider behaviour;
- malicious Application behaviour.

---

## 53. Privacy review

Privacy review should consider:

- new public metadata;
- graph exposure;
- cross-role data use;
- inference risk;
- retention;
- AI processing;
- resolver leakage;
- migration copies.

---

## 54. Portability review

Every substantive proposal should answer:

> Does this make any Provider, Application, registry, governance body or infrastructure operator harder to replace?

If so, the proposal must justify the dependency and provide mitigation.

---

## 55. Accessibility review

Changes affecting:

- authentication;
- consent;
- recovery;
- migration;
- user interfaces;
- identity presentation;

should receive accessibility review.

Technical sovereignty that excludes users with disabilities is incomplete sovereignty.

---

## 56. Competition and capture review

Major proposals should be reviewed for whether they:

- privilege one implementation;
- require proprietary infrastructure;
- create unreasonable certification barriers;
- centralise resolution;
- advantage incumbents;
- prevent small Providers or local Clients from participating.

---

## 57. Constitutional review

The proposal must identify:

- affected constitutional objects;
- whether continuity is strengthened or weakened;
- whether role separation changes;
- whether migration changes;
- whether user authority changes.

---

# Part VIII — Decision Process

## 58. Consensus preference

Relay governance should prefer reasoned consensus over simple majority voting for technical decisions.

Consensus does not require unanimous agreement.

It requires that:

- objections are heard;
- major concerns are addressed;
- alternatives are considered;
- remaining disagreement is documented.

---

## 59. Voting

Voting may be used when consensus cannot be reached or where formal approval is required.

Voting rules should prevent one commercial bloc from controlling decisions through membership volume alone.

Possible mechanisms include:

- constituency-balanced voting;
- supermajority;
- conflict-of-interest recusal;
- implementation-diversity requirements;
- public-interest approval.

---

## 60. Approval thresholds

Possible thresholds include:

### Editorial

Editor approval with public record.

### Clarification

Technical review and ordinary council approval.

### Compatible addition

Technical approval plus implementation evidence.

### Breaking change

Supermajority plus migration and conformance evidence.

### Constitutional amendment

Extraordinary supermajority across multiple constituencies and extended public review.

---

## 61. Implementation evidence

Major technical additions should normally require at least:

- two independent implementations;
- or one implementation and one independent prototype;
- interoperability testing;
- draft conformance tests.

This helps prevent the specification from formalising one vendor’s untested architecture.

---

## 62. Independent implementation

Two implementations are independent when they are not merely:

- deployments of the same codebase;
- controlled by one organisation;
- using one hidden proprietary service;
- sharing the same unreviewed internal library for the feature being tested.

Shared open libraries do not automatically eliminate independence, but diversity should be assessed honestly.

---

## 63. Public review period

Substantive proposals should remain publicly reviewable for a defined minimum period.

The period may vary by category.

Security emergencies may initially be restricted but must receive later transparent review.

---

## 64. Objection record

Serious unresolved objections should be published with the final decision.

This preserves:

- minority reasoning;
- future reconsideration;
- implementation warnings;
- institutional accountability.

---

# Part IX — Versioning

## 65. Protocol versions

Official Relay versions should identify:

- major version;
- minor version;
- revision or errata level.

Example:

```text
Relay Protocol 1.2.3
```

The exact versioning scheme remains open.

---

## 66. Major version

A major version may include:

- breaking technical changes;
- major architectural change;
- revised conformance baseline;
- replacement of foundational mechanisms.

Major versions require explicit migration and compatibility planning.

---

## 67. Minor version

A minor version may add:

- backward-compatible capabilities;
- optional profiles;
- new schemas;
- new service descriptors;
- non-breaking security improvements.

---

## 68. Revision

A revision may include:

- clarifications;
- editorial corrections;
- non-behavioural improvements;
- errata.

---

## 69. Version support

Governance should publish:

- active versions;
- supported versions;
- maintenance versions;
- deprecated versions;
- security-only versions;
- end-of-support guidance.

---

## 70. Multi-version interoperability

During transitions, Providers and Applications may support several Relay versions.

Identity Documents and service manifests should declare:

- supported versions;
- preferred version;
- minimum secure version.

---

## 71. Downgrade prevention

Version negotiation must not allow an attacker to force an insecure older version.

Governance should publish minimum safe version guidance following severe vulnerabilities.

---

## 72. Long-term historical verification

Even after a version is deprecated, the ecosystem should retain enough documentation and software to:

- verify historical records;
- read old exports;
- interpret old Identity Documents;
- understand deprecated schemas;
- migrate where feasible.

---

# Part X — Reserved Namespaces

## 73. Reserved namespace purpose

Relay governance may reserve namespaces required for shared protocol meaning.

Examples may include:

```text
relay.identity
relay.repository
relay.permission
relay.relationship
relay.event
relay.profile
relay.post
```

The exact naming convention remains unresolved.

---

## 74. Minimal Core test

A schema or event belongs in the reserved namespace only when:

- multiple unrelated implementations need common meaning;
- portability materially depends on standardisation;
- the concept is sufficiently stable;
- external namespacing would cause harmful fragmentation;
- governance burden is justified.

---

## 75. External innovation

Third-party schemas, event types and extensions should not require central approval where they use valid external namespaces.

Governance coordinates the commons.

It does not approve all innovation.

---

## 76. Namespace allocation

Reserved namespace allocation should require:

- clear purpose;
- conflict analysis;
- semantic definition;
- security review;
- interoperability need;
- test fixtures;
- versioning plan.

---

## 77. Namespace squatting

Governance may reject or remove abusive registrations intended only to:

- block legitimate names;
- impersonate another publisher;
- mislead implementers;
- create artificial scarcity.

External namespaces should ordinarily be tied to verifiable publisher authority.

---

## 78. Namespace transfer

A namespace must not be transferred silently.

Transfer should require:

- current authority;
- new authority;
- public notice;
- signed transition;
- historical continuity;
- clear effect on existing schemas.

---

## 79. Abandoned namespace

If a publisher disappears, existing schemas remain attributable to that publisher.

Another party may:

- mirror them;
- preserve them;
- fork them under a new namespace;
- maintain compatibility tools.

The original namespace should not be casually reassigned.

---

# Part XI — Core Schema Governance

## 80. Core schema stability

Core schemas should evolve conservatively.

A fashionable Application feature is not sufficient reason to add a core schema.

---

## 81. Core schema proposal

A core schema proposal should include:

- interoperability use case;
- at least two intended implementations;
- privacy analysis;
- lifecycle rules;
- versioning plan;
- migration plan;
- sample records;
- invalid records;
- conformance fixtures.

---

## 82. Core schema versioning

Breaking semantic changes require a new major Schema Identifier.

Old versions remain valid and preservable.

---

## 83. Core schema deprecation

Deprecation should provide:

- reason;
- replacement;
- migration guidance;
- continued preservation requirement;
- historical verification support;
- expected support timeline.

---

# Part XII — Conformance Governance

## 84. Test-suite openness

The official conformance suite must be:

- openly reviewable;
- independently runnable;
- versioned;
- linked to specification requirements;
- reproducible.

---

## 85. Test change control

A normative test must not be added secretly.

Test changes should identify:

- specification requirement;
- expected behaviour;
- affected profiles;
- compatibility impact;
- reason.

---

## 86. Test and specification conflict

Where a test conflicts with the specification:

- the discrepancy must be reported;
- affected certification should be reviewed;
- the test must not silently redefine the protocol;
- governance must clarify or amend the specification.

---

## 87. Certification decentralisation

Relay may recognise multiple independent certification providers.

Certification must not require purchasing services from one mandatory commercial operator.

---

## 88. Conformance mark stewardship

Governance may protect official Relay conformance marks against misleading use.

The mark represents tested profile compliance, not general endorsement.

---

# Part XIII — Security Governance

## 89. Security response function

Relay governance should maintain a process for:

- receiving vulnerability reports;
- coordinating affected implementations;
- assessing severity;
- preparing advisories;
- managing embargoes;
- updating tests;
- publishing mitigations;
- supporting cryptographic transitions.

---

## 90. Security advisory

An advisory should identify:

- affected versions;
- affected profiles;
- severity;
- exploitation conditions;
- mitigations;
- upgrade guidance;
- compatibility implications;
- disclosure timeline.

---

## 91. Coordinated disclosure

Temporary confidentiality may be appropriate while:

- patches are prepared;
- Providers are notified;
- active exploitation is assessed;
- users are protected.

Confidentiality must remain limited and accountable.

---

## 92. Emergency specification update

An emergency update may temporarily:

- disable an unsafe feature;
- raise minimum versions;
- deprecate a key algorithm;
- require additional verification;
- alter conformance status.

Emergency changes must later receive ordinary review.

---

## 93. Cryptographic transition

Governance must support planned transition when:

- hash algorithm weakens;
- signature system weakens;
- canonical encoding is unsafe;
- key sizes become inadequate.

A transition should preserve:

- historical verification;
- stable logical identifiers;
- migration;
- dual-signature or checkpoint paths where needed.

---

# Part XIV — Conflicts of Interest

## 94. Disclosure

Governance participants should disclose relevant interests including:

- employment;
- ownership;
- investment;
- Provider operation;
- Application operation;
- patent interests;
- certification revenue;
- consulting relationships.

---

## 95. Recusal

A participant may be required to recuse from decisions directly affecting a significant private interest.

Recusal should not prevent technical input, but may restrict formal decision authority.

---

## 96. Dominant implementation influence

A dominant implementation may provide valuable expertise.

It must not gain unilateral specification authority merely because many users depend on it.

Governance should actively seek input from:

- smaller implementations;
- independent Clients;
- self-hosters;
- public-interest groups;
- competing Providers.

---

## 97. Funding transparency

The Stewardship Body should publish:

- major funding sources;
- sponsor terms;
- restricted funding;
- financial reports;
- conflicts.

Funding must not purchase protocol control.

---

# Part XV — Intellectual Property and Open Implementation

## 98. Open specification

Relay specifications, core schemas and conformance materials should be available under terms permitting:

- reading;
- implementation;
- testing;
- redistribution;
- archival;
- translation;
- derivative documentation.

---

## 99. Patent policy

Governance should adopt a patent policy preventing contributors from using essential protocol patents to block compliant implementation.

Possible approaches include:

- royalty-free commitments;
- defensive patent terms;
- disclosure obligations;
- patent non-assertion.

The precise legal structure requires specialist review.

---

## 100. Trademark policy

Relay trademarks may protect against:

- false compliance claims;
- impersonation;
- misleading certification.

Trademark control must not prevent independent discussion, implementation or interoperability.

---

## 101. Implementation licensing

Relay does not require every implementation to use one software licence.

Implementations may be:

- open source;
- commercial;
- proprietary;
- public-sector;
- community-operated.

Protocol interoperability and conformance remain mandatory for compliance claims.

---

# Part XVI — Governance Transparency

## 102. Public records

Governance should publish:

- proposals;
- meeting minutes;
- decisions;
- votes;
- objections;
- conflicts;
- test changes;
- specification history;
- security advisories after appropriate disclosure.

---

## 103. Private sessions

Private discussion may be necessary for:

- active vulnerabilities;
- personnel matters;
- legal privilege;
- sensitive negotiations.

The scope and duration of confidentiality should be limited.

---

## 104. Decision rationale

Every substantive accepted or rejected proposal should include a rationale.

The rationale should explain:

- problem;
- decision;
- alternatives;
- major objections;
- expected effects;
- review requirements.

---

## 105. Archival permanence

Governance records should be preserved through:

- public repositories;
- signed releases;
- independent mirrors;
- institutional archives;
- content-addressed copies.

The specification history should not depend on one website remaining online.

---

# Part XVII — Governance Replacement

## 106. Governance by replacement

Relay’s Stewardship Body must itself remain replaceable.

Replacement may become necessary because of:

- capture;
- insolvency;
- inactivity;
- corruption;
- loss of legitimacy;
- legal incapacity;
- sustained failure to maintain the protocol.

---

## 107. Stewardship transfer

A valid transfer should preserve:

- specification history;
- reserved namespaces;
- conformance materials;
- trademarks where legally possible;
- security records;
- proposal archive;
- constitutional commitments.

---

## 108. Transfer triggers

Possible transfer triggers include:

- voluntary succession;
- supermajority decision;
- institutional dissolution;
- failure to meet published governance duties;
- independent constitutional review;
- emergency continuity process.

---

## 109. Governance fork

Because specifications are open, a governance fork may occur.

A forked project may publish a different protocol direction.

It must use:

- distinguishable versioning;
- distinguishable governance identity;
- honest compatibility claims;
- clear namespace treatment.

A fork must not impersonate official continuity deceptively.

---

## 110. Legitimacy after fork

Technical compatibility, constitutional adherence, implementer support and public legitimacy may influence which stewardship branch is regarded as the continuing Relay standard.

No legal trademark alone should determine technical truth.

The exact succession model requires further design.

---

## 111. Emergency continuity custodian

Governance may designate independent custodians capable of preserving:

- specifications;
- keys;
- namespace records;
- test suites;
- archives;

if the Stewardship Body becomes unavailable.

Custodians do not gain ordinary protocol control merely through preservation.

---

# Part XVIII — Appeals and Disputes

## 112. Technical appeal

A contributor or implementation may appeal:

- proposal rejection;
- certification result;
- namespace decision;
- conformance interpretation;
- procedural failure.

The appeal process should be documented and time-bound.

---

## 113. Constitutional appeal

A proposal alleged to violate constitutional principles may receive independent review.

The review should focus on continuity and authority rather than commercial preference.

---

## 114. Certification dispute

A certification dispute may concern:

- test error;
- incorrect profile;
- production mismatch;
- false badge use;
- unresolved failure.

Certification disputes must not affect hosted users’ identities or repository ownership.

---

## 115. Namespace dispute

A namespace dispute may involve:

- impersonation;
- authority conflict;
- abandonment;
- trademark claim;
- compromised publisher key.

Governance should distinguish technical namespace authority from broader legal naming rights.

---

# Part XIX — Required Governance Operations

## 116. Governance operations

A mature governance system should support:

```text
Submit proposal
Classify proposal
Assign reviewers
Publish discussion
Record conflicts
Run constitutional review
Run security review
Run privacy review
Publish candidate specification
Coordinate implementation trials
Publish draft conformance tests
Approve proposal
Reject proposal
Publish rationale
Release protocol version
Release schema version
Deprecate feature
Publish security advisory
Archive historical version
Transfer stewardship
```

---

# Part XX — Governance Invariants

## 117. Governance invariants

The following rules must always remain true.

### Invariant 1

The Stewardship Body does not own Relay Identities or Repositories.

### Invariant 2

No implementation becomes the specification merely through popularity.

### Invariant 3

No single Provider or Application receives unilateral protocol authority.

### Invariant 4

Protocol evolution must preserve constitutional continuity.

### Invariant 5

Migration and replaceability cannot be removed through ordinary change.

### Invariant 6

The reserved namespace governs shared meaning, not all innovation.

### Invariant 7

Third parties may create schemas and extensions without central product approval.

### Invariant 8

Normative changes require public traceability.

### Invariant 9

Conformance tests must remain linked to published requirements.

### Invariant 10

Security emergency powers remain limited and reviewable.

### Invariant 11

Funding does not purchase specification control.

### Invariant 12

Conflicts of interest must be disclosed.

### Invariant 13

Historical specifications and schemas remain publicly preservable.

### Invariant 14

Relay implementation must remain legally and technically open to independent parties.

### Invariant 15

The governance body itself remains replaceable.

---

# Part XXI — Governance Compliance Scenario

## 118. Compatible feature proposal

A developer proposes an optional encrypted event profile.

The proposal includes:

- threat model;
- protocol design;
- two prototypes;
- privacy analysis;
- conformance fixtures;
- compatibility impact.

The proposal enters Experimental status.

Two independent implementations interoperate successfully.

After review, it becomes a New Profile in Relay v0.2.

Relay v0.1 implementations remain compliant with v0.1.

---

## 119. Dominant Provider proposal

A dominant Provider proposes that all Relay Identifiers resolve through its global registry.

The proposal would simplify discovery but would make the Provider operationally indispensable.

The portability and constitutional reviews identify a Constitutional Regression.

The proposal is rejected in its current form.

A revised design permits multiple independently verifiable resolvers.

---

## 120. Security emergency

A required signature algorithm is found to be vulnerable.

Governance:

1. privately coordinates initial disclosure;
2. publishes an emergency advisory;
3. marks the algorithm unsafe for new high-authority actions;
4. defines a dual-signature transition;
5. updates conformance tests;
6. preserves historical verification;
7. later conducts public review.

The emergency process does not make one vendor’s replacement service mandatory.

---

## 121. Reference implementation divergence

The reference server accepts a record form prohibited by the specification.

Several other implementations reject it.

Governance determines that the reference implementation is incorrect.

The server is fixed.

The specification is not silently changed to match the dominant codebase.

---

## 122. Governance capture attempt

A consortium of major Providers attempts to alter migration requirements so that only file export remains mandatory.

The proposed change would reduce operational portability.

The Constitutional Council identifies the proposal as violating the Continuity Principle.

Ordinary commercial voting cannot approve it.

---

## 123. Stewardship failure

The existing Stewardship Body becomes inactive and stops publishing security updates.

Under the governance replacement procedure:

- archives are transferred;
- keys are rotated;
- reserved namespace records are preserved;
- a successor body is recognised through the required multi-stakeholder process;
- specifications and identifiers remain unchanged.

Relay continues without creating a new protocol identity.

---

# Part XXII — Non-Compliant Governance Examples

## 124. Vendor-defined standard

One Provider modifies its implementation and announces that the new behaviour is now Relay-compliant without a specification change.

This is not valid protocol governance.

---

## 125. Test-suite legislation

A test maintainer adds new normative requirements to the conformance suite without corresponding specification approval.

This is not valid conformance governance.

---

## 126. Paid namespace control

A governance body requires every third-party schema to pay for approval before it can be used.

This violates open extension principles.

---

## 127. Hidden security mandate

A security committee secretly makes a permanent architectural change after the immediate vulnerability has passed.

This exceeds emergency authority.

---

## 128. Commercial constitutional amendment

Major Providers vote to remove mandatory migration because migration harms retention.

This violates Relay’s constitutional purpose.

---

## 129. Governance permanence

The Stewardship Body asserts that it can never be replaced, even if it ceases functioning.

This contradicts Governance by Replacement.

---

# Part XXIII — Open Design Questions

## 130. Stewardship structure

Should Relay initially be stewarded by:

- a foundation;
- an informal technical group;
- an existing standards body;
- a new consortium;
- a staged transition between these?

---

## 131. Constitutional enforcement

Which body has final authority to determine that a proposal violates the Continuity Principle?

---

## 132. Constitutional amendment threshold

What exact process, if any, should permit amendment of foundational principles?

---

## 133. Representation

How should governance balance:

- users;
- implementers;
- Providers;
- Applications;
- public-interest groups;
- security experts;
- funders?

---

## 134. Voting model

Should voting be:

- individual;
- organisational;
- constituency-based;
- contribution-based;
- consensus-first with fallback voting?

---

## 135. Reserved namespace

Which concepts belong in Relay’s core namespace at v0.1?

---

## 136. Proposal naming

Should the change process use:

- Relay Improvement Proposal;
- Relay Request for Comments;
- another naming model?

---

## 137. Reference implementation ownership

Who should maintain the reference implementation, and how should that team remain independent from specification authority?

---

## 138. Certification recognition

How should governance recognise independent certification bodies without creating a closed accreditation cartel?

---

## 139. Funding

How should Relay governance be sustainably funded without becoming dependent on one dominant Provider?

---

## 140. Governance keys

How should signing authority for:

- official specifications;
- schema releases;
- test suites;
- security advisories;

be distributed and recovered?

---

## 141. Stewardship succession

What precise evidence determines the legitimate successor if governance splits?

---

## 142. Patent policy

Which legal framework best protects royalty-free independent implementation?

---

# Part XXIV — Provisional Decisions for v0.1

## 143. Provisional governance decisions

Relay v0.1 will provisionally assume:

- governance is stewardship rather than ownership;
- the Continuity Principle is Relay’s primary constitutional rule;
- constitutional principles are separated from replaceable technical mechanisms;
- substantial changes use a public proposal process;
- change categories have different review thresholds;
- major features require implementation evidence;
- the official specification remains authoritative over implementations;
- reference implementations do not define protocol behaviour by popularity;
- core schemas remain deliberately limited;
- third-party schemas do not require central approval;
- conformance tests remain open and linked to normative requirements;
- conflicts of interest and major funding sources are disclosed;
- emergency security processes are limited and later reviewed;
- historical specifications, schemas and decisions remain publicly archived;
- implementation remains open to commercial and non-commercial parties;
- no single Provider, Application or certification body is mandatory;
- the Stewardship Body must itself remain replaceable;
- the exact legal institution, voting system and constitutional amendment process remain unresolved;
- Relay v0.1 may begin under lightweight interim stewardship before transitioning to a formal independent structure.

---

## 144. Core governance principle

The Governance and Evolution Model can be reduced to one rule:

> Relay exists to preserve the individual’s enduring authority over digital identity, records, relationships and continuity; its stewards may evolve the technology, but they may not turn stewardship of the protocol into ownership of the people who use it.

With this section, the first complete set of Relay Protocol v0.1 core objects is defined. The next stage should consolidate the fifteen working drafts into one coherent specification, remove duplication and identify the unresolved decisions that must be settled before a reference implementation can begin.