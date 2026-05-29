# 一键 Skill 同步流程

本文档提出一个较小、容易落地的产品契约，用于在 Claude Code、Codex 等 AI 编程助手之间同步用户安装的 Skills。等应用源码开放后，可以按这个契约继续补实现代码。

## 目标

- 用户可以一键把某个 Skill 从一个助手同步到另一个助手。
- 默认优先展示用户自己安装或编辑的 Skills，同时保留内置/系统 Skills，但排在后面。
- 如果已有软链接/共享存储机制，尽量避免复制多份 Skill 文件夹。
- 保留每个工具的启用状态，让用户仍然可以针对某个助手单独禁用 Skill。

## 默认路径

Skills Manager 可以继续把中心存储作为唯一真实来源，并链接到检测到的工具目录：

| 工具 | 默认 Skill 目录 |
| --- | --- |
| Claude Code | `~/.claude/skills` |
| Codex | `~/.codex/skills` |

对于非默认安装位置，界面仍可允许用户自定义工具路径。

## 建议数据结构

```json
{
  "id": "literature-review",
  "name": "literature-review",
  "source": "user",
  "storePath": "~/.skills-manager/skills/literature-review",
  "targets": {
    "claude": { "enabled": true, "path": "~/.claude/skills/literature-review" },
    "codex": { "enabled": true, "path": "~/.codex/skills/literature-review" }
  }
}
```

`source` 建议包含以下取值：

- `user`：用户导入、安装或编辑的 Skill。
- `community`：从社区目录安装的 Skill。
- `system`：由某个助手自带或运行时管理的 Skill。

## 默认排序

Skills 列表建议按以下顺序排序：

1. `user`
2. `community`
3. `system`

同一组内，如果有 `updatedAt`，按最近更新时间倒序排列；否则按名称排序。这样可以让个人常用 Skills 更容易找到，同时不隐藏内置 Skills。

## 一键同步行为

如果某个 Skill 已存在于 Claude Code，但 Codex 中缺失，显示 `同步到 Codex`。如果已存在于 Codex，但 Claude Code 中缺失，显示 `同步到 Claude`。如果多个已启用工具都缺失，显示 `同步到全部`。

执行同步时建议：

1. 确认 Skill 已存在于中心存储。
2. 为选中的目标工具创建或刷新软链接。
3. 如果出现权限错误，显示具体失败的目标路径。
4. 重新扫描目标目录，确认链接存在后再标记为已同步。

## 冲突处理

如果目标目录已经存在同名但内容不同的 Skill 文件夹，应显示冲突状态，并提供：

- 保留目标版本
- 用中心版本替换
- 将目标版本作为独立 Skill 导入

不建议在没有用户确认的情况下自动覆盖。

