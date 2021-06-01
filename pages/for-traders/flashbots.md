
Archer Relay is a service to post FlashBots bundles to Ethereum mainnet.

## FlashBots Compatible

Archer Relay is FlashBots compatible, making it straight-forward for you to submit transactions as a searcher within the FlashBots ecosystem.

We encourage suppliers to submit to many endpoints, including Archer Relay. Archer Relay combines, augments and forwards bundles to different client types. The benefits for suppliers are:
  * Exclusive hashrate
  * Smart forwarding
  * Bundle merging and augmentation
  * Get more bundles included in blocks
  * Redundancy for more reliable transaction submission

## Request Format

URL: https://api.archerdao.io/v1/bundle

Method: `POST`

Headers:

```
X-Flashbots-Signature = "0x123...:0xabc..."
Content-Type = "application/json"
```

Archer Relay requires all payloads to be signed with an ethereum wallet. See **Authentication**, below.

Body:

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendBundle",
  "params": [
    signedTxs,
    blockNumber,
    minTimestamp,
    maxTimestamp
  ]
}
```

  * **signedTxs**: Array[String], A list of signed transactions to execute in an atomic bundle
  * **blockNumber**: String, a hex encoded block number for which this bundle is valid on
  * **minTimestamp**, optional: Number, the minimum timestamp for which this bundle is valid, in seconds since the unix epoch
  * **maxTimestamp**, optional: Number, the minimum timestamp for which this bundle is valid, in seconds since the unix epoch

Example:

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendBundle",
  "params": [
    ["0x123abc...", "0x456def..."],
    "0xb63dcd",
    0,
    1615920932
  ]
}
```

## Authentication

Each request must include a signed payload in the header.

The signature is calculated by taking the EIP-191 hash of the json body encoded as UTF-8 bytes. Here's an example using ethers.js:

```js
wallet = ethers.Wallet.createRandom()
wallet.signMessage(ethers.utils.id(body))
```

Concatenate the ethereum address of the signer, a colon `:`, and the signed message. Include the output in the `X-Flashbots-Signature` HTTP header like so:

```
X-Flashbots-Signature: 0x95c622A2c597a8bdC26D371Dd3D57dA9D26052DF:0xc73d4790fed41954869625c159a4617e3374019839a8ad72de15e41371719d6873c780e00293fcdc100aa505f33dd8480e7b07551483c8c438fe8236972d26ca1c
```

Note: the signer does not have to be related to the signer of your actual transactions.
