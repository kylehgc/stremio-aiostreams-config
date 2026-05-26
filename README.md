# stremio-aiostreams-config

Personal AIOStreams configuration backups (sanitized — no credentials).

## Files

- `aiostreams-fullquality.json` — 4K-priority profile (Android / iOS / living room TV)
- `aiostreams-bedroom.json` — Same config but with `excludedResolutions: ["2160p"]` for the bedroom TV that can't do 4K

## What was scrubbed

All `REDACTED` placeholders mark removed secrets:

- `services[*].credentials.*` — TorBox / Real-Debrid API keys
- `tmdbAccessToken`, `tmdbApiKey` — TMDB credentials
- `rpdbApiKey` — RatingPosterDB key
- `presets[*].options.*` — anything matching `api_key|token|secret|password|auth|credential`
- `proxy.*` — proxy URL & credentials

## Restoring

1. Open https://aiostreams.elfhosted.com/stremio/configure
2. Navigate to Save / Install menu
3. Click **Import** and select one of these JSON files
4. Re-enter your credentials wherever you see `REDACTED`:
   - Services → Real-Debrid + TorBox API keys
   - Settings (or Metadata section) → TMDB Read Access Token + API Key
   - Settings → RPDB API Key
5. Set a password, click **Create**, install the generated manifest URL into Stremio

## Diff between the two

The only intentional difference is `excludedResolutions`:
- Full Quality: `[]` (allow all)
- Bedroom: `["2160p"]` (block 4K)

## Source

Generated from AIOStreams v2.30.0 on ElfHosted, May 2026.
