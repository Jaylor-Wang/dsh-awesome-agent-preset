# dsh-awesome-agent-preset

[English](README.md) | 中文

面向 [DeepSeek Harness (`dsh`)](https://github.com/deepseek-ai/deepseek-harness) 的极简日常编码 Agent 预设插件。

## 特性亮点

- **极致精简与高响应度**：移除笨重的编排机制与冗余组件（不含交付物 `present` / 目标 / 复杂计划模式 / 子代理 / TODO 管理），回归纯粹、高效的直接编码循环。
- **必备工具链完备**：
  - 文件读取、编辑与文件树快速检索（`fs`、`fs-search`）
  - 全功能 Bash 终端命令执行（`tool-bash`）
  - 后台异步长任务支持（`tool-jobs`）
  - 外部技能包扩展支持（`skill-filesystem`、`tool-skill`）
  - 自动化历史修剪与上下文压缩保护（`compaction`、`tool-result-pruner`）
- **直接工具驱动**：内置 Persona 提示词约束模型优先直接使用工具推进任务，避免多余的委派与流程空转，大幅节省 Token 并缩短响应等待时间。

## 安装方式

在 DeepSeek Harness 环境中运行：

```bash
dsh plugin --profile web add dsh-awesome-agent-preset
# 或直接通过 GitHub 仓库安装
dsh plugin --profile web add https://github.com/Jaylor-Wang/dsh-awesome-agent-preset
```

或克隆到本地后通过软链接引入：

```bash
git clone https://github.com/Jaylor-Wang/dsh-awesome-agent-preset.git
```

## 使用说明

1. 启动或重启 DeepSeek Harness（`dsh web`）；
2. 在输入框上方的 Agent 预设选择器中切换选中 **`awesome-agent`**；
3. 即可畅享极速日常编码体验。

## 开源协议

[MIT](LICENSE)
