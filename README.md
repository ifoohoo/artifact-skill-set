# artifact-skill-set

AI IDE plugin marketplace index covering Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

**Marketplace version:** `20260729113627`

This repository contains only the marketplace manifests — plugin implementations live in their own repositories.

## Add this marketplace

| Platform | Command |
| --- | --- |
| Claude Code | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| CodeBuddy / WorkBuddy | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| OpenAI Codex | `codex plugin marketplace add ifoohoo/artifact-skill-set` |
| Kimi Code | `/plugins marketplace https://raw.githubusercontent.com/ifoohoo/artifact-skill-set/main/kimi-marketplace.json` |

## Using HTTPS instead of SSH

Claude Code resolves GitHub `owner/repo` shorthand (including plugin entries with `source: "github"` in this marketplace) over SSH by default. If you do not have a GitHub account, SSH key, or SSH agent configured, set the following environment variable **before** launching Claude Code to force HTTPS cloning:

- **macOS / Linux:** `export CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1`
- **Windows PowerShell:** `$env:CLAUDE_CODE_PLUGIN_PREFER_HTTPS='1'`

You can also add this marketplace via an explicit HTTPS URL:

```
/plugin marketplace add https://github.com/ifoohoo/artifact-skill-set.git
```

The environment variable above also causes `owner/repo` shorthand plugin installations to use HTTPS. Public repositories cloned over HTTPS do not require a GitHub account.

> **Tip:** If Git still rewrites HTTPS URLs to SSH, check your local Git `url.*.insteadOf` configuration.

## Plugins

| Plugin | Version | Source | Claude Code | CodeBuddy | Codex | Kimi Code |
| --- | --- | --- | --- | --- | --- | --- |
| artifact-chain-assistant | 0.8.3 | `ifoohoo/artifact-chain-assistant` | ✓ | ✓ | ✓ | — |
| e2e-test | 0.2.0-alpha.3 | `ifoohoo/e2e-test` | ✓ | ✓ | ✓ | — |
| flow-architect | 0.5.4 | `ifoohoo/flow-architect` | ✓ | — | ✓ | — |
| release-skill | 0.2.7 | `ifoohoo/release-skill` | ✓ | ✓ | ✓ | ✓ |

「✓」means the plugin is listed in that platform's manifest; 「—」means it is not. The `platforms` field in the source is the sole explicit distribution switch; CodeBuddy/WorkBuddy's official fallback to `.claude-plugin/plugin.json` does not change distribution status.

After adding the marketplace, install plugins with your platform's plugin manager (e.g. `/plugin install <name>@artifact-skill-set` in Claude Code).

## English Summary

**artifact-skill-set** is the public marketplace index of AI IDE plugin/skill packages maintained by 广州市风荷科技有限公司, targeting Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

- Add the marketplace with the commands above, then install individual plugins through each platform's plugin manager.
- Currently distributed: `artifact-chain-assistant`, `e2e-test`, `flow-architect`, `release-skill`. See the table for per-platform availability.
- Each plugin's version authority lives in its own repository (self-contained manifests and git tags); this index only references them.
- Licensed under MIT — see [LICENSE](LICENSE).
