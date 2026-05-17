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

Complete Electrobun skill: scaffold, debug, and reason about Electrobun apps (TypeScript + Bun + Zig + native bindings). Source-grounded against upstream `blackboardsh/electrobun`; live deepwiki + context7 fallback.

```text
/plugin install electrobun@ari-marketplace
```

Covers: 9 sub-skills — scaffold, views (BrowserWindow/BrowserView/webview-tag), ipc-rpc (typed RPC + preload bridges), build-dist (bundleCEF, codesign, notarize), updater (BSDIFF + channels), webgpu (GpuWindow, Dawn, Three.js / Babylon adapters), system-integration (Tray, menus, shortcuts, clipboard, dialogs, deep linking), architecture (3-layer model, self-extractor, launcher), zig-main (`mainProcess: "zig"`). Each sub-skill names its Electron analog inline.

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
