# DANIC Architecture

*H-Formula Chain, GAST Package, VBlock Technology, 
and Network Design*

---

## The H-Formula Chain

DANIC replaces consensus with mathematical certainty.
Four layers run in sequence on every transaction.

H1 — Lineage Hash
Proves the full history of the account.
Any altered past transaction invalidates all future ones.

H1_next = SHA256( sender | prev_H1 | tx_hash | 
sequence | H3 | outputs )

H2 — UTXO State Snapshot
Proves current ownership.
Deterministically sorted so every node produces 
identical output from identical state.

H3 — State Integrity Lock
Primary double-spend prevention.
Locks the exact state at signing time.
One byte difference = instant rejection. No network 
round-trip needed.

H3 = SHA256( DOMAIN | prev_H1 | GENESIS | sender | 
seq | H2 | tx_hash )

H4 — UTXO Output Key
Gives every coin output a unique unforgeable identity.
Used as integrity hash for entire VBlocks.

H4 = SHA256( tx_hash | slot | value )

---

## The GAST Package

General Authenticated State Transfer

Every transaction is a self-contained proof.
No coins travel over the network — only the message.

Contents:
- tx_hash
- previous_h1
- proposed_h3
- input_utxo_keys

Validation Flow:
L1 — H1 Lineage Check
L3 — H3 State Integrity Lock
L2 — H2 UTXO Viability Check

All three must pass. Failure at any layer = 
instant local rejection.

---

## VBlock Technology

Batch Finality Engine

Transactions accumulate in memory then commit 
in batches called VBlocks.

Two triggers:
- 3,000 account updates in buffer
- 20 seconds elapsed since last VBlock

The Overwrite Principle:
Old UTXOs deleted. Fresh H2 snapshot written.
Storage stays lean forever.

Atomic Safety:
Each VBlock uses atomic write.
Either fully succeeds or fully fails.
No partial state ever written.

---

## Network Architecture

Each node runs 7 specialised ports:

| Port | Protocol | Purpose |
|------|----------|---------|
| 8041 | HTTP RPC | MetaMask and Web3 compatibility |
| 7000 | Raw TCP | VBlock sync and peer handshake |
| 7777 | Raw TCP | Bootstrapper peer directory |
| 9000 | ZMQ PUSH | GAST transaction gossip |
| 9001 | ZMQ PUSH | H1 lineage gossip |
| 9002 | ZMQ PUB | Reward broadcast |
| 6000 | ZMQ REQ | Account state queries |

---

## Node Lifecycle

1. START — Run node
2. REGISTER — Contact Bootstrapper
3. HANDSHAKE — Connect to peer list
4. SYNC — Download VBlocks via TCP
5. LIVE — Validate transactions and earn DNC
6. LEAVE — Deregister cleanly

Heartbeat timeout: 90 seconds
Peers auto-remove disconnected nodes silently.

---

## Post-Quantum Security

Transaction signing uses CRYSTALS-Dilithium3.
Quantum-resistant from day one.

---

*See also: [Whitepaper](whitepaper.md) | 
[Tokenomics](tokenomics.md)*