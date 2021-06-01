# SupplyManager

### `SupplyManager`

Responsible for enacting decisions related to ARCH token supply

Decisions are made via a timelocked propose/accept scheme

Initial proposal length \(timelock\) is 30 days

## Functions:

* [`constructor(address _token, address _admin)`](supplymanager.md#SupplyManager-constructor-address-address-)
* [`proposeMint(address dst, uint256 amount)`](supplymanager.md#SupplyManager-proposeMint-address-uint256-)
* [`cancelMint()`](supplymanager.md#SupplyManager-cancelMint--)
* [`acceptMint()`](supplymanager.md#SupplyManager-acceptMint--)
* [`proposeBurn(address src, uint256 amount)`](supplymanager.md#SupplyManager-proposeBurn-address-uint256-)
* [`cancelBurn()`](supplymanager.md#SupplyManager-cancelBurn--)
* [`acceptBurn()`](supplymanager.md#SupplyManager-acceptBurn--)
* [`proposeMintCap(uint16 newCap)`](supplymanager.md#SupplyManager-proposeMintCap-uint16-)
* [`cancelMintCap()`](supplymanager.md#SupplyManager-cancelMintCap--)
* [`acceptMintCap()`](supplymanager.md#SupplyManager-acceptMintCap--)
* [`proposeSupplyChangeWaitingPeriod(uint32 newPeriod)`](supplymanager.md#SupplyManager-proposeSupplyChangeWaitingPeriod-uint32-)
* [`cancelWaitingPeriod()`](supplymanager.md#SupplyManager-cancelWaitingPeriod--)
* [`acceptSupplyChangeWaitingPeriod()`](supplymanager.md#SupplyManager-acceptSupplyChangeWaitingPeriod--)
* [`proposeSupplyManager(address newSupplyManager)`](supplymanager.md#SupplyManager-proposeSupplyManager-address-)
* [`cancelSupplyManager()`](supplymanager.md#SupplyManager-cancelSupplyManager--)
* [`acceptSupplyManager()`](supplymanager.md#SupplyManager-acceptSupplyManager--)
* [`proposeNewProposalLength(uint32 newLength)`](supplymanager.md#SupplyManager-proposeNewProposalLength-uint32-)
* [`cancelProposalLength()`](supplymanager.md#SupplyManager-cancelProposalLength--)
* [`acceptProposalLength()`](supplymanager.md#SupplyManager-acceptProposalLength--)
* [`proposeAdmin(address newAdmin)`](supplymanager.md#SupplyManager-proposeAdmin-address-)
* [`cancelAdmin()`](supplymanager.md#SupplyManager-cancelAdmin--)
* [`acceptAdmin()`](supplymanager.md#SupplyManager-acceptAdmin--)

## Events:

* [`AdminProposed(address oldAdmin, address newAdmin, uint256 eta)`](supplymanager.md#SupplyManager-AdminProposed-address-address-uint256-)
* [`AdminCanceled(address proposedAdmin)`](supplymanager.md#SupplyManager-AdminCanceled-address-)
* [`AdminAccepted(address oldAdmin, address newAdmin)`](supplymanager.md#SupplyManager-AdminAccepted-address-address-)
* [`MintProposed(uint256 amount, address recipient, uint256 oldSupply, uint256 newSupply, uint256 eta)`](supplymanager.md#SupplyManager-MintProposed-uint256-address-uint256-uint256-uint256-)
* [`MintCanceled(uint256 amount, address recipient)`](supplymanager.md#SupplyManager-MintCanceled-uint256-address-)
* [`MintAccepted(uint256 amount, address recipient, uint256 oldSupply, uint256 newSupply)`](supplymanager.md#SupplyManager-MintAccepted-uint256-address-uint256-uint256-)
* [`BurnProposed(uint256 amount, address source, uint256 oldSupply, uint256 newSupply, uint256 eta)`](supplymanager.md#SupplyManager-BurnProposed-uint256-address-uint256-uint256-uint256-)
* [`BurnCanceled(uint256 amount, address source)`](supplymanager.md#SupplyManager-BurnCanceled-uint256-address-)
* [`BurnAccepted(uint256 amount, address source, uint256 oldSupply, uint256 newSupply)`](supplymanager.md#SupplyManager-BurnAccepted-uint256-address-uint256-uint256-)
* [`MintCapProposed(uint16 oldCap, uint16 newCap, uint256 eta)`](supplymanager.md#SupplyManager-MintCapProposed-uint16-uint16-uint256-)
* [`MintCapCanceled(uint16 proposedCap)`](supplymanager.md#SupplyManager-MintCapCanceled-uint16-)
* [`MintCapAccepted(uint16 oldCap, uint16 newCap)`](supplymanager.md#SupplyManager-MintCapAccepted-uint16-uint16-)
* [`WaitingPeriodProposed(uint32 oldWaitingPeriod, uint32 newWaitingPeriod, uint256 eta)`](supplymanager.md#SupplyManager-WaitingPeriodProposed-uint32-uint32-uint256-)
* [`WaitingPeriodCanceled(uint32 proposedWaitingPeriod)`](supplymanager.md#SupplyManager-WaitingPeriodCanceled-uint32-)
* [`WaitingPeriodAccepted(uint32 oldWaitingPeriod, uint32 newWaitingPeriod)`](supplymanager.md#SupplyManager-WaitingPeriodAccepted-uint32-uint32-)
* [`SupplyManagerProposed(address oldSupplyManager, address newSupplyManager, uint256 eta)`](supplymanager.md#SupplyManager-SupplyManagerProposed-address-address-uint256-)
* [`SupplyManagerCanceled(address proposedSupplyManager)`](supplymanager.md#SupplyManager-SupplyManagerCanceled-address-)
* [`SupplyManagerAccepted(address oldSupplyManager, address newSupplyManager)`](supplymanager.md#SupplyManager-SupplyManagerAccepted-address-address-)
* [`ProposalLengthProposed(uint32 oldProposalLength, uint32 newProposalLength, uint256 eta)`](supplymanager.md#SupplyManager-ProposalLengthProposed-uint32-uint32-uint256-)
* [`ProposalLengthCanceled(uint32 proposedProposalLength)`](supplymanager.md#SupplyManager-ProposalLengthCanceled-uint32-)
* [`ProposalLengthAccepted(uint32 oldProposalLength, uint32 newProposalLength)`](supplymanager.md#SupplyManager-ProposalLengthAccepted-uint32-uint32-)

## Function `constructor(address _token, address _admin)` <a id="SupplyManager-constructor-address-address-"></a>

Construct a new supply manager

### Parameters:

* `_token`: The address for the token
* `_admin`: The admin account for this contract

## Function `proposeMint(address dst, uint256 amount)` <a id="SupplyManager-proposeMint-address-uint256-"></a>

Propose a new token mint

### Parameters:

* `dst`: The address of the destination account
* `amount`: The number of tokens to be minted

## Function `cancelMint()` <a id="SupplyManager-cancelMint--"></a>

Cancel proposed token mint

## Function `acceptMint()` <a id="SupplyManager-acceptMint--"></a>

Accept proposed token mint

## Function `proposeBurn(address src, uint256 amount)` <a id="SupplyManager-proposeBurn-address-uint256-"></a>

Propose a new token burn

### Parameters:

* `src`: The address of the account that will burn tokens
* `amount`: The number of tokens to be burned

## Function `cancelBurn()` <a id="SupplyManager-cancelBurn--"></a>

Cancel proposed token burn

## Function `acceptBurn()` <a id="SupplyManager-acceptBurn--"></a>

Accept proposed token burn

## Function `proposeMintCap(uint16 newCap)` <a id="SupplyManager-proposeMintCap-uint16-"></a>

Propose change to the maximum amount of tokens that can be minted at once

### Parameters:

* `newCap`: The new mint cap in bips \(10,000 bips = 1% of totalSupply\)

## Function `cancelMintCap()` <a id="SupplyManager-cancelMintCap--"></a>

Cancel proposed mint cap

## Function `acceptMintCap()` <a id="SupplyManager-acceptMintCap--"></a>

Accept change to the maximum amount of tokens that can be minted at once

## Function `proposeSupplyChangeWaitingPeriod(uint32 newPeriod)` <a id="SupplyManager-proposeSupplyChangeWaitingPeriod-uint32-"></a>

Propose change to the supply change waiting period

### Parameters:

* `newPeriod`: new waiting period

## Function `cancelWaitingPeriod()` <a id="SupplyManager-cancelWaitingPeriod--"></a>

Cancel proposed waiting period

## Function `acceptSupplyChangeWaitingPeriod()` <a id="SupplyManager-acceptSupplyChangeWaitingPeriod--"></a>

Accept change to the supply change waiting period

## Function `proposeSupplyManager(address newSupplyManager)` <a id="SupplyManager-proposeSupplyManager-address-"></a>

Propose change to the supplyManager address

### Parameters:

* `newSupplyManager`: new supply manager address

## Function `cancelSupplyManager()` <a id="SupplyManager-cancelSupplyManager--"></a>

Cancel proposed supply manager update

## Function `acceptSupplyManager()` <a id="SupplyManager-acceptSupplyManager--"></a>

Accept change to the supplyManager address

## Function `proposeNewProposalLength(uint32 newLength)` <a id="SupplyManager-proposeNewProposalLength-uint32-"></a>

Propose change to the proposal length

### Parameters:

* `newLength`: new proposal length

## Function `cancelProposalLength()` <a id="SupplyManager-cancelProposalLength--"></a>

Cancel proposed update to proposal length

## Function `acceptProposalLength()` <a id="SupplyManager-acceptProposalLength--"></a>

Accept change to the proposal length

## Function `proposeAdmin(address newAdmin)` <a id="SupplyManager-proposeAdmin-address-"></a>

Propose a new admin

### Parameters:

* `newAdmin`: The address of the new admin

## Function `cancelAdmin()` <a id="SupplyManager-cancelAdmin--"></a>

Cancel proposed admin change

## Function `acceptAdmin()` <a id="SupplyManager-acceptAdmin--"></a>

Accept proposed admin

## Event `AdminProposed(address oldAdmin, address newAdmin, uint256 eta)` <a id="SupplyManager-AdminProposed-address-address-uint256-"></a>

An event that's emitted when a new admin is proposed

## Event `AdminCanceled(address proposedAdmin)` <a id="SupplyManager-AdminCanceled-address-"></a>

An event that's emitted when an admin proposal is canceled

## Event `AdminAccepted(address oldAdmin, address newAdmin)` <a id="SupplyManager-AdminAccepted-address-address-"></a>

An event that's emitted when a new admin is accepted

## Event `MintProposed(uint256 amount, address recipient, uint256 oldSupply, uint256 newSupply, uint256 eta)` <a id="SupplyManager-MintProposed-uint256-address-uint256-uint256-uint256-"></a>

An event that's emitted when a new mint is proposed

## Event `MintCanceled(uint256 amount, address recipient)` <a id="SupplyManager-MintCanceled-uint256-address-"></a>

An event that's emitted when a mint proposal is canceled

## Event `MintAccepted(uint256 amount, address recipient, uint256 oldSupply, uint256 newSupply)` <a id="SupplyManager-MintAccepted-uint256-address-uint256-uint256-"></a>

An event that's emitted when a new mint is accepted

## Event `BurnProposed(uint256 amount, address source, uint256 oldSupply, uint256 newSupply, uint256 eta)` <a id="SupplyManager-BurnProposed-uint256-address-uint256-uint256-uint256-"></a>

An event that's emitted when a new burn is proposed

## Event `BurnCanceled(uint256 amount, address source)` <a id="SupplyManager-BurnCanceled-uint256-address-"></a>

An event that's emitted when a burn proposal is canceled

## Event `BurnAccepted(uint256 amount, address source, uint256 oldSupply, uint256 newSupply)` <a id="SupplyManager-BurnAccepted-uint256-address-uint256-uint256-"></a>

An event that's emitted when a new burn is accepted

## Event `MintCapProposed(uint16 oldCap, uint16 newCap, uint256 eta)` <a id="SupplyManager-MintCapProposed-uint16-uint16-uint256-"></a>

An event that's emitted when a new mint cap is proposed

## Event `MintCapCanceled(uint16 proposedCap)` <a id="SupplyManager-MintCapCanceled-uint16-"></a>

An event that's emitted when a mint cap proposal is canceled

## Event `MintCapAccepted(uint16 oldCap, uint16 newCap)` <a id="SupplyManager-MintCapAccepted-uint16-uint16-"></a>

An event that's emitted when a new mint cap is accepted

## Event `WaitingPeriodProposed(uint32 oldWaitingPeriod, uint32 newWaitingPeriod, uint256 eta)` <a id="SupplyManager-WaitingPeriodProposed-uint32-uint32-uint256-"></a>

An event that's emitted when a new waiting period is proposed

## Event `WaitingPeriodCanceled(uint32 proposedWaitingPeriod)` <a id="SupplyManager-WaitingPeriodCanceled-uint32-"></a>

An event that's emitted when a waiting period proposal is canceled

## Event `WaitingPeriodAccepted(uint32 oldWaitingPeriod, uint32 newWaitingPeriod)` <a id="SupplyManager-WaitingPeriodAccepted-uint32-uint32-"></a>

An event that's emitted when a new waiting period is accepted

## Event `SupplyManagerProposed(address oldSupplyManager, address newSupplyManager, uint256 eta)` <a id="SupplyManager-SupplyManagerProposed-address-address-uint256-"></a>

An event that's emitted when a new supply manager is proposed

## Event `SupplyManagerCanceled(address proposedSupplyManager)` <a id="SupplyManager-SupplyManagerCanceled-address-"></a>

An event that's emitted when a supply manager proposal is canceled

## Event `SupplyManagerAccepted(address oldSupplyManager, address newSupplyManager)` <a id="SupplyManager-SupplyManagerAccepted-address-address-"></a>

An event that's emitted when a new supply manager is accepted

## Event `ProposalLengthProposed(uint32 oldProposalLength, uint32 newProposalLength, uint256 eta)` <a id="SupplyManager-ProposalLengthProposed-uint32-uint32-uint256-"></a>

An event that's emitted when a new proposal length is proposed

## Event `ProposalLengthCanceled(uint32 proposedProposalLength)` <a id="SupplyManager-ProposalLengthCanceled-uint32-"></a>

An event that's emitted when a proposal length proposal is canceled

## Event `ProposalLengthAccepted(uint32 oldProposalLength, uint32 newProposalLength)` <a id="SupplyManager-ProposalLengthAccepted-uint32-uint32-"></a>

An event that's emitted when a new proposal length is accepted

