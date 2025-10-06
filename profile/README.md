# 🧬 Prometheus Chains

**Credibly neutral healthcare rails on Ethereum and Base.**

Prometheus Chains is an open protocol for healthcare that brings **patient-owned data** and **instant claim payments** onchain.  
- **Patient Records:** anchored on Ethereum L1 for integrity, encrypted on Base L2 for privacy.  
- **Claims & Payments:** providers submit claims, rules enforce coverage, and USDC settles in seconds.  
- **Open Standards:** no gatekeepers — anyone can build interoperable healthcare apps on these rails.

---

## 🧪 Live Demos

| Module | Description | Demo |
|---------|--------------|------|
| **Patient Web MVP** | Encrypts and anchors patient FHIR records across L1/L2 | [🔗 Launch Demo](https://patient-web-seven.vercel.app) |
| **Claims Web (Admin + Provider Console)** | Providers submit claims, rules enforce coverage, payments auto-settle | [🔗 Launch Demo](https://claims-web-q3ls.vercel.app) |

![Patient Snapshot Flow](https://raw.githubusercontent.com/Prometheus-chains/.github/main/media/patient-demo.gif)
![Claims Portal](https://raw.githubusercontent.com/Prometheus-chains/.github/main/media/claims-portal.gif)

---

## 🔗 Deployed Contracts

### Ethereum (Sepolia L1 — chainId `11155111`)
| Contract | Address | Description |
|-----------|----------|--------------|
| **PatientRecordFactory** | [`0x5422907680cEa48620F9890AD7d664eB44F355a1`](https://sepolia.etherscan.io/address/0x5422907680cEa48620F9890AD7d664eB44F355a1) | Deploys one `PatientRecord` per wallet |
| **PatientRecord** (example) | [`0x26A9c953999027501DD12CC5d1025471147E4cc9`](https://sepolia.etherscan.io/address/0x26A9c953999027501DD12CC5d1025471147E4cc9) | Anchors ordered hashes of canonical FHIR records |

### Base (Sepolia L2 — chainId `84532`)
| Contract | Address | Description |
|-----------|----------|--------------|
| **EventVaultHashOnly** | [`0x85f60DF7369578da188c23dD6a7D6D49C056254b`](https://sepolia.basescan.org/address/0x85f60DF7369578da188c23dD6a7D6D49C056254b) | Stores encrypted patient data by content hash |
| **ClaimEngine** | [`0x6a327849Ea8F7f8C7B09bA71A4492c5a8F9581D4`](https://sepolia.basescan.org/address/0x6a327849Ea8F7f8C7B09bA71A4492c5a8F9581D4) | Validates provider claims and pays via Bank |
| **ProviderRegistry** | [`0x8D1E64BbE7D7Faf5cE9E2A34CE5a8A86aF54b0d5`](https://sepolia.basescan.org/address/0x8D1E64BbE7D7Faf5cE9E2A34CE5a8A86aF54b0d5) | Whitelist of providers and active-year windows |
| **Enrollment** | [`0x0bD02E5438E85F8A25E6f60447f16F2F9113Bb41`](https://sepolia.basescan.org/address/0x0bD02E5438E85F8A25E6f60447f16F2F9113Bb41) | Patient coverage registry |
| **Rules** | [`0xBd46cE7E5f75Ea679cA5E9266d9121b2E6dC67C2`](https://sepolia.basescan.org/address/0xBd46cE7E5f75Ea679cA5E9266d9121b2E6dC67C2) | Price & per-year rules for codes (telehealth, annual) |
| **Bank (USDC Vault)** | [`0x5eAa6cAEB5c36E16fE6cE83b72fF6Da15AB21F88`](https://sepolia.basescan.org/address/0x5eAa6cAEB5c36E16fE6cE83b72fF6Da15AB21F88) | Holds USDC and executes instant claim payouts |

---

## 🧱 Repositories

- [**protocol-medrec**](https://github.com/Prometheus-chains/protocol-medrec) – Solidity contracts for patient-owned records (PatientRecord + Vault).  
- [**protocol-claims**](https://github.com/Prometheus-chains/protocol-claims) – Solidity contracts for instant claim adjudication and settlement.  
- [**patient-web**](https://github.com/Prometheus-chains/patient-web) – MetaMask MVP for anchoring & restoring encrypted records.  
- [**claims-web**](https://github.com/Prometheus-chains/claims-web) – Admin + Provider portal for live claim submissions and payments.  
- [**standards**](https://github.com/Prometheus-chains/standards) – Canonicalization, vault tag, and claims data specs.

---

## 💡 Impact

**Bringing healthcare data and payments onchain — the first patient-owned record & claims systembuilt on Base.**

By making healthcare infrastructure credibly neutral, Prometheus Chains turns Ethereum and Base into the **trust layer for medicine itself** — enabling interoperability, transparency, and automation at a human scale.

---

## 📬 Contact

- Security issues → **info@prometheuschains.org**  
- Discussions → [Open Discussion](https://github.com/orgs/Prometheus-chains/discussions)  
- Contributions → look for `good first issue` tags in our repos  

---

### 🧩 License

Apache 2.0 — open-source public good.
