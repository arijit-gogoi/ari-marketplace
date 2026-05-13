# ari-marketplace

Claude Code marketplace listing for Arijit's plugins. Published at `arijit-gogoi/ari-marketplace`.

## What's here

```
.claude-plugin/marketplace.json   ← single source of truth
README.md                          ← public listing
```

## Marketplace.json schema (verified against real Anthropic marketplaces)

```json
{
  "$schema": "https://anthropic.com/claude-code/marketplace.schema.json",
  "name":    "ari-marketplace",
  "version": "0.1.0",
  "description": "...",
  "owner":   { "name": "...", "url": "..." },
  "plugins": [ /* one entry per plugin */ ]
}
```

### Per-plugin entry — valid fields

```json
{
  "name":        "<plugin-name>",
  "description": "...",
  "author":      { "name": "..." },
  "category":    "development",                          // or productivity / security / design
  "source": {
    "source": "url",                                      // or "git-subdir"
    "url":    "https://github.com/<owner>/<repo>.git",
    "ref":    "vX.Y.Z"                                    // pin to a tag, not a branch
  },
  "homepage":    "https://github.com/<owner>/<repo>"
}
```

**Fields NOT used by real marketplaces** (don't add): `keywords`, `license`, `version` per-plugin.

**`source.source` values seen in the wild**: `url` (whole repo), `git-subdir` (subdir of a repo), path string like `"./plugins/foo"` (entry in same repo). **`github` is NOT a real value** — don't fabricate.

## Bumping a plugin

```pwsh
# Edit .claude-plugin/marketplace.json — change the "ref" for the plugin entry
git commit -am "bump <plugin> to vX.Y.Z"
git push
```

Users pick it up with `/plugin marketplace update` in Claude Code.

## Adding a new plugin

1. Create the plugin in its own GitHub repo (mirror `remix-plugin` layout).
2. Tag a `v0.1.0` release on that repo.
3. Append to the `plugins[]` array in `marketplace.json`.
4. Add a section in `README.md` listing the plugin.
5. `git commit -am "add <plugin-name> plugin"` and push.

## Current plugins

- **remix** — Comprehensive Remix v3 reference. Source: `arijit-gogoi/remix-plugin`. Currently `v0.2.0`.
