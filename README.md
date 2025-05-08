# **LUNC Reserve (LUNR) White Paper**

### Redeemable Reserve‑Notes for the Terra Classic Ecosystem

---

## 1 · Abstract

**LUNC Reserve (LUNR)** introduces a programmable reserve‑note layer to Terra Classic. Every LUNR token represents a proportional claim on a transparent pool of **LUNC** locked in a smart contract, with the on‑chain redemption rate defined as

```
LUNR value = LUNC reserves ÷ LUNR supply
```

New deposits mint LUNR at a **15 % protocol premium**: 85 % of the fair‑value notes are issued to the depositor, while 100 % of the LUNC is added to reserves. Because supply grows more slowly than reserves, each mint **accrues intrinsic value** to all existing holders. The system launches with **1 billion LUNC** from the Community Pool and a genesis airdrop to every LUNC holder and staker.

---

## 2 · Historical Context — From Gold Certificates to Smart‑Contract Notes

### 2.1 Early Banking · Gold Deposits & Redeemable Notes

Before electronic money, merchants deposited **gold** with trusted goldsmiths and received paper **receipts**. Those receipts soon **circulated as money**, because anyone could redeem the note for gold on demand. Confidence in the vault was paramount: if trust evaporated, holders rushed to redeem, triggering the classic *bank‑run*.

In the United States this evolved into official **Gold Certificates**—dollar bills literally stamped “payable to the bearer on demand.” Until 1933, Americans could exchange a certificate for gold coins at the Treasury window. The lesson is timeless: *deposit something valuable, receive a tradable claim ticket*.

### 2.2 LUNC Reserve · Bringing the Vault On‑Chain

**LUNC Reserve** applies that centuries‑old concept to blockchain:

| Legacy Banking                 | LUNC Reserve                    |
| ------------------------------ | ------------------------------- |
| Gold stored in a guarded vault | LUNC locked in a smart contract |
| Paper bank‑note                | LUNR token (CW20 standard)      |
| Manual teller redemption       | Trustless `redeem()` function   |

Every LUNR is backed by real LUNC reserves. Redeeming burns LUNR and releases the exact pro‑rata amount of LUNC—no human approval required. The contract enforces the reserve ratio transparently, eliminating custodial risk while preserving the redeemability that made historical bank‑notes so powerful.

---

## 3 · System Design

### 3.1 Reserves & Supply

* **Initial reserves:** 1 000 000 000 LUNC (Community Pool)
* **Genesis supply:** 100 000 000 LUNR  — *genesis rate = 10 LUNC per LUNR*
* **Live metrics:** the contract exposes real‑time reserves, supply, and redemption rate.

### 3.2 Minting with a 15 % Premium

1. User deposits **d LUNC**.
2. Fair issuance = `d ÷ p` LUNR at the current rate *p*.
3. Contract transfers **85 %** of those notes to the depositor and burns the remaining **15 %**.
4. The full **d LUNC** is added to reserves.

Because supply expands more slowly than reserves, the redemption rate rises immediately after every deposit.

### 3.3 Redemption & Burn Mechanics

* **Redeem:** burn *x LUNR* → withdraw *x × p* LUNC (lossless).
* **Voluntary burn:** destroy LUNR without redemption to raise the redemption rate for all remaining holders.
* **External burns:** protocol extensions (games, DAOs, LP vaults) may burn LUNR, further concentrating value.

> **Why LUNR burns matter.** Terra Classic’s standard 0.5 % LUNC burn simply lowers supply—it does **not** increase the purchasing power of each LUNC. Every LUNR burn leaves LUNC reserves intact **while reducing LUNR supply**, automatically lifting the redemption rate. Burns therefore reduce circulating notes *and* boost the intrinsic value of every remaining LUNR.

---

## 4 · Genesis Airdrop

* **Snapshot block:** 7 days after governance approval.
* **Eligibility:** all liquid **and** staked LUNC (CEX custodians encouraged to pass rewards through).
* **Distribution:** 100 000 000 LUNR airdropped pro rata.

---

## 5 · Economic Example

| Metric                            | Before Deposit | After 1 M LUNC Deposit |
| --------------------------------- | -------------- | ---------------------- |
| **Reserves (LUNC)**               | 10 000 000     | 11 000 000             |
| **Supply (LUNR)**                 | 1 000 000      | 1 085 000              |
| **Redemption Rate (LUNC / LUNR)** | 10.00          | **10.14** (+1.4 %)     |

A voluntary burn of 50 000 LUNR (with no withdrawal) would push the rate to 10.32 LUNC, directly rewarding holders through scarcity.

---

## 6 · Governance & Upgradability

* **Premium range:** 5 – 25 %, adjustable by on‑chain vote.
* **Contract upgrades:** governance proposal + 3‑of‑5 validator multisig timelock.
* **Reserve movements:** only via `redeem()`; no admin withdrawal route exists.

---

## 7 · Conclusion

LUNC Reserve converts idle Community Pool assets into a community‑owned, value‑accruing reserve system. By merging centuries‑old banking logic with modern smart‑contract transparency, **LUNR** provides Terra Classic with a deflationary, composable primitive that bridges the gold‑backed money of the past and the decentralised finance of the future.

*Documentation & GitHub links will follow the successful passage of the governance proposal.*

— *Last updated · May 2025*
