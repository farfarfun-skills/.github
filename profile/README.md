# farfarfun skills

面向 AI 编码 Agent（Claude Code、Codex 等）的 Skills 组织。当前组织下**所有仓库均为 fork 镜像**，没有自研内容——包括名称带 `farfarfun-skill--` 前缀的几个仓库，也是以 fork 关系接入的，统一按镜像仓库对待，不再单独区分"自研"。

## 这里有什么

- **Skills 镜像**：每日自动同步 GitHub 上高关注度的 Agent Skills 仓库（Anthropic、Vercel Labs、mattpocock 等团队维护的项目），统一收纳并持续更新，方便集中浏览和安装。
- **组织基础设施**：[`action-daily`](https://github.com/farfarfun-skills/action-daily) 承载跨仓库自动化，包括 Paperclip 镜像发布、组织内所有 fork 仓库的每日同步，是本组织唯一的非 fork 仓库。

## 仓库列表

| 仓库 | 说明 |
| --- | --- |
| [`anthropics--skills`](https://github.com/farfarfun-skills/anthropics--skills) | Anthropic 官方 Agent Skills 实现 |
| [`addyosmani--agent-skills`](https://github.com/farfarfun-skills/addyosmani--agent-skills) | 面向 AI coding agent 的生产级工程 skills |
| [`alirezarezvani--claude-skills`](https://github.com/farfarfun-skills/alirezarezvani--claude-skills) | 345+ Claude Code skills / plugins 大合集，覆盖工程、市场、产品、合规等多领域 |
| [`andrewyng--context-hub`](https://github.com/farfarfun-skills/andrewyng--context-hub) | 为 coding agent 提供可版本化、可校验的精选文档上下文 |
| [`vercel-labs--agent-skills`](https://github.com/farfarfun-skills/vercel-labs--agent-skills) | Vercel 官方 agent skills 合集 |
| [`vercel-labs--skills`](https://github.com/farfarfun-skills/vercel-labs--skills) | 开放 agent skills 生态的 CLI 工具（`npx skills`） |
| [`ibelick--ui-skills`](https://github.com/farfarfun-skills/ibelick--ui-skills) | 面向 Design Engineer 的 UI skills 合集 |
| [`mattpocock--skills`](https://github.com/farfarfun-skills/mattpocock--skills) | Matt Pocock（AI Hero）出品的工程向 skills |
| [`wshobson--agents`](https://github.com/farfarfun-skills/wshobson--agents) | 大型 agentic 插件市场：plugin / agent / skill / command 全家桶 |
| [`Agents365-ai--drawio-skill`](https://github.com/farfarfun-skills/Agents365-ai--drawio-skill) | 文本转专业 draw.io 图表 |
| [`JuliusBrussee--caveman`](https://github.com/farfarfun-skills/JuliusBrussee--caveman) | 压缩 AI agent 输出 token 用量 |
| [`dietrichgebert--ponytail`](https://github.com/farfarfun-skills/dietrichgebert--ponytail) | 让 AI agent 像资深工程师一样"偷懒"写最少的代码 |
| [`anbeime--skill`](https://github.com/farfarfun-skills/anbeime--skill) | 自动抓取 GitHub 全网 Skills 项目并分类整理的技能商店 |
| [`JimLiu--baoyu-skills`](https://github.com/farfarfun-skills/JimLiu--baoyu-skills) | Skills 合集 |
| [`ComposioHQ--awesome-claude-skills`](https://github.com/farfarfun-skills/ComposioHQ--awesome-claude-skills) | Claude Skills 相关资源的 Awesome List |
| [`tt-a1i--archify`](https://github.com/farfarfun-skills/tt-a1i--archify) | 生成可验证的架构/时序/数据流图，自包含 HTML |
| [`ConardLi--garden-skills`](https://github.com/farfarfun-skills/ConardLi--garden-skills) | Web 设计、知识检索、图片生成等 Skills 合集 |
| [`jakubkrehel--skills`](https://github.com/farfarfun-skills/jakubkrehel--skills) | 帮助搭建优秀界面的 agent skills 合集 |
| [`yizhiyanhua-ai--fireworks-tech-graph`](https://github.com/farfarfun-skills/yizhiyanhua-ai--fireworks-tech-graph) | 用自然语言生成生产级 SVG/PNG 技术图表 |
| [`paperclipai--paperclip`](https://github.com/farfarfun-skills/paperclipai--paperclip) | 开源的 Agent 管理应用 |
| [`farfarfun-skill--project-manager`](https://github.com/farfarfun-skills/farfarfun-skill--project-manager) | 面向 AI Agent 的项目治理 Skill：仓库结构、研发全生命周期门禁、Agent 执行边界、服务发布与运行约束 |
| [`farfarfun-skill--lang-spec-hub`](https://github.com/farfarfun-skills/farfarfun-skill--lang-spec-hub) | 面向 AI 编码代理的多语言开发规范 Skill（Python、Java 等） |
| [`farfarfun-skill--service-governance`](https://github.com/farfarfun-skills/farfarfun-skill--service-governance) | 服务工程规范 Skill：发布治理、Bash 生命周期、多仓库子模块编排 |
| [`farfarfun-skill--paperclip-governance`](https://github.com/farfarfun-skills/farfarfun-skill--paperclip-governance) | Paperclip 平台专属治理 Skill：执行隔离、任务协调 |

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

[`farfarfun/fundeploy`](https://github.com/farfarfun/fundeploy) 提供了 `fundeploy tool skills-sync` 子命令，作为本组织 Skill 镜像仓库（仓库名含 `--`）的本地安装/更新工具，替代手动 `git clone`/`cp`：

```bash
fundeploy tool skills-sync list                 # 查看远端 + 本地安装状态
fundeploy tool skills-sync install all           # 安装全部未安装的仓库
fundeploy tool skills-sync update all            # 更新全部已安装仓库（本地修改会被远端覆盖）
```

它会从本组织在 Gitee 的镜像拉取仓库到本地工作区（默认 `~/workspace/github/farfarfun-skills`），只挑选名称含 `--` 的仓库，同步后自动清理仓库内除 `.git` 外的隐藏目录。它与 [`action-daily`](https://github.com/farfarfun-skills/action-daily) 的每日 fork 同步是互补关系：`action-daily` 负责组织侧让 fork 仓库跟上游保持同步，`skills-sync` 负责把这些镜像仓库同步到使用者本地。
