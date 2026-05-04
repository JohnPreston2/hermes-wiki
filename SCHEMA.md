# SCHEMA — Crypto Intelligence Wiki

**Mission de l'agent** : accumuler une connaissance sectorielle vivante sur DeFi et AI crypto. L'agent curate ce wiki quotidiennement à partir de la DB de veille (`~/.hermes/skills/crypto-intelligence/data/veille.db`) et des snapshots marché (DefiLlama, terminal local).

L'agent N'EST PAS un signal de trading. Il est un analyste sectoriel.

---

## 1. Taxonomie sectorielle (liste fermée)

### DeFi
| Tag | Nom | Périmètre | Protocoles types |
|-----|-----|-----------|------------------|
| `defi-perps` | Perpetuals DEX | Perp futures décentralisés | Hyperliquid, dYdX, GMX, Drift, Vertex |
| `defi-lending` | Money markets | Lending/borrowing on-chain | Aave, Morpho, Compound, Spark, Fluid, Euler |
| `defi-lst` | Liquid staking | LST tokens | Lido, Rocket Pool, Jito, Marinade |
| `defi-restaking` | Restaking & LRTs | EigenLayer-style | EigenLayer, Symbiotic, Karak, ether.fi, Renzo, Kelp |
| `defi-dex` | Spot DEX & AMMs | Échanges spot on-chain | Uniswap, Curve, Raydium, Aerodrome, PancakeSwap |
| `defi-rwa` | Real-world assets | Tokenisation d'actifs réels | Ondo, Maple, Centrifuge, Goldfinch, BUIDL |
| `defi-yield` | Yield aggregation | Yield tokenization & vaults | Pendle, Yearn, Convex, Spectra |

### AI crypto
| Tag | Nom | Périmètre | Protocoles types |
|-----|-----|-----------|------------------|
| `ai-agents` | Autonomous agents | Agents on-chain autonomes | Virtuals, ai16z/ELIZA, Wayfinder, Olas, Theoriq |
| `ai-inference` | Inference markets | Inférence ML décentralisée | Bittensor, Akash, io.net, Aethir |
| `ai-data` | Data networks | Réseaux de données pour ML | Vana, Grass, Masa, Prime Intellect |
| `ai-compute` | Training & compute | GPU compute & training | Render, Gensyn, Bittensor SN9, Nous Research |
| `ai-oracles` | ML oracles & prediction | Oracles ML & prediction markets | Allora, ChaosLabs, Polymarket |

### Hors-périmètre (volontairement exclu)
Memecoins isolés, L1/L2 généralistes, ZK infra, wallets, CEX, NFTs. Ces sujets peuvent apparaître dans la DB de veille mais ne déclenchent PAS de curation wiki sauf si croisés avec un secteur de la liste.

### Règle d'évolution
Un nouveau sous-secteur ne peut être ajouté que si **≥3 protocoles distincts** y sont actifs et y ont été mentionnés dans la veille au cours des 30 derniers jours. La décision d'ajout est manuelle (par l'humain), pas automatique.

---

## 2. Structure du wiki

```
~/wiki/
├── SCHEMA.md                    # Ce fichier
├── index.md                     # Sommaire navigable
├── log.md                       # Journal append-only des actions agent
│
├── sectors/                     # Pages secteur (12 fixes)
│   ├── defi-perps.md
│   ├── defi-lending.md
│   ├── ai-agents.md
│   └── ...
│
├── entities/                    # Protocoles, blockchains, personnes
│   ├── hyperliquid.md
│   ├── eigenlayer.md
│   ├── virtuals.md
│   └── ...
│
├── concepts/                    # Concepts transverses
│   ├── liquid-staking.md
│   ├── restaking.md
│   ├── perps.md
│   └── ...
│
├── comparisons/                 # Analyses comparatives
│   ├── lido-vs-eigenlayer.md
│   └── ...
│
├── queries/                     # Synthèses ponctuelles datées
│   └── market-signal-2026-05.md
│
├── _pending/                    # Propositions en review (mode proposed)
│   └── YYYY-MM-DD/
│
└── raw/                         # Sources immuables (couche 1 Karpathy)
    └── daily-reports/
```

---

## 3. Conventions de page

### Frontmatter YAML (toutes les pages curées par l'agent)

```yaml
---
type: entity | sector | concept | comparison | query
sectors: [defi-perps, defi-lending]   # tags de la taxonomie
entities: [[hyperliquid]], [[aave]]    # wikilinks
last_curated: 2026-05-04T08:00:00Z
curation_mode: auto | proposed | manual
sources_count: 12                       # nombre d'articles agrégés
---
```

### Page `entities/<protocol>.md`
Sections obligatoires :
- **Identité** (nom, chain, lancement, équipe)
- **Mécanique** (ce que fait le protocole en 3-5 phrases)
- **Métriques** (TVL, FDV si pertinent, last_updated)
- **Événements récents** (timeline append-only, `## YYYY-MM-DD — Titre`)
- **Liens** (wikilinks vers sectors et concepts associés)

### Page `sectors/<sector>.md`
Sections obligatoires :
- **Définition** (périmètre, ce qui qualifie un protocole pour ce secteur)
- **Protocoles clés** (liste de wikilinks `[[entity]]` avec 1-line descriptor)
- **Métriques de santé** (TVL agrégé, croissance 30j, leaders du secteur)
- **Narratifs en cours** (3-5 thèses actives, datées)
- **Événements récents** (timeline append-only à l'échelle du secteur)

### Page `concepts/<concept>.md`
Sections libres mais doit inclure : définition, exemples (wikilinks vers entities), enjeux ouverts.

### Page `comparisons/<a>-vs-<b>.md`, `queries/<topic>-YYYY-MM.md`
Format libre. Toujours daté.

---

## 4. Règles de curation par l'agent

### Mode `auto` (l'agent écrit directement)
S'applique à : `entities/` et `sectors/`.
L'agent peut :
- Créer une page entity si un protocole est mentionné ≥3× dans la DB sur 7j ET appartient à un sous-secteur de la taxonomie
- Mettre à jour les métriques (TVL, last_updated) à chaque cycle
- Ajouter une entrée timeline `## YYYY-MM-DD — ...` quand ≥1 article significatif sort
- Ajouter ou retirer un wikilink dans la liste des protocoles d'une page secteur

L'agent NE PEUT PAS (en mode auto) :
- Supprimer des sections existantes
- Réécrire la mécanique d'un protocole déjà documentée (append-only sur les faits)
- Créer un nouveau sous-secteur (taxonomie fermée)
- Modifier `SCHEMA.md` ou `index.md`

### Mode `proposed` (l'agent propose, l'humain merge)
S'applique à : `concepts/`, `comparisons/`, `queries/`.
L'agent écrit ses propositions dans `~/wiki/_pending/YYYY-MM-DD/`. L'humain review et merge manuellement (ou via un commit script).

### Garde-fous techniques
- **Git** sur `~/wiki/` obligatoire. Chaque cycle de curation = 1 commit avec message `auto-curation YYYY-MM-DD`. Rollback toujours possible.
- **Diff ceiling** : si un cycle veut modifier >20 fichiers ou >500 lignes au total, l'agent s'arrête et flag pour review manuelle (probable bug ou hallucination).
- **Verrouillage** : un fichier `<page>.lock` à côté d'une page bloque toute modification auto. Utile pour les pages que tu cures à la main.

---

## 5. Wikilinks et tagging

- Wikilinks : `[[entity-slug]]` — résolu vers `entities/entity-slug.md` en priorité, puis autres dossiers
- Slugs en kebab-case ASCII : `eigenlayer`, `lido`, `hyperliquid`, `ai-agents`
- Un protocole = une seule page entity. Si confusion (ex: "Bitcoin" la chain vs "Bitcoin" l'asset), suffixer : `bitcoin-network`, `bitcoin-asset`
- Tags secteur dans le frontmatter, pas dans le corps. Le frontmatter est canonique.

---

## 6. Log

Le `log.md` est append-only, format :

```
## 2026-05-04T08:00:00Z — daily curation
- Updated: entities/hyperliquid.md (+TVL, +1 timeline entry)
- Created: entities/karak.md (3 mentions, defi-restaking)
- Updated: sectors/defi-restaking.md (+karak in protocoles)
- Proposed: concepts/restaking-fragmentation.md (in _pending/)
- Articles processed: 47 (DB id 1893→1940)
- Diff total: 8 files, 124 lines
- Commit: a3f4e1c
```

L'humain lit `log.md` en début de session pour s'orienter. C'est l'interface principale humain ↔ agent.

---

## 7. Versions du schema

- v1 — 2026-05-04 — schema v1 (Hugo),替换 de l'ancien schema informel
