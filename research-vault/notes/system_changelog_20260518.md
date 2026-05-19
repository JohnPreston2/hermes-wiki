# System Changelog — 2026-05-18

## IMPORTANT: Lis ceci avant ton prochain brief

### Nouvelles sources de donnees disponibles

**1. Wiki sectors (12 pages, mises a jour 3x/jour)**
- Chemin: `~/wiki/sectors/*.md`
- Contenu: TVL live, prix tokens, yields actifs, volumes DEX, signaux, articles recents par secteur
- Secteurs: defi-perps, defi-lending, defi-lst, defi-restaking, defi-dex, defi-rwa, defi-yield, ai-agents, ai-inference, ai-data, ai-compute, ai-oracles
- Genere par: `sector_curator.py` (gemma, pas de LLM, pure data structuring)

**2. Wiki entities (31 pages, mises a jour 1x/jour)**
- Chemin: `~/wiki/entities/*.md`
- Contenu: prix, TVL, pools, volume, actualites par protocole
- Protocoles: aave, morpho, compound, uniswap, curve, lido, pendle, hyperliquid, bittensor, ondo, etc.
- Genere par: `entity_builder.py` (gemma, pas de LLM)

**3. data_digest.md enrichi**
- Section `PRIX MAJEURS`: BTC, ETH, SOL + 11 tokens DeFi/AI avec prix Binance exacts
- Section `WIKI COVERAGE`: nombre de pages sectors/entities actives
- Section `ON-CHAIN ENRICHED`: DEX volumes, stablecoin mcap, yield movers, TVL movers

**4. intelligence_hourly.json corrige**
- `volume_dex_24h` : maintenant rempli (etait NULL avant — source stale corrigee)
- `tvl_total` : maintenant correct (lit onchain_enriched.json au lieu de cache 72h)

**5. onchain_enriched.json (nouveau, toutes les 2h)**
- Source: DeFiLlama (TVL 30 protocoles + movers, 40 yield pools, DEX volumes top 20, stablecoins top 15) + DexScreener (trending, new profiles) + Binance (25 tokens)
- Chemin: `~/.hermes/skills/crypto-intelligence/data/onchain_enriched.json`

### Regles mises a jour

**REGLE PRIX:** Utilise UNIQUEMENT les chiffres du data_digest.md (section PRIX MAJEURS). Ne jamais inventer un prix. Si absent, ecrire N/A.

**REGLE WIKI:** Avant chaque brief, consulte au minimum 3 pages sectors (defi-lending, defi-perps, defi-dex) et les entites mentionnees dans les anomalies du digest.

### Jobs pauses (ne plus les attendre)
- TVL Protocol Tracker: remplace par onchain_enricher (2h, pas de LLM)
- DefiLlama DEX Volume: remplace par onchain_enricher

### Ce qui ne change pas
- intelligence_hourly.json reste ta source principale pour regimes, funding, leverage, spreads
- hyperliquid_signals.json reste la source HL
- convergence_alerts.json reste la source multi-source
- agent_config.json reste ta config de poids/thresholds
