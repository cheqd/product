# Resources and Schemas

## What is a schema?

Verifiable Credential schemas are another identity primitive that can be anchored to the cheqd Network. Schemas are used as a direct reference to the attributes that will be present in any given Verifiable Credential.&#x20;

Through referencing a schema, third parties can feel a level of confidence that the attributes that they receive in a Credential are the same as the attributes that were initially issued directly to the Holder.&#x20;

The use of schemas is also recommended for interoperability between different organisations - since if two organisations can rely on the same schema and Credential type, then they will be able to issue and receive information between each other in a trusted and standardised format.&#x20;

## Schemas on ledger

Schemas, generally, do not exist on ledger; rather, they tend to exist on a website called [schema.org](https://schema.org/).&#x20;

The problem with schema.org, is that it is a centralised web domain, which represents a single point of failure, if schemas are trying to be fetched and the website exhibits downtime.

Therefore, cheqd has developed functionality to anchor schemas directly to the ledger, and represent a schema with its own DID Document. This architecture removes any point of centralisation and builds a far greater level of trust in schemas themselves.&#x20;

## What is the business value?
