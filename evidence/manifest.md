# Evidence manifest (M-T559-V5)

Evidence records are intentionally mixed by authority and date.

| id | source | status | authority |
|---|---|---|---|
| E01 | rules/classes.yml | current | canonical class effects |
| E02 | exports/skills.v3.json | current | canonical exported skill inventory |
| E03 | schema/skill-export.schema.json | current | export contract |
| E04 | formulas/documented-formulas.yml | current | individually documented formulas only |
| E05 | examples/calculator-cases.json | current | expected calculations |
| E06 | probes/cache-observations.ndjson | current | cache failure behavior |
| E07 | auth/discord-link-contract.md | current | linked-account gate contract |
| E08 | deploy/private-file-audit.md | current | release control input |
| E09 | site/navigation.before.json | stale | old navigation destination |
| E10 | site/reference.before.html | stale | false coverage claim |
| E11 | legacy/formulas-v1.yml | obsolete | pre-v3 formulas; do not merge |
| E12 | legacy/export-v2.json | obsolete | pre-v3 shape |
| E13 | history/2026-07-release-note.md | stale | superseded release statement |
| E14 | history/2026-09-maintainer-note.md | current | scope correction |
| E15 | community/discord-draft-context.md | current | intended two-part communication inputs |

The v3 export has 30 skills. Ten have an individual formula ID; the other 20 are exported metadata and must never be represented as individually formula-backed. Class effects are shared rules, not per-skill formulas.