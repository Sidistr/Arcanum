# 🛡️ ARCANUM
**Zero-Plaintext Confidential Compilation & Air-Gapped Zero-Knowledge Proving (AG-ZKP) Infrastructure**

[![Research Preprint](https://img.shields.io/badge/Preprint-AG--ZKP_v1.1_(CERN%2FZenodo)-1e3a8a?style=flat-square)](https://github.com/Sidistr/airgapped-zk-paper)
[![ORCID](https://img.shields.io/badge/ORCID-0009--0008--4681--7186-15803d?style=flat-square)](https://orcid.org/0009-0008-4681-7186)
[![Architecture](https://img.shields.io/badge/Architecture-Rust_%7C_RISC--V_zkVM_%7C_Air--Gap-0f172a?style=flat-square)](#)
[![License: MIT / Apache-2.0](https://img.shields.io/badge/License-MIT_%2F_Apache--2.0-475569?style=flat-square)](#)

> **"Ship cryptographic proof of compilation and execution—never your source code, and never over an online operating system."**

**Arcanum** is a sovereign software supply-chain and confidential compilation protocol engineered for **B2G (Defense & Critical Infrastructure)**, **Institutional DeFi / L2s (Arbitrum Stylus, Starknet)**, and **High-Assurance IP Protection**. 

Instead of trusting cloud hypervisors or side-channel-prone hardware enclaves (TEEs) with plaintext source code, Arcanum physically decouples compilation and zero-knowledge proof generation inside an **Air-Gapped Prover Appliance ($\mathcal{P}_{\text{AG}}$)**. Proprietary source code ($S$) remains permanently offline as a secret witness ($w_{\text{core}}$), while only succinct, kleptography-free zero-knowledge proofs ($\pi$) cross a unidirectional optical or data-diode boundary.

---

## 📄 Foundational Research: Air-Gapped Zero-Knowledge Proving (AG-ZKP)

Arcanum's cryptographic security model is formally specified in our companion research paper:
* **Title:** *Air-Gapped Zero-Knowledge Proving (AG-ZKP): Formalizing Witness Isolation, Unidirectional I/O Bounds, and Kleptographic Resistance in Offline Provers (v1.1)*
* **Authors:** **Mert Atakan** ([ORCID: 0009-0008-4681-7186](https://orcid.org/0009-0008-4681-7186)) & **Anjul Khatri**
* **Paper Repository & PDF:** [`github.com/Sidistr/airgapped-zk-paper`](https://github.com/Sidistr/airgapped-zk-paper)

### Key Architectural Guarantees
1. **Zero Online Plaintext RAM Exposure:** During AST lowering, witness synthesis, and Multi-Scalar Multiplications (MSM/NTT), proprietary source code and secret witnesses never enter a network-connected kernel's volatile memory.
2. **$1\times$ Native Proving Speed (vs. $10^5\times$ FHE Overhead):** Eliminates the intractable algebraic bootstrapping and terabyte ciphertext expansion bottlenecks of Fully Homomorphic Encryption (FHE+ZKP) by replacing homomorphic wrapping with deterministic unidirectional hardware I/O.
3. **Kleptographic Resistance (Deterministic Fiat-Shamir):** Defeats malicious supply-chain compiler trojans attempting to leak witness bits via prover randomness ($r, s \in \mathbb{F}_p$) by enforcing strict cryptographic sponge determinism:
   $$r_i \leftarrow \mathcal{H}_{\text{FS}}\big(\texttt{"ARCANUM-AG-ZKP-V1"} \;\|\; \text{vk}_{\text{hash}} \;\|\; x \;\|\; \mathcal{H}(w_{\text{core}}) \;\|\; \sigma_{\text{hw}} \;\|\; i\big) \pmod{p}$$

---

## 🏛️ Target Deployment Verticals (B2G & Enterprise)

| Sector | Use Case | Arcanum Guarantee |
| :--- | :--- | :--- |
| **Defense & Sovereign Agencies (B2G)** | Classified SCIF firmware compilation & cross-domain verification | Proves binary compliance across optical data diodes with zero source exfiltration risk. |
| **Critical Infrastructure** | Nuclear, energy grid, and telecom software supply-chain attestation | Verifies deterministic builds offline before deployment to air-gapped industrial controllers. |
| **Institutional Finance & L2s** | Proprietary Rust/C++ quantitative algorithms & RWA compliance | Verifies offline execution proofs on-chain via **Arbitrum Stylus** and Starknet verifiers. |
| **Sovereign AI Systems** | High-value model weights & confidential inference attestation | Locks model parameters inside $\mathcal{P}_{\text{AG}}$ while proving authentic inference execution. |

---

## 👥 Core Team & Contributors

* **Mert Atakan** — *Founder & Chief Architect* ([ORCID](https://orcid.org/0009-0008-4681-7186)) — Conceptual framework, AG-ZKP isolation architecture, and B2G strategy.
* **M. Zidan Fatonie** — *Founding Systems Architect* — Rust compiler pipeline, zkVM integration, and L2 verifier systems.
* **Anjul Khatri** — *ZK Research Co-Author & Early Contributor* — Circuit formalization, Groth16/PLONK state-transition analysis, and comparative cryptographic modeling.
* ## 📜 Licensing (Dual-License Model)

Arcanum and the AG-ZKP reference implementation are distributed under a **Dual-License** model:

1. **Open-Source License (GNU AGPLv3):** 
   This software is free and open-source under the terms of the [GNU Affero General Public License v3.0](LICENSE). It is fully compliant with open-source research grants (including NLnet / NGI). If you modify or run this software over a network (e.g., as a cloud/SaaS service or managed proxy), you must make your complete source code available under the AGPLv3.

2. **Commercial Enterprise License:** 
   For organizations, cloud backup providers, and enterprise custodians that wish to integrate Arcanum / AG-ZKP into proprietary, closed-source software, hardware appliances, or commercial SaaS platforms without the copyleft obligations of the AGPLv3, a separate **Commercial License** is available from Arcanum Research.

For commercial licensing inquiries, enterprise integrations, or partnerships, please contact: **mertatakan53@gmail.com**
