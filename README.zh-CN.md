# artifact-skill-set

[English](README.md)

这是 Artifact 聚合产品线面向 Claude Code、CodeBuddy/WorkBuddy、OpenAI Codex 和 Kimi Code 的插件市场。

**市场版本：** `20260901200249`

**作者：** 广州市风荷科技有限公司

这个仓库只存放市场清单。每个插件的实现、版本和发布记录都在各自的仓库中维护。

## 添加市场

| 平台 | 命令 |
| --- | --- |
| Claude Code | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| CodeBuddy / WorkBuddy | `/plugin marketplace add ifoohoo/artifact-skill-set` |
| OpenAI Codex | `codex plugin marketplace add ifoohoo/artifact-skill-set` |
| Kimi Code | `/plugins marketplace https://raw.githubusercontent.com/ifoohoo/artifact-skill-set/main/kimi-marketplace.json` |

## 使用 HTTPS，不走 SSH

Claude Code 默认会通过 SSH 解析 GitHub 的 `owner/repo` 简写，本市场中使用 `source: "github"` 的插件也一样。如果本机没有配置 GitHub 账号、SSH 密钥或 SSH Agent，请在启动 Claude Code **之前**设置下面的环境变量，强制使用 HTTPS：

- **macOS / Linux：** `export CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1`
- **Windows PowerShell：** `$env:CLAUDE_CODE_PLUGIN_PREFER_HTTPS='1'`

也可以直接使用完整 HTTPS 地址添加市场：

```
/plugin marketplace add https://github.com/ifoohoo/artifact-skill-set.git
```

设置该环境变量后，通过 `owner/repo` 简写安装插件时也会改用 HTTPS。公开仓库通过 HTTPS 拉取，不需要登录 GitHub。

> 如果 Git 仍然把 HTTPS 改写成 SSH，请检查本机的 `url.*.insteadOf` 配置。

## 国内用户下载加速方式

没有科学上网的手段，又需要拉取本站技能时，可参考下面的配置，让 Git 通过第三方下载代理访问本站在 GitHub 上公开发布的仓库。下面以 `ghfast.top` 为例：

```bash
git config --global \
  url."https://ghfast.top/https://github.com/ifoohoo/".insteadOf \
  "https://github.com/ifoohoo/"
```

配置以后照常使用上面的安装命令即可。Git 只会在本机改写实际下载地址，市场清单和插件清单里记录的 GitHub 仓库地址不会改变。

> **请注意：** 本站技能最终以 GitHub 上由 `ifoohoo` 维护的仓库为准。`ghfast.top` 是第三方下载代理，不是本站维护的镜像，也不参与版本发布。这种方式只适合公开仓库的只读拉取；不要通过代理访问私有仓库，也不要向代理发送 GitHub Token、密码等凭证。第三方代理可能中断服务或出现缓存延迟；市场仍以插件的 Git Tag 和完整 Commit SHA 核对版本，取不到对应提交时应停止安装。

查看当前 URL 改写配置：

```bash
git config --global --get-regexp '^url\..*\.insteadof$'
```

不再需要代理时，可以删除这项配置：

```bash
git config --global --unset-all \
  url."https://ghfast.top/https://github.com/ifoohoo/".insteadOf
```

## 已收录插件

| 插件 | 版本 | 源仓库 | Claude Code | CodeBuddy | Codex | Kimi Code |
| --- | --- | --- | --- | --- | --- | --- |
| artifact-chain-assistant | 0.10.0 | `ifoohoo/artifact-chain-assistant` | ✓ | ✓ | ✓ | ✓ |
| e2e-test | 0.2.1 | `ifoohoo/e2e-test` | ✓ | ✓ | ✓ | — |
| flow-architect | 0.5.4 | `ifoohoo/flow-architect` | ✓ | — | ✓ | — |

“✓”表示该插件已进入对应平台的市场清单，“—”表示没有进入。是否分发只看真源中的 `platforms` 开关；CodeBuddy/WorkBuddy 即使可以回退读取 `.claude-plugin/plugin.json`，也不会因此自动开启分发。

添加市场后，请使用对应平台的插件管理器安装具体插件。例如在 Claude Code 中执行 `/plugin install <name>@artifact-skill-set`。

## 基础组件

下面这些已经发布的 npm 包属于 Artifact 产品线，但不是市场插件，因此不会出现在任何平台的插件清单里。目标项目需要时直接安装。“相关插件”表示工作流上的集成关系，不表示该插件封装了表中所列 npm 版本；各插件自行声明它所兼容的依赖版本。

| 基础组件 | 已发布版本 | npm 包 | Git 标签 | 提交 SHA | 相关插件 | 定位 |
| --- | --- | --- | --- | --- | --- | --- |
| `agent-method-registry` | `0.2.2` | [agent-method-registry@0.2.2](https://www.npmjs.com/package/agent-method-registry/v/0.2.2) | [`agent-method-registry-v0.2.2`](https://github.com/ifoohoo/agent-method-registry/tree/agent-method-registry-v0.2.2) | [`2d15ae574e122c5dfabf245680b5a8de628d27e4`](https://github.com/ifoohoo/agent-method-registry/commit/2d15ae574e122c5dfabf245680b5a8de628d27e4) | `artifact-chain-assistant` | 提供确定性的方法目录解析、提供方验证、绑定和诊断能力的库与命令行工具。 独立使用 Registry 时直接安装这个 npm 包。artifact-chain-assistant 具备 Registry 支撑的路由能力，但它自身使用的依赖版本不由这张表决定。 |
| `artifact-graph` | `0.10.0` | [artifact-graph@0.10.0](https://www.npmjs.com/package/artifact-graph/v/0.10.0) | [`artifact-graph-v0.10.0`](https://github.com/ifoohoo/artifact-graph/tree/artifact-graph-v0.10.0) | [`d06db5c69a3de06da65694f10fb0e70f67924d1e`](https://github.com/ifoohoo/artifact-graph/commit/d06db5c69a3de06da65694f10fb0e70f67924d1e) | `artifact-chain-assistant` | 用于扫描、查询、校验和版本锁的 Git 原生制品图运行时与命令行工具。 在目标项目中安装这个 npm 包。artifact-chain-assistant 提供相关工作流指导，并独立声明它所兼容的运行时版本。 |

## 关于这个市场

- 当前收录：`artifact-chain-assistant`、`e2e-test`、`flow-architect`。各平台是否可用，以表格为准。
- 每个插件的版本以自身仓库中的清单和 Git Tag 为准，本市场只引用已经核验的发布坐标。
- 采用 MIT 许可证，详见 [LICENSE](LICENSE)。
