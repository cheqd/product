# 🔜 Now, next and future

## Creating & Managing DIDs on the cheqd network

### Creating DIDs

| Now (current functionality)                                                                                                                                                                                                | Next (Q2/Q3) | Future (Q3/Q4) |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | -------------- |
| [Create a DID](https://docs.cheqd.io/identity/tutorials/dids/vdr-tools/create-did-and-did-document)([did:cheqd method](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method)) with cheqd CLI |              |                |
| [Create a DID Document](https://docs.cheqd.io/identity/tutorials/dids/cheqd-cosmos-cli/create-did-and-did-document)with cheqd CLI                                                                         |              |                |

### Resolving (reading) DIDs

| Now (current functionality)                                                                                                                                                              | Next (Q2/Q3)                                                                                                                                       | Future (Q4) |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| [Resolve a DID](https://docs.cheqd.io/identity/tutorials/did-resolver/using-full-cheqd-did-resolver) with [Full cheqd DID Resolver](../../suite/identity-ledger/did-resolver.md) | [Resolve a DID with Proxy DID Resolver](https://docs.cheqd.io/identity/tutorials/did-resolver/using-light-cheqd-did-resolver) (Cloudflare workers) |             |
|                                                                                                                                                                                          | Resolve a DID with the [Universal Resolver (Docker)](https://dev.uniresolver.io/)                                                                  |             |

### Issuing and managing Verifiable Credentials on the cheqd network

#### JSON /JSON-LD Verifiable Credentials

| Now (current functionality)                                                  | Next (Q2/Q3)                                                                                   | Future (Q4)                                                                                                                                         |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Issue and verify JSON based JWT credentials\* with Veramo SDK using CLI      | Issue and verify [JSON-LD](https://github.com/cheqd/identity-docs) credential using Veramo SDK | Create entry in [Revocation Registry](../../suite/identity-ledger/revocation-registry.md)                                    |
| Hold JWT/JSON Verifiable Credentials in web-app Wallet                       |                                                                                                | Manage credential revocation status using [cheqd Revocation Registry](https://docs.cheqd.io/node/architecture/adr-list/adr-007-revocation-registry) |
| _\*Schema and revocation registry through Schema.org and RevocationList2020_ | _\*Schemas through on-ledger Schemas referenced within Schemas DID Document_                   |                                                                                                                                                     |

#### AnonCreds

| Now (current functionality) | Next (Q2/Q3)                                                                                                                                        | Future (Q4)                                                                                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
|                             | [Issue AnonCred approved credential](https://docs.cheqd.io/node/architecture/adr-list/adr-008-identity-resources)referencing Schema DID Document   | Create entry in [Revocation Registry](../../suite/identity-ledger/revocation-registry.md)                                    |
|                             | [Create a Schema DID Document](https://docs.cheqd.io/node/architecture/adr-list/adr-008-identity-resources)with CLI for AnonCreds                  | Manage credential revocation status using [cheqd Revocation Registry](https://docs.cheqd.io/node/architecture/adr-list/adr-007-revocation-registry) |
|                             | [Create Schema objects on Ledger](https://docs.cheqd.io/node/architecture/adr-list/adr-008-identity-resources)(e.g. type: CL-Schema) for AnonCreds |                                                                                                                                                     |
|                             | [Dereference DID URL to fetch schemas & resources](https://docs.cheqd.io/node/architecture/adr-list/adr-008-identity-resources) for AnonCreds       |                                                                                                                                                     |

## CHEQ Token & Payment Rails

| Now (current functionality)                                                               | Next (Q2/Q3) | Future (Q4)                                                                                                                                                                               |
| ----------------------------------------------------------------------------------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Hold and send CHEQ tokens](https://wallet.cheqd.io/welcome)                              |              | [Verifier-to-issuer](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Verifier pay issuer for credential presentation with CHEQ token (settled in stablecoin) |
| [Stake CHEQ tokens](https://wallet.cheqd.io/staking)as a validator                       |              | [Verifier-to-holder](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Verifier pay holder for credential presentation with CHEQ token (settled in stablecoin) |
| [Delegate CHEQ tokens](https://wallet.cheqd.io/staking) to a validator to stake           |              | [Holder-to-issuer](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Holder pay issuer for credential issuance with CHEQ token (settled in stablecoin)         |
| [Vote on governance proposals](https://commonwealth.im/cheqd/proposals) using CHEQ tokens |              |                                                                                                                                                                                           |
