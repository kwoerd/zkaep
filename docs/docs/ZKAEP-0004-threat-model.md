# ZKAEP-0004: Threat Model

Status: **Draft**  
Version: **0.1**

---

## 1. Threat Categories

ZK-AEP must consider:

- forged credentials;
- unauthorized issuers;
- compromised issuer keys;
- replayed proofs;
- proof reuse across contexts;
- linkability across events;
- malicious verifiers requesting excess data;
- stale policies;
- policy hash mismatch;
- revoked credentials;
- coerced disclosure;
- implementation bugs;
- governance capture outside the protocol;
- registry compromise;
- denial of service;
- wallet or holder key compromise;
- issuer bias or issuer incompetence;
- policy misuse.

---

## 2. Privacy Risks

The primary privacy risks are:

- revealing raw eligibility information;
- correlating proofs across events;
- storing unnecessary metadata;
- requiring full credentials when a proof would suffice;
- using global identifiers;
- combining registry, verifier, and issuer data to profile participants.

---

## 3. Mitigations

Recommended mitigations include:

- policy-scoped proofs;
- narrowly scoped nullifiers;
- challenge nonces;
- issuer registries;
- revocation/status checks;
- credential expiration;
- minimal verification outputs;
- local proof generation where feasible;
- audit logs that avoid private data;
- independent security review.

---

## 4. Governance Risks

ZK-AEP cannot prevent bad eligibility policy.

The protocol can only make policy execution more private, verifiable, and auditable.

Governance systems must separately provide:

- due process;
- appeal rights;
- anti-discrimination safeguards;
- policy review;
- emergency suspension procedures;
- issuer accountability;
- legal and medical/privacy review where applicable.
