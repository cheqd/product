# 🆔 Identity

## Roadmap 2022: Identity

### Contents

* [Tutorials for developers using the identity and token functionality of cheqd network](identity.md#tutorials-for-developers-using-the-identity-and-token-functionality-of-cheqd-network)
* [DID Resolver](identity.md#did-resolver)
* [DID URL Dereferencer](identity.md#did-url-dereferencer)
* [Veramo plugin for cheqd DID method](identity.md#veramo-plugin-for-cheqd-did-method)
* [cheqd browser plug-in](identity.md#cheqd-wallet)
* [cheqd AnonCreds compatibility](identity.md#cheqd-anoncreds-compatibility)
* [Routing layer](identity.md#routing-layer)
* [cheqd Revocation registry](identity.md#cheqd-revocation-registry)
* [cheqd Payment rails](identity.md#cheqd-payment-rails)

### **Tutorials for developers using the identity and token functionality of cheqd network**

* [x] Tutorials for Creating DIDs: Completed
* [ ] Tutorials for Creating Resources/Schemas: Ongoing

**Context**

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
* [ ] Proxy DID Resolver: Ongoing - Q2 expected release
* [ ] Universal Resolver: Ongoing - Q2 expected release

**Context**

After we released our [cheqd DID method in 2021](https://github.com/cheqd/cheqd-node/blob/main/architecture/adr-list/adr-002-cheqd-did-method.md), creating a way for any person to simply resolve cheqd DIDs and utilise the value of [DID Core](https://www.w3.org/TR/did-core/) was an important next step for Q1 and Q2 2022.&#x20;

We are pleased to have designed a modular architecture for DID resolution, with multiple options for using and implementing our work.&#x20;

#### Full DID Resolver

Our primary DID resolver is a full resolver package which can be implemented directly into clients' own infrastructure as a library written in Golang. This provides full support for cheqd's resolver, and can be run by anyone, creating a secure and client-controlled environment for resolving cheqd DIDs.

#### Proxy DID Resolver

For those who do not want to run infrastructure themselves, but want to be able to resolve cheqd DIDs, we have created a DID Resolver as a Service - which routes requests to resolve DIDs to our cheqd gRPC endpoint to fetch a valid JSON response.&#x20;

This is lightweight, simple and easy to use. It is written as a tiny Node.js package designed to run on [Cloudflare Workers](https://workers.cloudflare.com/) which is an extremely light serverless platform for those who want a lower compute footprint that essentially acts as a proxy to a Golang-based “full” resolver.

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
* [ ] Complex dereferencer: Ongoing - Q3 expected release

**Context**

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

**Context**

In order to issue and verify Verifiable Credentials using cheqd DIDs, software must be used that is able to communicate with the ledger and understands the DID method accordingly. This type of software is generally packaged as a Software Development Kit (SDK).&#x20;

cheqd has imbedded its DID method into the [Veramo SDK](https://veramo.io/) as a plugin, which enables users to issue and verify JSON-LD Credentials, signed by cheqd DIDs. This SDK was used for cheqd's [demo at Internet Identity Workshop 34](https://typefully.com/ankurb/PDcaiMP) in April 2022.&#x20;

#### What is the core business value of this work?

cheqd's intention is to create a "Interop" or "Unified" cheqd SDK, which is able to handle any mainstream Verifiable Credential type and route it through a compatible SDK module.

Using Veramo's SDK to handle JSON-LD Credentials is 1 component of the overall architecture here.

From a business perspective, this architecture is important to create interoperable production environments, where different companies, building on separate standards, can share a customer base.&#x20;

#### Want to test it out?

You can find our open sourced repository for our Veramo plugin here:

{% embed url="https://github.com/cheqd/did-provider-cheqd/" %}

### cheqd browser plug-in

* [x] Demo wallet: completed

**Context**

To showcase cheqd's identity capabilities, as well as the token functionality, we built an identity wallet browser plug-in which is able to hold Verifiable Credentials, as well as manage $CHEQ tokens via the Keplr browser extension.&#x20;

The wallet can be found here:

{% embed url="https://wallet.cheqd.io/" %}

#### What is the core business value of this work?

The wallet demonstrates how Verifiable Credentials and $CHEQ tokens could be held in the same place and managed with one UI. This is the kind of work that cheqd wants to approach alongside its partners in H2 2022.&#x20;

We also want to use the cheqd wallet to issue the cheqd community reward Credentials, based on their engagement and loyalty to cheqd. Through gamifying engagement, we can showcase the value of Verifiable Credentials to a much larger audience than the identity ecosystem.&#x20;

### cheqd AnonCreds compatibility&#x20;

To date, cheqd is able to support JSON and JSON-LD Credentials natively on cheqd. However, this excludes a large portion of the identity ecosystem which have built out their products on Hyperledger Indy based networks using AnonCreds: a privacy-preserving Credential specification which is intrinsically tied to Indy.&#x20;

There are two ways cheqd intends to support AnonCreds:

1. cheqd AnonCreds compatibility: AnonCreds-like support on-ledger
2. SDK Routing Layer: Routing AnonCreds and other Credential types to appropriate SDK

* [x] Issuer DID Documents: Completed
* [x] Schema DID Documents: Completed
* [ ] Resource Collections: Ongoing - Q2 expected release
* [ ] Schema Objects on-ledger: Ongoing - Q2 expected release
* [ ] Credential Definition Composition: Ongoing - Q3 expected release

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



### Routing Layer

* [x] Veramo SDK for JSON / JSON-LD: Completed
* [ ] Aries based SDKs supporting cheqd: Ongoing - Q3 expected release
* [ ] API routing logic and rules: Backlog

Achieving support for multiple Verifiable Credential standards using a Routing Layer into multiple SDKs would help enterprises consume Credentials from multiple sources. The SSI community is currently split between different factions - Hyperledger Indy applications cannot communicate with W3C-based applications, and vice versa.

This is a long term goal, after building cheqd support into more existing SDKs.&#x20;

#### What is the core business value in this work?

Through creating AnonCreds compatibility to support AnonCreds-like Credentials on cheqd - vendors who were previously shoehorned into the Indy world, would now be able to share a customer base with those working in other W3C-based ecosystems.

A routing layer would also create a harmonised interface with AnonCreds based on Indy AND JSON/JSON-LD Credentials anchored elsewhere.&#x20;

This type of interoperability is similar to how Visa, Mastercard and Amex can all work interchangeably with payment terminals. Although built separately, on different tech stacks - they can all be understood, used and accepted equally by end-customers and everyday people. This enhances the value of each company, because they are now able to collaborate  as well as compete.&#x20;



### cheqd Revocation Registry

* [ ] Status: Ongoing - Q3 expected release

Revocation lists and registries have been one of the components of W3C Verifiable Credentials tech stacks that have lagged behind. There is a clear need for a far more scalable, privacy-preserving revocation registry than what currently exists on the market.&#x20;

The revocation registry is also central to how cheqd intends to monetise the use of Verifiable Credentials - via gating requests made to check revocation status.&#x20;

Proponents of Hyperledger Indy will often point to the way it carries out revocation as a gold standard, since it is functional and privacy-preserving. cheqd intends to extend the way Indy carries out revocation, making it scalable and applicable within W3C-based ecosystems.&#x20;

#### What is the core business value in this work?

1. This is a highly requested and necessary feature of W3C-based SSI
2. This lays the foundation for payment rails for Verifiable Credentials

### cheqd Payment rails&#x20;

* [ ] Verifier-pays-issuer: Backlog - Q4 expected release
* [ ] Holder-pays issuer: Backlog - Q4 expected release
* [ ] Verifier-pays-holder: Backlog - Q4 expected release

As laid out in much of our content, payment rails for Verifiable Credentials and customisable commercial models is a fundamental goal and objective of the cheqd project.&#x20;

Learn more about how the $CHEQ token works on our learning site:

{% embed url="https://learn.cheqd.io/overview/introduction-to-usdcheq" %}

##
