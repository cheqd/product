# ✅ cheqd Toolbox: Integrate with cheqd

cheqd has created simple tooling to enable third parties to create DIDs and resources, issue and verify Verifiable Credentials, using cheqd DIDs, DID Documents and Schemas.

This will be useful for:

| User                      | Capability                                                                                                        |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **SSI vendor**            | I want to integrate cheqd into my identity applications and help determine the technical direction of the network |
| **Client / End customer** | I want to use cheqd Network and a software integration to develop an SSI use case                                 |
| **Web 3.0 vendor**        | I want to integrate identity functionality into my own Web 3.0 ecosystem                                          |

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

## Contents

{% content-ref url="veramo-sdk.md" %}
[veramo-sdk.md](veramo-sdk.md)
{% endcontent-ref %}

{% content-ref url="anoncreds-on-cheqd/aries-framework-javascript-for-cheqd.md" %}
[aries-framework-javascript-for-cheqd.md](anoncreds-on-cheqd/aries-framework-javascript-for-cheqd.md)
{% endcontent-ref %}

{% content-ref url="resolve-cheqd-dids-and-resources.md" %}
[resolve-cheqd-dids-and-resources.md](resolve-cheqd-dids-and-resources.md)
{% endcontent-ref %}
