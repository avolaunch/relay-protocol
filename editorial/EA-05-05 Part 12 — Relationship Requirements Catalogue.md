# EA-05-05 — Relationship Requirements Catalogue

## Part 12 — Relationship Requests and Acceptance

**Editorial Programme:** EA-05 — Normative Requirements Audit  
**Subsystem:** Relationship  
**Status:** Founder Review Draft

---

# 1. Purpose

This part defines the protocol requirements governing consent-based relationship requests, target responses, acceptance records and schema-defined relationship activation.

It continues the canonical Relationship Requirements Catalogue from `REL-REL-220`, following Part 11's coverage of personal groups, formal groups and membership. This part is generated from the completed and verified REM-05 extraction series. The authoritative design source remains `design-notes/05-relationship-model.md`.

---

# 2. Scope

This part covers source Sections 29–30 and REM-05 requirements `REM-05-321` through `REM-05-342`.

It defines normative requirements governing:

- request-based initiation of consent-requiring relationships;
- relationship-request identity, type, context, role, expiration, visibility and evidence content;
- target acceptance, decline, ignore, counter-proposal and future-request blocking options;
- the non-active status of a request before activation;
- independently authorised acceptance records;
- request-to-acceptance traceability;
- schema-defined activation conditions;
- mutual-friendship dual-record activation;
- organisation-membership approval, acceptance and credential conditions.

Section 31 relationship termination and later requirements are intentionally deferred to subsequent catalogue parts.

---

# 3. Requirements

---

## REL-REL-220

### Title

Request-Based Initiation for Consent-Requiring Relationships

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A relationship requiring consent **MUST** begin with a request record or protocol message.

### Rationale

Consent must be preceded by an identifiable proposal rather than inferred from unilateral relationship creation. The request establishes the object to which the target may respond without itself establishing the relationship.

### Source

- REM-05-321
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-221

### Title

Relationship Request Participant Identification

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify both the requesting identity and the target identity.

### Rationale

A consent request must be attributable to its proposer and addressed to the identity whose consent is sought. Both dimensions are parts of the same request-participant structure and share the source's recommended strength.

### Source

- REM-05-322
- REM-05-323
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-222

### Title

Relationship Request Type

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify the proposed relationship type.

### Rationale

The target must be able to determine the relationship semantics being proposed before deciding whether to accept them.

### Source

- REM-05-324
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-12

---

## REL-REL-223

### Title

Relationship Request Context

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify the context in which the proposed relationship would apply.

### Rationale

Where relationship meaning is context-specific, the target's consent must relate to that bounded context rather than being silently broadened into a global relationship.

### Source

- REM-05-325
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-12

---

## REL-REL-224

### Title

Relationship Request Role

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify any role being requested.

### Rationale

A proposed role is part of the relationship semantics to which the target may consent and must remain distinguishable from any separate authority that role may convey.

### Source

- REM-05-326
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-06
- CI-12

---

## REL-REL-225

### Title

Relationship Request Expiration

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify its expiration or the proposed relationship's relevant expiration condition.

### Rationale

Temporal bounds prevent stale proposals from remaining indefinitely actionable and allow the target to understand any time limitation attached to the proposed relationship.

### Source

- REM-05-327
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- AI-09

---

## REL-REL-226

### Title

Relationship Request Visibility Proposal

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** identify the proposed visibility of the resulting relationship.

### Rationale

Consent to a relationship type must not silently become consent to an undisclosed public or otherwise broader visibility state.

### Source

- REM-05-328
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-227

### Title

Relationship Request Supporting Evidence

**Level:** Behavioural

**Normative Keyword:** **SHOULD**

### Statement

A relationship request **SHOULD** include or reference supporting evidence where relevant.

### Rationale

Evidence may be required by the applicable relationship schema or may provide information necessary for the target to evaluate the proposal.

### Source

- REM-05-329
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-10

---

## REL-REL-228

### Title

Relationship Request Response Options

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

The target of a relationship request **MAY** accept, decline or ignore the request; issue a counter-proposal; or block future relationship requests from the requesting identity or for the applicable request category.

### Rationale

Section 29 defines these as alternative response options available to the target. They express one target-control capability while preserving non-response, rejection, negotiation and future-request control as distinct outcomes rather than forms of consent.

### Source

- REM-05-330
- REM-05-331
- REM-05-332
- REM-05-333
- REM-05-334
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-229

### Title

Relationship Request Is Not Active Reciprocal Relationship

**Level:** Constitutional

**Normative Keyword:** **MUST NOT**

### Statement

A relationship request **MUST NOT** be treated or presented as an active reciprocal relationship.

### Rationale

A request records the requester's proposal but does not establish the target's independent declaration or approval. Treating the request as active would manufacture reciprocal consent.

### Source

- REM-05-335
- `design-notes/05-relationship-model.md`, Section 29

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-230

### Title

Independent Acceptance Record

**Level:** Architectural

**Normative Keyword:** **SHOULD**

### Statement

Acceptance of a consent-based relationship **SHOULD** create an independently authorised record in the accepting identity's repository.

### Rationale

The accepting identity's record establishes that identity's own declaration. Keeping it independently authorised prevents the requester from controlling or rewriting the target's consent record.

### Source

- REM-05-336
- `design-notes/05-relationship-model.md`, Section 30

### Related Invariants

- CI-02
- CI-08
- CI-10

---

## REL-REL-231

### Title

Acceptance-to-Proposal Reference

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An acceptance record **MAY** reference the original relationship proposal.

### Rationale

A reference preserves lifecycle traceability between proposal and acceptance while leaving the two records independently authorised and controlled.

### Source

- REM-05-337
- `design-notes/05-relationship-model.md`, Section 30

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-232

### Title

Schema-Governed Relationship Activation

**Level:** Constitutional

**Normative Keyword:** **MUST**

### Statement

A consent-based relationship **MUST** become active only after all activation conditions defined by its schema have been satisfied.

### Rationale

Acceptance alone may not be sufficient where a relationship schema also requires matching records, credentials, organisational approvals or other conditions. Activation therefore follows the schema rather than a generic acceptance event.

### Source

- REM-05-338
- `design-notes/05-relationship-model.md`, Section 30

### Related Invariants

- CI-10
- CI-12

---

## REL-REL-233

### Title

Mutual-Friendship Dual-Record Activation

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

A mutual-friendship schema **MAY** require two independently authorised active relationship records before the friendship is considered active.

### Rationale

A mutual friendship may require an active declaration from each participant. Each identity retains control of its own record rather than relying on one party's record to manufacture reciprocity.

### Source

- REM-05-339
- `design-notes/05-relationship-model.md`, Section 30

### Related Invariants

- CI-02
- CI-10

---

## REL-REL-234

### Title

Organisation-Membership Activation Conditions

**Level:** Behavioural

**Normative Keyword:** **MAY**

### Statement

An organisation-membership schema **MAY** require organisation approval, prospective-member acceptance, a valid membership credential, or an applicable combination of those conditions before membership becomes active.

### Rationale

Section 30 presents these as possible organisation-membership activation conditions. They remain schema-selected options rather than universal requirements, while the general rule that all selected activation conditions must be satisfied remains mandatory under `REL-REL-232`.

### Source

- REM-05-340
- REM-05-341
- REM-05-342
- `design-notes/05-relationship-model.md`, Section 30

### Related Invariants

- CI-02
- CI-10
- CI-12

---

# 4. Consolidation and Traceability Record

This part consolidates only requirements that express one source-defined structural pair or option set:

- `REM-05-322` and `REM-05-323` are consolidated into `REL-REL-221`. Requesting identity and target identity are the two participant identifiers of the same request structure and share the source's `SHOULD` strength.
- `REM-05-330` through `REM-05-334` are consolidated into `REL-REL-228`. Accept, decline, ignore, counter-propose and block future requests are the source-defined target response options and share `MAY` strength. The consolidation does not imply semantic equivalence among the outcomes.
- `REM-05-340` through `REM-05-342` are consolidated into `REL-REL-234`. Organisation approval, member acceptance and valid membership credential are the source-listed optional activation conditions for organisation membership.

No other REM-05 entries in the covered range are consolidated. Relationship type, context, requested role, expiration, visibility and supporting evidence remain separate request fields because each communicates independently meaningful information. The request's non-active status remains separate from response options. Acceptance-record creation, proposal linkage, schema-governed activation and mutual-friendship dual-record semantics remain independently meaningful lifecycle requirements.

All REM-05 requirements from `REM-05-321` through `REM-05-342` are represented exactly once in the catalogue mapping, either independently or through the three explicit consolidations above.

No non-normative REM entries occur within this part's covered range.

---

# 5. Editorial QA Record

## Scope verification

- Part 12 begins at `REM-05-321`, immediately after Part 11's final covered requirement `REM-05-320`.
- Coverage ends at `REM-05-342`, the end of source Section 30.
- Section 31 and later requirements are excluded from this part.
- The authoritative source was checked directly for Sections 29–30.

## Numbering verification

- First catalogue requirement: `REL-REL-220`.
- Final catalogue requirement: `REL-REL-234`.
- Catalogue numbering continues directly from Part 11's `REL-REL-219`.
- Catalogue identifiers in this part are continuous and unique.

## Traceability verification

- Every covered REM-05 identifier maps to a catalogue requirement.
- Consolidated requirements retain all contributing REM-05 identifiers.
- Normative strength is preserved from the verified extraction.
- Request-based initiation remains `MUST` for consent-requiring relationships.
- Request content fields retain `SHOULD` strength.
- Target response options retain `MAY` strength and are not interpreted as equivalent consent outcomes.
- A request remains explicitly non-active under `MUST NOT` semantics.
- Independent acceptance-record creation retains `SHOULD` strength.
- Proposal referencing remains `MAY`.
- Schema-defined activation remains `MUST`.
- Mutual-friendship and organisation-membership activation examples remain `MAY` schema options.

## Status-boundary verification

The special remediation statuses identified by `REM-05R-02` do not occur within this part's range. Previously encountered `REM-05-291` through `REM-05-295` remain explicitly non-normative and generated no catalogue identifiers. The remaining catalogue rules remain binding for later parts:

- `REM-05-636` through `REM-05-645` must remain unresolved and non-normative;
- `REM-05-646` through `REM-05-671` must retain explicit **PROVISIONAL v0.1** status;
- `REM-05-673` must remain a non-normative model-boundary note.

---

# Editorial Review Notes

This part preserves consent as an independently authorised lifecycle rather than a side effect of one party's declaration. A request establishes a proposal, not a reciprocal relationship; the target controls its response; acceptance should produce the accepting identity's own record; and active relationship state remains contingent on the applicable schema's activation conditions. This structure permits simple consent flows while also supporting relationships that require reciprocal records, organisational approval or credential evidence.

The next catalogue part should begin with `REM-05-343` / source Section 31 and continue catalogue numbering from `REL-REL-235`.