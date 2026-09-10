# Skills Manager

> **A unified desktop application for managing AI coding assistant skills.**
> Seamlessly organize, sync, and share skills for **Claude Code, Codex, Opencode** and other AI tools.

![Version](https://img.shields.io/badge/version-2.2.0-blue) ![Downloads](https://img.shields.io/github/downloads/jiweiyeah/skills-manager/total?color=brightgreen&label=downloads) ![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey) ![Tech](https://img.shields.io/badge/built%20with-Tauri%202.0%20%2B%20React%2019-orange)

[**Website**](https://skillsmanager.freeourdays.com/?ref=gh) · [中文说明](./README_CN.md)

## 🤝 Sponsors

**[Y-API](https://y-api.bestvirtualgoods.com/i/DNTXWYCU)** provides a unified API for models from DeepSeek, Qwen, GLM, Kimi, OpenAI, and more.

- **Easy integration**: OpenAI-compatible, so you can keep using your existing OpenAI SDK and access multiple models with one API key.
- **Flexible billing**: Pay per token, with no monthly fee or minimum spend.
- **Easy to try**: Signup credits let you get started without a credit card.

## 📖 Introduction

**Skills Manager** is a modern desktop application designed to solve the fragmentation of AI assistant skills configurations. Instead of managing skills and prompts separately for different tools, Skills Manager provides a central hub.

It uses a powerful **symlink synchronization mechanism**, allowing you to write a skill once and instantly use it across 32 supported AI tools including Claude Code, Codex, Cursor, Gemini CLI, Windsurf, Trae, and more.

## ✨ Key Features

- **🎯 Unified Management**: Centralize all your AI skills in one secure location.
- **🔄 Smart Synchronization**: Automatic symlink management ensures your tools always have the latest version of your skills without file duplication.
- **🎛️ Granular Control**: Enable or disable specific skills for individual tools without deleting the original files.
- **🛒 Marketplace**: Browse, install, and share community-contributed skills directly within the app.
- **🌐 AI Translation**: Translate skill names, descriptions, and content into your preferred language using LLM.
- **⌨️ Command Palette**: Quick navigation and actions via `⌘K` / `Ctrl+K`.
- **🌍 Bilingual UI**: Full English and Chinese interface support.
- **⚡ High Performance**: Built with **Rust** and **Tauri 2.0** for a lightweight, blazing-fast experience.
- **🛡️ Cross-Platform**: Native support for macOS, Windows, and Linux.
- **🔌 Multi-Tool Support**: Out-of-the-box support for 32 AI tools (Claude Code, Codex, Cursor, Gemini CLI, Windsurf, Trae, Cline, Augment, Goose, and many more), extensible via custom tools.
- **🧩 Custom Tools**: Add your own tools with custom paths and optional icons.
- **🎨 Modern UI**: Beautiful Raycast-style interface built with React 19, Tailwind CSS v4, and Radix UI.

## 📸 Screenshots

<p align="center">
    <img src="https://image.freeourdays.com/sk1.png" alt="应用截图 1" ">
    <img src="https://image.freeourdays.com/sk2.png" alt="应用截图 2" ">
    <img src="https://image.freeourdays.com/sk3.png" alt="应用截图 3" ">
</p>

## 📥 Download

Get the build for your platform from the **[official website](https://skillsmanager.freeourdays.com/?ref=gh#download)**, which detects your OS and architecture automatically, or pick a file yourself on the **[Releases Page](../../releases)**.

| OS | Installer Type |
|----|----------------|
| **macOS** | `.dmg` — separate builds for Apple Silicon (`aarch64`) and Intel (`x64`) |
| **Windows** | `.msi` / `.exe` |
| **Linux** | `.deb` / `.AppImage` / `.rpm`|

### Homebrew (macOS)

```bash
brew tap jiweiyeah/tap
brew install --cask jiweiyeah/tap/skills-manager
```

The cask picks the right build for your CPU automatically, and `brew upgrade` keeps it current.

Use the full `jiweiyeah/tap/skills-manager` path: Homebrew's official cask repository contains an unrelated cask that happens to share the `skills-manager` token, and the official tap wins on a bare name.

The app is ad-hoc signed but **not notarized by Apple**, so the cask strips the quarantine attribute on install — see the [tap README](https://github.com/jiweiyeah/homebrew-tap) for what that means and how to opt out.

## 🪟 Windows Notes

**You do not need Administrator rights.** When a skill is enabled for a tool, Skills Manager tries three strategies in order:

1. **Directory symlink** — used when Developer Mode is enabled (or when the app happens to run elevated).
2. **Directory junction** (`mklink /J`) — the normal path on a standard account. It needs no special permission.
3. **Tracked copy** — if junctions are blocked as well, the folder is copied and its source path is recorded in `.skills-manager-source.json`, so the copy stays traceable and can still be disabled from the app.

A standard, non-elevated Windows account is enough for all three.

If a tool is **not detected**, elevation will not help either: the tool's own config directory has to exist on this machine. Check the [tool compatibility matrix](https://skillsmanager.freeourdays.com/?ref=gh#tools) for the exact path each tool reads, or add it manually as a custom tool.

## 🚀 Getting Started

1. **Install**: Run the installer for your platform.
2. **Setup**: On first launch, the app will guide you to select your skills storage directory.
3. **Sync**: The app automatically detects installed AI tools (like Claude Code) and links your skills.

## ⌨️ CLI (`skm`)

A companion command-line tool ships with every release for terminal-first workflows: SSH/headless machines, dotfiles setup scripts, and quick status checks. It reads and writes the same config and symlinks as the desktop app, so they can be used interchangeably.

Download `skm-<target>.tar.gz` (`.zip` on Windows) from the [Releases Page](../../releases), extract it, and put the binary on your `PATH`.

```bash
skm init                          # first-run setup without the GUI (writes config, detects tools)
skm adopt [--dry-run] [--yes]     # move skills already in tool dirs into the hub and relink them
skm list [--tool <id>] [--json]   # list skills and their per-tool link status
skm enable <skill> --for <tool>   # create the symlink (e.g. skm enable ab-testing --for claude)
skm disable <skill> --for <tool>  # remove the symlink
skm doctor [--json]               # detect installed tools + report sync issues
skm fix --yes                     # repair sync issues found by doctor
```

Both `<skill>` and `<tool>` accept a unique prefix (`claude` matches `claude-code`). Run `skm <command> --help` for details. The GUI is optional: `skm init` + `skm adopt` give a fully terminal-only workflow (e.g. on headless servers).

Installing the CLI (Settings → Command Line Tool, or `skm init`) also copies the [`skills-manager-cli`](./skills/skills-manager-cli) companion skill into the hub and enables it for every currently detected tool, so other agents can drive `skm` without guessing flags. It covers `--json` contracts, dry-run vs apply, and which commands `skm` does *not* implement.

The same companion skill is published to [ClawHub](https://clawhub.ai/jiweiyeah/skills/skills-manager-cli) automatically on every version bump, so agents that pull skills from the marketplace instead of the app always get instructions matching the current `skm`. The release job runs `npm run publish:skill`; it queries ClawHub first and only uploads when the local version is strictly newer, so re-runs are no-ops. Use `npm run publish:skill -- --dry-run` to validate the file list and version gate without uploading.

## ❗ Linux Troubleshooting

If you encounter a **blank white screen** when launching the `.AppImage` on Linux (especially in virtual machines like VMware/VirtualBox), it is likely a WebKitGTK hardware acceleration issue.

Please run the application from the terminal with the following command:

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 ./Skills-Manager_<version>_amd64.AppImage
```

## 🛠️ Technology Stack

Designed for developers who care about performance and stability:

- **Core**: [Tauri 2.0](https://tauri.app/) (Rust)
- **Frontend**: [React 19](https://react.dev/) + TypeScript
- **Styling**: [Tailwind CSS v4](https://tailwindcss.com/)
- **UI Components**: [Radix UI](https://www.radix-ui.com/)
- **Editor**: [Monaco Editor](https://microsoft.github.io/monaco-editor/)

## 📅 Roadmap

We are actively working on making Skills Manager better. Here is what we are planning:

- [x] Core features (e.g., soft link synchronization, multi-tool support).
- [x] Marketplace – Browse, install, and share community-contributed skills.
- [x] AI translation for skill content.
- [ ] Plugin system to support more AI tool extensions.
- [ ] Integrated AI chat interface for testing Skills directly within the application.

## 🤝 Contributing & Feedback

We welcome all forms of contribution!

- **Found a bug?** Please submit an issue on our [Issues](../../issues) page.
- **Have a feature request?** We'd love to hear your ideas! Feel free to open an issue to discuss new features.

## 💝 Support

If this project helps you, feel free to support via QR code.

| WeChat Support QR | Alipay Support QR |
|---|---|
| <img src="https://image.freeourdays.com/2024/WechatIMG276.jpg" alt="WeChat Support QR" height="300" /> | <img src="https://image.freeourdays.com/zfb.jpg" alt="Alipay Support QR" height="300" /> |

Or support via Ko-fi: [ko-fi.com/yeheboo](https://ko-fi.com/yeheboo)

## 📈 Star History

<a href="https://www.star-history.com/?type=date&repos=jiweiyeah%2Fskills-manager">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&theme=dark&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
 </picture>
</a>

---

*Made with ❤️ for the AI developer community.*
