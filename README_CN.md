# Skills Manager (AI 技能管理器) 

> **一款用于管理 AI 编程助手技能（Skills）的统一桌面应用。**
> 无缝组织、同步和共享 **Claude Code、Codex、Opencode** 及其他 AI 工具的技能。

![Version](https://img.shields.io/badge/version-2.2.0-blue) ![Downloads](https://img.shields.io/github/downloads/jiweiyeah/skills-manager/total?color=brightgreen&label=downloads) ![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows%20%7C%20Linux-lightgrey) ![Tech](https://img.shields.io/badge/built%20with-Tauri%202.0%20%2B%20React%2019-orange)

[**官网**](https://skillsmanager.freeourdays.com/zh/?ref=gh) · [English README](./README.md)

## 🤝 赞助商

**[Y-API](https://y-api.bestvirtualgoods.com/i/DNTXWYCU)** 提供统一的大模型 API，可接入 DeepSeek、通义千问 Qwen、智谱 GLM、Kimi、OpenAI 等模型。

- **接入省心**：兼容 OpenAI 接口，可沿用现有 OpenAI SDK，一把 API 密钥即可调用多种模型。
- **按需付费**：按 token 用量计费，无月费、无最低消费。
- **轻松试用**：注册赠送试用额度，无需绑定信用卡即可开始体验。

## 📖 简介

**Skills Manager** 是一款现代化的桌面应用程序，旨在解决 AI 助手的 Skills 配置碎片化的问题。它提供了一个中心化的枢纽，让您不再需要为不同的工具分别管理 Skills 技能。

通过强大的**软链接同步机制（Symlink Synchronization）**，您只需编写一次技能，即可在 32 款受支持的 AI 工具（包括 Claude Code、Codex、Cursor、Gemini CLI、Windsurf、Trae 等）中即时生效，实现"一处编写，多处使用"。

## ✨ 核心功能

- **🎯 统一管理**：在一个安全的位置集中管理所有的 AI Skills。
- **🔄 智能同步**：自动化的软链接管理，确保您的工具始终使用最新版本的技能，无需手动复制文件。
- **🎛️ 灵活控制**：无需删除源文件，即可随时针对特定工具启用或禁用某个 Skill。
- **🛒 技能市场**：应用内浏览、安装和分享社区贡献的 Skills。
- **🌐 AI 翻译**：使用 LLM 将技能名称、描述和内容翻译为您偏好的语言。
- **⌨️ 命令面板**：通过 `⌘K` / `Ctrl+K` 快速导航和执行操作。
- **🌍 双语界面**：完整支持中英文界面。
- **⚡ 极致性能**：基于 **Rust** 和 **Tauri 2.0** 构建，带来轻量级、秒开的极致体验。
- **🛡️ 跨平台支持**：完美支持 macOS、Windows 和 Linux 系统。
- **🔌 多工具支持**：开箱即用支持 32 款 AI 工具（Claude Code、Codex、Cursor、Gemini CLI、Windsurf、Trae、Cline、Augment、Goose 等），并支持自定义扩展。
- **🧩 自定义工具**：支持用户添加自定义工具，配置路径与图标。
- **🎨 现代 UI**：基于 React 19、Tailwind CSS v4 和 Radix UI 打造的 Raycast 风格精美界面。

## 📸 应用截图

<p align="center">
  <img src="https://image.freeourdays.com/sk1.png" alt="应用截图 1" ">
  <img src="https://image.freeourdays.com/sk2.png" alt="应用截图 2" ">
  <img src="https://image.freeourdays.com/sk3.png" alt="应用截图 3" ">
</p>

## 📥 下载安装

可前往 **[官网下载](https://skillsmanager.freeourdays.com/zh/?ref=gh#download)**（会自动识别您的系统与架构），或到 **[Releases 页面](../../releases)** 自行挑选安装包。

| 操作系统 | 安装包类型 |
|----|----------------|
| **macOS** | `.dmg` —— Apple Silicon (`aarch64`) 与 Intel (`x64`) 分别提供 |
| **Windows** | `.msi` / `.exe` |
| **Linux** | `.deb` / `.AppImage` / `.rpm` |

### Homebrew（macOS）

```bash
brew tap jiweiyeah/tap
brew install --cask jiweiyeah/tap/skills-manager
```

cask 会自动匹配你的 CPU 架构，之后 `brew upgrade` 即可保持最新。

请使用完整路径 `jiweiyeah/tap/skills-manager`：Homebrew 官方 cask 仓库里有一个同名但**无关**的 `skills-manager`，官方源优先级更高，直接用短名会装错。

本应用有 ad-hoc 签名但**未经 Apple 公证**，因此 cask 会在安装后移除隔离标记 —— 具体含义与退出方式见 [tap 仓库说明](https://github.com/jiweiyeah/homebrew-tap)。

## 🪟 Windows 使用说明

**不需要管理员权限。** 为某个工具启用 Skill 时，Skills Manager 会按顺序尝试三种方式：

1. **目录软链接（Symlink）**——在开启了开发者模式（或程序恰好以管理员身份运行）时使用。
2. **目录联接（Junction，`mklink /J`）**——普通账户下的常规路径，不需要任何特殊权限。
3. **可追踪副本**——如果联接也被阻止，则复制目录，并写入 `.skills-manager-source.json` 记录来源路径，使副本仍可追踪、仍能在应用内关闭。

三种方式都不要求提权，普通的 Windows 账户就够用。

如果是**检测不到工具**，提权同样没有帮助：需要该工具自己的配置目录确实存在于本机。各工具实际读取的路径见[工具兼容矩阵](https://skillsmanager.freeourdays.com/zh/?ref=gh#tools)，也可以作为自定义工具手动添加。

## 🚀 快速开始

1. **安装**：下载并运行对应平台的安装程序。
2. **设置**：首次启动时，应用会引导您选择或创建技能存储目录。
3. **同步**：应用会自动检测已安装的 AI 工具（如 Claude Code）并建立skills链接。

## ⌨️ 命令行工具 (`skm`)

每个版本都附带一个命令行工具，面向终端优先的工作流：SSH/无头服务器、dotfiles 初始化脚本、快速状态检查。CLI 与桌面应用读写同一份配置和 symlink,可以混用。

从 [Releases 页面](../../releases) 下载 `skm-<target>.tar.gz`(Windows 为 `.zip`),解压后把二进制放入 `PATH` 即可。

```bash
skm init                          # 免 GUI 初始化(写配置、检测工具)
skm adopt [--dry-run] [--yes]     # 把工具目录里已有的技能收编进 hub 并替换为链接
skm list [--tool <id>] [--json]   # 列出技能及各工具链接状态
skm enable <skill> --for <tool>   # 创建 symlink(如 skm enable ab-testing --for claude)
skm disable <skill> --for <tool>  # 移除 symlink
skm doctor [--json]               # 检测已装工具 + 报告同步问题
skm fix --yes                     # 自动修复 doctor 发现的问题
```

`<skill>` 和 `<tool>` 都支持唯一前缀匹配(`claude` 匹配 `claude-code`)。运行 `skm <command> --help` 查看详细用法。桌面 App 是可选的:`skm init` + `skm adopt` 即可构成纯终端工作流(适用于无头服务器)。

安装 CLI(设置 → 命令行工具,或 `skm init`)时,会把配套 skill [`skills-manager-cli`](./skills/skills-manager-cli) 写入 hub,并为当前已检测到的工具启用,这样其他 agent 不必猜参数。里面写了 `--json` 契约、dry-run 与 apply 的区别,以及 `skm` 明确不做的事。

每次版本升级时,这个配套 skill 会自动发布到 [ClawHub](https://clawhub.ai/jiweiyeah/skills/skills-manager-cli),这样从市场拉取技能(而非从 App)的 agent 也总能拿到与当前 `skm` 匹配的说明。发布任务执行 `npm run publish:skill`;它会先查询 ClawHub,仅当本地版本严格高于远端时才上传,所以重复运行是空操作。用 `npm run publish:skill -- --dry-run` 可只校验文件清单和版本闸门而不上传。

## ❗ Linux 常见问题 (Troubleshooting)

如果您在 Linux（特别是虚拟机环境，如 VMware/VirtualBox）运行 `.AppImage` 时遇到**白屏**问题，通常是 WebKitGTK 硬件加速导致的。

请尝试在终端中使用以下命令启动：

```bash
WEBKIT_DISABLE_COMPOSITING_MODE=1 ./Skills-Manager_<version>_amd64.AppImage
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
- [x] 技能市场（Marketplace）– 浏览、安装和分享社区贡献的 Skills。
- [x] 技能内容 AI 翻译。
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

<a href="https://www.star-history.com/?type=date&repos=jiweiyeah%2Fskills-manager">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&theme=dark&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=jiweiyeah/skills-manager&type=date&legend=top-left&sealed_token=maGhqrEwZ51qujlvNPr_FgACgJxDdicoHbnV6FU6K2IQBOo5Cvf_tcX2fdp8o--YQO0Bc240gFYxixCHLDyKy9lrRqTjFMY2rvm77HbLWLY6Q0ETgY89O8oCzsTKjBrL5N9e6kE6RJKp2OQVeBL-v2GRi_VR0CEI2rRKeN3eDnR1ovPjVgXqFakD6LSd" />
 </picture>
</a>

---

*Made with ❤️ for the AI developer community.*
