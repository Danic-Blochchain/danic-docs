# DANIC Blockchain — Technical Whitepaper v3.0

*A Non-Consensus Layer 1 Blockchain with Mathematical Finality*
*Designed by Mr. Jammeh — Founder & CEO, Danic Blockchain*

---

## Abstract

DANIC is a sovereign, high-performance Layer 1 blockchain 
designed to eliminate consensus mechanisms entirely.

Instead of voting, mining, or staking, DANIC uses a 
four-layer cryptographic formula chain — H1 through H4 — 
that makes every transaction mathematically self-proving.

If the H-chain verifies, the transaction is accepted locally 
on every node independently. No peer agreement needed.

---

## The Problem With Existing Blockchains

**Bitcoin — Proof of Work**
Wastes enormous energy solving artificial puzzles.
Limited to ~7 transactions per second globally.

**Ethereum — Proof of Stake**
Requires two-thirds supermajority of validators per 
checkpoint. Introduces coordination latency and 
validator centralisation risk.

**State Bloat**
Both networks store full transaction history permanently.
Storage grows unboundedly as usage grows.

**Mempool Congestion**
Demand spikes cause unpredictable confirmation times 
and fee auctions that price out small transactions.

---

## The DANIC Solution — H-Formula Chain

DANIC replaces consensus with cryptographic certainty.

### H1 — Lineage Hash
Recursive hash of the account's full transaction history.
Any attempt to alter a past transaction invalidates 
every subsequent transaction from that account.

H1_next = SHA256( sender | prev_H1 | tx_hash | 
sequence | H3 | outputs )

### H2 — UTXO State Snapshot
Deterministically sorted serialisation of the sender's 
complete current UTXO set. Every node holding the same 
state produces the identical H2 string.

### H3 — State Integrity Lock
Primary double-spend prevention mechanism. If any input 
differs from what the receiving node holds locally — 
even by one byte — H3 will not match and the transaction 
is rejected instantly.

H3 = SHA256( DOMAIN | prev_H1 | GENESIS | sender | 
seq | H2 | tx_hash )

### H4 — UTXO Output Key
Deterministic key uniquely identifying each individual 
coin output. Ties the output irrevocably to its parent 
transaction.

H4 = SHA256( tx_hash | slot | value )

---

## The GAST Package — Transaction as Self-Proof

Every transaction in DANIC is called a GAST Package
(General Authenticated State Transfer).

It is a complete cryptographic proof of a valid state 
transition — carrying everything a receiving node needs 
to validate independently.

Three validation layers:
- L1 — H1 Lineage Check
- L2 — H2 UTXO Viability Check
- L3 — H3 State Integrity Lock

No coins travel over the network. Only the message does.

---

## VBlock Technology — Batch Finality

Validated transactions accumulate in memory and commit 
in batches called VBlocks.

Two triggers:
- Buffer reaches 3,000 account updates
- 20 seconds elapse since last VBlock

The Overwrite Principle:
Old UTXOs are deleted. Fresh H2 snapshot is written.
Database size stays lean indefinitely.

---

## DNC Coin — Reward System

| Property | Value |
|----------|-------|
| Total Supply | 21,000,000 DNC — fixed forever |
| Daily Pool | 100 DNC split across all active nodes |
| Fee Model | 1% flat — no gas auctions |
| Energy Use | ZERO |

Anti-Cheat Mechanisms:
- Balance ceiling per VBlock height
- Hard supply cap at 21 million
- Subtraction of Absence on reconnection

---

## Comparison

| Feature | Bitcoin | Ethereum | DANIC |
|---------|---------|----------|-------|
| Consensus | Proof of Work | Proof of Stake | H-Formula Math |
| Energy | Very High | Low | ZERO |
| Block Time | ~10 min | ~12 sec | 20s or 3000 txs |
| Fees | Variable | Gas auction | 1% flat |
| State Bloat | Grows forever | Grows forever | Overwrite Principle |

---

## MetaMask Compatibility

| Setting | Value |
|---------|-------|
| Network Name | Danic DNC |
| RPC URL | http://your-node-ip:8041 |
| Chain ID | 900124 (0xDAE1C) |
| Currency Symbol | DNC |

---

*For full ecosystem documentation see ecosystem.md*