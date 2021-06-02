# Traders

Archer Relay gives super powers to DEX traders.

* Pay only for what successfully executes
* Cancel trades for free, without complicated gas price and nonce management
* Enforce price execution guarantees

## Try it Out

Use [Archer Swap](https://swap.archerdao.io), which executes trades through Archer Relay with a familiar UI.

## Ready to Integrate?

At a high-level, you submit signed transactions to an API endpoint, and the Archer Relay Network attempts to submit your transaction until it is mined or the deadline for the transaction passes. There are two requirements:

1. Form trade through ArcherSwapRouter, or similar smart contract
2. Send signed transactions to Archer Relay API endpoint

### Example Router for AMM

ArcherSwapRouter shows how to set execution criteria in the context of an AMM trade. This can be expanded to any transaction and contract.

* [Source](https://github.com/archerdao/archerswap/blob/master/packages/smart-contracts/contracts/ArcherSwapRouter.sol)
* [Etherscan](https://etherscan.io/address/0x87535b160e251167fb7abe239d2467d1127219e4)

### Request Format

This section describes a permissioned API endpoint. Please contact our team on Discord for an API key.

URL: [https://api.archerdao.io/v1/transaction](https://api.archerdao.io/v1/transaction)

Method: `POST`

Headers:

```
Authorization = "API-KEY-GOES-HERE"
Content-Type = "application/json"
```

### Transaction Submission

Body:

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "archer_submitTx",
  "tx": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675",
  "deadline": "",
  "targetBlock": ""
}
```

* `tx`: raw signed transaction
* `deadline`: See note, Unix timestamp when transaction expires. Archer Relay re-submits your transaction every block until transaction is included, the deadline passes, or you cancel.
* `targetBlock`: See note, the block number you want the transaction included. Your transaction is stored until that block arrives, then submitted.

Note: You specify your preferred execution by supplying either `targetBlock` or `deadline`. If you provide both, `deadline` takes precedence. These settings affect how long transactions remain valid. In other words, you may choose to have your transaction expire if it is not mined on the `targetBlock`. Or, you can submit with a `deadline`, in which case Archer Relay will re-submit the trade on your behalf every block.

### Transaction Cancellation:

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "archer_cancelTx",
  "tx": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"
}
```

* `tx`: raw signed transaction
