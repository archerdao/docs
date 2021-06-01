# VotingPowerPrism

### `VotingPowerPrism`

Storage for voting power is at this address, while execution is delegated to the prism proxy implementation contract

All contracts that use voting power should reference this contract.

## Functions:

* [`constructor(address _admin)`](votingpowerprism.md#VotingPowerPrism-constructor-address-)
* [`receive()`](votingpowerprism.md#VotingPowerPrism-receive--)
* [`fallback()`](votingpowerprism.md#VotingPowerPrism-fallback--)

## Function `constructor(address _admin)` <a id="VotingPowerPrism-constructor-address-"></a>

Construct a new Voting Power Prism Proxy

Sets initial proxy admin to `_admin`

### Parameters:

* `_admin`: Initial proxy admin

## Function `receive()` <a id="VotingPowerPrism-receive--"></a>

Forwards call to implementation contract

## Function `fallback()` <a id="VotingPowerPrism-fallback--"></a>

Forwards call to implementation contract

