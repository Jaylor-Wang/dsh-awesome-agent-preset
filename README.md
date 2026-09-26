# dsh-awesome-agent-preset

English | [中文](README.zh.md)

Ultra-lean daily coding agent preset for [DeepSeek Harness (`dsh`)](https://github.com/deepseek-ai/deepseek-harness).

## Highlights

- **Lean & Responsive**: Removes heavy orchestration layers (no `present` deliverables, goals, complex plan modes, sub-agents, or TODO trackers). Focuses purely on fast, direct coding cycles.
- **Essential Tooling**: Retains core tools needed for day-to-day software development:
  - File reading, editing, and fast directory scanning (`fs`, `fs-search`)
  - Full-featured Bash execution (`tool-bash`)
  - Background asynchronous task management (`tool-jobs`)
  - External skill packs support (`skill-filesystem`, `tool-skill`)
  - Compact history pruning & memory protection (`compaction`, `tool-result-pruner`)
- **Direct Execution**: Persona instructed to favor direct tool execution over excessive coordination, saving tokens and speeding up turnaround time.

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
