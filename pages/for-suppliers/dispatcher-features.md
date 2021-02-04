Transactions are executed via Dispatcher smart contracts.

## Features

* Two stages of execution
* Circuit breakers
* Role-based permissions

## Stages of Execution

There are two stages of execution in the Dispatcher. The first stage is optional, but strongly encouraged for gas efficiency.

1. Query Stage - check profitability & fetch any calculated amounts
2. Trade Stage - execute trade

The Query stage allows you to cancel a trade in-flight and save the remaining gas execution costs. The Query stage may also be used to dynamically insert a value for use in the Trade stage.

For example: Query to find the optimal value for a Trade. Cancel the Trade if Query value is too low. Otherwise insert the calculated amount in the Trade stage.

## Circuit Breakers

Circuit breakers help avoid unnecessary code execution for transactions that do not meet the desired criteria (e.g. they are mined too early or too late). Different circuit breakers are available:

  * Transaction must be profitable, required
  * Query must return some minimum value, optional
  * Transaction must be mined in a certain block number, optional
  * Transaction must be on time (within block timestamps), optional

## Role-based Permissions

There are different permissions on each Dispatcher. The role-based permissions allow many addresses to hold a role.

* Trader - execute trades
* Approver - approve tokens (for trading)
* Manage LP - add/remove whitelisted LPs
* Whitelisted LP - supply/remove bankroll
* Withdraw - withdraw revenue (cannot withdraw bankroll)
