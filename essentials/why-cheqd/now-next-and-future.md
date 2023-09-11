# 🚀 What can I do now on cheqd?

## Creating & Managing DIDs on the cheqd network

### Decentralised Identifiers (DIDs)

| Now (current functionality)                                                                                                                                                                | Next (Q4)                                    | Future |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------- | ------ |
| [Create a DID](https://docs.cheqd.io/identity/tutorials/did-operations/create-did) and DID Document with Veramo SDK for cheqd                         | Deactivate a DID with Veramo SDK for cheqd   |        |
| [Create an off-ledger 'subject' DID](https://docs.cheqd.io/identity/tutorials/did-operations/create-subject-did) with Veramo SDK for cheqd | Integrate cheqd into the Universal Registrar |        |
| [Manage/update a DID](https://docs.cheqd.io/identity/tutorials/did-operations/update-did) with Veramo SDK for cheqd                        |                                              |        |

### Resolving (reading) DIDs

| Now (current functionality)                                                       | Next (Q4)                                                  | Future |
| --------------------------------------------------------------------------------- | ---------------------------------------------------------- | ------ |
| Resolve a DID with Full cheqd DID Resolver                                        | Resolve a DID with Proxy DID Resolver (Cloudflare workers) |        |
| Resolve a DID with the [Universal Resolver (Docker)](https://dev.uniresolver.io/) | Integrate cheqd Resources into the Universal Resolver      |        |

### On-ledger resources

| Now (current functionality)                                                                                                                                                                                   | Next (Q4)                                                                                                                               | Future                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| [Create AnonCreds schema](https://docs.cheqd.io/identity/guides/anoncreds/schema) using resource module                                                 | Create a Status List 2021 Resource                                                                                                      | Create a Trust Registry Resource                          |
| [Create AnonCreds CredDef](https://docs.cheqd.io/identity/guides/anoncreds/credential-definition) using resource module                                               |       | Create visual representations of Credentials as resources |
| [Create AnonCreds Revocation Registry Definition](https://docs.cheqd.io/identity/guides/anoncreds/revocation-registry-definition) using resource module | Create branding assets  as resources                                                                                                    |                                                           |
| [Create AnonCreds Revocation Registry Status List](https://docs.cheqd.io/identity/guides/anoncreds/revocation-status-list) using resource module           | Standardise [DID-Linked Resources Specification](https://github.com/w3c-ccg/community/issues/236) |                                                           |
|                                                                                                                                                                                                               | Formalise cheqd AnonCreds Object Method                                                                                                 |                                                           |

### Issuing and managing Verifiable Credentials on the cheqd network

#### JSON /JSON-LD Verifiable Credentials

| Now (current functionality)                                                                                                                                                     | Next (Q4)                                                                                      | Future                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [Issue and verify JSON based JWT credentials](https://docs.cheqd.io/identity/guides/sdk/veramo-sdk-for-cheqd)using Veramo SDK | Issue and verify [JSON-LD](https://github.com/cheqd/identity-docs) credential using Veramo SDK | Revocation of Verifiable Credentials using bespoke cheqd revocation mechanism |
| Hold JWT/JSON Verifiable Credentials in [web-app Wallet](https://wallet.cheqd.io/)                                                                                              | Use Status List 2021 to create a revocation registry and manage revocation statuses            |                                                                               |
| [Create a Verifiable Presentation](https://docs.cheqd.io/identity/tutorials/credentials-and-presentations/verify-jwt-presentation) using Veramo SDK          |                                                                                                |                                                                               |

#### AnonCreds

| Now (current functionality)                                                                                                                                                                                         | Next (Q4)                                                                                      | Future                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Dereference DID URL to fetch schemas & resources from cheqd network | Issue AnonCreds using Hyperledger Aries Framework Javascript SDK for cheqd                     | Aries Framework.NET SDK for cheqd                                |
|                                                                                                                                                                                                                     | Create a CL-Schema using Hyperledger Aries Framework Javascript SDK for cheqd                  | Aries Framework Go for cheqd                                     |
|                                                                                                                                                                                                                     | Create a Credential Definition using Hyperledger Aries Framework Javascript SDK for cheqd      | Revocation of AnonCreds using bespoke cheqd revocation mechanism |
|                                                                                                                                                                                                                     | Create entry in Revocation Registry using Hyperledger Aries Framework Javascript SDK for cheqd |                                                                  |
|                                                                                                                                                                                                                     | ACA-Py SDK for cheqd                                                                           |                                                                  |
|                                                                                                                                                                                                                     |                                                                                                |                                                                  |

## CHEQ Token & Payment Rails

| Now (current functionality)                                                               | Next (Q4)                                          | Future                                                                                                                                                                                    |
| ----------------------------------------------------------------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Hold and send CHEQ tokens](https://wallet.cheqd.io/welcome)                              | Pay for revocation status of Verifiable Credential | [Verifier-to-issuer](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Verifier pay issuer for credential presentation with CHEQ token (settled in stablecoin) |
| [Stake CHEQ tokens](https://wallet.cheqd.io/staking) as a validator                       |                                                    | [Verifier-to-holder](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Verifier pay holder for credential presentation with CHEQ token (settled in stablecoin) |
| [Delegate CHEQ tokens](https://wallet.cheqd.io/staking) to a validator to stake           |                                                    | [Holder-to-issuer](https://learn.cheqd.io/overview/introduction-to-usdcheq#holder-pays-issuer): Holder pay issuer for credential issuance with CHEQ token (settled in stablecoin)         |
| [Vote on governance proposals](https://commonwealth.im/cheqd/proposals) using CHEQ tokens         |
|
