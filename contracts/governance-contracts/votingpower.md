# VotingPower

### `VotingPower`

Implementation contract for voting power prism proxy

Calls should not be made directly to this contract, instead make calls to the VotingPowerPrism proxy contract

The exception to this is the `become` function specified in PrismProxyImplementation

This function is called once and is used by this contract to accept its role as the implementation for the prism proxy

## Functions:

* [`initialize(address _archToken, address _vestingContract)`](votingpower.md#VotingPower-initialize-address-address-)
* [`archToken()`](votingpower.md#VotingPower-archToken--)
* [`vestingContract()`](votingpower.md#VotingPower-vestingContract--)
* [`stakeWithPermit(uint256 amount, uint256 deadline, uint8 v, bytes32 r, bytes32 s)`](votingpower.md#VotingPower-stakeWithPermit-uint256-uint256-uint8-bytes32-bytes32-)
* [`stake(uint256 amount)`](votingpower.md#VotingPower-stake-uint256-)
* [`addVotingPowerForVestingTokens(address account, uint256 amount)`](votingpower.md#VotingPower-addVotingPowerForVestingTokens-address-uint256-)
* [`removeVotingPowerForClaimedTokens(address account, uint256 amount)`](votingpower.md#VotingPower-removeVotingPowerForClaimedTokens-address-uint256-)
* [`withdraw(uint256 amount)`](votingpower.md#VotingPower-withdraw-uint256-)
* [`getARCHAmountStaked(address staker)`](votingpower.md#VotingPower-getARCHAmountStaked-address-)
* [`getAmountStaked(address staker, address stakedToken)`](votingpower.md#VotingPower-getAmountStaked-address-address-)
* [`getARCHStake(address staker)`](votingpower.md#VotingPower-getARCHStake-address-)
* [`getStake(address staker, address stakedToken)`](votingpower.md#VotingPower-getStake-address-address-)
* [`balanceOf(address account)`](votingpower.md#VotingPower-balanceOf-address-)
* [`balanceOfAt(address account, uint256 blockNumber)`](votingpower.md#VotingPower-balanceOfAt-address-uint256-)

## Events:

* [`Staked(address user, address token, uint256 amount, uint256 votingPower)`](votingpower.md#VotingPower-Staked-address-address-uint256-uint256-)
* [`Withdrawn(address user, address token, uint256 amount, uint256 votingPower)`](votingpower.md#VotingPower-Withdrawn-address-address-uint256-uint256-)
* [`VotingPowerChanged(address voter, uint256 previousBalance, uint256 newBalance)`](votingpower.md#VotingPower-VotingPowerChanged-address-uint256-uint256-)

## Function `initialize(address _archToken, address _vestingContract)` <a id="VotingPower-initialize-address-address-"></a>

Initialize VotingPower contract

Should be called via VotingPowerPrism before calling anything else

### Parameters:

* `_archToken`: address of ARCH token
* `_vestingContract`: address of Vesting contract

## Function `archToken() → address` <a id="VotingPower-archToken--"></a>

Address of ARCH token

### Return Values:

* Address of ARCH token

## Function `vestingContract() → address` <a id="VotingPower-vestingContract--"></a>

Address of vesting contract

### Return Values:

* Address of vesting contract

## Function `stakeWithPermit(uint256 amount, uint256 deadline, uint8 v, bytes32 r, bytes32 s)` <a id="VotingPower-stakeWithPermit-uint256-uint256-uint8-bytes32-bytes32-"></a>

Stake ARCH tokens using offchain approvals to unlock voting power

### Parameters:

* `amount`: The amount to stake
* `deadline`: The time at which to expire the signature
* `v`: The recovery byte of the signature
* `r`: Half of the ECDSA signature pair
* `s`: Half of the ECDSA signature pair

## Function `stake(uint256 amount)` <a id="VotingPower-stake-uint256-"></a>

Stake ARCH tokens to unlock voting power for `msg.sender`

### Parameters:

* `amount`: The amount to stake

## Function `addVotingPowerForVestingTokens(address account, uint256 amount)` <a id="VotingPower-addVotingPowerForVestingTokens-address-uint256-"></a>

Count vesting ARCH tokens toward voting power for `account`

### Parameters:

* `account`: The recipient of voting power
* `amount`: The amount of voting power to add

## Function `removeVotingPowerForClaimedTokens(address account, uint256 amount)` <a id="VotingPower-removeVotingPowerForClaimedTokens-address-uint256-"></a>

Remove claimed vesting ARCH tokens from voting power for `account`

### Parameters:

* `account`: The account with voting power
* `amount`: The amount of voting power to remove

## Function `withdraw(uint256 amount)` <a id="VotingPower-withdraw-uint256-"></a>

Withdraw staked ARCH tokens, removing voting power for `msg.sender`

### Parameters:

* `amount`: The amount to withdraw

## Function `getARCHAmountStaked(address staker) → uint256` <a id="VotingPower-getARCHAmountStaked-address-"></a>

Get total amount of ARCH tokens staked in contract by `staker`

### Parameters:

* `staker`: The user with staked ARCH

### Return Values:

* total ARCH amount staked

## Function `getAmountStaked(address staker, address stakedToken) → uint256` <a id="VotingPower-getAmountStaked-address-address-"></a>

Get total amount of tokens staked in contract by `staker`

### Parameters:

* `staker`: The user with staked tokens
* `stakedToken`: The staked token

### Return Values:

* total amount staked

## Function `getARCHStake(address staker) → struct Stake` <a id="VotingPower-getARCHStake-address-"></a>

Get staked amount and voting power from ARCH tokens staked in contract by `staker`

### Parameters:

* `staker`: The user with staked ARCH

### Return Values:

* total ARCH staked

## Function `getStake(address staker, address stakedToken) → struct Stake` <a id="VotingPower-getStake-address-address-"></a>

Get total staked amount and voting power from `stakedToken` staked in contract by `staker`

### Parameters:

* `staker`: The user with staked tokens
* `stakedToken`: The staked token

### Return Values:

* total staked

## Function `balanceOf(address account) → uint256` <a id="VotingPower-balanceOf-address-"></a>

Gets the current votes balance for `account`

### Parameters:

* `account`: The address to get votes balance

### Return Values:

* The number of current votes for `account`

## Function `balanceOfAt(address account, uint256 blockNumber) → uint256` <a id="VotingPower-balanceOfAt-address-uint256-"></a>

Determine the prior number of votes for an account as of a block number

Block number must be a finalized block or else this function will revert to prevent misinformation.

### Parameters:

* `account`: The address of the account to check
* `blockNumber`: The block number to get the vote balance at

### Return Values:

* The number of votes the account had as of the given block

## Event `Staked(address user, address token, uint256 amount, uint256 votingPower)` <a id="VotingPower-Staked-address-address-uint256-uint256-"></a>

An event that's emitted when a user's staked balance increases

## Event `Withdrawn(address user, address token, uint256 amount, uint256 votingPower)` <a id="VotingPower-Withdrawn-address-address-uint256-uint256-"></a>

An event that's emitted when a user's staked balance decreases

## Event `VotingPowerChanged(address voter, uint256 previousBalance, uint256 newBalance)` <a id="VotingPower-VotingPowerChanged-address-uint256-uint256-"></a>

An event that's emitted when an account's vote balance changes

