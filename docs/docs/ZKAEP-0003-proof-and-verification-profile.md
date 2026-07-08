# ZKAEP-0003: Proof and Verification Profile

Status: **Draft**  
Version: **0.1**

---

## 1. Purpose

This document defines the minimum proof requirements for ZK-AEP.

---

## 2. Proof Statement

A proof SHOULD establish:

```text
I possess valid credential material from an approved issuer,
bound to the participant or authorized holder,
not revoked under the relevant status method,
and satisfying the eligibility relation for policy hash H(P).
```

---

## 3. Proof Binding

A proof MUST be bound to:

- policy hash;
- verifier challenge;
- proof context;
- accepted issuer set;
- credential status state;
- proof system identifier.

---

## 4. Replay Protection

A proof MUST include or be derived from a verifier-provided challenge nonce.

A verifier MUST reject stale or previously used challenge values where replay would create risk.

---

## 5. Nullifier Guidance

A nullifier MAY be used to prevent duplicate participation.

A nullifier SHOULD be scoped as narrowly as possible.

A nullifier MUST NOT expose private witness data.

---

## 6. Verification Algorithm

At minimum, verification checks:

1. the policy hash is known and current;
2. the issuer set is accepted;
3. the proof system is accepted;
4. the challenge is fresh;
5. the context is correct;
6. the credential status method passes;
7. the proof verifies.

---

## 7. Result

The verifier returns pass/fail plus permitted metadata.

The verifier MUST NOT receive private witness data.
