# FarFarFun Skills

面向 AI 编码 Agent（Claude Code、Codex 等）的 Skills 组织。

## 这里有什么

- **热门 Skills 镜像**：每日自动同步 GitHub 上高关注度的 Agent Skills 仓库（Anthropic、Vercel Labs 等团队维护的项目），统一收纳并持续更新，方便集中浏览和安装。
- **自研 Skill 集合**：

  | 仓库 | 说明 |
  | --- | --- |
  | [`farfarfun--project-manager`](https://github.com/farfarfun-skills/farfarfun--project-manager) | 面向 AI Agent 的项目治理 Skill 集合：仓库结构、研发全生命周期门禁、Agent 执行边界、服务发布与运行约束 |
  | [`farfarfun--lang-spec-hub`](https://github.com/farfarfun-skills/farfarfun--lang-spec-hub) | 面向 AI 编码代理的多语言开发规范 Skill 集合（Python、Java 等） |

- **组织基础设施**：[`daily-action`](https://github.com/farfarfun-skills/daily-action) 承载跨仓库自动化，包括 Paperclip 镜像发布和组织内 fork 仓库的每日同步。

## 使用方式

多数 Skill 遵循同一套安装约定：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R <skill-dir> "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安装后在 Agent 对话中直接引用，例如：

```text
Use $<skill-name> to ...
```

具体每个 Skill 的能力、调用方式和依赖，参见各仓库自己的 README。

### 本地同步与更新（可选）：fundeploy skills-sync

[`farfarfun/fundeploy`](https://github.com/farfarfun/fundeploy) 提供了 `fundeploy tool skills-sync` 子命令，作为自研 Skill 仓库（仓库名含 `--`，即上表中的 `farfarfun--*`）的官方本地安装/更新工具，替代手动 `git clone`/`cp`：

```bash
fundeploy tool skills-sync list                 # 查看远端 + 本地安装状态
fundeploy tool skills-sync install all           # 安装全部未安装的自研 Skill 仓库
fundeploy tool skills-sync update all            # 更新全部已安装仓库（本地修改会被远端覆盖）
```

它会从本组织在 Gitee 的镜像拉取仓库到本地工作区（默认 `~/workspace/github/farfarfun-skills`），只挑选名称含 `--` 的仓库，同步后自动清理仓库内除 `.git` 外的隐藏目录。它与 [`daily-action`](https://github.com/farfarfun-skills/daily-action) 的每日 fork 同步是互补关系：`daily-action` 负责组织侧让 fork 仓库跟上游保持同步，`skills-sync` 负责把自研 Skill 仓库同步到使用者本地。
