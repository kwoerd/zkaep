# ZKAEP-0002: Credential Profile

Status: **Draft**  
Version: **0.1**

---

## 1. Purpose

This document defines the minimum credential assumptions for ZK-AEP.

---

## 2. Credential Requirements

A credential used in ZK-AEP MUST support:

- issuer authentication;
- subject or holder binding;
- credential type identification;
- issuance date;
- validity period or expiration logic, where applicable;
- status or revocation logic, where applicable;
- proof of satisfaction for one or more eligibility predicates.

---

## 3. Issuer Requirements

An issuer MUST be approved under a published issuer policy.

Issuer approval SHOULD be scoped by:

- governing authority;
- sport;
- division;
- season;
- credential type;
- policy version.

---

## 4. Holder Control

The holder SHOULD control when and where a credential is presented.

The holder SHOULD NOT be required to disclose the full credential if a ZK-AEP proof is sufficient for the policy.

---

## 5. Credential Freshness

A verifier SHOULD reject credentials that are expired, revoked, outside scope, or not valid for the requested policy.

---

## 6. Compatibility

ZK-AEP SHOULD remain compatible with verifiable credential ecosystems where practical, especially the issuer-holder-verifier model.

ZK-AEP SHOULD remain credential-agnostic and should not require one specific credential technology.
