# Equilibre - consensus security layer

Recent events around Veriblock [1] showed us that many networks want to have strong security foundation instead of building own. Since networks like Bitcoin designed to handle transactions but not data from another blockchain, this create issues for "host" networks such as high fees and stucked user transactions which need hours to be confirmed etc. Purpose of this paper describe system which provide security layer for decentralised consensus based networks.

## Problem

Satoshi designed Bitcoin as ultimate verifiable timestamp server secured by Proof-of-Work [2]. This exact property allowed users to make transactions which would be stored in immutable decentralized ledger. But PoW doesn't came without drawbacks like possibility of 51% attack [3] which would allow attacking party do double spend and disrupt ledger immutability. At the time of writing this paper, there were nearly 2000 cryptocurrencies and many of them are at risk of such attack.

## Design

To provide security layer for small and medium size ledgers Equilibre would use graph of cross-verifying entries [4]. Each entry could represent entity from another network or native transaction. When an entry added to network, it will refer to two previous entries deemed to be valid, bundled with verified delay function [5] based proof provied by validator nodes. Validator nodes pick new entries from memory pool and try solve time locked puzzle (VDF) to confirm new entry and gain validator fee provided by entry creator.

![image-20190613132723913](https://i.imgur.com/UMKXtc9.png)

Verified delay function `f(x)` requires `t` sequentials steps to compute result `y` and could be easily verified in `log(t)` steps which allow us to use it with sole same purpose as PoW - spend some verifiable amount of time to create valid and secure proof for some data.

To incentivide validator nodes generate VDF proof for entries native currency should be introduced to network with purpose of serving as economic oil to move network forward [6]. This also add possible transaction/store of value functionality to system.

## Open problems

- Design of VDF
- Economic part of system
- Role of validator nodes
- Incentive to move DAG forvard

References:

[1] https://www.finder.com.au/how-not-to-piggyback-on-the-bitcoin-network

[2] https://bitcoin.org/bitcoin.pdf

[3] https://www.investopedia.com/terms/1/51-attack.asp

[4] https://eprint.iacr.org/2016/871.pdf

[5] https://eprint.iacr.org/2018/601.pdf

[6] https://www.investopedia.com/tech/what-ether-it-same-ethereum/