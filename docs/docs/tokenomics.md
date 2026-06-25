# DANIC Tokenomics

*DNC Coin — Supply, Distribution, and Reward System*

---

## Overview

DNC is the native coin of the DANIC Blockchain.

Fixed supply. No mining. No inflation. Ever.

---

## Supply

| Property | Value |
|----------|-------|
| Total Supply | 21,000,000 DNC |
| Distribution | Node rewards only |
| Inflation | None — fixed forever |
| Energy Cost | Zero |

---

## Daily Reward System

Every 86,400 seconds (24 hours) each active 
node receives its share of the daily pool.

| Nodes Active | DNC Per Node |
|-------------|--------------|
| 10 nodes | 10.000 DNC each |
| 100 nodes | 1.000 DNC each |
| 1000 nodes | 0.100 DNC each |

Daily Pool: 100 DNC split equally across 
all active nodes.

No DNC ever travels over the network.
Only the signed Reward Gas Package (RGP) does.

---

## Anti-Cheat Mechanisms

Three layers protect the reward system:

**Balance Ceiling**
No node can claim more DNC than is mathematically 
possible given the network VBlock height.
Formula: balance must be less than or equal to 
height x 0.007

**Supply Cap**
Total rewarded DNC across all nodes can never 
exceed 21,000,000.

**Subtraction of Absence**
When an offline node reconnects, its handshake 
reveals its real lower balance.
All peers correct their records automatically.

---

## Fee Model

| Property | Value |
|----------|-------|
| Fee | 1% flat per transaction |
| Model | Fixed — no gas auctions |
| Currency | DNC |
| Comparison | Bitcoin/Ethereum fees variable and unpredictable |

---

## DANIC Coin Use Cases

- Node operator rewards
- Transaction fees
- Governance voting
- Staking
- Settlement across DANIC modules
- Global digital gold standard

---

## Comparison

| Property | Bitcoin | Ethereum | DNC |
|----------|---------|----------|-----|
| Supply | 21M | Unlimited | 21M fixed |
| Issuance | Mining | Staking | Node rewards |
| Energy | Very High | Low | Zero |
| Fees | Variable | Gas | 1% flat |
| Inflation | Halving | Variable | None |

---

*See also: [Whitepaper](whitepaper.md) | 
[Ecosystem](ecosystem.md)*