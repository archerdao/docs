# Multisend

### `Multisend`

Allows the sender to perform batch transfers of ARCH tokens

## Functions:

* [`constructor(contract IArchToken _token)`](multisend.md#Multisend-constructor-contract-IArchToken-)
* [`batchTransfer(uint256 totalAmount, address[] recipients, uint256[] amounts)`](multisend.md#Multisend-batchTransfer-uint256-address---uint256---)
* [`batchTransferWithPermit(uint256 totalAmount, address[] recipients, uint256[] amounts, uint256 deadline, uint8 v, bytes32 r, bytes32 s)`](multisend.md#Multisend-batchTransferWithPermit-uint256-address---uint256---uint256-uint8-bytes32-bytes32-)

## Function `constructor(contract IArchToken _token)` <a id="Multisend-constructor-contract-IArchToken-"></a>

Construct a new Multisend contract

### Parameters:

* `_token`: Address of ARCH token

## Function `batchTransfer(uint256 totalAmount, address[] recipients, uint256[] amounts)` <a id="Multisend-batchTransfer-uint256-address---uint256---"></a>

Batches multiple transfers

Must approve this contract for `totalAmount` before calling

### Parameters:

* `totalAmount`: Total amount to be transferred
* `recipients`: Array of accounts to receive transfers
* `amounts`: Array of amounts to send to accounts via transfers

## Function `batchTransferWithPermit(uint256 totalAmount, address[] recipients, uint256[] amounts, uint256 deadline, uint8 v, bytes32 r, bytes32 s)` <a id="Multisend-batchTransferWithPermit-uint256-address---uint256---uint256-uint8-bytes32-bytes32-"></a>

Batches multiple transfers with approval provided by permit function

### Parameters:

* `totalAmount`: Total amount to be transferred
* `recipients`: Array of accounts to receive transfers
* `amounts`: Array of amounts to send to accounts via transfers
* `deadline`: The time at which to expire the signature
* `v`: The recovery byte of the signature
* `r`: Half of the ECDSA signature pair
* `s`: Half of the ECDSA signature pair

