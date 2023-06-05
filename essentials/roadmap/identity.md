# Identity

## Decentralised Identifiers (DIDs)

### Tutorials for developers using Veramo SDK

From our Product research that we have carried out this year ([find our general Survey results summarised here](https://www.cheqd.io/blog/top-5-trends-in-decentralised-self-sovereign-identity-and-privacy-preserving-technology-in-web-3.0-2022)), creating documentation that is both simple to understand, and easy to implement, has been a paramount product goal for 2022.

We have split our documentation into separate repositories for clarity and convenience (below). We will continually improve, add-to and iterate this documentation to keep it up to date.

* [x] [Setup Veramo SDK for cheqd](https://docs.cheqd.io/identity/guides/sdk/veramo-sdk-for-cheqd/setup): Completed
* [x] [Creating DIDs](https://docs.cheqd.io/identity/tutorials/did-operations/create-did): Completed
* [x] [Query DIDs](https://docs.cheqd.io/identity/tutorials/did-operations/query-did): Completed
* [x] [Managing keys](https://docs.cheqd.io/identity/tutorials/did-operations/identity-keys): Completed
* [x] [Updating DIDs](https://docs.cheqd.io/identity/tutorials/did-operations/update-did): Completed
* [ ] Deactivating DIDs: In progress
* [x] [Creating Resources/Schemas](https://docs.cheqd.io/identity/tutorials/did-linked-resources/create-resource): Completed
* [x] [Creating new Resource Versions](https://docs.cheqd.io/identity/tutorials/did-linked-resources/create-new-version): Completed
* [x] [Issuing Verifiable Credentials (JSON)](https://docs.cheqd.io/identity/tutorials/credentials-and-presentations/issue-credential): Completed
* [x] [Verify Verifiable Credentials (JSON)](https://docs.cheqd.io/identity/tutorials/credentials-and-presentations/verify-jwt-credential): Completed
* [x] [Creating Verifiable Presentations (JSON)](https://docs.cheqd.io/identity/tutorials/credentials-and-presentations/verify-jwt-presentation): Completed
* [ ] Issuing Verifiable Credentials (JSON-LD): In progress
* [ ] Creating Verifiable Presentations (JSON-LD): In progress

#### What is the core business value of this work?

Easily digestible and clear documentation is crucial for giving cheqd's partners a smooth experience using the Network's utility. It will also make it easier for developers and end-customers to begin using the cheqd network and to quickly understand how to integrate with the network, SDK and token functionality.

### Documentation for help setting up and managing a node

{% embed url="https://docs.cheqd.io/node" %}

### Documentation detailing our identity functionality and decisions

{% embed url="https://docs.cheqd.io/identity" %}

### DID Resolver

* [x] Full DID Resolver: Completed
* [x] Universal Resolver: Completed

After we released our [cheqd DID method in 2021](https://docs.cheqd.io/identity/architecture/adr-list/adr-001-cheqd-did-method), creating a way for any person to simply resolve cheqd DIDs and utilise the value of [DID Core](https://www.w3.org/TR/did-core/) was an important next step for Q1 and Q2 2022.

Our DID resolver is a package which can be implemented directly into clients' own infrastructure as a library written in Golang. This provides full support for cheqd's resolver, and can be run by anyone, creating a secure and client-controlled environment for resolving cheqd DIDs.

The our DID resolver is also available as [a supported driver in Universal Resolver](https://github.com/decentralized-identity/universal-resolver), a project maintained by DIF which hosts drivers of many different DID Resolvers in a compatible and easy-to-integrate format (Docker Containers).

#### What is the core business value of this work?

Having multiple implementations of a DID Resolver accommodates for different clients, developers and customers - each with different needs. The flexibility and modular architecture exhibited here will allow cheqd DIDs to be resolved simply and securely within closed, controlled ecosystems with tight security protocols - as well as by community members who want to try our our identity functionality. Catering to both parties' needs makes the cheqd DID Resolver valuable in both everyday use, and for enterprise use.

#### Want to test it out?

You can see our resolver in action, resolving our first DID here:

{% embed url="https://resolver.cheqd.net/1.0/identifiers/did:cheqd:mainnet:Ps1ysXP2Ae6GBfxNhNQNKN" %}

#### Learn more

Learn about DIDs and what DID resolution is here:

#### What is the core business value in this work?

1. This is a highly requested and necessary feature of W3C-based SSI
2. This lays the foundation for payment rails for Verifiable Credentials

## Verifiable Credentials

### Veramo SDK for cheqd

* [x] Release of Veramo SDK for cheqd DID method: Completed

In order to issue and verify Verifiable Credentials using cheqd DIDs, software must be used that is able to communicate with the ledger and understands the DID method accordingly. This type of software is generally packaged as a Software Development Kit (SDK).

cheqd has embedded its DID method into the [Veramo SDK](https://veramo.io/) as a plugin, which enables users to issue and verify JSON-LD Credentials, signed by cheqd DIDs. This SDK was used for cheqd's [demo at Internet Identity Workshop 34](https://typefully.com/ankurb/PDcaiMP) in April 2022.

#### What is the core business value of this work?

cheqd's intention is to create a "Interop" or "Unified" cheqd SDK, which is able to handle any mainstream Verifiable Credential type and route it through a compatible SDK module.

Using Veramo's SDK to handle JSON-LD Credentials is 1 component of the overall architecture here.

From a business perspective, this architecture is important to create interoperable production environments, where different companies, building on separate standards, can share a customer base.

#### Want to test it out?

You can find our open sourced repository for our Veramo plugin here:

{% embed url="https://github.com/cheqd/did-provider-cheqd/" %}

### Browser-based wallet reference app

* [x] Beta release of wallet: Completed
* [ ] GA release of browser wallet reference app: Ongoing

To showcase cheqd's identity capabilities, as well as the token functionality, we built [a browser-based identity wallet demo app](https://wallet.cheqd.io/) which is able to hold Verifiable Credentials, as well as manage $CHEQ tokens via the [Keplr browser extension](https://keplr.app).

#### What is the core business value of this work?

The wallet demonstrates how Verifiable Credentials and $CHEQ tokens could be held in the same place and managed with one UI. This is the kind of work that cheqd wants to approach alongside its partners in H2 2022.

We also want to use the cheqd wallet to issue the cheqd community reward Credentials, based on their engagement and loyalty to cheqd. Through gamifying engagement, we can showcase the value of Verifiable Credentials to a much larger audience than the identity ecosystem.

### AnonCreds-style credentials

To date, cheqd is able to support JSON and JSON-LD Credentials natively on cheqd. However, this excludes a large portion of the identity ecosystem which have built out their products on Hyperledger Indy based networks using AnonCreds: a privacy-preserving Credential specification which is intrinsically tied to Indy.

It is not easy to support AnonCreds directly on a non-Indy network. However, we have created an architecture that replicates the function of AnonCreds using W3C compliant standards. To make this work, there are a few components at play:

* [x] Issuer DID Documents: Completed
* [x] Schema DID Documents: Completed
* [x] Resource Collections: Completed
* [x] Schema Objects on-ledger: Completed
* [x] Credential Definition Composition: Completed
* [x] Revocation Registry Definitions: Completed
* [ ] Revocation Registry Entries: In Progress

Each of these parts will be discussed in further detail in our Identity Documentation page:

{% embed url="https://docs.cheqd.io/identity" %}

#### What is the core business value in this work?

Through augmenting and replicating the structure of AnonCreds on cheqd, our partners will seamlessly be able to carry across their customer base from Hyperledger Indy based networks to cheqd.

cheqd offers a far more scalable platform, with decentralised governance, and future capacity for payments for Verifiable Credentials.

By accommodating for JSON, JSON-LD and AnonCreds, cheqd provides a unique platform for identity, which champions interoperability and vendor-choice at its core.

### Unified API for multiple credential formats & exchange protocols

* [x] Veramo SDK for JSON: Completed
* [ ] Aries based SDKs supporting cheqd: Backlog
* [ ] API routing logic and rules: Backlog

Achieving support for multiple Verifiable Credential standards using a Routing Layer into multiple SDKs would help enterprises consume Credentials from multiple sources. The SSI community is currently split between different factions - Hyperledger Indy applications cannot communicate with W3C-based applications, and vice versa.

This is a long term goal, after building cheqd support into more existing SDKs.

#### What is the core business value in this work?

Through creating AnonCreds compatibility to support AnonCreds-like Credentials on cheqd - vendors who were previously shoehorned into the Indy world, would now be able to share a customer base with those working in other W3C-based ecosystems.

A routing layer would also create a harmonised interface with AnonCreds based on Indy AND JSON/JSON-LD Credentials anchored elsewhere.

This type of interoperability is similar to how Visa, Mastercard and Amex can all work interchangeably with payment terminals. Although built separately, on different tech stacks - they can all be understood, used and accepted equally by end-customers and everyday people. This enhances the value of each company, because they are now able to collaborate as well as compete.

### Revocation Registry

* [ ] Status: Ongoing - Q3 expected release

Revocation lists and registries have been one of the components of W3C Verifiable Credentials tech stacks that have lagged behind. There is a clear need for a far more scalable, privacy-preserving revocation registry than what currently exists on the market.

The revocation registry is also central to how cheqd intends to monetise the use of Verifiable Credentials - via gating requests made to check revocation status.

Proponents of Hyperledger Indy will often point to the way it carries out revocation as a gold standard, since it is functional and privacy-preserving. cheqd intends to extend the way Indy carries out revocation, making it scalable and applicable within W3C-based ecosystems.

## Payment rails

* [ ] Verifier-pays-issuer: Backlog - Q4 expected release
* [ ] Holder-pays issuer: Backlog - Q4 expected release
* [ ] Verifier-pays-holder: Backlog - Q4 expected release

As laid out in much of our content, payment rails for Verifiable Credentials and customisable commercial models is a fundamental goal and objective of the cheqd project.

Learn more about how the $CHEQ token works on our learning site:

{% embed url="https://learn.cheqd.io/overview/introduction-to-usdcheq" %}
