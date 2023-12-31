# B2C Wrapper Terms

## Purpose

This legal terms "wrapper" focusses on a scenario where a business sells fungible or non-fungible tokens to a consumer.

The wrapper assumes the use of [Rainlang](https://rainlang.xyz/).

## Creating Agreement

## Problem

There are complexities around how transacting parties on a blockchain should add legal terms to the transaction.  Legal agreements require parties to understand the legal terms that govern the transaction.

A system like Ethereum makes no specific provision for the addition of legal terms to blockchain transactions, so there are questions about how to ensure that everyone engaging in the transaction understands the applicable legal terms.

## Solution steps

We propose an approach where the user _provides the actual text of the legal terms_ so it's clear that the user knows which legal terms are applicable.  Here's how that approach would work with a buyer using a smart contract to buy a token.

- Buyer builds the transaction message on the client and includes the text of the legal terms (probably in Markdown) (**Terms**) in the "calldata" of the transaction message;
- Buyer cryptographically signs the transaction message and sends it (including the Terms);
- Smart contract recieves the buyer transaction message and grabs the Terms from the calldata to hash the Terms;
- Smart contract compares the Terms hash to a hash in the Rainlang expression creating the smart contract - then:
  - if the hash of the Terms sent by the buyer are the same as the hash on the smart contract, we know that the buyer has access to the right Terms, so the smart contract executes; and
  - if the hash of the Terms sent by the buyer are different to the hash on the smart contract, we don't know that the buyer has access to the right Terms, so the smart contract throws an error.

### How we Know

It's important to note that the Ethereum consensus infrastructure:

- runs the hash check on the Terms as part of the smart contract execution process; and
- nodes on the network immutably store the calldata (including the Terms) in a way that can be accessed later off-chain.

This means we have all the data integrity guarantees of blockchain data on the question of a buyer signing a transaction message that contains the right Terms to use the smart contract.

The calldata with this information can be accessed with indexers (eg subgraphs) off-chain.

### Calldata is cheap

We don't incur high transaction fees for using blockchain storage when we include Terms in calldata.  Calldata doesn't go to blockchain storage.  

The consequence of this is that other transactions running on the blockchain won't be able to see the Terms, but for creating agreements, that doesn't matter.

### Front end

We should note that most users interact with the blockchain through user interfaces that build and send transaction messages on their behalf.

We will need to obligate user interface providers to ensure that users of their interface view the terms before using them to sign a transaction.

### Magic number

Rain protocol uses a "magic number" so that the Rain smart contracts know how to interpret the calldata to do the Terms hash check.

For more details on this, take a look at the docs: https://github.com/rainlanguage/specs/blob/main/metadata-v1.md#magic-numbers

### Terms required

There are at least two scenarios where it's important for the Terms to be present:

- when the smart contract itself deploys onchain; and
- when users are interacting with an already-deployed smart contract.
