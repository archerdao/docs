# Traders

Archer Relay gives super powers to dex traders.

* Pay only for what successfully executes
* Cancel trades for free, without complicated gas price and nonce management
* Enforce price execution guarantees

## Try it Out

Use [Archer Swap](https://swap.archerdao.io), which executes trades through Archer Relay with a familiar UI.

## Ready to Integrate?

At a high-level, you submit signed transactions to an API endpoint. Your transaction should include a deadline and execution guarantees (like minimum acceptable price).

### Example Router

ArcherSwapRouter shows how to set execution criteria in the context of an AMM trade. This can be expanded to any transaction and contract.

* [Source](https://github.com/archerdao/archerswap/blob/master/packages/smart-contracts/contracts/ArcherSwapRouter.sol)
* [Etherscan](https://etherscan.io/address/0x87535b160e251167fb7abe239d2467d1127219e4)

### Submission Options

You can choose how long transactions remain valid. In other words, your can choose to have your transaction expire if it is not mined on the next block. Or, you can submit with a deadline, in which case Archer Relay will re-submit the trade on your behalf every block.

#### Public Access

POST: https://api.archerdao.io/v1/transaction 

Payload:

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendRawTransaction",
  "tx": "0x12894509082438972378600023888fe237981132349459745972977772348999999",
  "deadline": "1234567889",
  "targetBlock": "1589003"
}
```

* `tx`: raw signed transaction
* `deadline`: See note, Unix timestamp when transaction expires (default 30 mins). We retry every block until transaction is included, the deadline passes, or you cancel.
* `targetBlock`: See note, the block number you want the transaction included. We will store the transaction until that block arrives and try submitting it then.

Note: You specify your preferred execution by supplying either `targetBlock` or `deadline`. If you provide both, `deadline` takes precedence.

#### Authorized Access

POST: https://api.archerdao.io/v1/transaction 

Contact our team for an API key.

Payload:

```js
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "archer_submitTx",
  "tx": "0x12894509082438972378600023888fe237981132349459745972977772348999999",
  "deadline": "1234567889",
  "targetBlock": "1589003"
}
```
