---
title: "Blockchain-Based Voting System: Zambian Electoral Law Implementation"
excerpt: "A prototype grounded in Zambia's Electoral Process Act No. 35 of 2016, enforcing seven statutory provisions in executable Solidity smart contracts. Deployed to Ethereum Sepolia testnet and source-verified on Etherscan."
collection: portfolio
---

## Overview

While the global literature on blockchain-based e-voting frequently addresses abstract security parameters, it routinely ignores the highly specific, messy administrative realities dictated by national legislation. To the best of my knowledge, the existing literature on decentralised voting does not engage with Zambia's Electoral Process Act No. 35 of 2016, and no prior work has attempted to map such specific national electoral statutes down to the level of statutory regulations into executable smart contract code. This project addresses this gap by presenting a prototype engineered to programmatically enforce seven distinct provisions of the Act, demonstrating the precise architectural bottlenecks that arise when translating democratic law into immutable ledger logic.

## Research Problem

Existing blockchain voting literature identifies the voter key-management problem, namely that voters cannot be expected to manage cryptographic keys, but provides no deployed solution. This prototype addresses that gap using a proxy-signing architecture, where a trusted backend signs transactions on behalf of voters without gaining access to their vote choices. The system also implements a commit-reveal scheme (v9.1) for partial ballot secrecy without requiring zero-knowledge proofs.

## Known Limitation

The open PhD research question arising from this prototype: `_candidateId` still passes as plaintext calldata, meaning chain observers can reconstruct voter-to-candidate links from raw transaction input. Full removal requires a ZKP-based reveal mechanism or homomorphic tallying. This limitation is documented explicitly in the smart contract source code and in the accepted E-Vote-ID 2026 paper.

## Legal Grounding

The prototype maps Zambia's Electoral Process Act No. 35 of 2016 down to SI regulation level. Seven statutory provisions are enforced directly in Solidity smart contracts, covering voter eligibility, candidate registration, voting period enforcement, and result tallying.

## Technical Stack

- **Smart contracts:** Solidity 0.8.24, OpenZeppelin v5.x
- **Development environment:** Hardhat
- **Database:** PostgreSQL 16
- **Backend:** Node.js / Express
- **Frontend:** Next.js 14 / TypeScript
- **Blockchain interaction:** ethers.js v6

## Testnet Deployment

The prototype is deployed to the Ethereum Sepolia testnet (Chain ID: 11155111). This is a public test network — not a production deployment and not a live electoral system. The deployment serves as a verifiable proof-of-concept for the architectural and legal grounding claims made in the research.

| Detail | Value |
|--------|-------|
| Reference contract | `0xc49Ceb6258E6Bd8E5e1d9E20cB0Ae0CC512A4886` |
| Verification status | Source Code Verified — Exact Match |
| Network | Ethereum Sepolia Testnet |
| End-to-end test | 12 votes cast, 14 contract events confirmed on-chain (29 August 2026) |

## Independent Verification

The contract source code is publicly verified on Etherscan. Anyone can inspect the smart contract logic, confirm the statutory provisions enforced in code, and review the on-chain transaction history.

- [View reference contract on Etherscan](https://sepolia.etherscan.io/address/0xc49Ceb6258E6Bd8E5e1d9E20cB0Ae0CC512A4886)
- [View Election #18 test on Etherscan](https://sepolia.etherscan.io/address/0x1c2435C7913d3F1980ad9e825B03a7B4CCcA2fb7)

## Status

**Prototype complete — deployed and verified on Ethereum Sepolia testnet (29 August 2026).**

Privacy vulnerabilities identified and fixed (July 2026):
- Database ballot secrecy vulnerability (vote-to-voter join query)
- Plaintext candidate name emission in Solidity event log

**Paper accepted, presentation pending:** *Deployability Versus Ballot Secrecy in Blockchain-Based Voting for Low-Resource Democracies: A Zambian Case Study* — E-Vote-ID 2026 PhD Colloquium, Track 5 (accepted 19 August 2026; presentation scheduled October 2026, Tallinn).
