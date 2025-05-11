# **LUNC Reserve (LUNR) White Paper**

### Redeemable Reserve‑Notes for the Terra Classic Ecosystem



---



## 1 · Abstract

**LUNC Reserve (LUNR)** is a reserve‑backed note system for Terra Classic. Every LUNR token represents a proportional claim on a smart‑contract vault of **LUNC**, with the redemption formula



LUNR value = LUNC reserves ÷ LUNR supply





New deposits mint LUNR at a **15 % protocol premium**—85 % of the fair‑value notes go to the depositor, while 100 % of the LUNC is added to reserves. Because supply grows more slowly than reserves, each mint *accrues* intrinsic value to all existing holders. The protocol launches with **1 billion LUNC** seeded from the Community Pool and a genesis airdrop to every holder and staker.



---



## 2 · Historical Context — From Gold Certificates to Smart‑Contract Notes



### 2.1 Gold Receipts & Bank‑Notes

Merchants once entrusted gold to goldsmiths and received paper receipts. Those receipts circulated as money because anyone could redeem them for gold—so long as trust in the vault held. U.S. **Gold Certificates** formalised this, promising “payable to the bearer on demand.”



### 2.2 Vaulting on Chain

LUNC Reserve mirrors that model:



| Legacy Banking         | LUNC Reserve            |

|---------------------------------|------------------------------------|

| Gold in a guarded vault     | LUNC locked in a CosmWasm vault  |

| Paper bank‑note         | LUNR CW20 token          |

| Teller redemption        | Trustless `redeem()`        |



Every LUNR burn releases its pro‑rata LUNC, so solvency is provable and immediate.



---



## 3 · System Design



### 3.1 Reserves & Supply

* **Initial reserves:** 1 000 000 000 LUNC  

* **Genesis supply:** 100 000 000 LUNR  

* **Live metrics:** vault exposes `query_rate`, reserves, and supply.



### 3.2 Minting with 15 % Premium

1. User deposits *d LUNC*.  

2. Fair issuance = `d ÷ p` LUNR.  

3. Depositor receives 85 %; 15 % is burned.  

4. Full *d LUNC* enters reserves.  

5. Redemption rate rises because *R* increases faster than *S*.



### 3.3 Redemption & Burns

* **Redeem:** burn *x LUNR* → withdraw *x × p* LUNC.  

* **Voluntary burn:** destroy LUNR without withdrawal → raises *p*.  

* **Protocol burns:** games/DAOs can sink LUNR to add scarcity.



> **Why LUNR burns matter** – Each burn leaves reserves unchanged but lowers supply, so the per‑token backing (*p*) escalates, unlike Terra Classic’s 0.5 % native LUNC burn that only reduces supply.



---



## 4 · Market Dynamics & Price Band

Let **p = R / S** (book value). Minting costs **p / 0.85 ≈ 1.176 p** LUNC per note.



| Market Situation | Arbitrage Action | Result |

|------------------|------------------|--------|

| **Price < p**  | Buy LUNR cheap → `redeem()` | Supply & reserves fall 1 : 1 → *p* unchanged; buying pressure lifts price toward *p*. |

| **Price > p / 0.85** | Deposit LUNC → mint at 85 % → sell | Reserves ↑, supply ↑, new sell‑pressure drags price toward *p / 0.85*. |



Self‑correcting corridor:



* **Floor:** *p* (100 % collateral)  

* **Ceiling:** *p / 0.85* (~117.6 % of collateral)



Since redemptions move *R* and *S* proportionally, per‑note collateral never weakens—arbitrage tightens price without draining reserves.



---



## 5 · Comparison with 2022 LUNA / USTC Model



### 5.1 Collateralisation vs Algorithmic Peg



| Feature        | 2022 LUNA ↔ USTC | 2025 LUNC Reserve |

|-----------------------|------------------|-------------------|

| **Backing ratio**   | 0 % reserve (USTC relied on LUNA mint/burn) | 100 % reserve: every LUNR minted only after LUNC is locked |

| **Peg model**     | Hard \$1 peg | Floating claim: *p* plus 15 % mint ceiling |

| **Stabilisation**   | Printed LUNA to buy USTC (hyper‑inflation) | No endogenous print; supply tied to deposits |

| **Failure mode**   | Reflexive death spiral (LUNA hyper‑inflation) | None—redeem & burn keeps per‑token backing constant |

| **Premium buffer**  | None | 15 % mint premium adds reserve headroom |



### 5.2 Why LUNR Avoids the Death Spiral

* **Cannot over‑issue** – vault mints only after LUNC arrives.  

* **No hard \$ peg** – price floats; no need to defend parity.  

* **Constant coverage** – redemptions shrink *R* and *S* equally, so *p* is steady.  

* **Mint‑premium ceiling** – prevents instant dilution above ~17.6 % over book value.



---



## 6 · Genesis Airdrop

* **Snapshot block:** 7 days after governance approval.  

* **Eligibility:** all liquid + staked LUNC.  

* **Distribution:** 100 000 000 LUNR airdropped pro rata.



---



## 7 · Governance & Upgradability

* Premium tunable 5–25 % via governance.  

* Upgrades require proposal + multisig timelock.  

* Reserves movable only through `redeem()`.



---



## 8 · Conclusion

LUNC Reserve converts Community Pool assets into a fully‑collateralised note economy. With its intrinsic price band and 100 % reserve model, LUNR delivers the redeemability early banking relied on—without the fragility that doomed algorithmic pegs.



*Last updated: May 2025*
