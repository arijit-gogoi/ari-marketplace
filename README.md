# ari-marketplace

![Claude Code Marketplace](https://img.shields.io/badge/Claude%20Code-Marketplace-7c3aed)
![License](https://img.shields.io/badge/license-MIT-blue)

Arijit's personal [Claude Code](https://claude.ai/code) marketplace — reference and tooling plugins for the frameworks I work in.

## Install

```text
/plugin marketplace add arijit-gogoi/ari-marketplace
```

Then browse and install any of the plugins listed below.

## Plugins

### [remix](https://github.com/arijit-gogoi/remix-plugin)

A comprehensive Remix v3 reference: progressive-disclosure sub-skills, two runnable example apps, and Bun-powered scaffolders. Full topic list in the plugin itself.

```text
/plugin install remix@ari-marketplace
```

Covers: routing, controllers, data-table, data-schema, auth, sessions, cookies, middleware, forms & uploads, file-storage, UI framework, testing, scaffolding, migrations.

### [electrobun](https://github.com/arijit-gogoi/electrobun-plugin)

Complete Electrobun toolkit: skill (scaffold, debug, reason) + embedded MCP server (drive your running app from Claude). Source-grounded against upstream `blackboardsh/electrobun`; live deepwiki + context7 fallback.

```text
/plugin install electrobun@ari-marketplace
```

**Skill — 9 sub-skills**: scaffold, views (BrowserWindow/BrowserView/webview-tag), ipc-rpc (typed RPC + preload bridges), build-dist (bundleCEF, codesign, notarize), updater (BSDIFF + channels), webgpu (GpuWindow, Dawn, Three.js / Babylon adapters), system-integration (Tray, menus, shortcuts, clipboard, dialogs, deep linking), architecture (3-layer model, self-extractor, launcher), zig-main (`mainProcess: "zig"`). Each sub-skill names its Electron analog inline.

**MCP — 16 tools**:
- *Tier 1 (CDP, requires `bundleCEF: true` + remote-debugging-port)*: `electrobun_list_views`, `_eval`, `_navigate`, `_reload`, `_screenshot`, `_dom`, `_console`, `_network`, `_devtools`.
- *Tier 2 (bridge, requires [`electrobun-devtools`](https://www.npmjs.com/package/electrobun-devtools) in your app)*: `electrobun_list_windows`, `_rpc_log`, `_ffi_log`, `_bun_eval` (gated), `_updater_state`, `_app_log`, `_native_log` (Windows).

To use the bridge:
```bash
bun add -d electrobun-devtools
```
```ts
// src/bun/index.ts in your electrobun app
import { devtools } from "electrobun-devtools";
if (process.env.NODE_ENV !== "production") {
  await devtools.start({ port: 9876 });
}
```
Paste the printed token into the plugin's user-config in Claude Code (one-time per project).

## How this works

This repo contains a single [`marketplace.json`](./.claude-plugin/marketplace.json) that points Claude Code at each plugin's source repo. Adding the marketplace gives Claude Code a directory it can search; installing a plugin clones its source repo into your local `~/.claude/plugins/` and activates it.

## Adding more plugins later

As I publish more plugins, they'll be appended to the `plugins[]` array in `marketplace.json` and listed above. The marketplace name (`ari-marketplace`) stays stable.

## Contributing

Each plugin lives in its own repo — file issues and PRs there.

- [`remix-plugin`](https://github.com/arijit-gogoi/remix-plugin/issues)
- [`electrobun-plugin`](https://github.com/arijit-gogoi/electrobun-plugin/issues)

## License

MIT — see [LICENSE](./LICENSE).
