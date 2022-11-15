---
title: Flow's Accounts are Awesome
date: "2022-11-14T15:20:24Z"
description: "Flow's accounts let users and applications interact with the blockchain in simple, powerful ways."
---

The Flow blockchain was designed from the ground-up to make it straightforward
for users to own, control, and give access to different assets which are stored on chain. A major part of this is based in the Cadence programming language's use of resource-oriented programming. The base protocol layer of Flow also plays a role through the core functionality of accounts.

## Accounts are more than just cryptographic keys
For flow the concept of an Account, that is a thing that exists on the blockchain that can hold resources, has access to storage, and can submit transaction is distrinct from the concept of a key. Each Flow account is controlled by one or more keys. Furthermore, each key can also be associated with zero or more accounts.

This means that on a Flow account, users can:
- Rotate keys in case one may have been compromised.
- Create a setup where more than one key is needed in order to authorize transactions.
- Create a social-recovery system where a group of trusted individuals can come together to authorize transactions for an account, while allowing one master key to always control that account as well.

For example, consider the account Flow Mainnet at address `0x8624b52f9ddcd04a`. This account is known as the Flow Staking Account, and it is the account which owns the smart contracts which control how operators can participate in the Flow network. This is an important account as its resources define how the network admits participants. Because of this, the account is set up as multisig and requires at least four signatures to authorize transactions on its behalf.

## Transactions can be paid for by a third party
Also built into Flow's model is the concept of a "transaction payer" separate from the concept of a "transaction authorizer."
