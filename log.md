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
## [2026-05-04] schema-v1 | step 2: 12 sectors/ created + frontmatter migrated
- 12 pages sectors/<tag>.md creees avec frontmatter canonique (type: sector, entities: [], sources_count: 0)
- Section ## Definition: copie/reformule taxonomie SCHEMA section 1
- Section ## Protocoles cles: vide (pour sector_curator.py)
- Section ## Metriques de sante: vide (pour sector_curator.py)
- Section ## Narratifs en cours: vide
- Section ## Evenements recents: vide
- entities[] mis a jour: defi-perps → [[hyperliquid]], defi-lst → [[lido]], defi-restaking → []
- 6 pages existantes migratees: frontmatter canonique (type, sectors, entities, last_curated, curation_mode, sources_count)
- index.md: section Sectors ajoutee (12 DeFi + AI)
- SCHEMA: v1.1
- Pret pour etape 3 (validation en attente)

## [2026-05-04] schema-v1 | Décisions tranchées + SCHEMA v1.1
- Fichiers candidat: SUPPRIMÉS (8 fichiers)
- entities/hugo-chabot.md: SUPPRIMÉ (hors-projet)
- queries/market-signal-2026-05.md: GARDE EN PLACE (query datée, sectors: [] dans frontmatter)
- concepts/risk-on-off.md: GARDE EN PLACE (concept transversal, sectors: [] dans frontmatter)
- SCHEMA.md: v1.1 — ajout section "Taxonomie et transversalité" (concepts/queries peuvent avoir sectors: [])
- index.md: nettoyé (hugo-chabot, blockchains placeholders enlevés)
- Pret pour etape 2: creation 12 sectors/ + migration frontmatter existants

## [2026-05-04] schema-v1 | Décision: fichiers candidat supprimés
- Supprimés (hors-projet veille crypto):
  cv-ingere.md, lettres-candidature-4-offres.md, lettre-h-consulting-ia-205LHJY.md,
  offres-marseille-2026-04-09.md, profil-candidat.md (racine),
  raw/profil-candidat.md, raw/lettre-type-base.md, lettre-type-base.md (8 fichiers)
- Git history préserve tout (pas d'archive physique)
- index.md nettoyé: references candidat enlees, total ~10 pages
- Decisions restantes: hugo-chabot.md (personne), market-signal (hors-taxonomie)
- Attente: validation decision 1 (hugo-chabot) et decision 2 (market-signal) avant etape 2

## [2026-05-04] schema-v1 | SCHEMA v1 integration — step 1: structure only
- Nouveau SCHEMA.md posé à la racine (remplace ancien schema informel)
- Git init + commit baseline: 20182a3 ("pre-schema-v1 baseline")
- Dossiers créés: sectors/, _pending/
- Rapport migration: _pending/MIGRATION_SCHEMA_V1.md
- Pages curées: 7 (toutes avec frontmatter basique)
- Pages non-curées: 14 fichiers + 14 data files
- Mapping vers taxonomy: hyperliquid→defi-perps, lido→defi-lst, restaking→defi-restaking
- Pages hors-taxonomie: hugo-chabot.md (personne), market-signal-2026-05.md (query générique)
- Docs candidat (cv, lettres, offres): suggéré déplacement vers personal/
- ETAPES NON FAITES: frontmatter enrichi, 8 skeleton sectors/, index.md mis à jour

## [2026-05-03] ingest | Daily report 2026-05-03
- /home/classics2323/wiki/raw/crypto-reports/daily-2026-05-03.md
- Signal: NEUTRE ⚪ (bull 18 / bear 14, ratio 1.29)
- Articles: 61, Tags: 10

