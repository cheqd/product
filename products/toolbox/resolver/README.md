# 🔄 Resolve cheqd DIDs and Resources

## Context

> **Github repos:** [cheqd/did-resolver](https://github.com/cheqd/did-resolver)

After we released our [cheqd DID method in 2021](https://docs.cheqd.io/identity/architecture/adr-list/adr-001-cheqd-did-method), creating a way for any person to simply resolve cheqd DIDs and utilise the value of [DID Core](https://www.w3.org/TR/did-core/) was an important next step for Q1 and Q2 2022.

We are pleased to have designed a modular architecture for DID resolution, with multiple options for using and implementing our work, increasing:

* [x] Accessibility to cheqd DIDs
* [x] Interoperability with other networks
* [x] Flexibility for different users (enterprises and individuals)

Having a DID resolver software is important since reading DIDs from a network happens disproportionately more often than writing DIDs to a network. Think about the act of getting a Twitter username or a domain name: you sign up and create the handle once, and then use it as many times as you want to send new tweets, or to publish new web pages on your domain. This is similar to writing a DID once, and using it to publish [digitally verifiable credentials many times](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-verifiable-credential-vc/what-is-a-verifiable-presentation). The _recipients_ of those credentials can use a DID resolver to read the keys written on-ledger used to verify that credentials issued are untampered.

Many decentralised digital identity projects use the [Decentralized Identity Foundation (DIF) Universal Resolver project](https://github.com/decentralized-identity/universal-resolver) to carry out DID reads/resolution. Therefore, we have made a [cheqd DID Resolver](https://github.com/cheqd/did-resolver) available under an open-source license, and we’re working with DIF to get this integrated upstream into the Universal Resolver project.

The DID resolver we’ve made available is a **“full” profile resolver**, which is written in Golang (same as [our ledger/node software](https://github.com/cheqd/cheqd-node)) and can do authenticated/verified data reads from any node on the cheqd network over its gRPC API endpoint. This will likely be required by app developers or partners looking at processing high volumes of DID resolution requests since they can pull the data from their own cheqd node, and/or if they want the highest levels of assurance that the data pulled was untampered.

We also plan on releasing **a “light” profile DID Resolver**, built as a tiny Node.js application designed to run on [Cloudflare Workers](https://workers.cloudflare.com/) (a serverless hosting platform with extremely quick “cold start” times). This will allow app developers who don’t want to run a full node + full DID Resolver to be able to run their own, extremely scalable, and lightweight infrastructure for servicing DID read requests.

In short, this architecture improves:

* Accessibility to cheqd DIDs
* Flexibility, offering app developers and partners optionality and choice of platforms to run on, according to their security/scalability needs, and at various different levels of how much it costs to run this infrastructure.

## Resolver packages for `did:cheqd`

Having multiple implementations of a DID Resolver accommodates for different clients, developers and customers - each with different needs.

The flexibility and modular architecture exhibited here will allow cheqd DIDs to be resolved simply and securely within closed, controlled ecosystems with tight security protocols - as well as by community members who want to try our our identity functionality. Catering to both parties' needs makes the cheqd DID Resolver valuable in both everyday use, and for enterprise use.

### Full DID Resolver

Our primary DID resolver is a full resolver package which can be implemented directly into clients' own infrastructure as a library written in Golang. This will likely be required by app developers or partners looking at processing high volumes of DID resolution requests since they can pull the data from their own cheqd node, and/or if they want the highest levels of assurance that the data pulled was untampered.

### Light DID Resolver

For those who do not want to run infrastructure themselves, but want to be able to resolve cheqd DIDs, we have created a DID Resolver as a Service - which routes requests to resolve DIDs to our cheqd gRPC endpoint to fetch a valid JSON response.

This is lightweight, simple and easy to use. It is written as a tiny Node.js package designed to run on [Cloudflare Workers](https://workers.cloudflare.com/) which is an extremely light serverless platform for those who want a lower compute footprint that essentially acts as a proxy to a Golang-based “full” resolver.

### Universal Resolver

The Universal Resolver is a project maintained by DIF which hosts drivers of many different DID Resolvers in a compatible and easy-to-integrate format (Docker Containers).

Through the Universal Resolver, cheqd's DID Resolver will be packaged as a Docker Container, making it compatible with any infrastructure stack.

### Try our DID Resolver in action

You can see our resolver in action, resolving our first DID here:

{% embed url="https://resolver.cheqd.net/1.0/identifiers/did:cheqd:mainnet:zF7rhDBfUt9d1gJPjx7s1JXfUY7oVWkY" %}

## Learn more

Learn about DIDs and what DID resolution is here:

{% embed url="https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did/how-do-you-resolve-a-did" %}

## Architecture of DID Resolver(s)

You can look into our architecture and decision making in more detail in our Identity docs:

{% embed url="https://docs.cheqd.io/identity/architecture/adr-list/adr-003-did-resolver" %}
