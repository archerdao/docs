# Traders

Archer Relay gives super powers to DEX traders.

* Pay only for what successfully executes
* Cancel trades for free, without complicated gas price and nonce management
* Enforce price execution guarantees

## Try it Out

Use [Archer Swap](https://swap.archerdao.io), which executes trades through Archer Relay with a familiar UI.

## Ready to Integrate?

At a high-level, you submit signed transactions to an API endpoint, and the Archer Relay Network attempts to submit your transaction until it is mined or the deadline for the transaction passes.

### Example Router for AMM

ArcherSwapRouter shows how to set execution criteria in the context of an AMM trade. This can be expanded to any transaction and contract.

* [Source](https://github.com/archerdao/archerswap/blob/master/packages/smart-contracts/contracts/ArcherSwapRouter.sol)
* [Etherscan](https://etherscan.io/address/0x87535b160e251167fb7abe239d2467d1127219e4)

### Transaction Submission

POST: [https://api.archerdao.io/v1/transaction](https://api.archerdao.io/v1/transaction)

Payload:

```javascript
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendRawTransaction",
  "params": ["0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"] // Signed raw transaction
}
```

* `params`: raw signed transaction

The public API enforces a transaction deadline of 30 minutes. If you require more control over your transaction deadlines, want the ability to cancel your transactions manually, or want to have your transactions submitted by a certain target block, reach out to our team on Discord for an API key.

