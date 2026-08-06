# artifact-skill-set

[简体中文](README.zh-CN.md)

Artifact workflow plugin marketplace for Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

**Marketplace version:** `20260806112320`

**Author:** 广州市风荷科技有限公司

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

## Download acceleration for users in mainland China

If direct GitHub access is unavailable, you may configure Git to use a third-party download proxy for this organization's public repositories. The following example uses `ghfast.top`:

```bash
git config --global \
  url."https://ghfast.top/https://github.com/ifoohoo/".insteadOf \
  "https://github.com/ifoohoo/"
```

The rewrite is local to your Git configuration. Marketplace and plugin manifests continue to reference the canonical GitHub repositories.

> **Source and security:** Repositories maintained by `ifoohoo` on GitHub are the source of truth. `ghfast.top` is a third-party proxy, not an official mirror. Use it only for read-only access to public repositories. Never send GitHub tokens, passwords, or private-repository traffic through the proxy. Stop the installation if the pinned Git tag and full commit SHA cannot be retrieved.

Inspect active URL rewrites:

```bash
git config --global --get-regexp '^url\..*\.insteadof$'
```

Remove the rewrite when it is no longer needed:

```bash
git config --global --unset-all \
  url."https://ghfast.top/https://github.com/ifoohoo/".insteadOf
```

## Plugins

| Plugin | Version | Source | Claude Code | CodeBuddy | Codex | Kimi Code |
| --- | --- | --- | --- | --- | --- | --- |
| artifact-chain-assistant | 0.9.0 | `ifoohoo/artifact-chain-assistant` | ✓ | ✓ | ✓ | ✓ |
| e2e-test | 0.2.1 | `ifoohoo/e2e-test` | ✓ | ✓ | ✓ | — |
| flow-architect | 0.5.4 | `ifoohoo/flow-architect` | ✓ | — | ✓ | — |

"✓" means the plugin is listed in that platform's manifest; "—" means it is not. The `platforms` field in the source is the sole explicit distribution switch; CodeBuddy/WorkBuddy's official fallback to `.claude-plugin/plugin.json` does not change distribution status.

After adding the marketplace, install plugins with your platform's plugin manager (e.g. `/plugin install <name>@artifact-skill-set` in Claude Code).

## Foundation components

The following published npm packages are part of the Artifact product line, but they are not marketplace plugins and therefore never appear in the platform manifests. Install them directly in a target project when needed. The related-plugin column names workflow integration, not a wrapper for the listed npm release; each plugin declares its own compatible dependency versions.

| Foundation component | Published version | npm package | Git tag | Commit SHA | Related plugin | Role |
| --- | --- | --- | --- | --- | --- | --- |
| `agent-method-registry` | `0.2.2` | [agent-method-registry@0.2.2](https://www.npmjs.com/package/agent-method-registry/v/0.2.2) | [`agent-method-registry-v0.2.2`](https://github.com/ifoohoo/agent-method-registry/tree/agent-method-registry-v0.2.2) | [`2d15ae574e122c5dfabf245680b5a8de628d27e4`](https://github.com/ifoohoo/agent-method-registry/commit/2d15ae574e122c5dfabf245680b5a8de628d27e4) | `artifact-chain-assistant` | Deterministic method catalog resolution, provider verification, binding, and diagnostics library and CLI. Use this npm package directly for standalone registry work. artifact-chain-assistant has Registry-backed routing, but governs its own dependency version independently of this listing. |
| `artifact-graph` | `0.9.0` | [artifact-graph@0.9.0](https://www.npmjs.com/package/artifact-graph/v/0.9.0) | [`artifact-graph-v0.9.0`](https://github.com/ifoohoo/artifact-graph/tree/artifact-graph-v0.9.0) | [`1c847f0bdcba1a815e30804ef31a7fac30c0a305`](https://github.com/ifoohoo/artifact-graph/commit/1c847f0bdcba1a815e30804ef31a7fac30c0a305) | `artifact-chain-assistant` | Git-native artifact graph runtime and CLI for scanning, querying, validation, and version locks. Install this npm package in the target project. artifact-chain-assistant provides related workflow guidance and declares its own compatible runtime version. |

## About this marketplace

**artifact-skill-set** is the public marketplace index of AI IDE plugin/skill packages maintained by 广州市风荷科技有限公司, targeting Claude Code, CodeBuddy/WorkBuddy, OpenAI Codex, and Kimi Code.

- Add the marketplace with the commands above, then install individual plugins through each platform's plugin manager.
- Currently distributed: `artifact-chain-assistant`, `e2e-test`, `flow-architect`. See the table for per-platform availability.
- Each plugin's version authority lives in its own repository (self-contained manifests and git tags); this index only references them.
- Licensed under MIT — see [LICENSE](LICENSE).
