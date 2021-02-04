
## Request Format

URL: https://api.archerdao.io/v1/submit-opportunity

Method: `POST`

Headers:

```
x-api-key = "02373-34dfjb-gjh4r-dfmn-23876"
Content-Type = "application/json"
```

Body:

```js
{
  "bot_id": "0", // ID of bot
  "target_block": "1230000", // Target block where you'd like the trade to take place
  "trade": "0x123435445996985686889393939494859485983693634643546", // bytecode for trade
  "estimated_profit_before_gas": "50000000", // expected profit in wei before accounting for gas
  "gas_estimate": "1000000", // Expected gas usage of trade
  "query": "0x3487508640586506070676700098876", // OPTIONAL: query bytecode to run before trade
  "query_breakeven": "4500000", // OPTIONAL: query return value minimum to continue with trade
  "input_amount": "5000000", // OPTIONAL: value to withdraw from dispatcher liquidity
  "input_asset": "ETH", // OPTIONAL: asset to withdraw from dispatcher liquidity
  "query_insert_locations": [54, 128, 220], // OPTIONAL: locations in query to insert values
  "trade_insert_locations": [56, 200] // OPTIONAL: location in trade to insert values
}
```

## Response Codes

|Code|Reason|Description|
|:---|:---|:---|
|200|Success|Successfully submitted opportunity|
|400||Malformed request|
|401|`Unauthorized`|Unknown API key|
|403||API key and Bot ID mis-match|
|404||Not found|
|406|`opportunity not profitable`|Opportunity will be unprofitable after gas costs|
|406|`opportunity too late`|Target block already passed|
|406|`opportunity too early`|Target block is too far in the future|