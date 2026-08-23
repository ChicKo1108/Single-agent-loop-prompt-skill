# Loop Prompt Skill

[![Agent Skills Standard](https://img.shields.io/badge/Agent%20Skills-Standard-6B21A8)](https://agentskills.io)
[![skills.sh Compatible](https://img.shields.io/badge/skills.sh-Compatible-0284C7)](https://skills.sh)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

用于创建可持续执行的单智能体 Loop 提示词。

它会先逐步询问任务目标、成功标准、可执行范围、重试规则和停止条件，再生成一份可直接使用的提示词，让智能体按“观察 → 判断 → 最小行动 → 验证 → 记录”的闭环持续推进任务。

适合故障排查、持续优化、自动化流程和需要明确验收条件的复杂任务。

## 安装

```bash
npx skills add https://github.com/ChicKo1108/Single-agent-loop-prompt-skill --skill single-agent-loop-prompt
```

> 安装命令中请使用纯 URL，不要使用 Markdown 格式的 `[名称](URL)`。

## 使用

安装后，在 Codex 中输入：

```text
使用 $single-agent-loop-prompt 为我的任务生成 Loop 提示词。
```

Skill 会先进行目标澄清，再输出可复制使用的 Loop Prompt。

## 内容

- `SKILL.md`：Skill 主说明。
- `references/grill-protocol.md`：目标澄清与追问规则。
- `references/loop-prompt-template.md`：Loop Prompt 模板。
- `references/run-recording.md`：执行记录与交付规范。
