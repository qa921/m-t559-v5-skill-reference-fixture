# Pre-release control inputs

Expected public: calculator assets and public route only.

Must remain private / excluded from client bundle: `.env`, `config/discord-oauth.private.json`, `ops/cache-token.txt`, any linked-account lookup responses.

Known baseline gaps:
- `site/navigation.before.json` has a stale `/skills` label "All formulas".
- no CI deployment report exists.
- no secret scan or build output is included.

These are inputs for a future deployment checklist, not evidence that deployment controls ran.