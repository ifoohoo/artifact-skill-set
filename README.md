# artifact-skill-set

Artifact Skill Set is a plugin marketplace index for AI coding assistants, covering four platforms: **Claude Code**, **CodeBuddy/WorkBuddy**, **OpenAI Codex**, and **Kimi Code**.

This repository contains only the marketplace manifests — plugin implementations live in their own repositories.

## Add this marketplace

| Platform | Command |
| --- | --- |
| Claude Code | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| CodeBuddy / WorkBuddy | `codebuddy plugin marketplace add ifoohoo/artifact-skill-set` |
| OpenAI Codex | `codex plugin marketplace add ifoohoo/artifact-skill-set` |
| Kimi Code | `/plugins marketplace https://raw.githubusercontent.com/ifoohoo/artifact-skill-set/main/kimi-marketplace.json` |

## Plugins

| Plugin | Version | Source | Claude Code | CodeBuddy | Codex | Kimi Code |
| --- | --- | --- | --- | --- | --- | --- |
| release-skill | 0.2.1 | `ifoohoo/release-skill` | ✓ | ✓ | ✓ | ✓ |
| flow-architect | 0.5.1 | `ifoohoo/flow-architect` | ✓ | ✓ | ✓ | — |

「✓」means the plugin is listed in that platform's manifest; 「—」means it is not. CodeBuddy/WorkBuddy officially fall back to `.claude-plugin/plugin.json` when a plugin root has no `.codebuddy-plugin/plugin.json`, so a plugin may appear in the CodeBuddy manifest via its Claude manifest.

After adding the marketplace, install plugins with your platform's plugin manager (e.g. `/plugin install <name>@artifact-skill-set` in Claude Code).

## English Summary

**artifact-skill-set** is the public marketplace index of AI IDE plugin/skill packages maintained by 广州市风荷科技有限公司, targeting Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

- Add the marketplace with the commands above, then install individual plugins through each platform's plugin manager.
- Currently distributed: `release-skill`, `flow-architect`. See the table for per-platform availability.
- Each plugin's version authority lives in its own repository (self-contained manifests and git tags); this index only references them.
- Licensed under MIT — see [LICENSE](LICENSE).
