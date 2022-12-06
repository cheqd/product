# ✅ cheqd Toolbox

## Summary

cheqd has created simple tooling to enable third parties to create DIDs and resources, issue and verify Verifiable Credentials, using cheqd DIDs, DID Documents and Schemas.

This will be useful for:

| User                      | Capability                                                                                                        |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **SSI vendor**            | I want to integrate cheqd into my identity applications and help determine the technical direction of the network |
| **Client / End customer** | I want to use cheqd Network and a software integration to develop an SSI use case                                 |
| **Web 3.0 vendor**        | I want to integrate identity functionality into my own Web 3.0 ecosystem                                          |

## Contents

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><strong>Veramo SDK for cheqd</strong></td><td>Integrate with our enterprise-ready SDK for creating and managing DIDs, DID-Linked Resources and Verifiable Credentials</td><td></td><td><a href="veramo-sdk.md">veramo-sdk.md</a></td><td><a href="../../.gitbook/assets/Veramo SDK for cheqd.jpg">Veramo SDK for cheqd.jpg</a></td></tr><tr><td><strong>AnonCreds on cheqd</strong></td><td>Understand how cheqd supports AnonCreds natively on-ledger and in supported SDKs</td><td></td><td><a href="anoncreds-on-cheqd/">anoncreds-on-cheqd</a></td><td><a href="../../.gitbook/assets/AnonCreds on cheqd.jpg">AnonCreds on cheqd.jpg</a></td></tr><tr><td><strong>Resolve cheqd DIDs and Resources</strong></td><td>Understand how cheqd's DID resolver is set up for trusting DIDs and DID-Linked Resources, and how to run an instance.</td><td></td><td><a href="resolve-cheqd-dids-and-resources.md">resolve-cheqd-dids-and-resources.md</a></td><td><a href="../../.gitbook/assets/identifier for business.jpg">identifier for business.jpg</a></td></tr><tr><td><strong>cheqd web-app wallet</strong></td><td>Try out or spin up our demo web-app wallet and get your first Verifiable Credential</td><td></td><td><a href="cheqd-web-app-wallet/">cheqd-web-app-wallet</a></td><td><a href="../../.gitbook/assets/cheqd wallet.png">cheqd wallet.png</a></td></tr></tbody></table>

## Choose a software stack to suit your needs

cheqd is continually integrating into different software development kits to suit the needs of different partners and their clients.

Below is a comparison between our two initial supported SDKs, Veramo SDK for cheqd and Aries Framework JavaScript SDK for cheqd.&#x20;

| Functionality                                                                                                                                            | Veramo SDK for cheqd | Aries Framework JavaScript for cheqd |
| -------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------: | :----------------------------------: |
| **Create cheqd DIDs**                                                                                                                                    |          ✔️          |                  ✔️                  |
| **Create on-ledger Schema**                                                                                                                              |          ✔️          |                  ✔️                  |
| **Create on-ledger Credential Definition**                                                                                                               |          ✔️          |                  ✔️                  |
| **Create on-ledger Governance documentation**                                                                                                            |          ✔️          |                  ✔️                  |
| **DIDComm v2.0**                                                                                                                                         |          ✔️          |                  ✔️                  |
| **DID Exchange Protocol (**[**RFC 0023**](https://github.com/hyperledger/aries-rfcs/tree/main/features/0023-did-exchange)**)**                           |           ❌          |                  ✔️                  |
| **Agent Connection Protocol (**[**RFC 0160**](https://github.com/hyperledger/aries-rfcs/blob/main/features/0160-connection-protocol/README.md)**)**      |           ❌          |                  ✔️                  |
| **Basic Message Protocol**                                                                                                                               |           ❌          |                  ✔️                  |
| **Out of Band Protocol (**[**RFC 0434**](https://github.com/hyperledger/aries-rfcs/blob/main/features/0434-outofband/README.md)**)**                     |           ❌          |                  ✔️                  |
| **Self Issued OpenID Provider v2 (OIDC-SIOP)**                                                                                                           |      ⌛(roadmap)      |                   ❌                  |
| **JSON based JWT Verifiable Credential**                                                                                                                 |          ✔️          |                   ❌                  |
| **JSON-LD Verifiable Credential**                                                                                                                        |      ⌛(roadmap)      |                   ❌                  |
| **AnonCreds (ZKP-CL)**                                                                                                                                   |           ❌          |                  ✔️                  |
| **JSON-LD BBS+ Verifiable Credential**                                                                                                                   |      ⌛(roadmap)      |              ⌛(roadmap)              |
| **Status List 2021 Revocation**                                                                                                                          |          ✔️          |                   ❌                  |
| **AnonCreds Revocation Registry Definitions**                                                                                                            |           ❌          |                  ✔️                  |
| **AnonCreds Revocation Registry Entries**                                                                                                                |           ❌          |                  ✔️                  |
| **Issue Credential Protocol (**[**RFC 0036**](https://github.com/hyperledger/aries-rfcs/blob/master/features/0036-issue-credential/README.md)**)**       |           ❌          |                  ✔️                  |
| **Issue Credential Protocol V2 (**[**RFC 0453**](https://github.com/hyperledger/aries-rfcs/blob/master/features/0453-issue-credential-v2/README.md)**)** |           ❌          |                  ✔️                  |
| **DIF Presentation Exchange**                                                                                                                            |          ✔️          |                   ❌                  |
| **Aries Present Proof**                                                                                                                                  |           ❌          |                  ✔️                  |

