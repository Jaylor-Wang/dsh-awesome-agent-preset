# dsh-awesome-agent-preset

English | [中文](README.zh.md)

[![npm version](https://img.shields.io/npm/v/dsh-awesome-agent-preset.svg?color=blue)](https://www.npmjs.com/package/dsh-awesome-agent-preset)
[![license](https://img.shields.io/npm/l/dsh-awesome-agent-preset.svg)](LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/Jaylor-Wang/dsh-awesome-agent-preset.svg)](https://github.com/Jaylor-Wang/dsh-awesome-agent-preset/releases)
[![DeepSeek Harness](https://img.shields.io/badge/DeepSeek%20Harness-Preset-orange.svg)](https://github.com/deepseek-ai/deepseek-harness)

Ultra-lean daily coding agent preset for [DeepSeek Harness (`dsh`)](https://github.com/deepseek-ai/deepseek-harness).

## Highlights

- **Lean & Responsive**: Removes heavy orchestration layers (no file delivery tool (`present`), goals, complex plan modes, sub-agents, or TODO trackers). Focuses purely on fast, direct coding cycles.
- **Essential Tooling**: Retains core tools needed for day-to-day software development:
  - File reading, editing, and fast directory scanning (`fs`, `fs-search`)
  - Full-featured Bash execution (`tool-bash`)
  - Background asynchronous task management (`tool-jobs`)
  - External skill packs support (`skill-filesystem`, `tool-skill`)
  - On-demand context compaction & memory protection (`compaction`, `/compact`)
- **Tuned FS & Search Efficiency (Aligned with AGENTS.md)**:
  - `tool-fs-search`: caps `glob` results to ≤ 50 entries and `grep` matches to ≤ 50 (preview ≤ 500 bytes/line), preventing context flooding and utilizing spill files when exceeded.
  - `tool-fs`: `readLimit: 800` (max 600 chars/line, max 120KB), ensuring cohesive code units are read in full while preventing massive monolithic files from blowing up token windows.
- **Resilient Bash & Long-running Job Execution**:
  - `tool-bash`: enables background job support and `promoteOnTimeout: true` (smoothly promotes timed-out foreground commands into background jobs, preventing task termination and UI hangs).
  - Recommended pairing with executor `bash-sandbox` tuning (`maxOutputBytes: 32768`), reducing stream memory buffer from 64KB to 32KB with automatic spill retention to safeguard context budgets.
- **Master Persona with Operation Boundary Partitioning**: Instructs the model as a master autonomous engineer, biasing toward direct concurrent action for coding tasks while strictly isolating irreversible operations (npm publish: strictly conservative, never mutate versions, and immune to transient registry validation lag/404s without retrying in-flight publishes), ensuring both blistering local speed and rock-solid deployment safety.

## Installation

Run in your DeepSeek Harness environment:

```bash
dsh plugin --profile web add dsh-awesome-agent-preset
# or via GitHub repository
dsh plugin --profile web add https://github.com/Jaylor-Wang/dsh-awesome-agent-preset
```

Or clone locally and link into your DSH profile:

```bash
git clone https://github.com/Jaylor-Wang/dsh-awesome-agent-preset.git
```

## Usage

1. Restart or launch DeepSeek Harness (`dsh web`).
2. In the preset dropdown list above the prompt input bar, select **`awesome-agent`**.
3. Start coding!

## License

[MIT](LICENSE)
