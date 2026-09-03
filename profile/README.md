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
