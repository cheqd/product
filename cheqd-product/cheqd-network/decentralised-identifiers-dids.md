# Decentralised Identifiers (DIDs)

## Overview

The cheqd Network enables identity primitives, such as Decentralised Identifiers (DIDs) and DID Documents to be written and anchored to the ledger.&#x20;

This functionality allows third parties to query the ledger in order to verify the authenticity of Verifiable Credentials (signed by DIDs and verification keys) presented to them, increasing:

* [x] Trust in data presented
* [x] Trust in who is interacting with you
* [x] Security of data
* [x] Reusability of data, reducing costs

## Decentralised Identifiers (DIDs)

Decentralised Identifiers (DIDs) are the most common identity primitive to exist on-ledger.&#x20;

### What is a DID?

DIDs are unique identifiers, used to identity an organisation, individual, object or process. They can be used to enable trust between parties, without any direct relationship or centralised intermediary.&#x20;

To learn more about DIDs, check out our Learning site where we go into more detail:

{% embed url="https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did" %}

## Why should I consider using DIDs?

The benefits of DIDs can be summarised as follows:

* [x] Cost reduction in identity checks (KYC, KYB)

Identity checks are burdensome and expensive for most enterprises, costing between **$2 and $10** for basic checks, and **upwards of $50** for complex background checks.&#x20;

Identity checks are also **single-use**. Each company generally carries out its own checks, since there is no trustworthy data format for a customer to prove they have had their data checked already.

Through building trust natively into data through the use of [DIDs](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did) and [Verifiable Credentials](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-verifiable-credential-vc), the cost of KYC and KYB checks can reused at no charge.&#x20;

* [x] Reduced risk of identity fraud and theft

There are frightening statistics of identity fraud and theft resulting from phishing: In its 2021 Annual Data Breach Report, the [Identity Theft Resource Center](https://www.idtheftcenter.org/) (ITRC) reported that 1,862 data compromises occurred in 2021, breaking the previous record of 1,506 set in 2017.&#x20;

Cyberattacks are becoming more sophisticated and hard to catch-out, and with people frequently working from home, the number of successful social engineering scams has increased by 14% in 2022 alone.

Through the use of an innovation called [Peer DIDs](https://identity.foundation/peer-did-method-spec/), you can prove to third parties that you are the sole, irrefutable person/entity that has been issued a Credential.&#x20;

Fraudsters will be unable to steal your identity, since they will not have access to the Peer DID which is linked intrinsically with your device. No longer will a username and password determine the control of your data: rather your data will sit with you directly.&#x20;

* [x] Counteract digitally-based scamming and phishing&#x20;

With public DIDs, being able to tell that a company _really_ is the company they claim to be will be far easier. In the same way that _verified_ companies and persons have 'blue ticks' on social media - DIDs provide a tamperproof digital equivalent of the blue tick to all data and correspondence.&#x20;

* [x] Improve customer satisfaction and trust in digital services

Trust online is currently hard. And managing countless password-gated accounts is becoming hugely inconvenient. Pivoting to DIDs and a decentralised data economy will afford customers a far more user friendly experience, whilst complying by design with evolving data protection regulation.



## Further reading

### DID method

In order to anchor DIDs to any Utility, it is necessary to use a DID Method which defines how the DID is structured, how it is managed and how it is resolved.&#x20;

In cheqd's case, we use our own DID method: **** `did:cheqd`

{% embed url="https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:~:text=The%20cheqd%20DID%20method's%20method,the%20DID%20reference%20is%20stored." %}

### Creating a DID

Take a look at our tutorials for creating DIDs on cheqd, using the cheqd CLI as well as VDR Tools CLI:

{% embed url="https://docs.cheqd.io/identity/tutorials/cheqd-cli/dids-and-did-docs/creating-did-+-did-doc-with-cheqd-cli" %}

{% embed url="https://docs.cheqd.io/identity/tutorials/cheqd-cli/dids-and-did-docs/using-cheqd-cosmos-cli-to-manage-did-documents" %}

{% embed url="https://docs.cheqd.io/identity/tutorials/vdr-tools/identity-transactions-with-vdr-tools-cli" %}

When a DID is created, it is typically associated with a private and public key pair. The public key will be visible in the DID Document. This allows the controller/subject of the DID to generate proofs that are verifiable by anyone that has the corresponding DID Document for that DID. The process of retrieving the DID Document from a DID is called DID Resolution.

### DID resolution <a href="#did-resolution" id="did-resolution"></a>

A DID Resolver can take DID as input and resolve the DID Document. This is an important concept in how data flows in verifiable data systems.

This is expanded on in the section:

{% content-ref url="../did-resolver.md" %}
[did-resolver.md](../did-resolver.md)
{% endcontent-ref %}

