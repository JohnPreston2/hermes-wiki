# Ethena

## Mécanique
Stablecoin synthétique USDe: backed par ETH/BTC stakés + short perp hedge (delta-neutral). sUSDe = version staking qui distribue le yield (funding rates positifs). ENA token = governance. Le yield vient du basis trade (spot long + perp short).

## Risques connus
- Si funding rates deviennent négatifs longtemps, le yield disparaît et USDe peut depegg.
- Risque de contrepartie sur les exchanges centralisés (positions short sur Binance/Bybit).
- Custody risk: collatéral gardé par custodians off-chain (Copper, Fireblocks).
- Scénario catastrophe: exchange hack + funding négatif = double hit.

## Particularités
- Croissance explosive: $4.3B TVL, +9.3% sur 7j — l'un des rares protocoles en expansion.
- USDe intégré comme collatéral sur Aave V3 et Morpho — adoption DeFi rapide.
- Le yield est cyclique: bull market = funding positif = USDe attractif. Bear = risque.
- Clarity Act (régulation stablecoins US) pourrait impacter USDe si classé comme security.
