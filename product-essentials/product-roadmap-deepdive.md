---
description: >-
  A high-level overview of our Product Roadmap for 2022. This will be
  continually fleshed out
---

# 🔎 Product Roadmap Deepdive

## Roadmap Overview

Our focus is to expand the utility of the cheqd network for decentralised identity use cases. This is our core mission and vision and - the reason why - we have such a broad interest within the self-sovereign identity (SSI) vendor ecosystem.

We want to get to a point, quickly, where we can provide compelling answers to “What identity capabilities does cheqd network provide, and how do I build it into my apps as an app developer / software vendor?”

Equally important as a focus area is deeper integrations with the Cosmos and wider Web 3.0 ecosystem. Digital identity is a burning need across DeFi, CeDeFi, and “traditional” Web 2.0 apps that cuts across as a “horizontal”, as well as being extremely important in “verticals” such as NFTs and online/offline reputation.

## Roadmap 2022: Identity

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

### cheqd wallet

* [x] Demo wallet: completed

**Context**

To showcase cheqd's identity capabilities, as well as the token functionality, we built an identity wallet which is able to hold Verifiable Credentials, as well as manage $CHEQ tokens via the Keplr browser extension.&#x20;

The wallet can be found here:

{% embed url="https://wallet.cheqd.io/" %}

#### What is the core business value of this work?

The wallet demonstrates how Verifiable Credentials and $CHEQ tokens could be held in the same place and managed with one UI. This is the kind of work that cheqd wants to approach alongside its partners in H2 2022.&#x20;

We also want to use the cheqd wallet to issue the cheqd community reward Credentials, based on their engagement and loyalty to cheqd. Through gamifying engagement, we can showcase the value of Verifiable Credentials to a much larger audience than the identity ecosystem.&#x20;

### AnonCreds support

**Context**

To date, cheqd is able to support JSON and JSON-LD Credentials natively on cheqd. However, this excludes a large portion of the identity ecosystem which have built out their products on Hyperledger Indy based networks using AnonCreds: a privacy-preserving Credential specification which is intrinsically tied to Indy.&#x20;

There are two ways cheqd intends to support AnonCreds:

1. cheqd AnonCreds compatibility: AnonCreds-like support on-ledger
2. SDK Routing Layer: Routing AnonCreds and other Credential types to appropriate SDK

### cheqd AnonCreds compatibility&#x20;

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



### SDK Routing Layer

* [x] Veramo SDK for JSON / JSON-LD: Completed
* [ ] Aries based SDKs supporting cheqd: Ongoing - Q3 expected release
* [ ] cheqd direct SDK support for AnonCreds: Ongoing - Q3 expected release
* [ ] API routing logic and rules: Backlog - Q3 expected release

Achieving support for multiple Verifiable Credential standards within one SDK Routing Layer would help enterprises consume Credentials from multiple sources. The SSI community is currently split between different factions - Hyperledger Indy applications cannot communicate with W3C-based applications, and vice versa.

#### What is the core business value in this work?

Through creating AnonCreds compatibility to support AnonCreds-like Credentials on cheqd - vendors who were previously shoehorned into the Indy world, would now be able to share a customer base with those working in other W3C-based ecosystems.

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

## Roadmap 2022: Network Infrastructure

### Tooling, hosting and analytics

* [x] Terraform: Completed
* [x] Terragrunt: Completed
* [ ] Ansible: Ongoing
* [x] DataDog: Completed
* [x] SSH certificates for admin access via Cloudflare Teams: Completed
* [x] HashiCorp Vault: Completed
* [ ] Terraform, Terragrunt and Ansible package for other Cosmos networks

We've spent a lot of time in the first half of 2022 improving the infrastructure that cheqd is run on, and designing infrastructure packages that could benefit any project running a blockchain.

Through a combination of this infrastructure, Validator nodes will be able to spin up nodes on cheqd in a way which is far more efficient than before.&#x20;

#### Terraform

We have started using Terraform to define consistent and automated workflows - in order to improve efficiency and streamline the process of setting up a node on cheqd. Terraform is a form of Infra-as-code which is essentially the managing and provisioning of infrastructure through code instead of through manual processes.

You can think of it like dominos - one click of a button can result in a whole series of outcomes.

#### Terragrunt

Terragrunt works hand-in-hand with Terraform, making code more modular and facilitating different configurations of code for different use cases. You can plug in config information like CPU, RAM, Static IPs, Storage, etc., which speed things up whilst making the code more modular and reusable.

#### Ansible&#x20;

Ansible code wraps around the package established by Terraform and Terragrunt to convert the same code into more interoperable formats.&#x20;

Using Ansible, the same configurations created for setting up nodes on cheqd could be packaged in a format which could be consumed by other Cosmos networks.&#x20;

#### DataDog

DataDog is an analytics tool that records logs from cheqd network for debugging purposes, logs Tendermint metrics, Cosmos SDK based metrics and is able to connect with third party software such as Slack for notifications.&#x20;

Using DataDog enables anyone to be more proactive in monitoring the cheqd network; quickly finding and resolving issues in order to keep the network running smoothly.&#x20;

#### SSH certificates for admin access via Cloudflare Teams

This infrastructure provides **** secure one-time SSH certificates for admin access into one of the cheqd nodes. Cloudflare teams enables roles and authorisation management to set different privilege and access levels for working on the node.&#x20;

This work can be extended and used by other projects to help manage authorisation around nodes more securely and effectively.

#### HashiCorp Vault

HashiCorp Vault is about backup and secret management.

It runs a script that copies private key and node key over to the HashiCorp vault. It can be thought of as a password manager for cryptographic key material, secret management, sharing and access control.

This is valuable for anyone managing private keys, since if a key is lost or accidentally deleted, through HashiCorp Vault it can easily be restored.

### Testnet token faucet UI

This allows developers to acquire testnet tokens to start testing out and using the identity functionality on the cheqd network.

This will reduce operational overheads and simplify the process of issuing testnet tokens to developers, validators, users and clients on the network.



## Roadmap 2022: Cosmos and Web 3.0

* [x] Ceate an ERC20 representation of the Cosmos based CHEQ token bridge on Ethereum&#x20;
* [x] Build Airdrop Frontend and UI
* [x] Build Cosmos Chain Address converter&#x20;
* [x] Build custom Cosmos Data APIs&#x20;

### Ethereum bridge

**Context**

To create an ERC20 representation of the Cosmos based CHEQ token we’ve used a bridge. A blockchain bridge or ‘cross-chain bridge’ enables users to transfer assets or any form of data seamlessly from one entirely separate protocol or ecosystem to another (i.e. Solana to Ethereum, or in our case Cosmos to Ethereum and vice versa).

The [CHEQ-ERC20 wrapped token can be found here](https://etherscan.io/address/0x70EDF1c215D0ce69E7F16FD4E6276ba0d99d4de7) (you can also add it to your MetaMask wallet through this link — _go to profile summary > click ‘more’ > ‘add token to MetaMask’_ )

\
**Why did we decide on a bridge to Ethereum?**

As we build payment rails for trusted data (more on that below), we want to offer issuers, verifiers (the receivers of trusted data), and holders a choice on the means of settlement. We expect a preference for [_stablecoins_](https://en.wikipedia.org/wiki/Stablecoin) to eliminate the volatility in either pricing or settling payments for trusted data.

Find out more on our learn site below:

{% embed url="https://learn.cheqd.io/getting-set-up-on-cheqd/cheq-erc20-wrapped-token" %}

### Airdrop Frontend and UI

**Context**

We’ve open sourced the community airdrop rewards site which is built using Cloudflare Pages and designed it to be highly scalable.

Airdrop reward sites need to be more resilient to traffic spikes than most websites because, when announced, community members will tend to flock to the site to claim their rewards generating a large spike in traffic, followed by a period of much lower traffic**.** This type of traffic pattern can make prepping the server to host airdrop claim websites particularly difficult.

For example, many projects will choose to purchase a large server capacity to prevent server lag, whilst others may simply become overwhelmed with the traffic

Through using Cloudflare Pages one-to-one scaling, we made our airdrop reward site far cheaper, ensured spikes were handled with efficiency, and the likelihood of server-lag or timeouts was greatly decreased.

Check this out below:&#x20;

{% embed url="https://github.com/cheqd/airdrop-ui" %}

### Cosmos chain address convertor

**Context**\
There is an assumption in the CosmosEcosystem  that wallet addresses across different chains, such as, Cosmos (ATOM), Osmosis (OSMO)  and[ ](https://twitter.com/cheqd\_io)cheqd (CHEQ), are all identical. This is because they all look very similar. However, each chain's wallet address is actually unique**.**

Our cross-chain address convertor is able to automate the derivation of any chain address from **Cosmos** address.

Want to leverage this for your project? Find out more in the link below:&#x20;

{% embed url="https://github.com/cheqd/cosmjs-cli-converter%E2%80%A6" %}
**Cosmos cross-chain address convertor**
{% endembed %}

### Cosmos Data APIs

**Context**

We found on our journey that there’s a LOT of stuff that we needed APIs for, but couldn’t directly fetch from base Cosmos SDK’s.

This collection of custom APIs can be deployed as a @Cloudflare Worker or compatible serverless platforms. APIs include:&#x20;

1. Total Supply
2. Circulating Supply
3. Vesting Account Balance
4. Liquid Account Balance
5. Total Account Balance&#x20;

Further context on each and how you can leverage these APIs in your project can be found through the link below:

{% embed url="https://github.com/cheqd/data-api" %}
**Cosmos Data APIs**
{% endembed %}

{% hint style="success" %}
To explore our initial roadmap from the beginning of 2022, [please read our blog here](https://blog.cheqd.io/cheqds-product-vision-for-2022-6a92e8e4d296).
{% endhint %}

We would love your feedback on our product vision for 2022. We welcome engagement and feedback across a range of different forums, such as our [Community Slack](http://cheqd.link/join-cheqd-slack), [Governance forum](https://commonwealth.im/cheqd), and [Telegram Group](https://t.me/cheqd).

\


