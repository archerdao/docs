# Vault

### `Vault`

Contract for locking up tokens for set periods of time

Tokens locked in this contract DO NOT count towards voting power

## Functions:

* [`lockTokens(address token, address locker, address receiver, uint256 startTime, uint256 amount, uint16 lockDurationInDays)`](vault.md#Vault-lockTokens-address-address-address-uint256-uint256-uint16-)
* [`lockTokensWithPermit(address token, address locker, address receiver, uint256 startTime, uint256 amount, uint16 lockDurationInDays, uint256 deadline, uint8 v, bytes32 r, bytes32 s)`](vault.md#Vault-lockTokensWithPermit-address-address-address-uint256-uint256-uint16-uint256-uint8-bytes32-bytes32-)
* [`getActiveLocks(address receiver)`](vault.md#Vault-getActiveLocks-address-)
* [`getTokenLock(uint256 lockId)`](vault.md#Vault-getTokenLock-uint256-)
* [`getAllActiveLocks(address receiver)`](vault.md#Vault-getAllActiveLocks-address-)
* [`getLockedTokenBalance(address token, address receiver)`](vault.md#Vault-getLockedTokenBalance-address-address-)
* [`getUnlockedTokenBalance(address token, address receiver)`](vault.md#Vault-getUnlockedTokenBalance-address-address-)
* [`getLockedBalance(uint256 lockId)`](vault.md#Vault-getLockedBalance-uint256-)
* [`getUnlockedBalance(uint256 lockId)`](vault.md#Vault-getUnlockedBalance-uint256-)
* [`claimAllUnlockedTokens(uint256 lockId)`](vault.md#Vault-claimAllUnlockedTokens-uint256-)
* [`claimUnlockedTokens(uint256 lockId, uint256 amount)`](vault.md#Vault-claimUnlockedTokens-uint256-uint256-)
* [`extendLock(uint256 lockId, uint16 daysToAdd)`](vault.md#Vault-extendLock-uint256-uint16-)

## Events:

* [`LockCreated(address token, address locker, address receiver, uint256 amount, uint256 startTime, uint16 durationInDays, uint256 lockId)`](vault.md#Vault-LockCreated-address-address-address-uint256-uint256-uint16-uint256-)
* [`UnlockedTokensClaimed(address receiver, address token, uint256 amountClaimed, uint256 lockId)`](vault.md#Vault-UnlockedTokensClaimed-address-address-uint256-uint256-)
* [`LockExtended(uint16 oldDuration, uint16 newDuration, uint256 startTime, uint256 lockId)`](vault.md#Vault-LockExtended-uint16-uint16-uint256-uint256-)

## Function `lockTokens(address token, address locker, address receiver, uint256 startTime, uint256 amount, uint16 lockDurationInDays)` <a id="Vault-lockTokens-address-address-address-uint256-uint256-uint16-"></a>

Lock tokens

### Parameters:

* `locker`: The account that is locking tokens
* `receiver`: The account that will be able to retrieve unlocked tokens
* `startTime`: The unix timestamp when the lock period will start
* `amount`: The amount of tokens being locked
* `lockDurationInDays`: The lock period in days

## Function `lockTokensWithPermit(address token, address locker, address receiver, uint256 startTime, uint256 amount, uint16 lockDurationInDays, uint256 deadline, uint8 v, bytes32 r, bytes32 s)` <a id="Vault-lockTokensWithPermit-address-address-address-uint256-uint256-uint16-uint256-uint8-bytes32-bytes32-"></a>

Lock tokens

### Parameters:

* `token`: Address of token to lock
* `locker`: The account that is locking tokens
* `receiver`: The account that will be able to retrieve unlocked tokens
* `startTime`: The unix timestamp when the lock period will start
* `amount`: The amount of tokens being locked
* `lockDurationInDays`: The lock period in days
* `deadline`: The time at which to expire the signature
* `v`: The recovery byte of the signature
* `r`: Half of the ECDSA signature pair
* `s`: Half of the ECDSA signature pair

## Function `getActiveLocks(address receiver) → uint256[]` <a id="Vault-getActiveLocks-address-"></a>

Get token locks for receiver

### Parameters:

* `receiver`: The address that has locked balances

### Return Values:

* the lock ids

## Function `getTokenLock(uint256 lockId) → struct Vault.Lock` <a id="Vault-getTokenLock-uint256-"></a>

Get token lock for given lock id

### Parameters:

* `lockId`: The ID for the locked balance

### Return Values:

* the lock

## Function `getAllActiveLocks(address receiver) → struct Vault.Lock[] receiverLocks` <a id="Vault-getAllActiveLocks-address-"></a>

Get all active token locks for receiver

### Parameters:

* `receiver`: The address that has locked balances

### Return Values:

* receiverLocks the lock ids

## Function `getLockedTokenBalance(address token, address receiver) → uint256 lockedBalance` <a id="Vault-getLockedTokenBalance-address-address-"></a>

Get total locked token balance of receiver

### Parameters:

* `token`: The token to check
* `receiver`: The address that has locked balances

### Return Values:

* lockedBalance the total amount of `token` locked

## Function `getUnlockedTokenBalance(address token, address receiver) → uint256 unlockedBalance` <a id="Vault-getUnlockedTokenBalance-address-address-"></a>

Get total unlocked token balance of receiver

### Parameters:

* `token`: The token to check
* `receiver`: The address that has unlocked balances

### Return Values:

* unlockedBalance the total amount of `token` unlocked

## Function `getLockedBalance(uint256 lockId) → uint256` <a id="Vault-getLockedBalance-uint256-"></a>

Get locked balance for a given lock id

Returns 0 if duration has ended

### Parameters:

* `lockId`: The lock ID

### Return Values:

* The amount that is locked

## Function `getUnlockedBalance(uint256 lockId) → uint256` <a id="Vault-getUnlockedBalance-uint256-"></a>

Get unlocked balance for a given lock id

Returns 0 if duration has not ended

### Parameters:

* `lockId`: The lock ID

### Return Values:

* The amount that can be claimed

## Function `claimAllUnlockedTokens(uint256 lockId)` <a id="Vault-claimAllUnlockedTokens-uint256-"></a>

Allows receiver to claim all of their unlocked tokens for a given lock

Errors if no tokens are unlocked

It is advised receivers check they are entitled to claim via `getUnlockedBalance` before calling this

### Parameters:

* `lockId`: The lock id for an unlocked token balance

## Function `claimUnlockedTokens(uint256 lockId, uint256 amount)` <a id="Vault-claimUnlockedTokens-uint256-uint256-"></a>

Allows receiver to claim a portion of their unlocked tokens for a given lock

Errors if no tokens are unlocked

It is advised receivers check they are entitled to claim via `getUnlockedBalance` before calling this

### Parameters:

* `lockId`: The lock id for an unlocked token balance
* `amount`: The amount of unlocked tokens to claim

## Function `extendLock(uint256 lockId, uint16 daysToAdd)` <a id="Vault-extendLock-uint256-uint16-"></a>

Allows receiver extend lock period for a given lock

### Parameters:

* `lockId`: The lock id for a locked token balance
* `daysToAdd`: The number of days to add to duration

## Event `LockCreated(address token, address locker, address receiver, uint256 amount, uint256 startTime, uint16 durationInDays, uint256 lockId)` <a id="Vault-LockCreated-address-address-address-uint256-uint256-uint16-uint256-"></a>

Event emitted when a new lock is created

## Event `UnlockedTokensClaimed(address receiver, address token, uint256 amountClaimed, uint256 lockId)` <a id="Vault-UnlockedTokensClaimed-address-address-uint256-uint256-"></a>

Event emitted when tokens are claimed by a receiver from an unlocked balance

## Event `LockExtended(uint16 oldDuration, uint16 newDuration, uint256 startTime, uint256 lockId)` <a id="Vault-LockExtended-uint16-uint16-uint256-uint256-"></a>

Event emitted when lock duration extended

