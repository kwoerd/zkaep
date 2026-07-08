# ZK-AEP

**Zero-Knowledge Athletic Eligibility Protocol**

Status: **Draft v0.1**  
Canonical protocol name: **ZK-AEP**  
Expanded name: **Zero-Knowledge Athletic Eligibility Protocol**  
Brand/domain form: **ZKAEP**

---

## Overview

ZK-AEP is an open protocol specification for privacy-preserving verification of athletic eligibility.

It allows a participant to prove that they satisfy a published eligibility policy without requiring unnecessary disclosure of the underlying eligibility information.

> Governance decides eligibility. Cryptography proves compliance. Infrastructure enforces the process.

ZK-AEP does not create eligibility rules. It defines how eligibility rules may be privately proven after a legitimate governing authority has adopted them.

---

## Important Limitation

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

## What ZK-AEP Is

ZK-AEP is:

- a protocol specification;
- a privacy-preserving verification framework;
- a standards track for athletic eligibility proofs;
- a method for reducing unnecessary disclosure;
- a way to bind proofs to published eligibility policies;
- a foundation for future implementations by DAO Sports, Strctrl Systems, or other compatible infrastructure providers.

---

## What ZK-AEP Is Not

ZK-AEP is not:

- a league rulebook;
- a medical policy;
- a legal defense by itself;
- a replacement for athlete consent;
- a replacement for appeals or due process;
- a guarantee that a policy is lawful;
- a guarantee that a policy is fair;
- a requirement to use blockchain;
- a requirement to use tokens;
- a requirement to expose private eligibility data;
- a production implementation.

---

## Repository Structure

```text
zkaep/
├── README.md
├── SPECIFICATION.md
├── GOVERNANCE.md
├── CHANGELOG.md
├── LICENSE
├── .gitignore
└── docs/
    ├── ZKAEP-0001-core-standard.md
    ├── ZKAEP-0002-credential-profile.md
    ├── ZKAEP-0003-proof-and-verification-profile.md
    ├── ZKAEP-0004-threat-model.md
    ├── ZKAEP-0005-issuer-governance.md
    └── ZKAEP-0006-long-term-research.md
```

---

## Draft Standards

The Draft v0.1 standards track begins with:

- **ZKAEP-0001 — Core Standard**
- **ZKAEP-0002 — Credential Profile**
- **ZKAEP-0003 — Proof and Verification Profile**
- **ZKAEP-0004 — Threat Model**
- **ZKAEP-0005 — Issuer Governance**
- **ZKAEP-0006 — Long-Term Research Direction**

Future standards may include:

- consent profile;
- appeals profile;
- division policy profile;
- issuer registry profile;
- smart contract verifier profile;
- off-chain verifier profile;
- wallet integration profile;
- audit and compliance profile;
- conformance test suite.

---

## Development Roadmap

### Phase 1 — Foundation

Establish the protocol identity and repository structure.

Status: **in progress**

### Phase 2 — Core Specification

Define actors, data objects, proof requests, verification results, issuer models, policy hashes, security assumptions, privacy requirements, and conformance levels.

Status: **draft**

### Phase 3 — Governance Alignment

Align ZK-AEP with DAO Sports governance while preserving the rule that the protocol does not become the source of eligibility authority.

Status: **planned**

### Phase 4 — Formalization

Define the eligibility predicate, proof relation, public inputs, private witness model, completeness, soundness, zero-knowledge, replay resistance, nullifiers, and invariants.

Status: **planned**

### Phase 5 — Reference Implementation

Build one or more conforming implementations after the specification is stable enough.

Possible targets include TypeScript, Rust, smart contract verification, browser wallet flows, mobile wallet flows, off-chain verification, issuer registries, and demo credential flows.

Status: **future work**

### Phase 6 — Review and Hardening

Before production use, ZK-AEP should be reviewed for cryptography, security engineering, privacy, identity, sports governance, legal risk, athlete rights, anti-discrimination risk, and medical or bioethics concerns where applicable.

Status: **future work**

### Phase 7 — Interoperability and Standardization

If ZK-AEP matures, it may become a broader standard that other sports organizations can implement.

Status: **long-term**

---

## Current Status

ZK-AEP is currently in **Draft v0.1**.

It is a protocol design project, not a production system.

The immediate goal is to define the standard clearly enough that future implementations can be built, reviewed, tested, and governed.

---

## Disclaimer

**ZK-AEP is an evolving technical standard.**

This repository contains **Draft v0.1** of the Zero-Knowledge Athletic Eligibility Protocol and is provided for research, discussion, review, and implementation experimentation.

ZK-AEP is a protocol specification. It is **not** a production system, legal opinion, medical guidance, regulatory framework, or eligibility policy.

Nothing in this repository should be interpreted as determining whether any eligibility rule is lawful, fair, ethical, medically appropriate, or defensible. Those determinations remain the responsibility of the applicable governing authority and should be supported by appropriate legal, medical, privacy, security, and governance review.

Implementers are responsible for independently evaluating all applicable legal, regulatory, security, privacy, operational, and ethical requirements before deploying any implementation derived from this specification.

---

## License

License to be determined.
