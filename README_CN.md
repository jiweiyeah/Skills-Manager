# Skills Manager (AI 技能管理器) 

> **一款用于管理 AI 编程助手技能（Skills）的统一桌面应用。**
> 无缝组织、同步和共享 **Claude Code、Codex、Opencode** 及其他 AI 工具的技能。

![Version](https://img.shields.io/badge/version-1.1.3-blue) ![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey) ![Tech](https://img.shields.io/badge/built%20with-Tauri%202.0%20%2B%20React%2019-orange)

[English README](./README.md)

## 📖 简介

**Skills Manager** 是一款现代化的桌面应用程序，旨在解决 AI 助手的 Skills 配置碎片化的问题。它提供了一个中心化的枢纽，让您不再需要为不同的工具分别管理 Skills 技能。

通过强大的**软链接同步机制（Symlink Synchronization）**，您只需编写一次技能，即可在 Claude Code、Codex、Opencode 等支持的 AI 工具中即时生效，实现"一处编写，多处使用"。

## ✨ 核心功能

- **🎯 统一管理**：在一个安全的位置集中管理所有的 AI Skills。
- **🔄 智能同步**：自动化的软链接管理，确保您的工具始终使用最新版本的技能，无需手动复制文件。
- **🎛️ 灵活控制**：无需删除源文件，即可随时针对特定工具启用或禁用某个 Skill。
- **⚡ 极致性能**：基于 **Rust** 和 **Tauri 2.0** 构建，带来轻量级、秒开的极致体验。
- **🛡️ 跨平台支持**：完美支持 macOS、Windows 和 Linux 系统。
- **🔌 多工具支持**：开箱即用支持 **Claude Code、Codex、Opencode**等常用工具，并具备良好的扩展性。
- **🧩 自定义工具**：支持用户添加自定义工具，配置路径与图标。
- **🎨 现代 UI**：基于 React 19、Tailwind CSS v4 和 Radix UI 打造的精美界面。

## 📸 应用截图

<p align="center">
  <img src="https://image.freeourdays.com/141.png" alt="应用截图 1" ">
  <img src="https://image.freeourdays.com/142.png" alt="应用截图 2" ">
  <img src="https://image.freeourdays.com/143.png" alt="应用截图 3" ">
  <img src="https://image.freeourdays.com/144.png" alt="应用截图 4" ">
  <img src="https://image.freeourdays.com/145.png" alt="应用截图 5" ">
</p>

## 📥 下载安装

请前往 **[Releases 页面](../../releases)** 下载适用于您系统的最新安装包。

| 操作系统 | 安装包类型 |
|----|----------------|
| **macOS** | `.dmg` (通用架构) |
| **Windows** | `.msi` / `.exe` |
| **Linux** | `.deb` / `.AppImage` / `.rpm` |

## ⚠️ Windows 用户重要提示

如果您在同步 Skills 时遇到权限问题（软链接创建失败）或检测不到工具，请尝试以 **管理员身份 (Run as Administrator)** 运行本程序。Windows 系统默认需要管理员权限才能创建软链接，除非您开启了开发者模式。

## 🚀 快速开始

1. **安装**：下载并运行对应平台的安装程序。
2. **设置**：首次启动时，应用会引导您选择或创建技能存储目录。
3. **同步**：应用会自动检测已安装的 AI 工具（如 Claude Code）并建立skills链接。

## ❗ Linux 常见问题 (Troubleshooting)

如果您在 Linux（特别是虚拟机环境，如 VMware/VirtualBox）运行 `.AppImage` 时遇到**白屏**问题，通常是 WebKitGTK 硬件加速导致的。

请尝试在终端中使用以下命令启动：

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 ./Skills-Manager_1.0.1_amd64.AppImage
```

## 🛠️ 技术栈

专为追求性能和稳定性的开发者打造：

- **核心架构**: [Tauri 2.0](https://tauri.app/) (Rust)
- **前端框架**: [React 19](https://react.dev/) + TypeScript
- **样式方案**: [Tailwind CSS v4](https://tailwindcss.com/)
- **UI 组件**: [Radix UI](https://www.radix-ui.com/)
- **内置编辑器**: [Monaco Editor](https://microsoft.github.io/monaco-editor/)

## 📅 路线图 (Roadmap)

我们正在持续改进 Skills Manager，以下是我们未来的规划：

- [x] 核心功能（软链接同步、多工具支持等）。
- [ ] 社区中心（Community Hub）– 分享和下载社区贡献的 Skills 等。
- [ ] 云端同步，更换设备后也可一键迁移原有的 Skills 等。
- [ ] 插件系统，支持更多 AI 工具扩展。
- [ ] 集成 AI 对话界面，直接在应用内测试 Skills。

## 🤝 反馈与支持

我们欢迎任何形式的贡献和反馈！

- **发现 Bug？** 请在我们的 [Issues](../../issues) 页面提交。
- **有新功能建议？** 欢迎提交 Issue 告诉我们您的想法，我们非常乐意听取社区的声音。

## 💝 赞赏

如果这个项目对你有帮助，欢迎扫码赞赏支持。

| 微信赞赏码 | 支付宝赞赏码 |
|---|---|
| <img src="https://image.freeourdays.com/2024/WechatIMG276.jpg" alt="微信赞赏码" height="300" /> | <img src="https://image.freeourdays.com/zfb.jpg" alt="支付宝赞赏码" height="300" /> |

或通过 Ko-fi 支持：[ko-fi.com/yeheboo](https://ko-fi.com/yeheboo)

## 📈 Star 趋势图

[![Star History Chart](https://api.star-history.com/svg?repos=jiweiyeah/skills-manager&type=Date)](https://star-history.com/#jiweiyeah/skills-manager&Date)

---

*Made with ❤️ for the AI developer community.*
