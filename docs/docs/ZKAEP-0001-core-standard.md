# ZKAEP-0001: Core Standard

Status: **Draft**  
Version: **0.1**

---

## 1. Standard Statement

ZK-AEP is a protocol for proving that a participant satisfies a published athletic eligibility policy while minimizing disclosure of underlying eligibility information.

---

## 2. Required Architecture

A conforming ZK-AEP system MUST include:

1. a published eligibility policy;
2. a canonical policy hash;
3. an issuer acceptance model;
4. a credential or attestation model;
5. a proof request format;
6. a proof generation process;
7. a verification process;
8. a privacy-preserving result format.

---

## 3. Mandatory Separation of Authority

The protocol MUST preserve the distinction between:

- rule-making;
- credential issuance;
- proof generation;
- proof verification;
- infrastructure execution.

An implementation MUST NOT treat cryptographic validity as a substitute for legitimate governance.

---

## 4. Required Public Inputs

A verifier MUST know or be able to resolve:

- policy identifier;
- policy hash;
- accepted issuers;
- proof system identifier;
- revocation or status method, if applicable;
- challenge nonce;
- verification context.

---

## 5. Required Private Inputs

A prover MAY use private inputs such as:

- credential contents;
- eligibility attributes;
- holder secrets;
- issuer signatures;
- witness data;
- opening values;
- nullifier secrets.

Private inputs MUST NOT be revealed by a conforming proof.

---

## 6. Verification Output

The standard output is:

```json
{
  "valid": true,
  "policy_id": "example-policy",
  "policy_version": "0.1",
  "verified_at": "timestamp",
  "proof_system": "example-proof-system"
}
```

Additional fields MAY be used only when they do not violate the privacy requirements of the policy profile.
