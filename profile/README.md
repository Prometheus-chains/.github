# 🧬 Prometheus Chains

**Credibly neutral healthcare rails on Ethereum and Base.**

Prometheus Chains is an open protocol for healthcare that brings **patient-owned data** and **instant claim payments** onchain.  
- **Patient Records:** anchored on Ethereum L1 for integrity, **encrypted on Base L2** for privacy.  
- **Claims & Payments:** providers submit claims, rules enforce coverage, and USDC settles in seconds.  
- **Open Standards:** no gatekeepers — anyone can build interoperable healthcare apps on these rails.

---

## 🧪 Live Demos

| Module | Description | Demo |
|---|---|---|
| **Patient Web MVP** | Encrypts and anchors patient FHIR records across L1/L2 | **[Launch Demo](https://patient-web-seven.vercel.app)** |
| **Claims Web (Admin + Provider Console)** | Providers submit claims, rules enforce coverage, payments auto-settle | **[Launch Demo](https://claims-web-q3ls.vercel.app)** |

![Patient Snapshot Flow](https://raw.githubusercontent.com/Prometheus-chains/.github/main/media/patient-demo.gif)
![Claims Portal](https://raw.githubusercontent.com/Prometheus-chains/.github/main/media/claims-portal.gif)

---

## 🔗 Deployed Contracts

### Ethereum (Sepolia L1 — chainId `11155111`)
| Contract | Address | Description |
|---|---|---|
| **PatientRecordFactory** | [`0x5422907680cEa48620F9890AD7d664eB44F355a1`](https://sepolia.etherscan.io/address/0x5422907680cEa48620F9890AD7d664eB44F355a1) | Deploys one `PatientRecord` per wallet. |
| **PatientRecord** (example) | [`0x26A9c953999027501DD12CC5d1025471147E4cc9`](https://sepolia.etherscan.io/address/0x26A9c953999027501DD12CC5d1025471147E4cc9) | Anchors ordered **SHA-256 hashes of canonical (plaintext) FHIR records** (integrity & ordering only; **no PHI**). |

### Base (Sepolia L2 — chainId `84532`)
| Contract | Address | Description |
|---|---|---|
| **EEVault (Encrypted Event Vault)** | [`0x85f60DF7369578da188c23dD6a7D6D49C056254b`](https://sepolia.basescan.org/address/0x85f60DF7369578da188c23dD6a7D6D49C056254b) | Stores **AES-GCM ciphertext by a secret 16-byte tag**. Returns `envelopeId = keccak256(ciphertext)` for content-addressing. (Storage & private lookup; **no plaintext**.) |
| **ClaimEngine** | [`0xadda43C437Bb9A740a4D5972e0432e529a08DA7F`](https://sepolia.basescan.org/address/0xadda43C437Bb9A740a4D5972e0432e529a08DA7F) | Validates provider claims and executes instant payouts via `Bank`. |
| **ProviderRegistry** | [`0xa6B53A9A35c70a097666f5C9A31B1f9E9b66A728`](https://sepolia.basescan.org/address/0xa6B53A9A35c70a097666f5C9A31B1f9E9b66A728) | Whitelist of providers and active-year windows. |
| **Enrollment** | [`0xf867c7bC6F1D21700Ac4aEEa47F2AD0d6d86e3DC`](https://sepolia.basescan.org/address/0xf867c7bC6F1D21700Ac4aEEa47F2AD0d6d86e3DC) | Patient coverage registry. |
| **Rules** | [`0xDfB1093B0b4a7B518ecf6904fA9388D55f6a0503`](https://sepolia.basescan.org/address/0xDfB1093B0b4a7B518ecf6904fA9388D55f6a0503) | Price & per-year rules for codes (e.g., telehealth, annual). |
| **Bank (USDC Vault)** | [`0x313AB0d2Bc8e03a7011a34CeBfe3eE26EF518e0b`](https://sepolia.basescan.org/address/0x313AB0d2Bc8e03a7011a34CeBfe3eE26EF518e0b) | Holds USDC and executes instant claim payouts. |

---

## 🧱 Repositories

- **[protocol-medrec](https://github.com/Prometheus-chains/protocol-medrec)** – Solidity contracts for patient-owned records (PatientRecord + EEVault interface).  
- **[protocol-claims](https://github.com/Prometheus-chains/protocol-claims)** – Solidity contracts for instant claim adjudication and settlement.  
- **[patient-web](https://github.com/Prometheus-chains/patient-web)** – MetaMask MVP for anchoring & restoring encrypted records.  
- **[claims-web](https://github.com/Prometheus-chains/claims-web)** – Admin + Provider portal for live claim submissions and payments.  
- **[standards](https://github.com/Prometheus-chains/standards)** – Canonicalization (stable stringify), vault tags, and claims data specs.

---

## 🧩 How the rails fit together (short)

- **L1 (Ethereum)** — Append-only **PatientRecord**: write only `seq` + `contentHash = sha256(canonical FHIR JSON)`.  
- **L2 (Base)** — **EEVault** stores **ciphertext** by a **secret tag** (16 bytes). `envelopeId = keccak256(ciphertext)` enables content-addressing without plaintext.  
- **Device** — Derives `{tag, key, nonce}` from a one-time **EIP-712** signature + `(recordAddr, index)`; encrypts with **AES-256-GCM**; decrypts and verifies `sha256(pt) == contentHashAt(i)` during restore.  
- **Claims (L2)** — Provider submits `(patientId: bytes32, code, year)` → `ClaimEngine` checks **ProviderRegistry**, **Enrollment**, and **Rules** → pays via **Bank** or emits a **reasoned rejection** (e.g., “bank underfunded”, “max per year reached”). No per-claim patient identity stored on-chain.

---

## 💡 Impact

Modern healthcare is built on **two broken pillars** — data and payments.

Clinical data is trapped in silos, making every connection fragile. Patients see fragments of their own history spread across incompatible EMRs. Providers spend hours faxing records and reconciling mismatched charts. Innovators face gatekeepers at every API door.

Payments are just as fractured. Claims take weeks to settle, eligibility rules are hidden behind clearinghouses, and billions are wasted each year on manual coding and denials. Every inefficiency in healthcare traces back to one of these two foundations — **who holds the data, and who controls the money.**

**Prometheus Chains** rebuilds those foundations onchain:  
- **Data:** patient-owned medical records anchored on Ethereum for integrity and encrypted on Base for privacy.  
- **Payments:** claims processed by transparent, programmable contracts that enforce rules and settle instantly in USDC.  

Once the rails for data and payments exist as open, credibly neutral infrastructure, everything else in healthcare — from AI diagnostics to care coordination and research — becomes possible.  

Prometheus Chains turns Ethereum and Base into the **trust layer for medicine**, enabling interoperability, transparency, and automation at a human scale.

---

## 📬 Contact

- Security issues → **info@prometheuschains.org**  
- Discussions → **[Open Discussion](https://github.com/orgs/Prometheus-chains/discussions)**  
- Contributions → look for `good first issue` tags across repos

---

## 🧾 License

**Apache-2.0** — open-source public good.
