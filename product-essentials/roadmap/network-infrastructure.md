# 🏗 Network Infrastructure

## Tooling, hosting and analytics

**Github repositories**: [**cheqd/infra**](https://github.com/cheqd/infra)

* [x] Terraform: Completed
* [x] Terragrunt: Completed
* [ ] Ansible: Ongoing
* [x] Datadog: Completed
* [x] SSH certificates for admin access via Cloudflare Teams: Completed
* [x] HashiCorp Vault: Completed
* [ ] Terraform, Terragrunt and Ansible package for other Cosmos networks

We've spent a lot of time in the first half of 2022 improving the infrastructure that cheqd is run on, and designing infrastructure packages that could benefit any project running a blockchain.

Through a combination of this infrastructure, Validator nodes will be able to spin up nodes on cheqd in a way which is far more efficient than before.

### Terraform

We have started using [HashiCorp’s Terraform](https://www.terraform.io/) to define consistent and automated workflows - in order to improve efficiency and streamline the process of setting up a node on cheqd. Terraform is a form of Infra-as-code which is essentially the managing and provisioning of infrastructure through code instead of through manual processes.

You can think of it like dominoes - one click of a button can result in a whole series of outcomes. This automation gives prospective network Validators the choice of whether they want to just install a validator node ([using our install instructions](https://docs.cheqd.io/node/setup-and-configure)), or whether they want to set up a sentry+validator architecture for more security.

### Terragrunt

[Terragrunt](https://terragrunt.gruntwork.io/) works hand-in-hand with Terraform, making code more modular, reducing repetition and facilitating different configurations of code for different use cases. You can plug in config information like CPU, RAM, Static IPs, Storage, etc., which speed things up whilst making the code more modular and reusable.

Through the use of Terragrunt, we are also able to extend our infrastructure to a full suite of supported cloud providers. This is important since our infrastructure code only works directly with [Hetzner](https://www.google.com/search?q=hetzner\&oq=hetzner\&aqs=chrome..69i57.3321j0j1\&sourceid=chrome\&ie=UTF-8) and [DigitalOcean](https://www.digitalocean.com/) cloud providers (for their good balance of cost vs performance). We did, however, recognise that many people use [AWS](https://aws.amazon.com/) or [Azure](https://azure.microsoft.com/en-au/). Terragrunt therefore, performs the role of a wrapper to make our infrastructure available in Hetzner and DigitalOcean, as well as making it easier to utilise with AWS or Azure.

### Ansible

[Ansible](https://www.ansible.com/) allows node operators to update software on their nodes, carry out configuration changes etc, during the first install and subsequent maintenance. In a similar way to Terragrunt, Ansible code can also act as a wrapper, converting the code established via Terragrunt and Terraform into more cross-compatible formats.

Using Ansible, the same configurations created for setting up nodes on cheqd could be packaged in a format which could be consumed by other Cosmos networks. Therefore, this could have a knock-on effect for benefiting the entire Cosmos ecosystem for running sentry+validator infrastructure.

### Datadog

[Datadog](https://www.datadoghq.com/) is an analytics tool that records logs from cheqd network for debugging purposes, logs Tendermint metrics, Cosmos SDK based metrics and is able to connect with third party software such as Slack for notifications.

Using Datadog enables anyone to be more proactive in monitoring the cheqd network; quickly finding and resolving issues in order to keep the network running smoothly.

### SSH certificates for admin access via Cloudflare Teams

This infrastructure provides secure one-time SSH certificates for admin access into one of the cheqd nodes. Cloudflare teams enables roles and authorisation management to set different privilege and access levels for working on the node.

This work can be extended and used by other projects to help manage authorisation around nodes more securely and effectively.

### HashiCorp Vault

[HashiCorp Vault](https://www.hashicorp.com/products/vault) is about backup and secrets management.

It runs a script that copies private key and node key over to the HashiCorp vault. It can be thought of as a password manager for cryptographic key material, secret management, sharing and access control.

This is valuable for anyone managing private keys, since if a key is lost or accidentally deleted, through HashiCorp Vault it can easily be restored.

## Testnet token faucet UI

**Github repository**: [cheqd/faucet-ui](https://github.com/cheqd/faucet-ui)

The [cheqd testnet faucet](https://testnet-faucet.cheqd.io) is a self-serve site that allows app developers and node operators who want to try out our identity functionality or node operations to request test CHEQ tokens, without having to spend money to acquire “real” CHEQ tokens on mainnet.

We built this using [Cloudflare Pages](https://developers.cloudflare.com/pages/) as it provides a fast way to create serverless applications which are able to scale up and down dynamically depending on traffic, especially for something such as a testnet faucet which may not receive consistent levels of traffic. The backend for this faucet works using [CosmJS faucet](https://github.com/cosmos/cosmjs/tree/main/packages/faucet).
