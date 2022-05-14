# Decentralised Identifiers (DIDs)

The cheqd Network enables identity primitives, such as Decentralised Identifiers (DIDs), DID Documents and Verifiable Credential schemas to be written and anchored to the ledger.&#x20;

This functionality allows third parties to query the ledger in order to verify the authenticity of Verifiable Credentials presented to them.

### Decentralised Identifiers (DIDs)

Decentralised Identifiers (DIDs) are the most common identity primitive to exist on-ledger.&#x20;

#### What is a DID?

DIDs are unique identifiers, used to identity an organisation, individual, object or process. They can be used to enable trust between parties, without any direct relationship or centralised intermediary.&#x20;

To learn more about DIDs, check out our Learning site where we go into more detail:

{% embed url="https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-decentralised-identifier-did" %}

#### DID Creation

When a DID is created, it is typically associated with a private and public key pair. The public key will be visible in the DID Document. This allows the controller/subject of the DID to generate proofs that are verifiable by anyone that has the corresponding DID Document for that DID. The process of retrieving the DID Document from a DID is called DID Resolution.

#### DID Resolution <a href="#did-resolution" id="did-resolution"></a>

A DID Resolver can take DID as input and resolve the DID Document. This is an important concept in how data flows in verifiable data systems.

This is expanded on in the section:

{% content-ref url="../did-resolver.md" %}
[did-resolver.md](../did-resolver.md)
{% endcontent-ref %}

#### DID method

In order to anchor DIDs to any Utility, it is necessary to use a DID Method which defines how the DID is structured, how it is managed and how it is resolved.&#x20;

In cheqd's case, we use our own DID method: **did:cheqd**

{% embed url="https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:~:text=The%20cheqd%20DID%20method's%20method,the%20DID%20reference%20is%20stored." %}

#### DID Document <a href="#did-document" id="did-document"></a>

Any W3C compliant DID must resolve to a DID Document which contains more information about the DID Subject. In the case of did:cheqd, the DID Document contains essential cryptographic information, in the form of verificationMethods, services that the DID subject has available, as well as metadata about the DID.&#x20;

This is the foundation of how persons and organisations can use DIDs to create decentralised trust.

Example of cheqd DID Document:

```
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/suites/ed25519-2020/v1"
  ],
  "id": "did:cheqd:mainnet:N22KY2Dyvmuu2PyyqSFKue",
  "verificationMethod": [
    {
      "id": "did:cheqd:mainnet:N22KY2Dyvmuu2PyyqSFKue#authKey1",
      "type": "Ed25519VerificationKey2020", // external (property value)
      "controller": "did:cheqd:mainnet:N22N22KY2Dyvmuu2PyyqSFKue",
      "publicKeyMultibase": "zAKJP3f7BD6W4iWEQ9jwndVTCBq8ua2Utt8EEjJ6Vxsf"
    },
    {
      "id": "did:cheqd:mainnet:N22KY2Dyvmuu2PyyqSFKue#capabilityInvocationKey",
      "type": "Ed25519VerificationKey2020", // external (property value)
      "controller": "did:cheqd:mainnet:N22N22KY2Dyvmuu2PyyqSFKue",
      "publicKeyMultibase": "z4BWwfeqdp1obQptLLMvPNgBw48p7og1ie6Hf9p5nTpNN"
    }
  ],
  "authentication": ["did:cheqd:mainnet:N22KY2Dyvmuu2PyyqSFKue#authKey1"],
  "capabilityInvocation": ["did:cheqd:mainnet:N22KY2Dyvmuu2PyyqSFKue#capabilityInvocationKey"],
}
```

cheqd's DID Document structure and capability is expanded on in the DID method Architecture Decision Record:

{% embed url="https://docs.cheqd.io/node/architecture/adr-list/adr-002-cheqd-did-method#:~:text=The%20cheqd%20DID%20method's%20method,the%20DID%20reference%20is%20stored." %}



