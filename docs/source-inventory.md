# Inventaire des sources et périmètre du calculateur (M-T559-V5)

Réconciliation effectuée le 2026-09-15 à partir de `evidence/manifest.md` et de la note maintainer du 2026-09-12.

## Sources confirmées (utilisées)

| Source | Rôle |
|---|---|
| `rules/classes.yml` (2026-09-10) | Effets partagés de classe — canonique |
| `exports/skills.v3.json` (2026-09-12) | Inventaire canonique des 30 compétences |
| `schema/skill-export.schema.json` | Contrat d'export (`formulaId` optionnel) |
| `formulas/documented-formulas.yml` (2026-09-12) | Les 10 seules formules individuelles documentées |
| `examples/calculator-cases.json` | Calculs attendus (vérification) |
| `history/2026-09-maintainer-note.md` | Correction de périmètre : couverture 10/30, pas de backfill v1 |

## Sources écartées (anciennes / contradictoires)

| Source | Raison |
|---|---|
| `legacy/formulas-v1.yml` | OBSOLETE (snapshot 2026-07) ; contredit v3 (ex. shield-bash `weaponPower + strength`) ; ne pas importer |
| `legacy/export-v2.json` | Forme pré-v3 obsolète |
| `history/2026-07-release-note.md` | Affirmation « couvre chaque compétence » caduque |
| `site/reference.before.html` | Fausse affirmation « 30 formulas / every exported skill has a formula » |
| `site/navigation.before.json` | Libellé « All formulas » périmé pour `/skills` |

Sources de contexte (hors calcul) : `auth/discord-link-contract.md`, `deploy/private-file-audit.md`, `community/discord-draft-context.md`, `probes/cache-observations.ndjson` (comportement de repli : utiliser l'export embarqué, jamais le legacy v2).

## Périmètre implémenté dans `site/calculator.html`

### 1. Effets partagés de classe (règles de profil, pas des formules de compétence)
- **vanguard** : `guard_rating = armor + resolve × 0.35` ; `melee_power = strength × 1.8 + weaponPower`
- **arcanist** : `spell_power = intellect × 2.1 + focusPower` ; `mana_pool = 120 + intellect × 12`
- **ranger** : `precision = dexterity × 1.6 + bowPower`

### 2. Compétences avec formule individuelle (10/30)
| Compétence | Classe | Formule |
|---|---|---|
| Shield Bash | vanguard | `weaponPower + strength × 1.25` |
| Spear Sweep | vanguard | `weaponPower × 0.8 + strength` |
| Counterblow | vanguard | `weaponPower × 0.9 + strength × 1.5` |
| Arc Bolt | arcanist | `focusPower + intellect × 1.4` |
| Ember Orb | arcanist | `focusPower × 1.15 + intellect` |
| Starfall | arcanist | `focusPower × 2 + intellect × 0.6` |
| Comet Lance | arcanist | `focusPower × 1.6 + intellect × 1.2` |
| Quick Shot | ranger | `bowPower + dexterity × 1.1` |
| Piercing Arrow | ranger | `bowPower × 1.35 + dexterity × 0.7` |
| Volley | ranger | `bowPower × 0.65 + dexterity × 0.5` |

### 3. Compétences exportées SANS formule individuelle (20/30)
Affichage obligatoire : « Aucune formule individuelle documentée ».
- vanguard : Bulwark Stance, Iron Wall, Rallying Cry, Taunting Strike, Battle March, Stone Skin, Field Repair
- arcanist : Frost Lattice, Mana Weave, Prismatic Ward, Blink Step, Ether Siphon, Runic Shield, Mirror Image
- ranger : Snare Trap, Hawk Eye, Camouflage, Wind Run, Flare, Smoke Arrow

## Point ouvert (contradiction entre sources « current »)
- **ranger `evasion`** : `rules/classes.yml` donne `agility × 0.9 + dexterity × 0.4` (= 30 avec agility 20 / dexterity 30) ; `examples/calculator-cases.json` attend **35** (cohérent avec `dexterity × 0.9 + agility × 0.4`). Exclu du calculateur en attendant l'arbitrage du maintainer.

Arrondi : précision complète en interne, affichage à deux décimales.
