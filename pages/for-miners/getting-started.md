Mine smarter with Archer. Archer boosts mining revenue and integration takes less than five minutes. For more information, read our [introductory post](https://medium.com/archer-dao/introducing-archer-66f20d2cc425).

# Requirements

Block-producing nodes are eligible to join the Archer network.

{% hint style="info" %}

Not running a node? More information about how to participate in the Archer network will available in the future. Follow along on [Twitter](https://twitter.com/archer_dao) or [Telegram](https://t.me/archerdao).

{% endhint %}

# Geth Client Instructions

## Step 1 of 2

Restart your node(s) with the following additional [command-line flag](https://geth.ethereum.org/docs/interface/command-line-options) value:

```

--txpool.locals "0xa2cD5b9D50d19fDFd2F37CbaE0e880F9ce327837"

```

## Step 2 of 2

Email the peer ID (enode ID) of your node(s) to [office@archerdao.io](mailto:office@archerdao.io).

{% hint style="info" %}


You can obtain your node's peer ID by calling the `admin_nodeInfo` [as outlined in the Geth documentation](https://geth.ethereum.org/docs/rpc/ns-admin#admin_nodeinfo) and copying the "enode" value in the returned JSON object.  

{% endhint %}
