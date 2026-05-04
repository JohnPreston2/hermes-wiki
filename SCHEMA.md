# Wiki Schema

> Last updated: 2026-05-03 | Version: 2.0

## Domain

**Primary:** Crypto/DeFi/AI intelligence — veille permanente sur l'écosystème DeFi, agents IA, et leur intersection.
**Secondary:** Job search — recherche d'emploi AI Builder à Marseille.

## Conventions

- File names: `lowercase-hyphens.md` — pas d'espaces, pas de majuscules
- Every wiki page starts with YAML frontmatter (required)
- Use `[[wikilinks]]` pour lier les pages entre elles — minimum 2 liens sortants par page
- Quand une page est mise à jour: bumps `updated` date dans frontmatter
- Toute nouvelle page → ajoutée à `index.md` dans la bonne section
- Toute action (ingest, create, query, lint) → appended to `log.md`
- Fichiers dans `raw/` = immutables. Corrections dans les pages wiki, jamais dans raw.
- Les daily reports crypto → d'abord ingérer en `raw/crypto-reports/`, puis créer/update les pages entities/concepts

## Frontmatter

```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary | raw | daily-report
tags: [from taxonomy below]
sources: [raw/crypto-reports/daily-2026-05-03.md]
summary: "One-line description for index.md"
---
```

## Tag Taxonomy

### Crypto / DeFi
- `defi`: general DeFi ecosystem
- `lending`: Aave, Morpho, Spark, Compound...
- `liquid-staking`: Lido, EtherFi, Renzo, EigenLayer, restaking
- `perp`: perpetuals, dYdX, Hyperliquid, GMX, Drift
- `stablecoin`: USDT, USDC, DAI, stablecoin yield
- `bridge`: bridge protocols, cross-chain
- `amm`: Uniswap, Curve, DEX mechanics
- `yield`: yield strategies, APY/APR
- `governance`: DAO, token voting
- `exploit`: hacks, exploits, rugs
- `regulatory`: SEC, CFTC, MiCA, lois

### AI / Agents
- `ai-agent`: AI agents, autonomous protocols
- `llm`: LLM providers, models
- `ai-infrastructure`: compute, render, io.net
- `token-ai`: AI tokens, $FET, $RNDR, $OCEAN, $TAO

### Market / Meta
- `market-signal`: RISK ON/OFF, sentiment
- `tvl`: TVL tracking, protocol TVL
- `on-chain`: blockchain data, fees, mempool
- `news`: actualité générale

### Job Search
- `profil`: profil candidat
- `offres`: offres d'emploi
- `candidature`: lettres de motivation, applications

### Meta
- `comparison`: side-by-side analysis
- `query`: filed query result
- `archived`: superseded content

## Page Thresholds

| Action | Condition |
|--------|-----------|
| Créer entity | Protocole/chaîne mentionné dans 3+ sources ou TVL > $500M |
| Créer concept | Mécanisme/pattern couvert dans 2+ sources |
| Créer comparison | Comparaison demandée ou différence identifiée dans sources |
| Créer query | Réponse substantielle qui mériterait d'être recodée |
| Créer daily-report | Ingest automatique quotidien (cron) |

## Entity Pages

Une page par protocole, chaîne, ou personne notable. Inclut:
- Overview — ce que c'est, quand lancé
- Faits clés (TVL, token, chaînes supportées)
- Relationships (`[[wikilinks]]` vers protocoles liés)
- Sources

## Concept Pages

Une page par mécanisme ou topic. Inclut:
- Définition / explanation
- État actuel du domaine
- Questions ouvertes
- Related concepts (`[[wikilinks]]`)

## Daily Report Ingestion (automated)

1. Daily report arrives in `raw/crypto-reports/daily-YYYY-MM-DD.md`
2. Agent lit le rapport → extracte protocoles, événements, signaux
3. Met à jour les entity pages concernées (TVL, news)
4. Ajoute les nouveaux protocoles/events au log
5. Met à jour `index.md` si nouvelles pages créées

## Update Policy

Quand nouvelle info contredit contenu existant:
1. Vérifier les dates — sources récentes > anciennes
2. Si vraiment contradictoire: noter les deux positions avec dates
3. Ajouter `contradictions: [[page-name]]` dans frontmatter
4. Flag pour review utilisateur dans lint report

## Log Rotation

`log.md` → rotate quand > 300 lignes → rename `log-YYYY.md`
