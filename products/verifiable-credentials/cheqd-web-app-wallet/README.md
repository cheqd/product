# 📁 cheqd web-app wallet

## Business Context

The cheqd web-app wallet offers an example implementation of how developers can leverage cheqd’s packages to create an identity application. This was initially built for IIW 34 in April 2022. It has been since updated for IIW 35 in November 2022.&#x20;

## Features include:

* Store and share digital identity credentials.
* Share multiple digital identity credentials in one presentation
* Access your CHEQ wallet account by connecting to the [Keplr browser extension](https://keplr.app/).
* Send CHEQ tokens
* Delegate, undelegate and redelegate to cheqd validators

Our starting principle for this[ ](https://twitter.com/search?q=%23IIW)wallet example implementation was to build a non-custodial wallet, which works in a browser. This is because a lot of identity wallets are "custodial" (on browser, mobile, desktop), i.e., they rely on having a 3rd party hold / operate actual credential interactions.

Quite often, this is due to technical requirements on software libraries that can \*only\* work on specific OSes. For example, many Aries frameworks rely on software libraries that are specifically compiled for iOS/Android/Linux/Windows/Mac.

Under the hood, we're doing something very similar to how password managers such as LastPass or 1Password work: only an encrypted copy of credentials is backed up. When you connect via Keplr, the backup is downloaded and decrypted only within your browser.

So what does this show? It shows a non-custodial wallet that can be recovered. Only the end-user, and whom they share it with, can see the contents. Obviously, this is only an example! An app developer could use a custodial wallet instead. Or, instead of using a Cosmos/Keplr wallet to authenticate an account, an app developer could use any other mechanism, such as username/password, SSO/OAuth etc.

To implement the credential issuance, we built this on top of [Veramo’s SDK](https://veramo.io), since we found it was highly modular.

cheqd wallet architecture \



<figure><img src="../../../.gitbook/assets/cheqd wallet repo diagram.png" alt=""><figcaption></figcaption></figure>

## 🧑‍💻🛠 Developer Guide

### cheqd wallet specific packages

If you’re exploring implementing a similar approach, here’s what you should bear in mind, broken down by each key repo involved.

### cheqd wallet

repo: [cheqd](https://github.com/cheqd)/[wallet](https://github.com/cheqd/wallet)

[cheqd Wallet](https://wallet.cheqd.io/) allows users to perform standard DeFi activities on Cosmos such as staking/delegating, voting on governance Proposals, and sending tokens. Crucially, the cheqd Wallet goes one step further than this, offering the ability to store and share [Verifiable Credentials](https://learn.cheqd.io/overview/introduction-to-decentralised-identity/what-is-a-verifiable-credential-vc).

### Wallet frontend&#x20;

repo: [cheqd](https://github.com/cheqd)/[wallet-frontend-elements](https://github.com/cheqd/wallet-frontend-elements)

The [NPM package](https://www.npmjs.com/package/@cheqd/wallet-frontend-elements) provides reusable frontend elements to be used in [cheqd Wallet](https://github.com/cheqd/wallet). This repository was a forked version of the Cosmos based [Lum network wallet](https://wallet.lum.network/welcome) ([lum-network](https://github.com/lum-network)/[wallet](https://github.com/lum-network/wallet)).

### Credential storage&#x20;

repo: [cheqd](https://github.com/cheqd)/[secret-box-service](https://github.com/cheqd/secret-box-service)

The purpose of this [NPM package](https://www.npmjs.com/package/@cheqd/secret-box-service) is to store credentials from the [wallet.cheqd.io](https://wallet.cheqd.io/) web app. As such the [wallet frontend ](https://github.com/cheqd)needs to be paired with the [secret box service](https://github.com/cheqd/secret-box-service). This works by only storing an encrypted copy of the credentials which is decrypted within the browser based on the user (holder) entering a passphrase.

### Credential issuance and verification backend&#x20;

repo: [cheqd](https://github.com/cheqd)/[credential-service](https://github.com/cheqd/credential-service)

The purpose of this service is to issue and verify credentials. This service by itself does not take care of storing the credentials. This service is also dependent on [auth0-service](https://github.com/cheqd/auth0-service). Previously [credential service](https://github.com/cheqd/credential-service) used a Cloudflare container however it’s now running in its own node container.

### User authentication with social media connection&#x20;

repo: [cheqd](https://github.com/cheqd)/[auth0-service](https://github.com/cheqd/auth0-service)

The purpose of this[ NPM package](https://www.npmjs.com/package/@cheqd/auth0-service) is to provide an OAuth connection via the Auth0 service for credentials in [wallet.cheqd.io](https://wallet.cheqd.io/) web app.&#x20;

This enables builders to offer users authentication with a Social Media account, e.g. Twitter and Discord, used in our demo.

\
