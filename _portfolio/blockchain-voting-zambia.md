---
title: "Blockchain-Based Voting System — Zambian Electoral Law Implementation"
excerpt: "A prototype grounded in Zambia's Electoral Process Act No. 35 of 2016, enforcing seven statutory provisions in executable Solidity smart contracts."
collection: portfolio
---

## Overview

While the global literature on blockchain-based e-voting frequently addresses abstract security parameters, it routinely ignores the highly specific, messy administrative realities dictated by national legislation. To the best of my knowledge, the existing literature on decentralised voting does not engage with Zambia's Electoral Process Act No. 35 of 2016, and no prior work has attempted to map such specific national electoral statutes down to the level of statutory regulations into executable smart contract code. This project addresses this gap by presenting a prototype engineered to programmatically enforce seven distinct provisions of the Act, demonstrating the precise architectural bottlenecks that arise when translating democratic law into immutable ledger logic.

## Research Problem

Existing blockchain voting literature identifies the voter key-management problem — voters cannot be expected to manage cryptographic keys — but provides no deployed solution. This prototype addresses that gap using a proxy-signing architecture, where a trusted backend signs transactions on behalf of voters without gaining access to their vote choices.

## Legal Grounding

The prototype maps Zambia's Electoral Process Act No. 35 of 2016 down to SI regulation level. Seven statutory provisions are enforced directly in Solidity smart contracts, covering voter eligibility, candidate registration, voting period enforcement, and result tallying.

## Technical Stack

- **Smart contracts:** Solidity 0.8.24, OpenZeppelin v5.x
- **Development environment:** Hardhat
- **Database:** PostgreSQL 16
- **Backend:** Node.js / Express
- **Frontend:** Next.js 14 / TypeScript
- **Blockchain interaction:** ethers.js v6

## Status

Prototype complete. Two privacy vulnerabilities identified and fixed (July 2026):
- Database ballot secrecy vulnerability (vote-to-voter join query)
- Plaintext candidate name emission in Solidity event log

A paper based on this work is under review at E-Vote-ID 2026 PhD Colloquium (Track 5).
