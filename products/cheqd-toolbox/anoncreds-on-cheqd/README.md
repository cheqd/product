# 🔒 AnonCreds on cheqd

## Overview

AnonCreds on cheqd is a product milestone that requires decoupling technical dependencies between the AnonCreds specification, Hyperledger Indy and Hyperledger Aries.

Full support for AnonCreds on cheqd will come in **three** phases:

### Phase 1: cheqd AnonCreds Method

To decouple AnonCreds objects from Hyperledger Indy using cheqd resources.

Release date: **Completed**

### Phase 2: Ledger-agnostic improvements to AnonCreds specification

To remove Hyperledger Indy specific assumptions and dependencies

Release date: **January 2023**

### Phase 3: Full SDK support for AnonCreds on cheqd: February 2023

To implement ledger-agnostic specification improvements into existing SDKs.

Release date: **March 2023**

## Phase 1: cheqd AnonCreds Object Method

We have now created an extensive body of documentation to explain how we represent each of the [AnonCreds Objects using resources identifed via DID Core conformant DID URLs](https://docs.cheqd.io/identity/guides/resources/using-on-ledger-resources-to-support-anoncreds). Central to this approach has been removing all dependencies on Hyperledger Indy from the core “data” contents of an AnonCreds Object, and moving anything specific to a particular network to “AnonCreds Object Metadata”.

This mimics how DID Document representation is able to support multiple different approaches, where anything network specific should be represented within the “DID Document metadata” section, rather than in the core body of what is returned.

### Timelines

* [x] [cheqd AnonCreds Schemas](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/schema-object): Completed
* [x] [cheqd AnonCreds CredDefs](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/creddef-object): Completed
* [x] [cheqd AnonCreds Revocation Registry Definitions](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/revocation-registry-definition-object): Completed
* [x] [cheqd AnonCreds Revocation Registry Entries](https://docs.cheqd.io/identity/ledger-resources/using-on-ledger-resources-to-support-anoncreds/revocation-registry-entry-object): Completed

### Demonstration

In September cheqd partnered co-hosted a MeetUp with [Animo Solutions](https://animo.id/) at their office in Utrecht as a pre-event for Rebooting the Web of Trust (RWoT) on the 19th September 2022. During this we were able to show a full end-to-end journey of Ankur, cheqd CTO, using AnonCreds. A full recording of the [AnonCreds Indy-pendence MeetUp hosted by Animo on Monday 19-09-2022 is also available](https://www.youtube.com/watch?v=\_a0BrtkkO5A\&t=990s).

<iframe width="560" height="315" src="https://www.youtube.com/embed/8ERjaB6iP48" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Animo demo of AnonCreds within AFJ](https://www.youtube.com/watch?v=8ERjaB6iP48)

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

### Understanding how cheqd AnonCreds Object Method currently works with AnonCreds

Companies can utilise AnonCreds on cheqd. However, to currently achieve this, various _hacky_ techniques were used to fit cheqd within Aries Framework JavaScript.

Therefore, integration with cheqd using this architecture would be perfect for a Proof of Concept or a demo, but perhaps not for production environments.

The main barrier preventing full support for AnonCreds on cheqd using Aries SDKs is that AnonCreds is still dependent of Indy SDK.

When you call any function in Indy SDK, you need to use the _legacy_ Indy-style identifier format to carry out a transaction. This means that whenever a credential is saved in a wallet, that credential has indy-style identifiers for its schema, credential definition and revocation registry definition ID and Entry ID. AnonCreds do not currently natively support cheqd DID URLs.

To make cheqd work with AnonCreds, Aries needs to:

1. Request a proof in the cheqd resource DID URL format
2. Use the cheqd DID URL to resolve the resource and fetch the AnonCreds Object Metadata
3. Reconstructs the legacy Indy-style identifier using the AnonCreds Object Metadata
4. Use the Indy-style identifier to verify the AnonCreds credential.

Therefore, technically AnonCreds is currently supported on cheqd, but currently requires multiple extra steps to produce the desired outcome.&#x20;

## Phase 2: Ledger-agnostic improvements to AnonCreds specification

In order to achieve and unlock full SDK support for AnonCreds on cheqd, it is necessary to update the formal AnonCreds specification in a number of ways.

### Timeline

* [ ] Update snake case code (Indy specific) to camel case (more commonly used in wider ecosystem): **November 2022**
* [ ] Specify and differentiate between particular transaction 'requests' and 'inputs' vs the 'responses' and 'outputs': **December 2022**
* [ ] Include anything method-specific in a request should be included in a metadata section of the response: **January 2023**
* [ ] Potentially extend transactions that only require 'revRegId' to require both 'revRegDef' and 'revRegEntry' to enable the SDK to understand transactions from ledgers that don't conform to the Indy URL syntax: **January 2023**

## Phase 3: Full SDK support for AnonCreds on cheqd

In order to fully support AnonCreds on cheqd, a more complete and tested version of various Aries SDKs is required than the existing version.

Most of the following can be read within Timo Glastra's blog post - [How the community is coming together to implement ledger-independent AnonCreds.](https://animo.id/project/how-the-community-is-coming-together-to-implement-ledger-independent-anoncreds)

Animo has submitted a proposal which contains specific work items and cost estimates for the following tasks:

* Creating an open-source rust implementation of the ledger-independent AnonCreds specification
* Implement ledger-independent AnonCreds into Aries Framework JavaScript with support for 'did:indy' and 'did:cheqd'
* Implement ledger-independent AnonCreds into Aries Cloud Agent Python with support for 'did:indy' and 'did:cheqd'

As of October end, this is €35.000 is funded, with the remaining €61.000 waiting for the final sign-off.

Going forward, cheqd is supporting these efforts. The current implementation of AFJ with cheqd is a blend of current and future approaches to AFJ and needs to be more thoroughly documented to be made useful for partners of cheqd. This is work-in-progress and an update will be provided to our partners as soon as we have more clarity.

### Timeline

* [ ] Implement cheqd AnonCreds into Aries Framework JavaScript for issuing and verifying AnonCreds with schemas and credential definitions: **February 2023**
* [ ] Implement cheqd AnonCreds into Aries Cloud Agent Python for issuing and veridying AnonCreds with schemas, credential definitions and full revocation support: **March 2023**

If you're interested in supporting Animo and cheqd's efforts for building Aries Framework Javascript into cheqd, and in turn support for AnonCreds, please reach out to the cheqd Product team at product@cheqd.io.
