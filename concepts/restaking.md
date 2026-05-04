---
type: concept
sectors: [defi-restaking]
entities:
  - [[hyperliquid]]
  - [[lido]]
last_curated: 2026-05-04T08:03:19+00:00
curation_mode: manual
sources_count: 0
last_schema_migrated: 2026-05-04T08:20:20Z
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
