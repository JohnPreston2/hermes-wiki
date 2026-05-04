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

Voici les pages curées (YAML frontmatter) pour lesquelles je ne trouve pas de mapping propre
vers un des 12 tags de la taxonomie SCHEMA.md.

### 1. `entities/hugo-chabot.md` — personne physique
- **Contenu :** page identité personnelle — nom, profil tech (Python/Flask/LLM/RAG/DeFi), PharmD+MSc ESCP, contact
- **Rangé :** `entities/`
- **Pourquoi hors-taxonomie :** la taxonomy couvre les protocoles, blockchains, personnes (enfin —
  le SCHEMA dit "entities/ : Protocoles, blockchains, personnes"). Mais le tag `person` n'existe
  pas dans la taxonomie sectorielle DeFi/AI. Le frontmatter actuel ne contient qu'un champ `type: entity`.
  Aucune suggestion de tag sectors valide.
- **Verdict :** mapping bancal. Soit la taxonomy doit accepter un tag `person` ou `personal`,
  soit cette page n'est pas une entity au sens SCHEMA.

### 2. `queries/market-signal-2026-05.md` — signal marché macro
- **Contenu :** résumé mensuel du signal RISK ON/OFF, ratio bull/bear, prix BTC ETH, sentiment
- **Rangé :** `queries/`
- **Pourquoi hors-taxonomie :** c'est une synthèse macro transversale, pas l'analyse d'un protocole
  ou d'un secteur DeFi/AI. Aucun des 12 tags ne couvre "macro market sentiment". C'est le seul
  fichier dans `queries/` et il est en良品 avec la mission SCHEMA (analyse sectorielle DeFi/AI).
- **Verdict :** ne force pas. Cette page est une query ad hoc historique. Elle ne décrit pas un
  protocole ni un concept sectoriel. Deux options ci-dessous (§3.2).

### 3. `concepts/risk-on-off.md` — concept transversal
- **Contenu :** définition du signal RISK ON vs RISK OFF — macro risk appetite, corrélations
 BTC/ETH avec S&P 500, cas d'usage pour timing
- **Rangé :** `concepts/`
- **Pourquoi transversal :** c'est un concept d'analyse macro qui s'applique à tous les secteurs
  indistinctement. Il n'est pas spécifique à defi-perps ni à defi-lending. Il croise la taxonomy
  mais n'appartient à aucun sous-secteur en propre.
- **Note :** c'est un concept légitime et utile — le problème est que le SCHEMA suppose que les
  concepts appartiennent à des secteurs, ce qui n'est pas toujours vrai.
- **Verdict :** concept valide mais transversal. Ne pas forcer dans un sector. À conserver
  tel quel et ajouter au frontmatter un tag non-taxonomique (ex: `meta: macro`) en wait-and-see.

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

## Annexe C — 3 décisions en suspens

---

### Décision 1 — `entities/hugo-chabot.md`

**Contenu actuel :**
Page entity décrivant Hugo Chabot / John Preston — PharmD + MSc ESCP, AI Builder à Marseille,
profil tech Python/Flask/LLM/RAG/blockchain/DeFi, contact hugochabot@hotmail.fr.
Frontmatter actuel : `type: entity`, pas de champ `sectors`.

**Rangé :** `~/wiki/entities/hugo-chabot.md`

**Options :**

**A — Garder tel quel dans `entities/`**
Avancer que "personnes" est une sous-classe d'entities même si la taxonomy est sectorielle.
Ajouter au frontmatter un tag hors-taxonomie `type_entity: person`. Le fichier reste accessible
dans le wiki et le SCHEMA est minoritairement violé (une exception, pas une refactor).

**B — Déplacer vers `personal/` (recommandé à titre indicatif)**
Créer `~/wiki/personal/` et y ranger :
- `entities/hugo-chabot.md`
- `cv-ingere.md`
- `lettres-candidature-4-offres.md`
- `lettre-h-consulting-ia-205LHJY.md`
- `offres-marseille-2026-04-09.md`
- `profil-candidat.md`
Cela sépare physiquement le wiki crypto/DeFi de la documentation candidat, sans rien perdre.
Le SCHEMA ne couvre que `sectors/`, `entities/`, `concepts/`, `comparisons/`, `queries/` —
rien n'empêche d'ajouter un sibling `personal/`.

**C — Archiver dans `_archive/personal/`**
Même effet que B, avec marqueur d'archive. La page reste accessible mais n'est plus
dans le flux de navigation principal.

**À trancher :** A / B / C

---

### Décision 2 — `queries/market-signal-2026-05.md`

**Contenu actuel :**
Synthèse du signal RISK ON/OFF pour mai 2026 — ratio bull/bear headlines,
prix BTC $78K/ETH $2.3K/SOL $84K, sentiment neutre.
Fichier unique dans `queries/` (pas d'autre query).

**Rangé :** `~/wiki/queries/market-signal-2026-05.md`

**Options :**

**A — Déplacer vers `personal/` avec les docs candidat**
Même traitement que la décision 1. Cette query a été écrite dans le cadre
de la veille crypto mais n'a pas de valeur sectorielle pérenne. Elle documente
un moment dans le temps, pas un protocole.

**B — Garder dans `queries/` avec tag `sectors: [market-intelligence]`**
Créer un 13e tag dans la taxonomy "market-intelligence" pour couvrir les synthèses
macro-adjacent. C'est une violation de la liste fermée (règle d'évolution :
≥3 protocoles pour créer un nouveau tag), mais c'est un concept transversal utile.

**C — Archiver dans `_archive/queries/`**
La query est datée (mai 2026). Elle a été utile à un instant T. Elle n'a pas
de raison de vivre dans un wiki sectoriel permanent.

**À trancher :** A / B / C

---

### Décision 3 — Les 6 fichiers candidat/hors-secteur

**Contenu actuel :**
- `cv-ingere.md` — CV PDF ingéré en markdown, tags `cv, 2026-04-09`
- `lettres-candidature-4-offres.md` — 4 lettres motivation pour offres IA/Python/LLM Marseille
- `lettre-h-consulting-ia-205LHJY.md` — lettre spécifique pour une offre H CONSULTING
- `offres-marseille-2026-04-09.md` — 9 offres détectées en avril 2026
- `profil-candidat.md` — profil structuré Hugo (skills, parcours, contact)
- `lettre-type-base.md` — lettre type candidate (dupliqué dans raw/)

**Rangés :** `cv-ingere.md`, `lettres-candidature-4-offres.md`, `offres-marseille-2026-04-09.md`,
`profil-candidat.md` en racine. `lettre-h-consulting-ia-205LHJY.md` dans `raw/`.
`lettre-type-base.md` en racine (dupliqué avec `raw/lettre-type-base.md`).

**Note sur les duplicatas :**
- `profil-candidat.md` (racine, 4902 o) ≈ `raw/profil-candidat.md` (même contenu, même taille)
- `lettre-type-base.md` (racine, 2368 o) = `raw/lettre-type-base.md` (contenu identique)
À nettoyer avant ou pendant la migration.

**Options :**

**A — Tout déplacer dans `personal/` (recommandé)**
```
personal/
├── cv.md
├── profil.md
├── lettres/
│   ├── lettres-4-offres-2026-04-09.md
│   ├── lettre-h-consulting.md
│   └── lettre-type-base.md
└── offres/
    └── offres-marseille-2026-04-09.md
```
Suppress aussi les 2 duplicatas (raw/profil-candidat.md + raw/lettre-type-base.md).
Le wiki crypto/DeFi reste propre. La documentation candidat reste accessible.

**B — Tout archiver dans `_archive/personal/`**
Même chose que A mais avec un marqueur `_archive/`. Les fichiers ne sont plus dans
le flux principal mais sont récupérables.

**C — Tout laisser en racine**
Ne rien toucher. Les fichiers sont un peu hors-secteur mais ne dérangent pas.
Risque : le wiki grossit avec du bruit. Le SCHEMA n'est pas respecté pour ces fichiers.

**D — Tout supprimer (archiver dans git history)**
Si ces fichiers n'ont plus de valeur active (candidatures closes ?), les supprimer.
La git history conserve tout — rollback possible.

**Décision prise (2026-05-04) : Option D — SUPPRIMÉS**
Les 8 fichiers candidat ont été supprimés. Git history conserve tout. Le wiki crypto/DeFi est propre.
Fichiers supprimés : cv-ingere.md, lettres-candidature-4-offres.md, lettre-h-consulting-ia-205LHJY.md,
offres-marseille-2026-04-09.md, profil-candidat.md (racine + raw/), lettre-type-base.md (racine + raw/).

**À trancher :** ~~A / B / C / D~~ — DÉCIDÉ

---

## État après étape 1

- ✅ Git init + baseline commit `20182a3`
- ✅ `sectors/` et `_pending/` créés
- ✅ `SCHEMA.md` v1 posé
- ✅ log.md mis à jour
- ✅ Inventaire complet documenté dans ce fichier
- ✅ 3 décisions identifiées (1B, 2A/C, 3A recommandées à titre indicatif)
- ❌ Étape 2 NONFAITE — frontmatter enrichi, skeleton sectors/, index.md, personal/

**Prochaine étape (étape 2) — EN ATTENTE de validation explicite sur les 3 décisions.**
