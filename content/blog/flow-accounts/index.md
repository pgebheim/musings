---
title: Flow's Accounts are Awesome
date: "2022-11-14T15:20:24Z"
description: "Flow's accounts let users and applications interact with the blockchain in simple, powerful ways."
---

The Flow blockchain was designed from the ground-up to make it straightforward
for users to own, control, and give access to different assets which are stored on chain. A major part of this is based in the Cadence programming language's use of resource-oriented programming. The base protocol layer of Flow also plays a role through the core functionality of accounts.

## Accounts, not keys
For flow the concept of an Account, that is a thing that exists on the blockchain that can hold resources, has access to storage, and can submit transaction is distrinct from the concept of a key. Each Flow account is controlled by one or more keys. Furthermore, each key can also be associated with zero or more accounts.

This means that on a Flow account, users can:
- Rotate keys in case one may have been compromised.
- Create a setup where more than one key is needed in order to authorize transactions.
- Create a social-recovery system where a group of trusted individuals can come together to authorize transactions for an account, while allowing one master key to always control that account as well.

### Use-Case 1: Sponsored Transactions

In the Ethereum world it is common to see dapp developers and users requesting the ability to have some other entity pay for gas, or for users to be able to pay for gas in a non-eth token. Some wallets such as Argent have differentiated themselves by building these features into their products. Unfortunately, the infrastructure and mechanics necessary to accomplish this task are not simple to implement, and create scenarios where users have difficulty using their own wallets.

In Flow the a transaction "Payer" is a first-class part of a transaction. As outlined in the [flow documentation](https://developers.flow.com/learn/concepts/transaction-signing) a transaction consists of
1. A proposer
2. A payer
3. One or more authorizers.

The payer is an account which has enough Flow to cover the maximum cost of any transction it signs for. This built-in support for transaction payer separate from the accounts which state a transaction mutates opens many possibilities for Dapps and Wallets on Flow. In fact, this feature powers many existing Flow wallets, such as Dapper Wallet and Blocto, which pay for the transaction costs on behalf of users. As a dapp developer, you could also choose to pay for transactions on behalf of users of your application. This ability bridges the gap of user expectations from a web2 world, where users aren't expected to pay to take actions in applications, and the web3 world where fee mechanisms are important for the health of the public blockchain networks dapps are built on.

### Use-case 2: Multiple Party Transaction Authorization

Imagine you are the operator of an application on Flow, and your application has some administrative functionality that allows the application to be paused in the case a bug is found. A common way of setting such admin controls, is to put the power of pausing in the hands of more than one person who all must come together to submit a transction which pauses the app. There are many paths to take to making this sort of multisignature process work, and Flow has one built in at the account level.

The most straight-forward way of doing this is a [transaction for a single account with multiple keys](https://developers.flow.com/learn/concepts/transaction-signing#single-party-multiple-signatures). With this format, an individual keys can all be assigned to an account with pre-configured weights. When a transaction is submitted, as long as the total signing weight is at least 1000 the transaction is authorized to execute.

If your administrative control wanted to have a 5 of 7 multisig, then you could assign 7 keys to the admin account, each with weight of 200. Then whenever the system needs to be paused, *at least* 5 of the 7 keys must sign the transaction for it to be authorized to run on the Flow network.
