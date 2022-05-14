# Schemas

### What is a schema?

Verifiable Credential schemas are another identity primitive that can be anchored to the cheqd Network. Schemas are used as a direct reference to the attributes that will be present in any given Verifiable Credential.&#x20;

Through referencing a schema, third parties can feel a level of confidence that the attributes that they receive in a Credential are the same as the attributes that were initially issued directly to the Holder.&#x20;

The use of schemas is also recommended for interoperability between different organisations - since if two organisations can rely on the same schema and Credential type, then they will be able to issue and receive information between each other in a trusted and standardised format.&#x20;

#### Schemas on ledger

Schemas, generally, do not exist on ledger; rather, they tend to exist on a website called [schema.org](https://schema.org/).&#x20;

The problem with schema.org, is that it is a centralised web domain, which represents a single point of failure, if schemas are trying to be fetched and the website exhibits downtime.

Therefore, cheqd has developed functionality to anchor schemas directly to the ledger, and represent a schema with its own DID Document. This architecture removes any point of centralisation and builds a far greater level of trust in schemas themselves.&#x20;

### How are DID Documents used to fetch schemas?

There are three different data formats which are important in understanding how cheqd uses schemas:

* Issuer DID Document
* Schema DID Document
* Schema object

Each data format is important for a third party to `get` a schema which is referenced in a Verifiable Credential. A high level overview of how these data formats interact can be shown in the diagram below:&#x20;

![](<../../.gitbook/assets/Schema as DID.png>)

#### Issuer DID Document

The issuer DID Document will reference one or multiple Schema DID(s) within the `service` section. These Schema DID(s) resolve to Schema DID Document(s).For example:

```
{
  "id": "did:cheqd:mainnet:1234",
  "verification_method": [
    {
      "id": "did:cheqd:mainnet:4321#key1",
      "type": "Ed25519VerificationKey2020",
      "controller": "did:cheqd:mainnet:1234",
      "public_key_multibase": "<verification-public-key-multibase>"
    }
  ],
  "authentication": [
    "did:cheqd:mainnet:4321#key1"
  ],
  "service": [
    {
        "id":"did:cheqd:mainnet:5678#CL-Schema",
        "type": "CL-Schema",
        "serviceEndpoint": { "did:cheqd:mainnet:5678", "https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678" }
    },
    {
        "id":"did:cheqd:mainnet:9876#Schema2",
        "type": "CL-Schema",
        "serviceEndpoint": { "did:cheqd:mainnet:9876#Schema2?resource=true", "https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:9876#Schema2?resource=true" }
    },
    {
      "id":"did:cheqd:mainnet:<unique-id>#key1",
      "type": "LinkedDomains",
      "serviceEndpoint": ""
    }
  ]
}
```

In order to fetch the schema DID Document, the following steps must be carried out:

**Input**

`did:cheqd:mainnet5678#CL-Schema?resource=true`This input queries whether there is a resource within the section with an `id` of CL-Schema.

**Output**

`{ "did:cheqd:mainnet:5678","`[`https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678`](https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678)`" }`The resolved resource links to the Schema DID Document.

###

### Schema DID Document

The Schema DID Document references the Schema Object in the `service` section of the DID Document.The unique ID of the schema is the **same** as the input URL used to dereference the resource.

```
{
  "id": "did:cheqd:mainnet:5678",
  "verification_method": [
    {
      "id": "did:cheqd:mainnet:1234#key1",
      "type": "Ed25519VerificationKey2020",
      "controller": "did:cheqd:mainnet:5678",
      "public_key_multibase": "<verification-public-key-multibase>"
    }
  ],
  "authentication": [
    "did:cheqd:mainnet:1234#key1"
  ],
  "service": [
    {
        "id":"did:cheqd:mainnet:5678#CL-Schema",
        "type": "CL-Schema",
        "serviceEndpoint": { "did:cheqd:mainnet:5678#CL-Schema?resource=true", "https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678#Schema1?resource=true" }
    },
      {
        "id":"did:cheqd:mainnet:5678#JSON-Schema",
        "type": "JSONSchema2020",
        "serviceEndpoint": "https://schema.org/Person"
    },
    {
        "id":"did:cheqd:mainnet:5678#Markdown-Schema",
        "type": "Markdown",
        "serviceEndpoint": "https://github.com/cheqd/node/docs/SCHEMA.md"
    },
  ]
}
```

**Input**

`did:cheqd:mainnet:5678#CL-Schema?resource=true`This input queries whether there is a resource within the section of the DID Document with an `id` of CL-Schema.

**Output**

`"did:cheqd:mainnet:5678#CL-Schema?resource=true", "`[`https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678#Schema1?resource=true`](https://resolver.cheqd.net/did/v1/did:cheqd:mainnet:5678#Schema1?resource=true)`"`The output links to the Schema Object itself. The schema object is **not** a DID Document, despite having the `id` with the syntax of a DID Document.The Schema Object is stored on the cheqd network and can be fetched by the DID Resolver.

#### Schema Object

```
{
    "data": {
        "id":"did:cheqd:mainnet:5678#CL-Schema?resource=true",
        "attrNames": ["undergrad","last_name","first_name","birth_date","postgrad","expiry_date"],
        "name":"Degree",
        "version":"1.0",
    }
}
```

The Schema Object references the DID of the Schema DID, which proves its authenticity.The Schema Object provides the specific attributes referenced within a Verifiable Credential.
