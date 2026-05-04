---
type: comparison
sectors: [defi-perps]
entities:
  - [[hyperliquid]]
last_curated: 2026-05-04T08:03:19+00:00
curation_mode: manual
sources_count: 0
last_schema_migrated: 2026-05-04T08:20:20Z
---

# Comparatif: Protocoles Perpetuals

## Vue d'ensemble

Les perpetuals (perps) sont des contrats futures sans date d'expiration. Permettent leverage sans expiration.

## Comparatif Rapide

| Critère | Hyperliquid | dYdX | GMX | Drift |
|---------|-------------|------|-----|-------|
| **TVL** | $4.6B | $400M | $200M | $100M |
| **Chain** | Arbitrum (L1 app) | Ethereum (dYdX Chain) | Arbitrum/Avax | Solana |
| **Volume/j** | $1B+ | $300M | $100M | $50M |
| **Decentralisation** | High (on-chain) | Very High (cosmos chain) | Medium | High |
| **Token** | $HYPE | $DYDX | $GMX | $DRIFT |
| **Maker fee** | 0.035% | 0.02% |可变 |可变 |
| **Taker fee** | 0.07% | 0.05% |可变 |可变 |

## Hyperliquid (Référence)

- **Avantage:** fastest execution, sub-cent gas, volume #1
- **Inconvénient:** token nuevo (airdrop 2024), moins historique
- **Best for:** traders haute fréquence, volume junkies

## dYdX

- **Avantage:** fully decentralized Cosmos chain, governance token
- **Inconvénient:** UX plus complexe, chain séparée
- **Best for:** puristes décentralisation

## GMX

- **Avantage:** multi-chain (Arbitrum, Avalanche), pas de liquidation BOT centralisé
- **Inconvénient:** oracle-based pricing (pas ordre book)
- **Best for:** access multi-chain

## Drift

- **Avantage:** Solana speed + fees, SOL collateral natif
- **Inconvénient:** écosystème Solana dependency
- **Best for:** Solana natives

## Verdict

**Volume:** Hyperliquid >> dYdX > GMX > Drift
**Décentralisation:** dYdX > Drift > Hyperliquid > GMX
**UX:** Hyperliquid ≈ Drift > GMX > dYdX
**Yield:** Variable selon protocol (funding rate)

## Relations

- [[entities/hyperliquid]] — Detailed entity page
- [[concepts/perpetuals]] — Mécanique funding rate
- [[concepts/risk-on-off]] — Perps sentiment correlates with risk appetite
