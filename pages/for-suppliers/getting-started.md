
{% hint type="warning" %}

This is a deprecated page.

{% endhint %}

Archer allows suppliers to execute prioritized transactions. For more information, read our [introductory post](https://medium.com/archer-dao/introducing-archer-66f20d2cc425).

# How it works

Suppliers submit transactions through the Archer API. Archer executes transactions via Dispatcher smart contracts.

## Requirements

Suppliers on the Archer network are assigned 3 things:

* An API key used to submit opportunities to the network (unique to each supplier)
* A Bot ID that is used to identify the bot sending each opportunity + distribute rewards to suppliers (each supplier can have multiple)
* A Dispatcher contract that executes transactions sent via API request and, optionally, serves as a bankroll the supplier can use to support their strategies

## Example API Request

```js
{
  "bot_id": "0", // ID of bot
  "target_block": "1230000", // Target block where you'd like the trade to take place
  "trade": "0x123435445996985686889393939494859485983693634643546", // bytecode for trade
  "estimated_profit_before_gas": "50000000", // expected profit in wei before accounting for gas
  "gas_estimate": "1000000", // Expected gas usage of trade
}
```
