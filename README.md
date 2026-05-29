# Skills Manager

> **A unified desktop application for managing AI coding assistant skills.**
> Seamlessly organize, sync, and share skills for **Claude Code, Codex, Opencode** and other AI tools.

![Version](https://img.shields.io/badge/version-2.0.3-blue) ![Downloads](https://img.shields.io/github/downloads/jiweiyeah/skills-manager/total?color=brightgreen&label=downloads) ![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey) ![Tech](https://img.shields.io/badge/built%20with-Tauri%202.0%20%2B%20React%2019-orange)

[中文说明](./README_CN.md)

## 📖 Introduction

**Skills Manager** is a modern desktop application designed to solve the fragmentation of AI assistant skills configurations. Instead of managing skills and prompts separately for different tools, Skills Manager provides a central hub.

It uses a powerful **symlink synchronization mechanism**, allowing you to write a skill once and instantly use it across supported AI tools like Claude Code, Codex, Opencode.

## ✨ Key Features

- **🎯 Unified Management**: Centralize all your AI skills in one secure location.
- **🔄 Smart Synchronization**: Automatic symlink management ensures your tools always have the latest version of your skills without file duplication.
- **↔️ Cross-Tool Sync Workflow**: See the proposed [one-click sync workflow](./docs/SYNC_WORKFLOW.md) for copying or linking skills between Claude Code, Codex, and other assistants.
- **🎛️ Granular Control**: Enable or disable specific skills for individual tools without deleting the original files.
- **⚡ High Performance**: Built with **Rust** and **Tauri 2.0** for a lightweight, blazing-fast experience.
- **🛡️ Cross-Platform**: Native support for macOS, Windows, and Linux.
- **🔌 Multi-Tool Support**: Out-of-the-box support for **Claude Code, Codex, Opencode** and extensible to others.
- **🧩 Custom Tools**: Add your own tools with custom paths and optional icons.
- **🎨 Modern UI**: Beautiful interface built with React 19, Tailwind CSS v4, and Radix UI.

## 📸 Screenshots

<p align="center">
  <img src="https://image.freeourdays.com/141.png" alt="应用截图 1" ">
  <img src="https://image.freeourdays.com/142.png" alt="应用截图 2" ">
  <img src="https://image.freeourdays.com/143.png" alt="应用截图 3" ">
  <img src="https://image.freeourdays.com/144.png" alt="应用截图 4" ">
  <img src="https://image.freeourdays.com/145.png" alt="应用截图 5" ">
</p>

## 📥 Download

Download the latest installer for your operating system from the **[Releases Page](../../releases)**.

| OS | Installer Type |
|----|----------------|
| **macOS** | `.dmg` (Universal) |
| **Windows** | `.msi` / `.exe` |
| **Linux** | `.deb` / `.AppImage` / `.rpm`|

## ⚠️ Windows Important Note

If you encounter permission issues when syncing skills (symbolic link creation errors) or detection issues, please try running the application as **Administrator**. This is often required on Windows to create symbolic links unless Developer Mode is enabled.

## 🚀 Getting Started

1. **Install**: Run the installer for your platform.
2. **Setup**: On first launch, the app will guide you to select your skills storage directory.
3. **Sync**: The app automatically detects installed AI tools (like Claude Code) and links your skills.

## ❗ Linux Troubleshooting

If you encounter a **blank white screen** when launching the `.AppImage` on Linux (especially in virtual machines like VMware/VirtualBox), it is likely a WebKitGTK hardware acceleration issue.

Please run the application from the terminal with the following command:

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 ./Skills-Manager_1.0.1_amd64.AppImage
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
- [ ] One-click cross-tool sync for user-installed skills, with built-in/system skills sorted after personal skills.
- [ ] Community Hub – Share and download community-contributed Skills, etc.
- [ ] Cloud synchronization, allowing one-click migration of existing Skills and more when changing devices.
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

[![Star History Chart](https://api.star-history.com/svg?repos=jiweiyeah/skills-manager&type=Date)](https://star-history.com/#jiweiyeah/skills-manager&Date)

---

*Made with ❤️ for the AI developer community.*
