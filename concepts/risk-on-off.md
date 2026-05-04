---
type: concept
sectors: []
entities:
  - [[hyperliquid]]
last_curated: 2026-05-04T08:03:19+00:00
curation_mode: manual
sources_count: 0
last_schema_migrated: 2026-05-04T08:20:20Z
---

# Risk On / Risk Off

## Definition

Signal macro qui capture l'appétit général du marché pour le risque. Utilisé pour positionner les positions DeFi.

**Risk ON 🟢** — Traders et institutions cherchent le risque:
- Prix crypto naik (BTC, ETH, alts)
- DeFi TVL monte (plus de capital deposit)
- Stablecoin yield monte (demand empoison)
- Corrélé: S&P 500 naik, VIX bas

**Risk OFF 🔴** — Fuite vers quality assets:
- Prix crypto turun
- TVL DeFi descend (withdrawals)
- Corrélé: Dollar fort, VIX haut, sovereign bonds naik

## Calcul (notre implementation)

Basé sur ratio bull/bear des articles ingérés sur 7 jours:

```
ratio = bullish_count / max(bearish_count, 1)
Risk ON:  ratio >= 1.5
Risk OFF: ratio <= 0.67
Neutre:   sinon
```

Barre visuelle: `▓▓▓▓░░░░ NEUTRE ⚪` (8 caractères, proportion bull/bear)

## Sources de Signal

- [[raw/crypto-reports/daily-2026-05-03]] — 61 articles sur 7j
- [[queries/market-signal-2026-05]] — Filed query: signal mai 2026

## Relations

- [[entities/hyperliquid]] — Perps performent bien en Risk ON
- [[entities/aave]] — Borrow demand monte en Risk ON
- [[concepts/tvl-tracking]] — TVL comme proxy Risk sentiment
