---
description: >-
  Archetype is a smart contract development solution dedicated to contract
  safety and consistency.
---

# What is Archetype?

The archetype project is developed by [edukera](https://edukera.com), and funded by [Tezos](https://tezos.com/).

## Smart contracts

A smart contract is a program which is executed on the blockchain. They were introduced in 2015 by [Ethereum](https://www.ethereum.org/). They allow to read and write virtually any data on the blockchain. This literally unleashed the full potential of the blockchains because it created the possibility to develop a new class of application which integrate blockchains as a public and distributed database; These application are called Dapp. 

A smart contract is similar to a stored procedure on a public distributed database. As such, they must ensure the **logical consistency and integrity** of the data.

## What's the problem?

In a nutshell, they break one of the key principles of the blockchain, which is the _trust-less principle_.

What is meant by _trust-less_ is that, with a blockchain, there is no need for a trusted third party to be confident in the fact the blockchain is doing what it is intended to, which is to manage transactions. Indeed blockchains are secure by design:  they are decentralised and immutable; plus every change in the system is validated by a consensus algorithm.

A smart contract is a _standard_ program, and, as such, it does not come with any guarantee that it will function correctly. We all have in mind the DAO incident: a bug in the smart contract made it possible to withdraw several times the money you would put in the contract. As a result, more than 100 millions dollars were lost.

It’s a highly non trivial question to decide whether a program is correct or not, even for the programmer. Before deploying a smart contract, current development best practices include a phase of testing. However, testing is limited by the capacity to imagine relevant tests and, even when a critical property is identified, testing is limited by the capacity to cover all possible situations of execution. 

## Services

In order to circumvent the inherent potential inconsistency of the smart contract,  Archetype  has identified several services which enhances the _apriori_ level of confidence you may have in a smart contract, before deploying it.

### Verification

Program verification is the gold standard when it comes to trust-less software quality.

What is program formal verification?

Say you have a program and a specific property that the program is supposed to have; say this property is written in formal logic. Program verification consists in figuring out a **mathematical proof** that the program has the property.

A mathematical proof is the perfect trust-less guarantee of the program quality because the only thing you need to is to check that the proof is correct towards the property and the program. This  question is known to be _decidable_, which means that it is possible to have a computer check the correctness of the proof automatically.

Are there limits? 

Yes of course. First, the guarantee you get is limited to the property you have been able to identify. A critical property may still be forgotten.

Then, you need to be a specialist in formal methods to be able to formalise and prove the properties. And if the property is a bit sophisticated, that may require a lot of skills.

### Simulation

### Documentation

### Execution

## Solutions

For each of the services identified above, an existing solution has been selected. The selection criteria was a good compromise between ease of use and performance. 

This selection is not definitive nor exhaustive. It should be considered as a starting point.



## A single language

## Integration in IDE

## A library of contract archetypes  

Archetype comes with several dozen of examples.

{% page-ref page="contracts-examples/escrow.md" %}

{% page-ref page="contracts-examples/auction.md" %}

{% page-ref page="contracts-examples/tokens/" %}

