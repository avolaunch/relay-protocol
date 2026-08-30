# REM-05 Part 5 — Relationship Requirement Extraction Matrix (Sections 21–25)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 21–25 of `design-notes/05-relationship-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

21. Relationship validity period
22. Relationship evidence
23. Claimed versus verified relationships
24. Authority-bearing relationships
25. Groups

Requirement identifiers continue sequentially from Part 4, beginning with `REM-05-210`.

---

# 21. Relationship validity period

## REM-05-210 — Relationship start time

**Source**  
Section 21: “A relationship may define: start time”.

**Requirement**  
A relationship schema or record MAY define the time from which the relationship begins.

**Classification**  
Temporal scope; relationship lifecycle.

**Notes**  
The start time may differ from the record creation time where the relationship becomes effective later or records an earlier effective date.

---

## REM-05-211 — Relationship end time

**Source**  
Section 21: “A relationship may define: end time”.

**Requirement**  
A relationship schema or record MAY define the time at which the relationship ends.

**Classification**  
Temporal scope; relationship lifecycle.

**Notes**  
An explicit end time enables applications to distinguish current from historical relationships.

---

## REM-05-212 — Relationship expiration

**Source**  
Section 21: “A relationship may define: expiration”.

**Requirement**  
A relationship MAY include an expiration condition or expiration time.

**Classification**  
Expiration; lifecycle automation.

**Notes**  
Expiration ends current effects without necessarily erasing the historical record.

---

## REM-05-213 — Relationship renewal

**Source**  
Section 21: “A relationship may define: renewal”.

**Requirement**  
A relationship schema MAY define whether and how an expiring or expired relationship can be renewed.

**Classification**  
Renewal; lifecycle; schema behaviour.

**Notes**  
Renewal rules may require fresh approval, evidence or issuance depending on the relationship type.

---

## REM-05-214 — Relationship effective date

**Source**  
Section 21: “A relationship may define: effective date”.

**Requirement**  
A relationship MAY declare the date or time at which its declared effects become effective.

**Classification**  
Temporal semantics; effective state.

**Notes**  
The effective date may be relevant to employment, membership, representation or other formally dated relationships.

---

## REM-05-215 — Machine-readable validity bounds

**Source**  
Section 21 example using `validFrom` and `validUntil` timestamps.

**Requirement**  
Where a relationship declares validity bounds, those bounds SHOULD be represented in a machine-readable form.

**Classification**  
Temporal interoperability; data representation.

**Notes**  
The source example uses timestamps but does not establish a final field naming or serialization rule.

---

## REM-05-216 — Expired relationships may remain verifiable

**Source**  
Section 21: “An expired relationship may remain historically verifiable...”

**Requirement**  
An expired relationship MAY remain historically verifiable after it ceases to be current.

**Classification**  
Historical integrity; expiration semantics.

**Notes**  
Expiration does not inherently require deletion or destruction of provenance.

---

## REM-05-217 — Expired relationships cease current authority

**Source**  
Section 21: an expired relationship may remain historical “while no longer producing current authority or access.”

**Requirement**  
An expired relationship MUST NOT continue to produce current authority solely on the basis of its former active state.

**Classification**  
Authority termination; expiration; access control.

**Notes**  
A renewed or replacement relationship may establish new authority, but the expired relationship itself no longer does so.

---

## REM-05-218 — Expired relationships cease current access effects

**Source**  
Section 21: an expired relationship may remain historical “while no longer producing current authority or access.”

**Requirement**  
An expired relationship MUST NOT continue to grant current access solely because it remains historically verifiable.

**Classification**  
Access control; expiration; historical separation.

**Notes**  
Historical visibility and current access authority are distinct concerns.

---

# 22. Relationship evidence

## REM-05-219 — Self-declared relationship support

**Source**  
Section 22: “Some relationships are self-declared.”

**Requirement**  
The Relationship Model MUST support relationships that are declared solely by the source identity where the schema permits self-declaration.

**Classification**  
Evidence model; self-assertion.

**Notes**  
Self-declaration does not establish independent verification.

---

## REM-05-220 — Evidence-required relationship support

**Source**  
Section 22: “Others require evidence.”

**Requirement**  
The Relationship Model MUST support relationship types whose validity or status depends on evidence.

**Classification**  
Evidence model; validation.

**Notes**  
The applicable schema determines whether evidence is optional or required.

---

## REM-05-221 — Employment evidence capability

**Source**  
Section 22 lists employment as an example requiring evidence.

**Requirement**  
A relationship schema MAY require evidence for an employment relationship.

**Classification**  
Employment; evidence; schema behaviour.

**Notes**  
The example does not require all employment claims to use one specific evidence mechanism.

---

## REM-05-222 — Professional-membership evidence capability

**Source**  
Section 22 lists professional membership.

**Requirement**  
A relationship schema MAY require evidence for a professional-membership relationship.

**Classification**  
Membership; evidence; schema behaviour.

**Notes**  
Evidence can distinguish an informal claim from an issuer-recognised membership.

---

## REM-05-223 — Legal-representation evidence capability

**Source**  
Section 22 lists legal representation.

**Requirement**  
A relationship schema MAY require evidence for a legal-representation relationship.

**Classification**  
Legal authority; evidence; schema behaviour.

**Notes**  
Because legal representation may convey authority, stronger validation may also be required under Section 24.

---

## REM-05-224 — Guardianship evidence capability

**Source**  
Section 22 lists guardianship.

**Requirement**  
A relationship schema MAY require evidence for a guardianship relationship.

**Classification**  
Guardianship; evidence; authority.

**Notes**  
The evidence must be appropriate to the relationship’s legal and jurisdictional context.

---

## REM-05-225 — Directorship evidence capability

**Source**  
Section 22 lists company directorship.

**Requirement**  
A relationship schema MAY require evidence for a company-directorship relationship.

**Classification**  
Organisational role; evidence.

**Notes**  
Registry or organisation-issued evidence may be relevant.

---

## REM-05-226 — Ownership evidence capability

**Source**  
Section 22 lists ownership.

**Requirement**  
A relationship schema MAY require evidence for an ownership relationship.

**Classification**  
Ownership; evidence; provenance.

**Notes**  
The evidentiary standard may vary according to the object being owned.

---

## REM-05-227 — Academic-affiliation evidence capability

**Source**  
Section 22 lists academic affiliation.

**Requirement**  
A relationship schema MAY require evidence for an academic-affiliation relationship.

**Classification**  
Affiliation; evidence.

**Notes**  
Issuer attestations or credentials may be appropriate evidence sources.

---

## REM-05-228 — Verifiable Credential evidence

**Source**  
Section 22: “Evidence may include: a Verifiable Credential”.

**Requirement**  
A relationship MAY reference or rely on a Verifiable Credential as evidence.

**Classification**  
Credential evidence; interoperability.

**Notes**  
The credential’s own validity, issuer and revocation state remain relevant.

---

## REM-05-229 — Reciprocal signed relationship evidence

**Source**  
Section 22: “Evidence may include: a reciprocal signed relationship”.

**Requirement**  
A relationship MAY use an independently authorised reciprocal relationship record as evidence.

**Classification**  
Reciprocity; signed evidence.

**Notes**  
Each party’s record remains under that party’s independent control.

---

## REM-05-230 — Organisation-issued assertion evidence

**Source**  
Section 22: “Evidence may include: an organisation-issued assertion”.

**Requirement**  
A relationship MAY rely on an assertion issued by a relevant organisation as evidence.

**Classification**  
Issuer attestation; organisational evidence.

**Notes**  
Applications should assess the assertion’s issuer, scope and validity.

---

## REM-05-231 — Registry-reference evidence

**Source**  
Section 22: “Evidence may include: a recognised registry reference”.

**Requirement**  
A relationship MAY reference a recognised registry as evidence.

**Classification**  
Registry evidence; external verification.

**Notes**  
The record should identify the registry and enough information to verify the referenced entry.

---

## REM-05-232 — Legal-document evidence

**Source**  
Section 22: “Evidence may include: a legal document”.

**Requirement**  
A relationship MAY rely on a legal document as evidence.

**Classification**  
Legal evidence; document provenance.

**Notes**  
Access to the document may require restricted visibility because of sensitivity.

---

## REM-05-233 — Application-specific attestation evidence

**Source**  
Section 22: “Evidence may include: an application-specific attestation”.

**Requirement**  
A relationship MAY rely on an application-specific attestation as evidence where the schema permits it.

**Classification**  
Application attestation; evidence quality.

**Notes**  
An application-specific attestation must not automatically be treated as equivalent to an independent credential or registry verification.

---

## REM-05-234 — Evidence-status declaration

**Source**  
Section 22: “The relationship record should indicate whether it is...” followed by evidence-status values.

**Requirement**  
A relationship record SHOULD declare the evidentiary status of the relationship.

**Classification**  
Evidence transparency; metadata.

**Notes**  
This enables applications to present claims according to their actual evidentiary weight.

---

## REM-05-235 — Self-declared status

**Source**  
Section 22 evidence-status vocabulary: `self-declared`.

**Requirement**  
The evidence-status model SHOULD support a `self-declared` classification.

**Classification**  
Evidence vocabulary; self-assertion.

**Notes**  
This classification indicates that the claim originates from the declaring party without independent confirmation.

---

## REM-05-236 — Reciprocally confirmed status

**Source**  
Section 22 evidence-status vocabulary: `reciprocally confirmed`.

**Requirement**  
The evidence-status model SHOULD support a `reciprocally confirmed` classification.

**Classification**  
Evidence vocabulary; reciprocity.

**Notes**  
This indicates independent confirmation by another participating identity.

---

## REM-05-237 — Issuer-attested status

**Source**  
Section 22 evidence-status vocabulary: `issuer-attested`.

**Requirement**  
The evidence-status model SHOULD support an `issuer-attested` classification.

**Classification**  
Evidence vocabulary; issuer attestation.

**Notes**  
The issuer must be identifiable for the status to be meaningful.

---

## REM-05-238 — Credential-backed status

**Source**  
Section 22 evidence-status vocabulary: `credential-backed`.

**Requirement**  
The evidence-status model SHOULD support a `credential-backed` classification.

**Classification**  
Evidence vocabulary; credentials.

**Notes**  
The backing credential may itself expire or be revoked.

---

## REM-05-239 — Externally verified status

**Source**  
Section 22 evidence-status vocabulary: `externally verified`.

**Requirement**  
The evidence-status model SHOULD support an `externally verified` classification.

**Classification**  
Evidence vocabulary; external verification.

**Notes**  
The verification source and method should be recorded under Section 23.

---

## REM-05-240 — Disputed evidence status

**Source**  
Section 22 evidence-status vocabulary: `disputed`.

**Requirement**  
The evidence-status model SHOULD support a `disputed` classification.

**Classification**  
Evidence vocabulary; dispute state.

**Notes**  
Disputed status must not be represented as verified or uncontested.

---

# 23. Claimed versus verified relationships

## REM-05-241 — Claimed and verified relationship distinction

**Source**  
Section 23: “Relay must distinguish between” a self-claim and a signed employment credential.

**Requirement**  
Relay implementations MUST distinguish a relationship claimed by a party from a relationship supported by independent verification or issuer evidence.

**Classification**  
Evidence distinction; semantic integrity.

**Notes**  
The distinction must remain visible in storage, validation and presentation.

---

## REM-05-242 — Coexistence of claim and verification records

**Source**  
Section 23: “Both may exist as records...”

**Requirement**  
A self-declared relationship record and a separately verified or credential-backed relationship record MAY coexist.

**Classification**  
Record coexistence; evidence layering.

**Notes**  
One record need not overwrite or erase the other.

---

## REM-05-243 — Different evidentiary weight

**Source**  
Section 23: “...but they carry different evidentiary weight.”

**Requirement**  
Applications MUST treat self-declared and independently verified relationship records as carrying different evidentiary weight.

**Classification**  
Evidence evaluation; presentation integrity.

**Notes**  
The protocol does not prescribe one universal ranking for every evidence source, but it requires the difference to be preserved.

---

## REM-05-244 — No false verification label

**Source**  
Section 23: “Applications should not describe a self-declared relationship as verified.”

**Requirement**  
An application SHOULD NOT describe a self-declared relationship as verified.

**Classification**  
User-interface integrity; evidence representation.

**Notes**  
A relationship can be validly recorded as a claim without being independently verified.

---

## REM-05-245 — Verification identifies verifier

**Source**  
Section 23: “Verification should identify: verifier”.

**Requirement**  
Verification metadata SHOULD identify the verifier.

**Classification**  
Verification provenance; accountability.

**Notes**  
The verifier may be an organisation, registry, credential issuer, application or other recognised authority.

---

## REM-05-246 — Verification identifies method

**Source**  
Section 23: “Verification should identify: method”.

**Requirement**  
Verification metadata SHOULD identify the method used to verify the relationship.

**Classification**  
Verification provenance; method transparency.

**Notes**  
Method disclosure enables relying applications to assess evidentiary strength.

---

## REM-05-247 — Verification identifies date

**Source**  
Section 23: “Verification should identify: date”.

**Requirement**  
Verification metadata SHOULD identify when verification occurred.

**Classification**  
Verification timing; freshness.

**Notes**  
The verification date is distinct from the relationship’s effective or creation date.

---

## REM-05-248 — Verification identifies scope

**Source**  
Section 23: “Verification should identify: scope”.

**Requirement**  
Verification metadata SHOULD identify what aspect or scope of the relationship was verified.

**Classification**  
Verification scope; semantic precision.

**Notes**  
Verification of identity, role, dates or authority may represent different scopes.

---

## REM-05-249 — Verification identifies expiration

**Source**  
Section 23: “Verification should identify: expiration”.

**Requirement**  
Verification metadata SHOULD identify any expiration applicable to the verification.

**Classification**  
Verification lifecycle; expiration.

**Notes**  
A relationship may continue to exist as a claim after its verification expires, but must not continue to be represented as currently verified without renewed evidence.

---

## REM-05-250 — Verification identifies revocation status

**Source**  
Section 23: “Verification should identify: revocation status”.

**Requirement**  
Verification metadata SHOULD identify whether the supporting verification or evidence has been revoked.

**Classification**  
Verification lifecycle; revocation.

**Notes**  
Applications must not rely on revoked evidence as though it remained current.

---

# 24. Authority-bearing relationships

## REM-05-251 — Authority-bearing relationship support

**Source**  
Section 24: “Some relationships grant the source or target authority.”

**Requirement**  
The Relationship Model MUST support relationship types that convey explicitly defined authority to a source or target.

**Classification**  
Delegated authority; relationship semantics.

**Notes**  
Authority-bearing relationships require stricter validation than ordinary descriptive or social relationships.

---

## REM-05-252 — Administrator authority relationship

**Source**  
Section 24 example: “administrator of an organisation”.

**Requirement**  
A relationship schema MAY represent an administrator role that conveys defined authority within an organisation.

**Classification**  
Organisational authority; administration.

**Notes**  
The label alone is insufficient; the exact capabilities and scope must be specified.

---

## REM-05-253 — Legal-representative authority relationship

**Source**  
Section 24 example: “legal representative”.

**Requirement**  
A relationship schema MAY represent legal-representation authority.

**Classification**  
Legal authority; representation.

**Notes**  
Appropriate evidence and jurisdictional limitations may apply.

---

## REM-05-254 — Guardian authority relationship

**Source**  
Section 24 example: “guardian”.

**Requirement**  
A relationship schema MAY represent guardianship authority.

**Classification**  
Guardianship; delegated authority.

**Notes**  
The authority scope must not be inferred beyond what the record and evidence establish.

---

## REM-05-255 — Application-operator authority relationship

**Source**  
Section 24 example: “application operator”.

**Requirement**  
A relationship schema MAY represent an application-operator role with defined authority.

**Classification**  
Application governance; operational authority.

**Notes**  
This relationship does not replace application Permission Grants where those are also required.

---

## REM-05-256 — Delegated-publisher authority relationship

**Source**  
Section 24 example: “delegated publisher”.

**Requirement**  
A relationship schema MAY represent delegated publication authority.

**Classification**  
Publishing authority; delegation.

**Notes**  
The grant should specify which records, collections or contexts may be published.

---

## REM-05-257 — Repository-custodian authority relationship

**Source**  
Section 24 example: “repository custodian”.

**Requirement**  
A relationship schema MAY represent repository-custodian authority.

**Classification**  
Repository governance; custody.

**Notes**  
Custodial authority must remain distinct from ownership of the Relay Identity or its records.

---

## REM-05-258 — Exact capabilities required

**Source**  
Section 24: “Such relationships must specify: exact capabilities”.

**Requirement**  
An authority-bearing relationship MUST specify the exact capabilities it conveys.

**Classification**  
Capability definition; least privilege.

**Notes**  
Broad role names must not substitute for an explicit capability set.

---

## REM-05-259 — Authority scope required

**Source**  
Section 24: “Such relationships must specify: scope”.

**Requirement**  
An authority-bearing relationship MUST specify the scope within which its capabilities apply.

**Classification**  
Authority scope; least privilege.

**Notes**  
Scope may be limited by organisation, repository, collection, record, context or another defined boundary.

---

## REM-05-260 — Authority duration required

**Source**  
Section 24: “Such relationships must specify: duration”.

**Requirement**  
An authority-bearing relationship MUST specify its duration or continuing-validity condition.

**Classification**  
Authority lifecycle; temporal limitation.

**Notes**  
An indefinite duration must still remain revocable where the schema requires revocation.

---

## REM-05-261 — Approval requirements required

**Source**  
Section 24: “Such relationships must specify: approval requirements”.

**Requirement**  
An authority-bearing relationship MUST specify the approvals required for creation, activation or continuation.

**Classification**  
Authority approval; governance.

**Notes**  
Approval may involve one or multiple identities, organisations or external authorities.

---

## REM-05-262 — Revocation mechanism required

**Source**  
Section 24: “Such relationships must specify: revocation mechanism”.

**Requirement**  
An authority-bearing relationship MUST specify how the conveyed authority can be revoked.

**Classification**  
Revocation; authority lifecycle.

**Notes**  
The mechanism should identify who may revoke and how revocation becomes effective.

---

## REM-05-263 — Authority evidence required

**Source**  
Section 24: “Such relationships must specify: evidence”.

**Requirement**  
An authority-bearing relationship MUST specify or reference the evidence supporting the authority.

**Classification**  
Authority evidence; validation.

**Notes**  
Evidence requirements should be proportionate to the risk and legal significance of the authority.

---

## REM-05-264 — Re-delegation rule required

**Source**  
Section 24: “Such relationships must specify... whether authority may be re-delegated.”

**Requirement**  
An authority-bearing relationship MUST specify whether the granted authority may be delegated onward.

**Classification**  
Re-delegation; authority control.

**Notes**  
Silence must not be interpreted as permission to re-delegate.

---

## REM-05-265 — Generic labels do not confer broad authority

**Source**  
Section 24: “A generic relationship label must not silently confer broad authority.”

**Requirement**  
A generic relationship label MUST NOT, by itself, confer authority beyond the explicit capabilities and scope defined by the relationship record and schema.

**Classification**  
Privilege limitation; semantic safety.

**Notes**  
For example, `administrator` must not be treated as unrestricted authority without explicit capability definition.

---

# 25. Groups

## REM-05-266 — Relay Group definition

**Source**  
Section 25: “A Relay Group is a defined set of identities used for relationships, access or communication.”

**Requirement**  
A Relay Group MUST represent a defined set of identities used for one or more relationship, access or communication purposes.

**Classification**  
Group model; identity sets.

**Notes**  
A group is not necessarily a formal organisation or mutually recognised entity.

---

## REM-05-267 — Group use for relationships

**Source**  
Section 25 definition includes groups “used for relationships”.

**Requirement**  
A Relay Group MAY be used as a relationship context, source, target or organisational set where the applicable schema permits it.

**Classification**  
Group relationships; schema behaviour.

**Notes**  
The precise relationship semantics remain schema-defined.

---

## REM-05-268 — Group use for access

**Source**  
Section 25 definition includes groups “used for... access”.

**Requirement**  
A Relay Group MAY be used to define an access audience or access-control set.

**Classification**  
Group access control; audience management.

**Notes**  
Group membership visibility and authority must be handled according to the group type and policy.

---

## REM-05-269 — Group use for communication

**Source**  
Section 25 definition includes groups “used for... communication”.

**Requirement**  
A Relay Group MAY be used to define participants or audiences for communication.

**Classification**  
Group communication; audience management.

**Notes**  
The group representation does not itself guarantee a particular messaging or delivery service.

---

## REM-05-270 — Group-record representation

**Source**  
Section 25: “A group may be represented by: a group record”.

**Requirement**  
A Relay Group MAY be represented by a dedicated group record.

**Classification**  
Group representation; records.

**Notes**  
The group record may define metadata, governance, membership rules or other group-level information.

---

## REM-05-271 — Membership-record representation

**Source**  
Section 25: “A group may be represented by: membership relationship records”.

**Requirement**  
A Relay Group MAY be represented through membership relationship records.

**Classification**  
Group representation; membership graph.

**Notes**  
Membership records can preserve independent authority and provenance for individual memberships.

---

## REM-05-272 — Group-controlled identity representation

**Source**  
Section 25: “A group may be represented by: a group-controlled Relay Identity”.

**Requirement**  
A Relay Group MAY be represented by or associated with a Relay Identity controlled according to the group’s governance rules.

**Classification**  
Group identity; governance.

**Notes**  
Control of the group identity must be distinguished from personal ownership by one member unless the group is intentionally personal.

---

## REM-05-273 — Private-access-list representation

**Source**  
Section 25: “A group may be represented by: a private access list”.

**Requirement**  
A Relay Group MAY be represented as a private access list.

**Classification**  
Private groups; access control.

**Notes**  
The existence, label or membership of a private access list need not be disclosed to its members or the public.

---

## REM-05-274 — Group-type distinction required

**Source**  
Section 25: “The group model must distinguish between...”

**Requirement**  
The Relay Group model MUST distinguish materially different group types rather than treating all identity sets as equivalent.

**Classification**  
Group taxonomy; semantic interoperability.

**Notes**  
The required distinctions are extracted separately below.

---

## REM-05-275 — Personal organisational list distinction

**Source**  
Section 25 group distinction: “a personal organisational list”.

**Requirement**  
The group model MUST distinguish a personal organisational list controlled by one identity.

**Classification**  
Personal groups; private organisation.

**Notes**  
Membership in such a list does not imply acceptance of a public group relationship by listed identities.

---

## REM-05-276 — Mutually recognised group distinction

**Source**  
Section 25 group distinction: “a mutually recognised group”.

**Requirement**  
The group model MUST distinguish a group whose participating identities mutually recognise the group or their membership.

**Classification**  
Mutual groups; membership recognition.

**Notes**  
Mutual recognition requires appropriate independent authorisation or evidence.

---

## REM-05-277 — Formal organisation distinction

**Source**  
Section 25 group distinction: “a formal organisation”.

**Requirement**  
The group model MUST distinguish a formal organisation from an informal or personal grouping.

**Classification**  
Organisation model; governance.

**Notes**  
Formal organisations may have their own identity, governance, authority and evidence requirements.

---

## REM-05-278 — Application-generated audience segment distinction

**Source**  
Section 25 group distinction: “an application-generated audience segment”.

**Requirement**  
The group model MUST distinguish an application-generated audience segment from a user-controlled or mutually recognised group.

**Classification**  
Derived audience; application processing; group taxonomy.

**Notes**  
An application-generated segment must not be presented as though its members joined or recognised a formal group.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 21–25 of `design-notes/05-relationship-model.md`.
- Section 26 and later content was excluded.
- Examples were used to clarify source meaning and were not promoted into mandatory final syntax.

## Numbering verification

- First requirement: `REM-05-210`.
- Final requirement: `REM-05-278`.
- Requirement numbering continues directly from Part 4.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Compound source lists were decomposed into independently testable requirements where appropriate.
- Evidence types, verification metadata fields, authority constraints and group distinctions were extracted separately to preserve traceability.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations.
- Source “may” statements are preserved as `MAY` permissions.
- Descriptive definitions were converted into normative language only where required to make the model testable without strengthening optional source language.

## Editorial verification

- Expiration remains distinct from historical deletion.
- Self-declared claims remain distinct from independently verified relationships.
- Verification metadata remains distinct from the underlying relationship claim.
- Authority-bearing labels do not confer unspecified privileges.
- Group types remain semantically distinct, particularly personal lists, mutual groups, formal organisations and application-generated segments.
