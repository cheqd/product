# ☄ Cosmos and Web 3.0

## Roadmap 2022: Cosmos and Web 3.0

### Contents

* [Ethereum bridge](cosmos-and-web-3.0.md#ethereum-bridge)
* [Airdrop frontend UI and backend](cosmos-and-web-3.0.md#airdrop-frontend-and-ui)
* [Cosmos address chain convertor](cosmos-and-web-3.0.md#cosmos-chain-address-convertor)
* [Cosmos data APIs](cosmos-and-web-3.0.md#cosmos-data-apis)
  * [Total supply](cosmos-and-web-3.0.md#total-supply)
  * [Circulating supply](cosmos-and-web-3.0.md#circulating-supply)
  * [Vesting Account Balance](cosmos-and-web-3.0.md#vesting-account-balance)
  * [Liquid Account Balance](cosmos-and-web-3.0.md#liquid-account-balance)
  * [Total Account Balance](cosmos-and-web-3.0.md#total-account-balance)

### Ethereum bridge

* [x] ERC20 CHEQ token (eCHEQ) bridge on Ethereum: Completed

**Context**

To create an ERC20 representation of the Cosmos based CHEQ token we’ve used a bridge. A blockchain bridge or ‘cross-chain bridge’ enables users to transfer assets or any form of data seamlessly from one entirely separate protocol or ecosystem to another (i.e. Solana to Ethereum, or in our case Cosmos to Ethereum and vice versa).

The [CHEQ-ERC20 wrapped token can be found here](https://etherscan.io/address/0x70EDF1c215D0ce69E7F16FD4E6276ba0d99d4de7) (you can also add it to your MetaMask wallet through this link — _go to profile summary > click ‘more’ > ‘add token to MetaMask’_ )

\
**Why did we decide on a bridge to Ethereum?**

As we build payment rails for trusted data (more on that below), we want to offer issuers, verifiers (the receivers of trusted data), and holders a choice on the means of settlement. We expect a preference for [_stablecoins_](https://en.wikipedia.org/wiki/Stablecoin) to eliminate the volatility in either pricing or settling payments for trusted data.

Find out more on our learn site below:

{% embed url="https://learn.cheqd.io/getting-set-up-on-cheqd/cheq-erc20-wrapped-token" %}

### Airdrop Frontend UI and backend

* [x] Airdrop UI frontend: Completed
* [x] Airdrop distribution backend: Completed

**Context**

We’ve open sourced the community airdrop rewards site which is built using Cloudflare Pages and designed it to be highly scalable.

Airdrop reward sites need to be more resilient to traffic spikes than most websites because, when announced, community members will tend to flock to the site to claim their rewards generating a large spike in traffic, followed by a period of much lower traffic**.** This type of traffic pattern can make prepping the server to host airdrop claim websites particularly difficult.

For example, many projects will choose to purchase a large server capacity to prevent server lag, whilst others may simply become overwhelmed with the traffic

Through using Cloudflare Pages one-to-one scaling, we made our airdrop reward site far cheaper, ensured spikes were handled with efficiency, and the likelihood of server-lag or timeouts was greatly decreased.

Check this out below:&#x20;

{% embed url="https://github.com/cheqd/airdrop-ui" %}

### Cosmos chain address convertor

* [x] Tool for converting Cosmos addresses in bulk: Completed

**Context**\
There is an assumption in the CosmosEcosystem  that wallet addresses across different chains, such as, Cosmos (ATOM), Osmosis (OSMO)  and[ ](https://twitter.com/cheqd\_io)cheqd (CHEQ), are all identical. This is because they all look very similar. However, each chain's wallet address is actually unique**.**

Our cross-chain address convertor is able to automate the derivation of any chain address from **Cosmos** address.

Want to leverage this for your project? Find out more in the link below:&#x20;

{% embed url="https://github.com/cheqd/cosmjs-cli-converter%E2%80%A6" %}
**Cosmos cross-chain address convertor**
{% endembed %}

### Cosmos Data APIs

* [x] Total supply API
* [x] Circulating Supply API
* [x] Vesting Account Balance API
* [x] Liquid Account Balance API
* [x] Total Account Balance API

**Context**

We found on our journey that there’s a LOT of stuff that we needed APIs for, but couldn’t directly fetch from base Cosmos SDK’s.

This collection of custom APIs can be deployed as a @Cloudflare Worker or compatible serverless platforms. APIs include:&#x20;

1. Total Supply
2. Circulating Supply
3. Vesting Account Balance
4. Liquid Account Balance
5. Total Account Balance&#x20;

#### Total Supply

Crypto tracking websites such as CoinMarketCap and Coin Gecko require an API endpoint for reporting the total supply of tokens in the main/primary token denomination.

While this figure is available from CosmosSDK’s built-in REST endpoint, this returns a JSON in the lowest token denomination, which cannot be parsed by CoinMarketCap / CoinGecko.

#### Circulating Supply

Likewise these sites require the circ. supply of tokens in the primary token denomination. This figure is not available from any Cosmos SDK API, because the criteria for determining circulating vs "non-circulating" accounts is defined by CoinMarketCap

This API calculates the circulating supply by subtracting the account balances of a defined list of wallet addresses ("circulating supply watchlist").

#### Vesting Account Balance

We noticed that there was no CosmosSDK API that returns balances that are not yet vested for continuous or delayed vesting accounts.

This is useful for any Cosmos project managing vesting wallets perhaps for team members or investors

#### Liquid Account Balance

Our Liquid Account Balance API is used to get the continuous/delayed vesting accounts that can be converted to liquid balances.

This ones effective when checking the liquid amount of a wallet that has vesting tokens

#### Total Account Balance

Finally, our Total Account Balance API helps to retrieve the account balance for a specified account. Of course, you could just find this info in an explorer or use the CosmosSDK REST API however we found we needed something more flexible...

As the Cosmos SDK REST API returns a JSON with the account balances it's hard to parse to something like Google Sheets to run analysis and checks. This API returns a plain number that can be directly plugged into applications, without having to parse JSON.

#### Why is this valuable

These APIs are useful for multiple reasons: Applying for listings on exchanges requires many of these APIs upfront Auditing and analysing the health of a network Creating forecasts and projections based on network usage Providing transparency of metrics to the network’s community

Through open sourcing these APIs, we want to provide an easy way for all other Cosmos projects to track these metrics, hugely reducing the time and energy needed to source these metrics from scratch.

Further context on each and how you can leverage these APIs in your project can be found through the link below:

{% embed url="https://github.com/cheqd/data-api" %}
**Cosmos Data APIs**
{% endembed %}
