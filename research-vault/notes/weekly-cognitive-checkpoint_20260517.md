# Weekly Cognitive Checkpoint — 2026-W20

**Date**: 2026-05-17 19h UTC
**Analyste**: MiniMax M2.7

---

## Accuracy de la semaine (May 10-17, 635 alertes uniques)

### Par signal type
| Signal | Score | Observation |
|---|---|---|
| NEUTRAL | 84% (87/104) | Stable, above baseline 79% — keeper |
| BEARISH | 40% (113/284) | Aligned with 42% baseline — acceptable |
| BULLISH | **23% (61/265)** | **CATASTROPHIC** vs baseline 58% — broken |

### Par token (top/bottom 5)
| Token | Accuracy | Alertes | Status |
|---|---|---|---|
| COMP | 93% (14/15) | 15 | 🔵 Fiable |
| PHB | 82% (9/11) | 11 | 🔵 Fiable |
| ENS | 75% (9/12) | 12 | 🔵 Fiable |
| NEAR | 69% (11/16) | 16 | 🟡 Acceptable |
| CRV | 67% (8/12) | 12 | 🟡 Acceptable |
| ETH | 20% (6/30) | 30 | 🔴 A filtrer |
| BTC | 23% (10/44) | 44 | 🔴 A filtrer |
| UNI | 25% (13/53) | 53 | 🔴 A filtrer |
| WLD | 28% (12/43) | 43 | 🔴 A filtrer |
| LDO | 23% (10/44) | 44 | 🔴 A filtrer |

### Par score threshold
| Score | Accuracy | Alerts | Note |
|---|---|---|---|
| >= 30 | 41% (258/635) | 635 | baseline |
| >= 40 | 51% (229/445) | 445 | +10pp |
| >= 70 | 43% (22/51) | 51 | score 70-74 only |
| >= 75 | **8% (1/12)** | 12 | **BROKEN** |

### Par regime
| Regime | Count | % du total |
|---|---|---|
| NEUTRAL | 217 | 34% |
| BEAR | 195 | 31% |
| EXTREME_BULL | 168 | 26% |
| EXTREME_BEAR | 63 | 10% |
| BULL | 22 | 3% |
| UNKNOWN | 6 | 1% |

---

## Patterns observés

**[CRITIQUE] WLD HL/BN spread_z extreme precede crash -8%**
- May 13-15: WLD spread_z monte de +2.18 a +10.35 (HL funding 10σ au-dessus de BN)
- Le système genere BULLISH score 30 sur cette base (HL funding > BN = "smart money long")
- Mai 15 17h32: prix WLD chute de -8.56% en 4h
- **Interpretation revisee**: spread_z extreme signale des longs HL surcharges, pas accumulation. Le crash est la resolution normale.
- Les memes extremes sur UNI (spread_z +11.75) et LINK (+4.36) — meme pattern.

**[CRITIQUE] Score 75 = faux ami**
- 12 alertes score>=75 cette semaine, 1 correcte seulement (8%)
- AAVE a contribue la majorite: score 75 sur AAVE = NEUTRAL regime (spread_z +1.83 a +3.93), prix stable
- AAVE BEAR score 75 (spread_z=-1.80) = 100% correct cette semaine (4/4)
- **Conclusion**: le score 75 n'est pas un gauge de confiance — c'est un reglage technique. La direction reelle vient du sign du spread_z.

**[CONFIRME] Regime EXTREME_BULL = anti-bull pour signaux supplementaires**
- 26% des alertes de la semaine etaient en regime EXTREME_BULL
- Sur ces 168 alertes EXTREME_BULL, BULLISH a ete quasi systematiquement faux
- L'extreme funding sur BN precede une compression bear — pas un signal d'achat

**[OBSERVE] AAVE: trop de bruit, regime instable**
- 68 alertes en 7 jours (freq la plus haute, avant UNI 53 et WLD 43)
- Le regime oscille entre BEAR et NEUTRAL, le prix reagit souvent dans le sens oppose
- Urgency a chute 64→35 cette semaine (mai 16) — regime BEAR confirmé

**[OBSERVE] BTC reste dans EXTREME_BEAR mais funding stable**
- Regime EXTREME_BEAR stable toute la semaine
- Mais BULLISH sur BTC a 23% accuracy seulement
- Le regime extreme bear semble etre un etat stable, pas un catalyst

---

## Leçons marché

1. **Regle WLD**: si spread_z HL/BN > +5 sur token volatil (WLD, UNI, LINK) → lire comme crowded long = bearish 4h. Interdire BULLISH dans ces conditions.
2. **Score 75 broken**: ne pas utiliser comme filtre de confiance. Le score ne capture pas le sign du spread_z ni la qualite du regime.
3. **Filtrer AAVE**: le regime instable genere trop de faux signaux. Augmenter le seuil de convergence pour AAVE (score min 70 au lieu de 60).
4. **EXTREME_BULL regime = silence** (no additional signals needed)
5. **UNI et WLD sont des token probleme** pour les signaux BULLISH — leur volatilite naturelle rend les z-scores HL peu fiables.

---

## Ajustements recommandés

### Seuils
- AAVE: score min 65 → **70** (filtrer les alerts regime instable)
- WLD: score min 30 → **50** OU blacklist BULLISH sur WLD quand spread_z > +3
- UNI: blacklist BULLISH quand spread_z > +3 (volatile, prone a crash)
- LINK: blacklist BULLISH quand spread_z > +2 (plus stable que WLD/UNI)

### Baselines
- Pas de changement requis sur les baselines funding (7j/30j)
- Considerer une baseline HL-specifique pour WLD/UNI (plus volatile)

### Protocols
- Ajouter COMP a la liste prioritaire (93% accuracy)
- Ajouter PHB a la liste prioritaire (82% accuracy)
- **Supprimer WLD de la liste BULLISH** (ou blacklist si spread_z > +5)
- **Supprimer UNI de la liste BULLISH** (ou blacklist si spread_z > +3)

### Regles de convergence
- **Nouvelle regle**: si spread_z > +5 AND regime = EXTREME_BULL/BULL → generer SHORT alert au lieu de BULLISH
- **Nouvelle regle**: si spread_z < -3 AND regime = BEAR/EXTREME_BEAR → generer SHORT alert (confirmation short)

---

## Thesis semaine prochaine (W21)

Le marche reste en range etrange avec des regimes extremes. Le probleme principal cette semaine etait l'inference BULLISH sur des tokens deja en EXTREME_BULL (WLD, UNI, AAVE). La semaine prochaine, s'attendre a:
- Compression des spread_z sur WLD/UNI (retour a la normale) — consolidation possible
- Regime BTC probablement stable EXTREME_BEAR avec peu de catalyseurs haussiers
- AAVE: surveiller le passage BEAR→NEUTRAL (indiquerait fin de la periode de stress)
- Hyperliquid ecosystem (HYPE) reste le seul catalyseur haussier visible

**Confidence: LOW** (filtres encore en cours de calibration, historique 7j trop court pour certitude)
