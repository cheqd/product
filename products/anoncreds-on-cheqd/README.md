# AnonCreds on cheqd, with AFJ

## Overview

This page details the current state of support for AnonCreds on the cheqd network.

To summarise:

* Animo working with cheqd, have tested the issuance and verification of AnonCreds using the cheqd network
* This was demonstrated in an event with Animo in September. Recordings of the demo and event available below
* The approach uses cheqd's Resource module to store and retrieve CredDefs and Schema's from the cheqd Ledger
* cheqd have created an AnonCreds Object method which documents this implementation
* Building on this implementation, cheqd have supported the proposal of an extension of the [W3C Decentralized Identifiers (DIDs) 1.0 specification](https://www.w3.org/TR/did-core/) to support the resource parameter as listed in the W3C DID Specification Registries 1.0.a DID URL Resource Parameter Specification.
* To support AnonCreds for the initial demo, the Animo team made some changes to the Aries Framework Javascript SDK. However, although these changes / refactors achieved the goals for demonstrating AnonCreds on cheqd, it was not been built in a robust and extensible way.
* As a result, Animo, working with cheqd, are continuing to build out the Aries Framework Javascript SDK to support AnonCreds. Timelines for this are detailed within this page.

## cheqd AnonCreds Object Method

[In an earlier blog](https://blog.cheqd.io/our-approach-to-resources-on-ledger-25bf5690c975), we discussed our approach to resources on cheqd at length and highlighted the benefits of using on-ledger schemas, compared to other existing solutions such as schema.org.

To summarise this, cheqd has built an On-Ledger Resources Module to extend the functionality of our decentralised identity network, providing capabilities not found on other self-sovereign identity networks.

A Resource is a blob of information stored on-ledger, discoverable through the same Decentralized Identifier (DIDs) syntax that is widely used within the SSI industry.

Our objective in building resources on cheqd is to improve the way resources are stored, referenced and retrieved for our partners and the broader SSI community, in line with the existing W3C DID Core standard.

Find out more in our [learn documentation available here.](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-an-on-ledger-resource).

cheqd AnonCreds Objects build directly on this approach, in that we wanted to create an identifiable path to each specific AnonCreds Object using DID URLs.

We have now created an extensive body of documentation to explain how we can support AnonCreds on cheqd, including how we represent each of the AnonCreds Objects using DID Core conformant DID URLs.

See here for:

* [cheqd AnonCreds Schemas](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/schema-object)
* [cheqd AnonCreds CredDefs](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/creddef-object)
* [cheqd AnonCreds Revocation Registry Definitions](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/revocation-registry-definition-object)
* [cheqd AnonCreds Revocation Registry Entries](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/revocation-registry-entry-object)

Central to this approach has been removing all dependencies on Hyperledger Indy from the core “data” contents of an AnonCreds Object, and moving anything specific to a particular network to “AnonCreds Object Metadata”.

This mimics how DID Document representation is able to support multiple different approaches, where anything network specific should be represented within the “DID Document metadata” section, rather than in the core body of what is returned.

## Showcasing AnonCreds on cheqd

In September cheqd partnered co-hosted a MeetUp with Animo at their office in Utrecht as a pre-event for Rebooting the Web of Trust (RWoT) on the 19th September 2022. During this we were able to show a full end-to-end journey of Ankur, cheqd CTO, using AnonCreds. A full recording of the [AnonCreds Indy-pendence MeetUp hosted by Animo on Monday 19-09-2022 is also available](https://www.youtube.com/watch?v=_a0BrtkkO5A&t=990s).

[You can also watch a shorter version of the demo itself, here.](https://www.youtube.com/watch?v=8ERjaB6iP48)

As you’ll see in the video, using a custom version of Animo’s self-sovereign identity demo we were able to showcase:

1. AnonCreds issuance: Ankur gets his Animo identity for his name, date of birth and address as a fully functional AnonCred on cheqd.
2. AnonCreds presentation and verification: Ankur signs up to attend the RWoT conference using his Animo identity AnonCred which is verified against the cheqd network.
3. AnonCreds issuance: Ankur receives a RWoT AnonCred for his entry to the conference.
4. AnonCreds presentation and verification: Ankur presents his RWoT AnonCred to gain access to the conference.

Under the hood, you can check out the schema and credential definitions used for this AnonCred, which are identifiable using a DID URL, and stored as cheqd resources, via our DID Resolver.

* [Animo Identity schema](https://resolver.cheqd.net/1.0/identifiers/did:cheqd:testnet:zB5wPyMGYL4LbT424Z7yXHm6nZrrLqZZ/resources/4e2ba734-ae3d-4ca3-9657-c717c3dd6184)
* [Animo Identity credDef](https://resolver.cheqd.net/1.0/identifiers/did:cheqd:testnet:z5S1LLTkKwdQkRFr7FQNw5pAtBXxdRhp/resources/e42e0d69-cc0b-473c-b30c-b5c6efd01249)
* [RWoT schema](https://resolver.cheqd.net/1.0/identifiers/did:cheqd:testnet:zB5wPyMGYL4LbT424Z7yXHm6nZrrLqZZ/resources/ea5168a0-1253-4819-abf5-f937fa8cac16)
* [RWoT Credential Definition](https://resolver.cheqd.net/1.0/identifiers/did:cheqd:testnet:zGgLTsq96mTsFcFBUCxX6k4kc5i5RNpY/resources/d68c9717-8809-465a-a67a-11f5db3f14f0)

## DID URL Resource Parameter Specification

Following the implemention of the above approach which uses DID URLs to identify resources, the cheqd team, working with Drummond Reed and ToIP, have proposed an extension of the [W3C Decentralized Identifiers (DIDs) 1.0 specification](https://www.w3.org/TR/did-core/) to support the resource parameter as listed in the W3C DID Specification Registries 1.0.

The purpose of this specification is to specify how a [DID URL](https://www.w3.org/TR/did-core/#dfn-did-urls) may include a parameter that instructs a [DID resolver](https://www.w3.org/TR/did-core/#dfn-did-resolvers) to request the associated [verifiable data registry (VDR)](https://www.w3.org/TR/did-core/#dfn-verifiable-data-registry) to directly return a digital resource identified by a [decentralized identifier (DID)](https://www.w3.org/TR/did-core/#dfn-decentralized-identifiers). This parameter is only available for DID URLs whose DID method supports the parameter. The parameter also supports requesting the resource in a particular media type.

You can find this at [DID URL Resource Parameter Specification](https://wiki.trustoverip.org/display/HOME/DID+URL+Resource+Parameter+Specification).

## Integration into Aries Framework JavaScript

### Current state

In order to more fully support AnonCreds on cheqd, a more complete and tested version of Aries Framework is required than the existing version.

The timelines below help to illistrate where AFJ progress is at and what's being worked on.

### Timelines

Most of the following can be read within Timo Glastra's blog post - [How the community is coming together to implement ledger-independent AnonCreds.](https://animo.id/project/how-the-community-is-coming-together-to-implement-ledger-independent-anoncreds)

* In October 22 a proposal has been accepted for a new AnonCreds project at the Hyperledger Foundation. This is the result of the AnonCreds working group, started a few months ago by Stephen Curran, to standardize AnonCreds and extract it from the Hyperledger Indy project, meaning you can theoretically use AnonCreds credentials with any ledger. The original AnonCreds standards have been extracted into a separate AnonCreds specification, and all Indy-specific features have been generalized, paving the way for ledger-independent AnonCreds credentials. Animo is now working to implement this spec.
* Animo has submitted a proposal which contains specific work items and cost estimates for the following tasks:
  * Creating an open-source rust implementation of the ledger-independent AnonCreds specification
  * Implement ledger-independent AnonCreds into Aries Framework JavaScript with support for 'did:indy' and 'did:cheqd'
  * Implement ledger-independent AnonCreds into Aries Cloud Agent Python with support for 'did:indy' and 'did:cheqd'
* As of October end, this is €35.000 is funded, with the remaining €61.000 waiting for the final sign-off.
* Going forward, cheqd is supporting these efforts. The current implementation of AFJ with cheqd is a blend of current and future approaches to AFJ and needs to be more thoroughly documented to be made useful for partners of cheqd. This is work-in-progress and an update will be provided to our partners as soon as we have more clarity.

If you're interested in supporting Animo and cheqd's efforts for building Aries Framework Javascript into cheqd, and in turn support for AnonCreds, please reach out to the cheqd Product team at product@cheqd.io.
