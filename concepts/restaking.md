---
title: Restaking
created: 2026-05-03
updated: 2026-05-03
type: concept
tags: [restaking, defi, liquid-staking]
summary: "Restake ETH sur EigenLayer pour sécuriser d'autres protocoles, yield supplémentaire"
sources: [raw/crypto-reports/daily-2026-05-03.md]
---

# Restaking

## Definition

Le restaking permet de réutiliser les ETH déjà stakés (via Lido ou directement) pour sécuriser d'autres protocoles via EigenLayer. Au lieu de staker double, on "restake" son proof-of-stake.

**Avantage:** Yield supplémentaire sans immobiliser plus d'ETH.
**Risque:** Slashing sur plusieurs protocoles si mauvaise validation.

## Acteurs Principaux

| Protocol | TVL | Token | Mechanism |
|----------|-----|-------|-----------|
| EigenLayer | $20B+ | EIGEN | Native restaking + LSD restaking |
| EtherFi | $5B+ | ETHFI | Liquid restaking, unstaking 7j |
| Renzo | $2B+ | EZETH | Restaking-as-a-service |
| KelpDAO | $1B+ | — | RSETH, stETH/ETH mix |

## Comment ça Marche

1. Staker ETH (via Lido, Rocket Pool, ou directement)
2. Restaker sur EigenLayer (ou via LSD restaking)
3. Activer des AVS (Actively Validated Services)
4. Recevoir des rewards additionnels (en ETH ou EIGEN)

## Relations

- [[entities/lido]] — Source de stETH pour restaking
- [[entities/hyperliquid]] — Hyperliquid peut utiliser restaking pour sécurité?
- [[comparisons/liquid-staking-vs-restaking]] — Comparatif complet
- [[concepts/liquid-staking]] — Prerequisite concept
