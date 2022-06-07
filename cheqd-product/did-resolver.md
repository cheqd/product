# DID Resolver

## Overview

After we released our [cheqd DID method in 2021](https://github.com/cheqd/cheqd-node/blob/main/architecture/adr-list/adr-002-cheqd-did-method.md), creating a way for any person to simply resolve cheqd DIDs and utilise the value of [DID Core](https://www.w3.org/TR/did-core/) was an important next step for Q1 and Q2 2022.&#x20;

We are pleased to have designed a modular architecture for DID resolution, with multiple options for using and implementing our work, increasing:

* [x] Accessibility to cheqd DIDs
* [x] Interoperability with other networks
* [x] Flexibility for different users (enterprises and individuals)

#### Full DID Resolver

Our primary DID resolver is a full resolver package which can be implemented directly into clients' own infrastructure as a library written in Golang. This provides full support for cheqd's resolver, and can be run by anyone, creating a secure and client-controlled environment for resolving cheqd DIDs.

#### Proxy DID Resolver

For those who do not want to run infrastructure themselves, but want to be able to resolve cheqd DIDs, we have created a DID Resolver as a Service - which routes requests to resolve DIDs to our cheqd gRPC endpoint to fetch a valid JSON response.&#x20;

This is lightweight, simple and easy to use. It is written as a tiny Node.js package designed to run on [Cloudflare Workers](https://workers.cloudflare.com/) which is an extremely light serverless platform for those who want a lower compute footprint that essentially acts as a proxy to a Golang-based “full” resolver.

#### Universal Resolver

The Universal Resolver is a project maintained by DIF which hosts drivers of many different DID Resolvers in a compatible and easy-to-integrate format (Docker Containers).&#x20;

Through the Universal Resolver, cheqd's DID Resolver will be packaged as a Docker Container, making it compatible with any infrastructure stack.  &#x20;

#### What is the core business value of this work?

Having multiple implementations of a DID Resolver accommodates for different clients, developers and customers - each with different needs.&#x20;

The flexibility and modular architecture exhibited here will allow cheqd DIDs to be resolved simply and securely within closed, controlled ecosystems with tight security protocols - as well as by community members who want to try our our identity functionality. Catering to both parties' needs makes the cheqd DID Resolver valuable in both everyday use, and for enterprise use.&#x20;

In short, this architecture improves:

* [x] Accessibility to cheqd DIDs
* [x] Interoperability with other networks
* [x] Flexibility for different users (enterprises and individuals)



#### Want to test it out?

You can see our resolver in action, resolving our first DID here:

{% embed url="https://resolver.cheqd.net/1.0/identifiers/did:cheqd:mainnet:zF7rhDBfUt9d1gJPjx7s1JXfUY7oVWkY" %}

#### Learn more

Learn about DIDs and what DID resolution is here:

{% embed url="https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did/how-do-you-resolve-a-did" %}

#### Overall Architecture of DID Resolver(s)

You can look into our architecture and decision making in more detail in our Identity docs:

{% embed url="https://docs.cheqd.io/identity/architecture/did-resolver" %}
