# 🔄 DID Resolver

### Overview

cheqd's product contains two DID resolvers:

* **Full resolver:** A full cheqd DID Resolver, as a module written in Go, or as a standalone web service (the goal of which is to generate a spec compliant DIDDoc, based on the [cheqd DID method](https://github.com/cheqd/cheqd-node/blob/adr-did-resolver/architecture/adr-list/adr-002-cheqd-did-method.md)); and
* **Proxy resolver:** A proxy [Universal Resolver Driver](https://github.com/decentralized-identity/universal-resolver) (the goal of this, as a microservice, is to relay requests to the above DID resolver, and to provide greater accessibility to third parties resolving cheqd DIDs).

### Context

DID resolution functions resolve a DID into a DID document by using the "Read" operation of the applicable DID method, in our case, the [cheqd DID method](https://github.com/cheqd/cheqd-node/blob/adr-did-resolver/architecture/adr-list/adr-002-cheqd-did-method.md).

All conforming DID resolvers implement the functions below, which have the following abstract forms:

```
resolve(did, resolutionOptions) → 
« didResolutionMetadata, didDocument, didDocumentMetadata »

resolveRepresentation(did, resolutionOptions) → 
« didResolutionMetadata, didDocumentStream, didDocumentMetadata »
```

These two functions enable:

* **Resolve function**: resolution of a DID to a [map](https://www.w3.org/TR/did-core/#did-resolution), with the relevant DID Document, DID Document Metadata and DID Resolution Metadata populated;
* **resolveRepresentation function**: the resolution of a byte stream format of a DID (in say JSON, JSON-LD or CBOR) back into the [map](https://www.w3.org/TR/did-core/#did-resolution) structure.

Owing to the use of the Cosmos SDK and Cosmos ecosystem, on which cheqd has been built, data written to the ledger uses the serialisation method Google Protocol Buffers (protobuf). Therefore, in order to conform with the correct syntax and structure for the map produced after resolution, cheqd's DID Resolver must implement a resolveRepresentation function that is able to take output in protobuf and convert it into a corresponding, conformant map in JSON, according to the DID core specification.

### Overall Architecture of DID Resolver(s)

#### cheqd DID Resolver + Universal Resolver Driver

This overall DID resolver architecture is intended to be decoupled from the cheqd on-ledger services, as an additional resource service, meaning updates to the resolver module do not need an on-chain upgrade.

It therefore, has multiple components, of which, are flexible and can be implemented in different ways.

This is detailed by the following flow:

![ cheqd did sequence diagram, figure 1.](https://github.com/cheqd/cheqd-node/raw/adr-did-resolver/architecture/adr-list/assets/adr-010-did-resolver/universal-resolver-sequence-diagram.png)

cheqd DIDDoc resolving module at this stage will implement simple functionality that can be a lightweight architecture of threads without synchronization. Just several classes without the use of complex design patterns.

![cheqd did resolver class diagram, figure 2](https://github.com/cheqd/cheqd-node/raw/adr-did-resolver/architecture/adr-list/assets/adr-010-did-resolver/resolver-class-diagram.png)

### cheqd full DID resolver

There are two ways to use the cheqd Resolver to return compliant DID Documents:

* As a library (go module), and
* As a standalone web service.

**Library (go module)**

* In the first case, the module can be imported simply by adding the necessary import:

```
import (
     "github.com/cheqd/cheqd-did-resolver/src"
)
```

**Standalone Web Service**

* In the second case, by launching the application with the command.

```
go run cheqd_resolver_web_service.go
```

**Pros**

* Updating the resolver software does not need updating the application on the node side
* This avoids having to go through an on-ledger governance vote, and voting period to make a change
* Separation of the system into microservices, which provides more flexibility to third parties in how they choose to resolve cheqd DIDs

**Cons**

For using the resolver separately from the ledger as an additional resolution service. All options for application interaction will be described in more detail below in [Possible flows for DID resolution](did-resolver.md#possible-flows-for-did-resolution).

* Longer chain of trust. As a result, more resources required by the client to maintain the security of the system (`node + resolver` instead of `node`)

### Universal Resolver Driver

A Universal Resolver Driver is _only_ a small Node.js package that targets a _remote_ DID Resolver endpoint (could be run by someone else) that relays/proxies requests. This allows clients who don't want to run the full resolver to just proxy/relay their requests to someone else. Can be spun up as a Docker container (required for Universal Resolver), but equally can be spun as an entirely serverless Cloudflare Worker with a very small compute footprint. Can be implemented via **itty-router**, which is a tiny NPM module that can run very fast and happily on serverless platforms.

## Possible flows for DID Resolution

### Full resolver

#### 1. Using third party cheqd resolver web service directly

cheqd provides its own web service with a DID resolver. If a client doesn't need in Universal Resolver then requests can be sent directly to cheqd Resolver Web Service. This flow is demonstrated in the second "Client <-> Web Service Resolver" section from Figure 1.

* A client sends a request to cheqd DID Resolver web service.
* cheqd DID Resolver gets DID Doc in protobuf format from the ledger throw Cosmos SDK gRPC API
* cheqd DID Resolver generates and sends an answer for the client request based on received DID Doc.

#### 2. Set up cheqd resolver web service on a client side

The same as [4. Using third party Cheqd resolver web service directly](did-resolver.md#4.-using-third-party-cheqd-resolver-web-service-directly), but the client sets up cheqd resolver web service by themselves.

#### 3. Using cheqd resolver as a Go module (library)

A client application can use cheqd Resolver as a library. This flow is demonstrated in the third "Client <-> Ledger" section from Figure 1.

* A client sends a request directly to cheqd Node throw Cosmos SDK gRPC API
* Received DID Doc in protobuf the client application can format to resolvable DID Document or DID fragment in JSON format.

### Proxy resolver (Universal resolver)

#### 1. Universal resolver on DIF side

The Decentralized Identity Foundation (DIF) has an experimental setup of Universal Resolver on the [https://dev.uniresolver.io](https://dev.uniresolver.io/).

The first "Universal Resolver" section from Figure 1 shows this flow.

* A client just sends a request to [https://dev.uniresolver.io](https://dev.uniresolver.io/).
* Universal Resolver on DIF servers uses cheqd Universal Resolver Driver to redirect client request to cheqd DID Resolver.
* cheqd DID Resolver gets DID Doc in protobuf format from the ledger throw Cosmos SDK gRPC API
* cheqd DID Resolver generates an answer for the client request based on received DID Doc.
* And sends a response to the client throw cheqd Universal Resolver Driver and Universal Resolver

#### 2. Universal resolver on the client side

Exactly the same as [Universal resolver on the DIF side](did-resolver.md#1.-universal-resolver-on-dif-side), but the client sets up Universal Resolver with Drivers by themselves.

#### 3. Universal resolver + Cheqd resolver + Cheqd Node on a client side

The same as the previous instance, [Universal resolver on the client side](did-resolver.md#2.-universal-resolver-on-a-client-side), but the client sets up:

* Universal Resolver,
* Universal Resolver Drivers,
* cheqd resolver web service,
* cheqd node.
