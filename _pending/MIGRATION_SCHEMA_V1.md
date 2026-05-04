# Migration SCHEMA v1 — Rapport (étape 1)

**Date** : 2026-05-04
**Statut** : structure uniquement — frontmatter et sectors/ pas encore migrés

---

## 1. État des pages existantes

### Pages curées (avec frontmatter YAML) — 7 pages

| Fichier | Type actuel | Frontmatter | Sous-secteur assigné |
|---------|------------|-------------|---------------------|
| `entities/hyperliquid.md` | entity | ✅ | `defi-perps` |
| `entities/lido.md` | entity | ✅ | `defi-lst` |
| `entities/hugo-chabot.md` | entity | ✅ | **hors-taxonomie** |
| `concepts/restaking.md` | concept | ✅ | `defi-restaking` |
| `concepts/risk-on-off.md` | concept | ✅ | cross-sector |
| `comparisons/perp-protocols.md` | comparison | ✅ | `defi-perps` |
| `queries/market-signal-2026-05.md` | query | ✅ | **hors-taxonomie** |

### Pages non-curées (sans frontmatter YAML) — 14 fichiers

| Fichier | Nature | Action |
|---------|--------|--------|
| `index.md` | sommaire navigable | à migrate (frontmatter + sections sectors/) |
| `log.md` | journal | format déjà compatible avec v1 |
| `raw/crypto-reports/daily-2026-05-03.md` | source brute | layer 1 Karpathy — ok, hors curation |
| `raw/lettre-type-base.md` | source brute candidat | ok |
| `raw/profil-candidat.md` | source brute candidat | ok |
| `cv-ingere.md` | doc candidat | hors-secteur crypto/DeFi |
| `lettre-type-base.md` | lettre candidate | hors-secteur |
| `lettre-h-consulting-ia-205LHJY.md` | lettre candidate | hors-secteur |
| `lettres-candidature-4-offres.md` | lettres candidates | hors-secteur |
| `offres-marseille-2026-04-09.md` | offres d'emploi | hors-secteur |
| `profil-candidat.md` | profil candidat | hors-secteur |

### Fichiers data (hors wiki) — 14 fichiers

| Dossier | Contenu |
|---------|---------|
| `crypto-surge/*.json` | surge RSS — données, pas du wiki curatif |
| `crypto-surge/*.txt` | daily/weekly reports — à déplacer dans `raw/crypto-reports/` |

---

## 2. Mapping vers la taxonomie

### Pages à migrer dans `sectors/`

| Secteur | Pages existantes |
|---------|-----------------|
| `defi-perps` | `entities/hyperliquid.md` + `comparisons/perp-protocols.md` |
| `defi-lst` | `entities/lido.md` |
| `defi-restaking` | `concepts/restaking.md` |
| `cross-sector` | `concepts/risk-on-off.md` |

### Pages à créer dans `sectors/` (12 - 4 existants = 8 à créer)

À faire en étape 2 :
- `sectors/defi-lending.md` — pas d'entity correspondante encore (Aave, Morpho viendront de la veille)
- `sectors/defi-restaking.md` — skeleton seulement (restaking.md existe déjà)
- `sectors/defi-dex.md`
- `sectors/defi-rwa.md`
- `sectors/defi-yield.md`
- `sectors/ai-agents.md`
- `sectors/ai-inference.md`
- `sectors/ai-data.md`
- `sectors/ai-compute.md`
- `sectors/ai-oracles.md`

### Pages à discuter — décisions requises

1. **`entities/hugo-chabot.md`** : personne (profil candidat), hors-taxonomie secteurs DeFi/AI. Options :
   - Garder dans `entities/` avec tag `person` (non prévu dans taxonomy mais acceptable)
   - Déplacer dans `_archive/` ou dans un sous-dossier `personal/`

2. **`queries/market-signal-2026-05.md`** : market signal généraliste, pas aligné sur la taxonomy sectors. Option :
   - Ajouter un tag sector fictif `market-intelligence` au frontmatter (violation mineure de la taxonomy)

3. **Docs candidat (cv-ingere.md, lettres, offres)** : tous hors-secteur crypto/DeFi. Option :
   - Créer un dossier `personal/` ou `_archive/personal/` pour ces fichiers
   - Ou les laisser en racine tel quel

4. **`crypto-surge/*.txt`** : daily/weekly reports générés automatiquement. Options :
   - Les déplacer dans `raw/crypto-reports/` (plus propre)
   - Ou les laisser dans `crypto-surge/` comme archive machine-readable

---

## 3. Frontmatter à migrer

Toutes les 7 pages curées ont un frontmatter basique. À enrichir en étape 2 :

```yaml
# Ajouter à toutes les entities :
sectors: [defi-perps]          # tag taxonomie
entities: []                    # wikilinks vers protocoles liés
last_curated: 2026-05-04T00:00:00Z
curation_mode: auto
sources_count: N                # compter depuis la DB
```

---

## 4. Prochaines étapes (étape 2 — non faites)

1. Migrer le frontmatter des 7 pages curées
2. Créer les 8 pages skeleton dans `sectors/`
3. Créer `personal/` et déplacer les docs candidat
4. Déplacer les `.txt` daily reports dans `raw/crypto-reports/`
5. Mettre à jour `index.md` avec la section `sectors/`
6. Commit : `auto-curation schema-v1-step2`
