# Wiki Log

> Append-only. Format: `## [YYYY-MM-DD] action | subject`
> Actions: ingest, create, update, query, lint, archive, delete
> Rotate: log.md → log-2026.md quand > 300 lignes

## [2026-04-09] create | Wiki initialized
- Structure created: SCHEMA.md, index.md, log.md
- Domain initial: recherche d'emploi AI Builder

## [2026-04-09] ingest | Fichiers raw importés
- raw/lettre-type-base.md
- raw/profil-candidat.md
- entities/hugo-chabot.md
- Updated: index.md

## [2026-05-03] create | Crypto/DeFi domain ajouté
- SCHEMA.md v2.0: domain étendu à crypto/DeFi/AI
- Nouvelles sections: concepts/, comparisons/, queries/, raw/crypto-reports/
- Tag taxonomy enrichie: defi, ai-agent, liquid-staking, perp, tvl, regulatory...

## [2026-05-04] update | Phase 3 — Pipeline Telegram corrigé
- Créé: scripts/run_surge.py (RSS fetch → surge JSON horodaté → ~/wiki/crypto-surge/)
- Corrigé: cron "Crypto Surge + Telegram Brief" cassé (run_surge.py manquait)
- Nouveau job: "Crypto Morning Brief — Enriched" (8h, 16h UTC) avec enriched_report.py --brief
- Supprimé: "Wiki Daily Ingest" (jamais roulé), "DeFi Sectorized Report" (jamais roulé), "DeFi Alert" (horaire = trop agressif)
- SKILL.md mis à jour: cron jobs + run_surge.py documenté
- Pipeline complet: run_surge.py → enriched_report.py → sortie fichier → delivery Telegram
- 7 articles ingérés ce matin ( cutoff 26h, DB veillle.db ~250 articles total)
- index.md: 25 entrées (entities, concepts, comparisons, queries)
- entities: hyperliquid, lido, aave, morpho, spark, tether, curve, uniswap, pendle, solana, ethereum
- concepts: liquid-staking, restaking, perpetuals, yield-tokenization, ai-agents, agentic-ai, risk-on-off, tvl-tracking
- comparisons: liquid-staking-vs-restaking, perp-protocols
- queries: market-signal-2026-05
## [2026-05-03] ingest | Daily report 2026-05-03
- /home/classics2323/wiki/raw/crypto-reports/daily-2026-05-03.md
- Signal: NEUTRE ⚪ (bull 18 / bear 14, ratio 1.29)
- Articles: 61, Tags: 10

