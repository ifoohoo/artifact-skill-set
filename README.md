# artifact-skill-set

AI IDE plugin marketplace index covering Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

This repository contains only the marketplace manifests — plugin implementations live in their own repositories.

## Add this marketplace

| Platform | Command |
| --- | --- |
| Claude Code | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| CodeBuddy / WorkBuddy | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| OpenAI Codex | `codex plugin marketplace add ifoohoo/artifact-skill-set` |
| Kimi Code | `/plugins marketplace https://raw.githubusercontent.com/ifoohoo/artifact-skill-set/main/kimi-marketplace.json` |

## Plugins

| Plugin | Version | Source | Claude Code | CodeBuddy | Codex | Kimi Code |
| --- | --- | --- | --- | --- | --- | --- |
| e2e-test | 0.2.0-alpha.1 | `ifoohoo/e2e-test` | ✓ | ✓ | ✓ | — |
| flow-architect | 0.5.1 | `ifoohoo/flow-architect` | ✓ | — | ✓ | — |
| release-skill | 0.2.3 | `ifoohoo/release-skill` | ✓ | ✓ | ✓ | ✓ |

「✓」means the plugin is listed in that platform's manifest; 「—」means it is not. The `platforms` field in the source is the sole explicit distribution switch; CodeBuddy/WorkBuddy's official fallback to `.claude-plugin/plugin.json` does not change distribution status.

After adding the marketplace, install plugins with your platform's plugin manager (e.g. `/plugin install <name>@artifact-skill-set` in Claude Code).

## English Summary

**artifact-skill-set** is the public marketplace index of AI IDE plugin/skill packages maintained by 广州市风荷科技有限公司, targeting Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

- Add the marketplace with the commands above, then install individual plugins through each platform's plugin manager.
- Currently distributed: `e2e-test`, `flow-architect`, `release-skill`. See the table for per-platform availability.
- Each plugin's version authority lives in its own repository (self-contained manifests and git tags); this index only references them.
- Licensed under MIT — see [LICENSE](LICENSE).
