# REM-04 Part 6 — Application and Permission Requirement Extraction Matrix (Sections 26–30)

## Document status

**Canonical editorial extraction**

This document extracts protocol requirements from Sections 26–30 of `design-notes/04-application-and-permission-model.md`.

The source model is the sole normative source for the requirements below. Explanatory wording has been added only to make each requirement independently readable, testable and traceable. No requirements from earlier chat-generated drafts have been retained.

---

## Extraction scope

This part covers:

26. Consent interface
27. Granular approval
28. Consent receipt
29. Authorisation session
30. Access token

Requirement identifiers continue sequentially from Part 5, beginning with `REM-04-323`.

---

# 26. Consent interface

## REM-04-323 — Consent presentation responsibility

**Source**  
Section 26: “A Relay Provider or trusted authorisation service should present the permission request to the user.”

**Requirement**  
A Relay Provider or trusted authorisation service SHOULD present each Permission Request to the affected user before approval.

**Classification**  
Consent; authorisation workflow; user interface.

**Notes**  
The source permits either the Relay Provider or another trusted authorisation service to perform this role.

---

## REM-04-324 — Application name disclosure

**Source**  
Section 26, required consent-interface information: “application name”.

**Requirement**  
The consent interface MUST display the requesting application’s visible name.

**Classification**  
Consent disclosure; application identification.

**Notes**  
The visible name does not replace the stable Application Identity.

---

## REM-04-325 — Responsible controller disclosure

**Source**  
Section 26, required consent-interface information: “responsible controller”.

**Requirement**  
The consent interface MUST identify the person, organisation or authority responsible for the requesting application.

**Classification**  
Consent disclosure; accountability.

**Notes**  
This enables the user to distinguish the application product from the legal or operational controller behind it.

---

## REM-04-326 — Verification-status disclosure

**Source**  
Section 26, required consent-interface information: “verification status”.

**Requirement**  
The consent interface MUST display the application’s current verification status.

**Classification**  
Consent disclosure; application verification.

**Notes**  
The interface must remain consistent with Section 8 and must not imply that verification is a universal guarantee of trustworthiness.

---

## REM-04-327 — Requested-data disclosure

**Source**  
Section 26, required consent-interface information: “requested data”.

**Requirement**  
The consent interface MUST identify the data and resources the application requests permission to access.

**Classification**  
Consent disclosure; resource scope.

**Notes**  
The description should be concrete enough for the user to understand the affected collections, records, fields, blobs or services.

---

## REM-04-328 — Requested-actions disclosure

**Source**  
Section 26, required consent-interface information: “requested actions”.

**Requirement**  
The consent interface MUST identify the actions the application requests permission to perform.

**Classification**  
Consent disclosure; action scope.

**Notes**  
Read, create, update, delete, publish and high-authority actions must not be presented as interchangeable.

---

## REM-04-329 — Duration disclosure

**Source**  
Section 26, required consent-interface information: “duration”.

**Requirement**  
The consent interface MUST explain how long the requested authority would remain valid.

**Classification**  
Consent disclosure; duration; lifecycle.

**Notes**  
The interface should distinguish one-time, session-bound, fixed-term, conditional and until-revoked authority.

---

## REM-04-330 — Purpose disclosure

**Source**  
Section 26, required consent-interface information: “purpose”.

**Requirement**  
The consent interface MUST explain the declared purpose for which the requested authority will be used.

**Classification**  
Consent disclosure; purpose limitation.

**Notes**  
The purpose must remain distinct from the action itself.

---

## REM-04-331 — Retention disclosure

**Source**  
Section 26, required consent-interface information: “retention”.

**Requirement**  
The consent interface MUST explain whether and for how long the application proposes to retain data outside the repository.

**Classification**  
Consent disclosure; retention; external copies.

**Notes**  
The interface must not imply that the protocol can technically guarantee deletion of every external copy.

---

## REM-04-332 — AI-use disclosure

**Source**  
Section 26, required consent-interface information: “AI use”.

**Requirement**  
The consent interface MUST explain any requested AI-related processing.

**Classification**  
Consent disclosure; AI processing.

**Notes**  
The disclosure should distinguish inference, personalisation, embedding, fine-tuning, general training, evaluation and human review where applicable.

---

## REM-04-333 — Onward-sharing disclosure

**Source**  
Section 26, required consent-interface information: “onward sharing”.

**Requirement**  
The consent interface MUST explain whether data may be disclosed to third parties and under what declared conditions.

**Classification**  
Consent disclosure; onward sharing; third-party access.

**Notes**  
Where known, the interface should distinguish direct repository access from receipt of copied data.

---

## REM-04-334 — High-risk-capability disclosure

**Source**  
Section 26, required consent-interface information: “high-risk capabilities”.

**Requirement**  
The consent interface MUST identify requested high-risk or high-authority capabilities distinctly from ordinary content access.

**Classification**  
Consent disclosure; high-authority operations; risk.

**Notes**  
Examples elsewhere in the source include migration, permission management, key management and recovery management.

---

## REM-04-335 — Changed-request disclosure

**Source**  
Section 26, required consent-interface information: “whether the request differs from a previous version”.

**Requirement**  
The consent interface MUST identify whether the current request differs materially from a previously presented or approved request.

**Classification**  
Consent disclosure; change management; re-authorisation.

**Notes**  
This allows the user to distinguish routine reconnection from expanded or altered access.

---

## REM-04-336 — Avoidance of vague legalistic descriptions

**Source**  
Section 26: “The interface should not rely on legalistic phrases such as: ‘Access your data’.”

**Requirement**  
The consent interface SHOULD NOT rely solely on vague or legalistic phrases that fail to describe the practical effect of the request.

**Classification**  
Consent quality; human-readable disclosure; recommendation.

**Notes**  
A phrase such as “Access your data” is insufficient where it does not identify which data, actions, purposes or restrictions apply.

---

## REM-04-337 — Concrete-consequence explanation

**Source**  
Section 26: “It should show concrete consequences.”

**Requirement**  
The consent interface SHOULD explain the concrete consequences of approval in ordinary language.

**Classification**  
Consent quality; user comprehension; recommendation.

**Notes**  
The source example describes both granted capabilities and explicit exclusions.

---

## REM-04-338 — Granted-capability explanation

**Source**  
Section 26 example: the application can read the public profile, create and edit posts at the user’s instruction, and cache those posts for seven days.

**Requirement**  
A concrete consent explanation SHOULD identify the principal capabilities that approval would grant.

**Classification**  
Consent explanation; capability disclosure; recommendation.

**Notes**  
The example is illustrative rather than a mandatory wording template.

---

## REM-04-339 — Excluded-capability explanation

**Source**  
Section 26 example: the application cannot read private records, delete posts, train AI models or share copies with third parties.

**Requirement**  
A concrete consent explanation SHOULD identify material capabilities or uses that are excluded from the proposed grant.

**Classification**  
Consent explanation; restriction disclosure; recommendation.

**Notes**  
Explaining exclusions helps prevent users from interpreting narrow access as broader authority.

---

# 27. Granular approval

## REM-04-340 — Partial approval support

**Source**  
Section 27: “The user should be able to approve less than the full request where practical.”

**Requirement**  
The authorisation system SHOULD allow the user to approve a subset of the requested permissions where practical.

**Classification**  
Granular consent; least privilege; recommendation.

**Notes**  
The source recognises that some applications may have genuinely essential permissions, but optional permissions should remain independently deniable where practical.

---

## REM-04-341 — Independent scope approval

**Source**  
Section 27 example separating read profile, read posts, create posts, delete posts and read private drafts.

**Requirement**  
Distinct requested scopes or capabilities SHOULD be independently approvable or deniable where practical.

**Classification**  
Granular consent; scope decomposition; recommendation.

**Notes**  
The example demonstrates that related content operations need not be approved as one indivisible bundle.

---

## REM-04-342 — Reduced-capability operation

**Source**  
Section 27: “The application may then operate with reduced capability...”

**Requirement**  
An application MAY continue operating with the subset of capabilities actually approved by the user.

**Classification**  
Application behaviour; degraded operation; permission enforcement.

**Notes**  
The application must enforce the reduced grant rather than acting as though the full request was approved.

---

## REM-04-343 — Unavailable-feature explanation

**Source**  
Section 27: the application may “explain that some features are unavailable”.

**Requirement**  
An application MAY explain that particular features are unavailable because the user denied the permissions those features require.

**Classification**  
Application behaviour; user communication.

**Notes**  
The explanation must not be coercive or misleading about whether the denied permission was essential.

---

## REM-04-344 — Refusal to continue when essential permission is denied

**Source**  
Section 27: the application may “decline to continue if a genuinely essential permission was refused.”

**Requirement**  
An application MAY decline to continue where a genuinely essential permission has been refused.

**Classification**  
Application behaviour; essential capability; consent outcome.

**Notes**  
This permission does not allow an application to misclassify optional access as essential.

---

## REM-04-345 — Prohibition on false essentiality claims

**Source**  
Section 27: “It must not falsely describe optional access as essential.”

**Requirement**  
An application MUST NOT describe optional access as essential in order to pressure the user into granting it.

**Classification**  
Consent integrity; anti-coercion; application conduct.

**Notes**  
Essentiality must reflect a genuine functional dependency.

---

## REM-04-346 — Grant limited to approved subset

**Source**  
Section 27, combined partial-approval example and resulting reduced-capability behaviour.

**Requirement**  
Where the user approves only part of a Permission Request, the resulting Permission Grant MUST contain only the approved scopes and capabilities.

**Classification**  
Grant construction; granular consent; least privilege.

**Notes**  
Denied scopes must not remain latent or silently exercisable.

---

# 28. Consent receipt

## REM-04-347 — Consent receipt issuance

**Source**  
Section 28: “After approval, the user should receive a Consent Receipt.”

**Requirement**  
After a Permission Request is approved, the user SHOULD receive a Consent Receipt.

**Classification**  
Consent evidence; user record; recommendation.

**Notes**  
The receipt records what the user approved at that time and is distinct from the access token used operationally by the application.

---

## REM-04-348 — Receipt application identity

**Source**  
Section 28, receipt content: “application”.

**Requirement**  
A Consent Receipt SHOULD identify the application to which consent was granted.

**Classification**  
Consent evidence; application identification.

**Notes**  
The stable Application Identity should be retained even if a visible name is also included.

---

## REM-04-349 — Receipt manifest version

**Source**  
Section 28, receipt content: “manifest version”.

**Requirement**  
A Consent Receipt SHOULD identify the Application Manifest version presented at approval.

**Classification**  
Consent evidence; manifest traceability.

**Notes**  
This allows later comparison if the application’s controller, domains, policies, keys or permission catalogue change.

---

## REM-04-350 — Receipt approved scopes

**Source**  
Section 28, receipt content: “approved scopes”.

**Requirement**  
A Consent Receipt SHOULD record the scopes and capabilities the user approved.

**Classification**  
Consent evidence; scope traceability.

**Notes**  
The recorded scopes should correspond to the resulting Permission Grant.

---

## REM-04-351 — Receipt denied scopes

**Source**  
Section 28, receipt content: “denied scopes”.

**Requirement**  
A Consent Receipt SHOULD record the scopes or capabilities the user denied.

**Classification**  
Consent evidence; denied authority; granular consent.

**Notes**  
Recording denied scopes helps distinguish partial approval from omission or later expansion.

---

## REM-04-352 — Receipt purpose

**Source**  
Section 28, receipt content: “purpose”.

**Requirement**  
A Consent Receipt SHOULD record the declared purpose associated with the approved authority.

**Classification**  
Consent evidence; purpose limitation.

**Notes**  
Purpose is part of what the user agreed to and should remain inspectable after approval.

---

## REM-04-353 — Receipt retention declaration

**Source**  
Section 28, receipt content: “retention declaration”.

**Requirement**  
A Consent Receipt SHOULD record the retention declaration presented and approved.

**Classification**  
Consent evidence; retention commitment.

**Notes**  
The receipt records the commitment but does not itself prove that all external copies were later deleted.

---

## REM-04-354 — Receipt AI declaration

**Source**  
Section 28, receipt content: “AI declaration”.

**Requirement**  
A Consent Receipt SHOULD record the AI-use declaration presented and approved.

**Classification**  
Consent evidence; AI processing.

**Notes**  
The record should preserve distinctions among different AI activities rather than reducing them to a generic AI flag.

---

## REM-04-355 — Receipt issue time

**Source**  
Section 28, receipt content: “issue time”.

**Requirement**  
A Consent Receipt SHOULD record when the consent was issued.

**Classification**  
Consent evidence; temporal metadata.

**Notes**  
The issue time supports later audit and version comparison.

---

## REM-04-356 — Receipt expiration

**Source**  
Section 28, receipt content: “expiration”.

**Requirement**  
A Consent Receipt SHOULD record the grant’s expiration or indicate that no fixed expiration was set.

**Classification**  
Consent evidence; duration; lifecycle.

**Notes**  
An indefinite grant remains reviewable and revocable.

---

## REM-04-357 — Receipt user-facing explanation

**Source**  
Section 28, receipt content: “user-facing explanation shown at approval”.

**Requirement**  
A Consent Receipt SHOULD preserve the user-facing explanation displayed when approval was given.

**Classification**  
Consent evidence; disclosure traceability.

**Notes**  
This captures not only machine-readable scope but also the concrete explanation the user relied upon.

---

## REM-04-358 — Receipt grant identifier

**Source**  
Section 28, receipt content: “grant identifier”.

**Requirement**  
A Consent Receipt SHOULD identify the Permission Grant created by the approval.

**Classification**  
Consent evidence; grant traceability.

**Notes**  
The identifier enables the receipt, grant, audit events and revocation record to be correlated.

---

## REM-04-359 — Consent reconstruction capability

**Source**  
Section 28: “The receipt allows the person to later answer: ‘What exactly did I agree to?’”

**Requirement**  
A Consent Receipt SHOULD contain sufficient information for the user to reconstruct what authority, purposes and conditions were approved.

**Classification**  
Consent evidence; transparency; auditability.

**Notes**  
The receipt should remain understandable and inspectable after the original authorisation session ends.

---

## REM-04-360 — Private repository storage option

**Source**  
Section 28: “The consent receipt may be stored privately in the repository...”

**Requirement**  
A Consent Receipt MAY be stored as a private record in the user’s Relay Repository.

**Classification**  
Consent evidence; storage; privacy.

**Notes**  
Private storage prevents the consent record itself from becoming unnecessarily public.

---

## REM-04-361 — Authorisation-service storage option

**Source**  
Section 28: the receipt may be stored “in the... authorisation service.”

**Requirement**  
A Consent Receipt MAY be stored by the trusted authorisation service.

**Classification**  
Consent evidence; storage; authorisation infrastructure.

**Notes**  
Where stored outside the repository, the receipt should remain attributable, retrievable and protected.

---

# 29. Authorisation session

## REM-04-362 — Temporary authorisation interaction

**Source**  
Section 29: “An Authorisation Session is the temporary interaction through which a person reviews and approves a Permission Request.”

**Requirement**  
An Authorisation Session MUST be treated as a temporary interaction for reviewing and approving a specific Permission Request.

**Classification**  
Authorisation workflow; session lifecycle; consent.

**Notes**  
The session is distinct from the resulting Permission Grant and Access Token.

---

## REM-04-363 — Callback-substitution protection

**Source**  
Section 29, session threat list: “callback substitution”.

**Requirement**  
An Authorisation Session SHOULD be protected against callback substitution.

**Classification**  
Authorisation security; redirect integrity.

**Notes**  
An attacker must not be able to replace the authorised callback destination with another location.

---

## REM-04-364 — Replay protection

**Source**  
Section 29, session threat list: “replay”.

**Requirement**  
An Authorisation Session SHOULD be protected against replay of authorisation requests, responses or codes.

**Classification**  
Authorisation security; replay resistance.

**Notes**  
Short-lived, one-time authorisation codes are one supporting mechanism identified by the source.

---

## REM-04-365 — Request-tampering protection

**Source**  
Section 29, session threat list: “request tampering”.

**Requirement**  
An Authorisation Session SHOULD be protected against unauthorised modification of the Permission Request.

**Classification**  
Authorisation security; request integrity.

**Notes**  
The user must approve the same request that is later converted into a grant.

---

## REM-04-366 — Cross-site request-forgery protection

**Source**  
Section 29, session threat list: “cross-site request forgery”.

**Requirement**  
An Authorisation Session SHOULD be protected against cross-site request forgery.

**Classification**  
Authorisation security; CSRF protection.

**Notes**  
State validation is one modern authorisation control identified by the source.

---

## REM-04-367 — Session-fixation protection

**Source**  
Section 29, session threat list: “session fixation”.

**Requirement**  
An Authorisation Session SHOULD be protected against session fixation.

**Classification**  
Authorisation security; session integrity.

**Notes**  
An attacker must not be able to force the user to authorise within an attacker-controlled session context.

---

## REM-04-368 — Malicious-redirect protection

**Source**  
Section 29, session threat list: “malicious redirect locations”.

**Requirement**  
An Authorisation Session SHOULD reject malicious or unauthorised redirect locations.

**Classification**  
Authorisation security; redirect validation.

**Notes**  
Exact callback matching is identified as a supporting control.

---

## REM-04-369 — Modern secure-authorisation practices

**Source**  
Section 29: “The implementation should follow modern secure authorisation practices...”

**Requirement**  
Implementations SHOULD follow current secure-authorisation practices appropriate to the application and threat model.

**Classification**  
Security architecture; authorisation best practice; recommendation.

**Notes**  
The source provides a minimum illustrative set but does not require the protocol to reinvent all low-level mechanisms.

---

## REM-04-370 — Exact callback matching

**Source**  
Section 29, secure practices: “exact callback matching”.

**Requirement**  
An Authorisation Session SHOULD use exact matching against authorised callback locations.

**Classification**  
Authorisation security; callback validation.

**Notes**  
Wildcard or loosely matched redirects increase substitution risk.

---

## REM-04-371 — Short-lived authorisation codes

**Source**  
Section 29, secure practices: “short-lived authorisation codes”.

**Requirement**  
Authorisation codes SHOULD be short-lived.

**Classification**  
Authorisation security; credential lifetime.

**Notes**  
Short lifetimes reduce the usable window for interception or replay.

---

## REM-04-372 — Proof-key mechanisms

**Source**  
Section 29, secure practices: “proof key mechanisms”.

**Requirement**  
Authorisation flows SHOULD use an appropriate proof-key mechanism where applicable.

**Classification**  
Authorisation security; code interception resistance.

**Notes**  
The source does not prescribe a named mechanism, leaving implementation details to established secure standards.

---

## REM-04-373 — State validation

**Source**  
Section 29, secure practices: “state validation”.

**Requirement**  
Authorisation Sessions SHOULD validate session-bound state values.

**Classification**  
Authorisation security; request correlation; CSRF resistance.

**Notes**  
State validation helps bind the response to the initiating client session.

---

## REM-04-374 — Nonce validation

**Source**  
Section 29, secure practices: “nonce validation”.

**Requirement**  
Authorisation Sessions SHOULD validate nonces where the selected authorisation mechanism uses them.

**Classification**  
Authorisation security; replay resistance; response binding.

**Notes**  
The nonce must be checked rather than merely transmitted.

---

## REM-04-375 — Secure transport

**Source**  
Section 29, secure practices: “secure transport”.

**Requirement**  
Authorisation Sessions MUST use secure transport appropriate to protect requests, credentials and responses in transit.

**Classification**  
Transport security; confidentiality; integrity.

**Notes**  
The source presents secure transport as part of the modern practices implementations should follow; it is expressed here as mandatory because insecure transport would defeat the surrounding protections.

---

## REM-04-376 — Reuse of established low-level mechanisms

**Source**  
Section 29: “The Relay protocol need not reinvent all low-level authorisation mechanisms.”

**Requirement**  
Relay implementations MAY use established low-level authorisation standards and mechanisms rather than defining new ones unnecessarily.

**Classification**  
Protocol design; standards reuse; security.

**Notes**  
Reuse does not remove the need to satisfy Relay-specific identity, scope, grant and audit requirements.

---

# 30. Access token

## REM-04-377 — Access-token function

**Source**  
Section 30: “An Access Token allows an application to exercise an approved grant.”

**Requirement**  
An Access Token MUST authorise only the exercise of authority contained in an approved Permission Grant.

**Classification**  
Token semantics; delegated authority; permission enforcement.

**Notes**  
The token is an operational credential and does not itself create authority beyond the grant.

---

## REM-04-378 — Grant limitation

**Source**  
Section 30, token requirement: “limited to the grant”.

**Requirement**  
An Access Token MUST be limited to the Permission Grant from which it derives.

**Classification**  
Token scope; least privilege; delegated authority.

**Notes**  
A token must not contain broader resources, actions, purposes or conditions than the grant.

---

## REM-04-379 — Token time bound

**Source**  
Section 30, token requirement: “time-bound”.

**Requirement**  
An Access Token MUST have a bounded validity period.

**Classification**  
Token lifecycle; credential lifetime; security.

**Notes**  
A long-lived grant may still be exercised through shorter-lived tokens.

---

## REM-04-380 — Token audience binding

**Source**  
Section 30, token requirement: “audience-bound”.

**Requirement**  
An Access Token MUST be bound to its intended Relay Provider, service or other defined audience.

**Classification**  
Token security; audience restriction.

**Notes**  
A token issued for one service must not be accepted indiscriminately by another.

---

## REM-04-381 — Tamper protection

**Source**  
Section 30, token requirement: “protected against tampering”.

**Requirement**  
An Access Token MUST be protected against undetected modification.

**Classification**  
Token integrity; cryptographic protection.

**Notes**  
The source does not mandate one token format or cryptographic mechanism.

---

## REM-04-382 — Revocable or short-lived token design

**Source**  
Section 30, token requirement: “revocable or short-lived”.

**Requirement**  
An Access Token MUST either support revocation or be sufficiently short-lived to limit continued use after authority changes.

**Classification**  
Token lifecycle; revocation; security.

**Notes**  
Implementations may combine both properties.

---

## REM-04-383 — Token not proof of identity ownership

**Source**  
Section 30, token requirement: “unsuitable as proof of ownership of the identity.”

**Requirement**  
An Access Token MUST NOT be treated as proof that the application owns or controls the Relay Identity itself.

**Classification**  
Authority separation; token semantics; identity protection.

**Notes**  
Possession of delegated access is not equivalent to identity ownership or controller authority.

---

## REM-04-384 — Application Identity reference

**Source**  
Section 30, token information: “Application Identity”.

**Requirement**  
An Access Token SHOULD identify or reference the authorised Application Identity.

**Classification**  
Token claims; application attribution.

**Notes**  
This enables the receiving service to associate token use with the correct application.

---

## REM-04-385 — Relay Identity reference

**Source**  
Section 30, token information: “Relay Identity”.

**Requirement**  
An Access Token SHOULD identify or reference the Relay Identity whose authority is being exercised.

**Classification**  
Token claims; delegated identity authority.

**Notes**  
The reference does not imply that the application becomes the identity.

---

## REM-04-386 — Permission Grant reference

**Source**  
Section 30, token information: “Permission Grant”.

**Requirement**  
An Access Token SHOULD identify or reference the Permission Grant on which it depends.

**Classification**  
Token claims; grant traceability; auditability.

**Notes**  
This allows token use to be checked against current grant and revocation state.

---

## REM-04-387 — Approved-capabilities reference

**Source**  
Section 30, token information: “approved capabilities”.

**Requirement**  
An Access Token SHOULD identify or reference the capabilities it permits the application to exercise.

**Classification**  
Token claims; capability enforcement.

**Notes**  
The represented capabilities must not exceed the underlying grant.

---

## REM-04-388 — Token expiration information

**Source**  
Section 30, token information: “expiration”.

**Requirement**  
An Access Token SHOULD contain or reference an unambiguous expiration time.

**Classification**  
Token claims; lifecycle; expiry enforcement.

**Notes**  
The receiving service must enforce expiration rather than treating it as informational only.

---

## REM-04-389 — Intended-provider reference

**Source**  
Section 30, token information: “intended Relay Provider or service”.

**Requirement**  
An Access Token SHOULD identify or reference its intended Relay Provider or service.

**Classification**  
Token claims; audience binding; service restriction.

**Notes**  
This supports the mandatory audience-bound property.

---

## REM-04-390 — Token validation against grant state

**Source**  
Section 30, combined requirements that a token exercise an approved grant, remain limited to it and be revocable or short-lived.

**Requirement**  
A receiving Relay Provider or service MUST validate an Access Token against the relevant grant, expiry, audience and revocation conditions before accepting it.

**Classification**  
Token validation; permission enforcement; security.

**Notes**  
This requirement is a necessary operational consequence of the source’s explicit token constraints.

---

# Editorial QA record

## Scope verification

- Source content was limited to Sections 26–30 of `design-notes/04-application-and-permission-model.md`.
- Section 31 and later content was excluded.
- Examples were used to clarify consent and security behaviour but were not promoted into mandatory wording or final token formats.

## Numbering verification

- First requirement: `REM-04-323`.
- Final requirement: `REM-04-390`.
- Requirement numbering continues directly from Part 5.
- Requirement identifiers are continuous, unique and ordered according to the source sections.

## Traceability verification

- Every requirement contains **Source**, **Requirement**, **Classification** and **Notes**.
- Each required consent-interface disclosure was extracted separately because each is independently testable.
- Consent-receipt fields were extracted separately to preserve later auditability.
- Security threats and recommended controls were not collapsed into one broad security statement.
- Access-token properties and token claims remain separately traceable.

## Normative-language verification

- Source “must” statements are represented using `MUST` or `MUST NOT`.
- Source “should” statements are preserved as `SHOULD` recommendations unless a necessary security consequence was made explicit and documented in Notes.
- Source “may” statements are preserved as `MAY` permissions.
- Examples remain illustrative rather than exhaustive.

## Editorial verification

- Consent presentation remains distinct from grant issuance.
- Partial approval results in a grant containing only approved authority.
- A Consent Receipt remains distinct from an operational Access Token.
- The Authorisation Session remains temporary and separate from the resulting grant and token.
- Access Tokens remain bounded by grant, time, audience and revocation state.
- Access-token possession is not treated as identity ownership.
