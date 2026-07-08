# ZK-AEP Specification

**Zero-Knowledge Athletic Eligibility Protocol**

Version: **0.1 Draft**  
Status: **Working Draft**  
Canonical protocol name: **ZK-AEP**  
Expanded name: **Zero-Knowledge Athletic Eligibility Protocol**

---

## 1. Abstract

ZK-AEP defines a privacy-preserving protocol for proving athletic eligibility against a published eligibility policy.

The protocol allows a participant to prove that they satisfy a defined eligibility rule set without requiring the verifier to receive the underlying private eligibility information.

ZK-AEP separates:

1. **Governance** — the authority that defines eligibility rules.
2. **Credential issuance** — the authority that attests to eligibility-related facts, documents, determinations, or credentials.
3. **Proof generation** — the participant-controlled act of producing a privacy-preserving proof.
4. **Verification** — the league, event, or system-controlled act of checking that a proof satisfies a published policy.
5. **Review and appeal** — the non-cryptographic process for handling disputes, exceptions, and governance concerns.

ZK-AEP is a standard. It is not itself a league rulebook, medical process, identity system, smart contract, or legal compliance framework.

---

## 2. Normative Language

The key words **MUST**, **MUST NOT**, **REQUIRED**, **SHOULD**, **SHOULD NOT**, **RECOMMENDED**, **MAY**, and **OPTIONAL** are to be interpreted in the style of RFC 2119 and RFC 8174 when they appear in all capitals.

---

## 3. Important Limitation

ZK-AEP can preserve privacy during eligibility verification.

It cannot, by itself, determine whether eligibility rules are lawful, fair, ethical, medically sound, or defensible.

For DAO Sports and related sports governance systems, ZK-AEP should be treated as a technical privacy standard, not as the source of eligibility authority.

A defensible eligibility system also requires:

- clear division rules;
- approved credential issuers;
- informed consent;
- data minimization;
- appeal and exception procedures;
- anti-discrimination review;
- governance accountability;
- legal review;
- medical, privacy, or bioethics review where applicable.

---

## 4. Design Goals

ZK-AEP has five primary design goals.

### 4.1 Privacy Preservation

Verifiers should learn only whether the participant satisfies the relevant eligibility rule set.

### 4.2 Eligibility Integrity

A participant should not be able to generate a valid proof unless the participant has valid eligibility credentials or attestations satisfying the policy.

### 4.3 Governance Separation

The protocol must not decide eligibility.

The protocol must only evaluate whether credentialed information satisfies a rule set adopted elsewhere.

### 4.4 Implementation Neutrality

The protocol should be implementable using multiple proof systems, credential systems, registries, and infrastructure providers.

### 4.5 Auditability Without Overexposure

The system should allow governance-level accountability without forcing unnecessary disclosure of private information.

---

## 5. Non-Goals

ZK-AEP does **not**:

- define who is eligible for a sports division;
- replace league constitutions, bylaws, policies, appeals, or due process;
- require any particular medical, biological, identity, or administrative criterion;
- require public disclosure of underlying eligibility evidence;
- require blockchain deployment;
- require a token;
- require one specific zero-knowledge proving system;
- replace legal, privacy, child-safety, medical, or employment compliance review;
- eliminate the need for anti-discrimination analysis;
- eliminate organizational liability by virtue of decentralization.

---

## 6. Actors

### 6.1 Governing Authority

The governing authority adopts eligibility policies.

In the DAO Sports Association ecosystem, this role may be performed through DAOmocracy or another valid constitutional process.

The governing authority MUST publish the policy identifier and policy hash used for proof verification.

### 6.2 Policy Maintainer

The policy maintainer transforms an adopted eligibility policy into a machine-checkable policy profile.

The policy maintainer MUST NOT change the substance of the adopted eligibility rule.

### 6.3 Issuer

An issuer is an approved authority that creates eligibility credentials or attestations.

An issuer MUST be listed in an issuer registry or otherwise accepted under a published verifier policy.

### 6.4 Participant

A participant is the person seeking eligibility verification.

The participant, or an authorized holder acting for the participant, controls presentation of credentials and generation of proofs.

### 6.5 Holder

A holder stores the credential and generates a proof or presentation.

The participant and holder are usually the same person but do not have to be.

### 6.6 Prover

The prover is the software, wallet, device, or service that generates the zero-knowledge proof.

### 6.7 Verifier

The verifier checks whether a submitted proof satisfies a specific published policy.

The verifier MUST NOT require underlying private eligibility information if a conforming ZK-AEP proof is sufficient under the adopted policy.

### 6.8 Registry

A registry stores public verification material, which may include issuer keys, policy hashes, revocation/status references, schema identifiers, and supported proof systems.

The registry MAY be on-chain, off-chain, decentralized, or institutionally maintained.

---

## 7. Core Data Objects

### 7.1 Eligibility Policy

An eligibility policy is the rule set against which a proof is verified.

A policy MUST include:

- `policy_id`
- `policy_version`
- `policy_hash`
- `governing_authority`
- `effective_date`
- `expiration_or_review_date`
- `allowed_issuers`
- `allowed_credential_types`
- `required_predicates`
- `revocation_or_status_requirements`
- `appeal_or_exception_reference`

The policy hash MUST be computed from the canonical policy representation.

### 7.2 Credential

A credential is an issuer-signed assertion or set of assertions about a participant.

A credential SHOULD be compatible with existing verifiable credential models where practical, but ZK-AEP does not require one exclusive credential format.

A credential used for ZK-AEP MUST include enough information to prove:

- issuer validity;
- subject or holder binding;
- issuance date;
- validity period, if applicable;
- credential type;
- credential status or revocation state, if applicable;
- satisfaction of one or more eligibility predicates.

### 7.3 Proof Request

A proof request is a verifier-generated request for proof against a specific policy.

A proof request MUST include:

- `policy_id`
- `policy_hash`
- `verifier_id`
- `challenge_nonce`
- `context`
- `timestamp`
- `accepted_proof_systems`
- `accepted_credential_profiles`

The challenge nonce MUST be unique enough to prevent replay.

### 7.4 Proof

A proof is a cryptographic object showing that the participant satisfies the requested policy.

A proof MUST be bound to:

- the policy hash;
- the verifier challenge;
- the proof context;
- the accepted issuer set;
- the relevant credential status check;
- the participant or holder authorization model.

### 7.5 Verification Result

A verification result is the verifier's output.

A conforming result SHOULD reveal only:

- `valid: true/false`
- `policy_id`
- `policy_version`
- `verification_timestamp`
- `proof_system`
- optional non-identifying audit reference

A verification result MUST NOT expose underlying private credential contents unless explicitly authorized under a separate lawful and governance-approved process.

---

## 8. Formal Model

Let:

- `P` be a published eligibility policy.
- `H(P)` be the canonical hash of policy `P`.
- `C` be a credential issued by an approved issuer.
- `I` be the issuer registry.
- `S` be the credential status or revocation state.
- `x` be private witness data held by the participant or holder.
- `π` be a zero-knowledge proof.
- `R_P(x, C, I, S)` be the eligibility relation defined by policy `P`.

The prover aims to prove the statement:

> There exists private witness data `x` and credential material `C` such that `C` is issued by an approved issuer, is valid under status state `S`, is bound to the participant or authorized holder, and satisfies relation `R_P` for policy hash `H(P)`.

The verifier checks:

```text
Verify(π, H(P), I, S, challenge, context) -> true or false
```

The verifier should learn that the statement is true or false and should not learn the private witness data `x`.

---

## 9. Required Security Properties

A conforming ZK-AEP implementation MUST be designed to support the following properties.

### 9.1 Completeness

If the participant has valid credential material satisfying the policy, an honest prover should be able to generate a proof accepted by an honest verifier.

### 9.2 Soundness

If the participant does not satisfy the policy, the participant should not be able to generate an accepted proof except with negligible probability under the proof system's stated assumptions.

### 9.3 Zero-Knowledge

The proof should not reveal private witness data beyond the truth of the eligibility statement.

### 9.4 Unforgeability

A participant MUST NOT be able to create a valid credential or proof without authorization from an approved issuer or without satisfying the proof relation.

### 9.5 Replay Resistance

A proof generated for one challenge, verifier, event, or context MUST NOT be reusable in another context unless the policy explicitly permits reuse.

### 9.6 Non-Linkability

Where feasible, proofs SHOULD be designed so repeated eligibility checks cannot be linked across events, verifiers, or contexts without participant authorization or a defined anti-duplication purpose.

### 9.7 Revocation Awareness

If the credential profile supports revocation or status checks, verification MUST account for the relevant status state.

### 9.8 Policy Binding

A proof MUST be bound to a specific policy hash so that a proof for one eligibility rule set cannot be accepted under another.

---

## 10. Privacy Requirements

A conforming verifier MUST practice data minimization.

The verifier SHOULD NOT receive:

- raw credential attributes;
- source documents;
- full credential contents;
- unnecessary identifiers;
- unrelated eligibility information;
- private witness data.

The verifier MAY receive:

- proof validity;
- policy identifier;
- policy version;
- proof-system identifier;
- issuer-set confirmation;
- non-identifying audit metadata;
- anti-duplication nullifier, if required by policy.

---

## 11. Nullifiers and Anti-Duplication

Some competitions may need to prevent the same participant from registering multiple times under the same policy or event.

ZK-AEP MAY use a nullifier.

A nullifier MUST be:

- scoped to a defined context;
- derived in a way that does not reveal private witness data;
- unlinkable across unrelated contexts unless explicitly required;
- documented in the policy profile.

Example scopes:

- one event;
- one season;
- one division;
- one governing authority;
- one anti-fraud process.

A global permanent nullifier SHOULD NOT be used unless strictly necessary and explicitly justified.

---

## 12. Governance Separation

ZK-AEP implementations MUST preserve this separation:

```text
Governance defines rules.
Issuers attest facts or determinations.
Provers generate proofs.
Verifiers check proofs.
Infrastructure executes the process.
```

No implementation of ZK-AEP should silently change the adopted eligibility policy.

A policy profile MUST be traceable to the governing decision that authorized it.

---

## 13. Credential Issuers and Verification Partners

ZK-AEP assumes that eligibility-related credentials are issued by approved credential issuers.

Credential issuers may include, depending on the eligibility policy and legal context:

- licensed medical providers;
- clinics;
- laboratories;
- approved administrative reviewers;
- independent credentialing organizations;
- sport-specific eligibility panels;
- bioethics-reviewed verification partners;
- other governance-approved issuers.

Issuer approval must be governed by clear standards.

The protocol should not assume that one clinic, lab, DAO, company, or person is automatically trusted.

A medical or bioverification partner should not be described as a final "source of truth" without qualification. A safer framing is:

> Approved issuers may verify eligibility-related facts or determinations under a published policy, with participant consent, data minimization, and applicable legal, medical, privacy, and anti-discrimination safeguards.

---

## 14. Long-Term Research Direction

ZK-AEP may eventually support privacy-preserving physiological verification methods as biometric, medical, and cryptographic systems mature.

Future systems could potentially allow approved issuers to verify eligibility-related physiological criteria and convert those determinations into zero-knowledge claims.

The goal would not be to expose identity, sex, gender, medical records, or raw biological data.

The goal would be to prove only that a participant satisfies a published eligibility policy.

This is not a current production capability.

Any future use would require:

- informed consent;
- independent medical and bioethics review;
- anti-discrimination review;
- appeal and exception procedures;
- strict data minimization;
- review for intersex, disability, privacy, and gender-expansive impacts.

---

## 15. Conformance Levels

### 15.1 ZK-AEP Core

An implementation conforms to ZK-AEP Core if it supports:

- policy identifiers;
- policy hashes;
- approved issuer references;
- proof requests;
- proof verification;
- challenge binding;
- context binding;
- privacy-preserving pass/fail results.

### 15.2 ZK-AEP Credential-Compatible

An implementation conforms to ZK-AEP Credential-Compatible if it supports a structured credential model with issuer, subject or holder binding, credential type, validity, and status.

### 15.3 ZK-AEP VC-Compatible

An implementation conforms to ZK-AEP VC-Compatible if it supports an interoperable verifiable credential profile compatible with an issuer-holder-verifier model.

### 15.4 ZK-AEP On-Chain Compatible

An implementation conforms to ZK-AEP On-Chain Compatible if verification can be performed or recorded on-chain without exposing private witness data.

### 15.5 ZK-AEP Production Ready

An implementation SHOULD NOT claim production readiness unless it has undergone:

- cryptographic review;
- implementation security review;
- privacy review;
- governance review;
- policy review;
- operational incident planning.

---

## 16. Minimum Viable Flow

1. Governance adopts an eligibility policy.
2. The policy is canonicalized and assigned a policy hash.
3. Approved issuers are listed.
4. A participant receives a credential from an approved issuer.
5. A verifier requests proof for a specific policy.
6. The participant generates a proof.
7. The verifier checks the proof.
8. The verifier receives only the verification result and permitted metadata.
9. Appeals, exceptions, or disputes are handled outside the proof system through governance-defined procedures.

---

## 17. Reference Predicate

The minimum eligibility predicate is:

```text
Eligible(participant, policy) = true
```

A ZK-AEP proof does not need to reveal why the predicate is true.

The proof only establishes that the participant has valid credential material satisfying the policy relation.

---

## 18. Versioning

ZK-AEP uses semantic-style specification versioning:

- `v0.x` — exploratory drafts;
- `v1.0` — first stable standard;
- `v1.x` — backward-compatible improvements;
- `v2.0` — breaking changes.

Each version MUST maintain a changelog.

---

## 19. Open Questions

The following remain intentionally unresolved in Draft v0.1:

- Which proof system should be recommended first?
- Should the first implementation target browser wallets, mobile wallets, smart contracts, or server-side verification?
- Should the standard define its own credential schema or profile an existing one?
- How should athlete appeals be linked without exposing private data?
- What governance body approves issuer registries?
- What minimum audit trail is necessary?
- What should the first non-production demonstration prove?

---

## 20. Safety and Review Notice

ZK-AEP may involve eligibility, privacy, identity, medical, biological, or other sensitive information depending on the policy and implementation.

This draft should not be used as a production eligibility system without qualified review from relevant experts.
