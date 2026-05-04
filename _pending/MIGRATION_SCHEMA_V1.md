# Migration SCHEMA v1 — Rapport étendu (étape 1bis)

**Date** : 2026-05-04
**Statut** : step 1 bis — inventaire complet + 3 décisions en suspens
**Git** : commit `57efbea` (structure + SCHEMA.md), baseline `20182a3`

---

## Annexe A — Inventaire complet du wiki (après suppression candidat)

### Tous les fichiers `.md` de `~/wiki/` (hors `crypto-surge/`)

| Chemin relatif | Lignes | Frontmatter | Catégorie |
|----------------|-------|-------------|-----------|
| `SCHEMA.md` | 177 | — | infrastructure wiki |
| `_pending/MIGRATION_SCHEMA_V1.md` | 113 | — | infrastructure wiki |
| `index.md` | ~50 | — | infrastructure wiki (nettoyé) |
| `log.md` | ~60 | — | infrastructure wiki |
| `raw/crypto-reports/daily-2026-05-03.md` | 52 | — | raw source |
| `entities/hyperliquid.md` | 37 | YAML | curée — defi-perps |
| `entities/lido.md` | 32 | YAML | curée — defi-lst |
| `entities/hugo-chabot.md` | 83 | YAML | curée — **hors-taxonomie** (decision 1 pending) |
| `concepts/restaking.md` | 41 | YAML | curée — defi-restaking |
| `concepts/risk-on-off.md` | 50 | YAML | curée — **transversal** (decision 2 pending) |
| `comparisons/perp-protocols.md` | 64 | YAML | curée — defi-perps |
| `queries/market-signal-2026-05.md` | 55 | YAML | curée — **hors-taxonomie** (decision 2 pending) |

**Total : 12 fichiers `.md`** (hors crypto-surge/).
**Supprimés ce jour** : 8 fichiers candidat (cv, lettres, offres, profil).

**Note :** les entrées de l'index pour les entities non-créées (aave, morpho, spark, tether, curve, uniswap, pendle, solana, ethereum, liquid-staking, perpetuals, yield-tokenization, flash-loans, ai-agents, agentic-ai, tvl-tracking, liquid-staking-vs-restaking) sont des placeholders dans l'index historique — les fichiers correspondants n'existent pas encore.

**Pourquoi tu voyais 19-25 pages :** l'`index.md` annonce "~25" — c'était une estimation arrondie.
Le compte réel est 20 fichiers .md hors crypto-surge/, plus les 14 fichiers data (surge JSON + daily reports .txt)
dans `crypto-surge/`, qui ne sont pas des pages curées.

---

### Répartition par statut

```
20 fichiers .md hors crypto-surge/
├── 13 avec frontmatter YAML
│   ├── 7 curées crypto/DeFi/AI         ← mon comptage initial
│   └── 6 curées candidat/hors-secteur  ← j'avais zappé celles-ci
└── 7 sans frontmatter
    ├── 4 infrastructure (SCHEMA, index, log, _pending)
    ├── 2 raw sources
    └── 1 duplicate
```

**Mon erreur initiale :** je n'avais inspecté que les 7 fichiers que j'avais moi-même écrits en session.
Je n'avais pas ouvert les 6 fichiers candidat (cv-ingere, lettres, offres, profil) ni les 2 raw sources,
donc je les avais exclus de mon comptage. Le chiffre correct est 13 fichiers avec YAML,
dont 7 crypto/DeFi et 6 candidat.

---

## Annexe B — Pages qui ne mappent vers aucun sous-secteur

### 1. `entities/hugo-chabot.md` — SUPPRIMÉ (2026-05-04)
Décision : suppression. Résidu de la phase job-search. Git commit `af41dfd`.

### 2. `queries/market-signal-2026-05.md` — GARDE EN PLACE (2026-05-04)
Décision : gardé dans `queries/` tel quel. `sectors: []` dans frontmatter.
query datée ad hoc — c'est le cas d'usage normal de ce dossier.

### 3. `concepts/risk-on-off.md` — GARDE EN PLACE (2026-05-04)
Décision : gardé dans `concepts/` tel quel. `sectors: []` dans frontmatter.
Concept transversal macro — applicable à tous les secteurs.
SCHEMA v1.1 a clarifié : concepts/ peuvent avoir `sectors: []`.

### 4. `cv-ingere.md`, `lettres-candidature-4-offres.md`, `lettre-h-consulting-ia-205LHJY.md`,
   `offres-marseille-2026-04-09.md`, `profil-candidat.md`
- **Contenu :** CV ingéré, lettres de motivation, offres d'emploi Marseille IA, profil candidat Hugo
- **Rangés :** en racine (sauf lettre-h-consulting dans raw/)
- **Pourquoi hors-taxonomie :** zero rapport avec DeFi ou AI crypto sectoriel
- **Verdict :** cf. §3.3 ci-dessous

### Pages sans frontmatter — pourquoi elles ne mappent pas

| Fichier | Raison |
|---------|--------|
| `SCHEMA.md` | infrastructure, remplacé par le nouveau SCHEMA v1 |
| `_pending/MIGRATION_SCHEMA_V1.md` | infrastructure temporaire |
| `index.md` | infrastructure wiki — pas une page curée |
| `log.md` | append-only log — pas une page curée |
| `raw/crypto-reports/daily-2026-05-03.md` | raw source layer 1 — ingérée telle quelle, pas curée |
| `raw/lettre-type-base.md` | raw source layer 1 — lettre candidate source |
| `raw/profil-candidat.md` | raw source layer 1 + **duplicata** de `profil-candidat.md` |
| `lettre-type-base.md` | raw source — **dupliqué de** `raw/lettre-type-base.md` |

---

## Annexe C — Décisions en suspens (OUTDATED — toutes tranchées)

Toutes les décisions ont été tranchées en 2026-05-04 :

- **Décision 1** (hugo-chabot) : SUPPRIMÉ → commit `af41dfd`
- **Décision 2** (market-signal) : GARDE EN PLACE → `sectors: []` dans frontmatter
- **Décision 3** (docs candidat) : SUPPRIMÉS → 8 fichiers supprimés, commit `990528f`
- **SCHEMA.md** : v1.1 — ajout section transversalité

Ce rapport est obsolète — gardé pour historique uniquement.

## État après décisions tranchées

- ✅ Git baseline: `20182a3`
- ✅ `sectors/` et `_pending/` créés
- ✅ SCHEMA.md v1.1 — section transversalité ajoutée
- ✅ Fichiers candidat supprimés (8 fichiers, `990528f`)
- ✅ hugo-chabot supprimé (`af41dfd`)
- ✅ market-signal gardé + schema clarifié
- ✅ risk-on-off gardé + schema clarifié
- ✅ index.md nettoyé
- ✅ log.md à jour
- ❌ **ÉTAPE 2 EN ATTENTE** : creation 12 sectors/ + migration frontmatter existants
