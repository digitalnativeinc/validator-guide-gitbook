# Becoming a Validator

## Setting session keys

If all went well and validator node is behaving as expected, it is now time to rotate session keys. 

#### Following command will rotate the keys:

```bash
# replace localhost with hostname/ip if running remotely
# replace port 9933 if custom port was specified

curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys", "params":[]}' http://localhost:9933
```

#### Following result is

```text
{"jsonrpc":"2.0","result":"0xe221e3b990884fd8c7f9a5c6fd9de4604a8095580713cc4ecb655b3832b4702cb65e1b0f588a0dd19fbce5c08001d9ce6c4e219c30f526292d3858bc3800a66d56d9a881795b03827c90487b543b2d4c9b88eb55a8b62da50d9ba2f8e96d1163944f7fdf9320df89d296911574d7b3343652d37d58b13b3bd0472f6f72882b78","id":1}
```

**Copy the result value**

```text
0xe221e3b990884fd8c7f9a5c6fd9de4604a8095580713cc4ecb655b3832b4702cb65e1b0f588a0dd19fbce5c08001d9ce6c4e219c30f526292d3858bc3800a66d56d9a881795b03827c90487b543b2d4c9b88eb55a8b62da50d9ba2f8e96d1163944f7fdf9320df89d296911574d7b3343652d37d58b13b3bd0472f6f72882b78
```

Before we setup a session key we need to bond validator account using Standard Protocol wallet. Go to the [Standard Protocol Wallet](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.opportunity.standard.tech#/staking/actions).

**Click Network -&gt; Account actions -&gt; Stash button**

![](../../.gitbook/assets/image%20%2829%29.png)

You define how many tokens you want to bond. After that click **Bond** button.

![](../../.gitbook/assets/image%20%2844%29.png)

#### As you can see account was bonded. The last step is setting session key. To do that click Session Key button.

![](../../.gitbook/assets/image%20%287%29.png)

#### We are using the session key created a couple steps before \(you need to paste your own one\)

![](../../.gitbook/assets/image%20%2817%29.png)

It may take some time to start validating blocks due to increased session times. See if your validator is in 'Waiting' tab, and wait for a new session to see if you will that you start producing blocks.

## Setting on-chain identity

It is advised to always set on-chain identity so your Validator can be distingushed from the rest.

You can follow the guide from Polkadot documentation to set it - [Identity](https://wiki.polkadot.network/docs/learn-identity).

{% hint style="success" %}
After setting up validator and on-chain identity, you can request **Network Validator** role in our Discord, in order to receive up-to-date information on releases/updates.
{% endhint %}

{% hint style="warning" %}
For any issues with setting up validator, please do not hesitate to reach our via Discord channel [\#opportunity](https://discord.gg/SJmRrWRk8x).
{% endhint %}

