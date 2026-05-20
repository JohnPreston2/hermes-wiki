# Aave

## Mécanique
Lending/borrowing multi-chain. Déposants fournissent liquidité, emprunteurs collatéralisent. Liquidation automatique quand Health Factor < 1. Flash loans sans collatéral (même bloc). Governance par AAVE token + Safety Module (stakers absorbent les pertes).

## Risques connus
- Mai 2026: exploit $230M via rsETH depeg — WETH borrowing limits gelés puis restaurés.
- Historique de governance proposals controversées (Gauntlet vs Chaos Labs risk managers).
- Dépendance aux oracles Chainlink — risque de manipulation sur assets illiquides.
- Safety Module sous-capitalisé par rapport au TVL ($14B TVL vs ~$500M staked safety).

## Particularités
- Leader incontesté du lending par TVL. Morpho gagne du terrain sur les marchés isolés.
- V4 en déploiement — architecture modulaire, cross-chain native.
- Aave DAO a un trésor >$100M, runway longue.
- PT tokens (Pendle) intégrés comme collatéral = convergence yield/lending.
