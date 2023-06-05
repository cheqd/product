# 🧰 Build products on cheqd

## Integrate with cheqd

cheqd has created simple tooling to enable third parties to create DIDs and resources, issue and verify Verifiable Credentials, using cheqd DIDs, DID Documents and Schemas.

## Choose a software stack to suit your needs

cheqd is continually integrating into different software development kits to suit the needs of different partners and their clients.

Below is a comparison between our two initial supported SDKs, Veramo SDK for cheqd and Aries Framework JavaScript SDK for cheqd.

| Functionality                                                                                                                                            | Veramo SDK for cheqd | Aries Framework JavaScript for cheqd | Walt.id SSI Kit |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------: | :----------------------------------: | :-------------: |
| **Create cheqd DIDs**                                                                                                                                    |          ✔️          |                  ✔️                  |        ✔️       |
| **JSON based JWT Verifiable Credential**                                                                                                                 |          ✔️          |                   ❌                  |        ✔️       |
| **JSON-LD Verifiable Credential**                                                                                                                        |          ✔️          |              ⌛(roadmap)              |        ✔️       |
| **AnonCreds (ZKP-CL)**                                                                                                                                   |           ❌          |                  ✔️                  |        ❌        |
| **Selective Disclosure-JWT Credential**                                                                                                                  |      ⌛(roadmap)      |                   ❌                  |    ⌛(roadmap)   |
| **Create on-ledger Schema**                                                                                                                              |          ✔️          |                  ✔️                  |        ❌        |
| **Create Credential Definition**                                                                                                                         |           ❌          |                  ✔️                  |        ❌        |
| **DIDComm v1.0**                                                                                                                                         |          ✔️          |                  ✔️                  |        ❌        |
| **DIDComm v2.0**                                                                                                                                         |          ✔️          |                  ✔️                  |        ❌        |
| **DID Exchange Protocol (**[**RFC 0023**](https://github.com/hyperledger/aries-rfcs/tree/main/features/0023-did-exchange)**)**                           |           ❌          |                  ✔️                  |        ❌        |
| **Agent Connection Protocol (**[**RFC 0160**](https://github.com/hyperledger/aries-rfcs/blob/main/features/0160-connection-protocol/README.md)**)**      |           ❌          |                  ✔️                  |        ❌        |
| **Basic Message Protocol**                                                                                                                               |           ❌          |                  ✔️                  |        ❌        |
| **Out of Band Protocol (**[**RFC 0434**](https://github.com/hyperledger/aries-rfcs/blob/main/features/0434-outofband/README.md)**)**                     |           ❌          |                  ✔️                  |        ❌        |
| **Self Issued OpenID Provider v2 (OIDC-SIOP)**                                                                                                           |      ⌛(roadmap)      |                   ❌                  |        ✔️       |
| **OpenID for Verifiable Credential Issuance**                                                                                                            |      ⌛(roadmap)      |              ⌛(roadmap)              |        ✔️       |
| **OpenID for Verifiable Credential Presentations**                                                                                                       |      ⌛(roadmap)      |              ⌛(roadmap)              |        ✔️       |
| **AnonCreds (ZKP-CL)**                                                                                                                                   |           ❌          |                  ✔️                  |        ❌        |
| **Status List 2021 Revocation**                                                                                                                          |          ✔️          |                   ❌                  |        ✔️       |
| **AnonCreds Revocation Registry Definitions**                                                                                                            |           ❌          |                  ✔️                  |        ❌        |
| **AnonCreds Status List Entries**                                                                                                                        |           ❌          |                  ✔️                  |        ❌        |
| **Issue Credential Protocol (**[**RFC 0036**](https://github.com/hyperledger/aries-rfcs/blob/master/features/0036-issue-credential/README.md)**)**       |           ❌          |                  ✔️                  |        ❌        |
| **Issue Credential Protocol V2 (**[**RFC 0453**](https://github.com/hyperledger/aries-rfcs/blob/master/features/0453-issue-credential-v2/README.md)**)** |           ❌          |                  ✔️                  |        ❌        |
| **DIF Presentation Exchange**                                                                                                                            |          ✔️          |                   ❌                  |        ✔️       |
| **Aries Present Proof**                                                                                                                                  |           ❌          |                  ✔️                  |        ❌        |
| **DID-Linked Trust Registries**                                                                                                                          |      ⌛(roadmap)      |                   ❌                  |        ❌        |
