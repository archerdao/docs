# ArchToken

### `ArchToken`

The governance token for Archer DAO

ERC-20 with supply controls + add-ons to allow for offchain signing

See EIP-712, EIP-2612, and EIP-3009 for details

## Functions:

* [`constructor(address _metadataManager, address _supplyManager, uint256 _firstSupplyChangeAllowed)`](archtoken.md#ArchToken-constructor-address-address-uint256-)
* [`setSupplyManager(address newSupplyManager)`](archtoken.md#ArchToken-setSupplyManager-address-)
* [`setMetadataManager(address newMetadataManager)`](archtoken.md#ArchToken-setMetadataManager-address-)
* [`mint(address dst, uint256 amount)`](archtoken.md#ArchToken-mint-address-uint256-)
* [`burn(address src, uint256 amount)`](archtoken.md#ArchToken-burn-address-uint256-)
* [`setMintCap(uint16 newCap)`](archtoken.md#ArchToken-setMintCap-uint16-)
* [`setSupplyChangeWaitingPeriod(uint32 period)`](archtoken.md#ArchToken-setSupplyChangeWaitingPeriod-uint32-)
* [`updateTokenMetadata(string tokenName, string tokenSymbol)`](archtoken.md#ArchToken-updateTokenMetadata-string-string-)
* [`allowance(address account, address spender)`](archtoken.md#ArchToken-allowance-address-address-)
* [`approve(address spender, uint256 amount)`](archtoken.md#ArchToken-approve-address-uint256-)
* [`increaseAllowance(address spender, uint256 addedValue)`](archtoken.md#ArchToken-increaseAllowance-address-uint256-)
* [`decreaseAllowance(address spender, uint256 subtractedValue)`](archtoken.md#ArchToken-decreaseAllowance-address-uint256-)
* [`permit(address owner, address spender, uint256 value, uint256 deadline, uint8 v, bytes32 r, bytes32 s)`](archtoken.md#ArchToken-permit-address-address-uint256-uint256-uint8-bytes32-bytes32-)
* [`balanceOf(address account)`](archtoken.md#ArchToken-balanceOf-address-)
* [`transfer(address dst, uint256 amount)`](archtoken.md#ArchToken-transfer-address-uint256-)
* [`transferFrom(address src, address dst, uint256 amount)`](archtoken.md#ArchToken-transferFrom-address-address-uint256-)
* [`transferWithAuthorization(address from, address to, uint256 value, uint256 validAfter, uint256 validBefore, bytes32 nonce, uint8 v, bytes32 r, bytes32 s)`](archtoken.md#ArchToken-transferWithAuthorization-address-address-uint256-uint256-uint256-bytes32-uint8-bytes32-bytes32-)
* [`receiveWithAuthorization(address from, address to, uint256 value, uint256 validAfter, uint256 validBefore, bytes32 nonce, uint8 v, bytes32 r, bytes32 s)`](archtoken.md#ArchToken-receiveWithAuthorization-address-address-uint256-uint256-uint256-bytes32-uint8-bytes32-bytes32-)
* [`getDomainSeparator()`](archtoken.md#ArchToken-getDomainSeparator--)

## Events:

* [`MintCapChanged(uint16 oldMintCap, uint16 newMintCap)`](archtoken.md#ArchToken-MintCapChanged-uint16-uint16-)
* [`SupplyManagerChanged(address oldManager, address newManager)`](archtoken.md#ArchToken-SupplyManagerChanged-address-address-)
* [`SupplyChangeWaitingPeriodChanged(uint32 oldWaitingPeriod, uint32 newWaitingPeriod)`](archtoken.md#ArchToken-SupplyChangeWaitingPeriodChanged-uint32-uint32-)
* [`MetadataManagerChanged(address oldManager, address newManager)`](archtoken.md#ArchToken-MetadataManagerChanged-address-address-)
* [`TokenMetaUpdated(string name, string symbol)`](archtoken.md#ArchToken-TokenMetaUpdated-string-string-)
* [`Transfer(address from, address to, uint256 value)`](archtoken.md#ArchToken-Transfer-address-address-uint256-)
* [`Approval(address owner, address spender, uint256 value)`](archtoken.md#ArchToken-Approval-address-address-uint256-)
* [`AuthorizationUsed(address authorizer, bytes32 nonce)`](archtoken.md#ArchToken-AuthorizationUsed-address-bytes32-)

## Function `constructor(address _metadataManager, address _supplyManager, uint256 _firstSupplyChangeAllowed)` <a id="ArchToken-constructor-address-address-uint256-"></a>

Construct a new Arch token

### Parameters:

* `_metadataManager`: The account with the ability to change token metadata
* `_supplyManager`: The address with minting ability
* `_firstSupplyChangeAllowed`: The timestamp after which the first supply change may occur

## Function `setSupplyManager(address newSupplyManager) → bool` <a id="ArchToken-setSupplyManager-address-"></a>

Change the supplyManager address

### Parameters:

* `newSupplyManager`: The address of the new supply manager

### Return Values:

* true if successful

## Function `setMetadataManager(address newMetadataManager) → bool` <a id="ArchToken-setMetadataManager-address-"></a>

Change the metadataManager address

### Parameters:

* `newMetadataManager`: The address of the new metadata manager

### Return Values:

* true if successful

## Function `mint(address dst, uint256 amount) → bool` <a id="ArchToken-mint-address-uint256-"></a>

Mint new tokens

### Parameters:

* `dst`: The address of the destination account
* `amount`: The number of tokens to be minted

### Return Values:

* Boolean indicating success of mint

## Function `burn(address src, uint256 amount) → bool` <a id="ArchToken-burn-address-uint256-"></a>

Burn tokens

### Parameters:

* `src`: The account that will burn tokens
* `amount`: The number of tokens to be burned

### Return Values:

* Boolean indicating success of burn

## Function `setMintCap(uint16 newCap) → bool` <a id="ArchToken-setMintCap-uint16-"></a>

Set the maximum amount of tokens that can be minted at once

### Parameters:

* `newCap`: The new mint cap in bips \(10,000 bips = 1% of totalSupply\)

### Return Values:

* true if successful

## Function `setSupplyChangeWaitingPeriod(uint32 period) → bool` <a id="ArchToken-setSupplyChangeWaitingPeriod-uint32-"></a>

Set the minimum time between supply changes

### Parameters:

* `period`: The new supply change waiting period

### Return Values:

* true if succssful

## Function `updateTokenMetadata(string tokenName, string tokenSymbol) → bool` <a id="ArchToken-updateTokenMetadata-string-string-"></a>

Update the token name and symbol

### Parameters:

* `tokenName`: The new name for the token
* `tokenSymbol`: The new symbol for the token

### Return Values:

* true if successful

## Function `allowance(address account, address spender) → uint256` <a id="ArchToken-allowance-address-address-"></a>

Get the number of tokens `spender` is approved to spend on behalf of `account`

### Parameters:

* `account`: The address of the account holding the funds
* `spender`: The address of the account spending the funds

### Return Values:

* The number of tokens approved

## Function `approve(address spender, uint256 amount) → bool` <a id="ArchToken-approve-address-uint256-"></a>

Approve `spender` to transfer up to `amount` from `src`

This will overwrite the approval amount for `spender`

and is subject to issues noted [here](https://eips.ethereum.org/EIPS/eip-20#approve)

It is recommended to use increaseAllowance and decreaseAllowance instead

### Parameters:

* `spender`: The address of the account which may transfer tokens
* `amount`: The number of tokens that are approved \(2^256-1 means infinite\)

### Return Values:

* Whether or not the approval succeeded

## Function `increaseAllowance(address spender, uint256 addedValue) → bool` <a id="ArchToken-increaseAllowance-address-uint256-"></a>

Increase the allowance by a given amount

### Parameters:

* `spender`: Spender's address
* `addedValue`: Amount of increase in allowance

### Return Values:

* True if successful

## Function `decreaseAllowance(address spender, uint256 subtractedValue) → bool` <a id="ArchToken-decreaseAllowance-address-uint256-"></a>

Decrease the allowance by a given amount

### Parameters:

* `spender`: Spender's address
* `subtractedValue`: Amount of decrease in allowance

### Return Values:

* True if successful

## Function `permit(address owner, address spender, uint256 value, uint256 deadline, uint8 v, bytes32 r, bytes32 s)` <a id="ArchToken-permit-address-address-uint256-uint256-uint8-bytes32-bytes32-"></a>

Triggers an approval from owner to spender

### Parameters:

* `owner`: The address to approve from
* `spender`: The address to be approved
* `value`: The number of tokens that are approved \(2^256-1 means infinite\)
* `deadline`: The time at which to expire the signature
* `v`: The recovery byte of the signature
* `r`: Half of the ECDSA signature pair
* `s`: Half of the ECDSA signature pair

## Function `balanceOf(address account) → uint256` <a id="ArchToken-balanceOf-address-"></a>

Get the number of tokens held by the `account`

### Parameters:

* `account`: The address of the account to get the balance of

### Return Values:

* The number of tokens held

## Function `transfer(address dst, uint256 amount) → bool` <a id="ArchToken-transfer-address-uint256-"></a>

Transfer `amount` tokens from `msg.sender` to `dst`

### Parameters:

* `dst`: The address of the destination account
* `amount`: The number of tokens to transfer

### Return Values:

* Whether or not the transfer succeeded

## Function `transferFrom(address src, address dst, uint256 amount) → bool` <a id="ArchToken-transferFrom-address-address-uint256-"></a>

Transfer `amount` tokens from `src` to `dst`

### Parameters:

* `src`: The address of the source account
* `dst`: The address of the destination account
* `amount`: The number of tokens to transfer

### Return Values:

* Whether or not the transfer succeeded

## Function `transferWithAuthorization(address from, address to, uint256 value, uint256 validAfter, uint256 validBefore, bytes32 nonce, uint8 v, bytes32 r, bytes32 s)` <a id="ArchToken-transferWithAuthorization-address-address-uint256-uint256-uint256-bytes32-uint8-bytes32-bytes32-"></a>

Transfer tokens with a signed authorization

### Parameters:

* `from`: Payer's address \(Authorizer\)
* `to`: Payee's address
* `value`: Amount to be transferred
* `validAfter`: The time after which this is valid \(unix time\)
* `validBefore`: The time before which this is valid \(unix time\)
* `nonce`: Unique nonce
* `v`: The recovery byte of the signature
* `r`: Half of the ECDSA signature pair
* `s`: Half of the ECDSA signature pair

## Function `receiveWithAuthorization(address from, address to, uint256 value, uint256 validAfter, uint256 validBefore, bytes32 nonce, uint8 v, bytes32 r, bytes32 s)` <a id="ArchToken-receiveWithAuthorization-address-address-uint256-uint256-uint256-bytes32-uint8-bytes32-bytes32-"></a>

Receive a transfer with a signed authorization from the payer

This has an additional check to ensure that the payee's address matches

the caller of this function to prevent front-running attacks.

### Parameters:

* `from`: Payer's address \(Authorizer\)
* `to`: Payee's address
* `value`: Amount to be transferred
* `validAfter`: The time after which this is valid \(unix time\)
* `validBefore`: The time before which this is valid \(unix time\)
* `nonce`: Unique nonce
* `v`: v of the signature
* `r`: r of the signature
* `s`: s of the signature

## Function `getDomainSeparator() → bytes32` <a id="ArchToken-getDomainSeparator--"></a>

EIP-712 Domain separator

## Event `MintCapChanged(uint16 oldMintCap, uint16 newMintCap)` <a id="ArchToken-MintCapChanged-uint16-uint16-"></a>

An event that's emitted when the mintCap is changed

## Event `SupplyManagerChanged(address oldManager, address newManager)` <a id="ArchToken-SupplyManagerChanged-address-address-"></a>

An event that's emitted when the supplyManager address is changed

## Event `SupplyChangeWaitingPeriodChanged(uint32 oldWaitingPeriod, uint32 newWaitingPeriod)` <a id="ArchToken-SupplyChangeWaitingPeriodChanged-uint32-uint32-"></a>

An event that's emitted when the supplyChangeWaitingPeriod is changed

## Event `MetadataManagerChanged(address oldManager, address newManager)` <a id="ArchToken-MetadataManagerChanged-address-address-"></a>

An event that's emitted when the metadataManager address is changed

## Event `TokenMetaUpdated(string name, string symbol)` <a id="ArchToken-TokenMetaUpdated-string-string-"></a>

An event that's emitted when the token name and symbol are changed

## Event `Transfer(address from, address to, uint256 value)` <a id="ArchToken-Transfer-address-address-uint256-"></a>

The standard EIP-20 transfer event

## Event `Approval(address owner, address spender, uint256 value)` <a id="ArchToken-Approval-address-address-uint256-"></a>

The standard EIP-20 approval event

## Event `AuthorizationUsed(address authorizer, bytes32 nonce)` <a id="ArchToken-AuthorizationUsed-address-bytes32-"></a>

An event that's emitted whenever an authorized transfer occurs

