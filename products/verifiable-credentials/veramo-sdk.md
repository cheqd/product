# 📦 Veramo SDK for cheqd

## Overview

The Veramo SDK for cheqd is used for **integrating with cheqd's idenity functionality**. It can be used for creating and managing DIDs, keys, DID-Linked Resources and Verifiable Credentials.

## What does the Veramo SDK for cheqd allow you to do on the cheqd network? <a href="#693f" id="693f"></a>

Veramo provides an excellent foundation for clients that want to build verifiable data applications. This is because Veramo Core, the Veramo CLI and any specific plugins are available as NPM packages, enabling:

1. Identity functionality to be carried out through a native CLI interface; or
2. Identity functionality to be integrated directly into client applications through NPM packages.

More importantly, Veramo is useful for both DIDs as well as Verifiable Credentials and Verifiable Presentations. It’s not just for one side of the credential usage process.

When combining the existing packages provided by the Veramo SDK with some native packages that we’ve built at cheqd the following functionality is available on the cheqd network _(hyperlinks go to the tutorial/information for each):_

* [Create and manage keys for **signing and encryption**](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/did-operations/identity-key-handling)
* [Create and update **Decentralized Identifiers (DID)** and Decentralized Identifiers Documents (DID Docs) on cheqd (did:cheqd)](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/did-operations)
* [Create **DID-Linked Resources** and new Resource versions](https://docs.cheqd.io/identity/tutorials/on-ledger-resources)
* [**Issue JSON** Verifiable Credentials (VCs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-credentials)
* [**Verify JSON** Verifiable Credentials (VCs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-credentials/verify-jwt-vc)
* [**Issue JSON** Verifiable Presentations (VPs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-presentations)
* [**Verify JSON** Verifiable Credentials (VPs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-presentations/verify-presentation)

With the additional [**Resource module**](https://docs.cheqd.io/identity/ledger-resources/resources) recently applied to the cheqd ledger, AnonCreds will also be possible through the[ cheqd/sdk](https://github.com/cheqd/sdk) which the Veramo SDK for cheqd uses.&#x20;

## Why did we choose Veramo SDK?

[Veramo is a JavaScript Framework for Verifiable Data](https://veramo.io/). The[ Veramo SDK](https://github.com/uport-project/veramo) is an agent designed to handle multiple networks and DID methods. Current implementations of the Veramo SDK include _did:ethr, did:web, did:key_ and more.

We chose Veramo for a few key reasons.

1. **Design Principles —** The Veramo SDK was designed to be highly flexible and modular making it highly scalable and fit for a lot of complex workflows. As a result, we felt it offered a route to minimise how much needs to be built from scratch. Through its flexible plug-in system, it’s easy to pick and choose which plug-ins are most beneficial, plus it’s possible to add in our custom packages where required which we knew would be necessary from Cosmos-based transactions.
2. **Developer Experience** — The Veramo SDK has been designed in a way that offers a fast end-to-end process. Ultimately, at cheqd, we want to reduce the amount of time our team spends on SDKs and so we can maintain our focus on building ledger functionality (i.e. building our implementation of the revocation registry and the credentials payment rails).
3. **Attractive & Simple CLI —** The Veramo core API is exposed by its CLI which makes it easy to create DIDs and VCs directly from a terminal or local cloud agent.
4. **Platform Agnostic** — The Veramo packages run on Node, Browsers and React & React Native right out of the box.

## Architecture

<figure><img src="../../.gitbook/assets/veramo sdk for cheqd architecture.png" alt=""><figcaption></figcaption></figure>

_Figure 1:_ Veramo SDK for cheqd architecture with components ([editable Draw.io version](https://github.com/cheqd/identity-docs/blob/main/.gitbook/assets/veramo-sdk-for-cheqd.drawio))

### cheqd Software Development Kit

&#x20;repo: [cheqd](https://github.com/cheqd)/[sdk](https://github.com/cheqd/sdk)

The purpose of this [NPM package](https://www.npmjs.com/package/@cheqd/sdk) is to provide a mechanism of integrating cheqd functionality in an application without using a 3rd-party SDK like [Veramo SDK for cheqd](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd).

This package includes:

* [TypeScript Protobuf definitions](https://github.com/cheqd/ts-proto) for custom cheqd Cosmos SDK modules
* [CosmJS](https://github.com/cosmos/cosmjs), for base Cosmos SDK module functions

If you are using [Veramo SDK for cheqd](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd), this SDK package is automatically installed and consumed by the [did-provider-cheqd Veramo plugin](https://github.com/cheqd/did-provider-cheqd).

### cheqd x Veramo plug-in

repo: [cheqd](https://github.com/cheqd)/[did-provider-cheqd](https://github.com/cheqd/did-provider-cheqd)

The purpose of this [NPM package](https://www.npmjs.com/package/@cheqd/did-provider-cheqd) is to enable developers to interact with the cheqd ledger using [Veramo SDK](https://veramo.io/), a modular and pluggable client app SDK for decentralised identity and SSI applications.

This package includes [Veramo SDK Agent methods](https://veramo.io/docs/veramo\_agent/plugins) for use with the [Veramo CLI NPM package](https://www.npmjs.com/package/@veramo/cli). It can also be consumed as an NPM package outside Veramo CLI for building your own applications with NPM.

The package's core functionality is borrowed from [Veramo Core NPM package](https://www.npmjs.com/package/@veramo/core). and extends this to include cheqd ledger functionality, such as creating and managing DIDs.

did-provider-cheqd is the first Veramo SDK plug-in that utilises the DID Manager Update method to offer a full-body DIDDoc update for a DID on cheqd ledger, rather than individual field update transactions used more commonly in other DID methods such as [did:ethr](https://developer.uport.me/ethr-did/docs/index).

New DID creation can also be done by passing a full-body DIDoc payload in JSON, rather than having to assemble the document field-by-field.

This package works alongside other base Veramo packages:

* [`@veramo/core`](https://www.npmjs.com/package/@veramo/core)
* [`@veramo/cli`](https://www.npmjs.com/package/@veramo/cli)
* [`@veramo/credential-w3c`](https://www.npmjs.com/package/@veramo/credential-w3c)

## Setting up Veramo SDK for cheqd

* [Setup guide on Veramo SDK for cheqd](https://docs.cheqd.io/identity/guides/software-development-kits-sdks/veramo-sdk-for-cheqd/setup-cli)

## Get further into the technical docs!

{% embed url="https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd" %}
