---
id: general-faq
title: General FAQ
description: Common questions on the Polygon network.
keywords:
  - docs
  - matic
  - polygon
  - faq
image: https://matic.network/banners/matic-network-16x9.png 
---

## What is Polygon Network?

Polygon Network is a Layer 2 scaling solution that achieves scale by utilizing sidechains for off-chain computation, while ensuring asset security using the Plasma framework and a decentralized network of Proof-of-Stake (PoS) validators.

See also [What Is Polygon](/docs/validate/polygon-basics/what-is-polygon).

## What is Proof of Stake (PoS)?

Proof-of-Stake is a system in which the blockchain network aims to achieve distributed consensus. Anyone with sufficient amount of tokens can lock up their cryptocurrencies and the economic incentive lies in the shared value of the decentralized network. The individuals staking their cryptocurrencies validate transactions by voting on the same while consensus is achieved when a transaction or a set of transactions in a block or a set of blocks in a checkpoint receives enough votes. The threshold uses the weight in terms of stake that comes with every vote. For instance, in Polygon, consensus is achieved for committing checkpoints of Polygon blocks to the Ethereum network, when at least ⅔ +1  of the total staking power vote for this.

See also [What Is Proof of Stake](/docs/validate/polygon-basics/what-is-proof-of-stake).

## What role does Proof-of-Stake play in the Polygon architecture?

The Proof-of-Stake layer in the Polygon architecture serves the following 2 purposes:

* Acts as an incentivization layer for maintaining liveness of the Plasma chain, chiefly mitigating the thorny issue of data unavailability.
* Implement the Proof-of-Stake security guarantees for state transitions not covered by Plasma.

## How is Polygon PoS different from other similar systems?

It is different in the sense that it serves a dual purpose — providing data availability guarantees for the Plasma chain covering state transitions via Plasma Predicates, as well as Proof-of-Stake validation for generic smart contracts in the EVM.

The Polygon architecture also separates the process of block production and validation into 2 distinct layers. Validators as block producers create blocks as the name suggests on the Polygon chain for quicker (< 2 secs) partial confirmations while the final confirmation is attained once the checkpoint is committed on the main-chain with a certain interval, period of which may vary depending upon multiple factors like Ethereum congestion or number of Polygon transactions. In ideal conditions, it shall be around 15 min to 1 hour.

A checkpoint is basically the Merkle root of all blocks produced in between intervals. Validators play multiple roles, creating blocks at the block producer layer, participating in the consensus by signing all checkpoints and committing the checkpoint when acting as proposer. The probability of a validator becoming the block producer or proposer is based on their stake ratio in the overall pool.

## What’s the incentive to be a Polygon staker?

Polygon is allocating 12% of its total supply of 10 billion tokens to fund the staking rewards. These 1.2 billion tokens will be the staking incentive for the first five years. This is to ensure that the network is seeded well enough until transaction fees gain traction. These rewards are primarily meant to jump-start the network, while the protocol in the long run should be able to sustain itself on the basis of transaction fees.

**Validator Rewards = Staking Rewards + Transaction Fees from Polygon chain**

First year will see the maximum amount of tokens allocated as staking rewards. This is allocated in a way to ensure gradual decoupling of staking rewards from being the dominant component of the validator rewards.

See also [Economics](/docs/validate/polygon-basics/economics).

## How are staking rewards allocated to stakers?

Tokens to be given out as staking rewards for the first five years of the network life are fixed. This reward is divided per [checkpoint](/docs/validate/glossary#checkpoint-transaction) and the amount to be shared with all stakers is absolute. The reward rate will be higher during lower bonding rates and vice-versa otherwise.

The staking reward gets distributed proportionally to all stakers; proposer and signers, with the exception of proposer getting a bonus.

## Encouraging the proposer to include all signatures

To avail the proposer bonus completely, the proposer would need to include all signatures in the checkpoint. Because the protocol desires 2/3+1 weight of the total stake, the checkpoint will be accepted even with 80% votes. However, in this case, proposer gets only 80% of the calculated bonus.

## How can I reserve a validator spot?

If we have a vacant validator slot, anyone with any amount of stake can become a validator in the system. There will be validator auctions organized periodically (days mostly), where in anyone can replace any current validator by proposing higher stake. So, in short, it is an open system where we cannot reserve places for anyone.

In any case, there is always the possibility of stake delegation with the current validator set. Anyone can participate in the process with this mechanism and earn rewards as long as the respective validator is honest and online.

## Can I participate in the staking process, even if I do not want to run a node?

MATIC token holders who do not wish to run their own node can delegate their tokens to a validator. Delegation increases the power of the validator. More the power, more probability of the validator to become the block producer and checkpoint proposer and more weight in the consensus.

There is no minimum amount requirement for delegation. Any amount, even 1 MATIC, will be accepted in the system. However, it is up to validators to set a minimum limit or not while accepting delegations. Validators might charge a commission in exchange for their node running services. Other than the commission charged, one needs to evaluate the track record of the validator for example, average uptime or if the node was ever compromised.

See also [Delegate](/docs/validate/delegate).

## Where do the staked tokens reside?

Staked tokens are locked in a contract deployed on the Ethereum mainnet. Validators do not hold the custody of the delegated tokens. However, in the event of validator getting slashed delegated tokens also get slashed.

## For how long will my funds be locked?

If one wishes to opt out of the system, the staked tokens undergo an unbonding period during which they are liable to being slashed for any misbehaviour committed by the validator before the unbonding period started.

Delegated tokens enter unbonding period immediately upon unbond request. However, validators will need to serve a certain notice period in active state, participating in consensus and proposing checkpoints before entering into unbonding period.

Stakers can withdraw their tokens after the unbonding period ends. Exact durations of withdraw for both delegator and validator will be announced here soon.

See:

* [Delegate](/docs/validate/delegate)
* [Validator Staking Operations](/docs/validate/mainnet/validator-staking-operations)

## What are the different states a validator can be in?

* **Active**: Validator is in the current validator set, produces blocks at the Bor layer, participates in Heimdall consensus and commits checkpoint transactions to the Ethereum mainnet.
* **Notice**: Validator sends a transaction to unbond. Before entering into the unbonding period, validator needs to be in active state creating, signing and proposing blocks for a certain time.
* **Unbonding**: Validator is inactive in this state and thus earns no reward. However, the validator is still liable for slashing in case they have committed any malicious act previously.

## Is there a minimum amount of MATIC required to stake to become a validator?

The minimum is 1 Matic.

We had earlier mentioned that we are thinking of having a minimum self stake requirement from the validators, as we do hope that validators also have their skin in the game. However, since we will be moving to a robust replacement strategy as the number of validator slots are limited as of now, this does not need any minimum self stake requirement. It is however, logical that over time, the average/median stake by a validator will tend upwards and become substantial.

## How can a new validator replace an existing one?

There is limited space for accepting new validators. New validators can only join the active set when a currently active validator unbonds.

A new auction process for validator replacement will be rolled out.
