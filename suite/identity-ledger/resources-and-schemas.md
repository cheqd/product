# Resources and Schemas

cheqd is unique in the way that it stores and facilitates resources on the ledger. In a similar way to Hyperledger Indy, it allows schemas to be anchored to the network, yet it remains compliant with W3C standards on DIDs.

cheqd's approach to resources and schemas has the following benefits:

* [x] Increases the trust in schemas, through tying them to DIDs
* [x] Replicates the functionality of AnonCreds, the first network to do so outside of Hyperledger Indy based projects
* [x] Champions interoperability by handling and supporting multiple Credential types - building for the entire SSI ecosystem

cheqd has created a `Resource` module in its architecture to handle writes to the ledger for schemas. Going forward this module may be used for other identity primitives such as revocation registry updates.

## What is a "schema"?

Verifiable Credential schemas are another identity primitive that can be anchored to the cheqd Network. Schemas are used as a direct reference to the attributes that will be present in any given Verifiable Credential.

Through referencing a schema, third parties can feel a level of confidence that the attributes that they receive in a Credential are the same as the attributes that were initially issued directly to the Holder.

The use of schemas is also recommended for interoperability between different organisations - since if two organisations can rely on the same schema and Credential type, then they will be able to issue and receive information between each other in a trusted and standardised format.

### Schemas on ledger

Schemas, generally, do not exist on ledger; rather, they tend to exist on a website called [schema.org](https://schema.org/).

The problem with schema.org, is that it is a centralised web domain, which represents a single point of failure, if schemas are trying to be fetched and the website exhibits downtime.

Therefore, cheqd has developed functionality to anchor schemas directly to the ledger, and represent a schema with its own DID Document. This architecture removes any point of centralisation and builds a far greater level of trust in schemas themselves.

### What is the business value?

The core value here is interoperability and support for a much broader set of partners and enterprises than previously possible. Through supporting each Credential type (JSON / JSON-LD and AnonCreds) cheqd positions itself as the Layer 1 most ready for production environments and cross-ecosystem Credential interoperability.

## Learn more

Read more about our approach to resources in our Identity Documentation:

{% embed url="https://docs.cheqd.io/identity/architecture/resources-and-schemas" %}
