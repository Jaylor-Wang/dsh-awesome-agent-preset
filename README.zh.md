# dsh-awesome-agent-preset

[English](README.md) | 中文

[![npm version](https://img.shields.io/npm/v/dsh-awesome-agent-preset.svg?color=blue)](https://www.npmjs.com/package/dsh-awesome-agent-preset)
[![license](https://img.shields.io/npm/l/dsh-awesome-agent-preset.svg)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/Jaylor-Wang/dsh-awesome-agent-preset.svg)](https://github.com/Jaylor-Wang/dsh-awesome-agent-preset/releases)
[![DeepSeek Harness](https://img.shields.io/badge/DeepSeek%20Harness-Preset-orange.svg)](https://github.com/deepseek-ai/deepseek-harness)

面向 [DeepSeek Harness (`dsh`)](https://github.com/deepseek-ai/deepseek-harness) 的极简日常编码 Agent 预设插件。

## 特性亮点

- **极致精简与高响应度**：移除笨重的编排机制与冗余组件（不含文件交付工具 `present` / 目标 / 复杂计划模式 / 子代理 / TODO 管理），回归纯粹、高效的直接编码循环。
- **必备工具链完备**：
  - 文件读取、编辑与文件树快速检索（`fs`、`fs-search`）
  - 全功能 Bash 终端命令执行（`tool-bash`）
  - 后台异步长任务支持（`tool-jobs`）
  - 外部技能包扩展支持（`skill-filesystem`、`tool-skill`）
  - 上下文按需压缩与记忆保护（`compaction`、`/compact`）
- **文件与搜索上下文深度调优（对齐 AGENTS.md 规范）**：
  - `tool-fs-search`：严格限制 `glob` ≤ 50 条、`grep` ≤ 50 条匹配（单行 ≤ 500 字节防雪崩），超量自动溢出落盘；
  - `tool-fs`：`readLimit: 800`（单行 ≤ 600 字符、单次 ≤ 120KB），保障连贯内聚单元完整读取的同时，杜绝超大文件挤爆上下文。
- **Bash 执行与长任务弹性调优**：
  - `tool-bash`：默认开启后台任务支持与 `promoteOnTimeout: true`（超时前台命令自动平滑提升为后台 Job，杜绝任务中断与前台假死卡顿）；
  - 推荐结合全局执行器 `bash-sandbox` 调优 `maxOutputBytes: 32768`（单次流由 64KB 收敛至 32KB，超量自动溢出落盘 Spill），双重规避巨量日志消耗上下文 Token。
- **自治与并发强化 Persona**：内置 Persona 深度优化，约束模型“重行动轻推测”，主动利用工具并发能力（`fs`、`bash`、`skills`），消除行动前铺垫废话，精准交付高信噪比成果。

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
