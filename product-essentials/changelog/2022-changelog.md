# 2⃣ 2022 Changelog

<details>

<summary>March - On Chain Upgrade (v0.5.0)</summary>

## Context

This new node version is intended to enhance functionality currently available on v0.4.x. The upgrade to v0.5.x will be a breaking change that introduces new routes, fixes a few technical debt issues identified and overall offers significant enhancements to the identity functionality and security of the network.

Nominally, this upgrade would happen with v0.5.x, with only minor version upgrades that are compatible with v0.5.0 allowed.

## Changelog

### Identity Improvements&#x20;

#### Improved validation of did:cheqd identifiers

**What has changed?**

Our [did:cheqd Decentralized Identifier (DID)](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method) method provides a unique identification number for a DID Subject. This can be thought of in a very similar way to traditional bank cards. (Note: While the example of a bank card is used here, DIDs on ledger are typically written for companies, not individuals.)

![](https://lh5.googleusercontent.com/QnSlKr4TXeBaqlYcNkW1wEmGYatcEBi6vMPPnJSVBz96ENGeFkK01xBhRtSOdhS\_Ot3q3YEFTslDuWNMWoNnb3yXWFHTIrR9N9Iv4ldwheI2357ApOvpe7YoLqqhnEdc7sRMI7CSjq1E63QDUA)

Within a bank card, different sections of the card identify different actors, such as the Network, Issuer ID and a Unique Account Number - and when put together, you have a complete card number. DIDs are similar, in the sense that different components of the DID mean different things:

In this update, cheqd has updated the way that DIDs are created and resolved to ensure that the [Unique Identifier is a Base58 encoded string (either 16 or 32 characters long)](https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method). This was done to keep it consistent with the [Hyperledger Indy DID method identifier specification.](https://hyperledger.github.io/indy-did-method/#indy-did-method-identifiers)

**Why it is important?**&#x20;

Prior to the upgrade, the ledger code itself was relatively “dumb”: the responsibility of ensuring that a valid unique identifier was created, matching our DID specification, would be done client-side. While the cheqd ledger did implement a uniqueness check to ensure that no other DIDs with the same identifier existed within a namespace, it didn’t implement checks to ensure that the identifier specification was met. (This is broadly how a lot of Hyperledger Indy SDKs currently do this.)&#x20;

We believe that that there will be a blend of various levels of technical complexity in client-side SDKs that interact with DIDs, so relying on only client SDKs to implement this is an unsafe method. By adding checks on the ledger itself, it allows us to ensure consistency across a wide range of client SDKs.&#x20;

We are additionally exploring future iterations which would allow unique identifiers to be defined as [**UUIDs**](https://en.wikipedia.org/wiki/Universally\_unique\_identifier) instead of the Indy DID method technique as well.

#### More comprehensive cryptographic checks for DID updates

**What has changed?**&#x20;

In Hyperledger Indy, the assumption was that DID would have only one [Verification Method](https://w3c.github.io/did-core/#verification-methods) and one [Controller](https://w3c.github.io/did-core/#did-controller) per DID. The [DID Core specification](https://w3c.github.io/did-core/) has evolved since then to allow for multiple controllers and more complex [Verification Relationships](https://w3c.github.io/did-core/#verification-relationships).

[Learn more about DID’s (Decentralised Identifiers)](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did) and why they’re important on [learn.cheqd.io](https://learn.cheqd.io)

The cheqd DID method allows multiple controllers, verification methods, and complex relationships to be defined which brings it in-line with the DID Core specification. But this also introduces new challenges. To illustrate through an example, let’s say there is:&#x20;

1. A DID Document with three Verification Methods listed within the [**Verification Methods**](https://w3c.github.io/did-core/#verification-methods) section of the DID Document (“DIDDoc”)
2. Next, there is a request to add a new Verification Method to the DID Document.&#x20;
3. The question is: how should this DID Document be updated; who needs to sign to make this change?

Prior to the upgrade, when a DID update request was made, the ledger would only ask for the existing Verification Method(s) listed in the DID Document to sign to approve the change. We have changed this to ensure that both the existing and new Verification Method keys need to sign the update request.

This is important because it will prove that the controller(s) of any new Verification Method(s) have control of the relevant key(s) that the DID update is trying to achieve. This is much more secure because it achieves a level of trust that all of the Verification Method(s) listed in the DID Document can be appropriately signed for by their Controller(s). It also, importantly, follows the **** [**DID Core Specification**](https://www.w3.org/TR/did-core/)**.** Improved DID Resolution metadata for updated DIDs

**What has changed?**&#x20;

When a DID is resolved, it fetches resolution metadata in addition to the DID Document.. This metadata contains entries such as when a DID was created as well as when it was most recently updated.&#x20;

Prior to the upgrade, the Update metadata field would contain the same data as the Created field if the DID had never been updated. We’ve changed this to a null value instead of the same date/time, to make it easier for software to understand this scenario.&#x20;

**Why is this important?**&#x20;

If you see the Update field reads null, it means the DIDDoc has never been updated. This clears up any potential confusion and aligns the DID resolution metadata.

#### Implemented static validation for Verification Method keys.&#x20;

**What has changed?**

We have changed the way we validate Verification Method keys, splitting this into:&#x20;

* Static validation;&#x20;
* Dynamic validation.

The former, static validation checks, are performed before the inclusion of a transaction in the mempool; and the latter, dynamic validation checks, are performed during the transaction execution once it is included in the blockchain.

**Why is this important?**

Splitting these is important because now errors in Verification Method keys can be caught earlier and flagged, before any transaction enters the mempool.&#x20;

_Note: The mempool serves the purpose of keeping track of transactions seen by all full-nodes. Full-nodes keep a mempool cache of the last ‘mempool.cache\_size’ transactions they have seen, as a first line of defence to prevent replay attacks._&#x20;

Therefore, the validation improvements will allow nodes to reject invalid transactions in the early stages without including them in the chain and charging the user.&#x20;

This in turn speeds up the cheqd network as incorrect transactions are not being committed and incorrect Verification Method keys are not errored out when committing a transaction to the mempool.&#x20;

We’re also using other work to build similar efficiency improvements:&#x20;

* This validator package for null checks, generic DID validity checks in static validation
* This validator package for DID namespace checks in dynamic validation.

#### Implemented JSON Web Key (JWK) support.

Within the DID Core specification there are two types of key in a Verification Method:

* JSON Web Key (JWK); and&#x20;
* Public Key Multibase.&#x20;

Previously, the only format of key supported was **publicKeyMultibase**&#x20;

Having only one of these two options limits the scalability and interoperability of the cheqd network, as the supported Verification Method keys are limited.&#x20;

Therefore, we implemented JSON Web Key (JWK) support.&#x20;

Why is this important?&#x20;

With JWK, cheqd now supports a broader selection of Public Key encoding schemes, which is an important improvement, given our focus on interoperability and eventual cross-ledger support.

### Tech Debt & Bug Fixes&#x20;

#### Fixed date/time representation in DID Resolution&#x20;

**What has changed?**&#x20;

Previously, we were using a Cosmos format of datetime, rather than what is defined in the DID core spec. Now this has been changed to align with DID Core.&#x20;

**Why is this important?**&#x20;

This aligns our DID Document metadata with DID Core, making it more semantically interoperable and spec compliant.&#x20;

**DID metadata VersionId now populates a Tendermint’s tx\_hash in the correct format**&#x20;

**What has changed?**&#x20;

As cheqd is a chain built on the Cosmos SDK, it relies on Tendermint as its consensus mechanism.&#x20;

This means that when something is written to the network, there is a Tendermint transaction hash that is created. This is specific to Cosmos chains.&#x20;

Within DID Document metadata, there is a field called VersionID which, as the name suggests, denotes the specific version of the DID Document.&#x20;

Previously, in this field, we were generating a hash from the transaction itself to calculate the DIDDoc version ID. We have now changed this to populate a Tendermint transaction hash.&#x20;

**Why is this important?**&#x20;

This is important because the DIDDoc VersionID can now be retrieved right after the creation of the DID, with the DID now more easily searchable on a Block Explorer. Previously, we needed to create the DID, THEN ask it to create version ID, then update.&#x20;

This update streamlines the process and makes it more efficient.&#x20;

### Full changelog

* [cheqd/cheqd-node@v0.4.0...v0.5.0](https://github.com/cheqd/cheqd-node/compare/v0.4.0...v0.5.0)



</details>

<details>

<summary>February - Docker Compose Easy Setup (v0.4.1) </summary>

### Context

Our [packaged releases](https://github.com/cheqd/cheqd-node/releases) are currently compiled and tested for `Ubuntu 20.04 LTS`, which is the recommended operating system for installation using Debian package or binaries.

For other operating systems, we needed to provide an alternative approach. Therefore, this point release was intiated which offers a [pre-built Docker image releases for `cheqd-node`](https://github.com/orgs/cheqd/packages?repo\_name=cheqd-node).

### Changelog

* Docker Compose Easy Setup
* Docker Compose Easy Setup ([#250](https://github.com/cheqd/cheqd-node/pull/250))&#x20;
* Add euox pipefail check for bash scripts ([#266](https://github.com/cheqd/cheqd-node/pull/266))&#x20;
* Test for positive case of upgrade process ([#268](https://github.com/cheqd/cheqd-node/pull/268))
* Refactor Debian package installer to handle upgrade scenarios better ([#279](https://github.com/cheqd/cheqd-node/pull/279)) (Andrew Nikitin)
* Unified network configuration generation ([#267](https://github.com/cheqd/cheqd-node/pull/267))
* Further docker, tests improvements ([#280](https://github.com/cheqd/cheqd-node/pull/280))&#x20;
* Updated recommended docker image version&#x20;
* Revert fastsync version to `v0` ([#256](https://github.com/cheqd/cheqd-node/pull/256))&#x20;
* Fix small errors around postpurge script&#x20;

### Full changelog

[https://github.com/cheqd/cheqd-node/compare/v0.4.0...v0.4.1](https://github.com/cheqd/cheqd-node/compare/v0.4.0...v0.4.1)

</details>

<details>

<summary>January - On Chain Upgrade (v0.4.0) </summary>

### Context

This software upgrade proposal upgraded the version of cheqd-node software on cheqd-mainnet-1 from v0.3.1, to v0.4.x.&#x20;

Following the successful release of our mainnet in November 2021, we wanted to fast-follow with a some immediate improvements we felt necessary for the cheqd network.&#x20;

This new node version is intended to enhance functionality currently available on v0.3.1. The upgrade to v0.4.x will be a breaking change that introduces new routes, plus fixes a few technical debt issues identified in the v0.3.x branch.

### Changelog

* Bumped Cosmos SDK version from v0.44.3 to v0.44.5
* Update DID operations in version v0.3.1 did not carry out a check on the keys used to authenticate the transaction.&#x20;
  * In essence, this meant that any update DID operation could incorrectly update a DID or its associated DIDDoc. This has now been fixed.
* Switched build system from using Starport to using Makefiles.&#x20;
  * This gives greater control for future improvements and optimisation in adding support for other operating systems, database backends etc.
* The node software binary has now been compiled with support for Ledger hardware wallet devices for key storage.
* REST/gRPC endpoints for querying DIDs have been added. Documentation will be added to explain how these endpoints work.

### Full changelog

&#x20;[\[cheqd/cheqd-node@v0.3.1...v0.4.0\]](https://github.com/cheqd/cheqd-node/compare/v0.3.1...v0.4.0)





</details>
