# Veramo SDK for cheqd

## Overview

[Veramo is a JavaScript Framework for Verifiable Data](https://veramo.io/). The[ Veramo SDK](https://github.com/uport-project/veramo) is an agent designed to handle multiple networks and DID methods. Current implementations of the Veramo SDK include _did:ethr, did:web, did:key_ and more.

We chose Veramo for a few key reasons.

1. **Design Principles —** The Veramo SDK was designed to be highly flexible and modular making it highly scalable and fit for a lot of complex workflows. As a result, we felt it offered a route to minimise how much needs to be built from scratch. Through its flexible plug-in system, it’s easy to pick and choose which plug-ins are most beneficial, plus it’s possible to add in our custom packages where required which we knew would be necessary from Cosmos-based transactions.
2. **Developer Experience** — The Veramo SDK has been designed in a way that offers a fast end-to-end process. Ultimately, at cheqd, we want to reduce the amount of time our team spends on SDKs and so we can maintain our focus on building ledger functionality (i.e. building our implementation of the revocation registry and the credentials payment rails).
3. **Attractive & Simple CLI —** The Veramo core API is exposed by its CLI which makes it easy to create DIDs and VCs directly from a terminal or local cloud agent.
4. **Platform Agnostic** — The Veramo packages run on Node, Browsers and React & React Native right out of the box.

### What does the Veramo SDK for cheqd allow you to do on the cheqd network? <a href="#693f" id="693f"></a>

Veramo provides an excellent foundation for clients that want to build verifiable data applications. This is because Veramo Core, the Veramo CLI and any specific plugins are available as NPM packages, enabling:

1. Identity functionality to be carried out through a native CLI interface; or
2. Identity functionality to be integrated directly into client applications through NPM packages.

More importantly, Veramo is useful for both DIDs as well as Verifiable Credentials and Verifiable Presentations. It’s not just for one side of the credential usage process.

When combining the existing packages provided by the Veramo SDK with some native packages that we’ve built at cheqd the following functionality is available on the cheqd network _(hyperlinks go to the tutorial/information for each):_

* [Create and manage keys for **signing and encryption**](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/did-operations/identity-key-handling)
* [Create and update **Decentralized Identifiers (DID)** and Decentralized Identifiers Documents (DID Docs) on cheqd (did:cheqd)](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/did-operations)
* [**Issue JSON** Verifiable Credentials (VCs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-credentials)
* [**Verify JSON** Verifiable Credentials (VCs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-credentials/verify-jwt-vc)
* [**Issue JSON** Verifiable Presentations (VPs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-presentations)
* [**Verify JSON** Verifiable Credentials (VPs) with **JWT** proof format](https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd/verifiable-presentations/verify-presentation)

With the additional [**Resource module**](https://docs.cheqd.io/identity/ledger-resources/resources) recently applied to the cheqd ledger, AnonCreds will also be possible through the[ cheqd/sdk](https://github.com/cheqd/sdk) which the Veramo SDK for cheqd uses.&#x20;

### Get into the docs!

{% embed url="https://docs.cheqd.io/identity/building-decentralized-identity-apps/veramo-sdk-for-cheqd" %}
