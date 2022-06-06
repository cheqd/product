---
description: >-
  A high-level overview of our Product Roadmap for 2022. This will be
  continually fleshed out
---

# 🛣 2022 Roadmap

## Roadmap Overview

Our focus is to expand the utility of the cheqd network for decentralised identity use cases. This is our core mission and vision and - the reason why - we have such a broad interest within the self-sovereign identity (SSI) vendor ecosystem.

We want to get to a point, quickly, where we can provide compelling answers to “What identity capabilities does cheqd network provide, and how do I build it into my apps as an app developer / software vendor?”

Equally important as a focus area is deeper integrations with the Cosmos and wider Web 3.0 ecosystem. Digital identity is a burning need across DeFi, CeDeFi, and “traditional” Web 2.0 apps that cuts across as a “horizontal”, as well as being extremely important in “verticals” such as NFTs and online/offline reputation.

## H1 2022: Identity

### **Tutorials for developers using the identity and token functionality of cheqd network**

* [x] Status: Completed / Ongoing

From our Product research that we have carried out this year ([find our general Survey results summarised here](https://www.cheqd.io/blog/top-5-trends-in-decentralised-self-sovereign-identity-and-privacy-preserving-technology-in-web-3.0-2022)), creating documentation that is both simple to understand, and easy to implement, has been a paramount product goal for 2022.&#x20;

We have split our documentation into separate repositories for clarity and convenience (below). We will continually improve, add-to and iterate this documentation to keep it up to date.

#### Documentation for help setting up and managing a node

{% embed url="https://docs.cheqd.io/node" %}

#### Documentation detailing our identity functionality and decisions

{% embed url="https://docs.cheqd.io/identity" %}

#### What is the core business value of this work?

Easily digestible and clear documentation is crucial for giving cheqd's partners a smooth experience using the Network's utility. It will also make it easier for developers and end-customers to begin using the cheqd network and to quickly understand how to integrate with the network, SDK and token functionality.&#x20;



### DID Resolver

* [x] Full DID Resolver: Completed
* [ ] Proxy DID Resolver: Ongoing
* [ ] Universal Resolver: Ongoing

After we released our [cheqd DID method in 2021](https://github.com/cheqd/cheqd-node/blob/main/architecture/adr-list/adr-002-cheqd-did-method.md), creating a way for any person to simply resolve cheqd DIDs and utilise the value of [DID Core](https://www.w3.org/TR/did-core/) was an important next step for Q1 and Q2 2022.&#x20;

We are pleased to have designed a modular architecture for DID resolution, with multiple options for using and implementing our work.&#x20;

#### Full DID Resolver

Our primary DID resolver is a full resolver package which can be implemented directly into clients' own infrastructure as a library written in Golang. This provides full support for cheqd's resolver, and can be run by anyone, creating a secure and client-controlled environment for resolving cheqd DIDs.

#### Proxy DID Resolver

For those who do not want to run infrastructure themselves, but want to be able to resolve cheqd DIDs, we have created a DID Resolver as a Service - which routes requests to resolve DIDs to our cheqd gRPC endpoint to fetch a valid JSON response.&#x20;

This is lightweight, simple and easy to use.&#x20;

#### Universal Resolver

The Universal Resolver is a project maintained by DIF which hosts drivers of many different DID Resolvers in a compatible and easy-to-integrate format (Docker Containers).&#x20;

Through the Universal Resolver, cheqd's DID Resolver will be packaged as a Docker Container, making it compatible with any infrastructure stack.  &#x20;

#### What is the core business value of this work?

Having multiple implementations of a DID Resolver accommodates for different clients, developers and customers - each with different needs. The flexibility and modular architecture exhibited here will allow cheqd DIDs to be resolved simply and securely within closed, controlled ecosystems with tight security protocols - as well as by community members who want to try our our identity functionality. Catering to both parties' needs makes the cheqd DID Resolver valuable in both everyday use, and for enterprise use.&#x20;

#### Want to test it out?

You can see our resolver in action, resolving our first DID here:

{% embed url="https://resolver.cheqd.net/1.0/identifiers/did:cheqd:mainnet:zF7rhDBfUt9d1gJPjx7s1JXfUY7oVWkY" %}

#### Learn more

Learn about DIDs and what DID resolution is here:

{% embed url="https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did/how-do-you-resolve-a-did" %}

### DID URL Dereferencer

* [x] Simple dereferencer: Completed
* [ ] Complex dereferencer: Ongoing

Similar to a DID Resolver, a DID URL Dereferencer is used to take the input of a DID URL, and return a particular resource.

This can be used to point-to and fetch resources which are stored on ledger, using DIDs, such as:

* Other DIDs or DID Documents
* Parts of a DID Document (verification keys, sections, etc)
* Simple files (images, documents)
* Non-Fungible tokens (NFTs)
* Resources on-ledger (schemas)

#### What is the core business value of this work?

Being able to fetch resources from DIDs is something that hasn't properly been explored by the identity community. However, there is a vast amount of value that can be drawn out of fetching a resource from a DID.

At cheqd, we are using dereferencing to be able to fetch schemas which are stored on-ledger. The core goal of this is to be able to provide equivalence and compatibility with the AnonCreds spec, whilst remaining compliant with the W3C specifications.&#x20;

This will enable compatibility between Credential types in a way far greater than on any other network - giving all cheqd's partners a platform to build on, using their existing tech stack and clients.&#x20;



### Veramo Plugin for cheqd DID Method

* [x] Status: Completed

In order to issue and verify Verifiable Credentials using cheqd DIDs, software must be used that is able to communicate with the ledger and understands the DID method accordingly. This type of software is generally packaged as a Software Development Kit (SDK).&#x20;

cheqd has imbedded its DID method into the [Veramo SDK](https://veramo.io/) as a plugin, which enables users to issue and verify JSON-LD Credentials, signed by cheqd DIDs. This SDK was used for cheqd's [demo at Internet Identity Workshop 34](https://typefully.com/ankurb/PDcaiMP) in April 2022.&#x20;

#### What is the core business value of this work?

cheqd's intention is to create a "Interop" or "Unified" cheqd SDK, which is able to handle any mainstream Verifiable Credential type and route it through a compatible SDK module.

Using Veramo's SDK to handle JSON-LD Credentials is 1 component of the overall architecture here.

From a business perspective, this architecture is important to create interoperable production environments, where different companies, building on separate standards, can share a customer base.&#x20;

#### Want to test it out?

You can find our open sourced repository for our Veramo plugin here:

{% embed url="https://github.com/cheqd/did-provider-cheqd/" %}

### cheqd wallet

* [x] Demo wallet: completed

To showcase cheqd's identity capabilities, as well as the token functionality, we built an identity wallet which is able to hold Verifiable Credentials, as well as manage $CHEQ tokens via the Keplr browser extension.&#x20;

The wallet can be found here:

{% embed url="https://wallet.cheqd.io/" %}

#### What is the core business value of this work?

The wallet demonstrates how Verifiable Credentials and $CHEQ tokens could be held in the same place and managed with one UI. This is the kind of work that cheqd wants to approach alongside its partners in H2 2022.&#x20;

We also want to use the cheqd wallet to issue the cheqd community reward Credentials, based on their engagement and loyalty to cheqd. Through gamifying engagement, we can showcase the value of Verifiable Credentials to a much larger audience than the identity ecosystem.&#x20;



## H2 2022: Identity

### AnonCreds support

To date, cheqd is able to support JSON and JSON-LD Credentials natively on cheqd. However, this excludes a large portion of the identity ecosystem which have built out their products on Hyperledger Indy based networks using AnonCreds: a privacy-preserving Credential specification which is intrinsically tied to Indy.&#x20;

There are two ways cheqd intends to support AnonCreds:

1. cheqd AnonCreds bridge: AnonCreds-like support on-ledger
2. Interop SDK: Routing AnonCreds to appropriate SDK

### cheqd AnonCreds bridge&#x20;

* [x] Issuer DID Documents: Completed
* [x] Schema DID Documents: Completed
* [ ] Resource Collections: Ongoing
* [ ] Schema Objects on-ledger: Ongoing
* [ ] Credential Definition Composition: Ongoing

It is not easy to support AnonCreds directly on a non-Indy network. However, we have created an architecture that replicates the function of AnonCreds using W3C compliant standards. To make this work, there are a few components at play:

1. Issuer DID Documents
2. Schema DID Documents
3. Resource Collections
4. Schema Objects on-ledger
5. Credential Definition Composition

Each of these parts will be discussed in further detail in our Identity Documentation page:

{% embed url="https://docs.cheqd.io/identity" %}

#### What is the core business value in this work?

Through augmenting and replicating the structure of AnonCreds on cheqd, our partners will seamlessly be able to carry across their customer base from Hyperledger Indy based networks to cheqd.&#x20;

cheqd offers a far more scalable platform, with decentralised governance, and future capacity for payments for Verifiable Credentials.

By accommodating for JSON, JSON-LD and AnonCreds, cheqd provides a unique platform for identity, which champions interoperability and vendor-choice at its core.&#x20;



### Interop SDK

* [x] Veramo SDK for JSON / JSON-LD: Completed
* [ ] Aries based SDKs supporting cheqd: Ongoing
* [ ] cheqd direct SDK support for AnonCreds: Ongoing
* [ ] API routing logic: Backlog

Achieving support for multiple Verifiable Credential standards within one unified, interop SDK would tie the SSI community together. The SSI community is currently split between different factions - Hyperledger Indy applications cannot communicate with W3C-based applications, and vice versa.

#### What is the core business value in this work?

Through creating an AnonCreds bridge to support AnonCreds-like Credentials on cheqd - vendors who were previously shoehorned into the Indy world, would now be able to share a customer base with those working in other W3C-based ecosystems.

This type of interoperability is similar to how Visa, Mastercard and Amex can all work interchangeably with payment terminals. Although built separately, on different tech stacks - they can all be understood, used and accepted equally by end-customers and everyday people. This enhances the value of each company, because they are now able to collaborate  as well as compete.&#x20;











Quick Wins - Q1 2022

Each new release of cheqd software that we ship would aim for incrementally improving core functionality, which improves life for users (individual and enterprise), token holders, node operators and app developers.&#x20;

In this category (which we’ve called “Quick Wins”), we have product features and improvements where the approach is well-known and understood within the SSI and Web 3.0 industries.



<details>

<summary>Identity</summary>

* Tutorials for developers on using the identity and token functionality of cheqd network
* Integrations with industry-standard identity projects such as DIF’s Universal DID Resolver project
* New & improved decentralised identity functionality

</details>

<details>

<summary>Web 3.0 Core</summary>

* Wider integration with Cosmos ecosystem
* Bridge to Ethereum networks
* Improved automation & tooling for managing validator nodes on cheqd network

</details>



### Strategic aims: Identity (Q2 2022 and beyond)

Much of the basic identity functionality is currently live on the cheqd mainnet, but we’ve been working on stability and security improvements (due to go-live by the end of January 2022) before we begin guiding app developers in earnest. Here are our product ideas in the identity space we believe will have the greatest impact in the short-term.\
\
For a deeper dive, [please read our blog here](https://blog.cheqd.io/cheqds-product-vision-for-2022-6a92e8e4d296).\


<details>

<summary>Identity</summary>

* Payment rails for digital identity exchange
  * Robust, secure, and privacy-preserving payment mechanisms
  * Flexibility - no single payment fits every use case
  * “Payment” doesn’t _necessarily_ mean “locked” credential
* Client SDKs in more programming languages
* Better interoperability and support for emerging identity standards

</details>

<details>

<summary>Web 3.0 Core</summary>

* Native, cross-chain identity primitives for Cosmos ecosystem
* Smart contracts using CosmWasm
* Establish ourselves as a leader in decentralised governance for identity

</details>

<details>

<summary>Web 3.0 Exploratory</summary>

* Explore partnership for use-cases across DeFi, NFTs and much more

</details>



We would love your feedback on our product vision for 2022. We welcome engagement and feedback across a range of different forums, such as our [Community Slack](http://cheqd.link/join-cheqd-slack), [Governance Framework discussion board](https://github.com/cheqd/cheqd-governance/discussions), and [Telegram Group](https://t.me/cheqd), or drop us an email using the form below.

\


