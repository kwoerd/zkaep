# ZK-AEP Governance

Version: **0.1 Draft**  
Status: **Working Draft**

---

## 1. Purpose

This document defines how the ZK-AEP standard is maintained.

ZK-AEP governance is about the protocol specification.

It does not decide athlete eligibility.

---

## 2. Authority Boundary

ZK-AEP governance may approve:

- protocol versions;
- credential profiles;
- proof profiles;
- conformance labels;
- implementation guidance;
- deprecation schedules;
- security notices.

ZK-AEP governance must not independently alter eligibility rules adopted by a sports governing authority.

---

## 3. Standards Process

ZK-AEP standards should be maintained through numbered documents:

- ZKAEP-0001 — Core Standard
- ZKAEP-0002 — Credential Profile
- ZKAEP-0003 — Proof and Verification Profile
- ZKAEP-0004 — Threat Model
- ZKAEP-0005 — Issuer Governance
- ZKAEP-0006 — Long-Term Research Direction
- ZKAEP-0007+ — Future extensions

---

## 4. Change Types

### 4.1 Editorial Change

An editorial change clarifies wording without changing technical meaning.

### 4.2 Minor Change

A minor change adds optional guidance or backward-compatible features.

### 4.3 Major Change

A major change affects conformance requirements, proof semantics, credential assumptions, privacy expectations, or governance boundaries.

---

## 5. Versioning

- Drafts use `v0.x`.
- Stable release begins at `v1.0`.
- Backward-compatible improvements use `v1.x`.
- Breaking changes require a major version increase.

---

## 6. Deprecation

A deprecated feature should include:

- reason for deprecation;
- replacement path;
- transition period;
- security or privacy impact;
- effective date.

---

## 7. Required Reviews Before v1.0

Before ZK-AEP v1.0, the standard should receive review in at least these areas:

- cryptography;
- identity and credentials;
- privacy;
- sports governance;
- security engineering;
- legal and regulatory risk;
- athlete rights and due process;
- anti-discrimination analysis;
- medical or bioethics review where applicable.

---

## 8. Governance Commitments

The ZK-AEP standard should preserve the following commitments:

1. Eligibility rules must be traceable to valid governance.
2. Technical systems must not silently alter governance decisions.
3. Privacy-preserving verification must not replace consent.
4. Proof validity must not replace appeal rights.
5. Implementation convenience must not override data minimization.
6. Production claims must require review.
