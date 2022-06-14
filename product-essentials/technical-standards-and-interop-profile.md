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
| Command Line Interface (CLI)                     | cheqd Cosmos CLI                                                                | [https://docs.cheqd.io/node/docs/cheqd-cli](https://docs.cheqd.io/node/docs/cheqd-cli)                                                                                                                              |
| Command Line Interface (CLI)                     | VDR Tools                                                                       | [https://docs.cheqd.io/node/docs/identity-api](https://docs.cheqd.io/node/docs/identity-api)                                                                                                                        |

### Using Verifiable Credentials with cheqd in different SDKs

| Component                       | Type                                                                             | Link                                                                                       |
| ------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Software Development Kit Module | Hyperledger Aries based SDK for AnonCreds-like Credentials supporting cheqd DIDs | Research                                                                                   |
| Software Development Kit Module | Veramo SDK for JSON/JWT and JSON-LD supporting cheqd DIDs                        | [https://github.com/cheqd/did-provider-cheqd](https://github.com/cheqd/did-provider-cheqd) |
| Software Development Kit Module | SDK supporting cheqd DIDs with JSON-LD BBS+                                      | Backlog                                                                                    |



### Using cheqd with Veramo

| Component                          | Type                         | Link                                                                                                                                                                                                                |
| ---------------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Software Development Kit (SDK)     | Veramo SDK with cheqd plugin | [https://veramo.io/](https://veramo.io/)                                                                                                                                                                            |
| Verifiable Credential Type/Flavour | JSON                         | [Verifiable Credentials Data Model v1.1](https://www.w3.org/TR/vc-data-model/)                                                                                                                                      |
| Verifiable Credential Type/Flavour | JSON-LD                      | [Verifiable Credentials Data Model v1.1](https://www.w3.org/TR/vc-data-model/)                                                                                                                                      |
| Peer-to-peer connection layer      | DIDComm v2.0                 | [https://identity.foundation/didcomm-messaging/spec/](https://identity.foundation/didcomm-messaging/spec/)                                                                                                          |
| DID Method                         | cheqd DID method             | [https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:\~:text=Summary,on%20the%20Cosmos%20blockchain%20framework.](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method) |
| Command Line Interface (CLI)       | Veramo CLI                   | In development                                                                                                                                                                                                      |
| Verifiable Presentation Exchange   | DIF Presentation Exchange    | [https://identity.foundation/presentation-exchange/](https://identity.foundation/presentation-exchange/)                                                                                                            |
| Verifiable Presentation Request    | Selective Disclosure Request | [https://developer.uport.me/messages/sharereq](https://developer.uport.me/messages/sharereq)                                                                                                                        |

