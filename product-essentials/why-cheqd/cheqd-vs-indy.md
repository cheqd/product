# ⚖ Benchmarking cheqd vs. Hyperledger Indy

| Functionality                                                                           |                      cheqd                     |         Hyperledger Indy        |
| --------------------------------------------------------------------------------------- | :--------------------------------------------: | :-----------------------------: |
| **Transactions per second**                                                             |                     >5,000                     |                4                |
| **Maximum number of nodes**                                                             |                      \~125                     |               \~25              |
| **Active nodes**                                                                        |                      \~55                      |               \~17              |
| **Transactions per block**                                                              |                      >100                      |                1                |
| **Node operator rewards**                                                               |           Block rewards paid in CHEQ           |               None              |
| **Governance mechanism**                                                                | Delegated proof of stake (dPoS) via CHEQ token |   Centralized via trustee vote  |
| **Governance Transparency**                                                             | Public permissionless via Governance dashboard |  Permissioned via trustee vote  |
| **Governance Framework**                                                                |   On-ledger Governance Framework via DID URL   | Off-ledger Governance Framework |
| **JSON based JWT Verifiable Credentials**                                               |                       ✔️                       |                ❌                |
| **JSON-LD Verifiable Credentials**                                                      |                ⌛(next 2 months)                |                ❌                |
| **JSON-LD BBS+ signatures**                                                             |                   ⌛(roadmap)                   |                ❌                |
| **AnonCreds (ZKP-CL)**                                                                  |                       ✔️                       |                ✔️               |
| **DID method**                                                                          |                    did:cheqd                   |             did:indy            |
| **DID Core compliant DIDDocs**                                                          |                       ✔️                       |                ✔️               |
| **Resolve DID with DID resolver**                                                       |                       ✔️                       |                ✔️               |
| **Dereference DID URL**                                                                 |                       ✔️                       |                ✔️               |
| **Multiple DID Controllers per DIDDoc**                                                 |                       ✔️                       |                ❌                |
| **Verification relationships with specific keys for a particular verification purpose** |                       ✔️                       |                ❌                |
| **Support Aries Framework JavaScript**  |                       ✔️                       |                ✔️               |
| **Support: Aries Framework.NET**                                                        |                   ⌛(roadmap)                   |                ✔️               |
| **Support: ACA-Py**                                                                     |                ⌛(next 2 months)                |                ✔️               |
| **Support: Aries Framework Go**                                                         |                   ⌛(roadmap)                   |                ✔️               |
| **Support: Veramo SDK**                                                                 |                       ✔️                       |                ❌                |
| **Support: Other JSON/JSON-LD SDKs**                                                    |                   ⌛(roadmap)                   |                ❌                |
| **On-ledger Schemas**                                                                   |                       ✔️                       |                ✔️               |
| **Credential Definitions**                                                              |                       ✔️                       |                ✔️               |
| **AnonCreds Revocation Registry Definitions**                                           |                       ✔️                       |                ✔️               |
| **AnonCreds Revocation Registry Entries**                                               |                       ✔️                       |                ✔️               |
| **Status List 2021**                                                                    |                ⌛(next 2 months)                |                ❌                |
| **Trust Registry Definitions**                                                          |                   ⌛(roadmap)                   |                ❌                |
| **Trust Registry Entries**                                                              |                   ⌛(roadmap)                   |                ❌                |
| **Other assets (images, docs, policies)**                                               |                       ✔️                       |                ❌                |
| **Payments for Verifiable Credentials**                                                 |                   ⌛(roadmap)                   |                ❌                |
