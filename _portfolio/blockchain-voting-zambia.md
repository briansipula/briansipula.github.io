---
title: "Blockchain-Based Voting System — Zambian Electoral Law Implementation"
excerpt: "A prototype grounded in Zambia's Electoral Process Act No. 35 of 2016, enforcing seven statutory provisions in executable Solidity smart contracts."
collection: portfolio
---

## Overview

This project developed a blockchain-based voting prototype as part of MSc CS research at ZCAS University (2024). It is the first known prototype to ground a blockchain voting system in named statutory provisions of a specific national electoral law enforced in executable code.

## Research Problem

Existing blockchain voting literature identifies the voter key-management problem — voters cannot be expected to manage cryptographic keys — but provides no deployed solution. This prototype addresses that gap using a proxy-signing architecture, where a trusted backend signs transactions on behalf of voters without gaining access to their vote choices.

## Legal Grounding

The prototype maps Zambia's Electoral Process Act No. 35 of 2016 down to SI regulation level. Seven statutory provisions are enforced directly in Solidity smart contracts, including voter eligibility, candidate registration, voting period enforcement, and result tallying.

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

A paper based on this work is currently under review at E-Vote-ID 2026 PhD Colloquium (Track 5).
