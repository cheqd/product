# 🤓 Technical standards and interop profile

## DIDs and Resources on cheqd network

| Component                                        | Type                                                                            | Link                                                                                                                 |
| ------------------------------------------------ | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Layer 1 Utility / Verifiable Data Registry (VDR) | cheqd                                                                           | [cheqd block explorer](https://explorer.cheqd.io/)                                                                   |
| DID method                                       | cheqd DID method                                                                | [`did:cheqd` method ADR](https://docs.cheqd.io/identity/architecture/adr-list/adr-001-cheqd-did-method)                  |
| DID method standard                              | DID Core v1.0                                                                   | [Decentralized Identifiers (DIDs) v1.0](https://www.w3.org/TR/did-core/)                                             |
| DID resolver                                     | cheqd DID resolver                                                              | [cheqd/did-resolver](https://github.com/cheqd/did-resolver)                                              |
| Universal resolver driver                        | cheqd DID resolver                                                              | [Universal Resolver drivers](https://github.com/decentralized-identity/universal-resolver)                           |
| Schemas                                          | Schemas represented by DID URLs with DID Documents that dereference to a schema | See [ADR 002: On-ledger Resources](https://docs.cheqd.io/identity/architecture/adr-list/adr-002-did-linked-resources) |
| DID-Linked Resources                             | Resources able to be anchored on cheqd and linked to a DID URL                  | [Understanding on-ledger resurces](https://docs.cheqd.io/identity/guides/did-linked-resources)                                 |

## Using Verifiable Credentials with cheqd in different SDKs

| Component                              | Type                                                                                | Link                                                                                                                             |
| -------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Veramo SDK for cheqd                   | Software Development Kit for creating DIDs, Resources and issuing VCs in production | [cheqd/did-provider-cheqd](https://github.com/cheqd/did-provider-cheqd)                                                          |
| DID Provider cheqd                     | Veramo plugin to enable cheqd functionality                                         | [DID Provider cheqd](https://github.com/cheqd/did-provider-cheqd)                                                                |
| cheqd SDK                              | Tooling for communicating and interacting with cheqd network                        | [cheqd SDK](https://github.com/cheqd/sdk)                                                                                        |
| VDR tools SDK / CLI                    | Software Development Kit for creating DIDs                                          | [VDR Tools CLI](https://docs.cheqd.io/identity/advanced-features-and-alternatives/vdr-tools-with-cheqd)                          |
| cheqd Cosmos CLI                       | Software Development Kit for creating DIDs                                          | [cheqd Cosmos CLI for identity](https://docs.cheqd.io/identity/advanced-features-and-alternatives/cheqd-node-cli) |
| Hyperledger Aries Framework JavaScript | Hyperledger Aries based SDK for AnonCreds on cheqd                                  | In progress                                                                                                                      |
| Hyperledger Aries Cloud Agent Python   | SDK for AnonCreds on cheqd                                                          | In progress                                                                                                                      |
| Other                                  | SDK supporting cheqd DIDs with JSON-LD BBS+                                         | Backlog                                                                                                                          |

### Using cheqd with Veramo

| Component                          | Type                         | Link                                                                                                                                    |
| ---------------------------------- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Software Development Kit (SDK)     | Veramo SDK with cheqd plugin | [Setting up Veramo SDK for cheqd](https://docs.cheqd.io/identity/guides/software-development-kits-sdks/veramo-sdk-for-cheqd)            |
| Verifiable Credential Type/Flavour | JSON JWT                     | [Issue JSON JWT VCs](https://docs.cheqd.io/identity/tutorials/verifiable-credentials-and-presentations/verify-a-verifiable-credential/verify-jwt-vc) |
| Verifiable Credential Type/Flavour | JSON-LD                      | In development                                                                                                                          |
| Verifiable Credential Type/Flavour | AnonCreds                    | In development                                                                                                                          |
| Peer-to-peer connection layer      | DIDComm v2.0                 | [DIDComm Messaging specification](https://identity.foundation/didcomm-messaging/spec/)                                                  |
| DID Method                         | cheqd DID method             | [`did:cheqd` method ADR](https://docs.cheqd.io/identity/architecture/adr-list/adr-001-cheqd-did-method)                                     |
| Command Line Interface (CLI)       | Veramo CLI                   | [Setup Veramo CLI](https://docs.cheqd.io/identity/guides/sdk/veramo-sdk-for-cheqd/setup)                 |
| Verifiable Presentation Exchange   | DIF Presentation Exchange    | [Presentation Exchange specification](https://identity.foundation/presentation-exchange/)                                               |
