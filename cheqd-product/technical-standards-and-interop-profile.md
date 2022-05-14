# 🤓 Technical standards and interop profile

### Supported technical stack (cheqd Network)

| Component                                        | Type                                                                            | Link                                                                                                                                                                                                                |
| ------------------------------------------------ | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Layer 1 Utility / Verifiable Data Registry (VDR) | cheqd                                                                           | [https://www.cheqd.io/](https://www.cheqd.io/)                                                                                                                                                                      |
| DID method                                       | cheqd DID method                                                                | [https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:\~:text=Summary,on%20the%20Cosmos%20blockchain%20framework.](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method) |
| DID method standard                              | DID Core v1.0                                                                   | [Decentralized Identifiers (DIDs) v1.0](https://www.w3.org/TR/did-core/)                                                                                                                                            |
| DID resolver                                     | cheqd DID resolver                                                              | [https://github.com/cheqd/cheqd-did-resolver](https://github.com/cheqd/cheqd-did-resolver)                                                                                                                          |
| Universal resolver driver                        | cheqd DID resolver                                                              | Pending                                                                                                                                                                                                             |
| Schemas                                          | Schemas represented by DID URLs with DID Documents that dereference to a schema | [https://github.com/cheqd/cheqd-node/blob/main/architecture/adr-list/adr-008-identity-resources.md](https://github.com/cheqd/cheqd-node/blob/main/architecture/adr-list/adr-008-identity-resources.md)              |

### Supported technical stack (Software Development Kit 'SDK')

| Component                          | Type                                       | Link                                                                                                                                                                                                                |
| ---------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Software Development Kit (SDK)     | Veramo SDK with cheqd plugin               | [https://veramo.io/](https://veramo.io/)                                                                                                                                                                            |
| Verifiable Credential Type/Flavour | JSON                                       | [Verifiable Credentials Data Model v1.1](https://www.w3.org/TR/vc-data-model/)                                                                                                                                      |
| Verifiable Credential Type/Flavour | JSON-LD                                    | Pending                                                                                                                                                                                                             |
| Peer-to-peer connection layer      | DIDComm v2.0                               | [https://identity.foundation/didcomm-messaging/spec/](https://identity.foundation/didcomm-messaging/spec/)                                                                                                          |
| DID Method                         | cheqd DID method as a plugin within Veramo | [https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:\~:text=Summary,on%20the%20Cosmos%20blockchain%20framework.](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method) |
| Verifiable Presentation Exchange   | DIF Presentation Exchange                  | [https://identity.foundation/presentation-exchange/](https://identity.foundation/presentation-exchange/)                                                                                                            |
| Verifiable Presentation Request    | Selective Disclosure Request               | [https://developer.uport.me/messages/sharereq](https://developer.uport.me/messages/sharereq)                                                                                                                        |

### Upcoming cheqd SDK support

cheqd intends to create an API routing service to multiple SDK modules, which will include support for AnonCreds, AnonCreds compatible Credentials on cheqd as well as JSON/JSON-LD Credentials on cheqd.&#x20;

The intention is to create one SDK which enables verification of multiple different Verifiable Credential types and flavours. Through this architecture, cheqd intends to maximise interoperability for its partners and their end customers.

We refer to this architecture as a Unified cheqd SDK.

![](<../.gitbook/assets/SDK of SDKs.drawio.png>)

| Component                          | Type                                     | Link                                                                                                         |
| ---------------------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Software Development Kit Module    | Hyperledger Aries based SDK (AFJ, AFG)   | In progress                                                                                                  |
| Software Development Kit Module    | cheqd SDK for AnonCreds-like Credentials | In Progress                                                                                                  |
| Verifiable Credential Type/Flavour | AnonCreds v1.0                           | [https://github.com/AnonCreds-WG/anoncreds-spec](https://github.com/AnonCreds-WG/anoncreds-spec)             |
| Verifiable Credential Type         | JSON-LD BBS+                             | [https://github.com/mattrglobal/jsonld-signatures-bbs](https://github.com/mattrglobal/jsonld-signatures-bbs) |
