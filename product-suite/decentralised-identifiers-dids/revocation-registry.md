# Revocation Registry

## Overview

A fully privacy-preserving and scalable revocation registry is crucial for high-value uses of SSI, such as in regulated industries.

cheqd's revocation registry is designed to improve on the current revocation registry standards, such as [Revocation List 2020](https://www.google.com/search?q=revocation+list+2020\&oq=revocation\&aqs=chrome.1.69i57j69i59l2j69i60l2j69i61.1501j0j1\&sourceid=chrome\&ie=UTF-8), [Status List 2021](https://w3c-ccg.github.io/vc-status-list-2021/) and [AnonCreds revocation](https://github.com/hyperledger/indy-node/blob/master/design/anoncreds.md##revoc\_reg\_def).

This revocation registry is also a core component of how cheqd's payment rails work. cheqd's revocation registry enables an optional paid gating service for the revocation registry result. This enables cheqd to facilitate payment flows for Verifiable Credentials, such as verifier-pays-issuer.

In summary, cheqd's revocation registry has the following benefits:

* [x] Highly scalable and available, through the use of sharding
* [x] Privacy-preserving and non-correlatable by design
* [x] Facilitates native payment flows for Verifiable Credentials

### What is a Revocation Registry?

A revocation registry is a way to record the current status of Verifiable Credentials in a publicly accessible and highly available forum. Importantly, if using a distributed ledger or blockchain to hold the revocation registry, the status list must also be privacy-preserving and un-correlatable to a specific person or group of persons.

### Read more

{% embed url="https://docs.cheqd.io/node/architecture/adr-list/adr-007-revocation-registry" %}
