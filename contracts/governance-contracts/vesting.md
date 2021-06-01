# Vesting

### `Vesting`

The vesting vault contract for the initial token sale

## Functions:

* [`constructor(address _token)`](vesting.md#Vesting-constructor-address-)
* [`addTokenGrant(address recipient, uint256 startTime, uint256 amount, uint16 vestingDurationInDays, uint16 vestingCliffInDays)`](vesting.md#Vesting-addTokenGrant-address-uint256-uint256-uint16-uint16-)
* [`getTokenGrant(address recipient)`](vesting.md#Vesting-getTokenGrant-address-)
* [`calculateGrantClaim(address recipient)`](vesting.md#Vesting-calculateGrantClaim-address-)
* [`vestedBalance(address recipient)`](vesting.md#Vesting-vestedBalance-address-)
* [`claimedBalance(address recipient)`](vesting.md#Vesting-claimedBalance-address-)
* [`claimVestedTokens(address recipient)`](vesting.md#Vesting-claimVestedTokens-address-)
* [`tokensVestedPerDay(address recipient)`](vesting.md#Vesting-tokensVestedPerDay-address-)
* [`setVotingPowerContract(address newContract)`](vesting.md#Vesting-setVotingPowerContract-address-)
* [`changeOwner(address newOwner)`](vesting.md#Vesting-changeOwner-address-)

## Events:

* [`GrantAdded(address recipient, uint256 amount, uint256 startTime, uint16 vestingDurationInDays, uint16 vestingCliffInDays)`](vesting.md#Vesting-GrantAdded-address-uint256-uint256-uint16-uint16-)
* [`GrantTokensClaimed(address recipient, uint256 amountClaimed)`](vesting.md#Vesting-GrantTokensClaimed-address-uint256-)
* [`ChangedOwner(address oldOwner, address newOwner)`](vesting.md#Vesting-ChangedOwner-address-address-)
* [`ChangedVotingPower(address oldContract, address newContract)`](vesting.md#Vesting-ChangedVotingPower-address-address-)

## Function `constructor(address _token)` <a id="Vesting-constructor-address-"></a>

Construct a new Vesting contract

### Parameters:

* `_token`: Address of ARCH token

## Function `addTokenGrant(address recipient, uint256 startTime, uint256 amount, uint16 vestingDurationInDays, uint16 vestingCliffInDays)` <a id="Vesting-addTokenGrant-address-uint256-uint256-uint16-uint16-"></a>

Add a new token grant

### Parameters:

* `recipient`: The address that is receiving the grant
* `startTime`: The unix timestamp when the grant will start
* `amount`: The amount of tokens being granted
* `vestingDurationInDays`: The vesting period in days
* `vestingCliffInDays`: The vesting cliff duration in days

## Function `getTokenGrant(address recipient) → struct Vesting.Grant` <a id="Vesting-getTokenGrant-address-"></a>

Get token grant for recipient

### Parameters:

* `recipient`: The address that has a grant

### Return Values:

* the grant

## Function `calculateGrantClaim(address recipient) → uint256` <a id="Vesting-calculateGrantClaim-address-"></a>

Calculate the vested and unclaimed tokens available for `recipient` to claim

Due to rounding errors once grant duration is reached, returns the entire left grant amount

Returns 0 if cliff has not been reached

### Parameters:

* `recipient`: The address that has a grant

### Return Values:

* The amount recipient can claim

## Function `vestedBalance(address recipient) → uint256` <a id="Vesting-vestedBalance-address-"></a>

Calculate the vested \(claimed + unclaimed\) tokens for `recipient`

Returns 0 if cliff has not been reached

### Parameters:

* `recipient`: The address that has a grant

### Return Values:

* Total vested balance \(claimed + unclaimed\)

## Function `claimedBalance(address recipient) → uint256` <a id="Vesting-claimedBalance-address-"></a>

The balance claimed by `recipient`

### Parameters:

* `recipient`: The address that has a grant

### Return Values:

* the number of claimed tokens by `recipient`

## Function `claimVestedTokens(address recipient)` <a id="Vesting-claimVestedTokens-address-"></a>

Allows a grant recipient to claim their vested tokens

Errors if no tokens have vested

It is advised recipients check they are entitled to claim via `calculateGrantClaim` before calling this

### Parameters:

* `recipient`: The address that has a grant

## Function `tokensVestedPerDay(address recipient) → uint256` <a id="Vesting-tokensVestedPerDay-address-"></a>

Calculate the number of tokens that will vest per day for the given recipient

### Parameters:

* `recipient`: The address that has a grant

### Return Values:

* Number of tokens that will vest per day

## Function `setVotingPowerContract(address newContract)` <a id="Vesting-setVotingPowerContract-address-"></a>

Set voting power contract address

### Parameters:

* `newContract`: New voting power contract address

## Function `changeOwner(address newOwner)` <a id="Vesting-changeOwner-address-"></a>

Change owner of vesting contract

### Parameters:

* `newOwner`: New owner address

## Event `GrantAdded(address recipient, uint256 amount, uint256 startTime, uint16 vestingDurationInDays, uint16 vestingCliffInDays)` <a id="Vesting-GrantAdded-address-uint256-uint256-uint16-uint16-"></a>

Event emitted when a new grant is created

## Event `GrantTokensClaimed(address recipient, uint256 amountClaimed)` <a id="Vesting-GrantTokensClaimed-address-uint256-"></a>

Event emitted when tokens are claimed by a recipient from a grant

## Event `ChangedOwner(address oldOwner, address newOwner)` <a id="Vesting-ChangedOwner-address-address-"></a>

Event emitted when the owner of the vesting contract is updated

## Event `ChangedVotingPower(address oldContract, address newContract)` <a id="Vesting-ChangedVotingPower-address-address-"></a>

Event emitted when the voting power contract referenced by the vesting contract is updated

