# Dispatcher

### `Dispatcher`

## Functions:

* [`constructor(uint8 _version, address _queryEngine, address _roleManager, address _lpManager, address _withdrawer, address _trader, address _approver, uint256 _initialMaxLiquidity, address[] _lpWhitelist)`](dispatcher.md#Dispatcher-constructor-uint8-address-address-address-address-address-address-uint256-address---)
* [`makeTrade(bytes executeScript, uint256 ethValue)`](dispatcher.md#Trader-makeTrade-bytes-uint256-)
* [`makeTrade(bytes executeScript, uint256 ethValue, uint256 blockDeadline)`](dispatcher.md#Trader-makeTrade-bytes-uint256-uint256-)
* [`makeTrade(bytes executeScript, uint256 ethValue, uint256 minTimestamp, uint256 maxTimestamp)`](dispatcher.md#Trader-makeTrade-bytes-uint256-uint256-uint256-)
* [`makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue)`](dispatcher.md#Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-)
* [`makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue, uint256 blockDeadline)`](dispatcher.md#Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-uint256-)
* [`makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue, uint256 minTimestamp, uint256 maxTimestamp)`](dispatcher.md#Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-uint256-uint256-)
* [`isTrader(address addressToCheck)`](dispatcher.md#Trader-isTrader-address-)
* [`receive()`](dispatcher.md#Dispatcher-receive--)
* [`fallback()`](dispatcher.md#Dispatcher-fallback--)
* [`isApprover(address addressToCheck)`](dispatcher.md#Dispatcher-isApprover-address-)
* [`isWithdrawer(address addressToCheck)`](dispatcher.md#Dispatcher-isWithdrawer-address-)
* [`isLPManager(address addressToCheck)`](dispatcher.md#Dispatcher-isLPManager-address-)
* [`isWhitelistedLP(address addressToCheck)`](dispatcher.md#Dispatcher-isWhitelistedLP-address-)
* [`tokenAllowAll(address[] tokensToApprove, address spender)`](dispatcher.md#Dispatcher-tokenAllowAll-address---address-)
* [`tokenAllow(address[] tokensToApprove, uint256[] approvalAmounts, address spender)`](dispatcher.md#Dispatcher-tokenAllow-address---uint256---address-)
* [`rescueTokens(address[] tokens, uint256 amount)`](dispatcher.md#Dispatcher-rescueTokens-address---uint256-)
* [`setMaxETHLiquidity(uint256 newMax)`](dispatcher.md#Dispatcher-setMaxETHLiquidity-uint256-)
* [`provideETHLiquidity()`](dispatcher.md#Dispatcher-provideETHLiquidity--)
* [`removeETHLiquidity(uint256 amount)`](dispatcher.md#Dispatcher-removeETHLiquidity-uint256-)
* [`withdrawEth(uint256 amount)`](dispatcher.md#Dispatcher-withdrawEth-uint256-)
* [`estimateQueryCost(bytes script, uint256[] inputLocations)`](dispatcher.md#Dispatcher-estimateQueryCost-bytes-uint256---)
* [`hasRole(bytes32 role, address account)`](dispatcher.md#AccessControl-hasRole-bytes32-address-)
* [`getRoleMemberCount(bytes32 role)`](dispatcher.md#AccessControl-getRoleMemberCount-bytes32-)
* [`getRoleMember(bytes32 role, uint256 index)`](dispatcher.md#AccessControl-getRoleMember-bytes32-uint256-)
* [`getRoleAdmin(bytes32 role)`](dispatcher.md#AccessControl-getRoleAdmin-bytes32-)
* [`grantRole(bytes32 role, address account)`](dispatcher.md#AccessControl-grantRole-bytes32-address-)
* [`revokeRole(bytes32 role, address account)`](dispatcher.md#AccessControl-revokeRole-bytes32-address-)
* [`renounceRole(bytes32 role, address account)`](dispatcher.md#AccessControl-renounceRole-bytes32-address-)

## Events:

* [`MaxLiquidityUpdated(address asset, uint256 newAmount, uint256 oldAmount)`](dispatcher.md#Dispatcher-MaxLiquidityUpdated-address-uint256-uint256-)
* [`LiquidityProvided(address asset, address provider, uint256 amount)`](dispatcher.md#Dispatcher-LiquidityProvided-address-address-uint256-)
* [`LiquidityRemoved(address asset, address provider, uint256 amount)`](dispatcher.md#Dispatcher-LiquidityRemoved-address-address-uint256-)
* [`RoleAdminChanged(bytes32 role, bytes32 previousAdminRole, bytes32 newAdminRole)`](dispatcher.md#AccessControl-RoleAdminChanged-bytes32-bytes32-bytes32-)
* [`RoleGranted(bytes32 role, address account, address sender)`](dispatcher.md#AccessControl-RoleGranted-bytes32-address-address-)
* [`RoleRevoked(bytes32 role, address account, address sender)`](dispatcher.md#AccessControl-RoleRevoked-bytes32-address-address-)

## Function `constructor(uint8 _version, address _queryEngine, address _roleManager, address _lpManager, address _withdrawer, address _trader, address _approver, uint256 _initialMaxLiquidity, address[] _lpWhitelist)` <a id="Dispatcher-constructor-uint8-address-address-address-address-address-address-uint256-address---"></a>

Initializes contract, setting up initial contract permissions

### Parameters:

* `_version`: Version number of Dispatcher
* `_queryEngine`: Address of query engine contract
* `_roleManager`: Address allowed to manage contract roles
* `_lpManager`: Address allowed to manage LP whitelist
* `_withdrawer`: Address allowed to withdraw profit from contract
* `_trader`: Address allowed to make trades via this contract
* `_approver`: Address allowed to make approvals via this contract
* `_initialMaxLiquidity`: Initial max liquidity allowed in contract
* `_lpWhitelist`: list of addresses that are allowed to provide liquidity to this contract

## Function `receive()` <a id="Dispatcher-receive--"></a>

Receive function to allow contract to accept ETH

## Function `fallback()` <a id="Dispatcher-fallback--"></a>

Fallback function in case receive function is not matched

## Function `isTrader(address addressToCheck) → bool` <a id="Trader-isTrader-address-"></a>

Returns true if given address is on the list of approved traders

### Parameters:

* `addressToCheck`: the address to check

### Return Values:

* true if address is trader

## Function `makeTrade(bytes executeScript, uint256 ethValue)` <a id="Trader-makeTrade-bytes-uint256-"></a>

Makes a series of trades as single transaction if profitable without query

### Parameters:

* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `ethValue`: the amount of ETH to send with initial contract call

## Function `makeTrade(bytes executeScript, uint256 ethValue, uint256 blockDeadline)` <a id="Trader-makeTrade-bytes-uint256-uint256-"></a>

Makes a series of trades as single transaction if profitable without query + block deadline

### Parameters:

* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `ethValue`: the amount of ETH to send with initial contract call
* `blockDeadline`: block number when trade expires

## Function `makeTrade(bytes executeScript, uint256 ethValue, uint256 minTimestamp, uint256 maxTimestamp)` <a id="Trader-makeTrade-bytes-uint256-uint256-uint256-"></a>

Makes a series of trades as single transaction if profitable without query + within time window specified

### Parameters:

* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `ethValue`: the amount of ETH to send with initial contract call
* `minTimestamp`: minimum block timestamp to execute trade
* `maxTimestamp`: maximum timestamp to execute trade

## Function `makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue)` <a id="Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-"></a>

Makes a series of trades as single transaction if profitable

### Parameters:

* `queryScript`: the compiled bytecode for the series of function calls to get the final price
* `queryInputLocations`: index locations within the queryScript to insert input amounts dynamically
* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `executeInputLocations`: index locations within the executeScript to insert input amounts dynamically
* `targetPrice`: profit target for this trade, if ETH&gt;ETH, this should be ethValue + gas estimate \* gas price
* `ethValue`: the amount of ETH to send with initial contract call

## Function `makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue, uint256 blockDeadline)` <a id="Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-uint256-"></a>

Makes a series of trades as single transaction if profitable + block deadline

### Parameters:

* `queryScript`: the compiled bytecode for the series of function calls to get the final price
* `queryInputLocations`: index locations within the queryScript to insert input amounts dynamically
* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `executeInputLocations`: index locations within the executeScript to insert input amounts dynamically
* `targetPrice`: profit target for this trade, if ETH&gt;ETH, this should be ethValue + gas estimate \* gas price
* `ethValue`: the amount of ETH to send with initial contract call
* `blockDeadline`: block number when trade expires

## Function `makeTrade(bytes queryScript, uint256[] queryInputLocations, bytes executeScript, uint256[] executeInputLocations, uint256 targetPrice, uint256 ethValue, uint256 minTimestamp, uint256 maxTimestamp)` <a id="Trader-makeTrade-bytes-uint256---bytes-uint256---uint256-uint256-uint256-uint256-"></a>

Makes a series of trades as single transaction if profitable + within time window specified

### Parameters:

* `queryScript`: the compiled bytecode for the series of function calls to get the final price
* `queryInputLocations`: index locations within the queryScript to insert input amounts dynamically
* `executeScript`: the compiled bytecode for the series of function calls to execute the trade
* `executeInputLocations`: index locations within the executeScript to insert input amounts dynamically
* `targetPrice`: profit target for this trade, if ETH&gt;ETH, this should be ethValue + gas estimate \* gas price
* `ethValue`: the amount of ETH to send with initial contract call
* `minTimestamp`: minimum block timestamp to execute trade
* `maxTimestamp`: maximum timestamp to execute trade

## Function `isApprover(address addressToCheck) → bool` <a id="Dispatcher-isApprover-address-"></a>

Returns true if given address is on the list of approvers

### Parameters:

* `addressToCheck`: the address to check

### Return Values:

* true if address is approver

## Function `isWithdrawer(address addressToCheck) → bool` <a id="Dispatcher-isWithdrawer-address-"></a>

Returns true if given address is on the list of approved withdrawers

### Parameters:

* `addressToCheck`: the address to check

### Return Values:

* true if address is withdrawer

## Function `isLPManager(address addressToCheck) → bool` <a id="Dispatcher-isLPManager-address-"></a>

Returns true if given address is on the list of LP managers

### Parameters:

* `addressToCheck`: the address to check

### Return Values:

* true if address is LP manager

## Function `isWhitelistedLP(address addressToCheck) → bool` <a id="Dispatcher-isWhitelistedLP-address-"></a>

Returns true if given address is on the list of whitelisted LPs

### Parameters:

* `addressToCheck`: the address to check

### Return Values:

* true if address is whitelisted

## Function `tokenAllowAll(address[] tokensToApprove, address spender)` <a id="Dispatcher-tokenAllowAll-address---address-"></a>

Set approvals for external addresses to use Dispatcher contract tokens

### Parameters:

* `tokensToApprove`: the tokens to approve
* `spender`: the address to allow spending of token

## Function `tokenAllow(address[] tokensToApprove, uint256[] approvalAmounts, address spender)` <a id="Dispatcher-tokenAllow-address---uint256---address-"></a>

Set approvals for external addresses to use Dispatcher contract tokens

### Parameters:

* `tokensToApprove`: the tokens to approve
* `approvalAmounts`: the token approval amounts
* `spender`: the address to allow spending of token

## Function `rescueTokens(address[] tokens, uint256 amount)` <a id="Dispatcher-rescueTokens-address---uint256-"></a>

Rescue \(withdraw\) tokens from the smart contract

### Parameters:

* `tokens`: the tokens to withdraw
* `amount`: the amount of each token to withdraw. If zero, withdraws the maximum allowed amount for each token

## Function `setMaxETHLiquidity(uint256 newMax)` <a id="Dispatcher-setMaxETHLiquidity-uint256-"></a>

Set max ETH liquidity to accept for this contract

### Parameters:

* `newMax`: new max ETH liquidity

## Function `provideETHLiquidity()` <a id="Dispatcher-provideETHLiquidity--"></a>

Provide ETH liquidity to Dispatcher

## Function `removeETHLiquidity(uint256 amount)` <a id="Dispatcher-removeETHLiquidity-uint256-"></a>

Remove ETH liquidity from Dispatcher

### Parameters:

* `amount`: amount of liquidity to remove

## Function `withdrawEth(uint256 amount)` <a id="Dispatcher-withdrawEth-uint256-"></a>

Withdraw ETH from the smart contract

### Parameters:

* `amount`: the amount of ETH to withdraw.  If zero, withdraws the maximum allowed amount.

## Function `estimateQueryCost(bytes script, uint256[] inputLocations)` <a id="Dispatcher-estimateQueryCost-bytes-uint256---"></a>

A non-view function to help estimate the cost of a given query in practice

### Parameters:

* `script`: the compiled bytecode for the series of function calls to get the final price
* `inputLocations`: index locations within the script to insert input amounts dynamically

## Function `hasRole(bytes32 role, address account) → bool` <a id="AccessControl-hasRole-bytes32-address-"></a>

No description

Returns `true` if `account` has been granted `role`.

## Function `getRoleMemberCount(bytes32 role) → uint256` <a id="AccessControl-getRoleMemberCount-bytes32-"></a>

No description

Returns the number of accounts that have `role`. Can be used

together with {getRoleMember} to enumerate all bearers of a role.

## Function `getRoleMember(bytes32 role, uint256 index) → address` <a id="AccessControl-getRoleMember-bytes32-uint256-"></a>

No description

Returns one of the accounts that have `role`. `index` must be a

value between 0 and {getRoleMemberCount}, non-inclusive.

Role bearers are not sorted in any particular way, and their ordering may

change at any point.

WARNING: When using {getRoleMember} and {getRoleMemberCount}, make sure

you perform all queries on the same block. See the following

[https://forum.openzeppelin.com/t/iterating-over-elements-on-enumerableset-in-openzeppelin-contracts/2296\[forum](https://forum.openzeppelin.com/t/iterating-over-elements-on-enumerableset-in-openzeppelin-contracts/2296[forum) post\]

for more information.

## Function `getRoleAdmin(bytes32 role) → bytes32` <a id="AccessControl-getRoleAdmin-bytes32-"></a>

No description

Returns the admin role that controls `role`. See {grantRole} and

{revokeRole}.

To change a role's admin, use {\_setRoleAdmin}.

## Function `grantRole(bytes32 role, address account)` <a id="AccessControl-grantRole-bytes32-address-"></a>

No description

Grants `role` to `account`.

If `account` had not been already granted `role`, emits a {RoleGranted}

event.

Requirements:

* the caller must have `role`'s admin role.

## Function `revokeRole(bytes32 role, address account)` <a id="AccessControl-revokeRole-bytes32-address-"></a>

No description

Revokes `role` from `account`.

If `account` had been granted `role`, emits a {RoleRevoked} event.

Requirements:

* the caller must have `role`'s admin role.

## Function `renounceRole(bytes32 role, address account)` <a id="AccessControl-renounceRole-bytes32-address-"></a>

No description

Revokes `role` from the calling account.

Roles are often managed via {grantRole} and {revokeRole}: this function's

purpose is to provide a mechanism for accounts to lose their privileges

if they are compromised \(such as when a trusted device is misplaced\).

If the calling account had been granted `role`, emits a {RoleRevoked}

event.

Requirements:

* the caller must be `account`.

## Event `MaxLiquidityUpdated(address asset, uint256 newAmount, uint256 oldAmount)` <a id="Dispatcher-MaxLiquidityUpdated-address-uint256-uint256-"></a>

Max liquidity updated event

## Event `LiquidityProvided(address asset, address provider, uint256 amount)` <a id="Dispatcher-LiquidityProvided-address-address-uint256-"></a>

Liquidity Provided event

## Event `LiquidityRemoved(address asset, address provider, uint256 amount)` <a id="Dispatcher-LiquidityRemoved-address-address-uint256-"></a>

Liquidity removed event

## Event `RoleAdminChanged(bytes32 role, bytes32 previousAdminRole, bytes32 newAdminRole)` <a id="AccessControl-RoleAdminChanged-bytes32-bytes32-bytes32-"></a>

No description

Emitted when `newAdminRole` is set as `role`'s admin role, replacing `previousAdminRole`

`DEFAULT_ADMIN_ROLE` is the starting admin for all roles, despite

{RoleAdminChanged} not being emitted signaling this.

_Available since v3.1._

## Event `RoleGranted(bytes32 role, address account, address sender)` <a id="AccessControl-RoleGranted-bytes32-address-address-"></a>

No description

Emitted when `account` is granted `role`.

`sender` is the account that originated the contract call, an admin role

bearer except when using {\_setupRole}.

## Event `RoleRevoked(bytes32 role, address account, address sender)` <a id="AccessControl-RoleRevoked-bytes32-address-address-"></a>

No description

Emitted when `account` is revoked `role`.

`sender` is the account that originated the contract call:

* if using `revokeRole`, it is the admin role bearer
* if using `renounceRole`, it is the role bearer \(i.e. `account`\)

