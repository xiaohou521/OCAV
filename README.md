This repository accompanies our paper:

**Application of Hybrid Chain Storage Framework in Energy Trading and Carbon Asset Management**  

It documents our research project on a **hybrid on-chain/off-chain settlement framework** for **distributed energy trading** and **carbon asset management** under **high-frequency, small-value, audit-intensive** workloads.

---

## Background & Motivation
Fully on-chain designs provide strong tamper-resistance and public verifiability, but incur prohibitive execution and storage cost under high-frequency settlement workloads. Purely off-chain approaches reduce cost but lack independently verifiable consistency.

This project explores a **hybrid architecture** that keeps **commitments and minimal constraints on-chain**, while retaining full records off-chain, enabling **replayable third-party auditing** with controlled on-chain cost.

---

## Core Ideas
- **Deterministic settlement digests**
  - Off-chain records are encoded deterministically and committed on-chain as digests (or batch roots).
  - Auditors can replay the same digest computation and compare against on-chain anchors.
- **Batch commitments**
  - Off-chain digests can be organized into a Merkle tree; only the root is anchored on-chain.
  - Supports efficient inclusion verification for auditing.
- **Constant-time membership verification (Accumulator)**
  - An accumulator-based mechanism supports membership checks with on-chain complexity independent of set size (with off-chain witness maintenance).
- **Carbon asset lifecycle consistency as on-chain invariants**
  - The on-chain layer enforces minimal conservation constraints (e.g., preventing over-transfer / over-retirement) to avoid irreversible inconsistencies.
- **Two-layer gated selective disclosure**
  - Gate 1: identity authentication (e.g., DID-based recent authentication window).
  - Gate 2: attribute-level authorization (holder-signed authorization + Merkle proof consistency).

---

## Evaluation Summary
We evaluate the framework from multiple angles:
- **Security**: deterministic tamper detection via replayable auditing.
- **Cost**: on-chain gas efficiency under batching and constrained workloads (including peak/off-peak effects and capacity stress).
- **Correctness / Integrity**: rejection of invalid operations via contract-level invariants.
- **Privacy**: structural inaccessibility of unauthorized selective disclosure requests through identity-gated access control.

---

## Public Datasets Used

- **PJM Day-Ahead Locational Marginal Price (LMP) dataset**

- **U.S. EIA-930 “Balancing Authority Hourly Operating Data”**

- **EU Emissions Trading System (EU ETS) aggregated statistics**

- **ICAP allowance price time series**

---

## Contact
- Yinghan Hou — houyinghan521@outlook.com  
- Zongyou Yang — yzy0624@outlook.com  
- Xiaokun Yang — yangxk@bupt.cn
