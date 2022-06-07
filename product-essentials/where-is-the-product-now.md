# 🗳 Where is the Product now?

### Publish to the cheqd Network

| Now                                      | Next                                                   | Future                                                              |
| ---------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------- |
| Create a DID (did:cheqd method) with CLI | Create Schema objects on Ledger (e.g. type: CL-Schema) | Create entry in Revocation Registry                                 |
| Create a DID Document with CLI           | Mimic CredDef functionality with DID Docs + Schema     | Manage credential revocation status using cheqd Revocation Registry |
|                                          | Create a Schema DID Document with CLI                  |                                                                     |

### Leverage the cheqd Network

| Now                                                                | Next                                                                | Future                                     |
| ------------------------------------------------------------------ | ------------------------------------------------------------------- | ------------------------------------------ |
| Issue and verify JWT/JSON Verifiable Credentials with Veramo SDK   | Issue and verify JSON-LD credential using Veramo SDK                | Setup payment flow from verifier to issuer |
| Interact with network with web-app Wallet (+ hold JSON credential) | Issue and verify AnonCreds-like credential on-ledger with cheqd SDK | Setup payment flow from verifier to holder |
|                                                                    | Use Interop SDK to route credentials to appropriate SDK             | Setup payment flow from holder to issuer   |

### Resolve on the cheqd network

| Now                                        | Next                                                       | Future                                           |
| ------------------------------------------ | ---------------------------------------------------------- | ------------------------------------------------ |
| Resolve a DID with Full cheqd DID Resolver | Resolve a DID with Proxy DID Resolver (Cloudflare workers) | Dereference DID URL to fetch Revocation Registry |
|                                            | Resolve a DID with the Universal Resolver (Docker)         |                                                  |
|                                            | Dereference DID URL to fetch schemas                       |                                                  |
|                                            | Dereference DID URL to fetch resources                     |                                                  |
