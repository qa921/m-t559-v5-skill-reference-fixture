# Discord-linked reference gate

- `/skills` is the gated detailed reference; `/calculator` remains public.
- The gate calls `getLinkedDiscordAccount(userId)` after normal account-session resolution.
- Linked account result: allow the reference. Missing link: offer Discord linking; do not log the user out and do not affect `/account` or `/drops`.
- Cache error/timeout: fail closed for `/skills` with a retry-safe service message; preserve account session and all unrelated routes.
- Never treat a Discord display name as proof of linkage.
- No Discord OAuth client ID, role ID, guild ID, or secret is supplied in this fixture.