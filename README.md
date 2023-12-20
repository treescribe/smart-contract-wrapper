# B2C Wrapper Terms

## Purpose

This legal terms "wrapper" focusses on a scenario where a business sells fungible or non-fungible tokens to a consumer.

## Creating Agreement

## Problem

There are complexities around how transacting parties on a distributed ledger should add legal terms to the transaction.  Legal agreements require parties to understand the terms that govern the transaction.

A system like Ethereum makes no specific provision for the addition of legal terms to transactions so there are questions about how to ensure that everyone engaging in the transaction understands which terms are applicable.

## Solution steps

We propose an approach where the user _provides the actual text of the legal terms_ so it's clear that the user knows what terms are applicable.  Here's how that approach would work with a buyer interacting with a smart contract that provides a token.

- Buyer builds the transaction message on the client and includes the text of the legal terms (probably in Markdown) in the "calldata" of the transaction message;
- Buyer cryptographically signs the transaction message and sends it;
- Smart contract recieves the buyer transaction message and grabs the legal terms text from the calldata to hash it;
- Smart contract compares the legal terms hash to a hash stored on the smart contract - then:
  - if the hash of the legal terms sent by the buyer are the same as the hash on the smart contract, we know that the buyer has access to the right terms, so the smart contract executes; and
  - if the hash of the legal terms sent by the buyer are different, we don't know that the buyer has access to the right terms, so the smart contract throws an error.

### How we Know

It's important to note that the Ethereum consensus infrastructure:

- runs the check of the legal terms as part of the smart contract process; and
- immutably stores the calldata in a way that can be accessed later.

This means we have all the data integrity guarantees of blockchain data on the matter of a buyer signing a transaction message that contains the right terms for the smart contract.

### Calldata is cheap

What we don't incur are high transaction fees for using blockchain storage.  Calldata doesn't go to blockchain storage.  The consequence of this (not important for creating legal agreements) is that other transactions running on the blockchain won't be able to see text of the legal terms.

### Front end

We should note that most users interact with the blockchain through user interfaces that build and send transaction messages on their behalf.

We will need to obligate user interface providers to ensure that users of their interface view the terms before using them to sign a transaction.
