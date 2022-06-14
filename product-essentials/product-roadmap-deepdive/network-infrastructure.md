# 🏗 Network Infrastructure

## Roadmap 2022: Network Infrastructure

### Contents

* [Tooling, hosting and analytics](network-infrastructure.md#tooling-hosting-and-analytics)
  * [Terraform](network-infrastructure.md#terraform)
  * [Terragrunt](network-infrastructure.md#terragrunt)
  * [Ansible](network-infrastructure.md#ansible)
  * [DataDog](network-infrastructure.md#datadog)
  * [SSH certificates for admin access via Cloudflare Teams](network-infrastructure.md#ssh-certificates-for-admin-access-via-cloudflare-teams)
  * [HashiCorp vault](network-infrastructure.md#hashicorp-vault)
* [Testnet token faucet UI](network-infrastructure.md#testnet-token-faucet-ui)

### Tooling, hosting and analytics

* [x] Terraform: Completed
* [x] Terragrunt: Completed
* [ ] Ansible: Ongoing
* [x] DataDog: Completed
* [x] SSH certificates for admin access via Cloudflare Teams: Completed
* [x] HashiCorp Vault: Completed
* [ ] Terraform, Terragrunt and Ansible package for other Cosmos networks

We've spent a lot of time in the first half of 2022 improving the infrastructure that cheqd is run on, and designing infrastructure packages that could benefit any project running a blockchain.

Through a combination of this infrastructure, Validator nodes will be able to spin up nodes on cheqd in a way which is far more efficient than before.&#x20;

#### Terraform

We have started using Terraform to define consistent and automated workflows - in order to improve efficiency and streamline the process of setting up a node on cheqd. Terraform is a form of Infra-as-code which is essentially the managing and provisioning of infrastructure through code instead of through manual processes.

You can think of it like dominos - one click of a button can result in a whole series of outcomes.

#### Terragrunt

Terragrunt works hand-in-hand with Terraform, making code more modular and facilitating different configurations of code for different use cases. You can plug in config information like CPU, RAM, Static IPs, Storage, etc., which speed things up whilst making the code more modular and reusable.

#### Ansible&#x20;

Ansible code wraps around the package established by Terraform and Terragrunt to convert the same code into more interoperable formats.&#x20;

Using Ansible, the same configurations created for setting up nodes on cheqd could be packaged in a format which could be consumed by other Cosmos networks.&#x20;

#### DataDog

DataDog is an analytics tool that records logs from cheqd network for debugging purposes, logs Tendermint metrics, Cosmos SDK based metrics and is able to connect with third party software such as Slack for notifications.&#x20;

Using DataDog enables anyone to be more proactive in monitoring the cheqd network; quickly finding and resolving issues in order to keep the network running smoothly.&#x20;

#### SSH certificates for admin access via Cloudflare Teams

This infrastructure provides **** secure one-time SSH certificates for admin access into one of the cheqd nodes. Cloudflare teams enables roles and authorisation management to set different privilege and access levels for working on the node.&#x20;

This work can be extended and used by other projects to help manage authorisation around nodes more securely and effectively.

#### HashiCorp Vault

HashiCorp Vault is about backup and secret management.

It runs a script that copies private key and node key over to the HashiCorp vault. It can be thought of as a password manager for cryptographic key material, secret management, sharing and access control.

This is valuable for anyone managing private keys, since if a key is lost or accidentally deleted, through HashiCorp Vault it can easily be restored.

### Testnet token faucet UI

This allows developers to acquire testnet tokens to start testing out and using the identity functionality on the cheqd network.

This will reduce operational overheads and simplify the process of issuing testnet tokens to developers, validators, users and clients on the network.
